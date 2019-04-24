---
title: /LINENUMBERS
ms.date: 11/04/2016
f1_keywords:
- /linenumbers
helpviewer_keywords:
- LINENUMBERS dumpbin option
- line numbers
- -LINENUMBERS dumpbin option
- /LINENUMBERS dumpbin option
ms.assetid: 1681d582-2c2f-484e-9920-109959549055
ms.openlocfilehash: ea4c3ac2ad582e0fe364f2da26511a66e9dc376c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269238"
---
# <a name="linenumbers"></a>/LINENUMBERS

```
/LINENUMBERS
```

## <a name="remarks"></a>Poznámky

Tato možnost zobrazuje čísla řádků souboru COFF. Čísla řádků existují v souboru objektu, pokud byl kompilován s databázi programu (/Zi) kompatibilní s C7 (/ Z7), nebo čísla pouze řádek (/ zd). Spustitelného souboru nebo knihovny DLL obsahuje COFF čísla řádků, pokud byla spojena s Generovat ladicí informace (/ DEBUG).

Pouze [/HEADERS](headers.md) – možnost nástroje DUMPBIN je k dispozici pro použití se soubory vytvořenými pomocí [/GL](gl-whole-program-optimization.md) – možnost kompilátoru.

## <a name="see-also"></a>Viz také:

[DUMPBIN – možnosti](dumpbin-options.md)
