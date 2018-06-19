---
title: 'Postupy: vytvoření úlohy, která je dokončena po prodlevě | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- task_completion_event class, example
- create a task that completes after a delay, example [C++]
ms.assetid: 3fc0a194-3fdb-4eba-8b8a-b890981a985d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fca1ba3874f02b44f96fd795b531536a23c8d462
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688408"
---
# <a name="how-to-create-a-task-that-completes-after-a-delay"></a>Postupy: Vytvoření úlohy, která je dokončena po prodlevě
Tento příklad ukazuje způsob použití [concurrency::task](../../parallel/concrt/reference/task-class.md), [concurrency::cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md), [concurrency::cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md), [ Concurrency::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md), [concurrency::timer](../../parallel/concrt/reference/timer-class.md), a [concurrency::call](../../parallel/concrt/reference/call-class.md) třídy k vytvoření úlohy, která je dokončena po prodlevě. Tuto metodu můžete použít k vytvoření smyčky, které příležitostně dotazování na data, zavést vypršení časových limitů, zpoždění zpracování vstupu uživatele po předem určenou dobu a tak dále.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `complete_after` a `cancel_after_timeout` funkce. `complete_after` Funkce vytvoří `task` objektu, která je dokončena po zadaný zpoždění. Použije `timer` objektu a `call` objekt, který chcete nastavit `task_completion_event` objektu po zadaný zpoždění. Pomocí `task_completion_event` třídu, můžete definovat úlohu, která je dokončena po vlákna nebo jiná úloha signalizuje, že hodnota je k dispozici. Pokud je nastavená události, naslouchací proces úkoly dokončí a jejich pokračování mají naplánované spuštění.  
  
> [!TIP]
>  Další informace o `timer` a `call` třídy, které jsou součástí knihovna asynchronních agentů, najdete v části [asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md).  
  
 `cancel_after_timeout` Funkce je založena na `complete_after` funkce na zrušení úlohy, pokud tento úkol neskončí před daného časového limitu. `cancel_after_timeout` Funkce vytvoří dvě úlohy. První úlohou označuje úspěch a dokončení po dokončení zadané úlohy; v druhé úloze znamená selhání a dokončení po zadaný časový limit. `cancel_after_timeout` Funkce vytvoří pokračování úlohu, která se spouští po dokončení úloh úspěch nebo selhání. Pokud první dokončení úlohy selhání pokračování zruší zdroji tokenu zrušit úlohu celkové.  
  
 [!code-cpp[concrt-task-delay#1](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_1.cpp)]  
  
## <a name="example"></a>Příklad  
 Následující příklad vypočítá počet prvočísel v rozsahu [0, 100000] vícekrát. Operace se nezdaří, pokud nebyl proveden v daném časovém limitu. `count_primes` Funkce ukazuje, jak používat `cancel_after_timeout` funkce. Se vrátí počet si mosty v daném rozsahu a selže, pokud úkol neskončí v zadaný čas. `wmain` Volání funkce `count_primes` funkce vícekrát. Pokaždé, když, poloviny časový limit. Aplikace se ukončí po operaci nebyl dokončen aktuální časový limit.  
  
 [!code-cpp[concrt-task-delay#2](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_2.cpp)]  
  
 Pokud použijete tento postup se zrušit úlohy po prodlevě, všechny nezahájených úkolů nespustí po celkové úloha je zrušena. Je však důležité pro všechny dlouhodobé úlohy včas reagovat na zrušení. Další informace o zrušení úlohy najdete v tématu [zrušení v knihovně PPL](cancellation-in-the-ppl.md).  
  
## <a name="example"></a>Příklad  
 Tady je kompletní kód v tomto příkladu:  
  
 [!code-cpp[concrt-task-delay#3](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_3.cpp)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Kompilace kódu, zkopírujte jej a vložte ji do projektu sady Visual Studio nebo ho vložte do souboru, který je pojmenován `task-delay.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe /EHsc úloh delay.cpp**  
  
## <a name="see-also"></a>Viz také  
 [Funkční paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [Task – třída (Concurrency Runtime)](../../parallel/concrt/reference/task-class.md)   
 [cancellation_token_source – třída](../../parallel/concrt/reference/cancellation-token-source-class.md)   
 [cancellation_token – třída](../../parallel/concrt/reference/cancellation-token-class.md)   
 [task_completion_event – třída](../../parallel/concrt/reference/task-completion-event-class.md)   
 [Třída Timer](../../parallel/concrt/reference/timer-class.md)   
 [Call – třída](../../parallel/concrt/reference/call-class.md)   
 [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Zrušení v knihovně PPL](cancellation-in-the-ppl.md)

