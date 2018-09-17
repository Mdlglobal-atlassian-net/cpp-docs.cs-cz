---
title: Vedlejší efekty závislostí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dependencies, side effects
- NMAKE program, dependents
ms.assetid: d4e8db25-fdc0-4d73-81ec-1538f2e1b3e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a70df679434b187bc2eee4eb4aad5881db0da1c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716516"
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

## <a name="see-also"></a>Viz také

[Cíle](../build/targets.md)