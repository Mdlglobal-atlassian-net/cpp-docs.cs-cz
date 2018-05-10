---
title: Funkce usnadnění | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message passing functions
ms.assetid: 42477c9e-a8a6-4dc4-a98e-93c6dc8c4dd0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9eecb7d2a45079ff14740167a192eafaab268150
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="message-passing-functions"></a>Funkce usnadnění
Knihovna asynchronních agentů poskytuje několik funkcí, které umožňují předávání zpráv mezi součástmi.  
  
 Tyto funkce pro předávání zpráv se používají s různými typy bloku zpráv. Další informace o typech bloku zpráv, které jsou definovány Concurrency Runtime najdete v tématu [asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md).  
  
##  <a name="top"></a> Oddíly  
 Toto téma popisuje následující funkce předávání zpráv:  
  
-   [odesílání a asend –](#send)  
  
-   [přijímat a try_receive –](#receive)  
  
-   [Příklady](#examples)  
  
##  <a name="send"></a> odesílání a asend –  

 [Concurrency::send](reference/concurrency-namespace-functions.md#send) funkce odešle zprávu do zadané cílové synchronně a [concurrency::asend](reference/concurrency-namespace-functions.md#asend) funkce odešle zprávu do zadané cílové asynchronně. Jak `send` a `asend` funkce Počkejte, dokud cíl Určuje, že se bude nakonec přijmout nebo odmítnout zprávy.  
  
 `send` Funkce čeká, dokud cílový přijme nebo odmítne zprávy před vrátí. `send` Funkce vrátí `true` Pokud byla zpráva doručena a `false` jinak. Protože `send` funkce funguje synchronně, `send` funkce čeká na cíl, který má přijmout zprávu před vrátí.  
  
 Naopak `asend` funkce nečekat na cíl, který má přijmout nebo odmítnout zprávu, než ho vrátí. Místo toho `asend` funkce vrátí `true` Pokud cíl přijme zprávu a bude nakonec trvat. V opačném `asend` vrátí `false` že cíl odmítl zprávy, nebo odložena rozhodnutí o tom, jestli se má provést zprávy.  
  
 [[Horní](#top)]  
  
##  <a name="receive"></a> přijímat a try_receive –  

 [Concurrency::receive](reference/concurrency-namespace-functions.md#receive) a [concurrency::try_receive](reference/concurrency-namespace-functions.md#try_receive) funkce Číst data z daného zdroje. `receive` Funkce čeká data k dispozici, zatímco `try_receive` funkce vrátí okamžitě.  
  
 Použití `receive` funkce při musí mít data pokračujte. Použití `try_receive` fungovat, pokud zablokujete nesmí aktuální kontext nebo není nutné mít data pokračujte.  
  
 [[Horní](#top)]  
  
##  <a name="examples"></a> Příklady  
 Příklady, které používají `send` a `asend`, a `receive` funkce, najdete v následujících tématech:  
  
-   [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)  
  
-   [Postupy: Implementace různých vzorů producent–příjemce](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)  
  
-   [Postupy: Poskytování pracovních funkcí třídám call a transformer](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)  
  
-   [Postupy: Použití transformace v datovém kanálu](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)  
  
-   [Postupy: Výběr z dokončených úloh](../../parallel/concrt/how-to-select-among-completed-tasks.md)  
  
-   [Postupy: Odesílání zpráv v pravidelných intervalech](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)  
  
-   [Postupy: Použití filtru bloku zpráv](../../parallel/concrt/how-to-use-a-message-block-filter.md)  
  
 [[Horní](#top)]  
  
## <a name="see-also"></a>Viz také  
 [Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)   
 [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Send – funkce](reference/concurrency-namespace-functions.md#send)   
 [asend – funkce](reference/concurrency-namespace-functions.md#asend)   
 [Receive – funkce](reference/concurrency-namespace-functions.md#receive)   
 [try_receive – funkce](reference/concurrency-namespace-functions.md#try_receive)


