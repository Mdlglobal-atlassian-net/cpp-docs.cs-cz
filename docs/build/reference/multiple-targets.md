---
title: Několik cílů
ms.date: 11/04/2016
helpviewer_keywords:
- makefiles, targets
- multiple targets in NMAKE
- targets, multiple in NMAKE
- NMAKE program, targets
ms.assetid: b609a179-0b9f-4b08-9930-998047588ae0
ms.openlocfilehash: 43e5216d5e11e89aff9b6f0c69ff4e76a8cc9da8
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822982"
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

## <a name="see-also"></a>Viz také:

[Cíle](targets.md)
