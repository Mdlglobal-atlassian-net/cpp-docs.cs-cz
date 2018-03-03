---
title: "Multiplikativní operátory a operátor numerického zbytku | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '%'
- /
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], multiplicative
- arithmetic operators [C++], multiplicative operators
- modulus operator [C++]
- '* operator'
- division operator [C++], multiplicative operators
- '% operator'
- multiplication operator [C++], multiplicative operators
- multiplicative operators [C++]
- division operator
ms.assetid: b53ea5da-d0b4-40dc-98f3-0aa52d548293
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bb6ad2396b47932f05d9404485e4b32a7e92363b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="multiplicative-operators-and-the-modulus-operator"></a>Multiplikativní operátory a operátor numerického zbytku
## <a name="syntax"></a>Syntaxe  
  
```  
expression * expression   
expression / expression   
expression % expression  
```  
  
## <a name="remarks"></a>Poznámky  
 Operátory násobení jsou:  
  
-   Násobení (**\***)  
  
-   Dělení (**/**)  
  
-   Numerického zbytku (zbytek po dělení) (`%`)  
  
 Tyto binární operátory mají asociativitu zleva doprava.  
  
 Operátory násobení vezmou operandy aritmetických typů. Operátor numerického zbytku (`%`), které se přísnější v, že jejími operandy, musí být celočíselné typu. (Získat zbytku s plovoucí desetinnou čárkou dělení, použijte funkci běhu [fmod](../c-runtime-library/reference/fmod-fmodf.md).) Převody zahrnutých v [standardní převody](standard-conversions.md) se použijí pro operandy, a výsledkem je převedený typu.  
  
 Operátor násobení dává výsledek vynásobení prvního operandu druhým.  
  
 Operátor dělení dává výsledek vydělení prvního operandu druhým.  
  
 Operátor numerického zbytku vypočítá zbytek poskytují následující výraz, kde *e1* je první operand a *e2* je druhý: *e1* -(*e1*  /  *e2*) \* *e2*, kde jsou oba operandy celočíselných typů.  
  
 Dělení nulou ve výrazu dělení nebo zbytku není definováno a způsobí chybu modulu run-time. Následující výrazy proto způsobí nedefinované chybné výsledky:  
  
```  
i % 0  
f / 0.0  
```  
  
 Pokud jsou oba operandy na výraz násobení, dělení, nebo zbytku mají stejné znaménko, výsledek je kladný. Jinak je výsledek záporný. Výsledek znaménka operace modulus je definován implementací.  
  
> [!NOTE]
>  Vzhledem k tomu, že převody prováděné operátory násobení nepočítají s podmínkami přetečení nebo podtečení, informace se mohou ztratit, pokud výsledek operace násobení nelze reprezentovat v typu operandu po převodu.  
  
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 V programu Microsoft C++ výsledek výrazu zbytku je vždy stejný jako znaménko prvního operandu.  
  
**Konkrétní Microsoft END**  
 Pokud je vypočítané dělení dvou celých čísel nepřesné a pouze jeden operand je záporný, výsledkem je největší celé číslo (v rozsahu bez ohledu na znaménko) menší než přesná hodnota, kterou by byla výsledkem operace dělení. Například vypočtená hodnota vlastnosti -11 / 3 je-3.666666666. Výsledek tohoto celočíselné dělení je -3.  
  
 Vztah mezi multiplikativní operátory je dán identity (*e1* / *e2*) \* *e2*  +  *e1* % *e2* == *e1*.  
  
## <a name="example"></a>Příklad  
 Následující program ukazuje operátory násobení. Všimněte si, že buď operand `10 / 3` musí být explicitně přetypovat na typ `float` předejdete zkrácení tak, že jsou oba operandy typu `float` před dělení.  
  
```  
// expre_Multiplicative_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
int main() {  
   int x = 3, y = 6, z = 10;  
   cout  << "3 * 6 is " << x * y << endl  
         << "6 / 3 is " << y / x << endl  
         << "10 % 3 is " << z % x << endl  
         << "10 / 3 is " << (float) z / x << endl;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Výrazy s binárními operátory](../cpp/expressions-with-binary-operators.md)   
 [Předdefinované C++ operátory, prioritu a Asociativnost](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Multiplikativní operátory jazyka C](../c-language/c-multiplicative-operators.md)