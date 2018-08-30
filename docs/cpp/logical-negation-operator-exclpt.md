---
title: 'Logický operátor negace: ! | Dokumenty Microsoft'
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- '!'
- Not
dev_langs:
- C++
helpviewer_keywords:
- '! operator'
- NOT operator
- logical negation
ms.assetid: 650add9f-a7bc-426c-b01d-5fc6a81c8b62
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4594a8b1a881b6fa92909e7c7014087ff6240de8
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211815"
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
