---
title: 'Operátory rovnosti: == a !='
ms.date: 11/04/2016
f1_keywords:
- '!='
- ==
helpviewer_keywords:
- '!= operator'
- equality operator
- not equal to comparison operator
- equality operator [C++], syntax
- == operator
- not_eq operator
- equal to operator
ms.assetid: ba4e9659-2392-4fb4-be5a-910a2a6df45a
ms.openlocfilehash: 8a0c08f438528caeaac6d5e52e806a36fe56dd25
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189244"
---
# <a name="equality-operators--and-"></a>Operátory rovnosti: == a !=

## <a name="syntax"></a>Syntaxe

```
expression == expression
expression != expression
```

## <a name="remarks"></a>Poznámky

Binární operátory rovnosti porovnávají své operandy pro striktní rovnost nebo nerovnost.

Operátory rovnosti, které se rovnají (`==`) a nejsou rovny (`!=`), mají nižší prioritu než relační operátory, ale chovají se podobně. Výsledný typ pro tyto operátory je **bool**.

Operátor EQUAL-to (`==`) vrátí **hodnotu true** (1), pokud mají oba operandy stejnou hodnotu. v opačném případě vrátí **hodnotu false** (0). Operátor not-equal-to (`!=`) vrátí **hodnotu true** , pokud operandy nemají stejnou hodnotu; v opačném případě vrátí **hodnotu false**.

## <a name="operator-keyword-for-"></a>Klíčové slovo operátoru pro! =

Operátor `not_eq` je textový ekvivalent operátoru `!=`. Existují dva způsoby, jak získat přístup k operátoru `not_eq` ve svých programech: zahrňte hlavičkový soubor `iso646.h`nebo zkompilujte pomocí možnosti kompilátoru [/za](../build/reference/za-ze-disable-language-extensions.md) (Disable Language Extensions).

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

Operátory rovnosti mohou porovnat ukazatele na členy stejného typu. V takovém případě jsou prováděny převody ukazatele na člena. Ukazatele na členy lze také porovnat s konstantním výrazem, který je vyhodnocen na hodnotu 0.

## <a name="see-also"></a>Viz také

[Výrazy s binárními operátory](../cpp/expressions-with-binary-operators.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Relační operátory a operátory rovnosti jazyka C](../c-language/c-relational-and-equality-operators.md)
