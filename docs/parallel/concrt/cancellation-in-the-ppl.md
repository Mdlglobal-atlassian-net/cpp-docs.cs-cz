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
ms.openlocfilehash: 6e23ccd6fcae03bcad40ea560356f4d1290dbcdd
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866334"
---
# <a name="cancellation-in-the-ppl"></a>Zrušení v knihovně PPL

Tento dokument vysvětluje úlohu zrušení v knihovně PPL (Parallel Patterns Library), jak zrušit paralelní práci a jak určit, kdy je zrušená paralelní práce.

> [!NOTE]
> Modul runtime používá zpracování výjimek k implementaci zrušení. Ve vašem kódu tyto výjimky nezachyťte ani nezpracovávají. Kromě toho doporučujeme napsat kód bezpečný pro výjimku do těla funkce pro vaše úkoly. Například můžete použít vzor RAII ( *pořízení prostředku* ) a zajistit tak správné zpracování prostředků, když je vyvolána výjimka v těle úlohy. Kompletní příklad, který používá vzor RAII k vyčištění prostředku v úloze s možností zrušení, naleznete v tématu [Návod: odebrání práce z vlákna uživatelského rozhraní](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md).

## <a name="key-points"></a>Klíčové body

- Zrušení je kooperativní a zahrnuje koordinaci kódu, který požaduje zrušení a úlohu, která reaguje na zrušení.

- Pokud je to možné, použijte tokeny zrušení ke zrušení práce. Třída [Concurrency:: cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) definuje token zrušení.

