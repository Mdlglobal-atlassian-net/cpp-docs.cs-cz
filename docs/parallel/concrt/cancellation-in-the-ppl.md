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
ms.openlocfilehash: 3a7f9c5720c4bd6a43a1a95f9bc19680ba0a9c1e
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2019
ms.locfileid: "69631716"
---
# <a name="cancellation-in-the-ppl"></a>Zrušení v knihovně PPL

Tento dokument vysvětluje úlohu zrušení v knihovně PPL (Parallel Patterns Library), jak zrušit paralelní práci a jak určit, kdy je zrušená paralelní práce.

> [!NOTE]
>  Modul runtime používá zpracování výjimek k implementaci zrušení. Ve vašem kódu tyto výjimky nezachyťte ani nezpracovávají. Kromě toho doporučujeme napsat kód bezpečný pro výjimku do těla funkce pro vaše úkoly. Například můžete použít vzor RAII ( *pořízení prostředku* ) a zajistit tak správné zpracování prostředků, když je vyvolána výjimka v těle úlohy. Kompletní příklad, který používá vzor RAII k vyčištění prostředku v úloze s možností zrušení, najdete v tématu [Názorný postup: Odebrání práce z vlákna](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)uživatelského rozhraní.

## <a name="key-points"></a>Klíčové body

- Zrušení je kooperativní a zahrnuje koordinaci kódu, který požaduje zrušení a úlohu, která reaguje na zrušení.

- Pokud je to možné, použijte tokeny zrušení ke zrušení práce. Třída [Concurrency:: cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) definuje token zrušení.

