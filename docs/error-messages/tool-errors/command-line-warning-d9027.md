---
title: "Upozornění příkazového řádku D9027 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- D9027
dev_langs:
- C++
helpviewer_keywords:
- D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2769eb5f78cb1d5bdd6749e65429d83b69a2807b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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