---
title: Kumulativní závislosti
ms.date: 11/04/2016
helpviewer_keywords:
- dependencies, cumulative
- cumulative dependencies in NMAKE
- dependencies
ms.assetid: fa6dd777-80b8-437d-87a7-aec0ed818a49
ms.openlocfilehash: de0a9649be8f0dae58f45d8980d2df610ff2febe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294080"
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

## <a name="see-also"></a>Viz také:

[Cíle](targets.md)
