---
title: 'Postupy: Použití skupin plánů k ovlivnění pořadí provádění'
ms.date: 11/04/2016
helpviewer_keywords:
- schedule groups, using [Concurrency Runtime]
- using schedule groups [Concurrency Runtime]
ms.assetid: 73124194-fc3a-491e-a23f-fbd7b5a4455c
ms.openlocfilehash: 84829664603999893f32caab39af250059bf9788
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141920"
---
# <a name="how-to-use-schedule-groups-to-influence-order-of-execution"></a>Postupy: Použití skupin plánů k ovlivnění pořadí provádění

V Concurrency Runtime je pořadí, ve kterém jsou úkoly plánovány, nedeterministické. Zásady plánování ale můžete použít k ovlivnění pořadí, ve kterém se úlohy spouštějí. V tomto tématu se dozvíte, jak používat skupiny plánů společně se zásadami plánovače [Concurrency:: SchedulingProtocol](reference/concurrency-namespace-enums.md#policyelementkey) , aby bylo ovlivněno pořadí, ve kterém se úlohy spouštějí.

V příkladu se dvakrát spustí sada úloh, z nichž každá má jinou zásadu plánování. Obě zásady omezují maximální počet zpracovávaných prostředků na dva. První spuštění používá zásady `EnhanceScheduleGroupLocality`, což je výchozí nastavení, přičemž druhý běh používá zásady `EnhanceForwardProgress`. V rámci zásad `EnhanceScheduleGroupLocality` spustí Plánovač všechny úlohy v jedné skupině plánů do doby, než každý úkol dokončí nebo neposkytne. V rámci zásad `EnhanceForwardProgress` se Plánovač při kruhovém dotazování dokončí na další skupinu plánů, a to po dokončení jednoho úkolu nebo výsledkem.

Když každá skupina plánu obsahuje související úlohy, zásada `EnhanceScheduleGroupLocality` obvykle vede ke zvýšení výkonu, protože mezi úlohami se zachovává mezipamětí mezipaměti. Zásady `EnhanceForwardProgress` umožňují, aby úkoly probíhaly v průběhu plánování a byly užitečné v případě, že budete vyžadovat, aby plánování v rámci skupin plánů bylo spravedlivé.

## <a name="example"></a>Příklad

Tento příklad definuje třídu `work_yield_agent`, která je odvozena z [: concurrency:: Agent](../../parallel/concrt/reference/agent-class.md). Třída `work_yield_agent` provede pracovní jednotku, vypočítá aktuální kontext a pak provede další pracovní jednotku. Agent používá funkci [Concurrency:: wait](reference/concurrency-namespace-functions.md#wait) k kooperativnímu získání aktuálního kontextu, aby bylo možné spustit ostatní kontexty.

Tento příklad vytvoří čtyři objekty `work_yield_agent`. Pro ilustraci, jak nastavit zásady plánovače tak, aby ovlivnilo pořadí, ve kterém se agenti spouštějí, příklad přidruží první dva agenty jednu skupinu plánů a další dva agenty s jinou skupinou plánování. V příkladu se používá metoda [Concurrency:: CurrentScheduler:: CreateScheduleGroup –](reference/currentscheduler-class.md#createschedulegroup) k vytvoření objektů [Concurrency:: Schedule](../../parallel/concrt/reference/schedulegroup-class.md) . Tento příklad spustí všechny čtyři agenty dvakrát, pokaždé s jinou zásadou plánování.

[!code-cpp[concrt-scheduling-protocol#1](../../parallel/concrt/codesnippet/cpp/how-to-use-schedule-groups-to-influence-order-of-execution_1.cpp)]

Tento příklad vytvoří následující výstup.

```Output
Using EnhanceScheduleGroupLocality...
group 0,
    task 0: first loop...
group 0,
    task 1: first loop...
group 0,
    task 0: waiting...
group 1,
    task 0: first loop...
group 0,
    task 1: waiting...
group 1,
    task 1: first loop...
group 1,
    task 0: waiting...
group 0,
    task 0: second loop...
group 1,
    task 1: waiting...
group 0,
    task 1: second loop...
group 0,
    task 0: finished...
group 1,
    task 0: second loop...
group 0,
    task 1: finished...
group 1,
    task 1: second loop...
group 1,
    task 0: finished...
group 1,
    task 1: finished...

Using EnhanceForwardProgress...
group 0,
    task 0: first loop...
group 1,
    task 0: first loop...
group 0,
    task 0: waiting...
group 0,
    task 1: first loop...
group 1,
    task 0: waiting...
group 1,
    task 1: first loop...
group 0,
    task 1: waiting...
group 0,
    task 0: second loop...
group 1,
    task 1: waiting...
group 1,
    task 0: second loop...
group 0,
    task 0: finished...
group 0,
    task 1: second loop...
group 1,
    task 0: finished...
group 1,
    task 1: second loop...
group 0,
    task 1: finished...
group 1,
    task 1: finished...
```

Obě zásady vytváří stejnou posloupnost událostí. Zásady, které používá `EnhanceScheduleGroupLocality`, však spustí obě agenty, kteří jsou součástí první skupiny plán, než spustí agenty, kteří jsou součástí druhé skupiny. Zásada, která používá `EnhanceForwardProgress` spustí jednoho agenta z první skupiny a potom spustí prvního agenta ve druhé skupině.

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo ho vložte do souboru s názvem `scheduling-protocol.cpp` a potom spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

> **CL. exe/EHsc Scheduling-Protocol. cpp**

## <a name="see-also"></a>Viz také

[Skupiny plánů](../../parallel/concrt/schedule-groups.md)<br/>
[Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)
