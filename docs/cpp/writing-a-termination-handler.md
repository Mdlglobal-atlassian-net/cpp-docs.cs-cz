---
title: "Zápis obslužné rutiny ukončení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- structured exception handling [C++], termination handlers
- exceptions [C++], terminating
- termination handlers [C++], writing
- handlers [C++]
- handlers [C++], termination
- termination handlers
- exception handling [C++], termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 52aa1f8f-f8dd-44b8-be94-5e2fc88d44fb
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a4a90c28f9bb2a681e88463dfd6bd9d3ff0a1d99
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="writing-a-termination-handler"></a>Zápis obslužné rutiny ukončení
Na rozdíl od obslužné rutiny výjimky je obslužná rutina ukončení spuštěna vždy, bez ohledu na to, zda je chráněný blok kódu ukončen normálně. Jediným účelem obslužné rutiny ukončení by mělo být zajištění, že prostředky, jako například paměť, popisovače a soubory, jsou správně uzavřeny bez ohledu na to, jak část kódu dokončí provádění.  
  
 Obslužné rutiny ukončení používají příkaz try-finally.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [Try-finally – příkaz](../cpp/try-finally-statement.md)  
  
-   [Vymazání prostředků](../cpp/cleaning-up-resources.md)  
  
-   [Načasování akce ve zpracování výjimek](../cpp/timing-of-exception-handling-a-summary.md)  
  
-   [Omezení obslužných rutin ukončení](../cpp/restrictions-on-termination-handlers.md)  
  
## <a name="see-also"></a>Viz také  
 [Strukturované zpracování (C/C++) výjimek](../cpp/structured-exception-handling-c-cpp.md)