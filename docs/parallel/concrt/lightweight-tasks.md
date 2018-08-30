---
title: Prosté úlohy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- lightweight tasks
ms.assetid: b6dcfc7a-9fa9-4144-96a6-2845ea272017
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8548412436be6e505c0ea08a2991e6948496f592
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210281"
---
# <a name="lightweight-tasks"></a>Prosté úlohy
Tento dokument popisuje využití jednoduché úlohy v modulu Runtime souběžnosti. A *lehký úkol* je úloha, kterou naplánujete přímo z `concurrency::Scheduler` nebo `concurrency::ScheduleGroup` objektu. Lehký úkol vypadá podobně jako funkce, které poskytují rozhraní Windows API [CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread) funkce. Prosté úlohy proto jsou užitečné při přizpůsobení stávajícího kódu pro použití funkce plánování modulu Runtime souběžnosti. Samotný modul Concurrency Runtime používá k plánování asynchronních agentů a zasílání zpráv mezi asynchronní bloky zpráv jednoduché úlohy.  
  
> [!TIP]
>  Poskytuje výchozí plánovač Concurrency Runtime, a proto není nutné vytvořit ve vaší aplikaci. Vzhledem k tomu, že Plánovač úloh umožňuje optimalizovat výkon vašich aplikací, doporučujeme začít s [knihovna paralelních vzorů (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) nebo [asynchronní knihovnou agentů](../../parallel/concrt/asynchronous-agents-library.md) máte nového modulu runtime souběžnosti.  
  
 Prosté úlohy provést menší nároky na než asynchronní agenti a skupiny úloh. Například modul runtime neinformuje můžete po dokončení lehký úkol. Kromě toho modul runtime nepodporuje catch ani zpracovat výjimky, které jsou vyvolány z lehký úkol. Další informace o zpracování výjimek a jednoduché úlohy, naleznete v tématu [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).  
  
 Pro většinu úloh doporučujeme, že používáte více robustní funkce, jako jsou skupiny úloh a paralelních algoritmů protože umožňují snadněji rozdělit složité úlohy na ty informace o jednodušší. Další informace o skupinách úkolů najdete v tématu [paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Další informace o paralelních algoritmech naleznete v tématu [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).  
  
 Chcete-li vytvořit lehký úkol, zavolejte [concurrency::ScheduleGroup::ScheduleTask](reference/schedulegroup-class.md#scheduletask), [concurrency::CurrentScheduler::ScheduleTask](reference/currentscheduler-class.md#scheduletask), nebo [concurrency::Scheduler::ScheduleTask ](reference/scheduler-class.md#scheduletask) metody. Čekání na dokončení nenáročné úlohy, počkejte Plánovač nadřazené vypnout nebo pomocí mechanismu synchronizace, jako [concurrency::event](../../parallel/concrt/reference/event-class.md) objektu.  
  
## <a name="example"></a>Příklad  
 Příklad, který ukazuje, jak přizpůsobit existující kód používal prostou úlohu, naleznete v tématu [návod: přizpůsobení stávajícího kódu pro použití prostých úloh](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md).  
  
## <a name="see-also"></a>Viz také  
 [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Návod: Přizpůsobení stávajícího kódu pro použití prostých úloh](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)

