---
title: "Logický operátor OR: || | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '||'
dev_langs: C++
helpviewer_keywords:
- OR operator [C++], logical
- '|| operator'
- OR operator
- logical OR operator
ms.assetid: 31837c99-2655-4bf3-8ded-f13b7a9dc533
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 462c0091b3d1bd53eff7e221d2dea7d36403ab8d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="logical-or-operator-"></a>Logický operátor OR: ||
## <a name="syntax"></a>Syntaxe  
  
```  
  
logical-or-expression   
||  
 logical-and-expression  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Logický operátor OR (`||`) vrátí logickou hodnotu **true** Pokud nebo oba operandy **true** a vrátí **false** jinak. Operandy jsou před vyhodnocením implicitně převáděny na typ `bool`, přičemž výsledek je také typu `bool`. Logická operace OR je asociativní zleva doprava.  
  
 Operandy logického operátoru OR nemusí být stejného typu, musí však být typy celého čísla nebo ukazatele. Operandy jsou obvykle relační výrazy nebo výrazy rovnosti.  
  
 První operand je zcela vyhodnocen a před pokračováním ve vyhodnocování logického výrazu OR jsou dokončeny všechny vedlejší účinky.  
  
 Druhý operand je vyhodnocen pouze v případě, že je první operand vyhodnocen na hodnotu false (0). Tím jsou odstraněna nepotřebná vyhodnocení druhého operandu, je-li logický výraz OR vyhodnocen na hodnotu true.  
  
```  
printf( "%d" , (x == w || x == y || x == z) );  
```  
  
 Rovná-li se v příkladu výše proměnná `x` proměnné `w`, `y` nebo `z`, je druhý argument funkce `printf` vyhodnocen na hodnotu true a dojde k vypsání hodnoty 1. Jinak je vyhodnocena jako false a hodnota 0 je vytisknout. Jakmile jedna z podmínek vyhodnotí jako true, přestane vyhodnocení.  
  
## <a name="operator-keyword-for-124124"></a>Operator – klíčové slovo pro &#124; &#124;  
 **Nebo** operátor je ekvivalentem text `||`. Existují dva způsoby pro přístup **nebo** operátor v programy: zahrnout soubor hlaviček `iso646.h`, nebo kompilovat s [/Za](../build/reference/za-ze-disable-language-extensions.md) – možnost kompilátoru (zakázat jazyková rozšíření).  
  
## <a name="example"></a>Příklad  
  
```  
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
[Předdefinované C++ operátory přednost a Asociativnost](cpp-built-in-operators-precedence-and-associativity.md) [operátory předdefinované C++, prioritu a Asociativnost](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Logické operátory jazyka C](../c-language/c-logical-operators.md)