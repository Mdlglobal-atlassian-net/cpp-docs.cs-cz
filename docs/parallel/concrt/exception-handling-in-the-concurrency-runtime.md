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
ms.openlocfilehash: 4c7fee363da023b9252471a35aaecd262a55f17c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854135"
---
# <a name="exception-handling-in-the-concurrency-runtime"></a>Zpracování výjimek v Concurrency Runtime

Concurrency Runtime používá C++ zpracování výjimek ke komunikaci mnoha druhů chyb. Tyto chyby zahrnují neplatné použití modulu runtime, běhové chyby, jako například selhání získání prostředku, a chyby, ke kterým dochází v pracovních funkcích, které poskytnete úlohám a skupinám úloh. Když úloha nebo skupina úloh vyvolá výjimku, modul runtime tuto výjimku udržuje a zazařazuje do kontextu, který čeká na dokončení úlohy nebo skupiny úloh. Pro součásti, jako například odlehčené úlohy a agenty, modul runtime nespravuje výjimky. V těchto případech je nutné implementovat vlastní mechanismus zpracování výjimek. Toto téma popisuje, jak modul runtime zpracovává výjimky, které jsou vyvolány úkoly, skupiny úloh, zjednodušené úlohy a asynchronní agenti a jak reagovat na výjimky ve vašich aplikacích.

## <a name="key-points"></a>Klíčové body

- Když úloha nebo skupina úloh vyvolá výjimku, modul runtime tuto výjimku udržuje a zazařazuje do kontextu, který čeká na dokončení úlohy nebo skupiny úloh.

