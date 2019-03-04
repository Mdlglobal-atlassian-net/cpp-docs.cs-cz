---
title: 'Postupy: Použití skupin plánů k ovlivnění pořadí provádění'
ms.date: 11/04/2016
helpviewer_keywords:
- schedule groups, using [Concurrency Runtime]
- using schedule groups [Concurrency Runtime]
ms.assetid: 73124194-fc3a-491e-a23f-fbd7b5a4455c
ms.openlocfilehash: 99e0383fc8d16f3eeb6e43e59424ab0984ee5c14
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284356"
---
# <a name="how-to-use-schedule-groups-to-influence-order-of-execution"></a>Postupy: Použití skupin plánů k ovlivnění pořadí provádění

V modulu Runtime souběžnosti je Nedeterministický pořadí, ve kterém úkoly jsou naplánovány. Plánování zásad můžete však použít k ovlivnění pořadí, ve kterém je spuštěný úkoly. Toto téma ukazuje způsob použití skupin plánů spolu s [concurrency::SchedulingProtocol](reference/concurrency-namespace-enums.md#policyelementkey) zásadu plánovače k ovlivnění pořadí, ve kterém je spuštěný úkoly.

V příkladu spustí sadu úloh dvakrát, každý s různé zásady plánování. Obě zásady omezit maximální počet prostředků pro zpracování do dvou. Při prvním spuštění používá `EnhanceScheduleGroupLocality` zásad, což je výchozí a druhá spuštění používá `EnhanceForwardProgress` zásad. V části `EnhanceScheduleGroupLocality` zásad, Plánovač spustí všechny úlohy ve skupině pro jeden plán dokud každý úkol dokončí nebo provede. V části `EnhanceForwardProgress` zásad, Plánovač přesune do další skupiny plánu způsobem kruhové dotazování po dokončení pouze jeden úkol nebo provede.

Když každá skupina plánu obsahuje související úlohy `EnhanceScheduleGroupLocality` zásad obvykle za následek vylepšení výkonu vzhledem k tomu, že umístění mezipaměti je zachováno mezi úkoly. `EnhanceForwardProgress` Zásad umožňuje úkoly a postup směrem vpřed a je užitečné, když budete potřebovat plánování rovnost napříč skupinami pro plán.

## <a name="example"></a>Příklad

Tento příklad definuje `work_yield_agent` třída, která je odvozena z [concurrency::agent](../../parallel/concrt/reference/agent-class.md). `work_yield_agent` Třídy provádějí určitou jednotku práce, vrací aktuální kontext a poté provede jinou jednotku práce. Agent použije [concurrency::wait](reference/concurrency-namespace-functions.md#wait) funkce tak, aby mohly běžet jiných kontextech kooperativně výnosu aktuálního kontextu.

Tento příklad vytvoří čtyři `work_yield_agent` objekty. Si ukážeme, jak nastavit zásady plánovače na vliv na pořadí, ve kterém je spuštěný agenty, v příkladu přidruží první dva agenty skupiny jeden plán a další dva agenty s jinou skupinu plánu. V příkladu se používá [concurrency::CurrentScheduler::CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup) metodu pro vytvoření [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) objekty. V příkladu spustí všechny čtyři agenty dvakrát, pokaždé, když se různé zásady plánování.

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

Obě zásady vytvořit stejnou posloupnost událostí. Nicméně jsou zásady, která používá `EnhanceScheduleGroupLocality` spustí oba agenty, které jsou součástí první skupinu plánu před spuštěním agenty, které jsou součástí druhé skupině. Zásady, které využívají `EnhanceForwardProgress` začne jednoho agenta z první skupinu a pak spustí první agent v druhé skupině.

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `scheduling-protocol.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe /EHsc scheduling-protocol.cpp**

## <a name="see-also"></a>Viz také:

[Skupiny plánů](../../parallel/concrt/schedule-groups.md)<br/>
[Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)
