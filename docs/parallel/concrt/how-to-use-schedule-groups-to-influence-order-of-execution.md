---
title: 'Postupy: použití skupin plánů k ovlivnění pořadí provádění | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- schedule groups, using [Concurrency Runtime]
- using schedule groups [Concurrency Runtime]
ms.assetid: 73124194-fc3a-491e-a23f-fbd7b5a4455c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c41617f562a0abefdecf74d52e7a886ad6326f9e
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691193"
---
# <a name="how-to-use-schedule-groups-to-influence-order-of-execution"></a>Postupy: Použití skupin plánů k ovlivnění pořadí provádění
Pořadí, ve kterém jsou naplánované úlohy v Concurrency Runtime je Nedeterministický. Plánování zásad můžete však použít k ovlivnění pořadí, ve kterém se spouštět úlohy. Toto téma ukazuje způsob použití skupin plánů společně s [concurrency::SchedulingProtocol](reference/concurrency-namespace-enums.md#policyelementkey) zásad plánovače k ovlivnění pořadí, ve kterém se spouštět úlohy.  

  
 V příkladu spustí sadu úloh dvakrát, každý s různé zásady plánování. Obě zásady omezení maximální počet zpracování prostředků ke dvěma. První spuštění používá `EnhanceScheduleGroupLocality` zásad, který je výchozí a druhý spusťte používá `EnhanceForwardProgress` zásad. V části `EnhanceScheduleGroupLocality` zásady, Plánovač spustí všechny úlohy ve skupině jeden plán až do dokončení každé úlohy nebo dosáhnout. V části `EnhanceForwardProgress` zásad plánovače přesune na další skupinu plán způsobem kruhového dotazování po dokončení právě jednu úlohu nebo vypočítá.  
  
 Když každá skupina plánu obsahuje souvisejících úloh `EnhanceScheduleGroupLocality` zásad obvykle dochází lepší výkon, protože polohu mezipaměti se zachová, i mezi úkoly. `EnhanceForwardProgress` Zásady umožňuje, aby postup směrem vpřed úlohy a je užitečné, když potřebujete plánování rovnosti v rámci skupiny plánu.  
  
## <a name="example"></a>Příklad  
 Tento příklad definuje `work_yield_agent` třída, která je odvozena z [concurrency::agent](../../parallel/concrt/reference/agent-class.md). `work_yield_agent` Třída provádí pracovní jednotka, vypočítá aktuální kontext a potom provede další jednotky práce. Agent používá [concurrency::wait](reference/concurrency-namespace-functions.md#wait) funkce, která se tak, aby jiných kontextech spolupráce při yield aktuálního kontextu.  
  
 Tento příklad vytvoří čtyři `work_yield_agent` objekty. Pro ilustraci, jak nastavit zásady plánovače ovlivnit pořadí, ve kterém agenty spouštět, přidruží příklad první dva agenty jeden plán skupině a tito dva agenti s jinou skupinu plánu. V příkladu se používá [concurrency::CurrentScheduler::CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup) metodu pro vytvoření [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) objekty. V příkladu spustí všechny čtyři agenty dvakrát, pokaždé, když se různé zásady plánování.  
  
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
  
 Obě zásady vytvořit stejné posloupnost událostí. Ale zásady používající `EnhanceScheduleGroupLocality` spustí i agenty, kteří jsou součástí první skupinu plán před spuštěním agentů, které jsou součástí druhé skupině. Zásadu, která používá `EnhanceForwardProgress` začne jednoho agenta z první skupinu a pak spustí první agenta ve druhé skupině.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `scheduling-protocol.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **plánování /EHsc cl.exe-protocol.cpp**  
  
## <a name="see-also"></a>Viz také  
 [Skupiny plánů](../../parallel/concrt/schedule-groups.md)   
 [Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)

