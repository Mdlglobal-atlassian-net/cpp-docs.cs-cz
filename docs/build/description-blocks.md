---
title: Bloky popisů
ms.date: 11/04/2016
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
ms.openlocfilehash: 214963b5c3f633e8d029cee0500d4bd5fab6ed53
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490596"
---
# <a name="description-blocks"></a>Bloky popisů

Popis blok je řádku závislostí může volitelně následovat bloku příkazů:

```
targets... : dependents...
    commands...
```

Řádek závislostí Určuje jeden nebo více cílů a nula nebo více závislé položky. Cíl musí být na začátku řádku. Jsou povoleny samostatné cíle z položky závislé na dvojtečkou (:); mezery ani tabulátory. Rozdělit na řádku, použijte po cíl nebo závislé na zpětné lomítko (\). Cíl neexistuje, je předchozí časové razítko než závislé, zda je [pseudotarget](../build/pseudotargets.md), NMAKE provede příkazy. Pokud závislé je cílem jinde a neexistuje nebo není aktuální s ohledem na vlastní položky závislé na, aktualizuje NMAKE rolích dependent před aktualizací aktuální závislostí.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

[Cíle](../build/targets.md)

[Závislé prvky](../build/dependents.md)

## <a name="see-also"></a>Viz také

[NMAKE – referenční zdroje](../build/nmake-reference.md)