---
title: Skupiny plánů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- schedule groups
ms.assetid: 03523572-5891-4d17-89ce-fa795605f28b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c1395fbc58d8a4d1d06cd93eea21c0f3d2dec8c6
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="schedule-groups"></a>Skupiny plánů
Tento dokument popisuje roli skupiny plánu v Concurrency Runtime. A *plán skupiny* způsobem přidružuje nebo skupin, souvisejících úloh společně. Všechny plánovače má jeden nebo více skupin plán. Použití skupin plánů, pokud požadujete vysokou míru polohu mezi úlohy, například když skupinu souvisejících úloh těžit z provádění na stejném procesoru uzlu. Instance plánovače naopak používejte, když vaše aplikace má požadavky na konkrétní kvalitu, například pokud chcete omezit množství prostředků zpracování, které jsou přiděleny sadu úloh. Další informace o instance plánovače najdete v tématu [instance plánovače](../../parallel/concrt/scheduler-instances.md).  
  
> [!TIP]
>  Concurrency Runtime poskytuje výchozí plánovač, a proto není nutné vytvořit ve vaší aplikaci. Protože Plánovač úloh umožňuje optimalizovat výkon aplikací, doporučujeme začínat [paralelní vzory knihovna PPL ()](../../parallel/concrt/parallel-patterns-library-ppl.md) nebo [knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md) Pokud jste nové do Concurrency Runtime.  
  
 Každý `Scheduler` objekt má výchozí skupiny plánu pro každý uzel plánování. A *plánování uzlu* se mapuje na základní topologie systému. Modul runtime vytvoří uzel Non-Uniform k paměti (NUMA) nebo jedna plánování uzel každého balíčku pro procesor, podle toho, která počet je větší. Pokud není výslovně úlohu k přidružíte skupinu plán, zvolí Plánovač které skupiny přidat úlohy.  
  
 `SchedulingProtocol` Zásad plánovače ovlivňuje pořadí, ve kterém plánovač provádí úlohy v každé skupině plán. Když `SchedulingProtocol` je nastaven na `EnhanceScheduleGroupLocality` (což je výchozí nastavení), plánovače úloh zvolí další úlohy ze skupiny plán, který ho pracuje na při dokončení aktuální úlohy nebo spolupráce při vypočítá. Plánovač úloh vyhledá aktuální skupiny plánu pro pracovní předtím, než ji přesune na další skupinu k dispozici. Na druhé straně, když `SchedulingProtocol` je nastaven na `EnhanceForwardProgress`, Plánovač přesune na další skupinu plán po dokončení každé úlohy nebo dosáhnout. Příklad, který porovnává tyto zásady, naleznete v části [postupy: použití skupin plánů vliv pořadí spouštění](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).  
  

 Modul runtime používá [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) třída k reprezentování skupiny plánu. Chcete-li vytvořit `ScheduleGroup` objektu, volání [concurrency::CurrentScheduler::CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup) nebo [concurrency::Scheduler::CreateScheduleGroup](reference/scheduler-class.md#createschedulegroup) metoda. Modul runtime používá mechanismus počítání odkaz k řízení životnost `ScheduleGroup` objekty, stejně jako s `Scheduler` objekty. Při vytváření `ScheduleGroup` objektu modulu runtime nastaví odkaz na jeden čítač. [Concurrency::ScheduleGroup::Reference](reference/schedulegroup-class.md#reference) metoda zvýší čítač reference o jednu. [Concurrency::ScheduleGroup::Release](reference/schedulegroup-class.md#release) metoda snižuje čítač reference o jednu.  
  
 Mnoho typů v Concurrency Runtime umožňuje přidružit objekt společně s skupinu plánu. Například [concurrency::agent](../../parallel/concrt/reference/agent-class.md) třídy a zpráva bloku třídy, jako [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md), [concurrency::join](../../parallel/concrt/reference/join-class.md)a souběžnost::[ časovač](reference/timer-class.md), poskytovat přetížené verze konstruktoru, které trvat `ScheduleGroup` objektu. Modul runtime používá `Scheduler` objekt, který je přidružen to `ScheduleGroup` objekt, který chcete naplánovat úlohu.  
  
 Můžete také [concurrency::ScheduleGroup::ScheduleTask](reference/schedulegroup-class.md#scheduletask) metoda naplánování prosté úlohy. Další informace o prosté úlohy najdete v tématu [prosté úlohy](../../parallel/concrt/lightweight-tasks.md).  

  
## <a name="example"></a>Příklad  
 Příklad, používá naplánovali skupiny k řízení pořadí provádění úloh, naleznete v části [postupy: použití skupin plánů vliv pořadí spouštění](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).  
  
## <a name="see-also"></a>Viz také  
 [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Instance plánovače](../../parallel/concrt/scheduler-instances.md)   
 [Postupy: Použití skupin plánů k ovlivnění pořadí provádění](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)

