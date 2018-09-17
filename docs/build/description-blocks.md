---
title: Bloky popisů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d83e010f690f96afa5a57eb89ca1e8f4cf444225
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45699657"
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