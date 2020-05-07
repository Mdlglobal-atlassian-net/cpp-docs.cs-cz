---
title: Degradace celých čísel
ms.date: 11/04/2016
helpviewer_keywords:
- demoting integers
ms.assetid: 51fb3654-60b0-4de7-80eb-bd910086c18a
ms.openlocfilehash: edfb8f03094c10cf0cf33b0eb799d5d822ac017d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234402"
---
# <a name="demotion-of-integers"></a>Degradace celých čísel

**3.2.1.2 ANSI** Výsledek převodu celého čísla na kratší celé číslo se znaménkem nebo výsledek převodu unsigned integer na celé číslo se znaménkem stejné délky, pokud hodnotu nelze reprezentovat

Když je **dlouhé** celé číslo přetypování na typ **short**nebo je **krátká** hodnota přetypování na `char`, jsou zachovány nejméně významné bajty.

Například tento řádek

```
short x = (short)0x12345678L;
```

přiřadí hodnotu 0x5678 do proměnné `x` a tento řádek

```
char y = (char)0x1234;
```

přiřadí hodnotu 0x34 do proměnné `y`.

Když jsou proměnné se znaménkem převedeny na proměnné bez znaménka a naopak, zůstanou bitové vzory stejné. Například přetypování-2 (0xFE) na hodnotu bez znaménka vrací 254 (také 0xFE).

## <a name="see-also"></a>Viz také

[Celá čísla](../c-language/integers.md)
