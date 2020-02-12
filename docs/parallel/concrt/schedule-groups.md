---
title: Skupiny plánů
ms.date: 11/04/2016
helpviewer_keywords:
- schedule groups
ms.assetid: 03523572-5891-4d17-89ce-fa795605f28b
ms.openlocfilehash: 1765c10f4cf8fe499aed1a140d2bba1ecaaf2300
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142301"
---
# <a name="schedule-groups"></a>Skupiny plánů

Tento dokument popisuje roli skupin plánů v Concurrency Runtime. *Skupina plánování* spřáhne nebo skupiny, související úkoly společně. Každý Plánovač má jednu nebo více skupin plánování. Skupiny plánů se používají, když budete potřebovat vysoký stupeň lokálních operací mezi úkoly, například když se skupina souvisejících úloh vykonává ve stejném uzlu procesoru. Naopak použijte instance Scheduleru, pokud má vaše aplikace specifické požadavky na kvalitu, například když chcete omezit množství prostředků zpracování, které jsou přiděleny sadě úkolů. Další informace o instancích Scheduleru najdete v tématu [instance Scheduleru](../../parallel/concrt/scheduler-instances.md).

> [!TIP]
> Concurrency Runtime poskytuje výchozí Plánovač, a proto není nutné ho v aplikaci vytvořit. Vzhledem k tomu, že Plánovač úloh pomáhá doladit výkon aplikací, doporučujeme začít s knihovnou [paralelních vzorů (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) nebo s [knihovnou asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md) , pokud s Concurrency Runtime začínáte.

Každý objekt `Scheduler` má výchozí skupinu Schedule pro každý uzel plánování. *Uzel plánování* se mapuje na podkladovou topologii systému. Modul runtime vytvoří jeden plánovací uzel pro každý balíček procesoru nebo uzel neuniformní paměti architektury (NUMA), podle toho, kolik je větší. Pokud neprovedete explicitně přidružení úlohy ke skupině plánů, Plánovač zvolí, do které skupiny se má úkol přidat.

Zásady plánovače `SchedulingProtocol` mají vliv na pořadí, ve kterém plánovač spouští úlohy v každé skupině plánů. Pokud je `SchedulingProtocol` nastaveno na `EnhanceScheduleGroupLocality` (což je výchozí nastavení), Plánovač úloh zvolí další úkol ze skupiny plán, na které pracuje, když aktuální úkol dokončí nebo spolupracuje. Plánovač úloh vyhledá aktuální skupinu plánu pro práci předtím, než se přesune k další dostupné skupině. Naopak když je `SchedulingProtocol` nastavená na `EnhanceForwardProgress`, Plánovač se po dokončení každého úkolu přesune k další skupině Schedule. Příklad, který porovnává tyto zásady, naleznete v tématu [How to: use Schedule Groups to ovlivnit pořadí provádění](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).

Modul runtime používá třídu [Concurrency:: Schedule](../../parallel/concrt/reference/schedulegroup-class.md) ke znázornění skupin plánování. Chcete-li vytvořit objekt `ScheduleGroup`, zavolejte metodu [Concurrency:: CurrentScheduler:: CreateScheduleGroup –](reference/currentscheduler-class.md#createschedulegroup) nebo [Concurrency:: Scheduler:: CreateScheduleGroup –](reference/scheduler-class.md#createschedulegroup) . Modul runtime používá mechanismus počítání odkazů k řízení životnosti `ScheduleGroup` objektů, stejně jako s objekty `Scheduler`. Při vytváření objektu `ScheduleGroup` nastaví modul runtime referenční čítač na jednu. Metoda [Concurrency:: Schedule:: Reference](reference/schedulegroup-class.md#reference) zvyšuje referenční čítač o jeden. Metoda [Concurrency:: Schedule:: Release](reference/schedulegroup-class.md#release) sníží odkazový čítač o jednu.

Mnoho typů v Concurrency Runtime umožňuje přidružit objekt společně se skupinou plánování. Například třídy [Concurrency:: Agent](../../parallel/concrt/reference/agent-class.md) a bloku zpráv, například [concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md), [Concurrency:: JOIN](../../parallel/concrt/reference/join-class.md)a concurrency::[Timer](reference/timer-class.md), poskytují přetížené verze konstruktoru, který přijímá objekt `ScheduleGroup`. Modul runtime používá objekt `Scheduler`, který je přidružen k tomuto objektu `ScheduleGroup` k naplánování úlohy.

K naplánování zjednodušené úlohy můžete také použít metodu [Concurrency:: Schedule:: ScheduleTask –](reference/schedulegroup-class.md#scheduletask) . Další informace o nenáročných úlohách najdete v tématu [odlehčené úlohy](../../parallel/concrt/lightweight-tasks.md).

## <a name="example"></a>Příklad

Příklad, který používá skupiny Schedule k řízení pořadí provádění úloh, naleznete v tématu [How to: use Schedule Groups to ovlivnit pořadí provádění](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).

## <a name="see-also"></a>Viz také

[Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Instance plánovače](../../parallel/concrt/scheduler-instances.md)<br/>
[Postupy: Použití skupin plánů k ovlivnění pořadí provádění](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)
