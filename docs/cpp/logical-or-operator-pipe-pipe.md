---
title: 'Logický operátor OR: ||'
ms.date: 06/14/2018
f1_keywords:
- '||'
helpviewer_keywords:
- OR operator [C++], logical
- '|| operator'
- OR operator
- logical OR operator
ms.assetid: 31837c99-2655-4bf3-8ded-f13b7a9dc533
ms.openlocfilehash: 94b2bc024dd7223ac7adacc72924f5ee289bab37
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178077"
---
# <a name="logical-or-operator-"></a>Logický operátor OR: ||

## <a name="syntax"></a>Syntaxe

> logický operátor *or* **||** *logický operátor and-Expression*

## <a name="remarks"></a>Poznámky

Logický operátor OR ( **||** ) vrátí logickou hodnotu true, pokud má buď operátor nebo oba OPERANDY hodnotu true, jinak vrátí hodnotu false. Operandy jsou implicitně převedeny na typ **bool** před vyhodnocením a výsledek je typu **bool**. Logická operace OR je asociativní zleva doprava.

Operandy logického operátoru OR nemusí být stejného typu, musí však být typy celého čísla nebo ukazatele. Operandy jsou obvykle relační výrazy nebo výrazy rovnosti.

První operand je zcela vyhodnocen a před pokračováním ve vyhodnocování logického výrazu OR jsou dokončeny všechny vedlejší účinky.

Druhý operand je vyhodnocen pouze v případě, že je první operand vyhodnocen na hodnotu false (0). Tím jsou odstraněna nepotřebná vyhodnocení druhého operandu, je-li logický výraz OR vyhodnocen na hodnotu true.

```cpp
printf( "%d" , (x == w || x == y || x == z) );
```

Rovná-li se v příkladu výše proměnná `x` proměnné `w`, `y` nebo `z`, je druhý argument funkce `printf` vyhodnocen na hodnotu true a dojde k vypsání hodnoty 1. V opačném případě se vyhodnotí jako false a bude vytištěna hodnota 0. Jakmile se jedna z podmínek vyhodnotí jako true, vyhodnocování se zastaví.

## <a name="operator-keyword-for-124124"></a>Klíčové slovo operátoru pro&#124;&#124;

Operátor **or** je textový ekvivalent **||** . Existují dva způsoby, jak získat přístup k operátoru **or** ve svých programech: zahrňte soubor hlaviček \<iso646. h > nebo zkompilujte pomocí možnosti kompilátoru [/za](../build/reference/za-ze-disable-language-extensions.md) (Disable Language Extensions).

## <a name="example"></a>Příklad

```cpp
// expre_Logical_OR_Operator.cpp
// compile with: /EHsc
// Demonstrate logical OR
#include <iostream>
using namespace std;
int main() {
   int a = 5, b = 10, c = 15;
   cout  << boolalpha
         << "The true expression "
         << "a < b || b > c yields "
         << (a < b || b > c) << endl
         << "The false expression "
         << "a > b || b > c yields "
         << (a > b || b > c) << endl;
}
```

## <a name="see-also"></a>Viz také

[C++Přednost předdefinovaných operátorů a asociativita](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Logické operátory jazyka C](../c-language/c-logical-operators.md)
