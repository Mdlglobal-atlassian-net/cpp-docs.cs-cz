---
title: "Upozornění příkazového řádku D9027 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: D9027
dev_langs: C++
helpviewer_keywords: D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5ccdccbc4c6df8f948b44eeaa096cff46824d043
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="command-line-warning-d9027"></a>Upozornění příkazového řádku D9027
zdrojový soubor se\<filename >' ignorovat  
  
 CL.exe ignorovat vstupní zdrojový soubor.  
  
 Toto upozornění může být způsobeno mezeru mezi možnost /Fo a výstupní soubor na příkazovém řádku s parametrem /c. Příklad:  
  
```  
cl /c /Fo output.obj input.c   
```  
  
 Protože je mezera mezi /Fo a `output.obj`, trvá CL.exe `output.obj` jako název souboru vstupního souboru. Chcete-li problém vyřešit, odeberte místo:  
  
```  
cl /c /Fooutput.obj input.c   
```