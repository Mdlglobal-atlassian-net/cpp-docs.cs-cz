---
title: 'Návod: Přizpůsobení stávajícího kódu pro použití prostých úloh'
ms.date: 04/25/2019
helpviewer_keywords:
- using lightweight tasks [Concurrency Runtime]
- lightweight tasks, using [Concurrency Runtime]
ms.assetid: 1edfe818-d274-46de-bdd3-e92967c9bbe0
ms.openlocfilehash: 658cc82442bf362b7f50e787169ce75373275d9c
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857032"
---
# <a name="walkthrough-adapting-existing-code-to-use-lightweight-tasks"></a>Návod: Přizpůsobení stávajícího kódu pro použití prostých úloh

Toto téma ukazuje, jak přizpůsobit existující kód, který používá rozhraní Windows API k vytvoření a spuštění vlákna používal prostou úlohu.

A *lehký úkol* je úloha, kterou naplánujete přímo z [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) nebo [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) objektu. Prosté úlohy jsou užitečné při přizpůsobení stávajícího kódu pro použití funkce plánování modulu Runtime souběžnosti.

## <a name="prerequisites"></a>Požadavky

Před zahájením tohoto návodu, přečtěte si téma [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující příklad ukazuje typické použití rozhraní API Windows k vytváření a spouštění vlákna. V tomto příkladu [CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread) funkce má být volána `MyThreadFunction` na samostatném vlákně.

### <a name="code"></a>Kód

[!code-cpp[concrt-windows-threads#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_1.cpp)]

### <a name="comments"></a>Komentáře

Tento příklad vytvoří následující výstup.

```Output
Parameters = 50, 100
```

Následující kroky ukazují, jak přizpůsobit v příkladu kódu na využití modulu Runtime souběžnosti provést stejnou úlohu.

### <a name="to-adapt-the-example-to-use-a-lightweight-task"></a>Úprava příkladu tak, aby používal prostou úlohu

1. Přidat `#include` směrnice pro concrt.h souboru záhlaví.

[!code-cpp[concrt-migration-lwt#2](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_2.cpp)]

1. Přidat `using` směrnice pro `concurrency` oboru názvů.

[!code-cpp[concrt-migration-lwt#3](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_3.cpp)]

1. Změňte deklaraci `MyThreadFunction` používat `__cdecl` konvence volání a vrácení `void`.

[!code-cpp[concrt-migration-lwt#4](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_4.cpp)]

1. Upravit `MyData` struktury mají zahrnout [concurrency::event](../../parallel/concrt/reference/event-class.md) objekt, který signalizuje k hlavní aplikaci, že dokončení úlohy.

[!code-cpp[concrt-migration-lwt#5](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_5.cpp)]

1. Nahraďte volání `CreateThread` voláním [concurrency::CurrentScheduler::ScheduleTask](reference/currentscheduler-class.md#scheduletask) metody.

[!code-cpp[concrt-migration-lwt#6](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_6.cpp)]

1. Nahraďte volání `WaitForSingleObject` voláním [concurrency::event::wait](reference/event-class.md#wait) metoda čekat na dokončení úlohy.

[!code-cpp[concrt-migration-lwt#7](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_7.cpp)]

1. Odeberte volání `CloseHandle`.

1. Změnit signaturu definici `MyThreadFunction` tak, aby odpovídaly kroku 3.

[!code-cpp[concrt-migration-lwt#8](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_8.cpp)]

9. Na konci `MyThreadFunction` fungovat, zavolejte [concurrency::event::set](reference/event-class.md#set) metoda na signál pro hlavní aplikaci, že dokončení úlohy.

[!code-cpp[concrt-migration-lwt#9](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_9.cpp)]

10. Odeberte `return` příkaz z `MyThreadFunction`.

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Dokončené následující příklad zobrazuje kód, který používá lehký úkol k volání `MyThreadFunction` funkce.

### <a name="code"></a>Kód

[!code-cpp[concrt-migration-lwt#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_10.cpp)]

### <a name="comments"></a>Komentáře

## <a name="see-also"></a>Viz také:

[Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Scheduler – třída](../../parallel/concrt/reference/scheduler-class.md)