- Při použití tokenů zrušení použijte metodu [Concurrency:: cancellation_token_source:: Cancel](reference/cancellation-token-source-class.md#cancel) k zahájení zrušení a funkci [concurrency:: cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) , která bude reagovat na zrušení. Použijte metodu [Concurrency:: cancellation_token:: is_canceled](reference/cancellation-token-class.md#is_canceled) a ověřte, zda jiná úloha vyžadovala zrušení.

- Zrušení se neprojeví okamžitě. I když se nová práce nespustí, pokud se zruší úloha nebo skupina úloh, musí aktivní práce kontrolovat a reagovat na zrušení.

- Pokračování založené na hodnotách zdědí token zrušení jeho předchozí úlohy. Pokračování založené na úlohách nikdy nedědí token jeho předchozí úlohy.

- Metodu [Concurrency:: cancellation_token:: none](reference/cancellation-token-class.md#none) použijte při volání konstruktoru nebo funkce, která přebírá objekt `cancellation_token`, ale nechcete, aby operace zrušit. Také Pokud neprojdete token zrušení do konstruktoru [Concurrency:: Task](../../parallel/concrt/reference/task-class.md) nebo funkce [concurrency:: create_task](reference/concurrency-namespace-functions.md#create_task) , tento úkol není zrušit.

## <a name="top"></a>V tomto dokumentu

- [Paralelní pracovní stromy](#trees)

- [Rušení paralelních úloh](#tasks)

    - [Zrušení paralelní práce pomocí tokenu zrušení](#tokens)

    - [Zrušení paralelní práce pomocí metody Cancel](#cancel)

    - [Zrušení paralelní práce pomocí výjimek](#exceptions)

- [Rušení paralelních algoritmů](#algorithms)

- [Kdy použít zrušení](#when)

## <a name="trees"></a>Paralelní pracovní stromy

PPL používá úkoly a skupiny úloh ke správě jemně odstupňovaných úloh a výpočtů. Skupiny úloh můžete vnořit do stromů, ve kterých se tvoří *stromy* paralelní práce. Následující ilustrace znázorňuje paralelní pracovní strom. Na tomto obrázku `tg1` a `tg2` reprezentují skupiny úloh; `t1`, `t2`, `t3`, `t4`a `t5` reprezentují práci, kterou provádějí skupiny úloh.

![Paralelní pracovní strom](../../parallel/concrt/media/parallelwork_trees.png "Paralelní pracovní strom")

Následující příklad ukazuje kód, který je požadován pro vytvoření stromu na ilustraci. V tomto příkladu jsou `tg1` a `tg2` objekty [Concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) ; `t1`, `t2`, `t3`, `t4`a `t5` jsou objekty [Concurrency:: task_handle](../../parallel/concrt/reference/task-handle-class.md) .

[!code-cpp[concrt-task-tree#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_1.cpp)]

Můžete také použít třídu [Concurrency:: task_group](reference/task-group-class.md) k vytvoření podobné pracovní struktury. Třída [Concurrency:: Task](../../parallel/concrt/reference/task-class.md) také podporuje pojem pracovní stromové struktury. Strom `task` ale je stromem závislostí. Ve stromové struktuře `task` po aktuální práci dokončí budoucí funkce. Ve stromové struktuře skupin úloh se interní práce dokončí před vnější prací. Další informace o rozdílech mezi úlohami a skupinami úloh najdete v tématu [Task paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

[[Nahoře](#top)]

## <a name="tasks"></a>Rušení paralelních úloh

Existuje několik způsobů, jak zrušit paralelní práci. Upřednostňovaným způsobem je použít token zrušení. Skupiny úloh také podporují metodu [Concurrency:: task_group:: Cancel](reference/task-group-class.md#cancel) a metodu [concurrency:: structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) . Konečným způsobem je vyvolat výjimku v těle pracovní funkce úkolu. Bez ohledu na to, kterou metodu zvolíte, je třeba pochopit, že zrušení neproběhne okamžitě. I když se nová práce nespustí, pokud se zruší úloha nebo skupina úloh, musí aktivní práce kontrolovat a reagovat na zrušení.

Další příklady, které zruší Paralelní úlohy, naleznete v tématu [Návod: připojení pomocí úloh a požadavků XML http](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md), [Postupy: použití zrušení pro přerušení paralelní smyčky](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)a [Postup: použití zpracování výjimek k přerušení paralelní smyčky](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).

### <a name="tokens"></a>Zrušení paralelní práce pomocí tokenu zrušení

Třídy `task`, `task_group`a `structured_task_group` podporují zrušení pomocí tokenů zrušení. PPL definuje třídy [Concurrency:: cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md) a [concurrency:: cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) pro tento účel. Použijete-li k zrušení práce token zrušení, modul runtime nespustí novou práci, která se přihlásí k odběru tohoto tokenu. Práce, která je již aktivní, může použít členskou funkci [is_canceled](../../parallel/concrt/reference/cancellation-token-class.md#is_canceled) k monitorování tokenu zrušení a zastavení, kdy může.

Chcete-li zahájit zrušení, zavolejte metodu [Concurrency:: cancellation_token_source:: Cancel](reference/cancellation-token-source-class.md#cancel) . Na zrušení můžete reagovat těmito způsoby:

- Pro `task` objekty použijte funkci [Concurrency:: cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) . `cancel_current_task` zruší aktuální úlohu a jakékoli její pokračování založené na hodnotách. (Zrušení *tokenu* zrušení, který je spojen s úlohou nebo jejich pokračováním, nelze zrušit.)

- Pro skupiny úloh a paralelní algoritmy použijte funkci [Concurrency:: is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) ke zjištění zrušení a vraťte se co nejdříve z těla úkolu, když tato funkce vrátí **hodnotu true**. (Nevolejte `cancel_current_task` ze skupiny úloh.)

Následující příklad ukazuje první základní vzor pro zrušení úlohy. Tělo úlohy občas kontroluje zrušení v rámci smyčky.

[!code-cpp[concrt-task-basic-cancellation#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_2.cpp)]

Funkce `cancel_current_task` vyvolá; Proto nemusíte explicitně vracet z aktuální smyčky nebo funkce.

> [!TIP]
> Alternativně můžete volat funkci [Concurrency:: interruption_point](reference/concurrency-namespace-functions.md#interruption_point) místo `cancel_current_task`.

Je důležité volat `cancel_current_task` v případě, že odpovíte na zrušení, protože úloha přechází na zrušený stav. Pokud vrátíte úvodní místo volání `cancel_current_task`, operace přejde do stavu dokončeno a všechny pokračování založené na hodnotách se spustí.

> [!CAUTION]
> Nikdy nevyvolávat `task_canceled` z vašeho kódu. Místo toho zavolejte `cancel_current_task`.

Když úloha skončí ve zrušeném stavu, vyvolá metoda [Concurrency:: task:: Get](reference/task-class.md#get) [concurrency:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md). (Naopak, [Concurrency:: task:: wait](reference/task-class.md#wait) vrátí [task_status:: Canceled](reference/concurrency-namespace-enums.md#task_group_status) a nevyvolává.) Následující příklad znázorňuje toto chování pro pokračování založené na úlohách. Pokračování na základě úkolů je vždy voláno, i když je předchozí úloha zrušena.

[!code-cpp[concrt-task-canceled#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_3.cpp)]

Vzhledem k tomu, že pokračování založené na hodnotách dědí token jejich předchozí úlohy, pokud nebyla vytvořena pomocí explicitního tokenu, pokračování okamžitě vstoupí do stavu zrušeno, i když je stále spuštěn předchozí úkol. Proto jakákoli výjimka, která je vyvolána předchozí úlohou po zrušení, není rozšířena na úlohy pokračování. Zrušení vždy Přepisuje stav předchozí úlohy. Následující příklad je podobný předchozímu, ale ilustruje chování pro pokračování založené na hodnotách.

[!code-cpp[concrt-task-canceled#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_4.cpp)]

> [!CAUTION]
> Pokud neprojdete token zrušení do konstruktoru `task` nebo funkce [Concurrency:: create_task](reference/concurrency-namespace-functions.md#create_task) , tato úloha není zrušit. Kromě toho je nutné předat stejný token zrušení do konstruktoru všech vnořených úloh (tj. úloh, které jsou vytvořeny v těle jiné úlohy) pro zrušení všech úloh současně.

Je možné, že budete chtít spustit libovolný kód při zrušení tokenu zrušení. Pokud například uživatel klikne na tlačítko **Storno** v uživatelském rozhraní, aby operaci zrušil, můžete toto tlačítko zakázat, dokud uživatel nespustí jinou operaci. Následující příklad ukazuje, jak použít metodu [Concurrency:: cancellation_token:: register_callback](reference/cancellation-token-class.md#register_callback) k registraci funkce zpětného volání, která se spouští při zrušení tokenu zrušení.

[!code-cpp[concrt-task-cancellation-callback#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_5.cpp)]

[Paralelismus úkolu](../../parallel/concrt/task-parallelism-concurrency-runtime.md) dokumentu vysvětluje rozdíl mezi pokračováním založeným na hodnotách a úlohami. Pokud neposkytnete objekt `cancellation_token` do úlohy pokračování, pokračování zdědí token zrušení z předchozí úlohy následujícími způsoby:

- Pokračování na základě hodnoty vždy zdědí token zrušení předchozí úlohy.

- Pokračování na základě úlohy nikdy nedědí token zrušení předchozí úlohy. Jediným způsobem, jak provést zrušení pokračování na základě úkolů, je explicitně předat token zrušení.

Tato chování nejsou ovlivněna chybnou úlohou (to znamená, že jedna vyvolá výjimku). V tomto případě je zrušené pokračování založené na hodnotách; pokračování založené na úlohách není zrušeno.

> [!CAUTION]
> Úkol, který je vytvořen v jiné úloze (jinými slovy, vnořená úloha), nedědí token zrušení nadřazené úlohy. Pouze pokračování založené na hodnotách zdědí token zrušení jeho předchozí úlohy.

> [!TIP]
> Metodu [Concurrency:: cancellation_token:: none](reference/cancellation-token-class.md#none) použijte při volání konstruktoru nebo funkce, která přebírá objekt `cancellation_token` a nechcete, aby operace zrušit.

Můžete také poskytnout token zrušení konstruktoru objektu `task_group` nebo `structured_task_group`. Důležitým aspektem je, že podřízené skupiny úloh dědí tento token zrušení. Příklad, který demonstruje tento koncept pomocí funkce [Concurrency:: run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token) ke spuštění volání `parallel_for`, naleznete v části [zrušení paralelních algoritmů](#algorithms) dále v tomto dokumentu.

[[Nahoře](#top)]

#### <a name="cancellation-tokens-and-task-composition"></a>Tokeny zrušení a skládání úloh

Funkce [Concurrency:: when_all](reference/concurrency-namespace-functions.md#when_all) a [concurrency:: when_any](reference/concurrency-namespace-functions.md#when_all) vám pomohou vytvořit více úkolů pro implementaci běžných vzorů. Tato část popisuje, jak tyto funkce fungují s tokeny zrušení.

Když zadáte token zrušení do funkce `when_all` a `when_any`, tato funkce se zruší pouze v případě zrušení tohoto tokenu zrušení nebo když jedna z úkolů účastníka skončí ve zrušeném stavu nebo vyvolá výjimku.

Funkce `when_all` dědí token zrušení z každého úkolu, který sestaví celkovou operaci, když k ní neposkytnete token zrušení. Úkol vrácený z `when_all` se zruší, když se kterákoli z těchto tokenů zruší, a nejméně jedna z úkolů účastníka se ještě nespustila nebo neběží. K podobnému chování dojde, když jedna z úloh vyvolá výjimku – úkol vrácený z `when_all` je okamžitě zrušen s touto výjimkou.

Modul runtime zvolí token zrušení pro úkol, který se vrátí z funkce `when_any` po dokončení této úlohy. Pokud žádný z úkolů účastníka nekončí v dokončeném stavu a jedna nebo více úloh vyvolá výjimku, je vybrána jedna z úloh, které se vyvolaly k dokončení `when_any` a jeho token je vybrán jako token pro finální úkol. Pokud se v dokončeném stavu dokončí více než jeden úkol, úloha vrácená z `when_any` úlohy skončí v dokončeném stavu. Modul runtime se pokusí vybrat dokončenou úlohu, jejíž token není během dokončování zrušen, aby se úloha vrácená z `when_any` okamžitě nezrušila, i když jiné spuštěné úlohy mohou být dokončeny v pozdějším bodě.

[[Nahoře](#top)]

### <a name="cancel"></a>Zrušení paralelní práce pomocí metody Cancel

Metody [Concurrency:: task_group:: Cancel](reference/task-group-class.md#cancel) a [concurrency:: structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) nastaví skupinu úloh na stav zrušeno. Po volání `cancel`skupina úloh nespustí budoucí úkoly. Metody `cancel` mohou být volány více podřízenými úlohami. Zrušená úloha způsobí, že metody [Concurrency:: task_group:: wait](reference/task-group-class.md#wait) a [concurrency:: structured_task_group:: wait](reference/structured-task-group-class.md#wait) vrátí [Concurrency:: Canceled](reference/concurrency-namespace-enums.md#task_group_status).

Pokud je skupina úloh zrušena, volání z každé podřízené úlohy do modulu runtime mohou aktivovat *bod přerušení*, což způsobí, že modul runtime vyvolá výjimku a zachytí typ interní výjimky pro zrušení aktivních úloh. Concurrency Runtime nedefinuje konkrétní body přerušení; mohou nastat při jakémkoli volání modulu runtime. Modul runtime musí zpracovat výjimky, které vyvolá, aby bylo možné provést zrušení. Proto neprovádějte zpracování neznámých výjimek v těle úlohy.

Pokud podřízená úloha provádí časově náročnou operaci a nevolá ji do modulu runtime, musí pravidelně kontrolovat zrušení a skončit včas. Následující příklad ukazuje jeden způsob, jak určit, kdy se práce zruší. Úloha `t4` zruší nadřazenou skupinu úloh, když dojde k chybě. Úloha `t5` občas volá metodu `structured_task_group::is_canceling` pro kontrolu zrušení. Pokud je nadřazená skupina úloh zrušena, úloha `t5` vytiskne zprávu a ukončí se.

[!code-cpp[concrt-task-tree#6](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_6.cpp)]

Tento příklad kontroluje zrušení<sup>každé 100.</sup> iterace smyčky Task. Frekvence, se kterou kontrolujete zrušení, závisí na objemu práce, kterou vaše úloha provádí, a na tom, jak rychle potřebujete, aby úkoly reagovaly na zrušení.

Pokud nemáte přístup k objektu nadřazené skupiny úloh, zavolejte funkci [Concurrency:: is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) , abyste zjistili, jestli je nadřazená skupina úloh zrušená.

Metoda `cancel` ovlivňuje pouze podřízené úlohy. Pokud například zrušíte zrušení skupiny úloh `tg1` na ilustraci stromové struktury paralelní práce, budou ovlivněny všechny úlohy stromu (`t1`, `t2`, `t3`, `t4`a `t5`). Pokud zrušíte vnořenou skupinu úloh `tg2`, budou ovlivněny pouze úlohy `t4` a `t5`.

Když zavoláte metodu `cancel`, všechny podřízené skupiny úloh se také zruší. Zrušení však nemá vliv na žádné nadřazené skupiny úloh v paralelní pracovní větvi. Následující příklady znázorňují to sestavením na ilustraci paralelní práce ve stromové struktuře.

První z těchto příkladů vytvoří pracovní funkci pro úlohu `t4`, která je podřízenou položkou skupiny úloh `tg2`. Pracovní funkce volá funkci `work` ve smyčce. Pokud jakékoliv volání `work` selžou, úloha zruší svou nadřazenou skupinu úloh. Tím dojde k tomu, že skupina úloh `tg2`a, aby zadala zrušený stav, ale nezruší `tg1`skupiny úloh.

[!code-cpp[concrt-task-tree#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_7.cpp)]

Tento druhý příklad je podobný prvnímu, s tím rozdílem, že úloha zruší `tg1`skupiny úloh. To má vliv na všechny úlohy ve stromové struktuře (`t1`, `t2`, `t3`, `t4`a `t5`).

[!code-cpp[concrt-task-tree#3](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_8.cpp)]

Třída `structured_task_group` není bezpečná pro přístup z více vláken. Proto podřízená úloha, která volá metodu svého nadřazeného objektu `structured_task_group`, vytvoří nespecifikované chování. Výjimkou z tohoto pravidla jsou metody `structured_task_group::cancel` a [Concurrency:: structured_task_group:: is_canceling](reference/structured-task-group-class.md#is_canceling) . Podřízená úloha může zavolat tyto metody pro zrušení nadřazené skupiny úloh a kontrolu zrušení.

> [!CAUTION]
> I když můžete použít token zrušení ke zrušení práce, která je prováděna skupinou úloh, která se spouští jako podřízený objekt `task`, nemůžete použít metody `task_group::cancel` nebo `structured_task_group::cancel` k zrušení `task` objektů, které se spouštějí ve skupině úloh.

[[Nahoře](#top)]

### <a name="exceptions"></a>Zrušení paralelní práce pomocí výjimek

Použití tokenů zrušení a metoda `cancel` jsou efektivnější než zpracování výjimek při zrušení paralelní pracovní struktury. Tokeny zrušení a metoda `cancel` zruší v horní části úlohu a všechny podřízené úlohy. Zpracování výjimek naopak funguje tak, jak je v dolní části, a musí každou podřízenou skupinu úloh zrušit nezávisle, protože se výjimka rozšíří nahoru. Téma [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md) vysvětluje, jak Concurrency Runtime používá výjimky k oznamování chyb. Ne všechny výjimky však naznačují chybu. Například algoritmus vyhledávání může při hledání výsledku zrušit jeho přidruženou úlohu. Jak již bylo zmíněno dříve, zpracování výjimek je méně efektivní než použití metody `cancel` ke zrušení paralelní práce.

> [!CAUTION]
> Doporučujeme použít výjimky pro zrušení paralelní práce pouze v případě potřeby. Tokeny zrušení a skupina úloh `cancel` metody jsou efektivnější a méně náchylné k chybě.

Pokud vyvoláte výjimku v těle pracovní funkce, kterou předáte do skupiny úloh, modul runtime uloží tuto výjimku a zařadí výjimku do kontextu, který čeká na dokončení skupiny úloh. Stejně jako u metody `cancel` modul runtime zahodí všechny úlohy, které ještě nebyly spuštěny, a nepřijímá nové úlohy.

Tento třetí příklad se podobá druhému, s tím rozdílem, že `t4` úlohy vyvolá výjimku, která zruší `tg2`skupiny úloh. Tento příklad používá `try`-`catch` pro kontrolu zrušení, pokud skupina úloh `tg2` čeká na dokončení jeho podřízených úloh. Podobně jako v prvním příkladu způsobí, že skupina úloh `tg2` do stavu zrušeno, ale nezruší `tg1`skupiny úloh.

[!code-cpp[concrt-task-tree#4](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_9.cpp)]

Tento čtvrtý příklad používá zpracování výjimek ke zrušení celého pracovního stromu. V příkladu se zachytí výjimka, když skupina úloh `tg1` čeká na dokončení svých podřízených úkolů místo toho, aby skupina úloh `tg2` čekat na své podřízené úlohy. Podobně jako v druhém příkladu to způsobí, že obě úlohy jsou ve stromové struktuře `tg1` a `tg2`k zadání zrušeného stavu.

[!code-cpp[concrt-task-tree#5](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_10.cpp)]

Vzhledem k tomu, že metody `task_group::wait` a `structured_task_group::wait` vyvolávají výjimku, když podřízená úloha vyvolá výjimku, nedostanete z nich návratovou hodnotu.

[[Nahoře](#top)]

## <a name="algorithms"></a>Rušení paralelních algoritmů

Paralelní algoritmy v PPL, například `parallel_for`, sestavení ve skupinách úloh. Proto můžete použít mnoho stejných postupů pro zrušení paralelního algoritmu.

Následující příklady ilustrují několik způsobů zrušení paralelního algoritmu.

V následujícím příkladu je použita funkce `run_with_cancellation_token` pro volání algoritmu `parallel_for`. Funkce `run_with_cancellation_token` přijímá token zrušení jako argument a asynchronně volá poskytnutou pracovní funkci. Vzhledem k tomu, že paralelní algoritmy jsou vytvořeny na základě úkolů, dědí token zrušení nadřazené úlohy. Proto `parallel_for` může reagovat na zrušení.

[!code-cpp[concrt-cancel-parallel-for#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_11.cpp)]

Následující příklad používá metodu [Concurrency:: structured_task_group:: run_and_wait](reference/structured-task-group-class.md#run_and_wait) pro volání algoritmu `parallel_for`. Metoda `structured_task_group::run_and_wait` čeká na dokončení poskytnuté úlohy. Objekt `structured_task_group` umožňuje pracovní funkci úlohu zrušit.

[!code-cpp[concrt-task-tree#7](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_12.cpp)]

Tento příklad vytvoří následující výstup.

```Output
The task group status is: canceled.
```

Následující příklad používá zpracování výjimek pro zrušení smyčky `parallel_for`. Modul runtime zazařazuje výjimku do volajícího kontextu.

[!code-cpp[concrt-task-tree#9](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_13.cpp)]

Tento příklad vytvoří následující výstup.

```Output
Caught 50
```

Následující příklad používá logický příznak pro koordinaci zrušení ve `parallel_for` smyčce. Každý úkol je spuštěn, protože tento příklad nepoužívá metodu `cancel` nebo zpracování výjimek ke zrušení celé sady úkolů. Proto tato technika může mít více výpočetních režijních nákladů než mechanismus zrušení.

[!code-cpp[concrt-task-tree#8](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_14.cpp)]

Každá metoda zrušení má své výhody oproti ostatním. Vyberte metodu, která vyhovuje vašim konkrétním potřebám.

[[Nahoře](#top)]

## <a name="when"></a>Kdy použít zrušení

Použití zrušení je vhodné, pokud je možné včas ukončit každého člena skupiny souvisejících úloh. Existují však některé scénáře, kdy zrušení nemusí být vhodné pro vaši aplikaci. Například vzhledem k tomu, že zrušení úlohy je kooperativní, nebude celá sada úkolů zrušena, pokud je nějaký jednotlivý úkol zablokován. Například pokud jedna úloha ještě nebyla spuštěna, ale odblokuje jinou aktivní úlohu, nespustí se, pokud je skupina úloh zrušena. To může způsobit zablokování ve vaší aplikaci. Druhý příklad, kdy použití zrušení nemusí být vhodné, je při zrušení úlohy, ale jeho podřízená úloha provádí důležitou operaci, jako je například uvolnění prostředku. Vzhledem k tomu, že je při zrušení nadřazené úlohy zrušena celková sada úkolů, tato operace se neprovede. Příklad, který ukazuje tento bod, naleznete v tématu [Vysvětlení způsobu, jakým zrušení a zpracování výjimek ovlivňují oddíl zničení objektů](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) v tématu osvědčené postupy v tématu Knihovna paralelních vzorů.

[[Nahoře](#top)]

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Postupy: Přerušení paralelní smyčky pomocí zrušení](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)|Ukazuje, jak použít zrušení pro implementaci paralelního vyhledávacího algoritmu.|
|[Postupy: Přerušení paralelní smyčky pomocí zpracování výjimek](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|Ukazuje, jak použít třídu `task_group` k zápisu vyhledávacího algoritmu pro základní stromovou strukturu.|
|[Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Popisuje způsob, jakým modul runtime zpracovává výjimky, které jsou vyvolány skupinami úloh, odlehčenými úlohami a asynchronními agenty a jak reagovat na výjimky ve vašich aplikacích.|
|[Paralelní úkoly](../../parallel/concrt/task-parallelism-concurrency-runtime.md)|Popisuje, jak se úlohy týkají skupin úloh a jak můžete ve svých aplikacích používat nestrukturované a strukturované úlohy.|
|[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)|Popisuje paralelní algoritmy, které souběžně provádějí práci na kolekcích dat.|
|[Knihovna PPL (Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Poskytuje přehled knihovny paralelních vzorů.|

## <a name="reference"></a>Referenční informace

[task – třída (Concurrency Runtime)](../../parallel/concrt/reference/task-class.md)

[cancellation_token_source – třída](../../parallel/concrt/reference/cancellation-token-source-class.md)

[cancellation_token – třída](../../parallel/concrt/reference/cancellation-token-class.md)

[task_group – třída](reference/task-group-class.md)

[structured_task_group – třída](../../parallel/concrt/reference/structured-task-group-class.md)

[parallel_for funkce](reference/concurrency-namespace-functions.md#parallel_for)
