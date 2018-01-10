---
title: "Bitový operátor AND: &amp; | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: bitand
dev_langs: C++
helpviewer_keywords:
- AND operator
- bitwise operators [C++], AND operator
- '& operator [C++], bitwise operators'
ms.assetid: 76f40de3-c417-47b9-8a77-532f3fc990a5
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f3d74a39c68e4c16e55837a87e027e9e5991351f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="bitwise-and-operator-amp"></a>Bitový operátor AND:&amp;
## <a name="syntax"></a>Syntaxe  
  
```  
  
expression   
&  
 expression  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Může být jiné-výrazy a výrazy, nebo (předmětem omezení typu dál uvedených) rovnosti výrazy, relační výrazy, sčítání výrazy, multiplikativní výrazy, ukazatel na člena výrazy, přetypování výrazy unární výrazy přípony, nebo primární výrazů.  
  
 Bitový operátor AND (**&**) porovnává každý bit první operand pro příslušné bity Druhý operand. Pokud jsou obě bits 1, 1 je nastavena odpovídající bit výsledek. Odpovídající bit výsledek, jinak hodnota nastavena na hodnotu 0.  
  
 Celočíselné typy musí být oba operandy bitový operátor AND. Obvyklé aritmetické převody zahrnutých v [standardní převody](standard-conversions.md), se použijí pro operandy.  
  
## <a name="operator-keyword-for-"></a>Operator – klíčové slovo pro &  
 `bitand` Operátor je ekvivalentem text  **&** . Existují dva způsoby pro přístup `bitand` operátor v programy: zahrnout soubor hlaviček `iso646.h`, nebo kompilovat s [/Za](../build/reference/za-ze-disable-language-extensions.md) – možnost kompilátoru (zakázat jazyková rozšíření).  
  
## <a name="example"></a>Příklad  
  
```  
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
 [Integrované operátory C++, jejich priorita a asociativita](cpp-built-in-operators-precedence-and-associativity.md)  
 [Předdefinované C++ operátory, prioritu a Asociativnost](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Bitové operátory jazyka C](../c-language/c-bitwise-operators.md)