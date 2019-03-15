---
title: Vedlejší efekty závislostí
ms.date: 11/04/2016
helpviewer_keywords:
- dependencies, side effects
- NMAKE program, dependents
ms.assetid: d4e8db25-fdc0-4d73-81ec-1538f2e1b3e8
ms.openlocfilehash: b89306b6e4d85e0e08729fb1d35fb041d69647e7
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823163"
---
# <a name="dependency-side-effects"></a>Vedlejší efekty závislostí

Pokud cíl není zadán s dvojtečkou (:) dvou řádcích závislostí v různých umístěních a zobrazit příkazy po pouze jeden z řádků, interpretuje NMAKE jakoby sousední nebo kombinované závislosti. Odvozené pravidlo pro závislost, která nemá žádné příkazy, ale místo toho předpokládá, že závislosti patří do jedné popis bloku a provede příkazy zadané společně se závislosti vyvolat. Například tato sada pravidel:

```Output
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
```

je vyhodnocen jako tato:

```Output
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

Tomuto chování nedojde-li dvojtečka (`::`) se používá. Například tato sada pravidel:

```Output
bounce.exe :: jump.obj
   echo Building bounce.exe...

bounce.exe :: up.obj
```

je vyhodnocen jako tato:

```Output
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
# invokes an inference rule
```

## <a name="see-also"></a>Viz také:

[Cíle](targets.md)
