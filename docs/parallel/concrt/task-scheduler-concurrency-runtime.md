---
title: "Úloha plánovače (Concurrency Runtime) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- oversubscription [Concurrency Runtime]
- task scheduler [Concurrency Runtime], oversubscription
- schedule groups [Concurrency Runtime]
- task scheduler [Concurrency Runtime], lightweight tasks
- task scheduler [Concurrency Runtime]
- lightweight tasks [Concurrency Runtime]
- task scheduler [Concurrency Runtime], scheduler policies
- task scheduler [Concurrency Runtime], schedule groups
- wait function [Concurrency Runtime]
- task scheduler [Concurrency Runtime], scheduler instances
- scheduler instances [Concurrency Runtime]
- scheduler policies [Concurrency Runtime]
- task scheduler [Concurrency Runtime], wait function
ms.assetid: 9aba278c-e0c9-4ede-b7c6-fedf7a365d90
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d2d2d1fa21299867ba7a295ad9ef17759cab6c86
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="task-scheduler-concurrency-runtime"></a>Plánovač úloh (Concurrency Runtime)
Témata v této části dokumentace popisují důležité funkce Plánovač úloh Concurrency Runtime. Plánovač úloh je užitečné, pokud chcete optimalizovat výkon váš stávající kód, který používá Concurrency Runtime.  
  
> [!IMPORTANT]
>  Plánovač úloh není k dispozici z aplikace pro univerzální platformu Windows (UWP). Další informace najdete v tématu [vytváření asynchronních operací v jazyce C++ pro aplikace UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).  
>   
>  V sadě Visual Studio 2015 a novější [concurrency::task](../../parallel/concrt/reference/task-class.md) třídy a souvisejících typů v ppltasks.h použít zachovalo Windows jako jejich plánovače. Toto téma se týká už typy, které jsou definovány v ppltasks.h. Paralelní algoritmy například parallel_for – dál používat jako výchozí plánovač Concurrency Runtime.  
  
> [!TIP]
>  Concurrency Runtime poskytuje výchozí plánovač, a proto není nutné vytvořit ve vaší aplikaci. Protože Plánovač úloh umožňuje optimalizovat výkon aplikací, doporučujeme začínat [paralelní vzory knihovna PPL ()](../../parallel/concrt/parallel-patterns-library-ppl.md) nebo [knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md) Pokud jste nové do Concurrency Runtime.  
  
 Plánovač úloh plány a koordinuje úlohy v době běhu. A *úloh* je jednotka práce, která provádí konkrétní úlohu. Úlohu můžete obvykle běží paralelně s ostatními úkoly. Práce, které se provádí pomocí seskupení položek úloh, paralelní algoritmy a asynchronních agentů jsou všechny úlohy.  
  
 Plánovač úloh spravuje podrobnosti, které se vztahují k efektivní plánování úloh na počítačích, které mají více výpočetní prostředky. Plánovač úloh také používá nejnovější funkce příslušný operační systém. Proto aplikace, které automaticky používají Concurrency Runtime škálování a zlepšení na hardware, který se má rozšířit možnosti.  
  
 [Porovnání se ostatní modely souběžného zpracování](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md) popisuje rozdíly mezi plánování mechanismy preemptivní a spolupráci. Plánovač úloh používá spolupráci plánování a algoritmus krádež pracovní spolu s plánovači preemptivní operačního systému k dosažení maximální využití prostředků zpracování.  
  
 Concurrency Runtime poskytuje výchozí plánovač, takže není nutné spravovat infrastrukturu podrobnosti. Proto obvykle použijete Plánovač úloh přímo. Ale kvality potřebám vaší aplikace, můžete Plánovač úloh vlastní plánování zásad nebo přidružení plánovače poskytnout konkrétní úlohy. Předpokládejme například, že máte paralelní řazení rutiny, která není škálování nad rámec čtyřmi procesory. Můžete použít *zásady plánovače* k vytvoření plánovače, který generuje více než čtyři souběžné úlohy. Rutiny řazení systémem tento plánovač umožňuje další aktivní plánovače všechny zbývající prostředků zpracování.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Instance plánovače](../../parallel/concrt/scheduler-instances.md)|Popisuje instance plánovače a jak používat `concurrency::Scheduler` a `concurrency::CurrentScheduler` třídy k jejich správě. Instance plánovače použijte, pokud chcete přidružit explicitní plánování zásady konkrétní typy úloh.|  
|[Zásady plánovače](../../parallel/concrt/scheduler-policies.md)|Popisuje roli zásady plánovače. Zásady plánovače použijte, pokud chcete řídit strategie používající Plánovač při správě úloh.|  
|[Skupiny plánů](../../parallel/concrt/schedule-groups.md)|Popisuje roli skupiny plánu. Použití skupin plánů, pokud požadujete vysokou míru polohu mezi úlohy, například když skupinu souvisejících úloh těžit z provádění na stejném procesoru uzlu.|  
|[Prosté úlohy](../../parallel/concrt/lightweight-tasks.md)|Popisuje roli prosté úlohy. Prosté úlohy je užitečný v případě přizpůsobení stávajícího kódu pro použití funkce plánování Concurrency Runtime.|  
|[Kontexty](../../parallel/concrt/contexts.md)|Popisuje roli kontextů, `concurrency::wait` funkce a `concurrency::Context` třídy. Tato funkce používejte, když potřebujete řídit při kontexty blokovat, odblokovat a yield nebo pokud chcete povolit Překryvný odběr ve vaší aplikaci.|  
|[Funkce správy paměti](../../parallel/concrt/memory-management-functions.md)|Popisuje `concurrency::Alloc` a `concurrency::Free` funkce. Tyto funkce můžou zlepšit výkon paměti přidělením a způsobem souběžné uvolňování paměti.|  
|[Porovnání s jinými modely souběžného zpracování](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md)|Popisuje rozdíly mezi plánování mechanismy preemptivní a spolupráci.|  
|[Knihovna PPL (Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Popisuje způsob použití různých paralelní vzorů, například paralelní algoritmy ve svých aplikacích.|  
|[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)|Popisuje způsob použití asynchronních agentů ve svých aplikacích.|  
|[Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)|Popisuje Concurrency Runtime, který zjednodušuje paralelní programování a obsahuje odkazy na související témata.|

