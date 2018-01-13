---
title: "Operátory sčítání: + a - | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- +
- '-'
dev_langs: C++
helpviewer_keywords:
- operators [C++], addition
- subtraction operator [C++], additive operators
- + operator [C++], additive operators
- additive operators [C++]
- arithmetic operators [C++], additive operators
- '- operator [C++], additive operators in C++'
ms.assetid: d4afafe7-e201-4c69-a649-37f17756e784
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8d316505939b22149b53a1012113a7aba88e2dcc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="additive-operators--and--"></a>Operátory sčítání: + a -
## <a name="syntax"></a>Syntaxe  
  
```  
expression + expression   
expression - expression  
```  
  
## <a name="remarks"></a>Poznámky  
 Mezi aditivní operátory patří:  
  
-   Přidání (**+**)  
  
-   Odčítání (**-**)  
  
 Tyto binární operátory mají asociativitu zleva doprava.  
  
 Aditivní operátory přebírají operandy aritmetických typů nebo typů ukazatele. Výsledkem přidání (**+**) operátor je součet hodnot operandy. Výsledkem odčítání (**-**) operátor je rozdíl mezi operandy. Jsou-li jeden nebo oba operandy ukazateli, musí být ukazateli na objekt, nikoli na funkce. Jsou-li oba operandy ukazateli, nedávají výsledky smysl, pokud nebudou oba operandy ukazateli na objekty stejného pole.  
  
 Operátory sčítání trvat operandy *aritmetické*, *integrální*, a *skalární* typy. Ty jsou definovány v následující tabulce.  
  
### <a name="types-used-with-additive-operators"></a>Typy použité spolu s aditivními operátory  
  
|Typ|Význam|  
|----------|-------------|  
|*aritmetické operace*|Celočíselné typy a typy s plovoucí desetinnou čárkou se společně nazývají „aritmetické“ typy.|  
|*integrální*|Typy char a int všech velikostí (long, short) a výčty jsou „celočíselné“ typy.|  
|*Skalární*|Skalární operandy jsou operandy aritmetického typu nebo typu ukazatele.|  
  
 Platnými kombinacemi pro tyto operátory jsou:  
  
 *aritmetické* + *aritmetické*  
  
 *Skalární* + *integrální*  
  
 *integrální* + *skalární*  
  
 *aritmetické* - *aritmetické*  
  
 *Skalární* - *skalární*  
  
 Všimněte si, že sčítání a odčítání nejsou ekvivalentními operacemi.  
  
 Pokud jsou oba operandy aritmetické typu, převody zahrnutých v [standardní převody](standard-conversions.md) se použijí pro operandy, a výsledkem je převedený typu.  
  
## <a name="example"></a>Příklad  
  
```  
// expre_Additive_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
#define SIZE 5  
using namespace std;  
int main() {  
   int i = 5, j = 10;  
   int n[SIZE] = { 0, 1, 2, 3, 4 };  
   cout  << "5 + 10 = " << i + j << endl  
         << "5 - 10 = " << i - j << endl;  
  
   // use pointer arithmetic on array  
  
   cout << "n[3] = " << *( n + 3 ) << endl;  
}  
```  
  
## <a name="pointer-addition"></a>Přidání ukazatele  
 Pokud je jeden z operandů při operaci sčítání ukazatelem na pole objektů, ostatní musí být celočíselného typu. Výsledkem je ukazatel, který je stejného typu jako původní ukazatel a odkazuje na jiný prvek pole. Tento koncept dokládá následující příklad části kódu:  
  
```  
short IntArray[10]; // Objects of type short occupy 2 bytes  
short *pIntArray = IntArray;  
  
for( int i = 0; i < 10; ++i )  
{  
    *pIntArray = i;  
    cout << *pIntArray << "\n";  
    pIntArray = pIntArray + 1;  
}  
```  
  
 Přestože je celočíselná hodnota 1 přičtena k ukazateli `pIntArray`, neznamená to „přičíst 1 k adrese“, spíše znamená „nastavit ukazatel na další objekt v poli“, který je 2 bajty (nebo `sizeof( int )`) daleko.  
  
> [!NOTE]
>  Kód ve tvaru `pIntArray = pIntArray + 1` se v programech jazyka C++ nachází jen zřídka. K provedení zvýšení jsou vhodnější tvary `pIntArray++` nebo `pIntArray += 1`.  
  
## <a name="pointer-subtraction"></a>Odečtení ukazatele  
 Jsou-li oba operandy ukazateli, výsledek odčítání je rozdíl (v prvcích pole) mezi operandy. Výsledkem výrazu odčítání je celočíselná hodnota se znaménkem typu ptrdiff_t (definovaného ve standardním vloženém souboru STDDEF.H).  
  
 Jeden z operandů může být celočíselného typu, pokud jde o druhý operand. Výsledek odčítání je stejného typu jako původní ukazatel. Operátor odečítání hodnotu ukazatel (*n* - *i*) element TD pole, kde  *n*  je element na kterou odkazuje původní ukazatele a *i* je integrální hodnota Druhý operand.  
  
## <a name="see-also"></a>Viz také  
 [Výrazy s binárními operátory](../cpp/expressions-with-binary-operators.md)   
 [Předdefinované C++ operátory, prioritu a Asociativnost](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Sčítací operátory jazyka C](../c-language/c-additive-operators.md)
