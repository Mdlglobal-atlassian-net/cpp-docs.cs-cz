---
title: 'Bitový inkluzivní operátor OR: |'
ms.date: 06/14/2018
f1_keywords:
- '|'
helpviewer_keywords:
- OR operator [C++], bitwise inclusive
- bitwise operators [C++], OR operator
- inclusive OR operator
- '| operator'
ms.assetid: 4c8a6a68-d828-447d-875a-aedb4ce3aa9a
ms.openlocfilehash: 0df3493930206d655c0d9bca8a2468151aa3c2c6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445508"
---
# <a name="bitwise-inclusive-or-operator-"></a>Bitový inkluzivní operátor OR: |

## <a name="syntax"></a>Syntaxe

> *výraz1* **|** *Výraz2*

## <a name="remarks"></a>Poznámky

Bitový operátor OR ( **&#124;** ) porovnává každý bit svého prvního operandu s odpovídajícím bitem jeho druhého operandu. Pokud má bit hodnotu 1, odpovídající bit výsledku je nastaven na hodnotu 1. V opačném případě je odpovídající bit výsledek nastaven na hodnotu 0.

Oba operandy bitového inkluzivního operátoru OR musí být celočíselné typy. Obvyklé aritmetické převody, které jsou pokryty [standardními](standard-conversions.md) převody, jsou aplikovány na operandy.

## <a name="operator-keyword-for-124"></a>Klíčové slovo operátoru pro&#124;

Operátor **bitor** je textový ekvivalent **&#124;** . Existují dva způsoby, jak získat přístup k operátoru **bitor** ve svých programech: zahrňte hlavičkový soubor \<iso646. h > nebo zkompilujte pomocí možnosti kompilátoru [/za](../build/reference/za-ze-disable-language-extensions.md) (zakázat jazykové rozšíření).

## <a name="example"></a>Příklad

```cpp
// expre_Bitwise_Inclusive_OR_Operator.cpp
// compile with: /EHsc
// Demonstrate bitwise inclusive OR
#include <iostream>
using namespace std;

int main() {
   unsigned short a = 0x5555;      // pattern 0101 ...
   unsigned short b = 0xAAAA;      // pattern 1010 ...

   cout  << hex << ( a | b ) << endl;   // prints "ffff" pattern 1111 ...
}
```

## <a name="see-also"></a>Viz také

[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Bitové operátory jazyka C](../c-language/c-bitwise-operators.md)