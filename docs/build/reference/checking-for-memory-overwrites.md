---
title: Kontrola pro přepisy paměti | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- memory, overwrites
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 258aa6ae01d48df6717135f7dc8b73fc3f9e697a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369848"
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