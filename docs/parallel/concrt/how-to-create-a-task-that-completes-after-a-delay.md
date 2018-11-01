---
title: 'Postupy: Vytvoření úlohy, která je dokončena po prodlevě'
ms.date: 11/04/2016
helpviewer_keywords:
- task_completion_event class, example
- create a task that completes after a delay, example [C++]
ms.assetid: 3fc0a194-3fdb-4eba-8b8a-b890981a985d
ms.openlocfilehash: 89564a00dbfde078ef98cd53110853e30e33ad6b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616334"
---
# <a name="how-to-create-a-task-that-completes-after-a-delay"></a>Postupy: Vytvoření úlohy, která je dokončena po prodlevě

Tento příklad ukazuje způsob použití [concurrency::task](../../parallel/concrt/reference/task-class.md), [concurrency::cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md), [concurrency::cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md), [ Concurrency::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md), [concurrency::timer](../../parallel/concrt/reference/timer-class.md), a [concurrency::call](../../parallel/concrt/reference/call-class.md) třídy k vytvoření úlohy, která se dokončí po prodlevě. Tuto metodu můžete použít k vytvoření cyklů, které příležitostně dotazovat na data, představují vypršení časových limitů, zpracování vstupu uživatele na předem stanovenou dobu zpoždění a tak dále.

## <a name="example"></a>Příklad

Následující příklad ukazuje `complete_after` a `cancel_after_timeout` funkce. `complete_after` Vytvoří funkci `task` objektu, která se dokončí po zadané době. Použije `timer` objektu a `call` nastavíte `task_completion_event` objektu po zadané době. S použitím `task_completion_event` třídy, můžete definovat úlohu, která se dokončí po vlákno nebo jiný úkol signalizuje, že hodnota je k dispozici. Při nastavení události úkoly modulu listener a jejich pokračování je naplánováno ke spuštění.

> [!TIP]
>  Další informace o `timer` a `call` naleznete v tématu třídy, které jsou částí asynchronní knihovnou agentů, [asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md).

`cancel_after_timeout` Vychází z funkce `complete_after` funkce zrušení úlohy, pokud se tento úkol nebude dokončen před daného časového limitu. `cancel_after_timeout` Funkce vytvoří dvě úlohy. První úkol označuje úspěch a dokončí po dokončení zadané úlohy; druhá úloha označuje chybu a dokončí po zadaný časový limit. `cancel_after_timeout` Funkce vytvoří úlohu pokračování, který se spustí po dokončení úlohy úspěch nebo neúspěch. Pokud dokončení první úlohy selhání pokračování zruší zdroj tokenu zrušení jedné úlohy.

[!code-cpp[concrt-task-delay#1](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_1.cpp)]

## <a name="example"></a>Příklad

Následující příklad vypočítá počet prvočísel v rozsahu [0, 100000] více než jednou. Operace se nezdaří, pokud v daném časovém limitu nedokončí. `count_primes` Funkce ukazuje, jak používat `cancel_after_timeout` funkce. Spočítá počet základen v daném rozsahu a selže, pokud úkol neskončí v zadaný čas. `wmain` Volání funkce `count_primes` funkce více než jednou. Pokaždé, když, poloviny časový limit. Program skončí po operaci nedokončí v aktuální časový limit.

[!code-cpp[concrt-task-delay#2](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_2.cpp)]

Když použijete tento postup zrušit úlohy po prodlevě, všechny úlohy nezahájené nespustí po zrušení jedné úlohy. Je však důležité pro jakékoli dlouhotrvající úlohy včas reagovat na zrušení. Další informace o zrušení úlohy najdete v tématu [zrušení v knihovně PPL](cancellation-in-the-ppl.md).

## <a name="example"></a>Příklad

Tady je kompletní kód v tomto příkladu:

[!code-cpp[concrt-task-delay#3](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_3.cpp)]

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Chcete-li kód zkompilovat, ho zkopírujte a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `task-delay.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe/EHsc úloh delay.cpp**

## <a name="see-also"></a>Viz také

[Funkční paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[task – třída (Concurrency Runtime)](../../parallel/concrt/reference/task-class.md)<br/>
[cancellation_token_source – třída](../../parallel/concrt/reference/cancellation-token-source-class.md)<br/>
[cancellation_token – třída](../../parallel/concrt/reference/cancellation-token-class.md)<br/>
[task_completion_event – třída](../../parallel/concrt/reference/task-completion-event-class.md)<br/>
[timer – třída](../../parallel/concrt/reference/timer-class.md)<br/>
[call – třída](../../parallel/concrt/reference/call-class.md)<br/>
[Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Zrušení v knihovně PPL](cancellation-in-the-ppl.md)