- Při použití tokenů zrušení použijte metodu [Concurrency:: cancellation_token_source:: Cancel](reference/cancellation-token-source-class.md#cancel) k zahájení zrušení a funkci [Concurrency:: cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) , která reaguje na zrušení. Použijte metodu [Concurrency:: cancellation_token:: is_canceled](reference/cancellation-token-class.md#is_canceled) ke kontrole, zda jiná úloha vyžadovala zrušení.

- Zrušení se neprojeví okamžitě. I když se nová práce nespustí, pokud se zruší úloha nebo skupina úloh, musí aktivní práce kontrolovat a reagovat na zrušení.

- Pokračování založené na hodnotách zdědí token zrušení jeho předchozí úlohy. Pokračování založené na úlohách nikdy nedědí token jeho předchozí úlohy.

- Použijte metodu [Concurrency:: cancellation_token:: none](reference/cancellation-token-class.md#none) při volání konstruktoru nebo funkce, která přebírá `cancellation_token` objekt, ale nechcete, aby byla operace zrušit. Také Pokud neprojdete token zrušení do konstruktoru [Concurrency:: Task](../../parallel/concrt/reference/task-class.md) nebo funkce [Concurrency:: create_task](reference/concurrency-namespace-functions.md#create_task) , tento úkol není zrušit.

##  <a name="top"></a>V tomto dokumentu

- [Paralelní pracovní stromy](#trees)

- [Rušení paralelních úloh](#tasks)

    - [Zrušení paralelní práce pomocí tokenu zrušení](#tokens)

    - [Zrušení paralelní práce pomocí metody Cancel](#cancel)

    - [Zrušení paralelní práce pomocí výjimek](#exceptions)

- [Rušení paralelních algoritmů](#algorithms)

- [Kdy použít zrušení](#when)

##  <a name="trees"></a>Paralelní pracovní stromy

PPL používá úkoly a skupiny úloh ke správě jemně odstupňovaných úloh a výpočtů. Skupiny úloh můžete vnořit do stromů, ve kterých se tvoří *stromy* paralelní práce. Následující ilustrace znázorňuje paralelní pracovní strom. Na tomto obrázku `tg1` a `tg2` reprezentovat skupiny úloh; `t1`, ,`t2` ,a`t5` reprezentovat práci, kterou provádějí skupiny úloh. `t3` `t4`

![Paralelní pracovní strom](../../parallel/concrt/media/parallelwork_trees.png "Paralelní pracovní strom")

Následující příklad ukazuje kód, který je požadován pro vytvoření stromu na ilustraci. V tomto příkladu `tg1` `tg2` jsou objekty [Concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) ; `t1`, ,`t2` ,a`t5` jsou objekty [Concurrency:: task_handle](../../parallel/concrt/reference/task-handle-class.md) . `t3` `t4`

[!code-cpp[concrt-task-tree#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_1.cpp)]

Můžete také použít třídu [Concurrency:: task_group](reference/task-group-class.md) k vytvoření podobné pracovní struktury. Třída [Concurrency:: Task](../../parallel/concrt/reference/task-class.md) také podporuje pojem pracovní stromové struktury. `task` Strom však je stromem závislostí. `task` Ve stromové struktuře budou budoucí funkce dokončeny po aktuální práci. Ve stromové struktuře skupin úloh se interní práce dokončí před vnější prací. Další informace o rozdílech mezi úlohami a skupinami úloh najdete v tématu [Task paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

[[Nahoře](#top)]

##  <a name="tasks"></a>Rušení paralelních úloh

Existuje několik způsobů, jak zrušit paralelní práci. Upřednostňovaným způsobem je použít token zrušení. Skupiny úloh také podporují metodu [Concurrency:: task_group:: Cancel](reference/task-group-class.md#cancel) a metodu [Concurrency:: structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) . Konečným způsobem je vyvolat výjimku v těle pracovní funkce úkolu. Bez ohledu na to, kterou metodu zvolíte, je třeba pochopit, že zrušení neproběhne okamžitě. I když se nová práce nespustí, pokud se zruší úloha nebo skupina úloh, musí aktivní práce kontrolovat a reagovat na zrušení.

Další příklady, které zruší Paralelní úlohy, najdete [v tématu Názorný postup: Postup připojení pomocí úloh a požadavků](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)XML http, [jak: Pomocí zrušení můžete přerušit paralelní smyčku](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)a [postupovat takto: Použijte zpracování výjimek pro přerušení paralelní smyčky](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).

###  <a name="tokens"></a>Zrušení paralelní práce pomocí tokenu zrušení

Třídy `task`, `task_group` a`structured_task_group` podporují zrušení pomocí tokenů zrušení. PPL definuje třídy [Concurrency:: cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md) a [Concurrency:: cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) pro tento účel. Použijete-li k zrušení práce token zrušení, modul runtime nespustí novou práci, která se přihlásí k odběru tohoto tokenu. Práce, která je již aktivní, může použít členskou funkci [is_canceled](../../parallel/concrt/reference/cancellation-token-class.md#is_canceled) k monitorování tokenu zrušení a zastavení, kdy může.

Chcete-li zahájit zrušení, zavolejte metodu [Concurrency:: cancellation_token_source:: Cancel](reference/cancellation-token-source-class.md#cancel) . Na zrušení můžete reagovat těmito způsoby:

- Pro `task` objekty použijte funkci [Concurrency:: cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) . `cancel_current_task`zruší aktuální úlohu a jakékoli její pokračování založené na hodnotách. (Zrušení tokenu zrušení, který je spojen s úlohou nebo jejich pokračováním, nelze zrušit.)

- Pro skupiny úloh a paralelní algoritmy použijte funkci [Concurrency:: is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) k detekci zrušení a vraťte se co nejdříve z těla úkolu, když tato funkce vrátí **hodnotu true**. (Nevolejte `cancel_current_task` ze skupiny úloh.)

Následující příklad ukazuje první základní vzor pro zrušení úlohy. Tělo úlohy občas kontroluje zrušení v rámci smyčky.

[!code-cpp[concrt-task-basic-cancellation#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_2.cpp)]

`cancel_current_task` Funkce vyvolá; proto nemusíte explicitně vracet z aktuální smyčky nebo funkce.

> [!TIP]
> Alternativně můžete zavolat funkci [Concurrency:: interruption_point](reference/concurrency-namespace-functions.md#interruption_point) místo `cancel_current_task`.

Je důležité volat `cancel_current_task` v případě, že odpovíte na zrušení, protože přejde úlohu do stavu zrušeno. Pokud vrátíte úvodní místo volání `cancel_current_task`, operace přejde do stavu dokončeno a všechny pokračování založené na hodnotách se spustí.

> [!CAUTION]
> Nikdy nevyvolávat `task_canceled` z vašeho kódu. Místo `cancel_current_task` toho zavolejte.

Když úloha skončí ve zrušeném stavu, vyvolá metoda [Concurrency:: task:: Get](reference/task-class.md#get) [Concurrency:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md). (Naopak, [Concurrency:: task:: wait](reference/task-class.md#wait) vrátí [task_status:: Canceled](reference/concurrency-namespace-enums.md#task_group_status) a nevyvolává.) Následující příklad znázorňuje toto chování pro pokračování založené na úlohách. Pokračování na základě úkolů je vždy voláno, i když je předchozí úloha zrušena.

[!code-cpp[concrt-task-canceled#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_3.cpp)]

Vzhledem k tomu, že pokračování založené na hodnotách dědí token jejich předchozí úlohy, pokud nebyla vytvořena pomocí explicitního tokenu, pokračování okamžitě vstoupí do stavu zrušeno, i když je stále spuštěn předchozí úkol. Proto jakákoli výjimka, která je vyvolána předchozí úlohou po zrušení, není rozšířena na úlohy pokračování. Zrušení vždy Přepisuje stav předchozí úlohy. Následující příklad je podobný předchozímu, ale ilustruje chování pro pokračování založené na hodnotách.

[!code-cpp[concrt-task-canceled#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_4.cpp)]

> [!CAUTION]
> Pokud neprojdete token zrušení do `task` konstruktoru nebo funkce [Concurrency:: create_task](reference/concurrency-namespace-functions.md#create_task) , tento úkol není zrušit. Kromě toho je nutné předat stejný token zrušení do konstruktoru všech vnořených úloh (tj. úloh, které jsou vytvořeny v těle jiné úlohy) pro zrušení všech úloh současně.

Je možné, že budete chtít spustit libovolný kód při zrušení tokenu zrušení. Pokud například uživatel klikne na tlačítko **Storno** v uživatelském rozhraní, aby operaci zrušil, můžete toto tlačítko zakázat, dokud uživatel nespustí jinou operaci. Následující příklad ukazuje, jak použít metodu [Concurrency:: cancellation_token:: register_callback](reference/cancellation-token-class.md#register_callback) k registraci funkce zpětného volání, která se spouští při zrušení tokenu zrušení.

[!code-cpp[concrt-task-cancellation-callback#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_5.cpp)]

Paralelismus [úkolu](../../parallel/concrt/task-parallelism-concurrency-runtime.md) dokumentu vysvětluje rozdíl mezi pokračováním založeným na hodnotách a úlohami. Pokud neposkytnete `cancellation_token` objekt pro úlohu pokračování, pokračování zdědí token zrušení z předchozí úlohy následujícími způsoby:

- Pokračování na základě hodnoty vždy zdědí token zrušení předchozí úlohy.

- Pokračování na základě úlohy nikdy nedědí token zrušení předchozí úlohy. Jediným způsobem, jak provést zrušení pokračování na základě úkolů, je explicitně předat token zrušení.

Tato chování nejsou ovlivněna chybnou úlohou (to znamená, že jedna vyvolá výjimku). V tomto případě je zrušené pokračování založené na hodnotách; pokračování založené na úlohách není zrušeno.

> [!CAUTION]
> Úkol, který je vytvořen v jiné úloze (jinými slovy, vnořená úloha), nedědí token zrušení nadřazené úlohy. Pouze pokračování založené na hodnotách zdědí token zrušení jeho předchozí úlohy.

> [!TIP]
> Použijte metodu [Concurrency:: cancellation_token:: none](reference/cancellation-token-class.md#none) při volání konstruktoru nebo funkce, která přebírá `cancellation_token` objekt a nechcete, aby se operace zrušit.

Můžete také poskytnout token zrušení konstruktoru `task_group` objektu nebo. `structured_task_group` Důležitým aspektem je, že podřízené skupiny úloh dědí tento token zrušení. Příklad, který demonstruje tento koncept pomocí funkce [Concurrency:: run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token) ke spuštění volání `parallel_for`, naleznete v části [zrušení paralelních algoritmů](#algorithms) dále v tomto dokumentu.

[[Nahoře](#top)]

#### <a name="cancellation-tokens-and-task-composition"></a>Tokeny zrušení a skládání úloh

Funkce [Concurrency:: when_all](reference/concurrency-namespace-functions.md#when_all) a [Concurrency:: when_any](reference/concurrency-namespace-functions.md#when_all) vám pomohou vytvořit více úkolů pro implementaci běžných vzorů. Tato část popisuje, jak tyto funkce fungují s tokeny zrušení.

Když zadáte token zrušení do `when_all` funkce a `when_any` , tato funkce zruší pouze v případě zrušení tohoto tokenu zrušení nebo když jedna z úkolů účastníka skončí ve zrušeném stavu nebo vyvolá výjimku.

`when_all` Funkce dědí token zrušení z každého úkolu, který sestaví celkovou operaci, když k ní neposkytnete token zrušení. Úloha, která je vrácena z `when_all` , je zrušena, když dojde ke zrušení některé z těchto tokenů, a nejméně jedna z úkolů účastníka ještě nebyla spuštěna nebo je spuštěná. K podobnému chování dojde, když jedna z úloh vyvolá výjimku – úkol, který je vrácen z `when_all` , se okamžitě zruší s touto výjimkou.

Modul runtime zvolí token zrušení pro úkol, který je vrácen `when_any` funkcí po dokončení této úlohy. Pokud žádný z úkolů účastníka nekončí v dokončeném stavu a jedna nebo více úloh vyvolá výjimku, je zvolena jedna z úloh, které vyvolaly, pro `when_any` dokončení a jeho token je vybrán jako token pro finální úkol. Pokud se v dokončeném stavu dokončí více než jeden úkol, úloha vrácená z `when_any` úlohy skončí v dokončeném stavu. Modul runtime se pokusí vybrat dokončenou úlohu, jejíž token není během dokončování zrušen, aby úloha, která je vrácena z `when_any` , nebyla okamžitě zrušena, i když jiné spuštěné úlohy mohou být dokončeny později.

[[Nahoře](#top)]

###  <a name="cancel"></a>Zrušení paralelní práce pomocí metody Cancel

Metody [Concurrency:: task_group:: Cancel](reference/task-group-class.md#cancel) a [Concurrency:: structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) nastaví skupinu úloh na stav zrušeno. Po volání `cancel`skupina úloh nespustí budoucí úkoly. `cancel` Metody mohou být volány více podřízenými úlohami. Zrušená úloha způsobí, že metody [Concurrency:: task_group:: wait](reference/task-group-class.md#wait) a [Concurrency:: structured_task_group:: wait](reference/structured-task-group-class.md#wait) vrátí [Concurrency:: Canceled](reference/concurrency-namespace-enums.md#task_group_status).

Pokud je skupina úloh zrušena, volání z každé podřízené úlohy do modulu runtime mohou aktivovat *bod přerušení*, což způsobí, že modul runtime vyvolá výjimku a zachytí typ interní výjimky pro zrušení aktivních úloh. Concurrency Runtime nedefinuje konkrétní body přerušení; mohou nastat při jakémkoli volání modulu runtime. Modul runtime musí zpracovat výjimky, které vyvolá, aby bylo možné provést zrušení. Proto neprovádějte zpracování neznámých výjimek v těle úlohy.

Pokud podřízená úloha provádí časově náročnou operaci a nevolá ji do modulu runtime, musí pravidelně kontrolovat zrušení a skončit včas. Následující příklad ukazuje jeden způsob, jak určit, kdy se práce zruší. Úloha `t4` zruší nadřazenou skupinu úloh, když dojde k chybě. Úloha `t5` občas`structured_task_group::is_canceling` volá metodu pro kontrolu zrušení. Pokud je nadřazená skupina úloh zrušena, úloha `t5` vytiskne zprávu a ukončí se.

[!code-cpp[concrt-task-tree#6](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_6.cpp)]

Tento příklad kontroluje zrušení každé 100. iterace smyčky Task.<sup></sup> Frekvence, se kterou kontrolujete zrušení, závisí na objemu práce, kterou vaše úloha provádí, a na tom, jak rychle potřebujete, aby úkoly reagovaly na zrušení.

Pokud nemáte přístup k objektu nadřazené skupiny úloh, zavolejte funkci [Concurrency:: is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) , která určí, zda je nadřazená skupina úloh zrušena.

Tato `cancel` metoda ovlivňuje pouze podřízené úlohy. Například `tg1` Pokud zrušíte zrušení skupiny úloh na ilustraci stromové struktury paralelní práce, budou ovlivněny všechny úkoly stromu (`t1`, `t2`, `t3` `t4`, a `t5`). Pokud zrušíte vnořenou skupinu úloh, `tg2`budou ovlivněny pouze úlohy `t5` `t4` a.

Při volání `cancel` metody jsou také zrušeny všechny podřízené skupiny úloh. Zrušení však nemá vliv na žádné nadřazené skupiny úloh v paralelní pracovní větvi. Následující příklady znázorňují to sestavením na ilustraci paralelní práce ve stromové struktuře.

První z těchto příkladů vytvoří pro úlohu `t4`pracovní funkci, která je podřízenou položkou skupiny `tg2`úloh. Pracovní funkce volá funkci `work` ve smyčce. Pokud jakékoli volání `work` selžou, úloha zruší svou nadřazenou skupinu úloh. Tím dojde k tomu `tg2` , že skupina úloh vstoupí do stavu zrušeno, ale neruší skupinu `tg1`úloh.

[!code-cpp[concrt-task-tree#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_7.cpp)]

Tento druhý příklad je podobný prvnímu, s tím rozdílem, že úloha zruší skupinu `tg1`úloh. To má vliv na všechny úlohy ve stromové `t2`struktuře `t3`( `t4``t1`,, `t5`, a).

[!code-cpp[concrt-task-tree#3](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_8.cpp)]

Třída `structured_task_group` není bezpečná pro přístup z více vláken. Proto podřízená úloha, která volá metodu svého nadřazeného `structured_task_group` objektu, vytvoří nespecifikované chování. Výjimkou z tohoto pravidla jsou `structured_task_group::cancel` metody a [Concurrency:: structured_task_group:: is_canceling](reference/structured-task-group-class.md#is_canceling) . Podřízená úloha může zavolat tyto metody pro zrušení nadřazené skupiny úloh a kontrolu zrušení.

> [!CAUTION]
>  I když můžete použít token zrušení ke zrušení práce provedené skupinou úloh, která běží jako `task` podřízený objekt objektu, nemůžete `task_group::cancel` použít metody nebo `structured_task_group::cancel` pro zrušení `task` objektů, které se spouštějí ve skupině úloh.

[[Nahoře](#top)]

###  <a name="exceptions"></a>Zrušení paralelní práce pomocí výjimek

Použití tokenů zrušení a `cancel` metoda jsou efektivnější než zpracování výjimek při zrušení paralelní pracovní struktury. Tokeny zrušení a `cancel` metoda zruší v horní části úlohu a všechny podřízené úlohy. Zpracování výjimek naopak funguje tak, jak je v dolní části, a musí každou podřízenou skupinu úloh zrušit nezávisle, protože se výjimka rozšíří nahoru. Téma [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md) vysvětluje, jak Concurrency Runtime používá výjimky k oznamování chyb. Ne všechny výjimky však naznačují chybu. Například algoritmus vyhledávání může při hledání výsledku zrušit jeho přidruženou úlohu. Jak již bylo zmíněno dříve, zpracování výjimek je méně efektivní než použití `cancel` metody pro zrušení paralelní práce.

> [!CAUTION]
>  Doporučujeme použít výjimky pro zrušení paralelní práce pouze v případě potřeby. Tokeny zrušení a metody skupiny `cancel` úloh jsou efektivnější a méně náchylné k chybě.

Pokud vyvoláte výjimku v těle pracovní funkce, kterou předáte do skupiny úloh, modul runtime uloží tuto výjimku a zařadí výjimku do kontextu, který čeká na dokončení skupiny úloh. Stejně jako u `cancel` metody modul runtime zahodí všechny úlohy, které ještě nebyly spuštěny, a nepřijímá nové úlohy.

Tento třetí příklad se podobá druhému, s tím rozdílem, že úloha `t4` vyvolá výjimku pro zrušení skupiny `tg2`úloh. Tento `try` příklad používá - `tg2` blok pro kontrolu zrušení v případě, že skupina úloh čeká na dokončení svých podřízených úkolů. `catch` Podobně jako v prvním příkladu Tato akce způsobí, že `tg2` skupina úloh vstoupí do stavu zrušeno, ale neruší skupinu `tg1`úloh.

[!code-cpp[concrt-task-tree#4](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_9.cpp)]

Tento čtvrtý příklad používá zpracování výjimek ke zrušení celého pracovního stromu. V příkladu se zachytí výjimka, když `tg1` skupina úloh počká na dokončení svých podřízených úkolů místo v případě, `tg2` že skupina úloh počká na své podřízené úlohy. Podobně jako v druhém příkladu to způsobí, že obě skupiny úkolů jsou ve `tg1` stromové struktuře, a `tg2`Pokud chcete zadat stornovaný stav.

[!code-cpp[concrt-task-tree#5](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_10.cpp)]

Vzhledem k tomu `structured_task_group::wait` , že metody avyvolávajívýjimku,kdyžpodřízenáúlohavyvolávýjimku,nedostaneteznichnávratovouhodnotu.`task_group::wait`

[[Nahoře](#top)]

##  <a name="algorithms"></a>Rušení paralelních algoritmů

Paralelní algoritmy v PPL, `parallel_for`například, sestavení ve skupinách úloh. Proto můžete použít mnoho stejných postupů pro zrušení paralelního algoritmu.

Následující příklady ilustrují několik způsobů zrušení paralelního algoritmu.

Následující příklad používá `run_with_cancellation_token` funkci k `parallel_for` volání algoritmu. `run_with_cancellation_token` Funkce přebírá token zrušení jako argument a volá zadanou pracovní funkci synchronně. Vzhledem k tomu, že paralelní algoritmy jsou vytvořeny na základě úkolů, dědí token zrušení nadřazené úlohy. `parallel_for` Proto může reagovat na zrušení.

[!code-cpp[concrt-cancel-parallel-for#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_11.cpp)]

Následující příklad používá metodu [Concurrency:: structured_task_group:: run_and_wait](reference/structured-task-group-class.md#run_and_wait) pro volání `parallel_for` algoritmu. `structured_task_group::run_and_wait` Metoda čeká na dokončení poskytnuté úlohy. `structured_task_group` Objekt umožňuje pracovní funkci úlohu zrušit.

[!code-cpp[concrt-task-tree#7](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_12.cpp)]

Tento příklad vytvoří následující výstup.

```Output
The task group status is: canceled.
```

Následující příklad používá zpracování výjimek ke zrušení `parallel_for` smyčky. Modul runtime zazařazuje výjimku do volajícího kontextu.

[!code-cpp[concrt-task-tree#9](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_13.cpp)]

Tento příklad vytvoří následující výstup.

```Output
Caught 50
```

Následující příklad používá logický příznak pro koordinaci zrušení ve `parallel_for` smyčce. Každý úkol je spuštěn, protože tento příklad nepoužívá `cancel` zpracování metody nebo výjimek ke zrušení celé sady úkolů. Proto tato technika může mít více výpočetních režijních nákladů než mechanismus zrušení.

[!code-cpp[concrt-task-tree#8](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_14.cpp)]

Každá metoda zrušení má své výhody oproti ostatním. Vyberte metodu, která vyhovuje vašim konkrétním potřebám.

[[Nahoře](#top)]

##  <a name="when"></a>Kdy použít zrušení

Použití zrušení je vhodné, pokud je možné včas ukončit každého člena skupiny souvisejících úloh. Existují však některé scénáře, kdy zrušení nemusí být vhodné pro vaši aplikaci. Například vzhledem k tomu, že zrušení úlohy je kooperativní, nebude celá sada úkolů zrušena, pokud je nějaký jednotlivý úkol zablokován. Například pokud jedna úloha ještě nebyla spuštěna, ale odblokuje jinou aktivní úlohu, nespustí se, pokud je skupina úloh zrušena. To může způsobit zablokování ve vaší aplikaci. Druhý příklad, kdy použití zrušení nemusí být vhodné, je při zrušení úlohy, ale jeho podřízená úloha provádí důležitou operaci, jako je například uvolnění prostředku. Vzhledem k tomu, že je při zrušení nadřazené úlohy zrušena celková sada úkolů, tato operace se neprovede. Příklad, který ukazuje tento bod, naleznete v tématu [Vysvětlení způsobu, jakým zrušení a zpracování výjimek ovlivňují oddíl zničení objektů](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) v tématu osvědčené postupy v tématu Knihovna paralelních vzorů.

[[Nahoře](#top)]

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Postupy: Přerušení paralelní smyčky pomocí zrušení](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)|Ukazuje, jak použít zrušení pro implementaci paralelního vyhledávacího algoritmu.|
|[Postupy: Přerušení paralelní smyčky pomocí zpracování výjimek](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|Ukazuje, jak použít `task_group` třídu pro zápis vyhledávacího algoritmu pro základní stromovou strukturu.|
|[Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Popisuje způsob, jakým modul runtime zpracovává výjimky, které jsou vyvolány skupinami úloh, odlehčenými úlohami a asynchronními agenty a jak reagovat na výjimky ve vašich aplikacích.|
|[Paralelní úkoly](../../parallel/concrt/task-parallelism-concurrency-runtime.md)|Popisuje, jak se úlohy týkají skupin úloh a jak můžete ve svých aplikacích používat nestrukturované a strukturované úlohy.|
|[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)|Popisuje paralelní algoritmy, které souběžně provádějí práci na kolekcích dat.|
|[Knihovna PPL (Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Poskytuje přehled knihovny paralelních vzorů.|

## <a name="reference"></a>Reference

[task – třída (Concurrency Runtime)](../../parallel/concrt/reference/task-class.md)

[cancellation_token_source – třída](../../parallel/concrt/reference/cancellation-token-source-class.md)

[cancellation_token – třída](../../parallel/concrt/reference/cancellation-token-class.md)

[task_group – třída](reference/task-group-class.md)

[structured_task_group – třída](../../parallel/concrt/reference/structured-task-group-class.md)

[parallel_for – funkce](reference/concurrency-namespace-functions.md#parallel_for)
