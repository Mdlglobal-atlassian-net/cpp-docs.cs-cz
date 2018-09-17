---
title: Kumulativní závislosti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dependencies, cumulative
- cumulative dependencies in NMAKE
- dependencies
ms.assetid: fa6dd777-80b8-437d-87a7-aec0ed818a49
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a66b153a52da06cca14845b9a58fcef0f42676d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725709"
---
# <a name="cumulative-dependencies"></a>Kumulativní závislosti

Závislosti se v bloku Popis kumulativní, pokud cíl se opakuje.

Například tato sada pravidel,

```Output
bounce.exe : jump.obj
bounce.exe : up.obj
   echo Building bounce.exe...
```

je vyhodnocen jako tato:

```Output
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

Více cílů na více řádcích závislostí v jedné popis bloku jsou hodnoceny jako každý byly zadány v bloku samostatné popis, ale cíle, které nejsou na posledním řádku závislost nepoužívejte bloku příkazů. NMAKE se pokusí použít odvozené pravidlo pro tyto cíle.

Například tato sada pravidel,

```Output
leap.exe bounce.exe : jump.obj
bounce.exe climb.exe : up.obj
   echo Building bounce.exe...
```

je vyhodnocen jako tato:

```Output

leap.exe : jump.obj
# invokes an inference rule
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
climb.exe : up.obj
   echo Building bounce.exe...
```

## <a name="see-also"></a>Viz také

[Cíle](../build/targets.md)