---
title: -IMPORTS (DUMPBIN) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /imports
dev_langs:
- C++
helpviewer_keywords:
- IMPORTS dumpbin option
- /IMPORTS dumpbin option
- -IMPORTS dumpbin option
ms.assetid: 6a296216-2b1b-40f8-8736-cd4553a22456
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5b3b1e3a74fea278bc142d02f793308b6b0e054
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713567"
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

## <a name="see-also"></a>Viz také

[DUMPBIN – možnosti](../../build/reference/dumpbin-options.md)