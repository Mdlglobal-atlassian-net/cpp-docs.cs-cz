---
title: 'Logický operátor AND: &amp;&amp;'
ms.date: 11/04/2016
f1_keywords:
- '&&'
helpviewer_keywords:
- logical AND operator
- AND operator
- '&& operator'
ms.assetid: 50cfa664-a8c4-4b31-9bab-2f80d7cd2d1f
ms.openlocfilehash: b21d91009c455b67af6fae88fceafeeaf8043301
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179429"
---
# <a name="logical-and-operator-ampamp"></a>Logický operátor AND: &amp;&amp;

## <a name="syntax"></a>Syntaxe

```
expression && expression
```

## <a name="remarks"></a>Poznámky

Logický operátor AND ( **&&** ) vrátí logickou hodnotu true, pokud mají oba OPERANDY hodnotu true a vrátí hodnotu false v opačném případě. Operandy jsou implicitně převedeny na typ **bool** před vyhodnocením a výsledek je typu **bool**. Logický a má asociativita zleva doprava.

Operandy logického operátoru AND nemusí být stejného typu, ale musí být integrálního typu nebo typu ukazatele. Operandy jsou obvykle relační výrazy nebo výrazy rovnosti.

První operand je zcela vyhodnocen a všechny vedlejší účinky jsou dokončeny před pokračováním v vyhodnocení logického výrazu AND.

Druhý operand je vyhodnocen pouze v případě, že je první operand vyhodnocen jako true (nenulový). Toto vyhodnocení eliminuje nepotřebné vyhodnocení druhého operandu v případě, že logický operátor AND je false. Toto zkrácené hodnocení můžete použít, chcete-li zabránit přečtení ukazatele na hodnotu null, jak je znázorněno v následujícím příkladu:

```cpp
char *pch = 0;
...
(pch) && (*pch = 'a');
```

Pokud má `pch` hodnotu null (0), pravá strana výrazu se nikdy nevyhodnotí. Proto není možné přiřazení přes ukazatel s hodnotou null.

## <a name="operator-keyword-for-"></a>Klíčové slovo operátoru pro & &

Operátor **and** je textový ekvivalent **&&** . Existují dva způsoby, jak získat přístup k operátoru **and** ve svých programech: zahrňte hlavičkový soubor `iso646.h`nebo zkompilujte pomocí možnosti kompilátoru [/za](../build/reference/za-ze-disable-language-extensions.md) (Disable Language Extensions).

## <a name="example"></a>Příklad

```cpp
// expre_Logical_AND_Operator.cpp
// compile with: /EHsc
// Demonstrate logical AND
#include <iostream>

using namespace std;

int main() {
   int a = 5, b = 10, c = 15;
   cout  << boolalpha
         << "The true expression "
         << "a < b && b < c yields "
         << (a < b && b < c) << endl
         << "The false expression "
         << "a > b && b < c yields "
         << (a > b && b < c) << endl;
}
```

## <a name="see-also"></a>Viz také

[C++Přednost předdefinovaných operátorů a asociativita](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Logické operátory jazyka C](../c-language/c-logical-operators.md)
