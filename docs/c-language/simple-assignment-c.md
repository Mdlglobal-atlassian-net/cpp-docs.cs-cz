---
title: Jednoduché Assignment (C) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- type conversion [C++], simple assignment
- data type conversion [C++], simple assignment
- operators [C], simple assignment
- assignment operators [C++], simple
- simple assignment operator
- equal sign
ms.assetid: e7140a0a-7104-4b3a-b293-7adcc1fdd52b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff4e032e205680da84369075514e3177fa5fb33e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051019"
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