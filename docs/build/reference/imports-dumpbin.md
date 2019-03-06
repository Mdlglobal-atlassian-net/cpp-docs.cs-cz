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
ms.openlocfilehash: 94009670329887a0b8a35e7b8b36996a84c7faa6
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417499"
---
# <a name="imports-dumpbin"></a>/IMPORTS (DUMPBIN)

```
/IMPORTS[:file]
```

Tato možnost zobrazuje seznam knihoven DLL (obojí staticky propojené a [zpožděné načtení](../../build/reference/linker-support-for-delay-loaded-dlls.md)), které jsou importovány do spustitelný soubor nebo knihovny DLL a jednotlivé importy ze všech těchto knihoven DLL.

Volitelný `file` specifikace umožňuje určit, aby se zobrazil importy pro pouze tuto knihovnu DLL. Příklad:

```
dumpbin /IMPORTS:msvcrt.dll
```

## <a name="remarks"></a>Poznámky

Tato možnost zobrazí výstup je podobný [/EXPORTUJE](../../build/reference/dash-exports.md) výstup.

Pouze [/HEADERS](../../build/reference/headers.md) – možnost nástroje DUMPBIN je k dispozici pro použití se soubory vytvořenými pomocí [/GL](../../build/reference/gl-whole-program-optimization.md) – možnost kompilátoru.

## <a name="see-also"></a>Viz také:

[DUMPBIN – možnosti](../../build/reference/dumpbin-options.md)
