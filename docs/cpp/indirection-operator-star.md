---
title: 'Deferenční operátor: * | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- '* operator'
- indirection operator
- operators [C++], indirection
- indirection operator [C++], syntax
ms.assetid: c50309e1-6c02-4184-9fcb-2e13c1f4ac03
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a23951697a5f736305734c6d49044a2e33ac4783
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200490"
---
# <a name="indirection-operator-"></a>Deferenční operátor: *
## <a name="syntax"></a>Syntaxe  
  
```  
* cast-expression  
```  
  
## <a name="remarks"></a>Poznámky  
 Operátor unární dereference (<strong>\*</strong>) přistoupí přes ukazatel; to znamená, převede hodnotu ukazatele na l hodnotou. Operand operátoru dereference musí být ukazatel na typ. Výsledek výrazu dereference je typ, ze kterého je odvozen typ ukazatele. Použití <strong>\*</strong> operátor v tomto kontextu se liší od jeho význam jako binární operátor, který je násobení.  
  
 Ukazuje-li operand na funkci, je výsledkem označení funkce. Ukazuje-li na umístění úložiště, je výsledkem l-hodnota označující umístění úložiště.  
  
 Operátor dereference lze kumulativně dereference ukazatele na ukazatele. Příklad:  
  
```cpp 
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
  
 Pokud je hodnota ukazatele neplatná, výsledek není definován. Následující seznam zahrnuje některé z nejběžnějších situací, které zneplatňují hodnotu ukazatele.  
  
-   Ukazatel je nulový.  
  
-   Ukazatel určuje adresu místní položky, která není v době reference viditelná.  
  
-   Ukazatel určuje adresu, která je pro typ objektu, na který ukazatel ukazuje, nesprávně zarovnána.  
  
-   Ukazatel určuje adresu, která není používána spuštěným programem.  
  
## <a name="see-also"></a>Viz také:  
 [Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)   
 [Integrované operátory C++, Priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operátor address-of: &](../cpp/address-of-operator-amp.md)   
 [Dereferenční operátory a operátory adresy](../c-language/indirection-and-address-of-operators.md)