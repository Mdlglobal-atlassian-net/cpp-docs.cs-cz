---
title: 'Logický operátor negace: !'
ms.date: 08/27/2018
f1_keywords:
- '!'
- Not
helpviewer_keywords:
- '! operator'
- NOT operator
- logical negation
ms.assetid: 650add9f-a7bc-426c-b01d-5fc6a81c8b62
ms.openlocfilehash: 7b37e5108ca01d782c13508c0cd7a96b096cd745
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50493720"
---
# <a name="logical-negation-operator-"></a>Logický operátor negace: !

## <a name="syntax"></a>Syntaxe

```
! cast-expression
```

## <a name="remarks"></a>Poznámky

Operátor logické negace (**!**) změní význam jeho operandu. Operand musí být aritmetického typu nebo typu ukazatele (nebo výraz, jehož výsledkem je aritmetický typ nebo typ ukazatele). Operand je implicitně převeden na typ **bool**. Výsledkem je hodnota TRUE, pokud má převedený operand hodnotu FALSE; Výsledkem je FALSE, pokud má převedený operand hodnotu TRUE. Výsledek je typu **bool**.

Pro výraz *e*, je jednočlenný výraz `!e` je ekvivalentní výraz `(e == 0)`, s výjimkou případů, ve kterém se účastní přetížené operátory.

## <a name="operator-keyword-for-"></a>Klíčové slovo pro operátor !

**Není** operátor je alternativní pravopis **!**. Existují dva způsoby přístupu k **není** operátor ve svých programech: zahrnutím souboru hlaviček \<soubor iso646.h >, nebo kompilací s [/Za](../build/reference/za-ze-disable-language-extensions.md) – možnost kompilátoru (zakázání jazykových rozšíření).

## <a name="example"></a>Příklad

```cpp
// expre_Logical_NOT_Operator.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main() {
    int i = 0;
    if (!i)
        cout << "i is zero" << endl;
}
```

## <a name="see-also"></a>Viz také:

[Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Unární aritmetické operátory](../c-language/unary-arithmetic-operators.md)<br/>
