---
title: Skupiny plánů
ms.date: 11/04/2016
helpviewer_keywords:
- schedule groups
ms.assetid: 03523572-5891-4d17-89ce-fa795605f28b
ms.openlocfilehash: febcc0a9c7af75801962ea6be687ce87cc5501d4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407910"
---
# <a name="schedule-groups"></a>Skupiny plánů

Tento dokument popisuje roli skupiny plánu v modulu Runtime souběžnosti. A *skupinu plánu* spřáhne nebo seskupuje, související úlohy. Každý Plánovač má jeden nebo více skupin plánů. Použití skupin plánů Pokud vyžadujete vysoký stupeň lokality mezi úkoly, třeba když skupinu úkoly související s výhodou spuštěna ve stejném uzlu procesoru. Naopak použijte instance plánovače, pokud vaše aplikace má požadavky na konkrétní kvalitu, například když chcete omezit množství prostředků pro zpracování, které jsou přiděleny sady úloh. Další informace o instance plánovače naleznete v tématu [instance plánovače](../../parallel/concrt/scheduler-instances.md).

> [!TIP]
>  Poskytuje výchozí plánovač Concurrency Runtime, a proto není nutné vytvořit ve vaší aplikaci. Vzhledem k tomu, že Plánovač úloh umožňuje optimalizovat výkon vašich aplikací, doporučujeme začít s [knihovna paralelních vzorů (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) nebo [asynchronní knihovnou agentů](../../parallel/concrt/asynchronous-agents-library.md) máte nového modulu runtime souběžnosti.

Každý `Scheduler` objekt nemá výchozí skupiny plánu pro každý uzel plánování. A *plánování uzel* mapuje na základní topologie systému. Modul runtime vytvoří jeden uzel plánování pro každý balíček procesoru nebo uzel Non-Uniform k paměti (NUMA), podle toho, která počet je větší. Pokud jste nepřidružujte explicitně úkol k plánu skupiny, Plánovač zvolí která skupina úkol má přidat.

`SchedulingProtocol` Zásadu plánovače ovlivňuje pořadí, ve kterém plánovače spouští úlohy v každé skupině plánu. Když `SchedulingProtocol` je nastavena na `EnhanceScheduleGroupLocality` (což je výchozí hodnota), Plánovač úloh zvolí další úkol z plánu skupiny, která funguje na aktuální úloha dokončí nebo kooperativně provede. Plánovač úloh vyhledá aktuální skupinu plánu pro pracovní předtím, než se přesune na další skupinu k dispozici. Naopak když `SchedulingProtocol` je nastavena na `EnhanceForwardProgress`, Plánovač přesune na další skupinu plánu poté, co každý úkol dokončí nebo provede. Příklad, který porovnává tyto zásady, najdete v části [jak: Použití skupin plánů k ovlivnění pořadí provádění](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).

Modul runtime používá [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) třídy k reprezentování skupiny plánu. Chcete-li vytvořit `ScheduleGroup` objektu, volejte [concurrency::CurrentScheduler::CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup) nebo [concurrency::Scheduler::CreateScheduleGroup](reference/scheduler-class.md#createschedulegroup) metoda. Modul runtime používá mechanismus pro počítání odkazů k řízení životnosti `ScheduleGroup` objekty, stejně jako s `Scheduler` objekty. Když vytvoříte `ScheduleGroup` objektu, modul runtime nastaví odkaz na jeden čítač. [Concurrency::ScheduleGroup::Reference](reference/schedulegroup-class.md#reference) metoda zvýší čítač odkaz o jednu. [Concurrency::ScheduleGroup::Release](reference/schedulegroup-class.md#release) metoda dekrementuje čítače reference o jednu.

Mnoho typů v modulu Runtime souběžnosti umožňují přiřadit objektu společně se skupinu plánování. Například [concurrency::agent](../../parallel/concrt/reference/agent-class.md) třídy a zprávy bloku tříd, například [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md), [concurrency::join](../../parallel/concrt/reference/join-class.md)a souběžnosti::[ časovač](reference/timer-class.md), poskytuje přetížené verze konstruktoru, můžou `ScheduleGroup` objektu. Modul runtime používá `Scheduler` objekt, který je spojen s tímto `ScheduleGroup` objektu k plánování úlohy.

Můžete také použít [concurrency::ScheduleGroup::ScheduleTask](reference/schedulegroup-class.md#scheduletask) metoda naplánování lehký úkol. Další informace o jednoduché úlohy, naleznete v tématu [prostých úloh](../../parallel/concrt/lightweight-tasks.md).

## <a name="example"></a>Příklad

Například, že používá naplánovat skupiny k řízení pořadí provádění úloh, naleznete v tématu [jak: Použití skupin plánů k ovlivnění pořadí provádění](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).

## <a name="see-also"></a>Viz také:

[Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Instance plánovače](../../parallel/concrt/scheduler-instances.md)<br/>
[Postupy: Použití skupin plánů k ovlivnění pořadí provádění](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)
