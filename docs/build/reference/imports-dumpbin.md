---
title: /IMPORTS (DUMPBIN)
ms.date: 11/04/2016
f1_keywords:
- /imports
helpviewer_keywords:
- IMPORTS dumpbin option
- /IMPORTS dumpbin option
- -IMPORTS dumpbin option
ms.assetid: 6a296216-2b1b-40f8-8736-cd4553a22456
ms.openlocfilehash: c8b0f88b38eb657fe4d3916ef0df13972e985cbe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291836"
---
# <a name="imports-dumpbin"></a>/IMPORTS (DUMPBIN)

```
/IMPORTS[:file]
```

Tato možnost zobrazuje seznam knihoven DLL (obojí staticky propojené a [zpožděné načtení](linker-support-for-delay-loaded-dlls.md)), které jsou importovány do spustitelný soubor nebo knihovny DLL a jednotlivé importy ze všech těchto knihoven DLL.

Volitelný `file` specifikace umožňuje určit, aby se zobrazil importy pro pouze tuto knihovnu DLL. Příklad:

```
dumpbin /IMPORTS:msvcrt.dll
```

## <a name="remarks"></a>Poznámky

Tato možnost zobrazí výstup je podobný [/EXPORTUJE](dash-exports.md) výstup.

Pouze [/HEADERS](headers.md) – možnost nástroje DUMPBIN je k dispozici pro použití se soubory vytvořenými pomocí [/GL](gl-whole-program-optimization.md) – možnost kompilátoru.

## <a name="see-also"></a>Viz také:

[DUMPBIN – možnosti](dumpbin-options.md)
