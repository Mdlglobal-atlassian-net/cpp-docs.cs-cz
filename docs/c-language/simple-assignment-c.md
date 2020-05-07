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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62158277"
---
# <a name="simple-assignment-c"></a>Jednoduché přiřazení (C)

Operátor jednoduchého přiřazení přiřadí svůj pravý operand levému operandu. Hodnota pravého operandu je převedena na typ výrazu přiřazení a nahradí hodnotu uloženou v objektu určeném levým operandem. Pravidla převodu pro přiřazení platí (viz [převody přiřazení](../c-language/assignment-conversions.md)).

```
double x;
int y;

x = y;
```

V tomto příkladu `y` je hodnota převedena na typ **Double** a je přiřazena `x`.

## <a name="see-also"></a>Viz také

[Operátory přiřazení v jazyce C](../c-language/c-assignment-operators.md)
