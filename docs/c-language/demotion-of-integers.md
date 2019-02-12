---
title: Degradace celých čísel
ms.date: 11/04/2016
helpviewer_keywords:
- demoting integers
ms.assetid: 51fb3654-60b0-4de7-80eb-bd910086c18a
ms.openlocfilehash: edfb8f03094c10cf0cf33b0eb799d5d822ac017d
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152648"
---
# <a name="demotion-of-integers"></a>Degradace celých čísel

**ANSI 3.2.1.2** výsledek převodu celého čísla na kratší celé číslo se znaménkem nebo výsledek převodu celé číslo bez znaménka na celé číslo se znaménkem stejné délky, pokud hodnota nemůže být reprezentovaná

Při **dlouhé** celé číslo přetypováno na **krátké**, nebo **krátký** přetypováno na `char`, jsou zachovány nejméně významné bajty.

Například tento řádek

```
short x = (short)0x12345678L;
```

přiřadí hodnotu 0x5678 do proměnné `x` a tento řádek

```
char y = (char)0x1234;
```

přiřadí hodnotu 0x34 do proměnné `y`.

Když jsou proměnné se znaménkem převedeny na proměnné bez znaménka a naopak, zůstanou bitové vzory stejné. Například přetypování -2 (0xFE) na hodnotu bez znaménka vrátí hodnotu 254 (také 0xFE).

## <a name="see-also"></a>Viz také:

[Celá čísla](../c-language/integers.md)
