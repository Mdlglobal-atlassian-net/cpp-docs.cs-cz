---
title: "Kontrola pro přepisy paměti | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: memory, overwrites
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4560fb580d3d1b24feccf84dc07bde7dc38458c2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="checking-for-memory-overwrites"></a>Kontrola přepisů paměti
Pokud dojde k narušení přístupu pro volání na funkci pro zpracování haldy, je možné, že váš program má poškozena halda. Běžné příznakem tato situace by byl:  
  
```  
Access Violation in _searchseg  
```  
  
 [_Heapchk –](../../c-runtime-library/reference/heapchk.md) funkce je k dispozici v obou ladění a verzi sestavení (pouze systém Windows NT) pro ověření integrity haldě knihovny běhu. Můžete použít `_heapchk` stejným způsobem jako `AfxCheckMemory` funkce izolovat haldy přepsat, například:  
  
```  
if(_heapchk()!=_HEAPOK)  
   DebugBreak();  
```  
  
 Pokud tuto funkci někdy selže, budete muset izolovat od této chvíle byla poškozena halda.  
  
## <a name="see-also"></a>Viz také  
 [Oprava problémů se sestavením pro vydání](../../build/reference/fixing-release-build-problems.md)