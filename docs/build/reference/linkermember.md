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
ms.openlocfilehash: a0456fd9ed1729b4a6cfa200a54ba211a64e94ea
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813276"
---
# <a name="linkermember"></a>/LINKERMEMBER

```
/LINKERMEMBER[:{1|2}]
```

## <a name="remarks"></a>Poznámky

Tato možnost zobrazuje veřejných symbolů definovaných v knihovně. Zadejte argument 1 pro zobrazení symbolů v pořadí objektů spolu s jejich posunů. Zadejte argument 2 zobrazit posuny a čísla indexu objektů a potom zobrazí seznam symboly v abecedním pořadí, spolu s objekt indexu pro každý. K získání obou výstupy, zadejte /LINKERMEMBER bez tento číselný argument.

Pouze [/HEADERS](headers.md) – možnost nástroje DUMPBIN je k dispozici pro použití se soubory vytvořenými pomocí [/GL](gl-whole-program-optimization.md) – možnost kompilátoru.

## <a name="see-also"></a>Viz také:

[DUMPBIN – možnosti](dumpbin-options.md)
