---
title: 'Deferenční operátor: *'
ms.date: 11/04/2016
helpviewer_keywords:
- '* operator'
- indirection operator
- operators [C++], indirection
- indirection operator [C++], syntax
ms.assetid: c50309e1-6c02-4184-9fcb-2e13c1f4ac03
ms.openlocfilehash: a35d8cb28baaee37ad64a61cbcb9d4c76a5aad06
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482732"
---
# <a name="indirection-operator-"></a>Deferenční operátor: *

## <a name="syntax"></a>Syntaxe

```
* cast-expression
```

## <a name="remarks"></a>Poznámky

Operátor unární dereference (<strong>\*</strong>) přistoupí přes ukazatel; to znamená, převede hodnotu ukazatele na l hodnotou. Operand operátoru dereference musí být ukazatel na typ. Výsledek výrazu dereference je typ, ze kterého je odvozen typ ukazatele. Použití <strong>\*</strong> operátor v tomto kontextu se liší od jeho význam jako binární operátor, který je násobení.

Ukazuje-li operand na funkci, je výsledkem označení funkce. Ukazuje-li na umístění úložiště, je výsledkem l-hodnota označující umístění úložiště.

Operátor dereference lze kumulativně dereference ukazatele na ukazatele. Příklad:

```cpp
// expre_Indirection_Operator.cpp
// compile with: /EHsc
// Demonstrate indirection operator
#include <iostream>
using namespace std;
int main() {
   int n = 5;
   int *pn = &n;
   int **ppn = &pn;

   cout  << "Value of n:\n"
         << "direct value: " << n << endl
         << "indirect value: " << *pn << endl
         << "doubly indirect value: " << **ppn << endl
         << "address of n: " << pn << endl
         << "address of n via indirection: " << *ppn << endl;
}
```

Pokud je hodnota ukazatele neplatná, výsledek není definován. Následující seznam zahrnuje některé z nejběžnějších situací, které zneplatňují hodnotu ukazatele.

- Ukazatel je nulový.

- Ukazatel určuje adresu místní položky, která není v době reference viditelná.

- Ukazatel určuje adresu, která je pro typ objektu, na který ukazatel ukazuje, nesprávně zarovnána.

- Ukazatel určuje adresu, která není používána spuštěným programem.

## <a name="see-also"></a>Viz také:

[Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operátor address-of: &](../cpp/address-of-operator-amp.md)<br/>
[Dereferenční operátory a operátory adresy](../c-language/indirection-and-address-of-operators.md)