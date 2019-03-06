---
title: /LINKERMEMBER
ms.date: 11/04/2016
f1_keywords:
- /linkermember
helpviewer_keywords:
- /LINKERMEMBER dumpbin option
- LINKERMEMBER dumpbin option
- -LINKERMEMBER dumpbin option
ms.assetid: c96868c1-d70e-4651-ae36-c55b58b16406
ms.openlocfilehash: 8669198ee62032e15e40c821ed2e4caccdebe519
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417486"
---
# <a name="linkermember"></a>/LINKERMEMBER

```
/LINKERMEMBER[:{1|2}]
```

## <a name="remarks"></a>Poznámky

Tato možnost zobrazuje veřejných symbolů definovaných v knihovně. Zadejte argument 1 pro zobrazení symbolů v pořadí objektů spolu s jejich posunů. Zadejte argument 2 zobrazit posuny a čísla indexu objektů a potom zobrazí seznam symboly v abecedním pořadí, spolu s objekt indexu pro každý. K získání obou výstupy, zadejte /LINKERMEMBER bez tento číselný argument.

Pouze [/HEADERS](../../build/reference/headers.md) – možnost nástroje DUMPBIN je k dispozici pro použití se soubory vytvořenými pomocí [/GL](../../build/reference/gl-whole-program-optimization.md) – možnost kompilátoru.

## <a name="see-also"></a>Viz také:

[DUMPBIN – možnosti](../../build/reference/dumpbin-options.md)
