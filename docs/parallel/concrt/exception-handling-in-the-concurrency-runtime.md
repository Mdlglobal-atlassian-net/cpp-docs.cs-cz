---
title: Zpracování výjimek v Concurrency Runtime
ms.date: 11/04/2016
helpviewer_keywords:
- lightweight tasks, exception handling [Concurrency Runtime]
- exception handling [Concurrency Runtime]
- structured task groups, exception handling [Concurrency Runtime]
- agents, exception handling [Concurrency Runtime]
- task groups, exception handling [Concurrency Runtime]
ms.assetid: 4d1494fb-3089-4f4b-8cfb-712aa67d7a7a
ms.openlocfilehash: 8239913c369605503134a9ea4c99789528911868
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272630"
---
# <a name="exception-handling-in-the-concurrency-runtime"></a>Zpracování výjimek v Concurrency Runtime

Modulu Runtime souběžnosti používá ke komunikaci různé druhy chyb zpracování výjimek jazyka C++. Tyto chyby patří neplatné použití modulu runtime, chyby za běhu, jako je například selhání získání prostředku a chyby, ke kterým dochází v pracovní funkce, které poskytují úloh a skupin úloh. Pokud úkol nebo úkol skupiny vyvolá výjimku, modul runtime obsahuje tuto výjimku a zařadí do kontextu, který se čeká na úkolu nebo skupiny úkolů na dokončení. Komponent, jako jsou jednoduché úlohy a agentů modul runtime nedokáže spravovat výjimky za vás. V těchto případech je nutné implementovat vlastní mechanismus zpracování výjimek. Toto téma popisuje, jak modul runtime zpracovává výjimky, které jsou vyvolány pomocí úloh, úkolů skupiny, lehkých úloh a asynchronních agentů a jak reagovat na výjimky ve vašich aplikacích.

## <a name="key-points"></a>Klíčové body

- Pokud úkol nebo úkol skupiny vyvolá výjimku, modul runtime obsahuje tuto výjimku a zařadí do kontextu, který se čeká na úkolu nebo skupiny úkolů na dokončení.

