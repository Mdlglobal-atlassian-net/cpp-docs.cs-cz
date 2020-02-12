---
title: 'Návod: Přizpůsobení stávajícího kódu pro použití prostých úloh'
ms.date: 04/25/2019
helpviewer_keywords:
- using lightweight tasks [Concurrency Runtime]
- lightweight tasks, using [Concurrency Runtime]
ms.assetid: 1edfe818-d274-46de-bdd3-e92967c9bbe0
ms.openlocfilehash: e7c6096829a1cd45cfdb849a1899d6b4a2d4cb78
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141998"
---
# <a name="walkthrough-adapting-existing-code-to-use-lightweight-tasks"></a>Návod: Přizpůsobení stávajícího kódu pro použití prostých úloh

V tomto tématu se dozvíte, jak upravit existující kód, který používá rozhraní Windows API k vytvoření a spuštění vlákna pro použití zjednodušené úlohy.

*Odlehčený úkol* je úkol, který naplánujete přímo z objektu [Concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) nebo [Concurrency:: Schedule](../../parallel/concrt/reference/schedulegroup-class.md) . Jednoduché úlohy jsou užitečné, když upravujete existující kód pro použití funkce plánování Concurrency Runtime.

## <a name="prerequisites"></a>Předpoklady

Než začnete tento návod, přečtěte si téma [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

## <a name="example"></a>Příklad

Následující příklad ilustruje typické použití rozhraní API systému Windows k vytvoření a spuštění vlákna. Tento příklad používá funkci [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) k volání `MyThreadFunction` v samostatném vlákně.

### <a name="initial-code"></a>Počáteční kód

[!code-cpp[concrt-windows-threads#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_1.cpp)]

Tento příklad vytvoří následující výstup.

```Output
Parameters = 50, 100
```

Následující kroky ukazují, jak upravit příklad kódu pro použití Concurrency Runtime k provedení stejné úlohy.

### <a name="to-adapt-the-example-to-use-a-lightweight-task"></a>Úprava příkladu tak, aby používal prostou úlohu

1. Přidejte direktivu `#include` pro hlavičkový soubor ConcRT. h.

[!code-cpp[concrt-migration-lwt#2](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_2.cpp)]

1. Přidejte direktivu `using` pro obor názvů `concurrency`.

[!code-cpp[concrt-migration-lwt#3](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_3.cpp)]

1. Změňte deklaraci `MyThreadFunction`, aby používala konvenci volání `__cdecl` a vrátila `void`.

[!code-cpp[concrt-migration-lwt#4](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_4.cpp)]

1. Upravte strukturu `MyData` tak, aby zahrnovala objekt [Concurrency:: Event](../../parallel/concrt/reference/event-class.md) , který signalizuje hlavní aplikaci, kterou byl úkol dokončen.

[!code-cpp[concrt-migration-lwt#5](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_5.cpp)]

1. Nahraďte volání `CreateThread` voláním metody [Concurrency:: CurrentScheduler:: ScheduleTask –](reference/currentscheduler-class.md#scheduletask) .

[!code-cpp[concrt-migration-lwt#6](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_6.cpp)]

1. Nahraďte volání `WaitForSingleObject` voláním metody [Concurrency:: Event:: wait](reference/event-class.md#wait) , která čeká na dokončení úlohy.

[!code-cpp[concrt-migration-lwt#7](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_7.cpp)]

1. Odeberte volání `CloseHandle`.

1. Změňte signaturu definice `MyThreadFunction` tak, aby odpovídala kroku 3.

[!code-cpp[concrt-migration-lwt#8](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_8.cpp)]

1. Na konci funkce `MyThreadFunction` volejte metodu [Concurrency:: Event:: set](reference/event-class.md#set) k signalizaci hlavní aplikaci, kterou byl úkol dokončen.

[!code-cpp[concrt-migration-lwt#9](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_9.cpp)]

1. Odeberte příkaz `return` z `MyThreadFunction`.

### <a name="completed-code"></a>Dokončený kód

Následující dokončený příklad ukazuje kód, který používá odlehčený úkol pro volání funkce `MyThreadFunction`.

[!code-cpp[concrt-migration-lwt#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_10.cpp)]

## <a name="see-also"></a>Viz také

[Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Scheduler – třída](../../parallel/concrt/reference/scheduler-class.md)
