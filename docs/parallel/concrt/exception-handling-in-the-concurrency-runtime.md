---
title: "Zpracování výjimek v Concurrency Runtime | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- lightweight tasks, exception handling [Concurrency Runtime]
- exception handling [Concurrency Runtime]
- structured task groups, exception handling [Concurrency Runtime]
- agents, exception handling [Concurrency Runtime]
- task groups, exception handling [Concurrency Runtime]
ms.assetid: 4d1494fb-3089-4f4b-8cfb-712aa67d7a7a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 72cde17c0bcb6a3582305167e6358f761c16f248
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="exception-handling-in-the-concurrency-runtime"></a>Zpracování výjimek v Concurrency Runtime
Concurrency Runtime používá ke komunikaci různé druhy chyb pro zpracování výjimek C++. Tyto chyby patří neplatný použití za běhu, chyby za běhu, jako je například selhání získat prostředek a chyb vzniklých v pracovní funkce, které poskytnete úlohy a skupiny úloh. Pokud úlohy nebo skupina úloh vyvolá výjimku, modul runtime obsahuje této výjimky a zařazuje do kontextu, která čeká na úkolu nebo skupina úloh ukončíte. Modul runtime pro součásti, jako je například prosté úlohy a agenty, nespravuje výjimky za vás. V těchto případech je nutné implementovat vlastní mechanismus zpracování výjimek. Toto téma popisuje, jak modul runtime zpracovává výjimky, které jsou vyvolány úlohy, skupiny úloh, prosté úlohy a asynchronních agentů a jak reagovat na výjimky ve vašich aplikacích.  
  
## <a name="key-points"></a>Klíčové body  
  
-   Pokud úlohy nebo skupina úloh vyvolá výjimku, modul runtime obsahuje této výjimky a zařazuje do kontextu, která čeká na úkolu nebo skupina úloh ukončíte.  
  
