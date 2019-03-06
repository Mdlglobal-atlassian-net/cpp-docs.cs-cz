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
ms.openlocfilehash: aec21026ded821f9a87e7c0c2aeefd13a927a401
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417304"
---
# <a name="linenumbers"></a>/LINENUMBERS

```
/LINENUMBERS
```

## <a name="remarks"></a>Poznámky

Tato možnost zobrazuje čísla řádků souboru COFF. Čísla řádků existují v souboru objektu, pokud byl kompilován s databázi programu (/Zi) kompatibilní s C7 (/ Z7), nebo čísla pouze řádek (/ zd). Spustitelného souboru nebo knihovny DLL obsahuje COFF čísla řádků, pokud byla spojena s Generovat ladicí informace (/ DEBUG).

Pouze [/HEADERS](../../build/reference/headers.md) – možnost nástroje DUMPBIN je k dispozici pro použití se soubory vytvořenými pomocí [/GL](../../build/reference/gl-whole-program-optimization.md) – možnost kompilátoru.

## <a name="see-also"></a>Viz také:

[DUMPBIN – možnosti](../../build/reference/dumpbin-options.md)
