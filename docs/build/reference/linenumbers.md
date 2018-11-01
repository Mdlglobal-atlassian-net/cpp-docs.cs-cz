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
ms.openlocfilehash: af6e3c7c3693bd95924a86640399b15eb3378ed7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663746"
---
# <a name="linenumbers"></a>/LINENUMBERS

```
/LINENUMBERS
```

## <a name="remarks"></a>Poznámky

Tato možnost zobrazuje čísla řádků souboru COFF. Čísla řádků existují v souboru objektu, pokud byl kompilován s databázi programu (/Zi) kompatibilní s C7 (/ Z7), nebo čísla pouze řádek (/ zd). Spustitelného souboru nebo knihovny DLL obsahuje COFF čísla řádků, pokud byla spojena s Generovat ladicí informace (/ DEBUG).

Pouze [/HEADERS](../../build/reference/headers.md) – možnost nástroje DUMPBIN je k dispozici pro použití se soubory vytvořenými pomocí [/GL](../../build/reference/gl-whole-program-optimization.md) – možnost kompilátoru.

## <a name="see-also"></a>Viz také

[DUMPBIN – možnosti](../../build/reference/dumpbin-options.md)