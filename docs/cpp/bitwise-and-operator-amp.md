---
title: 'Bitový operátor AND: &amp;'
ms.date: 11/04/2016
f1_keywords:
- bitand
helpviewer_keywords:
- AND operator
- bitwise operators [C++], AND operator
- '& operator [C++], bitwise operators'
ms.assetid: 76f40de3-c417-47b9-8a77-532f3fc990a5
ms.openlocfilehash: b7d0d73802a5af7ab71e980d73eaff5c5b3c4bb8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575354"
---
# <a name="bitwise-and-operator-amp"></a>Bitový operátor AND: &amp;

## <a name="syntax"></a>Syntaxe

```
expression & expression
```

## <a name="remarks"></a>Poznámky

Výrazy mohou být jiné a výrazů, nebo (na základě práv subjektů k omezení typů, které jsou uvedené níže) výrazy rovnosti, relační výrazy, sčítání výrazy, násobení výrazy, ukazatel na člen výrazy, výrazy přetypování, unární výrazy, výrazy přípony nebo primární výrazy.

Bitový operátor AND (**&**) porovnává každý bit prvního operandu s odpovídajícím bitem druhého operandu. Pokud i službu bits 1, odpovídající bit výsledku je nastavená na 1. V opačném případě je odpovídající výsledek bit nastaven na hodnotu 0.

Oba operandy bitového operátoru AND musí být integrální typy. Obvyklé aritmetické převody uvedené v [standardní převody](standard-conversions.md), jsou na operandy použity.

## <a name="operator-keyword-for-"></a>Klíčové slovo pro operátor &

**Bitand** operátor je textový ekvivalent operátoru **&**. Existují dva způsoby přístupu k **bitand** operátor ve svých programech: zahrnutím souboru hlaviček `iso646.h`, nebo kompilací s [/Za](../build/reference/za-ze-disable-language-extensions.md) – možnost kompilátoru (zakázání jazykových rozšíření).

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

## <a name="see-also"></a>Viz také:

[Integrované operátory C++, jejich priorita a asociativita](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Bitové operátory jazyka C](../c-language/c-bitwise-operators.md)