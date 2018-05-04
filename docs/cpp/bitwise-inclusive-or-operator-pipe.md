---
title: 'Bitový inkluzivní operátor OR: || Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: fc43460bc2c20262156bfdc6bd7f69a693c222f0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="bitwise-inclusive-or-operator-"></a>Bitový inkluzivní operátor OR: |
## <a name="syntax"></a>Syntaxe  
  
```  
  
expression   
|  
 expression  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Bitový inkluzivní operátor OR (**&#124;**) porovnává každý bit jeho první operand odpovídající bit její druhý operand. Pokud je buď bit 1, odpovídající výsledek bit nastavená na 1. Odpovídající bit výsledek, jinak hodnota nastavena na hodnotu 0.  
  
 Oba operandy bitového inkluzivního operátoru OR musí být celočíselné typy. Obvyklé aritmetické převody zahrnutých v [standardní převody](standard-conversions.md) se použijí pro operandy.  
  
## <a name="operator-keyword-for-124"></a>Operator – klíčové slovo pro&#124;  
 `bitor` Operátor je ekvivalentem text **&#124;**. Existují dva způsoby pro přístup `bitor` operátor v programy: zahrnout soubor hlaviček `iso646.h`, nebo kompilovat s [/Za](../build/reference/za-ze-disable-language-extensions.md) – možnost kompilátoru (zakázat jazyková rozšíření).  
  
## <a name="example"></a>Příklad  
  
```  
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
 [Předdefinované C++ operátory, prioritu a Asociativnost](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Bitové operátory jazyka C](../c-language/c-bitwise-operators.md)

