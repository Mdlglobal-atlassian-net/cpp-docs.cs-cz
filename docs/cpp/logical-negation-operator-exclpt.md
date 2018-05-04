---
title: 'Logický operátor negace: ! | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- '!'
- Not
dev_langs:
- C++
helpviewer_keywords:
- '! operator'
- NOT operator
- logical negation
ms.assetid: 650add9f-a7bc-426c-b01d-5fc6a81c8b62
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b64e9887e51666405d3c6c106b40c99528ea4510
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="logical-negation-operator-"></a>Logický operátor negace: !
## <a name="syntax"></a>Syntaxe  
  
```  
  
! cast-expression  
```  
  
## <a name="remarks"></a>Poznámky  
 Logický operátor negace (**!**) obrátí význam jeho operand. Operand musí být aritmetického typu nebo typu ukazatele (nebo výraz, jehož výsledkem je aritmetický typ nebo typ ukazatele). Operand je implicitně převeden na typ `bool`. Výsledkem je **true** pokud převedený operand **false**; výsledkem je **false** pokud převedený operand **true**. Výsledek je typu `bool`.  
  
 Pro výraz *e*, unární výraz **! *** e* je ekvivalentní výrazu **(*** e* `==` 0), s výjimkou případů, které se účastní přetížené operátory.  
  
## <a name="operator-keyword-for-"></a>Klíčové slovo pro operátor !  
 **Není** operátor je ekvivalentem text **!**. Existují dva způsoby pro přístup **není** operátor v programy: zahrnout soubor hlaviček `iso646.h`, nebo kompilovat s [/Za](../build/reference/za-ze-disable-language-extensions.md) – možnost kompilátoru (zakázat jazyková rozšíření).  
  
## <a name="example"></a>Příklad  
  
```  
// expre_Logical_NOT_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main() {  
   int i = 0;  
   if (!i)  
      cout << "i is zero" << endl;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)   
 [Předdefinované C++ operátory, prioritu a Asociativnost](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Unární aritmetické operátory](../c-language/unary-arithmetic-operators.md)