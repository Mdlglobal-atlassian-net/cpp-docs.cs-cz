---
title: 'Návod: Přizpůsobení stávajícího kódu pro použití zjednodušených úloh'
ms.date: 04/25/2019
helpviewer_keywords:
- using lightweight tasks [Concurrency Runtime]
- lightweight tasks, using [Concurrency Runtime]
ms.assetid: 1edfe818-d274-46de-bdd3-e92967c9bbe0
ms.openlocfilehash: 406d4d24d0042c7bded4f94dcef1e7731ab3947f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512147"
---
# <a name="walkthrough-adapting-existing-code-to-use-lightweight-tasks"></a>Návod: Přizpůsobení stávajícího kódu pro použití zjednodušených úloh

V tomto tématu se dozvíte, jak upravit existující kód, který používá rozhraní Windows API k vytvoření a spuštění vlákna pro použití zjednodušené úlohy.

*Odlehčený úkol* je úkol, který naplánujete přímo z objektu [Concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) nebo [Concurrency:: Schedule](../../parallel/concrt/reference/schedulegroup-class.md) . Jednoduché úlohy jsou užitečné, když upravujete existující kód pro použití funkce plánování Concurrency Runtime.

## <a name="prerequisites"></a>Požadavky

Než začnete tento návod, přečtěte si téma [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující příklad ilustruje typické použití rozhraní API systému Windows k vytvoření a spuštění vlákna. Tento příklad používá funkci [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) k volání `MyThreadFunction` v samostatném vlákně.

### <a name="code"></a>Kód

[!code-cpp[concrt-windows-threads#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_1.cpp)]

### <a name="comments"></a>Komentáře

Tento příklad vytvoří následující výstup.

```Output
Parameters = 50, 100
```

Následující kroky ukazují, jak upravit příklad kódu pro použití Concurrency Runtime k provedení stejné úlohy.

### <a name="to-adapt-the-example-to-use-a-lightweight-task"></a>Úprava příkladu tak, aby používal prostou úlohu

1. `#include` Přidejte direktivu pro hlavičkový soubor ConcRT. h.

[!code-cpp[concrt-migration-lwt#2](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_2.cpp)]

1. Přidejte direktivu `concurrency` pro obor názvů. `using`

[!code-cpp[concrt-migration-lwt#3](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_3.cpp)]

1. Změňte deklaraci `MyThreadFunction` na `__cdecl` použití konvence volání a vraťte `void`se.

[!code-cpp[concrt-migration-lwt#4](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_4.cpp)]

1. Upravte strukturu tak, aby zahrnovala objekt [Concurrency:: Event](../../parallel/concrt/reference/event-class.md) , který signalizuje hlavní aplikaci, kterou byl úkol dokončen. `MyData`

[!code-cpp[concrt-migration-lwt#5](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_5.cpp)]

1. Nahraďte volání `CreateThread` voláním metody [Concurrency:: CurrentScheduler:: ScheduleTask –](reference/currentscheduler-class.md#scheduletask) .

[!code-cpp[concrt-migration-lwt#6](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_6.cpp)]

1. Nahraďte volání `WaitForSingleObject` voláním metody [Concurrency:: Event:: wait](reference/event-class.md#wait) , která čeká na dokončení úlohy.

[!code-cpp[concrt-migration-lwt#7](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_7.cpp)]

1. Odeberte volání `CloseHandle`.

1. Změňte signaturu definice `MyThreadFunction` , aby odpovídala kroku 3.

[!code-cpp[concrt-migration-lwt#8](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_8.cpp)]

9. Na konci `MyThreadFunction` funkce volejte metodu [Concurrency:: Event:: set](reference/event-class.md#set) k signalizaci hlavní aplikaci, kterou byl úkol dokončen.

[!code-cpp[concrt-migration-lwt#9](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_9.cpp)]

10. Odeberte příkaz z `MyThreadFunction`. `return`

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující dokončený příklad ukazuje kód, který používá odlehčený úkol pro volání `MyThreadFunction` funkce.

### <a name="code"></a>Kód

[!code-cpp[concrt-migration-lwt#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_10.cpp)]

### <a name="comments"></a>Komentáře

## <a name="see-also"></a>Viz také:

[Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Scheduler – třída](../../parallel/concrt/reference/scheduler-class.md)