- Pokud je to možné, zajistěte, aby každé volání [Concurrency:: task:: Get](reference/task-class.md#get) a [Concurrency:: task:: počkalo](reference/task-class.md#wait) s `try`/`catch` blok pro zpracování chyb, ze kterých můžete obnovit. Modul runtime ukončí aplikaci, pokud úloha vyvolá výjimku a tato výjimka není zachycena úkolem, jedním z jeho pokračování nebo hlavní aplikací.

- Vždy se spustí pokračování založené na úlohách; Nezáleží na tom, zda byl předchozí úkol úspěšně dokončen, vyvolal výjimku nebo byl zrušen. Pokračování založené na hodnotách se nespustí, pokud předchozí úloha vyvolá nebo zruší.

- Vzhledem k tomu, že se pokračování na základě úkolů spouští vždy, zvažte, zda na konec řetězce pokračování přidat pokračování na základě úkolů. To může zajistit, že váš kód bude sledovat všechny výjimky.

- Modul runtime vyvolá [Concurrency:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md) při volání metody [Concurrency:: task:: Get](reference/task-class.md#get) a této úlohy je zrušeno.

- Modul runtime nespravuje výjimky pro zjednodušené úlohy a agenty.

## <a name="top"></a>V tomto dokumentu

- [Úkoly a pokračování](#tasks)

- [Skupiny úloh a paralelní algoritmy](#task_groups)

- [Výjimky vyvolané modulem runtime](#runtime)

- [Více výjimek](#multiple)

- [Zrušení](#cancellation)

- [Prosté úlohy](#lwts)

- [Asynchronní agenti](#agents)

## <a name="tasks"></a>Úkoly a pokračování

Tato část popisuje, jak modul runtime zpracovává výjimky, které jsou vyvolány objekty [Concurrency:: Task](../../parallel/concrt/reference/task-class.md) a jejich pokračování. Další informace o modelu úlohy a pokračování najdete v tématu [Task paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

Pokud vyvoláte výjimku v těle pracovní funkce, kterou předáte objektu `task`, modul runtime tuto výjimku uloží a zařadí do kontextu, který volá [Concurrency:: task:: Get](reference/task-class.md#get) nebo [Concurrency:: task:: wait](reference/task-class.md#wait). [Paralelní](../../parallel/concrt/task-parallelism-concurrency-runtime.md) vytváření dokumentů popisuje pokračování na základě úloh oproti hodnotám, ale k sumarizaci, pokračování založené na hodnotách přebírá parametr typu `T` a pokračování na základě úloh přijímá parametr typu `task<T>`. Pokud úkol, který vyvolává výjimku, má jedno nebo více pokračování na základě hodnoty, nejsou tato pokračování naplánována ke spuštění. Následující příklad znázorňuje toto chování:

[!code-cpp[concrt-eh-task#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_1.cpp)]

Pokračování založené na úlohách umožňuje zpracovat jakoukoli výjimku, která je vyvolána předchozí úlohou. Vždy se spustí pokračování založené na úlohách; Nezáleží na tom, zda byla úloha úspěšně dokončena, vyvolala výjimku nebo byla zrušena. Pokud úkol vyvolá výjimku, je naplánováno spuštění jeho pokračování na základě úkolů. Následující příklad ukazuje úkol, který vždy vyvolá. Úkol má dvě pokračování; jedna je založená na hodnotách a druhá je založená na úlohách. Výjimka založená na úlohách vždy běží, a proto může zachytit výjimku, která je vyvolána předchozí úlohou. Když příklad čeká na dokončení obou pokračování, výjimka je vyvolána znovu, protože výjimka úlohy je vždy vyvolána, když je volána `task::get` nebo `task::wait`.

[!code-cpp[concrt-eh-continuations#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_2.cpp)]

Pro zachycení výjimek, které můžete zpracovat, doporučujeme použít pokračování na základě úkolů. Vzhledem k tomu, že se pokračování na základě úkolů spouští vždy, zvažte, zda na konec řetězce pokračování přidat pokračování na základě úkolů. To může zajistit, že váš kód bude sledovat všechny výjimky. Následující příklad ukazuje základní řetězec pokračování založený na hodnotách. Třetí úloha v řetězu vyvolá, a proto jakékoli pokračování založené na hodnotách, které následují, není spuštěno. Konečné pokračování je však založené na úlohách a je proto vždy spuštěno. Toto konečné pokračování zpracovává výjimku, která je vyvolána třetí úlohou.

Doporučujeme, abyste zachytili nejvíc konkrétní výjimky, které můžete. Toto konečné pokračování na základě úkolů můžete vynechat, pokud nemáte specifické výjimky pro zachycení. Veškerá výjimka zůstane neošetřená a může aplikaci ukončit.

[!code-cpp[concrt-eh-task-chain#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_3.cpp)]

> [!TIP]
> K přidružení výjimky k události dokončení úkolu lze použít metodu [Concurrency:: task_completion_event:: set_exception](../../parallel/concrt/reference/task-completion-event-class.md) . [Paralelismuing pro úlohy](../../parallel/concrt/task-parallelism-concurrency-runtime.md) dokumentu popisuje třídu [concurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) podrobněji.

[Concurrency:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md) je důležitým typem běhové výjimky, který souvisí s `task`. Modul runtime vyvolá `task_canceled` při volání `task::get` a tato úloha je zrušena. (Naopak `task::wait` vrátí [task_status:: Canceled](reference/concurrency-namespace-enums.md#task_group_status) a nevyvolává.) Tuto výjimku můžete zachytit a zpracovat z pokračování založeného na úlohách nebo při volání `task::get`. Další informace o zrušení úlohy najdete v části [zrušení v PPL](cancellation-in-the-ppl.md).

> [!CAUTION]
> Nikdy nevyvolávat `task_canceled` z vašeho kódu. Místo toho volejte [Concurrency:: cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) .

Modul runtime ukončí aplikaci, pokud úloha vyvolá výjimku a tato výjimka není zachycena úkolem, jedním z jeho pokračování nebo hlavní aplikací. Pokud dojde k chybě vaší aplikace, můžete nakonfigurovat aplikaci Visual Studio, C++ aby byla přerušena výjimka, když dojde k výjimce. Po diagnostikování umístění neošetřené výjimky použijte pro jeho zpracování pokračování založené na úlohách.

Výjimky oddílu [vyvolané modulem runtime](#runtime) v tomto dokumentu popisují, jak pracovat s výjimkami za běhu podrobněji.

[[Nahoře](#top)]

## <a name="task_groups"></a>Skupiny úloh a paralelní algoritmy

Tato část popisuje, jak modul runtime zpracovává výjimky, které jsou vyvolány skupinami úloh. Tato část se týká také paralelních algoritmů, jako je [Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for), protože tyto algoritmy se vytvářejí ve skupinách úloh.

> [!CAUTION]
> Ujistěte se, že rozumíte důsledkům, které mají výjimky na závislých úlohách. Doporučené postupy týkající se použití zpracování výjimek s úkoly nebo paralelními algoritmy naleznete v tématu [pochopení způsobu, jakým zpracování zrušení a výjimek ovlivňuje oddíl zničení objektů](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) v tématu osvědčené postupy v tématu Knihovna paralelních vzorů.

Další informace o skupinách úloh najdete v tématu [Task paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Další informace o paralelních algoritmech najdete v tématu [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).

Pokud vyvoláte výjimku v těle pracovní funkce, kterou předáte do [Concurrency:: task_group](reference/task-group-class.md) nebo [concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) objektu modul runtime ukládá tuto výjimku a zazařazuje je do kontextu, který volá [Concurrency:: task_group:: wait](reference/task-group-class.md#wait), [Concurrency:: structured_task_group:: wait](reference/structured-task-group-class.md#wait), [Concurrency:: task_group:: run_and_wait](reference/task-group-class.md#run_and_wait)nebo [Concurrency:: structured_task_group:: run_and_wait](reference/structured-task-group-class.md#run_and_wait). Modul runtime také zastaví všechny aktivní úlohy, které jsou ve skupině úloh (včetně těch v podřízených skupinách úloh), a zahodí všechny úlohy, které ještě nebyly spuštěny.

Následující příklad ukazuje základní strukturu pracovní funkce, která vyvolá výjimku. V příkladu se používá objekt `task_group` k vytištění hodnot dvou objektů `point` paralelně. Funkce `print_point` Work tiskne hodnoty `point` objektu do konzoly. Funkce Work vyvolá výjimku, pokud je vstupní hodnota `NULL`. Modul runtime ukládá tuto výjimku a zařazuje je do kontextu, který volá `task_group::wait`.

[!code-cpp[concrt-eh-task-group#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_4.cpp)]

Tento příklad vytvoří následující výstup.

```Output
X = 15, Y = 30Caught exception: point is NULL.
```

Úplný příklad, který používá zpracování výjimek ve skupině úloh, naleznete v tématu [How to: use Reexception rechází z paralelní smyčky](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).

[[Nahoře](#top)]

## <a name="runtime"></a>Výjimky vyvolané modulem runtime

Výjimka může být způsobena voláním modulu runtime. Většina typů výjimek, s výjimkou [Concurrency:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md) a [concurrency:: operation_timed_out](../../parallel/concrt/reference/operation-timed-out-class.md), označují chybu programování. Tyto chyby jsou obvykle neobnovitelné, proto by neměly být zachyceny nebo zpracovávány kódem aplikace. Doporučujeme, abyste zachytit nebo zpracovávat neodstranitelné chyby v kódu aplikace, když potřebujete diagnostikovat chyby programování. Nicméně porozumění typům výjimek, které jsou definovány modulem runtime, vám může pomáhat diagnostikovat chyby programování.

Mechanismus zpracování výjimek je stejný pro výjimky, které jsou vyvolány modulem runtime jako výjimky, které jsou vyvolány pracovními funkcemi. Například funkce [Concurrency:: Receive](reference/concurrency-namespace-functions.md#receive) vyvolá `operation_timed_out`, když neobdrží zprávu v zadaném časovém období. Pokud `receive` vyvolá výjimku v pracovní funkci, kterou předáte do skupiny úloh, modul runtime tuto výjimku uloží a zařadí do kontextu, který volá `task_group::wait`, `structured_task_group::wait`, `task_group::run_and_wait`nebo `structured_task_group::run_and_wait`.

Následující příklad používá algoritmus [Concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) k paralelnímu spuštění dvou úloh. První úkol počká pět sekund a poté pošle zprávu do vyrovnávací paměti zpráv. Druhý úkol pomocí funkce `receive` čeká tři sekundy na přijetí zprávy ze stejné vyrovnávací paměti zpráv. Funkce `receive` vyvolá `operation_timed_out`, pokud neobdrží zprávu v časovém intervalu.

[!code-cpp[concrt-eh-time-out#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_5.cpp)]

Tento příklad vytvoří následující výstup.

```Output
The operation timed out.
```

Chcete-li zabránit abnormálnímu ukončení aplikace, ujistěte se, že váš kód zpracovává výjimky při volání do modulu runtime. Také zpracovávat výjimky při volání do externího kódu, který používá Concurrency Runtime, například knihovny třetí strany.

[[Nahoře](#top)]

## <a name="multiple"></a>Více výjimek

Pokud úloha nebo paralelní algoritmus přijímá více výjimek, modul runtime zařazování pouze jedné z těchto výjimek do volajícího kontextu. Modul runtime nezaručuje, která výjimka zařazování.

Následující příklad používá algoritmus `parallel_for` k tisku čísel do konzoly. Vyvolá výjimku, pokud je vstupní hodnota menší než minimální hodnota nebo větší než maximální hodnota. V tomto příkladu může vícenásobné pracovní funkce vyvolat výjimku.

[!code-cpp[concrt-eh-multiple#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_6.cpp)]

Následující ukázka ukazuje výstup pro tento příklad.

```Output
8293104567Caught exception: -5: the value is less than the minimum.
```

[[Nahoře](#top)]

## <a name="cancellation"></a>Výmaz

Ne všechny výjimky indikují chybu. Například algoritmus hledání může použít zpracování výjimek k zastavení přidružené úlohy, když najde výsledek. Další informace o tom, jak používat mechanismy zrušení v kódu, naleznete v tématu [zrušení v PPL](../../parallel/concrt/cancellation-in-the-ppl.md).

[[Nahoře](#top)]

## <a name="lwts"></a>Jednoduché úlohy

Odlehčený úkol je úkol, který naplánujete přímo z objektu [Concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) . Jednoduché úlohy mají méně režijních nákladů než běžné úlohy. Modul runtime však nezachytí výjimky, které jsou vyvolány odlehčenými úlohami. Namísto toho je výjimka zachycena neošetřenou obslužnou rutinou výjimky, která ve výchozím nastavení ukončí proces. Proto použijte vhodný mechanismus pro zpracování chyb ve vaší aplikaci. Další informace o odlehčených úlohách najdete v tématu [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

[[Nahoře](#top)]

## <a name="agents"></a>Asynchronní agenti

Podobně jako jednoduché úlohy modul runtime nespravuje výjimky, které jsou vyvolány pomocí asynchronních agentů.

Následující příklad ukazuje jeden ze způsobů zpracování výjimek ve třídě, která je odvozena z [: concurrency:: Agent](../../parallel/concrt/reference/agent-class.md). Tento příklad definuje třídu `points_agent`. Metoda `points_agent::run` čte objekty `point` z vyrovnávací paměti zpráv a tiskne je do konzoly. Metoda `run` vyvolá výjimku, pokud obdrží ukazatel `NULL`.

Metoda `run` obklopuje veškerou práci ve `try`-bloku `catch`. Blok `catch` ukládá výjimku do vyrovnávací paměti zpráv. Aplikace zkontroluje, jestli agent zjistil chybu, čtením z této vyrovnávací paměti po dokončení agenta.

[!code-cpp[concrt-eh-agents#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_7.cpp)]

Tento příklad vytvoří následující výstup.

```Output
X: 10 Y: 20
X: 20 Y: 30
error occurred in agent: point must not be NULL
the status of the agent is: done
```

Vzhledem k tomu, že blok `try`-`catch` existuje mimo `while` cyklus, Agent ukončí zpracování při výskytu první chyby. Pokud byl blok `try`-`catch` uvnitř `while` smyčky, bude agent dál pokračovat, i když dojde k chybě.

Tento příklad ukládá výjimky do vyrovnávací paměti zpráv, aby mohla jiná komponenta monitorovat agenta pro chyby při spuštění. V tomto příkladu se k uložení chyby používá objekt [Concurrency:: single_assignment](../../parallel/concrt/reference/single-assignment-class.md) . V případě, kdy Agent zpracovává více výjimek, třída `single_assignment` ukládá pouze první zprávu, která je předána. Chcete-li uložit pouze poslední výjimku, použijte třídu [Concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) . Chcete-li uložit všechny výjimky, použijte třídu [Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) . Další informace o těchto blocích zpráv naleznete v tématu [asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md).

Další informace o asynchronních agentech najdete v tématu [Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md).

[[Nahoře](#top)]

## <a name="summary"></a>Shrnut

[[Nahoře](#top)]

## <a name="see-also"></a>Viz také

[Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)<br/>
[Paralelní úkoly](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)<br/>
[Zrušení v knihovně PPL](cancellation-in-the-ppl.md)<br/>
[Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)
