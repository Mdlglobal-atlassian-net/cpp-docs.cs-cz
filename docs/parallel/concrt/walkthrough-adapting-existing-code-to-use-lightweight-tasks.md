---
title: 'Návod: Přizpůsobení stávajícího kódu pro použití prostých úloh | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- using lightweight tasks [Concurrency Runtime]
- lightweight tasks, using [Concurrency Runtime]
ms.assetid: 1edfe818-d274-46de-bdd3-e92967c9bbe0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c4fe3bb4b576bd1f9160b4a3cdc3142be5cdff05
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="walkthrough-adapting-existing-code-to-use-lightweight-tasks"></a>Návod: Přizpůsobení stávajícího kódu pro použití prostých úloh
Toto téma ukazuje, jak přizpůsobit existující kód, který používá rozhraní API systému Windows k vytvoření a provedení vlákno pro použití prostých úloh.  
  
 A *prostých úloh* je úkol, který můžete naplánovat přímo z [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) nebo [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) objektu. Prosté úlohy je užitečný v případě přizpůsobení stávajícího kódu pro použití funkce plánování Concurrency Runtime.  
  
## <a name="prerequisites"></a>Požadavky  
 Než začnete tohoto průvodce, přečtěte si téma [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ilustruje typickému využití rozhraní API systému Windows k vytváření a spouštění vlákna. Tento příklad používá [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) funkce k volání `MyThreadFunction` na samostatné vlákno.  
  
### <a name="code"></a>Kód  
 [!code-cpp[concrt-windows-threads#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_1.cpp)]  
  
### <a name="comments"></a>Komentáře  
 Tento příklad vytvoří následující výstup.  
  
```Output  
Parameters = 50, 100  
```  
  
 Následující kroky ukazují, jak přizpůsobit příklad kódu pomocí Concurrency Runtime provést stejný úkol.  
  
### <a name="to-adapt-the-example-to-use-a-lightweight-task"></a>Úprava příkladu tak, aby používal prostou úlohu  
  
1.  Přidat `#include` direktivy pro concrt.h soubor hlavičky.  
  
 [!code-cpp[concrt-migration-lwt#2](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_2.cpp)]  
  
2.  Přidat `using` direktivy pro `concurrency` oboru názvů.  
  
 [!code-cpp[concrt-migration-lwt#3](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_3.cpp)]  
  
3.  Změňte deklaraci `MyThreadFunction` používat `__cdecl` konvence volání a vrátit `void`.  
  
 [!code-cpp[concrt-migration-lwt#4](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_4.cpp)]  
  
4.  Změnit `MyData` struktura zahrnout [concurrency::event](../../parallel/concrt/reference/event-class.md) objekt, který k hlavní aplikaci signalizuje, že dokončení úlohy.  
  
 [!code-cpp[concrt-migration-lwt#5](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_5.cpp)]  
  
5.  Nahraďte volání `CreateThread` pomocí volání [concurrency::CurrentScheduler::ScheduleTask](reference/currentscheduler-class.md#scheduletask) metoda.  

  
 [!code-cpp[concrt-migration-lwt#6](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_6.cpp)]  
  

6.  Nahraďte volání `WaitForSingleObject` pomocí volání [concurrency::event::wait](reference/event-class.md#wait) metoda čekat na dokončení úlohy.  

 [!code-cpp[concrt-migration-lwt#7](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_7.cpp)]  
  
7.  Odeberte volání `CloseHandle`.  
  
8.  Změnit podpis definice `MyThreadFunction` tak, aby odpovídaly krok 3.  
  
 [!code-cpp[concrt-migration-lwt#8](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_8.cpp)]  
  
9. Na konci `MyThreadFunction` fungovat, volání [concurrency::event::set](reference/event-class.md#set) metoda signál k hlavní aplikaci dokončení úlohy.  
  
 [!code-cpp[concrt-migration-lwt#9](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_9.cpp)]  
  
10. Odeberte `return` příkaz z `MyThreadFunction`.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující dokončené příklad ukazuje kód, který používá prostých úloh k volání `MyThreadFunction` funkce.  
  
### <a name="code"></a>Kód  
 [!code-cpp[concrt-migration-lwt#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_10.cpp)]  
  
### <a name="comments"></a>Komentáře  
  
## <a name="see-also"></a>Viz také  
 [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Scheduler – třída](../../parallel/concrt/reference/scheduler-class.md)
