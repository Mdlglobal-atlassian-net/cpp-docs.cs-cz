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
ms.openlocfilehash: 0843ba95467c3ae0d735476de48a8195a59788f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62368653"
---
# <a name="logical-and-operator-ampamp"></a>Logický operátor AND: &amp;&amp;

## <a name="syntax"></a>Syntaxe

```
expression && expression
```

## <a name="remarks"></a>Poznámky

Logický operátor AND (**&&**) vrátí logickou hodnotu TRUE, pokud jsou oba operandy hodnotu TRUE a v opačném případě vrátí hodnotu FALSE. Operandy jsou implicitně převedeny na typ **bool** před hodnocení a výsledek je typu **bool**. Logický operátor AND má asociativní zleva doprava.

Operandy logického operátoru AND nemusí být stejného typu, ale musí být integrálového typu nebo typu ukazatele. Operandy jsou obvykle relační výrazy nebo výrazy rovnosti.

První operand je zcela vyhodnocen a všechny vedlejší účinky jsou dokončeny před pokračováním ve vyhodnocování logického výrazu AND.

Druhý operand je vyhodnocen pouze v případě, že první operand vyhodnocen na hodnotu true (nenulový). Toto vyhodnocení odstraňuje nepotřebná vyhodnocení druhého operandu po logický výraz AND je NEPRAVDA. To může být použito krátká smyčka – vyhodnocení, aby se zabránilo přístup přes ukazatel null, jak je znázorněno v následujícím příkladu:

```cpp
char *pch = 0;
...
(pch) && (*pch = 'a');
```

Pokud `pch` má hodnotu null (0) pravé straně výraz nikdy není vyhodnocen. Proto není možné přiřazení přes ukazatel s hodnotou null.

## <a name="operator-keyword-for-"></a>Klíčové slovo pro operátor & &

**a** operátor je textový ekvivalent operátoru **&&**. Existují dva způsoby přístupu k **a** operátor ve svých programech: zahrnutím souboru hlaviček `iso646.h`, nebo kompilací s [/Za](../build/reference/za-ze-disable-language-extensions.md) – možnost kompilátoru (zakázání jazykových rozšíření).

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

## <a name="see-also"></a>Viz také:

[Integrované operátory C++ Priorita a asociativita](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Logické operátory jazyka C](../c-language/c-logical-operators.md)