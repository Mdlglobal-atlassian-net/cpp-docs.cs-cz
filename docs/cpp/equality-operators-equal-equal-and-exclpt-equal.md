---
title: "Operátory rovnosti: == a! = | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- not_eq
- '!='
- ==
dev_langs: C++
helpviewer_keywords:
- '!= operator'
- equality operator
- not equal to comparison operator
- equality operator [C++], syntax
- == operator
- not_eq operator
- equal to operator
ms.assetid: ba4e9659-2392-4fb4-be5a-910a2a6df45a
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a064ca4c4d490d89705ffa30deb4eb132002cd16
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="equality-operators--and-"></a>Operátory rovnosti: == a !=
## <a name="syntax"></a>Syntaxe  
  
```  
expression == expression  
expression != expression  
```  
  
## <a name="remarks"></a>Poznámky  
 Operátory rovnosti binární porovnání operandy striktní rovnosti nebo nerovnosti.  
  
 Operátory rovnosti rovno (`==`) a není rovno (`!=`), mít nižší prioritu než relační operátory, ale chovají podobně. Typ výsledku pro tyto operátory je `bool`.  
  
 Operátor je rovno (`==`) vrátí **true** (1) Pokud oba operandy mají stejnou hodnotu; jinak vrátí **false** (0). Operátor není rovno (`!=`) vrátí **true** Pokud operandy nemají stejnou hodnotu; jinak vrátí **false**.  
  
## <a name="operator-keyword-for-"></a>Operator – klíčové slovo pro! =  
 Operátor `not_eq` je textový ekvivalent operátoru `!=`. Existují dva způsoby pro přístup `not_eq` operátor v programy: zahrnout soubor hlaviček `iso646.h`, nebo kompilovat s [/Za](../build/reference/za-ze-disable-language-extensions.md) – možnost kompilátoru (zakázat jazyková rozšíření).  
  
## <a name="example"></a>Příklad  
  
```  
// expre_Equality_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
int main() {  
   cout  << boolalpha  
         << "The true expression 3 != 2 yields: "  
         << (3 != 2) << endl  
         << "The false expression 20 == 10 yields: "  
         << (20 == 10) << endl;  
}  
```  
  
 Operátory rovnosti můžete porovnat ukazatelé na členy stejného typu. Porovnání jsou prováděny převody ukazatele na člena. Ukazatelé na členy můžete také porovnání s konstantní výraz, jehož výsledkem je 0.  
  
## <a name="see-also"></a>Viz také  
 [Výrazy s binárními operátory](../cpp/expressions-with-binary-operators.md)   
 [Předdefinované C++ operátory, prioritu a Asociativnost](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C relační operátory a operátory rovnosti](../c-language/c-relational-and-equality-operators.md)