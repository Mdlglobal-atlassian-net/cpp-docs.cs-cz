---
title: 'Logický operátor negace: !'
ms.date: 08/27/2018
f1_keywords:
- '!'
helpviewer_keywords:
- '! operator'
- NOT operator
- logical negation
ms.assetid: 650add9f-a7bc-426c-b01d-5fc6a81c8b62
ms.openlocfilehash: 06142ef15fcdbafdbae4b892772a04b117c087f6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446536"
---
# <a name="logical-negation-operator-"></a>Logický operátor negace: !

## <a name="syntax"></a>Syntaxe

```
! cast-expression
```

## <a name="remarks"></a>Poznámky

Logický operátor negace ( **!** ) obrátí význam jeho operandu. Operand musí být aritmetického typu nebo typu ukazatele (nebo výraz, jehož výsledkem je aritmetický typ nebo typ ukazatele). Operand je implicitně převeden na typ **bool**. Výsledek je TRUE, pokud je převedený operand FALSE; výsledek je FALSE, pokud má převedený operand hodnotu TRUE. Výsledek je typu **bool**.

Pro výraz *e*je unární výraz `!e` ekvivalentní k výrazu `(e == 0)`, s výjimkou případů, kdy jsou zapojeny přetížené operátory.

## <a name="operator-keyword-for-"></a>Klíčové slovo pro operátor !

Operátor **Not** je alternativním pravopisem **!** . Existují dva způsoby, jak získat přístup k operátoru **Not** ve svých programech: zahrňte soubor hlaviček \<iso646. h > nebo zkompilujte pomocí možnosti kompilátoru [/za](../build/reference/za-ze-disable-language-extensions.md) (Disable Language Extensions).

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

## <a name="see-also"></a>Viz také

[Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Unární aritmetické operátory](../c-language/unary-arithmetic-operators.md)<br/>
