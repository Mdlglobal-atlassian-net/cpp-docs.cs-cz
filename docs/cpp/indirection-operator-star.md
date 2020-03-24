---
title: 'Deferenční operátor: *'
ms.date: 11/04/2016
helpviewer_keywords:
- '* operator'
- indirection operator
- operators [C++], indirection
- indirection operator [C++], syntax
ms.assetid: c50309e1-6c02-4184-9fcb-2e13c1f4ac03
ms.openlocfilehash: 8f27cfd943455d52b04c41ef2d2d83e6e03a84c0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178274"
---
# <a name="indirection-operator-"></a>Deferenční operátor: *

## <a name="syntax"></a>Syntaxe

```
* cast-expression
```

## <a name="remarks"></a>Poznámky

Unární operátor indirekce (<strong>\*</strong>) odkazuje na ukazatel; To znamená, že převede hodnotu ukazatele na l-value. Operandem operátoru dereference musí být ukazatel na typ. Výsledek nepřímého výrazu je typ, ze kterého je odvozen typ ukazatele. Použití operátoru <strong>\*</strong> v tomto kontextu se liší od významu jako binární operátor, což je násobení.

Ukazuje-li operand na funkci, je výsledkem označení funkce. Ukazuje-li na umístění úložiště, je výsledkem l-hodnota označující umístění úložiště.

Operátor dereference lze použít kumulativně pro přesměrování ukazatelů na ukazatele. Příklad:

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

## <a name="see-also"></a>Viz také

[Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operátor address-of: &](../cpp/address-of-operator-amp.md)<br/>
[Dereferenční operátory a operátory adresy](../c-language/indirection-and-address-of-operators.md)
