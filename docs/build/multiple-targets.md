---
title: Několik cílů
ms.date: 11/04/2016
helpviewer_keywords:
- makefiles, targets
- multiple targets in NMAKE
- targets, multiple in NMAKE
- NMAKE program, targets
ms.assetid: b609a179-0b9f-4b08-9930-998047588ae0
ms.openlocfilehash: 2762e458781e3a95f478ea3477fc8ef02f9196fb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50645055"
---
# <a name="multiple-targets"></a>Několik cílů

NMAKE vyhodnocuje více cílů v jedné závislosti jakoby každý byly zadány v samostatných popis bloku.

Například to...

```Output
bounce.exe leap.exe : jump.obj
   echo Building...
```

.. je vyhodnocen jako tato:

```Output
bounce.exe : jump.obj
   echo Building...
leap.exe : jump.obj
   echo Building...
```

## <a name="see-also"></a>Viz také

[Cíle](../build/targets.md)