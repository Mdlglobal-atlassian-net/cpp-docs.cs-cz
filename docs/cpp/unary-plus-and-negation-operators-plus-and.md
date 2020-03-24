---
title: 'Unární operátory Plus a Negation: + a -'
ms.date: 11/04/2016
f1_keywords:
- +
- '-'
helpviewer_keywords:
- unary operators [C++], plus
- '- operator'
- negation operator
- + operator [C++], unary operators
- + operator
ms.assetid: 2c58c4f4-0d92-4ae3-9d0c-1a6157875cc1
ms.openlocfilehash: e640d18dc3755385188e166c57ad5e912ac24fb4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160590"
---
# <a name="unary-plus-and-negation-operators--and--"></a>Unární operátory Plus a Negation: + a -

## <a name="syntax"></a>Syntaxe

```
+ cast-expression
- cast-expression
```

## <a name="-operator"></a>+ – operátor

Výsledek unárního operátoru plus ( **+** ) je hodnota jeho operandu. Operand unárního operátoru plus musí být aritmetického typu.

Pro celočíselné operandy je prováděno celočíselné povýšení. Výsledným typem je typ, na nějž byl operand povýšen. Proto výraz `+ch`, kde `ch` je typu **char**, má za následek typ **int**; hodnota se nezměnila. Další informace o tom, jak se povýšení provádí, najdete v tématu [standardní převody](standard-conversions.md) .

## <a name="--operator"></a>- – operátor

Unární operátor negace ( **-** ) vytvoří negativní operand. Operandem unárního operátoru negace musí být aritmetický typ.

Celočíselné povýšení proběhne na celočíselných operandech a výsledný typ je typ, na který je operand povýšen. Další informace o tom, jak se povýšení provádí, najdete v tématu [standardní převody](standard-conversions.md) .

**Specifické pro společnost Microsoft**

Unární negace množství bez znaménka je prováděna odečtením hodnoty operandu 2 ^ n, kde n je počet bitů v objektu daného typu bez znaménka.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
