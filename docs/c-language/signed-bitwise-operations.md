---
title: Podepsané bitové operace
ms.date: 11/04/2016
helpviewer_keywords:
- bitwise operations
- signed bitwise operations
ms.assetid: 1e5cf65b-ee32-41a0-a5c2-82c1854091f6
ms.openlocfilehash: 43f65fd5d1ea14ef5e15f18d9c8516ccf5fb1e08
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62158316"
---
# <a name="signed-bitwise-operations"></a>Podepsané bitové operace

**ANSI 3,3** Výsledky bitových operací u celých čísel se znaménkem

Bitové operace s celými čísly se znaménkem fungují stejně jako bitové operace s celými čísly bez znaménka. Například `-16 & 99` lze vyjádřit v binárním formátu jako

```
  11111111 11110000
& 00000000 01100011
  _________________
  00000000 01100000
```

Výsledkem bitové operace AND je 96.

## <a name="see-also"></a>Viz také

[Celá čísla](../c-language/integers.md)
