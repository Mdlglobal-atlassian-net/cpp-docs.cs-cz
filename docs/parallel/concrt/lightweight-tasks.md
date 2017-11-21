---
title: "Prosté úlohy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: lightweight tasks
ms.assetid: b6dcfc7a-9fa9-4144-96a6-2845ea272017
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9b9caa028d7f870ecdd6c67503c6bc9448cff1d3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="lightweight-tasks"></a>Prosté úlohy
Tento dokument popisuje roli prosté úlohy v Concurrency Runtime. A *prostých úloh* je úkol, který můžete naplánovat přímo z `concurrency::Scheduler` nebo `concurrency::ScheduleGroup` objektu. Prosté úlohy se podobá funkci, která zadáte na rozhraní API systému Windows [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) funkce. Prosté úlohy proto jsou užitečné při přizpůsobení stávajícího kódu pro použití funkce plánování Concurrency Runtime. Concurrency Runtime samotné používá prosté úlohy k plánování asynchronních agentů a odesílání zpráv mezi asynchronní bloky zpráv.  
  
> [!TIP]
>  Concurrency Runtime poskytuje výchozí plánovač, a proto není nutné vytvořit ve vaší aplikaci. Protože Plánovač úloh umožňuje optimalizovat výkon aplikací, doporučujeme začínat [paralelní vzory knihovna PPL ()](../../parallel/concrt/parallel-patterns-library-ppl.md) nebo [knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md) Pokud jste nové do Concurrency Runtime.  
  
 Prosté úlohy provádění menší režii než asynchronních agentů a skupiny úloh. Například modul runtime neinformuje můžete po dokončení prostých úloh. Kromě toho modul runtime nemá catch nebo zpracování výjimek, které jsou vyvolány z prosté úlohy. Další informace o zpracování výjimek a prosté úlohy najdete v tématu [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).  
  
 Pro většinu úloh doporučujeme použít robustnější funkce, jako je skupin úloh a paralelní algoritmy vzhledem k tomu, které vám umožní snadno rozdělit složité úlohy na více základní ty. Další informace o skupinách úloh najdete v tématu [paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Další informace o paralelní algoritmy najdete v tématu [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).  
  
 Chcete-li vytvořit úlohu lightweight, zavolejte [concurrency::ScheduleGroup::ScheduleTask](reference/schedulegroup-class.md#scheduletask), [concurrency::CurrentScheduler::ScheduleTask](reference/currentscheduler-class.md#scheduletask), nebo [concurrency::Scheduler::ScheduleTask ](reference/scheduler-class.md#scheduletask) metoda. Počkat na dokončení prosté úlohy, počkejte Plánovač nadřazené vypnutí nebo pomocí mechanismus synchronizace, jako například [concurrency::event](../../parallel/concrt/reference/event-class.md) objektu.  
  
## <a name="example"></a>Příklad  
 Příklad, který ukazuje, jak k přizpůsobení stávajícího kódu pro použití prostých úloh, naleznete v části [návod: přizpůsobení stávajícího kódu pro použití prostých úloh](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md).  
  
## <a name="see-also"></a>Viz také  
 [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Návod: Přizpůsobení stávajícího kódu pro použití prostých úloh](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)

