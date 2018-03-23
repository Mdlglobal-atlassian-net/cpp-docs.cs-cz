---
title: 'Jeden & č. 39; s vlastní operátor doplňku: ~ | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- "~"
dev_langs:
- C++
helpviewer_keywords:
- tilde (~) one's complement operator
- one's complement operator
- bitwise-complement operator
- compl operator
- ~ operator [C++], syntax
ms.assetid: 4bf81967-34f7-4b4b-aade-fd03d5da0174
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 635a3e3b2d270d2164adc3f25a260085d7c50d60
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="one39s-complement-operator-"></a>Jeden & č. 39; s vlastní operátor doplňku: ~
## <a name="syntax"></a>Syntaxe  
  
```  
  
~ cast-expression  
```  
  
## <a name="remarks"></a>Poznámky  
 Jeden z operátorů doplňku (`~`), někdy nazývaný operátor „bitového doplňku“, vrací jedničkový bitový doplněk svého operandu. To znamená, že každý bit, který je 1 v operandu, je 0 ve výsledku. A naopak, každý bit, který je 0 v operandu, je 1 ve výsledku. Operand operátoru jedničkového doplňku musí být celočíselného typu.  
  
## <a name="operator-keyword-for-"></a>Klíčové slovo pro operátor ~  
 Operátor `compl` je textový ekvivalent operátoru `~`. Existují dva způsoby pro přístup `compl` operátor v programy: zahrnout soubor hlaviček `iso646.h`, nebo kompilovat s [/Za](../build/reference/za-ze-disable-language-extensions.md).  
  
## <a name="example"></a>Příklad  
  
```  
// expre_One_Complement_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
int main () {  
   unsigned short y = 0xFFFF;  
   cout << hex << y << endl;  
   y = ~y;   // Take one's complement  
   cout << hex << y << endl;  
}  
```  
  
 V tomto příkladu je nová hodnota přiřazená proměnné `y` jedničkovým doplňkem hodnoty bez znaménka 0xFFFF nebo 0x0000.  
  
 Celočíselné povýšení proběhne na celočíselných operandech a výsledný typ je typ, na který je operand povýšen. V tématu [standardní převody](standard-conversions.md) Další informace o tom, jak se provádí povýšení.  
  
## <a name="see-also"></a>Viz také  
 [Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)   
 [Předdefinované C++ operátory, prioritu a Asociativnost](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Unární aritmetické operátory](../c-language/unary-arithmetic-operators.md)