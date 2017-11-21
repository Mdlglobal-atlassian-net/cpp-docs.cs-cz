---
title: "Postupy: implementace různých vzorů typu výrobce spotřebitel | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- producer-consumer patterns, implementing [Concurrency Runtime]
- implementing producer-consumer patterns [Concurrency Runtime]
ms.assetid: 75f2c7cc-5399-49ea-98eb-847fe6747169
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4daf7005eabee7f6cf74144c08c8d8d8aabef232
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-implement-various-producer-consumer-patterns"></a>Postupy: Implementace různých vzorů typu výrobce-spotřebitel
Toto téma popisuje způsob implementace vzoru producent – příjemce ve vaší aplikaci. V tomto vzoru *producent* odešle zprávy do blok zpráv a *příjemce* čte zprávy z tohoto bloku.  
  
 Téma ukazuje dva scénáře. Spotřebitel v prvního scénáře, musí mít každá zpráva odeslaná Autor. V druhý scénář příjemce pravidelně se dotazuje na data a proto nemá přijímat každou zprávu.  
  
 Obou příkladech v tomto tématu použijte k přenosu zpráv od výrobce k příjemce agenty, bloky zpráv a funkce pro předávání zpráv. Proto, že agent používá [concurrency::send](reference/concurrency-namespace-functions.md#send) funkce pro zápis zpráv do [concurrency::ITarget](../../parallel/concrt/reference/itarget-class.md) objektu. Uživatelský agent používá [concurrency::receive](reference/concurrency-namespace-functions.md#receive) funkce umožní číst zprávy z [concurrency::ISource](../../parallel/concrt/reference/isource-class.md) objektu. Jak agenty obsahovat hodnotu sentinel ke koordinaci konec zpracování.  
  
 Další informace o asynchronních agentů najdete v tématu [asynchronních agentů](../../parallel/concrt/asynchronous-agents.md). Další informace o bloky zpráv a funkce pro předávání zpráv najdete v tématu [asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md) a [funkce předávání zpráv](../../parallel/concrt/message-passing-functions.md).  
  
## <a name="example"></a>Příklad  
 V tomto příkladu producent agent odešle řadu čísla agent příjemce. Příjemce obdrží každý z těchto čísel a vypočítá svoje průměru. Aplikace zapíše průměr ke konzole.  
  
 Tento příklad používá [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) objekt, který chcete povolit producent do fronty zpráv. `unbounded_buffer` Třída implementuje `ITarget` a `ISource` tak, aby autor a příjemce může odesílat a přijímat zprávy do a z sdílené vyrovnávací paměti. `send` a `receive` funkce koordinaci úlohy šíření data od výrobce k příjemce.  
  
 [!code-cpp[concrt-producer-consumer-average#1](../../parallel/concrt/codesnippet/cpp/how-to-implement-various-producer-consumer-patterns_1.cpp)]  
  
 Tento příklad vytvoří následující výstup.  
  
```Output  
The average is 50.  
```  
  
## <a name="example"></a>Příklad  
 V tomto příkladu producent agent odešle řadu akcií agent příjemce. Agent příjemce pravidelně čte aktuální uvozovky a vytiskne ji do konzoly.  
  
 V tomto příkladu se podobá předchozímu, s tím rozdílem, že se používá [concurrency::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) objekt, který chcete povolit producent sdílet jednu zprávu s příjemce. Jako v předchozím příkladu `overwrite_buffer` třída implementuje `ITarget` a `ISource` tak, aby autor a příjemce může fungovat na sdílené zprávy vyrovnávací paměti.  
  
 [!code-cpp[concrt-producer-consumer-quotes#1](../../parallel/concrt/codesnippet/cpp/how-to-implement-various-producer-consumer-patterns_2.cpp)]  
  
 Tento příklad vytvoří následující ukázkový výstup.  
  
```Output  
Current quote is 24.44.  
Current quote is 24.44.  
Current quote is 24.65.  
Current quote is 24.99.  
Current quote is 23.76.  
Current quote is 22.30.  
Current quote is 25.89.  
```  
  
 Na rozdíl od s `unbounded_buffer` objekt, `receive` funkce neodebere zprávu od `overwrite_buffer` objektu. Pokud příjemce čte z vyrovnávací paměti zpráv více než jednou před Autor přepíše zprávy, získá příjemce stejnou zprávu pokaždé, když.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `producer-consumer.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe /EHsc producent – consumer.cpp**  
  
## <a name="see-also"></a>Viz také  
 [Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)   
 [Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)   
 [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Funkce usnadnění](../../parallel/concrt/message-passing-functions.md)
