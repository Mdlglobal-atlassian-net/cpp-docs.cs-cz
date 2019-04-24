---
title: Výpočet nezbytných hodnot
ms.date: 11/04/2016
helpviewer_keywords:
- helper functions, calculating necessary values
ms.assetid: 4f037d0f-881a-4a48-a9d2-9f8872dfccb7
ms.openlocfilehash: 75952bbcdf823aa675b35702841c81e511105ca8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272647"
---
# <a name="calculating-necessary-values"></a>Výpočet nezbytných hodnot

Dvě důležité údaje se třeba dá vypočítat jako pomocné rutiny zpoždění. Za tímto účelem existují delayhlp.cpp pro výpočet v těchto dvou vložené funkce.

- Vypočítá první index aktuální importu do tří různých tabulek (importovat tabulku adres (IAT), tabulky vázané importních adres (BIAT) a tabulky odvázat importních adres (UIAT)).

- Druhá vrátí počet importů v platné IAT.

```cpp
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

## <a name="see-also"></a>Viz také:

[Základní informace o podpůrné funkci](understanding-the-helper-function.md)
