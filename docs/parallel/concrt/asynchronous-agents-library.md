---
title: "Knihovna asynchronních agentů | Microsoft Docs"
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
- Agents Library
- Asynchronous Agents Library
ms.assetid: d2a72a31-8ba6-4220-ad7a-e403a6acaa42
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: be12f47a6fb33350137a8f9b1c78ff75519c8af7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="asynchronous-agents-library"></a>Knihovna asynchronních agentů
Knihovna asynchronních agentů (nebo jenom *knihovna agentů*) poskytuje programovací model, který umožňuje zvýšit robustnost vývoj aplikace s povolenými souběžnosti. Knihovna agentů je knihovny šablon jazyka C++, který podporuje služby založené na objektu actor programovací model a zprávy v procesu předávání pro hrubý toku dat a paralelní zpracování úlohy. Knihovna agentů je založený na plánování a prostředků součásti správy Concurrency Runtime.  
  
## <a name="programming-model"></a>Programovací model  
 Knihovna agentů poskytuje alternativy do sdíleného stavu tím, že umožňuje připojení izolované komponenty přes model asynchronní komunikaci, která je založená na toku dat místo tok řízení. *Toku dat* odkazuje programování modelu, kde jsou vytvářeny výpočtů, když všechny požadované dat je k dispozici. *řízení toku* odkazuje na programovací model, kde jsou vytvářeny výpočtů v předurčeném pořadí.  
  
 Programovací model toku dat souvisí s koncept *předávání zpráv*, kde nezávislé komponenty programu vzájemnou komunikaci odesláním zprávy.  
  
 Knihovna agentů se skládá ze tří součástí: *asynchronních agentů*, *asynchronní bloky zpráv*, a *funkce předávání zpráv*. Agenti uchování stavu a používat bloky zpráv a funkce předávání zpráv pro komunikaci mezi sebou a se externích součástí. Funkce pro předávání zpráv umožňují agentům odesílat a přijímat zprávy do a z externích součástí. Asynchronní bloky zpráv podržte zprávy a aktivovat agenty ke komunikaci synchronizované způsobem.  
  
 Následující obrázek znázorňuje jak dva agenti použití bloky zpráv a funkce předávání zpráv pro komunikaci. V tomto obrázku `agent1` odešle zprávu do `agent2` pomocí [concurrency::send](reference/concurrency-namespace-functions.md#send) funkce a [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) objektu. `agent2`používá [concurrency::receive](reference/concurrency-namespace-functions.md#receive) funkce na tuto zprávu přečíst. `agent2`stejnou metodu používá k odeslání zprávy do `agent1`. Přerušovanou šipky představují tok dat mezi agenty. Plnou šipky připojit k bloky zpráv, které budou zápisu nebo čtení z agentů.  
  
 ![Součástí knihovna agentů](../../parallel/concrt/media/agent_librarycomp.png "agent_librarycomp")  
  
 Příklad kódu, který implementuje tomto obrázku je znázorněno dále v tomto tématu.  
  
 Programovací model agenta má několik výhod oproti jiné souběžnosti a synchronizace mechanismy, například události. Jednou z výhod je, že pomocí předávání zpráv přenést změny stavu mezi objekty, můžete izolovat přístup ke sdíleným prostředkům a tím zlepšují škálovatelnost. Předávání zpráv výhodou je, že dojde ke svázání synchronizace místo příkazů do objektu externí synchronizace dat. To zjednodušuje přenos dat mezi součástmi a můžete eliminovat programovací chyby ve svých aplikacích.  
  
## <a name="when-to-use-the-agents-library"></a>Když použít knihovnu agentů  
 Knihovna agentů použijte, když máte více operací, které musí vzájemnou komunikaci asynchronně. Bloky zpráv a funkce pro předávání zpráv umožňuje zapsat paralelní aplikace bez nutnosti synchronizace mechanismy, například zámky. Díky tomu se můžete soustředit na aplikační logiku.  
  
 Agent programovací model se často používá k vytvoření *datových kanálů* nebo *sítě*. Datový kanál je několika komponent, z nichž každá provádí konkrétní úlohu, která přispívá ke větší cíl. Každá komponenta v kanálu toku dat provede práci při přijetí zprávy z jiné komponenty. Výsledek této práce je předán do jiné komponenty v kanálu nebo sítě. Komponenty funkce se dá použít další podrobných souběžnosti z jiné knihovny, například, [paralelní vzory knihovna PPL ()](../../parallel/concrt/parallel-patterns-library-ppl.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad implementuje na obrázku uvedené dříve v tomto tématu.  
  
 [!code-cpp[concrt-basic-agents#1](../../parallel/concrt/codesnippet/cpp/asynchronous-agents-library_1.cpp)]  
  
 Tento příklad vytvoří následující výstup:  
  
```Output  
agent1: sending request...  
agent2: received 'request'.  
agent2: sending response...  
agent1: received '42'.  
```  
  
 Následující témata popisují funkce použité v tomto příkladu.  
  
## <a name="related-topics"></a>Související témata  
 [Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)  
 Popisuje roli asynchronních agentů v řešení větší výpočetní úlohy.  
  
 [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)  
 Popisuje různé typy bloku zpráv, které jsou poskytovány knihovna agentů.  
  
 [Funkce pro předávání zpráv](../../parallel/concrt/message-passing-functions.md)  
 Popisuje různé rutiny předávání zpráv, které jsou poskytovány knihovna agentů.  
  
 [Postupy: Implementace různých vzorů producent–příjemce](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)  
 Popisuje způsob implementace vzoru producent – příjemce ve vaší aplikaci.  
  
 [Postupy: Poskytování pracovních funkcí třídám call a transformer](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)  
 Znázorňuje několik způsobů, jak poskytování pracovních funkcí k [concurrency::call](../../parallel/concrt/reference/call-class.md) a [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) třídy.  
  
 [Postupy: Použití transformace v datovém kanálu](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)  
 Ukazuje, jak používat [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) – třída v datovém kanálu.  
  
 [Postupy: Výběr z dokončených úloh](../../parallel/concrt/how-to-select-among-completed-tasks.md)  
 Ukazuje, jak používat [concurrency::choice](../../parallel/concrt/reference/choice-class.md) a [concurrency::join](../../parallel/concrt/reference/join-class.md) třídy vyberte první úlohy k dokončení vyhledávacího algoritmu.  
  
 [Postupy: Odesílání zpráv v pravidelných intervalech](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)  
 Ukazuje, jak používat [concurrency::timer](../../parallel/concrt/reference/timer-class.md) třída k odesílání zpráv v pravidelných intervalech.  
  
 [Postupy: Použití filtru bloku zpráv](../../parallel/concrt/how-to-use-a-message-block-filter.md)  
 Ukazuje, jak povolit bloku asynchronní zpráva k přijetí nebo odmítnutí zprávy pomocí filtru.  
  
 [Knihovna PPL (Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md)  
 Popisuje, jak používat různé paralelní vzory, třeba paralelní algoritmy ve svých aplikacích.  
  
 [Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)  
 Popisuje Concurrency Runtime, který zjednodušuje paralelní programování a obsahuje odkazy na související témata.

