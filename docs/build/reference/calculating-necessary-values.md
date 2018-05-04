---
title: Výpočet nezbytných hodnot | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- helper functions, calculating necessary values
ms.assetid: 4f037d0f-881a-4a48-a9d2-9f8872dfccb7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f8f51e448aab0978d6a7eb39a753c2274d2cae6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="calculating-necessary-values"></a>Výpočet nezbytných hodnot
Dvě zásadní informace nutné vypočítat pomocná rutina zpoždění. Za tímto účelem jsou dvě funkce vložené v delayhlp.cpp pro výpočet tyto informace.  
  
-   První vypočítá index aktuální importu do tří různých tabulek (import tabulky adres (IAT), tabulky adres vázané import (BIAT) a tabulky adres nevázaný import (UIAT)).  
  
-   Druhý spočítá počet importy v platný IAT.  
  
```  
// utility function for calculating the index of the current import  
// for all the tables (INT, BIAT, UIAT, and IAT).  
__inline unsigned  
IndexFromPImgThunkData(PCImgThunkData pitdCur, PCImgThunkData pitdBase) {  
    return pitdCur - pitdBase;  
    }  
  
// utility function for calculating the count of imports given the base  
// of the IAT. NB: this only works on a valid IAT!  
__inline unsigned  
CountOfImports(PCImgThunkData pitdBase) {  
    unsigned        cRet = 0;  
    PCImgThunkData  pitd = pitdBase;  
    while (pitd->u1.Function) {  
        pitd++;  
        cRet++;  
        }  
    return cRet;  
    }  
```  
  
## <a name="see-also"></a>Viz také  
 [Základní informace o podpůrné funkci](understanding-the-helper-function.md)