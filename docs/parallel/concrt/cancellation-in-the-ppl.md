---
title: Zrušení v knihovně PPL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parallel algorithms, canceling [Concurrency Runtime]
- canceling parallel algorithms [Concurrency Runtime]
- parallel tasks, canceling [Concurrency Runtime]
- cancellation in the PPL
- parallel work trees [Concurrency Runtime]
- canceling parallel tasks [Concurrency Runtime]
ms.assetid: baaef417-b2f9-470e-b8bd-9ed890725b35
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a0c74ad5877a5b490414d96bf0f13b32309a21a
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="cancellation-in-the-ppl"></a>Zrušení v knihovně PPL
Tento dokument popisuje roli zrušení v paralelní vzory knihovny (PPL), jak zrušit paralelní práce a jak určit, kdy je zrušena paralelní práce.  
  
> [!NOTE]
>  Modul runtime používá výjimek implementovat zrušení. Catch nebo zpracování těchto výjimek v kódu. Kromě toho doporučujeme napsat kód výjimky bezpečných v těla funkce pro vaše úkoly. Například můžete použít *prostředků pořízení je inicializace* (RAII) vzor zajistit prostředky jsou při je vyvolána výjimka v těle úlohy správně zpracována. Úplný příklad, který používá vzor RAII k vyčištění prostředků v úlohu možné zrušit, najdete v části [návod: odstranění práce z uživatelského rozhraní vláken](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md).  
  
## <a name="key-points"></a>Klíčové body  
  
-   Zrušení je spolupráci a zahrnuje koordinovat kód, který požaduje zrušení a úloha, která reaguje na zrušení.  
  
-   Pokud je to možné, slouží ke zrušení pracovní zrušení tokenů. [Concurrency::cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) třída definuje token zrušení.  
  

