---
title: Bloky popisů
ms.date: 11/04/2016
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
ms.openlocfilehash: da9265d6b0026bb47496d3aa58847824b5d634d2
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823369"
---
# <a name="description-blocks"></a>Bloky popisů

Popis blok je řádku závislostí může volitelně následovat bloku příkazů:

```
targets... : dependents...
    commands...
```

Řádek závislostí Určuje jeden nebo více cílů a nula nebo více závislé položky. Cíl musí být na začátku řádku. Jsou povoleny samostatné cíle z položky závislé na dvojtečkou (:); mezery ani tabulátory. Rozdělit na řádku, použijte po cíl nebo závislé na zpětné lomítko (\). Cíl neexistuje, je předchozí časové razítko než závislé, zda je [pseudotarget](pseudotargets.md), NMAKE provede příkazy. Pokud závislé je cílem jinde a neexistuje nebo není aktuální s ohledem na vlastní položky závislé na, aktualizuje NMAKE rolích dependent před aktualizací aktuální závislostí.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

[Cíle](targets.md)

[Závislé prvky](dependents.md)

## <a name="see-also"></a>Viz také:

[NMAKE – referenční zdroje](nmake-reference.md)
