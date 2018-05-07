---
title: Upozornění příkazového řádku D9027 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9027
dev_langs:
- C++
helpviewer_keywords:
- D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dfe2493290c4e4cc5b744136b8e7036c6559220a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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