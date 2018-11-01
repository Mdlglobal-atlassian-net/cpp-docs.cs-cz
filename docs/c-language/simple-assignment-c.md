---
title: Jednoduché přiřazení (C)
ms.date: 11/04/2016
helpviewer_keywords:
- type conversion [C++], simple assignment
- data type conversion [C++], simple assignment
- operators [C], simple assignment
- assignment operators [C++], simple
- simple assignment operator
- equal sign
ms.assetid: e7140a0a-7104-4b3a-b293-7adcc1fdd52b
ms.openlocfilehash: 76c48fc6774f97bab69f916ad7e5176e91d004ab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50574912"
---
# <a name="simple-assignment-c"></a>Jednoduché přiřazení (C)

Operátor jednoduchého přiřazení přiřadí svůj pravý operand levému operandu. Hodnota pravého operandu je převedena na typ výrazu přiřazení a nahradí hodnotu uloženou v objektu určeném levým operandem. Použít pravidla převodu pro přiřazení (viz [převody přiřazení](../c-language/assignment-conversions.md)).

```
double x;
int y;

x = y;
```

V tomto příkladu hodnota `y` je převeden na typ **double** a přiřazená `x`.

## <a name="see-also"></a>Viz také

[Operátory přiřazení v jazyce C](../c-language/c-assignment-operators.md)