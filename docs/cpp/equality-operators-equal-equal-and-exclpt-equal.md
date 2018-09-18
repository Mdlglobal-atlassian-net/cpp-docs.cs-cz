---
title: 'Operátory rovnosti: == a! = | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- not_eq
- '!='
- ==
dev_langs:
- C++
helpviewer_keywords:
- '!= operator'
- equality operator
- not equal to comparison operator
- equality operator [C++], syntax
- == operator
- not_eq operator
- equal to operator
ms.assetid: ba4e9659-2392-4fb4-be5a-910a2a6df45a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d1072892c4ad69396c62a728f7e828e9c683d155
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068478"
---
# <a name="equality-operators--and-"></a>Operátory rovnosti: == a !=

## <a name="syntax"></a>Syntaxe

```
expression == expression
expression != expression
```

## <a name="remarks"></a>Poznámky

Binární relační operátory porovnání operandy striktní zjištění rovnosti či nerovnosti.

Relační operátory je rovno (`==`) a není rovno (`!=`), mají nižší prioritu než relační operátory, ale chovají podobně. Je typ výsledku pro tyto operátory **bool**.

Operátor rovnosti (`==`) vrátí **true** (1), pokud oba operandy mají stejnou hodnotu; v opačném případě vrátí **false** (0). Operátor není rovno (`!=`) vrátí **true** Pokud operandy nemají stejnou hodnotu; v opačném případě vrátí **false**.

## <a name="operator-keyword-for-"></a>Klíčové slovo pro operátor! =

Operátor `not_eq` je textový ekvivalent operátoru `!=`. Existují dva způsoby přístupu k `not_eq` operátor ve svých programech: zahrnutím souboru hlaviček `iso646.h`, nebo kompilací s [/Za](../build/reference/za-ze-disable-language-extensions.md) – možnost kompilátoru (zakázání jazykových rozšíření).

## <a name="example"></a>Příklad

```cpp
// expre_Equality_Operators.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main() {
   cout  << boolalpha
         << "The true expression 3 != 2 yields: "
         << (3 != 2) << endl
         << "The false expression 20 == 10 yields: "
         << (20 == 10) << endl;
}
```

Operátory rovnosti můžete porovnat ukazatelů na členy stejného typu. Porovnání jsou provedeny převody ukazatele na člen. Ukazatelé na členy je také možné porovnat s konstantním výrazem vyhodnoceným na hodnotu 0.

## <a name="see-also"></a>Viz také:

[Výrazy s binárními operátory](../cpp/expressions-with-binary-operators.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Relační operátory a operátory rovnosti jazyka C](../c-language/c-relational-and-equality-operators.md)