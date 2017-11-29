---
title: "Postupy: odesílání zpráv v pravidelných intervalech | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- timer class, example
- sending messages at regular intervals [Concurrency Runtime]
ms.assetid: 4b60ea6c-97c8-4d69-9f7b-ad79f3548026
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c5c10ba2a1fee400ef99799c7c83a3bdcacd084f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-send-a-message-at-a-regular-interval"></a>Postupy: Odesílání zpráv v pravidelných intervalech
Tento příklad ukazuje, jak používat souběžnost::[timer – třída](../../parallel/concrt/reference/timer-class.md) k odesílání zpráv v pravidelných intervalech.  
  
## <a name="example"></a>Příklad  

 Následující příklad používá `timer` objektu k hlášení průběhu během časově náročná operace. Tento příklad obsahuje odkazy `timer` do objektu [concurrency::call](../../parallel/concrt/reference/call-class.md) objektu. `call` Objekt vytiskne indikátor průběhu do konzoly v pravidelných intervalech. [Concurrency::timer::start](reference/timer-class.md#start) metoda spustí časovač na samostatný kontext. `perform_lengthy_operation` Volání funkce [concurrency::wait](reference/concurrency-namespace-functions.md#wait) funkce v hlavní kontextu k simulaci časově náročná operace.  

  
 [!code-cpp[concrt-report-progress#1](../../parallel/concrt/codesnippet/cpp/how-to-send-a-message-at-a-regular-interval_1.cpp)]  
  
 Tento příklad vytvoří následující výstup:  
  
```Output  
Performing a lengthy operation..........done.  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `report-progress.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe /EHsc sestavy progress.cpp**  
  
## <a name="see-also"></a>Viz také  
 [Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)   
 [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Funkce usnadnění](../../parallel/concrt/message-passing-functions.md)