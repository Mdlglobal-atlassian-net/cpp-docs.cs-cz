---
title: 'Bitový operátor AND: &amp;'
ms.date: 11/04/2016
helpviewer_keywords:
- AND operator
- bitwise operators [C++], AND operator
- '& operator [C++], bitwise operators'
ms.assetid: 76f40de3-c417-47b9-8a77-532f3fc990a5
ms.openlocfilehash: b5c99d19be3461b10a1126dea3a45d308c0fc558
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181288"
---
# <a name="bitwise-and-operator-amp"></a>Bitový operátor AND: &amp;

## <a name="syntax"></a>Syntaxe

```
expression & expression
```

## <a name="remarks"></a>Poznámky

Výrazy můžou být jiné výrazy a – nebo (podléhají omezením typu uvedeným níže) výrazy rovnosti, relační výrazy, výrazy doplňku, multiplikativní výrazy, ukazatel na členské výrazy, výrazy přetypování, unární výrazy, přípony výrazů nebo primární výrazy.

Bitový operátor AND ( **&** ) porovnává každý bit prvního operandu s odpovídajícím bitem druhého operandu. Pokud jsou obě bity 1, odpovídající bit výsledku je nastaven na hodnotu 1. V opačném případě je odpovídající bit výsledek nastaven na hodnotu 0.

Oba operandy bitového operátoru AND musí být integrálních typů. Obvyklé aritmetické převody, které jsou pokryty [standardními](standard-conversions.md)převody, jsou aplikovány na operandy.

## <a name="operator-keyword-for-"></a>Klíčové slovo operátoru pro &

Operátor **BITAND** je textový ekvivalent **&** . Existují dva způsoby, jak získat přístup k operátoru **BITAND** ve svých programech: zahrňte hlavičkový soubor `iso646.h`nebo zkompilujte pomocí možnosti kompilátoru [/za](../build/reference/za-ze-disable-language-extensions.md) (Disable Language Extensions).

## <a name="example"></a>Příklad

```cpp
// expre_Bitwise_AND_Operator.cpp
// compile with: /EHsc
// Demonstrate bitwise AND
#include <iostream>
using namespace std;
int main() {
   unsigned short a = 0xFFFF;      // pattern 1111 ...
   unsigned short b = 0xAAAA;      // pattern 1010 ...

   cout  << hex << ( a & b ) << endl;   // prints "aaaa", pattern 1010 ...
}
```

## <a name="see-also"></a>Viz také

[Integrované operátory C++, jejich priorita a asociativita](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Bitové operátory jazyka C](../c-language/c-bitwise-operators.md)
