---
title: Zrušení v knihovně PPL
ms.date: 11/19/2018
helpviewer_keywords:
- parallel algorithms, canceling [Concurrency Runtime]
- canceling parallel algorithms [Concurrency Runtime]
- parallel tasks, canceling [Concurrency Runtime]
- cancellation in the PPL
- parallel work trees [Concurrency Runtime]
- canceling parallel tasks [Concurrency Runtime]
ms.assetid: baaef417-b2f9-470e-b8bd-9ed890725b35
ms.openlocfilehash: 27c0ea3cfcf62060800c1c0b034dde7de6357250
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368495"
---
# <a name="cancellation-in-the-ppl"></a>Zrušení v knihovně PPL

Tento dokument vysvětluje roli zrušení v knihovně paralelnívzory (PPL), jak zrušit paralelní práci a jak určit, kdy je zrušena paralelní práce.

> [!NOTE]
> Runtime používá zpracování výjimek k implementaci zrušení. Nezachytát ani zpracovávat tyto výjimky v kódu. Kromě toho doporučujeme napsat kód bezpečné pro výjimky v tělech funkcí pro vaše úkoly. Například můžete použít vzorek *pořízení prostředků je inicializace* (RAII) k zajištění, že prostředky jsou správně zpracovány při vyvolání výjimky v těle úkolu. Úplný příklad, který používá vzor RAII k vyčištění prostředku v úkolu zrušitelné, naleznete v [návodu: Odebrání práce z vlákna uživatelského rozhraní](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md).

## <a name="key-points"></a>Klíčové body

- Zrušení je spolupráce a zahrnuje koordinaci mezi kódem, který požaduje zrušení a úkol, který reaguje na zrušení.

- Pokud je to možné, použijte zrušení tokeny zrušit práci. [Souběžnost::cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) třída definuje token zrušení.

