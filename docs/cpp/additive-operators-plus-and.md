---
title: 'Operátory sčítání: + a - | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- +
- '-'
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], addition
- subtraction operator [C++], additive operators
- + operator [C++], additive operators
- additive operators [C++]
- arithmetic operators [C++], additive operators
- '- operator [C++], additive operators in C++'
ms.assetid: d4afafe7-e201-4c69-a649-37f17756e784
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89fc0f122f0859e6fc891ddfccd4bc99e7034bfe
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947719"
---
# <a name="additive-operators--and--"></a>Operátory sčítání: + a -
## <a name="syntax"></a>Syntaxe  
  
```  
expression + expression   
expression - expression  
```  
  
## <a name="remarks"></a>Poznámky  
 Mezi aditivní operátory patří:  
  
-   Sčítání (**+**)  
  
-   Odčítání (**-**)  
  
 Tyto binární operátory mají asociativitu zleva doprava.  
  
 Aditivní operátory přebírají operandy aritmetických typů nebo typů ukazatele. Výsledek součtu (**+**) operátor je součet operandů. Výsledek odčítání (**-**) – operátor je rozdíl mezi operandy. Jsou-li jeden nebo oba operandy ukazateli, musí být ukazateli na objekt, nikoli na funkce. Jsou-li oba operandy ukazateli, nedávají výsledky smysl, pokud nebudou oba operandy ukazateli na objekty stejného pole.  
  
 Aditivní operátory přebírají operandy *aritmetické*, *integrální*, a *skalární* typy. Ty jsou definovány v následující tabulce.  
  
### <a name="types-used-with-additive-operators"></a>Typy použité spolu s aditivními operátory  
  
|Typ|Význam|  
|----------|-------------|  
|*Aritmetické operace*|Celočíselné typy a typy s plovoucí desetinnou čárkou se společně nazývají „aritmetické“ typy.|  
|*Celočíselný typ*|Typy char a int všech velikostí (long, short) a výčty jsou „celočíselné“ typy.|  
|*scalar*|Skalární operandy jsou operandy aritmetického typu nebo typu ukazatele.|  
  
 Platnými kombinacemi pro tyto operátory jsou:  
  
 *aritmetické* + *aritmetické*  
  
 *scalar* + *integral*  
  
 *integrální* + *skalární*  
  
 *aritmetické* - *aritmetické*  
  
 *Skalární* - *skalární*  
  
 Všimněte si, že sčítání a odčítání nejsou ekvivalentními operacemi.  
  
 Pokud jsou oba operandy aritmetického typu, převody uvedené v [standardní převody](standard-conversions.md) jsou použity na operandy a výsledek je určen převedeným typem.  
  
## <a name="example"></a>Příklad  
  
```cpp 
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
  
```cpp 
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
 Jsou-li oba operandy ukazateli, výsledek odčítání je rozdíl (v prvcích pole) mezi operandy. Výraz odčítání poskytuje podepsaných integrálních výsledek typu **ptrdiff_t** (definované ve standardním vloženém souboru \<stddef.h >).  
  
 Jeden z operandů může být celočíselného typu, pokud jde o druhý operand. Výsledek odčítání je stejného typu jako původní ukazatel. Hodnota odčítání je ukazatel (*n* - *můžu*) tý prvek pole, ve kterém *n* elementu ukazuje původní ukazatel a *můžu* je celočíselná hodnota druhého operandu.  
  
## <a name="see-also"></a>Viz také  
 [Výrazy s binárními operátory](../cpp/expressions-with-binary-operators.md)   
 [Integrované operátory C++, Priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Sčítací operátory jazyka C](../c-language/c-additive-operators.md)
