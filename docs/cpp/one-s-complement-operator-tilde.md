---
title: 'Jeden&#39;s vlastní operátor doplňku: ~ | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 79d34a4057ccbe5c10a6d22a14eed4317e62c464
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408635"
---
# <a name="one39s-complement-operator-"></a>Jeden&#39;s vlastní operátor doplňku: ~
## <a name="syntax"></a>Syntaxe  
  
```  
~ cast-expression  
```  
  
## <a name="remarks"></a>Poznámky  
 Jeden z operátorů doplňku (`~`), někdy nazývaný operátor „bitového doplňku“, vrací jedničkový bitový doplněk svého operandu. To znamená, že každý bit, který je 1 v operandu, je 0 ve výsledku. A naopak, každý bit, který je 0 v operandu, je 1 ve výsledku. Operand operátoru jedničkového doplňku musí být celočíselného typu.  
  
## <a name="operator-keyword-for-"></a>Klíčové slovo pro operátor ~  
 **Compl** operátor je textový ekvivalent operátoru `~`. Existují dva způsoby přístupu k **compl** operátor ve svých programech: zahrnutím souboru hlaviček `iso646.h`, nebo kompilací s [/Za](../build/reference/za-ze-disable-language-extensions.md).  
  
## <a name="example"></a>Příklad  
  
```cpp 
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
  
 Celočíselné povýšení proběhne na celočíselných operandech a výsledný typ je typ, na který je operand povýšen. Zobrazit [standardní převody](standard-conversions.md) Další informace o tom, jak je povýšení provedeno.  
  
## <a name="see-also"></a>Viz také:  
 [Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)   
 [Integrované operátory C++, Priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Unární aritmetické operátory](../c-language/unary-arithmetic-operators.md)