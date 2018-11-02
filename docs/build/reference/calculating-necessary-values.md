---
title: Výpočet nezbytných hodnot
ms.date: 11/04/2016
helpviewer_keywords:
- helper functions, calculating necessary values
ms.assetid: 4f037d0f-881a-4a48-a9d2-9f8872dfccb7
ms.openlocfilehash: 80c028a315669fb0032628bb86a834d429935f50
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50513864"
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

## <a name="see-also"></a>Viz také

[Základní informace o podpůrné funkci](understanding-the-helper-function.md)