- Pokud je to možné, před a za všechna volání [Concurrency::Task:: Get](reference/task-class.md#get) a [Concurrency::Task:: wait](reference/task-class.md#wait) s `try` / `catch` bloku zpracování chyb, které se dají obnovit z. Modul runtime ukončí aplikaci, pokud úloha vyvolá výjimku a byla zachycena výjimka není úloha, některou jeho pokračování nebo hlavní aplikace.

- Pokračování podle úloh vždy spuštěn; nezáleží, jestli předchozí úloha dokončena úspěšně, došlo k výjimce nebo byla zrušena. Pokračování založené na hodnotách se nespustí, pokud je předchozí úloha vyvolá akci vytváření či zruší.

- Vždy spustit pokračování podle úloh, proto zvažte, jestli se má přidat pokračování podle úloh na konci řetězce pokračování. To může pomoct zajistit, že váš kód dodržuje všechny výjimky.

- Modul runtime vyvolá [concurrency::task_canceled](../../parallel/concrt/reference/task-canceled-class.md) při volání [Concurrency::Task:: Get](reference/task-class.md#get) a tato úloha se zruší.

- Modul runtime nedokáže spravovat výjimky pro jednoduché úlohy a agenty.

##  <a name="top"></a> V tomto dokumentu

- [Úlohy a pokračování](#tasks)

- [Skupiny úloh a paralelních algoritmů](#task_groups)

- [Výjimky vyvolané modulem Runtime](#runtime)

- [Více výjimek](#multiple)

- [Zrušení](#cancellation)

- [Prosté úlohy](#lwts)

- [Asynchronní agenti](#agents)

##  <a name="tasks"></a> Úlohy a pokračování

Tato část popisuje, jak modul runtime zpracovává výjimky, které jsou vyvolány [concurrency::task](../../parallel/concrt/reference/task-class.md) objekty a jejich pokračování. Další informace o modelu úlohy a pokračování v tématu [paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

Při vyvolání výjimky v těle funkce práce, kterou předat `task` modul runtime ukládá tuto výjimku a zařadí do kontextu, který volá objektů [Concurrency::Task:: Get](reference/task-class.md#get) nebo [souběžnosti:: Task::wait](reference/task-class.md#wait). Dokument [paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md) popisuje podle úloh a pokračování založené na hodnotách, ale chcete-li vytvořit souhrn, pokračování založené na hodnotách přebírá parametr typu `T` a pokračování podle úloh přebírá parametr typu `task<T>`. Pokud úloha, která vyvolá má jeden nebo více pokračování založené na hodnotách, nejsou tyto pokračování naplánováno ke spuštění. Následující příklad ukazuje toto chování:

[!code-cpp[concrt-eh-task#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_1.cpp)]

Pokračování podle úloh umožňuje zpracovat jakoukoliv výjimku, která je předchozí úloha vyvolá výjimku. Pokračování podle úloh vždy spuštěn; nezáleží, jestli úloha dokončena úspěšně, došlo k výjimce nebo byla zrušena. Pokud úloha vyvolá výjimku, jeho pokračování podle úloh jsou naplánovány ke spuštění. Následující příklad zobrazuje úlohu, která vždy vyvolá výjimku. Úkol má dvě pokračování; jedna je založené na hodnotách a druhý je založený na úlohách. Výjimky založené na úlohách vždy používá a proto může zachytit výjimku, která je předchozí úloha vyvolá výjimku. Pokud příklad čeká na obou pokračování na dokončení, výjimka je znovu vyvolána, protože úloh výjimka je vyvolána, vždy když `task::get` nebo `task::wait` je volána.

[!code-cpp[concrt-eh-continuations#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_2.cpp)]

Doporučujeme používat pokračování podle úloh pro zachycení výjimky, které budete moct zpracovat. Vždy spustit pokračování podle úloh, proto zvažte, jestli se má přidat pokračování podle úloh na konci řetězce pokračování. To může pomoct zajistit, že váš kód dodržuje všechny výjimky. Následující příklad ukazuje základní založené na hodnotách řetěz pokračování. Třetí úloha v řetězci vyvolá, a proto nejsou založené na hodnotách pokračování, které na něho spustit. Ale konečnou pokračující je založený na úlohách a proto je vždy spuštěn. Tato konečnou pokračující zpracovává výjimku, která je vyvolána třetí úlohou.

Doporučujeme, abyste zachytit nejvíce specifické výjimky, které je možné. Tento poslední pokračování podle úloh můžete vynechat, pokud nemáte specifické výjimky pro zachycení. Jakoukoli výjimku zůstává neošetřená a můžete ukončit aplikaci.

[!code-cpp[concrt-eh-task-chain#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_3.cpp)]

> [!TIP]
>  Můžete použít [concurrency::task_completion_event::set_exception](../../parallel/concrt/reference/task-completion-event-class.md) metoda výjimku přidružit k události dokončení úkolu. Dokument [paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md) popisuje [concurrency::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) třídy podrobněji.

[Concurrency::task_canceled](../../parallel/concrt/reference/task-canceled-class.md) je důležité runtime typ výjimky, které se týkají `task`. Modul runtime vyvolá `task_canceled` při volání `task::get` a tato úloha se zruší. (A naopak, `task::wait` vrátí [task_status::canceled](reference/concurrency-namespace-enums.md#task_group_status) a nevyvolá.) Můžete zachytit a zpracovat tuto výjimku z pokračování podle úloh nebo při volání `task::get`. Další informace o zrušení úlohy najdete v tématu [zrušení v knihovně PPL](cancellation-in-the-ppl.md).

> [!CAUTION]
>  Nikdy nevyvolají `task_canceled` z vašeho kódu. Volání [concurrency::cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) místo.

Modul runtime ukončí aplikaci, pokud úloha vyvolá výjimku a byla zachycena výjimka není úloha, některou jeho pokračování nebo hlavní aplikace. Pokud vaše aplikace dojde k chybě, můžete nakonfigurovat sady Visual Studio přerušit, když jsou vyvolány výjimky jazyka C++. Po dokončení diagnostiky umístění neošetřené výjimky použijte pokračování podle úloh. aby to zvládnul.

V části [výjimky vyvolané modulem Runtime](#runtime) v tomto dokumentu popisuje, jak pracovat s výjimky modulu CLR podrobněji.

[[Horní](#top)]

##  <a name="task_groups"></a> Skupiny úloh a paralelních algoritmů

Tato část popisuje, jak modul runtime zpracovává výjimky, které jsou vyvolány skupiny úloh. Tato část platí také pro paralelní algoritmy, jako [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for), protože tyto algoritmy stavět na skupiny úloh.

> [!CAUTION]
>  Ujistěte se, že chápete důsledky, které mají výjimky na závislé úlohy. Doporučené postupy o tom, jak použít zpracování výjimek s úkoly a paralelní algoritmy, naleznete v tématu [porozumění jak zrušení a výjimky zpracování odstraňování objektů ovlivnit](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) kapitoly osvědčené postupy paralelních Vzory tématu v knihovně.

Další informace o skupinách úkolů najdete v tématu [paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Další informace o paralelních algoritmech naleznete v tématu [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).

Při vyvolání výjimky v těle funkce práce, kterou předat [concurrency::task_group](reference/task-group-class.md) nebo [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) modul runtime ukládá tuto výjimku a zařadí ho objektů v kontextu, který volá [Concurrency::task_group:: wait](reference/task-group-class.md#wait), [Concurrency::structured_task_group:: wait](reference/structured-task-group-class.md#wait), [Concurrency::task_group:: run_and_wait](reference/task-group-class.md#run_and_wait), nebo [Concurrency::structured_task_group:: run_and_wait](reference/structured-task-group-class.md#run_and_wait). Modul runtime také zastaví všechny aktivní úkoly, které jsou ve skupině úloh (včetně těch v podřízených skupinách úloh) a zahodí všechny úkoly, které ještě nebyly spuštěny.

Následující příklad ukazuje základní struktura pracovní funkce, která vyvolá výjimku. V příkladu se používá `task_group` objekt pro tisk hodnoty dvou `point` objekty paralelně. `print_point` Pracovní funkce vypíše hodnoty `point` objekt do konzoly. Pracovní funkce vyvolá výjimku, pokud je vstupní hodnota `NULL`. Modul runtime ukládá tuto výjimku a zařadí do kontextu, který volá `task_group::wait`.

[!code-cpp[concrt-eh-task-group#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_4.cpp)]

Tento příklad vytvoří následující výstup.

```Output
X = 15, Y = 30Caught exception: point is NULL.
```

Úplný příklad používající zpracování výjimek v skupiny úloh, naleznete v tématu [jak: Použijte zpracování výjimek pro přerušení paralelní smyčky](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).

[[Horní](#top)]

##  <a name="runtime"></a> Výjimky vyvolané modulem Runtime

Během volání modulu runtime může způsobit výjimku. Většina typy výjimek, s výjimkou [concurrency::task_canceled](../../parallel/concrt/reference/task-canceled-class.md) a [concurrency::operation_timed_out](../../parallel/concrt/reference/operation-timed-out-class.md), označení o programovou chybu. Tyto chyby jsou obvykle neopravitelná a proto by neměl být zachycena nebo kódem aplikace. Doporučujeme, abyste pouze catch nebo zpracovat neopravitelným chybám v kódu aplikace, když potřebujete diagnostikovat chyby. Ale pochopení typy výjimek, které jsou definovány modulem runtime může pomoci diagnostikovat chyby.

Mechanismus zpracování výjimek je stejný pro výjimky vyvolané modulem runtime jako výjimky, které jsou vyvolány pracovní funkce. Například [concurrency::receive](reference/concurrency-namespace-functions.md#receive) funkce vyvolá `operation_timed_out` Pokud zprávu neobdrží v zadaném časovém období. Pokud `receive` pracovní funkce vyvolá výjimku, že předáte do skupiny úloh, modul runtime ukládá tuto výjimku a zařadí do kontextu, který volá `task_group::wait`, `structured_task_group::wait`, `task_group::run_and_wait`, nebo `structured_task_group::run_and_wait`.

V následujícím příkladu [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algoritmus k paralelnímu spouštění dvě úlohy. První úloha čeká pět sekund a pak odešle zprávu do vyrovnávací paměti zpráv. Druhý úkol používá `receive` funkce čekání na příjem zprávy ze stejné vyrovnávací paměti zpráv tři sekundy. `receive` Funkce vyvolá `operation_timed_out` pokud neobdrží zprávu v časovém období.

[!code-cpp[concrt-eh-time-out#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_5.cpp)]

Tento příklad vytvoří následující výstup.

```Output
The operation timed out.
```

Pokud chcete zabránit abnormální ukončení aplikace, ujistěte se, že váš kód zpracovává výjimky při volání do modulu runtime. Také zpracování výjimek při volání do externí kód, který používá modulu Runtime souběžnosti, například knihovny třetí strany.

[[Horní](#top)]

##  <a name="multiple"></a> Více výjimek

Pokud úloha nebo paralelní algoritmus obdrží více výjimek, modul runtime zařazuje pouze jeden z těchto výjimek pro volání kontextu. Modul runtime nezaručuje výjimky se zařazuje.

V následujícím příkladu `parallel_for` algoritmus tisknout čísla do konzoly. Vyvolá výjimku, pokud je vstupní hodnota menší než minimální hodnotu nebo větší než maximální hodnotu. V tomto příkladu více pracovní funkce může vyvolat výjimku.

[!code-cpp[concrt-eh-multiple#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_6.cpp)]

Následuje ukázkový výstup pro účely tohoto příkladu.

```Output
8293104567Caught exception: -5: the value is less than the minimum.
```

[[Horní](#top)]

##  <a name="cancellation"></a> Zrušení

Některé výjimky signalizují chybu. Vyhledávací algoritmus může například použít zpracování výjimek zastaví jeho přidruženého úkolu, pokud najde výsledek. Další informace o tom, jak použít mechanismy zrušení v kódu, naleznete v tématu [zrušení v knihovně PPL](../../parallel/concrt/cancellation-in-the-ppl.md).

[[Horní](#top)]

##  <a name="lwts"></a> Prosté úlohy

Lehký úkol je úkol, který plánujete přímo z [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) objektu. Prosté úlohy provést menší nároky na než běžné úkoly. Modul runtime však nebude zachytávat výjimky, které jsou vyvolány jednoduché úlohy. Místo toho výjimka zachycena obslužnou rutinu neošetřených výjimek, který ukončí proces ve výchozím nastavení. Proto použijte vhodný mechanismus zpracování chyb v aplikaci. Další informace o jednoduché úlohy, naleznete v tématu [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

[[Horní](#top)]

##  <a name="agents"></a> Asynchronní agenti

Jako jsou jednoduché úlohy modul runtime nedokáže spravovat výjimky, které jsou vyvolány asynchronních agentů.

Následující příklad ukazuje jeden ze způsobů zpracování výjimek ve třídě, která je odvozena z [concurrency::agent](../../parallel/concrt/reference/agent-class.md). Tento příklad definuje `points_agent` třídy. `points_agent::run` Metoda čtení `point` objekty z vyrovnávací paměti zpráv a vypíše do konzoly. `run` Metoda vyvolá výjimku, pokud obdrží `NULL` ukazatele.

`run` Metoda obklopuje veškerou práci v `try` - `catch` bloku. `catch` Bloku ukládá výjimku do vyrovnávací paměti zpráv. Aplikace zkontroluje, zda agent došlo k chybě, přečtěte si téma z této vyrovnávací paměti po dokončení agenta.

[!code-cpp[concrt-eh-agents#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_7.cpp)]

Tento příklad vytvoří následující výstup.

```Output
X: 10 Y: 20
X: 20 Y: 30
error occurred in agent: point must not be NULL
the status of the agent is: done
```

Protože `try` - `catch` bloku existuje mimo `while` smyčky, agent ukončí zpracování, pokud se setká s první chyba. Pokud `try` - `catch` bloku byl uvnitř `while` smyčky, agent bude pokračovat po dojde k chybě.

V tomto příkladu výjimky ukládá do vyrovnávací paměti zpráv tak, aby jiné součásti můžete sledovat v agentovi pro chyby za běhu. Tento příklad používá [concurrency::single_assignment](../../parallel/concrt/reference/single-assignment-class.md) objekt pro uložení chyby. V případě, kde agent zpracovává více výjimek `single_assignment` třídy uloží pouze první zprávu, která je předána do něj. Chcete-li uložit pouze poslední výjimku, použijte [concurrency::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) třídy. Chcete-li uložit všechny výjimky, použijte [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) třídy. Další informace o těchto bloků zpráv, najdete v části [asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md).

Další informace o asynchronních agentů najdete v tématu [asynchronních agentů](../../parallel/concrt/asynchronous-agents.md).

[[Horní](#top)]

##  <a name="summary"></a> Souhrn

[[Horní](#top)]

## <a name="see-also"></a>Viz také:

[Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)<br/>
[Funkční paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)<br/>
[Zrušení v knihovně PPL](cancellation-in-the-ppl.md)<br/>
[Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)
