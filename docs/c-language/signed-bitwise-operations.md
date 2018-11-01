---
title: Podepsané bitové operace
ms.date: 11/04/2016
helpviewer_keywords:
- bitwise operations
- signed bitwise operations
ms.assetid: 1e5cf65b-ee32-41a0-a5c2-82c1854091f6
ms.openlocfilehash: d178900a25a5d7a080068fb1919fcba2853bef14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652007"
---
# <a name="signed-bitwise-operations"></a>Podepsané bitové operace

**ANSI 3.3** výsledky bitových operací s celými čísly se znaménkem

Bitové operace s celými čísly se znaménkem fungují stejně jako bitové operace s celými čísly bez znaménka. Například `-16 & 99` může být vyjádřena v binárním souboru jako

```
  11111111 11110000
& 00000000 01100011
  _________________
  00000000 01100000
```

Výsledkem bitové operace AND je 96.

## <a name="see-also"></a>Viz také

[Celá čísla](../c-language/integers.md)