-   Pokud použijete zrušení tokenů, použijte [concurrency::cancellation_token_source::cancel](reference/cancellation-token-source-class.md#cancel) metoda zahájíte zrušení a [concurrency::cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) funkce reagovat na zrušení. Použití [concurrency::cancellation_token::is_canceled](reference/cancellation-token-class.md#is_canceled) metoda zkontrolujte, zda jiná úloha vyžaduje zrušení.
  
-   Zrušení neproběhne okamžitě. I když nový pracovní neběží, pokud úlohy nebo skupina úloh byla zrušena, musí aktivní prací. Zkontrolujte a reagovat na zrušení.  
  
-   Na základě hodnoty pokračování dědí tokenu zrušení jeho předchozí úlohou. Pokračování založený na úlohách nikdy dědí tokenu svou předchozí úlohou.  
  
-   Použití [concurrency::cancellation_token:: žádné](reference/cancellation-token-class.md#none) metoda při volání konstruktoru nebo funkce, která přebírá `cancellation_token` objektu, ale nechcete, aby se zrušit operaci. Navíc pokud se nepředají token zrušení pro [concurrency::task](../../parallel/concrt/reference/task-class.md) konstruktor nebo [concurrency::create_task](reference/concurrency-namespace-functions.md#create_task) funkce, tuto úlohu je nevratné.  


  
##  <a name="top"></a> V tomto dokumentu  
  
- [Paralelní pracovní stromy](#trees)  
  
- [Zrušení paralelních úloh](#tasks)  
  
    - [Použití Token zrušení pro zrušení paralelní práce](#tokens)  
  
    - [Pomocí Storno metodu zrušit paralelní práce](#cancel)  
  
    - [Použití výjimek zrušit paralelní práce](#exceptions)  
  
- [Zrušení paralelních algoritmů](#algorithms)  
  
- [Kdy nepoužívat zrušení](#when)  
  
##  <a name="trees"></a> Paralelní pracovní stromy  
 Knihovně PPL používá ke správě podrobných úlohy a výpočty úlohy a skupiny úloh. Vnoření skupin úloh do formuláře *stromy* paralelní práce. Následující obrázek znázorňuje stromu paralelní práce. V tomto obrázku `tg1` a `tg2` představují skupiny úloh; `t1`, `t2`, `t3`, `t4`, a `t5` představují práci, kterou provést skupiny úloh.  
  
 ![Paralelní pracovní stromu](../../parallel/concrt/media/parallelwork_trees.png "parallelwork_trees")  
  
 Následující příklad ukazuje kód, který je potřeba vytvořit stromu na obrázku. V tomto příkladu `tg1` a `tg2` jsou [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) objekty; `t1`, `t2`, `t3`, `t4`, a `t5` jsou [concurrency::task_handle](../../parallel/concrt/reference/task-handle-class.md) objekty.  
  
 [!code-cpp[concrt-task-tree#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_1.cpp)]  
  
 Můžete také [concurrency::task_group](reference/task-group-class.md) třídy za účelem vytvoření podobné pracovní větev. [Concurrency::task](../../parallel/concrt/reference/task-class.md) třída také podporuje představu o stromu práce. Ale `task` stromu je závislost stromu. V `task` stromu budoucí funguje dokončena po aktuální pracovní. Ve stromu skupiny úloh interní pracovní dokončení před vnější práci. Další informace o rozdílech mezi úlohy a skupin úloh naleznete v tématu [paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
 [[Horní](#top)]  
  
##  <a name="tasks"></a> Zrušení paralelních úloh  

 Chcete-li zrušit paralelní práce několika způsoby. Upřednostňovaný způsob je pomocí tokenu zrušení. Skupiny úloh také podporu [concurrency::task_group::cancel](reference/task-group-class.md#cancel) metoda a [concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel) metoda. Posledním způsobem je vyvolána výjimka v těle funkce pracovních úloh. Bez ohledu na to, jakou metodu zvolíte Pochopte, že zrušení neproběhne okamžitě. I když nový pracovní neběží, pokud úlohy nebo skupina úloh byla zrušena, musí aktivní prací. Zkontrolujte a reagovat na zrušení.  

  
 Další příklady, které zrušení paralelních úloh najdete v tématu [návod: připojení pomocí úloh a žádostí XML HTTP](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md), [postupy: použití zrušení přerušení paralelní smyčky](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md), a [postupy: použití Zpracování přerušení paralelní smyčky výjimek](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).  
  
###  <a name="tokens"></a> Použití Token zrušení pro zrušení paralelní práce  
 `task`, `task_group`, A `structured_task_group` třídy podporují zrušení prostřednictvím zrušení tokenů. Definuje knihovně PPL [concurrency::cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md) a [concurrency::cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) třídy pro tento účel. Použijete-li zrušit pracovní token zrušení, modul runtime nespustí nové práci, která si předplatí tento token. Můžete použít pracovní, která je již aktivní [is_canceled –](../../parallel/concrt/reference/cancellation-token-class.md#is_canceled) – členská funkce ke sledování token zrušení a zastavit, když je to možné.  
  

 Chcete-li zahájit zrušení, volejte [concurrency::cancellation_token_source::cancel](reference/cancellation-token-source-class.md#cancel) metoda. Můžete reagovat na zrušení těmito způsoby:  
  
-   Pro `task` objekty, používají [concurrency::cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) funkce. `cancel_current_task` Zruší aktuální úlohy a všechny jeho pokračování na základě hodnoty. (Nezruší zrušení *tokenu* který je přidružen úlohu nebo jeho pokračování.)  
  
-   U skupin úloh a paralelní algoritmy, použijte [concurrency::is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) funkce ke zjišťování zrušení a vracet co nejdříve z textu úloh funkce vrátí hodnotu `true`. (Nevolejte `cancel_current_task` ze skupiny úloh.)  

  
 Následující příklad ukazuje první základní vzor pro zrušení úlohy. Úloha textu příležitostně zkontroluje zrušení uvnitř smyčku.  
  
 [!code-cpp[concrt-task-basic-cancellation#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_2.cpp)]  
  
 `cancel_current_task` Funkce vrátí; proto není potřeba explicitně vrátit z aktuální smyčky nebo funkce.  
  
> [!TIP]

>  Alternativně můžete volat [concurrency::interruption_point](reference/concurrency-namespace-functions.md#interruption_point) funkce místo `cancel_current_task`.  
  
 Je důležité k volání `cancel_current_task` když jste reagovat na zrušení vzhledem k tomu, že přechází úlohu zrušené stavu. Pokud jste již v rané fázi vrátí místo volání `cancel_current_task`operaci přechází do stavu dokončení a spouštějí žádné pokračování na základě hodnoty.  
  
> [!CAUTION]
>  Nikdy throw `task_canceled` z vašeho kódu. Volání `cancel_current_task` místo.  
  
 Při ukončení úlohy v zrušené stavu, [concurrency::task::get](reference/task-class.md#get) vyvolá metoda [concurrency::task_canceled](../../parallel/concrt/reference/task-canceled-class.md). (Pokud naopak [concurrency::task::wait](reference/task-class.md#wait) vrátí [task_status::canceled](reference/concurrency-namespace-enums.md#task_group_status) a nevyvolá výjimku.) Následující příklad ilustruje toto chování pro pokračování založený na úlohách. Pokračování založeného na úloze je volána vždy, i když se zruší předchozí úloha.  

  
 [!code-cpp[concrt-task-canceled#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_3.cpp)]  
  
 Vzhledem k tomu, že na základě hodnoty pokračování zdědí tokenu jejich předchozí úlohou, pokud byly vytvořeny s explicitní token, pokračování okamžitě zadejte zrušené stavu i v případě, že předchozí úloha stále probíhá. Jakékoli výjimky vyvolané předchozí úlohou po zrušení není tedy rozšíří do úloh pokračování. Zrušení vždy přepíše stav předchozí úlohou. V následujícím příkladu se podobá předchozí, ale ukazuje chování pro pokračování na základě hodnoty.  
  
 [!code-cpp[concrt-task-canceled#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_4.cpp)]  
  
> [!CAUTION]

>  Pokud se nepředají token zrušení pro `task` konstruktor nebo [concurrency::create_task](reference/concurrency-namespace-functions.md#create_task) funkce, tuto úlohu je nevratné. Kromě toho je nutné předat stejný token zrušení do konstruktoru všech vnořených úloh (to znamená, úlohy, které jsou vytvořené v těle jiná úloha) současně zrušit všechny úlohy.  
  
 Můžete chtít spustit libovolný kód, když se zruší token zrušení. Například pokud uživatel vybere **zrušit** tlačítko na uživatelské rozhraní na tlačítko Storno, může zakázat toto tlačítko, dokud uživatel spustí jiná operace. Následující příklad ukazuje, jak používat [concurrency::cancellation_token::register_callback](reference/cancellation-token-class.md#register_callback) metody pro registraci funkce zpětného volání, která se spouští při zrušení token zrušení.  

  
 [!code-cpp[concrt-task-cancellation-callback#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_5.cpp)]  
  
 Dokument [paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md) najdete vysvětlení rozdílu mezi pokračování založené na hodnotu a založený na úlohách. Pokud nezadáte `cancellation_token` objekt úkolů pokračování, pokračování dědí token zrušení z předchozí úlohou následujícími způsoby:  
  
-   Pokračování založené na hodnotu vždy dědí tokenu zrušení předchozí úlohou.  
  
-   Pokračování založený na úlohách nikdy dědí tokenu zrušení předchozí úlohou. Jediný způsob, jak provést pokračování založený na úlohách možné zrušit je explicitně předat token zrušení.  
  
 Tyto chování nemá vliv chybný úkolu (to znamená, jeden, který vyvolá výjimku). V takovém případě je zrušena pokračování na základě hodnoty; pokračování založený na úlohách není zrušena.  
  
> [!CAUTION]
>  Úloha, která je vytvořen v jiné úloze (jinými slovy, vnořené úlohy) nedědí token zrušení úlohy nadřazené. Pouze na základě hodnoty pokračování dědí tokenu zrušení jeho předchozí úlohou.  
  
> [!TIP]

>  Použití [concurrency::cancellation_token:: žádné](reference/cancellation-token-class.md#none) metoda při volání konstruktoru nebo funkce, která přebírá `cancellation_token` objektu a vy nechcete, aby se zrušit operaci.  
  
 Můžete zadat také token zrušení do konstruktoru objektu `task_group` nebo `structured_task_group` objektu. Důležitým aspektem to je, že podřízené skupiny úloh zdědí tento token zrušení. Pro příklad, který ukazuje tento koncept pomocí [concurrency::run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token) funkce spustit na volání `parallel_for`, najdete v části [zrušení paralelních algoritmů](#algorithms) později v tomto dokument.  
  
 [[Horní](#top)]  
  
#### <a name="cancellation-tokens-and-task-composition"></a>Tokeny zrušení a skládání úloh  

 [Souběžnosti:: HYPERLINK "http://msdn.microsoft.com/library/system.threading.tasks.task.whenall(v=VS.110).aspx" when_all –](reference/concurrency-namespace-functions.md#when_all) a [concurrency::when_any](reference/concurrency-namespace-functions.md#when_all) funkce vám může pomoct vytvořit více úloh k implementaci běžných vzorů. Tato část popisuje, jak tyto funkce fungují s zrušení tokenů.  
  
 Když zadáte token zrušení pro buď `when_all` a `when_any` fungovat, že funkce zruší jenom v případě, že token zrušení byla zrušena, nebo pokud jeden účastníka úloh končí ve stavu, zrušené nebo vyvolá výjimku.  
  
 `when_all` Funkce zdědí každý úkol, který vytvoří celou operaci, když nezadáte token zrušení k němu token zrušení. Úloha, která je vrácena z `when_all` se zruší, pokud všechny tyto tokeny zrušena a alespoň jeden z účastníků úlohy ještě nezačala nebo je spuštěná. K podobné chování dochází při jednu z úloh vyvolá výjimku - úloha, která je vrácena z `when_all` se okamžitě zruší, k této výjimce.  
  
 Modul runtime rozhodne token zrušení pro úlohu, která je vrácena z `when_any` fungovat po dokončení této úlohy. Pokud žádná z účastnické úlohy dokončíte ve stavu dokončení a vyvolá výjimku, jeden nebo více úloh, jednu z úloh, které vrátil je zvolen k dokončení `when_any` a jeho token je zvolen jako token pro konečnou úlohu. Je-li více než jeden úkol dokončí v dokončené uveďte, úloha, která je vrácena z `when_any` končí úloha ve stavu dokončení. Modul runtime pokusí vyberte dokončené úlohy, jejichž token není zrušena v době dokončení tak, aby úloha, která je vrácena z `when_any` není zrušena okamžitě, přestože jiných provádění úkolů může dokončit později.  
  
 [[Horní](#top)]  
  
###  <a name="cancel"></a> Pomocí Storno metodu zrušit paralelní práce  

 [Concurrency::task_group::cancel](reference/task-group-class.md#cancel) a [concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel) metody nastavit skupinu úkolů zrušené stav. Po zavolání metody `cancel`, skupině úloh nespustí budoucí úlohy. `cancel` Metody je možné volat v několika podřízené úlohy. Zrušené úlohy [concurrency::task_group::wait](reference/task-group-class.md#wait) a [concurrency::structured_task_group::wait](reference/structured-task-group-class.md#wait) metody vrátit [concurrency::canceled](reference/concurrency-namespace-enums.md#task_group_status).  

  
 Pokud je zrušena skupinu úloh, můžete aktivovat volání z každé podřízené úlohy do modulu runtime *bod přerušení*, což způsobí, že modulu runtime throw a catch typ vnitřní výjimky pro zrušení aktivních úloh. Concurrency Runtime nedefinuje specifické přerušení body; mohou probíhat v žádném volání modulu runtime. Modul runtime musí zpracování výjimek, které vyvolává za účelem provedení zrušení. Proto není zpracování neznámé výjimek v těle úlohy.  
  
 Pokud podřízené úlohy provede časově náročná operace a nevyvolá do modulu runtime, musí pravidelně kontrolovat zrušení a ukončete včas. Následující příklad ukazuje jeden způsob jak určit, kdy je zrušena pracovní. Úloha `t4` zruší nadřazenou skupinu úloh, když dojde k chybě. Úloha `t5` příležitostně volá `structured_task_group::is_canceling` umožňuje kontrolu pro zrušení. Pokud je zrušena nadřazenou skupinu úloh, úkolů `t5` vytiskne zprávu a ukončí.  
  
 [!code-cpp[concrt-task-tree#6](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_6.cpp)]  
  
 Tento příklad zkontroluje pro zrušení na každých 100<sup>tý</sup> iteraci smyčky úloh. Frekvence, ve kterém můžete kontrolovat pro zrušení závisí na množství práce, kterou vaše úloha provede a jak rychle potřebujete pro úlohy reagovat na zrušení.  
  
 Pokud nemáte přístup k nadřazený objekt skupiny úloh, zavolejte [concurrency::is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) funkce k určení, zda je zrušená nadřazené skupiny úloh.  

  
 `cancel` Metoda má vliv pouze na podřízené úlohy. Například, pokud zrušíte skupiny úloh `tg1` obrázek stromu paralelní práce, všechny úlohy ve stromové struktuře (`t1`, `t2`, `t3`, `t4`, a `t5`) se vztahuje. Pokud zrušíte skupině vnořené úlohy `tg2`, pouze úlohy `t4` a `t5` vliv.  
  
 Při volání `cancel` metoda, všechny podřízené úlohy skupiny také došlo ke zrušení. Zrušení neovlivní žádné nadřazených položek skupiny úloh ve stromu paralelní práce. Následující příklady ukazují to podle budovy na obrázku stromu paralelní práce.  
  
 První z těchto příkladech vytvoří pracovní funkci pro úlohu `t4`, která je podřízená této skupiny úloh `tg2`. Pracovní funkce volá funkci `work` ve smyčce. Pokud žádné volat na `work` selže, úloha zruší své nadřazené skupiny úloh. To způsobí, že skupina úkolů `tg2` k zadání zrušené stavu, ale nezruší skupina úkolů `tg1`.  
  
 [!code-cpp[concrt-task-tree#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_7.cpp)]  
  
 Tato druhém příkladu vypadá takto: první z nich, s tím rozdílem, že úloha zruší skupina úkolů `tg1`. Tato akce ovlivní všechny úlohy ve stromové struktuře (`t1`, `t2`, `t3`, `t4`, a `t5`).  
  
 [!code-cpp[concrt-task-tree#3](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_8.cpp)]  
  
 `structured_task_group` Třída není bezpečné pro přístup z více vláken. Proto podřízené úlohy, který volá metodu nadřazené `structured_task_group` objekt vytváří neurčené chování. Výjimky pro toto pravidlo jsou `structured_task_group::cancel` a [concurrency::structured_task_group::is_canceling](reference/structured-task-group-class.md#is_canceling) metody. Tyto metody zrušit nadřazené skupině úloh a zkontrolujte pro zrušení můžete volat podřízené úlohy.  

 
> [!CAUTION]
>  I když používáte token zrušení zrušit práci, kterou provádí skupinu úkolů, který běží jako podřízenou `task` objektu, nemůžete použít `task_group::cancel` nebo `structured_task_group::cancel` metody zrušit `task` objekty, které spustit ve skupině úloh.  
  
 [[Horní](#top)]  
  
###  <a name="exceptions"></a> Použití výjimek zrušit paralelní práce  
 Použití zrušení tokenů a `cancel` metoda jsou efektivnější než zpracování na zrušení paralelní práce stromu výjimek. Zrušení tokenů a `cancel` metoda zrušení úlohy a všechny podřízené úlohy způsobem shora dolů. Zpracovávání výjimek v jazyce naopak funguje způsobem zdola nahoru a musí zrušit každou podřízenou skupinu úloh nezávisle jako výjimka šíří směrem nahoru. Téma [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md) vysvětluje, jak Concurrency Runtime používá ke komunikaci chyby výjimky. Ne všechny výjimky však znamenat chybu. Například vyhledávacího algoritmu může zrušit jeho přidružených úloh, pokud najde výsledek. Jak je uvedeno nahoře, výjimek je však méně efektivní než při použití `cancel` metoda zrušit paralelní práce.  
  
> [!CAUTION]
>  Doporučujeme používat výjimky zrušit paralelní práce pouze v případě potřeby. Zrušení tokenů a skupině úloh `cancel` metody jsou efektivnější a méně náchylné k chybám.  
  
 Pokud je vyvolána výjimka v těle pracovní funkce, kterou předáte pro skupinu úloh, modulu runtime ukládá této výjimky a zařazuje výjimka, která má kontext, který se čeká na skupině úloh ukončíte. Stejně jako u `cancel` metoda, modul runtime, zahodí se všechny úlohy, které nebyly ještě nezačala a nepřijímá nové úkoly.  
  
 Tento příklad třetí podobá druhý, s výjimkou této úlohy `t4` vyvolá výjimku pro zrušení skupiny úloh `tg2`. Tento příklad používá `try` - `catch` bloku ke kontrole pro zrušení při skupiny úloh `tg2` čeká na dokončení úkolů jeho podřízené. Podobně jako v prvním příkladu, to způsobí, že skupina úkolů `tg2` k zadání zrušené stavu, ale nezruší skupina úkolů `tg1`.  
  
 [!code-cpp[concrt-task-tree#4](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_9.cpp)]  
  
 Zpracovávání výjimek v jazyce zrušit stromu celou pracovní tomto čtvrtý příkladu. V příkladu zachytí výjimky při úkolů skupiny `tg1` čeká na dokončení místo při jeho podřízených úkolů úkolů skupiny `tg2` čeká na jeho podřízené úlohy. Jako druhém příkladu to způsobí, že obě úlohy skupiny ve stromu `tg1` a `tg2`, zadat zrušené stavu.  
  
 [!code-cpp[concrt-task-tree#5](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_10.cpp)]  
  
 Protože `task_group::wait` a `structured_task_group::wait` metody výjimku při podřízené úlohy vyvolá výjimku, neobdržíte návratovou hodnotu z nich.  
  
 [[Horní](#top)]  
  
##  <a name="algorithms"></a> Zrušení paralelních algoritmů  
 Paralelní algoritmy v knihovně PPL, například `parallel_for`, sestavení na skupiny úloh. Proto můžete řadu se stejné techniky zrušit paralelní algoritmus.  
  
 Následující příklady ilustrují několik způsobů, jak zrušit paralelní algoritmus.  
  
 Následující příklad používá `run_with_cancellation_token` funkce k volání `parallel_for` algoritmus. `run_with_cancellation_token` Funkce přijme token jako argument zrušení a zavolá funkci zadané pracovní synchronně. Protože paralelní algoritmy jsou založena na úlohy, dědí token zrušení úlohy nadřazené. Proto `parallel_for` může reagovat na zrušení.  
  
 [!code-cpp[concrt-cancel-parallel-for#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_11.cpp)]  
  

 Následující příklad používá [concurrency::structured_task_group::run_and_wait](reference/structured-task-group-class.md#run_and_wait) metoda k volání `parallel_for` algoritmus. `structured_task_group::run_and_wait` Metoda čeká na dokončení zadané úlohy. `structured_task_group` Objektu umožňuje pracovní funkce se zrušit úlohy.  
  
 [!code-cpp[concrt-task-tree#7](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_12.cpp)]  
  
 Tento příklad vytvoří následující výstup.  
  
```Output  
The task group status is: canceled.  
```  
  
 Následující příklad používá výjimek zrušit `parallel_for` smyčky. Modul runtime zařazuje výjimka, která má kontext volání.  
  
 [!code-cpp[concrt-task-tree#9](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_13.cpp)]  
  
 Tento příklad vytvoří následující výstup.  
  
```Output  
Caught 50  
```  
  
 Následující příklad používá ke koordinaci zrušení v logický příznak `parallel_for` smyčky. Spustí každý úkol, protože v tomto příkladu se nepoužívá `cancel` metoda nebo výjimky zpracování zrušit celou sadu úloh. Proto tato technika může mít větší výpočetní režijní náklady než mechanismus zrušení.  
  
 [!code-cpp[concrt-task-tree#8](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_14.cpp)]  
  
 Každá metoda zrušení má oproti ostatním výhod. Zvolte metodu, která odpovídá vašim konkrétním potřebám.  
  
 [[Horní](#top)]  
  
##  <a name="when"></a> Kdy nepoužívat zrušení  
 Použití zrušení je vhodné, když každého člena skupiny souvisejících úloh můžete ukončit včas. Je však několik scénářů, kde zrušení nemusí být vhodné pro vaši aplikaci. Například zrušení úlohy je spolupráci, a proto celou sadu úloh nebude zrušit, pokud je blokovaný všechny jednotlivé úlohy. Například pokud ještě nezačala jeden úkol, ale jeho odblokuje aktivní jiná úloha, se nespustí, pokud došlo ke zrušení skupiny úloh. To může způsobit zablokování v aplikaci. Je druhý například použití zrušení kde nemusí být vhodné v případě, že úloha se zruší, ale důležité operace, jako je například uvolnění prostředku provede jeho podřízené úlohy. Protože celou sadu úloh se zruší, když nadřazený úkol je zrušeno, nebude provést tuto operaci. Příklad, který znázorňuje tento bod, najdete v článku [Rady pro pochopení jak zrušení a výjimky zpracování odstranění objektu ovlivnit](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) část v osvědčené postupy v tématu Parallel Library vzory.  
  
 [[Horní](#top)]  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: Přerušení paralelní smyčky pomocí zrušení](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)|Ukazuje, jak použít k implementaci paralelního vyhledávacího algoritmu zrušení.|  
|[Postupy: Přerušení paralelní smyčky pomocí zpracování výjimek](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|Ukazuje, jak používat `task_group` třída pro psaní vyhledávacího algoritmu pro základní stromové struktury.|  
|[Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Popisuje, jak modul runtime zpracovává výjimky, které jsou vyvolány skupiny úloh, prosté úlohy a asynchronních agentů a jak reagovat na výjimky ve vašich aplikacích.|  
|[Funkční paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md)|Popisuje, jak úlohy vztahují k skupin úloh a použití strukturovaných a nestrukturovaných úloh ve svých aplikacích.|  
|[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)|Popisuje paralelní algoritmy, které souběžně provádět práci na kolekce dat|  
|[Knihovna PPL (Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Poskytuje přehled Parallel Library vzory.|  
  
## <a name="reference"></a>Odkaz  
 [task – třída (Concurrency Runtime)](../../parallel/concrt/reference/task-class.md)  
  
 [cancellation_token_source – třída](../../parallel/concrt/reference/cancellation-token-source-class.md)  
  
 [cancellation_token – třída](../../parallel/concrt/reference/cancellation-token-class.md)  
  
 [task_group – třída](reference/task-group-class.md)  
  
 [structured_task_group – třída](../../parallel/concrt/reference/structured-task-group-class.md)  

 [parallel_for – funkce](reference/concurrency-namespace-functions.md#parallel_for)


