---
title: "Deferenční operátor: * | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- '* operator'
- indirection operator
- operators [C++], indirection
- indirection operator [C++], syntax
ms.assetid: c50309e1-6c02-4184-9fcb-2e13c1f4ac03
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 271708c8908e6d213047283c431e03726946e059
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="indirection-operator-"></a>Deferenční operátor: *
## <a name="syntax"></a>Syntaxe  
  
```  
  
* cast-expression  
```  
  
## <a name="remarks"></a>Poznámky  
 Deferenční operátor unární (**\***) dereferences ukazatel; to znamená, převede hodnotu ukazatel na hodnotu l. Operand operátoru indirection musí být ukazatel typu. Výsledkem výrazu indirection je typ, ze kterého je odvozený typ ukazatele. Použití  **\***  operátor v tomto kontextu se liší od jeho význam jako binární operátor, který je násobení.  
  
 Ukazuje-li operand na funkci, je výsledkem označení funkce. Ukazuje-li na umístění úložiště, je výsledkem l-hodnota označující umístění úložiště.  
  
 Deferenční operátor lze kumulativně dereference ukazatele na ukazatele. Příklad:  
  
```  
// expre_Indirection_Operator.cpp  
// compile with: /EHsc  
// Demonstrate indirection operator  
#include <iostream>  
using namespace std;  
int main() {  
   int n = 5;  
   int *pn = &n;  
   int **ppn = &pn;  
  
   cout  << "Value of n:\n"  
         << "direct value: " << n << endl  
         << "indirect value: " << *pn << endl  
         << "doubly indirect value: " << **ppn << endl  
         << "address of n: " << pn << endl  
         << "address of n via indirection: " << *ppn << endl;  
}  
```  
  
 Pokud je hodnota ukazatele je neplatná, výsledkem nedefinovaný. Následující seznam zahrnuje některé z nejběžnějších situací, které zneplatňují hodnotu ukazatele.  
  
-   Ukazatel je nulový.  
  
-   Ukazatel určuje adresu místní položky, která není v době reference viditelná.  
  
-   Ukazatel určuje adresu, která je pro typ objektu, na který ukazatel ukazuje, nesprávně zarovnána.  
  
-   Ukazatel určuje adresu, která není používána spuštěným programem.  
  
## <a name="see-also"></a>Viz také  
 [Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)   
 [Předdefinované C++ operátory, prioritu a Asociativnost](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Adresa operátoru: &](../cpp/address-of-operator-amp.md)   
 [Deferenční operátory a operátory adresy](../c-language/indirection-and-address-of-operators.md)