-   Pokud je to možné, uzavřete každé volání [concurrency::task::get](reference/task-class.md#get) a [concurrency::task::wait](reference/task-class.md#wait) s `try` / `catch` bloku se budou zpracovávat chyby, které můžete obnovit z. Modul runtime ukončí aplikaci, pokud úloha vyvolá výjimku a byla zachycena výjimka není úlohou, jeden z jeho pokračování nebo hlavní aplikace.  
  
-   Na základě úkolů pokračování vždy spouští; nezáleží, jestli předchozí úloha dokončena úspěšně, došlo k výjimce, nebo byla zrušena. Pokud předchozí úloha vyvolá nebo zruší pokračování na základě hodnotu nejde spustit.  
  
-   Vzhledem k pokračování založený na úlohách vždy běží, zvažte, zda přidat pokračování založený na úlohách na konci vašeho pokračování řetězce. To může pomoct zajistit, aby váš kód zaznamenává všechny výjimky.  
  
-   Modul runtime vyvolá [concurrency::task_canceled](../../parallel/concrt/reference/task-canceled-class.md) při volání [concurrency::task::get](reference/task-class.md#get) a zrušení této úlohy.  

  
-   Modul runtime nespravuje výjimky pro prosté úlohy a agenty.  
  
##  <a name="top"></a>V tomto dokumentu  
  
- [Úlohy a pokračování](#tasks)  
  
- [Skupin úloh a paralelní algoritmy](#task_groups)  
  
- [Výjimky vyvolané modul Runtime](#runtime)  
  
- [Několik výjimek](#multiple)  
  
- [Zrušení](#cancellation)  
  
- [Prosté úlohy](#lwts)  
  
- [Asynchronní agenti](#agents)  
  
##  <a name="tasks"></a>Úlohy a pokračování  
 Tato část popisuje, jak modul runtime zpracovává výjimky, které jsou vyvolány [concurrency::task](../../parallel/concrt/reference/task-class.md) objekty a jejich pokračování. Další informace týkající se úloh a pokračování modelu najdete v tématu [paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
 Když vyvolat výjimku v těle pracovní funkci, která můžete předat `task` objektu modulu runtime ukládá této výjimky a zařazuje do kontextu, který volá [concurrency::task::get](reference/task-class.md#get) nebo [souběžnosti:: Task::wait –](reference/task-class.md#wait). Dokument [paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md) popisuje podle úloh a pokračování na základě hodnoty, ale chcete shrnout, na základě hodnoty pokračování přebírá parametr typu `T` a pokračování založený na úlohách přebírá parametr typu `task<T>`. Pokud úloha, která vyvolá má jeden nebo více na základě hodnoty pokračování, nejsou tyto pokračování naplánovat na spuštění. Následující příklad ilustruje toto chování:  

  
 [!code-cpp[concrt-eh-task#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_1.cpp)]  
  
 Pokračování založený na úlohách umožňuje zpracovat jakékoli výjimky vyvolané předchozí úlohou. Na základě úkolů pokračování vždy spouští; nezáleží, jestli úloha dokončena úspěšně, došlo k výjimce, nebo byla zrušena. Pokud úloha vyvolá výjimku, pokračování jeho založený na úlohách naplánovány ke spuštění. Následující příklad ukazuje úlohu, která vždy vyvolá. Úloha má dva pokračování; jeden je založená na hodnotu a druhá je založený na úlohách. Výjimka založený na úlohách vždy běží a proto může zachytit výjimku, která je vyvolána předchozí úlohou. Když příklad čeká na obou pokračování ukončíte, je vzhledem k tomu, kdy je vyvolána vždy výjimku úlohy znovu vyvolána výjimka `task::get` nebo `task::wait` je volána.  
  
 [!code-cpp[concrt-eh-continuations#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_2.cpp)]  
  
 Doporučujeme použít založený na úlohách pokračování zachycení výjimky, které budete moci zpracovat. Vzhledem k pokračování založený na úlohách vždy běží, zvažte, zda přidat pokračování založený na úlohách na konci vašeho pokračování řetězce. To může pomoct zajistit, aby váš kód zaznamenává všechny výjimky. Následující příklad ukazuje základní pokračování založené na hodnotu řetězce. Vyvolá třetí úloh v řetězu, a proto nejsou žádné pokračování na základě hodnoty, které následují ji spustit. Však finální pokračování je založený na úlohách a proto vždy spouští. Tento poslední pokračování zpracovává výjimku, která je vyvolána třetí úlohou.  
  
 Doporučujeme, abyste zachytit nejvíce výjimky, které můžete. Pokud nemáte konkrétní výjimky k zachycení, můžete vynechat tento poslední pokračování založený na úlohách. Jakékoli výjimky zůstanou neošetřených a můžete ukončit aplikaci.  
  
 [!code-cpp[concrt-eh-task-chain#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_3.cpp)]  
  
> [!TIP]
>  Můžete použít [concurrency::task_completion_event::set_exception](../../parallel/concrt/reference/task-completion-event-class.md) metodu pro výjimku přidružit k události dokončení úlohy. Dokument [paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md) popisuje [concurrency::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) třída podrobněji.  
  

 [Concurrency::task_canceled](../../parallel/concrt/reference/task-canceled-class.md) je typ výjimky důležité runtime, která má vztah k `task`. Modul runtime vyvolá `task_canceled` při volání `task::get` a zrušení této úlohy. (Pokud naopak `task::wait` vrátí [task_status::canceled](reference/concurrency-namespace-enums.md#task_group_status) a nevyvolá výjimku.) Můžete zachytit a zpracování této výjimky z pokračování založený na úlohách, nebo při volání `task::get`. Další informace o zrušení úlohy najdete v tématu [zrušení v knihovně PPL](cancellation-in-the-ppl.md).  

  
> [!CAUTION]
>  Nikdy throw `task_canceled` z vašeho kódu. Volání [concurrency::cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) místo.  
  
 Modul runtime ukončí aplikaci, pokud úloha vyvolá výjimku a byla zachycena výjimka není úlohou, jeden z jeho pokračování nebo hlavní aplikace. Pokud aplikace spadne, můžete nakonfigurovat Visual Studio pro přerušení, pokud jsou vyvolány výjimky jazyka C++. Po dokončení diagnostiky umístění neošetřené výjimky, použijte pokračování založeného na úloze se nezdařilo.  
  
 V části [výjimky vyvolané modulem Runtime](#runtime) v tomto dokumentu popisuje, jak pracovat s výjimky za běhu podrobněji.  
  
 [[Horní](#top)]  
  
##  <a name="task_groups"></a>Skupin úloh a paralelní algoritmy  

 Tato část popisuje, jak modul runtime zpracovává výjimky, které jsou vyvolány skupiny úloh. Tato část platí také pro paralelní algoritmy, jako [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for), protože tyto algoritmy sestavení na skupiny úloh.  
  
> [!CAUTION]
>  Ujistěte se, že rozumíte důsledky, které mají výjimky na závislé úlohy. Doporučené postupy o používání zpracování výjimek s úlohy nebo paralelní algoritmy, najdete v článku [Rady pro pochopení jak zrušení a výjimky zpracování odstranění objektu ovlivnit](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) část v osvědčené postupy paralelně Vzory téma v knihovně.  
  
 Další informace o skupinách úloh najdete v tématu [paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Další informace o paralelní algoritmy najdete v tématu [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).  

 Když vyvolat výjimku v těle pracovní funkci, která můžete předat [concurrency::task_group](reference/task-group-class.md) nebo [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) objektu modulu runtime ukládá této výjimky a je zařazuje na kontext, který volá [concurrency::task_group::wait](reference/task-group-class.md#wait), [concurrency::structured_task_group::wait](reference/structured-task-group-class.md#wait), [concurrency::task_group::run_and_wait](reference/task-group-class.md#run_and_wait), nebo [concurrency::structured_task_group::run_and_wait](reference/structured-task-group-class.md#run_and_wait). Modul runtime také zastaví všechny aktivní úlohy, které jsou ve skupině úloh (včetně těch v podřízené skupiny úloh) a zahodí se všechny úlohy, které nebyly ještě nezačala.  

  
 Následující příklad ukazuje základní struktura pracovní funkci, která vyvolá výjimku. V příkladu se používá `task_group` objekt tisknout hodnoty dva `point` objekty paralelně. `print_point` Pracovní funkce vytiskne hodnoty `point` objektu do konzoly. Pracovní funkce vyvolá výjimku, pokud je vstupní hodnota `NULL`. Modul runtime ukládá výjimku a zařazuje do kontextu, který volá `task_group::wait`.  
  
 [!code-cpp[concrt-eh-task-group#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_4.cpp)]  
  
 Tento příklad vytvoří následující výstup.  
  
```Output  
X = 15, Y = 30Caught exception: point is NULL.  
```  
  
 Úplný příklad, který používá zpracování výjimek v skupinu úloh, najdete v části [postupy: použití zpracování výjimek přerušení paralelní smyčky](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).  
  
 [[Horní](#top)]  
  
##  <a name="runtime"></a>Výjimky vyvolané modul Runtime  
 Volání modulu runtime může způsobit výjimku. Většina typů výjimek, s výjimkou [concurrency::task_canceled](../../parallel/concrt/reference/task-canceled-class.md) a [concurrency::operation_timed_out](../../parallel/concrt/reference/operation-timed-out-class.md), znamenat chybě programování. Tyto chyby jsou obvykle neopravitelné a proto by nemělo být zachycena nebo zpracovávaných kódu aplikace. Doporučujeme vám jenom catch nebo zpracovávat neopravitelné chyby v kódu aplikace, když potřebujete diagnostikovat programovací chyby. Ale Principy typů výjimek, které jsou definovány modulem runtime vám může pomoci diagnostikovat programovací chyby.  
  
 Zpracování mechanismus výjimek je stejný pro výjimky, které jsou vyvolány modulem runtime jako výjimky, které jsou vyvolány pracovních funkcí. Například [concurrency::receive](reference/concurrency-namespace-functions.md#receive) funkce vrátí `operation_timed_out` při neobdrží zprávu v zadaném časovém období. Pokud `receive` vyvolá výjimku ve funkci pracovní předáte pro skupinu úloh, modulu runtime ukládá této výjimky a zařazuje do kontextu, který volá `task_group::wait`, `structured_task_group::wait`, `task_group::run_and_wait`, nebo `structured_task_group::run_and_wait`.  
  
 Následující příklad používá [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algoritmus, který se spustí úlohy dvou paralelně. První úlohou vyčká pět sekund a pak odešle zprávu do vyrovnávací paměti zpráv. V druhé úloze používá `receive` funkce až tři sekundy pro příjem zprávy ze stejné vyrovnávací paměť zprávy. `receive` Funkce vrátí `operation_timed_out` neobdrží zprávu v časovém období.  
  
 [!code-cpp[concrt-eh-time-out#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_5.cpp)]  
  
 Tento příklad vytvoří následující výstup.  
  
```Output  
The operation timed out.  
```  
  
 Chcete-li zabránit abnormální ukončení aplikace, ujistěte se, že váš kód ošetřuje výjimky při volání do modulu runtime. Zpracování výjimek, také při volání do externí kód, který používá Concurrency Runtime, například knihovnu třetích stran.  
  
 [[Horní](#top)]  
  
##  <a name="multiple"></a>Několik výjimek  
 Pokud úloha nebo paralelní algoritmus obdrží několik výjimek, modul runtime zařazuje pouze jeden z těchto výjimek kontext volání. Modul runtime nezaručuje výjimky, které je zařazuje.  
  
 Následující příklad používá `parallel_for` algoritmus tisknout čísla do konzoly. Ho vyvolá výjimku, pokud vstupní hodnota je menší než minimální hodnota nebo větší než některé maximální hodnota. V tomto příkladu můžete několik pracovních funkcí vyvolat výjimku.  
  
 [!code-cpp[concrt-eh-multiple#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_6.cpp)]  
  
 Následuje příklad výstupu v tomto příkladu.  
  
```Output  
8293104567Caught exception: -5: the value is less than the minimum.  
```  
  
 [[Horní](#top)]  
  
##  <a name="cancellation"></a>Zrušení  
 Ne všechny výjimky znamenat chybu. Vyhledávací algoritmus může například použít výjimek zastavit přidružené úkolu, pokud najde výsledek. Další informace o tom, jak použijte mechanismy pro zrušení ve vašem kódu najdete v tématu [zrušení v knihovně PPL](../../parallel/concrt/cancellation-in-the-ppl.md).  
  
 [[Horní](#top)]  
  
##  <a name="lwts"></a>Prosté úlohy  
 Prosté úlohy je úkol, který můžete naplánovat přímo z [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) objektu. Prosté úlohy provádění menší režii než běžné úlohy. Modul runtime však nezachytí výjimky, které jsou vyvolány prosté úlohy. Místo toho je výjimka zachycena obslužná rutina neošetřených výjimek, které ve výchozím nastavení tento proces se ukončuje. Proto použijte vhodný mechanismus zpracování chyb v aplikaci. Další informace o prosté úlohy najdete v tématu [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  
 [[Horní](#top)]  
  
##  <a name="agents"></a>Asynchronní agenti  
 Prosté úlohy, jako je modul runtime nespravuje výjimky, které jsou vyvolány asynchronních agentů.  
  
 Následující příklad ukazuje jeden ze způsobů zpracování výjimek ve třídě, která je odvozena z [concurrency::agent](../../parallel/concrt/reference/agent-class.md). Tento příklad definuje `points_agent` třídy. `points_agent::run` Metoda čtení `point` objekty z vyrovnávací paměti zpráv a vypíše je do konzoly. `run` Metoda vyvolá výjimku, pokud obdrží `NULL` ukazatel.  
  
 `run` Metoda obklopuje všechnu práci v `try` - `catch` bloku. `catch` Bloku ukládá do vyrovnávací paměti zpráv výjimku. Aplikace zkontroluje, zda agent došlo k chybě ve čtení z této vyrovnávací paměti po dokončení agenta.  
  
 [!code-cpp[concrt-eh-agents#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_7.cpp)]  
  
 Tento příklad vytvoří následující výstup.  
  
```Output  
X: 10 Y: 20  
X: 20 Y: 30  
error occurred in agent: point must not be NULL  
the status of the agent is: done  
```  
  
 Protože `try` - `catch` bloku existuje mimo `while` smyčky, agent ukončí zpracování, pokud se setká první chyba. Pokud `try` - `catch` bloku byl uvnitř `while` smyčky, agent bude pokračovat ve potom, co dojde k chybě.  
  
 Tento příklad výjimky ukládá do vyrovnávací paměti zpráv tak, aby další komponentou můžete monitorovat agenta chyby při jeho spuštění. Tento příklad používá [concurrency::single_assignment](../../parallel/concrt/reference/single-assignment-class.md) objekt pro uložení k chybě. V případě, kdy agent zpracovává více výjimek `single_assignment` třída ukládá pouze první zprávu, která je předána do ní. Chcete-li uložit pouze poslední výjimka, použijte [concurrency::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) třídy. Chcete-li uložit všechny výjimky, použijte [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) třídy. Další informace o těchto bloky zpráv najdete v tématu [asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md).  
  
 Další informace o asynchronních agentů najdete v tématu [asynchronních agentů](../../parallel/concrt/asynchronous-agents.md).  
  
 [[Horní](#top)]  
  
##  <a name="summary"></a>Souhrn  
 [[Horní](#top)]  
  
## <a name="see-also"></a>Viz také  
 [Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)   
 [Funkční paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)   
 [Zrušení v knihovně PPL](cancellation-in-the-ppl.md)   
 [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)

