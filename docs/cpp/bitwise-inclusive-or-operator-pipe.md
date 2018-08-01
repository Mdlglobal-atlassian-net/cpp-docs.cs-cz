---
title: 'Bitový inkluzivní operátor OR: || Dokumentace Microsoftu'
ms.custom: ''
ms.date: 06/14/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- bitor
- '|'
dev_langs:
- C++
helpviewer_keywords:
- OR operator [C++], bitwise inclusive
- bitwise operators [C++], OR operator
- inclusive OR operator
- '| operator'
ms.assetid: 4c8a6a68-d828-447d-875a-aedb4ce3aa9a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75cb922f2bd5cc6da2666a59bd0827b7ec013bf2
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408719"
---
# <a name="bitwise-inclusive-or-operator-"></a>Bitový inkluzivní operátor OR: |

## <a name="syntax"></a>Syntaxe

> *Expression1* **|** *expression2*

## <a name="remarks"></a>Poznámky

Bitový inkluzivní operátor OR (**&#124;**) porovnává každý bit jeho prvního operandu s odpovídajícím bitem jeho druhého operandu. Pokud buď bit na hodnotu 1, odpovídající bit výsledku je nastavená na 1. V opačném případě je odpovídající výsledek bit nastaven na hodnotu 0.

Oba operandy bitového inkluzivního operátoru OR musí být celočíselné typy. Obvyklé aritmetické převody uvedené v [standardní převody](standard-conversions.md) jsou na operandy použity.

## <a name="operator-keyword-for-124"></a>Klíčové slovo pro operátor&#124;

**Bitor** operátor je textový ekvivalent operátoru **&#124;**. Existují dva způsoby přístupu k **bitor** operátor ve svých programech: zahrnutím souboru hlaviček \<soubor iso646.h >, nebo kompilací s [/Za](../build/reference/za-ze-disable-language-extensions.md) – možnost kompilátoru (zakázání jazykových rozšíření).

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

## <a name="see-also"></a>Viz také:
 [Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)  
 [Bitové operátory jazyka C](../c-language/c-bitwise-operators.md)  