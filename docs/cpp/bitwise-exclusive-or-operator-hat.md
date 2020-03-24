---
title: 'Bitový exkluzivní operátor OR: ^'
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], bitwise
- exclusive OR operator
- XOR operator
- bitwise operators [C++], OR operator
- ^ operator
- OR operator [C++], bitwise exclusive
- operators [C++], logical
ms.assetid: f9185d85-65d5-4f64-a6d6-679758d52217
ms.openlocfilehash: 9a44dc60a985729aae79ed0e2e48c44adace647b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190713"
---
# <a name="bitwise-exclusive-or-operator-"></a>Bitový exkluzivní operátor OR: ^

## <a name="syntax"></a>Syntaxe

```
expression ^ expression
```

## <a name="remarks"></a>Poznámky

Bitový exkluzivní operátor OR ( **^** ) porovnává každý bit jeho prvního operandu s odpovídajícím bitem jeho druhého operandu. Pokud je jeden bit 0 a druhý bit je 1, odpovídající bit výsledku je nastaven na hodnotu 1. V opačném případě je odpovídající bit výsledek nastaven na hodnotu 0.

Oba operandy logického operátoru OR musí být integrálního typu. Obvyklé aritmetické převody, které jsou pokryty [standardními](standard-conversions.md) převody, jsou aplikovány na operandy.

## <a name="operator-keyword-for-"></a>Klíčové slovo operátoru pro ^

Operátor **XOR** je textový ekvivalent **^** . Existují dva způsoby, jak získat přístup k operátoru **XOR** ve svých programech: zahrňte hlavičkový soubor `iso646.h`nebo zkompilujte pomocí možnosti kompilátoru [/za](../build/reference/za-ze-disable-language-extensions.md) (Disable Language Extensions).

## <a name="example"></a>Příklad

```cpp
// expre_Bitwise_Exclusive_OR_Operator.cpp
// compile with: /EHsc
// Demonstrate bitwise exclusive OR
#include <iostream>
using namespace std;
int main() {
   unsigned short a = 0x5555;      // pattern 0101 ...
   unsigned short b = 0xFFFF;      // pattern 1111 ...

   cout  << hex << ( a ^ b ) << endl;   // prints "aaaa" pattern 1010 ...
}
```

## <a name="see-also"></a>Viz také

[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
