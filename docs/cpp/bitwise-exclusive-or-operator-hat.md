---
title: "Bitový exkluzivní operátor OR: ^ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- operators [C++], bitwise
- exclusive OR operator
- XOR operator
- bitwise operators [C++], OR operator
- ^ operator
- OR operator [C++], bitwise exclusive
- operators [C++], logical
ms.assetid: f9185d85-65d5-4f64-a6d6-679758d52217
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6d6bd80c7144ea3f4a2288e07b7801612ed62efd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="bitwise-exclusive-or-operator-"></a>Bitový exkluzivní operátor OR: ^
## <a name="syntax"></a>Syntaxe  
  
```  
expression ^ expression  
```  
  
## <a name="remarks"></a>Poznámky  
Bitový exkluzivní operátor OR (**^**) porovnává každý bit jeho první operand odpovídající bit její druhý operand. Pokud je jeden bit 0 a dalších bit je 1, 1 je nastavena odpovídající výsledek bit. Odpovídající bit výsledek, jinak hodnota nastavena na hodnotu 0.  
  
Celočíselné typy musí být oba operandy k bitový exkluzivní operátor OR. Obvyklé aritmetické převody zahrnutých v [standardní převody](standard-conversions.md) se použijí pro operandy.  
  
## <a name="operator-keyword-for-"></a>Operator – klíčové slovo pro ^  
**Xor** operátor je ekvivalentem text  **^** . Existují dva způsoby pro přístup **xor** operátor v programy: zahrnout soubor hlaviček `iso646.h`, nebo kompilovat s [/Za](../build/reference/za-ze-disable-language-extensions.md) – možnost kompilátoru (zakázat jazyková rozšíření).  
  
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


