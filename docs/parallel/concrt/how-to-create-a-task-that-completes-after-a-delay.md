---
title: 'Postupy: Vytvoření úlohy, která je dokončena po prodlevě'
ms.date: 11/04/2016
helpviewer_keywords:
- task_completion_event class, example
- create a task that completes after a delay, example [C++]
ms.assetid: 3fc0a194-3fdb-4eba-8b8a-b890981a985d
ms.openlocfilehash: 76189f45eb486e06b040155f6697bf003659b474
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141748"
---
# <a name="how-to-create-a-task-that-completes-after-a-delay"></a>Postupy: Vytvoření úlohy, která je dokončena po prodlevě

Tento příklad ukazuje, jak použít třídy [Concurrency:: Task](../../parallel/concrt/reference/task-class.md), [concurrency:: cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md), [Concurrency:: cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md), [Concurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md), [Concurrency:: Timer](../../parallel/concrt/reference/timer-class.md)a [Concurrency:: Call](../../parallel/concrt/reference/call-class.md) , k vytvoření úlohy, která se dokončí po zpoždění. Tuto metodu můžete použít k vytvoření smyček, které občas dotazují na data, zavádějí časové limity, zpoždění při zpracování vstupu uživatele pro předstanovenou dobu a tak dále.

## <a name="example"></a>Příklad

Následující příklad ukazuje funkce `complete_after` a `cancel_after_timeout`. Funkce `complete_after` vytvoří objekt `task`, který se dokončí po zadané prodlevě. K nastavení `task_completion_event` objektu po zadané prodlevě používá objekt `timer` a objekt `call`. Pomocí třídy `task_completion_event` můžete definovat úlohu, která se dokončí po vlákně nebo jiné úloze signalizuje, že je k dispozici hodnota. Po nastavení události jsou dokončeny úlohy naslouchacího procesu a jejich pokračování je naplánováno na spuštění.

> [!TIP]
> Další informace o třídách `timer` a `call`, které jsou součástí knihovny asynchronních agentů, naleznete v tématu [asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md).

Funkce `cancel_after_timeout` je vytvořena na funkci `complete_after` pro zrušení úlohy, pokud tato úloha není dokončena před daným časovým limitem. Funkce `cancel_after_timeout` vytvoří dvě úlohy. První úkol indikuje úspěch a skončí po dokončení poskytnuté úlohy; druhá úloha indikuje selhání a skončí po zadaném časovém limitu. Funkce `cancel_after_timeout` vytvoří úlohu pokračování, která se spustí po dokončení úlohy úspěch nebo neúspěch. Pokud se úloha selhání nejprve dokončí, pokračování zruší zdroj tokenu, aby se zrušil celkový úkol.

[!code-cpp[concrt-task-delay#1](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_1.cpp)]

## <a name="example"></a>Příklad

Následující příklad vypočítá počet primárních čísel v rozsahu [0, 100000] několikrát. Operace se nezdařila, pokud není dokončena v daném časovém limitu. Funkce `count_primes` ukazuje, jak používat funkci `cancel_after_timeout`. Spočítá počet primárních dat v daném rozsahu a neproběhne úspěšně, pokud úloha není dokončena v zadaném čase. Funkce `wmain` volá funkci `count_primes` několikrát. Pokaždé, když se zkrátí časový limit. Program skončí po dokončení operace v aktuálním časovém limitu.

[!code-cpp[concrt-task-delay#2](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_2.cpp)]

Použijete-li tento postup ke zrušení úloh po uplynutí určité prodlevy, všechny nezahájené úkoly se po zrušení celkového úkolu nespustí. Je ale důležité, aby jakékoli dlouhotrvající úlohy reagovaly včas na zrušení. Další informace o zrušení úlohy najdete v části [zrušení v PPL](cancellation-in-the-ppl.md).

## <a name="example"></a>Příklad

Zde je kompletní kód pro tento příklad:

[!code-cpp[concrt-task-delay#3](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_3.cpp)]

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Chcete-li zkompilovat kód, zkopírujte jej a vložte jej do projektu aplikace Visual Studio nebo jej vložte do souboru s názvem `task-delay.cpp` a poté spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

**CL. exe/EHsc Task-Delay. cpp**

## <a name="see-also"></a>Viz také

[Paralelní úkoly](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[task – třída (Concurrency Runtime)](../../parallel/concrt/reference/task-class.md)<br/>
[cancellation_token_source – třída](../../parallel/concrt/reference/cancellation-token-source-class.md)<br/>
[cancellation_token – třída](../../parallel/concrt/reference/cancellation-token-class.md)<br/>
[task_completion_event – třída](../../parallel/concrt/reference/task-completion-event-class.md)<br/>
[timer – třída](../../parallel/concrt/reference/timer-class.md)<br/>
[call – třída](../../parallel/concrt/reference/call-class.md)<br/>
[Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Zrušení v knihovně PPL](cancellation-in-the-ppl.md)
