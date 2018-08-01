---
title: 'Bitový exkluzivní operátor OR: ^ | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], bitwise
- exclusive OR operator
- XOR operator
- bitwise operators [C++], OR operator
- ^ operator
- OR operator [C++], bitwise exclusive
- operators [C++], logical
ms.assetid: f9185d85-65d5-4f64-a6d6-679758d52217
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fe2f64c20c0d741608dfb2631c2e36026a31e8bb
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406673"
---
# <a name="bitwise-exclusive-or-operator-"></a>Bitový exkluzivní operátor OR: ^
## <a name="syntax"></a>Syntaxe  
  
```  
expression ^ expression  
```  
  
## <a name="remarks"></a>Poznámky  
Bitový exkluzivní operátor OR (**^**) porovnává každý bit jeho prvního operandu s odpovídajícím bitem jeho druhého operandu. Pokud jeden bit na hodnotu 0 a dalších bit na hodnotu 1, odpovídající bit výsledku je nastavená na 1. V opačném případě je odpovídající výsledek bit nastaven na hodnotu 0.  
  
Oba operandy bitový exkluzivní operátor OR musí být integrální typy. Obvyklé aritmetické převody uvedené v [standardní převody](standard-conversions.md) jsou na operandy použity.  
  
## <a name="operator-keyword-for-"></a>Klíčové slovo pro operátor ^  
**Xor** operátor je textový ekvivalent operátoru **^**. Existují dva způsoby přístupu k **xor** operátor ve svých programech: zahrnutím souboru hlaviček `iso646.h`, nebo kompilací s [/Za](../build/reference/za-ze-disable-language-extensions.md) – možnost kompilátoru (zakázání jazykových rozšíření).  
  
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
  
## <a name="see-also"></a>Viz také:  
 [Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   