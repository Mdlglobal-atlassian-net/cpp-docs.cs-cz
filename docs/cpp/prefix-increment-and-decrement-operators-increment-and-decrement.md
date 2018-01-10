---
title: "Operátory přírůstku a snížení předpony: ++ a--| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- --
- ++
dev_langs: C++
helpviewer_keywords:
- increment operators [C++], syntax
- ++ operator [C++], prefix increment operators
- operators [C++], decrement
- -- operator [C++], prefix decrement operators [C++]
- operators [C++], increment
- decrement operators [C++], syntax
- decrement operators [C++]
ms.assetid: 45ea7fc7-f279-4be9-a216-1d9a0ef9eb7b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ff153c462361e8b6bac8f3c10192025352da650f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="prefix-increment-and-decrement-operators--and---"></a>Operátory přírůstku a snížení předpony: ++ a --
## <a name="syntax"></a>Syntaxe  
  
```  
++ unary-expression  
-- unary-expression  
```  
  
## <a name="remarks"></a>Poznámky  
 Operátor přírůstku předpony (`++`) přičítá jeho operand; tato zvýšena hodnota je výsledkem výrazu. Operand musí být hodnota l není typu **const**. Výsledkem je hodnota l stejného typu jako operand.  
  
 Operátor snížení předpony (**--**) je podobná operátor přírůstku předponu, s tím rozdílem, že se odečte jedním operand a výsledkem je tato hodnota odečte.  

 **Visual Studio 2017 verze 15.3 a novější** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): operand operátoru přírůstek nebo snížení nesmí být typu `bool`.
  
 Jak předponu a operátory přírůstku a snížení operátory ovlivnit operandy. Klíčovým rozdílem mezi nimi je pořadí, ve kterém přírůstek nebo snížení probíhá vyhodnocení výrazu. (Další informace najdete v tématu [operátory přípony přírůstku a snížení](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md).) Ve formuláři, předpony přírůstek nebo snížení probíhá před hodnota je použita ve vyhodnocení výrazu, tak hodnota výrazu se liší od hodnoty operand. Ve formuláři, operátory přírůstek nebo snížení probíhá po hodnota se používá při vyhodnocení výrazu, tak hodnota výrazu je stejná jako hodnota operandu. Například následující programu výtisků "`++i = 6`":  
  
```  
// expre_Increment_and_Decrement_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
int main() {  
   int i = 5;  
   cout << "++i = " << ++i << endl;  
}  
```  
  
 Operand typu integrální nebo plovoucí je zvýšena nebo snížena na celé číslo 1. Typ výsledku je stejný jako typ operandu. Operand typu ukazatele je zvýšena nebo snížena velikost objektu, který ho adresy. Body zvýšena ukazatele na další objekt; odečte ukazatel odkazuje na objekt předchozí.  
  
 Protože operátory přírůstku a snížení mít vedlejší účinky, pomocí výrazů s operátory zvýšení nebo snížení hodnoty v [makro preprocesoru](../preprocessor/macros-c-cpp.md) může mít nežádoucí výsledky. Vezměte v úvahu v tomto příkladu:  
  
```  
// expre_Increment_and_Decrement_Operators2.cpp  
#define max(a,b) ((a)<(b))?(b):(a)  
  
int main()  
{  
   int i = 0, j = 0, k;  
   k = max( ++i, j );  
}  
```  
  
 Makro zasahuje do:  
  
```  
k = ((++i)<(j))?(j):(++i);  
```  
  
 Pokud `i` je větší než nebo rovno `j` nebo menší než `j` o 1, se se zvýší dvakrát.  
  
> [!NOTE]
>  Vložených funkcí jazyka C++ jsou vhodnější makra v mnoha případech, protože se vyhnete vedlejší účinky, jako jsou zde popsané a povolit jazyk, který chcete provést podrobnější kontrola typu.  
  
## <a name="see-also"></a>Viz také  
 [Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)   
 [Předdefinované C++ operátory, prioritu a Asociativnost](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operátory inkrementace a dekrementace předpony](../c-language/prefix-increment-and-decrement-operators.md)