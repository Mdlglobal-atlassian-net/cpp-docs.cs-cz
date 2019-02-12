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
ms.openlocfilehash: 77c61101e9540a0d9469e7176eb15992a73b4b09
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148969"
---
# <a name="simple-assignment-c"></a>Jednoduché přiřazení (C)

Operátor jednoduchého přiřazení přiřadí svůj pravý operand levému operandu. Hodnota pravého operandu je převedena na typ výrazu přiřazení a nahradí hodnotu uloženou v objektu určeném levým operandem. Použít pravidla převodu pro přiřazení (viz [převody přiřazení](../c-language/assignment-conversions.md)).

```
double x;
int y;

x = y;
```

V tomto příkladu hodnota `y` je převeden na typ **double** a přiřazená `x`.

## <a name="see-also"></a>Viz také:

[Operátory přiřazení v jazyce C](../c-language/c-assignment-operators.md)