- Při použití tokenů zrušení použijte metodu [concurrency::cancellation_token_source:cancel](reference/cancellation-token-source-class.md#cancel) k zahájení zrušení a funkci [concurrency::cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) k reakci na zrušení. Pomocí metody [souběžnosti::cancellation_token::is_canceled](reference/cancellation-token-class.md#is_canceled) zkontrolujte, zda jiný úkol nepožadoval zrušení.

- Ke zrušení nedojde okamžitě. Přestože nová práce není spuštěna, pokud je úkol nebo skupina úkolů zrušena, aktivní práce musí zkontrolovat zrušení a reagovat na na ně.

- Pokračování založené na hodnotě dědí token zrušení jeho předchozí úlohy. Pokračování založené na úlohách nikdy nezdědí token jeho předchozí úlohy.

- Při volání konstruktoru nebo funkce, která přebírá `cancellation_token` objekt, ale nechcete, aby byla operace zrušena, použijte metodu [souběžnosti::cancellation_token::none.](reference/cancellation-token-class.md#none) Také pokud nepředátoken zrušení [concurrency::task](../../parallel/concrt/reference/task-class.md) konstruktor nebo [souběžnost::create_task](reference/concurrency-namespace-functions.md#create_task) funkce, tento úkol není zrušitelný.

## <a name="in-this-document"></a><a name="top"></a>V tomto dokumentu

- [Paralelní pracovní stromy](#trees)

- [Zrušení paralelních úloh](#tasks)

  - [Použití tokenu zrušení ke zrušení paralelní práce](#tokens)

  - [Použití metody zrušení k zrušení paralelní práce](#cancel)

  - [Použití výjimek ke zrušení paralelní práce](#exceptions)

- [Zrušení paralelních algoritmů](#algorithms)

- [Kdy nepoužívat zrušení](#when)

## <a name="parallel-work-trees"></a><a name="trees"></a>Paralelní pracovní stromy

PPL používá úkoly a skupiny úkolů ke správě jemně odstupňovaných úkolů a výpočtů. Skupiny úkolů můžete vnořit a vytvořit *stromy* paralelní práce. Následující obrázek znázorňuje paralelní pracovní strom. Na tomto `tg1` obrázku a `tg2` představují skupiny úkolů; `t1` `t2`, , `t4`, `t5` a představují práci, kterou provádějí skupiny úkolů. `t3`

![Paralelní pracovní strom](../../parallel/concrt/media/parallelwork_trees.png "Paralelní pracovní strom")

Následující příklad ukazuje kód, který je nutný k vytvoření stromu na obrázku. V tomto `tg1` příkladu a `tg2` jsou [souběžnost::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) objekty; `t1`, `t2` `t3`, `t4`, `t5` a [jsou souběžnosti::task_handle](../../parallel/concrt/reference/task-handle-class.md) objekty.

[!code-cpp[concrt-task-tree#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_1.cpp)]

Můžete také použít [souběžnost::task_group](reference/task-group-class.md) třídy k vytvoření podobného pracovního stromu. [Souběžnost::task](../../parallel/concrt/reference/task-class.md) class také podporuje pojem stromu práce. `task` Strom je však strom závislostí. Ve `task` stromu se budoucí práce dokončí po aktuální práci. Ve stromu skupiny úloh se interní práce dokončí před vnější prací. Další informace o rozdílech mezi úkoly a skupinami úkolů naleznete v [tématu Paralelismus úkolu](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

[[Nahoře]](#top)

## <a name="canceling-parallel-tasks"></a><a name="tasks"></a>Zrušení paralelních úloh

Existuje několik způsobů, jak zrušit paralelní práci. Upřednostňovaným způsobem je použití tokenu zrušení. Skupiny úloh také podporují [souběžnost::task_group::cancel](reference/task-group-class.md#cancel) metodu a metodu [concurrency::structured_task_group::cancel.](reference/structured-task-group-class.md#cancel) Posledním způsobem je vyvolat výjimku v těle pracovní funkce úkolu. Bez ohledu na to, kterou metodu zvolíte, pochopit, že zrušení nedochází okamžitě. Přestože nová práce není spuštěna, pokud je úkol nebo skupina úkolů zrušena, aktivní práce musí zkontrolovat zrušení a reagovat na na ně.

Další příklady, které ruší paralelní úlohy, naleznete [v tématu Connecting Using Tasks and XML HTTP Requests](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md), [How to: Use Cancellation to Break from a Parallel Loop](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md), and How [to: Use Exception Handling to Break from a Parallel Loop](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).

### <a name="using-a-cancellation-token-to-cancel-parallel-work"></a><a name="tokens"></a>Použití tokenu zrušení ke zrušení paralelní práce

`task`Služby `task_group`, `structured_task_group` a třídy podporují zrušení pomocí tokenů zrušení. PPL definuje [souběžnost::cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md) a [souběžnost::cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) třídy pro tento účel. Při použití tokenzrušení zrušit práci, runtime nespustí novou práci, která se přihlásí k odběru tohoto tokenu. Práce, která je již aktivní můžete použít [is_canceled](../../parallel/concrt/reference/cancellation-token-class.md#is_canceled) členské funkce sledovat token zrušení a zastavit, když je to možné.

Chcete-li zahájit zrušení, zavolejte metodu [concurrency::cancellation_token_source::cancel.](reference/cancellation-token-source-class.md#cancel) Na zrušení reagujete těmito způsoby:

- Pro `task` objekty použijte funkci [souběžnosti::cancel_current_task.](reference/concurrency-namespace-functions.md#cancel_current_task) `cancel_current_task`zruší aktuální úlohu a všechny jeho pokračování založené na hodnotě. (Nezruší *token* zrušení, který je přidružen k úloze nebo jeho pokračování.)

- Pro skupiny úloh a paralelní algoritmy použijte funkci [concurrency::is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) ke zjištění zrušení a vrácení co nejdříve z těla úkolu, když tato funkce vrátí **hodnotu true**. (Nevolat `cancel_current_task` ze skupiny úkolů.)

Následující příklad ukazuje první základní vzor pro zrušení úkolu. Tělo úkolu občas kontroluje zrušení uvnitř smyčky.

[!code-cpp[concrt-task-basic-cancellation#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_2.cpp)]

Funkce `cancel_current_task` hází; proto není nutné explicitně vrátit z aktuální smyčky nebo funkce.

> [!TIP]
> Alternativně můžete volat [funkci souběžnosti::interruption_point](reference/concurrency-namespace-functions.md#interruption_point) `cancel_current_task`místo .

Je důležité volat, `cancel_current_task` když odpovíte na zrušení, protože převede úkol do zrušeného stavu. Pokud vrátíte brzy `cancel_current_task`namísto volání , operace přechody do stavu dokončení a všechny pokračování založené na hodnotě jsou spuštěny.

> [!CAUTION]
> Nikdy `task_canceled` házet z kódu. Místo `cancel_current_task` toho zavolej.

Když úkol skončí ve stavu zrušený, [souběžnost::task::get](reference/task-class.md#get) metoda vyvolá [souběžnost::task_canceled](../../parallel/concrt/reference/task-canceled-class.md). (Naopak [souběžnost::task::wait](reference/task-class.md#wait) vrátí [task_status::canceled](reference/concurrency-namespace-enums.md#task_group_status) and does not throw.) Následující příklad ilustruje toto chování pro pokračování založené na úlohách. Pokračování založené na úlohách se vždy nazývá, i když je předchozí úloha zrušena.

[!code-cpp[concrt-task-canceled#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_3.cpp)]

Vzhledem k tomu, že pokračování založená na hodnotě dědí token jejich předchozí úlohy, pokud byly vytvořeny s explicitní token, pokračování okamžitě zadat zrušený stav i v případě, že předchozí úloha je stále spuštěna. Proto žádná výjimka, která je vyvolána předchozí úlohy po zrušení není rozšířena na úkoly pokračování. Zrušení vždy přepíše stav předchozí úlohy. Následující příklad se podobá předchozí, ale ilustruje chování pro pokračování založené na hodnotě.

[!code-cpp[concrt-task-canceled#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_4.cpp)]

> [!CAUTION]
> Pokud nepředáte token zrušení `task` konstruktoru nebo [funkci concurrency::create_task,](reference/concurrency-namespace-functions.md#create_task) nebude možné tuto úlohu zrušit. Kromě toho musíte předat stejný token zrušení konstruktoru všech vnořených úkolů (to znamená, že úkoly, které jsou vytvořeny v těle jiné úlohy) zrušit všechny úkoly současně.

Můžete chtít spustit libovolný kód při zrušení tokenu zrušení. Pokud například uživatel v uživatelském rozhraní zvolí tlačítko **Storno,** můžete operaci zakázat, dokud uživatel nespustí jinou operaci. Následující příklad ukazuje, jak použít [metodu concurrency::cancellation_token::register_callback](reference/cancellation-token-class.md#register_callback) k registraci funkce zpětného volání, která se spustí při zrušení tokenu zrušení.

[!code-cpp[concrt-task-cancellation-callback#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_5.cpp)]

Dokument [Task Parallelism](../../parallel/concrt/task-parallelism-concurrency-runtime.md) vysvětluje rozdíl mezi pokračováními založenými na hodnotách a úkoly. Pokud nezadáte `cancellation_token` objekt pro úlohu pokračování, pokračování zdědí token zrušení z předchozí úlohy následujícími způsoby:

- Pokračování založené na hodnotě vždy zdědí token zrušení předchozí úlohy.

- Pokračování založené na úlohách nikdy nezdědí token zrušení předchozí úlohy. Jediný způsob, jak provést pokračování na základě úlohy zrušitelné, je explicitně předat token zrušení.

Tato chování nejsou ovlivněny chybové úlohy (to znamená, že vyvolání výjimky). V tomto případě je zrušeno pokračování založené na hodnotě; pokračování založené na úlohách není zrušeno.

> [!CAUTION]
> Úloha vytvořená v jiné úloze (jinými slovy vnořená úloha) nedědí token zrušení nadřazené úlohy. Pouze pokračování založené na hodnotě zdědí token zrušení jeho předchozí úlohy.

> [!TIP]
> Při volání konstruktoru nebo funkce, která přebírá `cancellation_token` objekt, použijte metodu [concurrency::cancellation_token::none.](reference/cancellation-token-class.md#none)

Můžete také poskytnout token zrušení konstruktoru `task_group` `structured_task_group` nebo objektu. Důležitým aspektem je, že podřízené skupiny úloh dědí tento token zrušení. Příklad, který ukazuje tento koncept pomocí [funkce concurrency::run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token) `parallel_for`ke spuštění volání , naleznete v [tématu Zrušení paralelních algoritmů](#algorithms) dále v tomto dokumentu.

[[Nahoře]](#top)

#### <a name="cancellation-tokens-and-task-composition"></a>Tokeny zrušení a skládání úloh

[Souběžnost::when_all](reference/concurrency-namespace-functions.md#when_all) a [souběžnost::when_any](reference/concurrency-namespace-functions.md#when_all) funkce vám mohou pomoci vytvořit více úkolů k implementaci běžných vzorů. Tato část popisuje, jak tyto funkce fungují s tokeny zrušení.

Pokud zadáte token zrušení buď `when_all` `when_any` a funkce, tato funkce zruší pouze v případě, že token zrušení je zrušena nebo když jeden z účastníků úkoly končí ve zrušeném stavu nebo vyvolá výjimku.

Funkce `when_all` zdědí token zrušení z každé úlohy, která skládá celkovou operaci, pokud neposkytujete token zrušení k němu. Úloha, která `when_all` je vrácena z je zrušena, pokud některý z těchto tokenů jsou zrušeny a alespoň jeden z úkolů účastníka ještě nebylspuštěn nebo je spuštěn. K podobnému chování dochází, když jeden z úkolů vyvolá výjimku - úloha, která je vrácena z `when_all` je okamžitě zrušena s výjimkou této výjimky.

Runtime zvolí token zrušení pro úlohu, `when_any` která je vrácena z funkce po dokončení této úlohy. Pokud žádný z účastníků úkoly dokončit v dokončeném stavu a jeden nebo více úkolů vyvolá výjimku, jeden z úkolů, které hodil je vybrán k dokončení `when_any` a jeho token je vybrán jako token pro konečný úkol. Pokud více než jeden úkol dokončí ve stavu dokončení, `when_any` úkol, který je vrácen z úkolu končí ve stavu dokončení. Modul runtime se pokusí vybrat dokončenou úlohu, jejíž token není zrušen v `when_any` době dokončení tak, aby úloha, která je vrácena z není okamžitě zrušena, i když jiné provádění úloh může být dokončena později.

[[Nahoře]](#top)

### <a name="using-the-cancel-method-to-cancel-parallel-work"></a><a name="cancel"></a>Použití metody zrušení k zrušení paralelní práce

[Souběžnost::task_group:cancel](reference/task-group-class.md#cancel) a [concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel) methods nastavit skupinu úkolů do zrušeného stavu. Po volání `cancel`skupina úkolů nespustí budoucí úkoly. Metody `cancel` mohou být volány více podřízenými úkoly. Zrušený úkol způsobí [souběžnost::task_group::wait](reference/task-group-class.md#wait) a [concurrency::structured_task_group::wait](reference/structured-task-group-class.md#wait) metody vrátit [souběžnost::canceled](reference/concurrency-namespace-enums.md#task_group_status).

Pokud je skupina úloh zrušena, volání z každé podřízené úlohy do běhu může vyvolat *bod přerušení*, což způsobí, že za běhu vyvolat a zachytit typ vnitřní výjimky zrušit aktivní úlohy. Souběžnost Runtime nedefinuje konkrétní body přerušení; mohou nastat v libovolném volání runtime. Runtime musí zpracovat výjimky, které vyvolá k provedení zrušení. Proto nezpracovat neznámé výjimky v těle úkolu.

Pokud podřízená úloha provádí časově náročnou operaci a nevolá do runtime, musí pravidelně kontrolovat zrušení a ukončení včas. Následující příklad ukazuje jeden způsob, jak zjistit, kdy je práce zrušena. Úloha `t4` zruší nadřazenou skupinu úkolů, když narazí na chybu. Úloha `t5` občas `structured_task_group::is_canceling` volá metodu ke kontrole zrušení. Pokud je nadřazená `t5` skupina úkolů zrušena, vytiskne zprávu a ukončí ji.

[!code-cpp[concrt-task-tree#6](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_6.cpp)]

Tento příklad kontroluje zrušení na každé 100<sup>iteraci</sup> smyčky úlohy. Četnost kontroly zrušení závisí na množství práce, kterou váš úkol provádí, a na tom, jak rychle potřebujete, aby úkoly reagovaly na zrušení.

Pokud nemáte přístup k objektu nadřazené skupiny úkolů, zavolejte funkci [concurrency::is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) a zjistěte, zda je nadřazená skupina úkolů zrušena.

Metoda `cancel` ovlivňuje pouze podřízené úkoly. Pokud například `tg1` zrušíte skupinu úkolů na obrázku paralelního pracovního`t1`stromu, budou ovlivněny všechny úkoly ve stromu `t2`( , , `t3`, `t4`, a `t5`). Pokud zrušíte vnořenou `tg2`skupinu `t4` `t5` úkolů, budou ovlivněny pouze úkoly a úkoly.

Při volání `cancel` metody jsou zrušeny také všechny podřízené skupiny úloh. Zrušení však nemá vliv na všechny rodiče skupiny úloh v paralelním pracovním stromu. Následující příklady to ukazují sestavením na ilustraci paralelního pracovního stromu.

První z těchto příkladů vytvoří pracovní funkci `t4`pro úkol , která `tg2`je podřízenou skupinou úkolů . Pracovní funkce volá `work` funkci ve smyčce. Pokud se `work` nezdaří jakékoli volání, úloha zruší svou nadřazenou skupinu úkolů. To způsobí, `tg2` že skupina úkolů zadá zrušený stav, ale nezruší skupinu `tg1`úkolů .

[!code-cpp[concrt-task-tree#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_7.cpp)]

Tento druhý příklad se podobá prvnímu, s tím `tg1`rozdílem, že úkol zruší skupinu úkolů . To ovlivní všechny úkoly`t1` `t2`ve `t3` `t4`stromu `t5`( , , , , a ).

[!code-cpp[concrt-task-tree#3](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_8.cpp)]

Třída `structured_task_group` není bezpečná pro přístup z více vláken. Proto podřízené úlohy, která volá `structured_task_group` metodu nadřazeného objektu vytváří nespecifikované chování. Výjimky z tohoto pravidla `structured_task_group::cancel` jsou a [souběžnost::structured_task_group::is_canceling](reference/structured-task-group-class.md#is_canceling) metody. Podřízená úloha může tyto metody volat ke zrušení nadřazené skupiny úkolů a ke kontrole zrušení.

> [!CAUTION]
> Přestože token zrušení můžete použít ke zrušení práce, která je prováděna `task` skupinou úloh, `task_group::cancel` `structured_task_group::cancel` která je `task` spuštěna jako podřízený objekt, nelze použít metody nebo ke zrušení objektů spuštěných ve skupině úloh.

[[Nahoře]](#top)

### <a name="using-exceptions-to-cancel-parallel-work"></a><a name="exceptions"></a>Použití výjimek ke zrušení paralelní práce

Použití tokenů zrušení a `cancel` metody jsou efektivnější než zpracování výjimek při zrušení paralelnípracovní strom. Tokeny zrušení `cancel` a metoda zrušit úkol a všechny podřízené úkoly způsobem shora dolů. Naopak zpracování výjimek funguje způsobem zdola nahoru a musí zrušit každou podřízenou skupinu úloh nezávisle, protože výjimka se šíří směrem nahoru. Téma [Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md) vysvětluje, jak runtime souběžnosti používá výjimky ke komunikaci chyb. Ne všechny výjimky však označují chybu. Vyhledávací algoritmus může například zrušit přidružený úkol při hledání výsledku. Však jak již bylo zmíněno dříve, `cancel` zpracování výjimek je méně efektivní než pomocí metody zrušit paralelní práce.

> [!CAUTION]
> Doporučujeme použít výjimky zrušit paralelní práce pouze v případě potřeby. Tokeny zrušení a `cancel` metody skupiny úloh jsou efektivnější a méně náchylné k chybám.

Při vyvolání výjimky v těle pracovní funkce, kterou předáte skupině úloh, za běhu uloží tuto výjimku a zařazuje výjimku do kontextu, který čeká na dokončení skupiny úloh. Stejně `cancel` jako u metody zahodí zahození všech úloh, které ještě nebyly spuštěny, a nepřijímá nové úkoly.

Tento třetí příklad se podobá druhému, s tím rozdílem, že úloha `t4` vyvolá výjimku pro zrušení skupiny `tg2`úloh . Tento příklad `try` - `catch` používá blok ke kontrole zrušení, když skupina `tg2` úloh čeká na dokončení podřízených úkolů. Stejně jako v prvním příkladu to způsobí, že skupina `tg2` úkolů zadá zrušený stav, ale nezruší skupinu `tg1`úkolů .

[!code-cpp[concrt-task-tree#4](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_9.cpp)]

Tento čtvrtý příklad používá zpracování výjimek ke zrušení celého pracovního stromu. Příklad zachytí výjimku, `tg1` když skupina úloh čeká na dokončení `tg2` podřízených úkolů namísto toho, když skupina úkolů čeká na podřízené úkoly. Stejně jako druhý příklad to způsobí, `tg1` že `tg2`obě skupiny úkolů ve stromu a , zadat zrušený stav.

[!code-cpp[concrt-task-tree#5](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_10.cpp)]

Vzhledem `task_group::wait` `structured_task_group::wait` k tomu, že a metody vyvolat při podřízené úlohy vyvolá výjimku, neobdržíte vrácenou hodnotu z nich.

[[Nahoře]](#top)

## <a name="canceling-parallel-algorithms"></a><a name="algorithms"></a>Zrušení paralelních algoritmů

Paralelní algoritmy v PPL, `parallel_for`například , stavět na skupinách úloh. Proto můžete použít mnoho stejných technik zrušit paralelní algoritmus.

Následující příklady ilustrují několik způsobů zrušení paralelní algoritmus.

Následující příklad používá `run_with_cancellation_token` funkci k `parallel_for` volání algoritmu. Funkce `run_with_cancellation_token` přebírá token zrušení jako argument a volá zajišťovnou pracovní funkci synchronně. Vzhledem k tomu, že paralelní algoritmy jsou postaveny na úkolech, dědí token zrušení nadřazené úlohy. Proto `parallel_for` může reagovat na zrušení.

[!code-cpp[concrt-cancel-parallel-for#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_11.cpp)]

Následující příklad používá [metodu concurrency::structured_task_group::run_and_wait](reference/structured-task-group-class.md#run_and_wait) k volání `parallel_for` algoritmu. Metoda `structured_task_group::run_and_wait` čeká na dokončení zadaný úkol. Objekt `structured_task_group` umožňuje pracovní funkci zrušit úlohu.

[!code-cpp[concrt-task-tree#7](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_12.cpp)]

Tento příklad vytváří následující výstup.

```Output
The task group status is: canceled.
```

Následující příklad používá zpracování výjimek ke zrušení `parallel_for` smyčky. Zařazuje zařazuje zařazuje výjimku z kontextu volání.

[!code-cpp[concrt-task-tree#9](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_13.cpp)]

Tento příklad vytváří následující výstup.

```Output
Caught 50
```

Následující příklad používá logický příznak ke koordinaci zrušení ve `parallel_for` smyčce. Každá úloha je spuštěna, `cancel` protože tento příklad nepoužívá metodu nebo zpracování výjimek ke zrušení celkové sady úkolů. Proto tato technika může mít více výpočetní režie než mechanismus zrušení.

[!code-cpp[concrt-task-tree#8](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_14.cpp)]

Každá metoda zrušení má výhody oproti ostatním. Vyberte si metodu, která vyhovuje vašim specifickým potřebám.

[[Nahoře]](#top)

## <a name="when-not-to-use-cancellation"></a><a name="when"></a>Kdy nepoužívat zrušení

Použití zrušení je vhodné, pokud každý člen skupiny souvisejících úkolů může být ukončen včas. Existují však některé scénáře, kde zrušení nemusí být vhodné pro vaši aplikaci. Například vzhledem k tomu, že zrušení úkolu je kooperativní, celková sada úkolů se nezruší, pokud je blokován jakýkoli jednotlivý úkol. Pokud například jeden úkol ještě nebyl zahájen, ale odblokuje jiný aktivní úkol, nebude spuštěn, pokud je skupina úkolů zrušena. To může způsobit zablokování dojít ve vaší aplikaci. Druhým příkladem, kde použití zrušení nemusí být vhodné, je, když je úloha zrušena, ale jeho podřízená úloha provádí důležitou operaci, jako je například uvolnění prostředku. Vzhledem k tomu, že celková sada úkolů je zrušena při zrušení nadřazené úlohy, tato operace nebude provedena. Příklad, který ilustruje tento bod, naleznete [v části Pochopit, jak zrušení a zpracování výjimek ovlivňují zničení objektů](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) v tématu Doporučené postupy v tématu Knihovna paralelních vzorů.

[[Nahoře]](#top)

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Postupy: Přerušení paralelní smyčky pomocí zrušení](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)|Ukazuje, jak použít zrušení k implementaci paralelní ho rešeampu.|
|[Postupy: Přerušení paralelní smyčky pomocí zpracování výjimek](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|Ukazuje, jak `task_group` pomocí třídy napsat vyhledávací algoritmus pro základní stromové struktury.|
|[Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Popisuje, jak modul runtime zpracovává výjimky, které jsou vyvolány skupinami úloh, zjednodušené úlohy a asynchronní agenti a jak reagovat na výjimky ve vašich aplikacích.|
|[Paralelismus úkolu](../../parallel/concrt/task-parallelism-concurrency-runtime.md)|Popisuje, jak úkoly souvisejí se skupinami úkolů a jak můžete v aplikacích používat nestrukturované a strukturované úkoly.|
|[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)|Popisuje paralelní algoritmy, které současně provádějí práci na sběru dat|
|[Knihovna PPL (Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Obsahuje přehled knihovny paralelních vzorů.|

## <a name="reference"></a>Referenční informace

[třída úlohy (souběžné běhové zařízení)](../../parallel/concrt/reference/task-class.md)

[třída cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md)

[cancellation_token třída](../../parallel/concrt/reference/cancellation-token-class.md)

[task_group – třída](reference/task-group-class.md)

[structured_task_group – třída](../../parallel/concrt/reference/structured-task-group-class.md)

[funkce parallel_for](reference/concurrency-namespace-functions.md#parallel_for)
