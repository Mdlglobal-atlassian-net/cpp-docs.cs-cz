---
title: Pole (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declaring arrays [C++], about declaring arrays
- multidimensional arrays [C++]
- arrays [C++]
ms.assetid: 3f5986aa-485c-4ba4-9502-67e2ef924238
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0fe8e5f53d05ac159fd577b260268f297b59d146
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="arrays-c"></a>Pole (C++)
Pole je kolekce podobně jako objekty. Nejjednodušším případě pole je vektor, který může být deklarován v následujícím pořadí:  
  
```  
  
      decl-specifier identifier [ constant-expression ]  
decl-specifier identifier []  
decl-specifier identifer [][ constant-expression] . . .  
decl-specifier identifier [ constant-expression ]  
[ constant-expression ] . . .  
```  
  
 1. Specifikátor deklarace:  
  
-   Specifikátor třídy úložiště volitelné.  
  
-   Volitelné **const** nebo `volatile` specifikátory.  
  
-   Název typu elementy pole.  
  
 2. Deklarátor:  
  
-   Identifikátor.  
  
-   Konstantní výraz integrální typu v závorkách, **[].** Pokud více dimenzí jsou deklarováno s použitím dalších závorky, může být konstantní výraz vynechán na první sadu závorky.  
  
-   Volitelné další závorky nadřazených konstantní výrazy.  
  
 3. Inicializátoru volitelné.  V tématu [inicializátory](../cpp/initializers.md).  
  
 Počet prvků v poli je dána konstantní výraz. První prvek v poli je 0-té elementu a je posledním prvkem (*n*-1) elementu, kde *n* je počet elementů pole může obsahovat. *Konstantní výraz* musí být celočíselné typu a musí být větší než 0. Pole nulovou velikostí je povolen, pouze pokud je pole poslední pole v `struct` nebo **sjednocení** a pokud jsou povolené rozšíření Microsoft (/Ze).  
  
 Následující příklad ukazuje, jak definovat pole v době běhu:  
  
```  
// arrays.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main() {  
   using namespace std;  
   int size = 3, i = 0;  
  
   int* myarr = new int[size];  
  
   for (i = 0 ; i < size ; i++)  
      myarr[i] = 10;  
  
   for (i = 0 ; i < size ; i++)  
      printf_s("myarr[%d] = %d\n", i, myarr[i]);  
  
   delete [] myarr;  
}  
```  
  
 Pole jsou odvozené typy a konstruovat proto z jiných základní nebo odvozené typy s výjimkou funkcí, odkazy, a `void`.  
  
 Pole sestavený z jiných polí jsou vícerozměrná pole. Tyto vícerozměrná pole nejsou zadány tak, že více konstantní výrazy v závorkách pořadí. Představte si třeba tuto deklaraci:  
  
```  
int i2[5][7];  
```  
  
 Určuje pole typu `int`, koncepčně uspořádaných dvourozměrná matice pět řádků a sloupců sedm, jak je znázorněno na následujícím obrázku:  
  
 ![Koncepční rozložení více&#45;dimenzí pole](../cpp/media/vc38rc1.gif "vc38RC1")  
Koncepční rozložení multidimenzionálního pole  
  
 V deklaracích multidimensioned pole, které mají inicializátoru seznamu (jak je popsáno v [inicializátory](../cpp/initializers.md)), můžete tento parametr vynechán konstantní výraz, který určuje rozsah pro první dimenzi. Příklad:  
  
```  
// arrays2.cpp  
// compile with: /c  
const int cMarkets = 4;  
// Declare a float that represents the transportation costs.  
double TransportCosts[][cMarkets] = {   
   { 32.19, 47.29, 31.99, 19.11 },  
   { 11.29, 22.49, 33.47, 17.29 },  
   { 41.97, 22.09,  9.76, 22.55 }  
};  
```  
  
 Předchozí deklaraci definuje pole, které je tři řádků a sloupců čtyři. Řádky představují objekty pro vytváření a sloupce, které představují trhy, na které se dodávají objekty pro vytváření. Hodnoty jsou náklady na Transport z objekty Factory trhů. První dimenze pole je vynechána, ale kompilátor vyplní ho tak, že prověří inicializátoru.  
  
 Témata v této části:  
  
-   [Používání polí](../cpp/using-arrays-cpp.md)  
  
-   [Pole ve výrazech](../cpp/arrays-in-expressions.md)  
  
-   [Interpretace operátoru podskriptu](../cpp/interpretation-of-subscript-operator.md)  
  
-   [Indirekce u typů polí](../cpp/indirection-on-array-types.md)  
  
-   [Pořadí polí jazyka C++](../cpp/ordering-of-cpp-arrays.md)  
  
## <a name="example"></a>Příklad  
 Postup vynechání specifikace hranice pro první dimenzi multidimenzionálního pole lze také v deklaracích funkce následujícím způsobem:  
  
```  
// multidimensional_arrays.cpp  
// compile with: /EHsc  
// arguments: 3  
#include <limits>   // Includes DBL_MAX  
#include <iostream>  
  
const int cMkts = 4, cFacts = 2;  
  
// Declare a float that represents the transportation costs  
double TransportCosts[][cMkts] = {   
   { 32.19, 47.29, 31.99, 19.11 },  
   { 11.29, 22.49, 33.47, 17.29 },  
   { 41.97, 22.09,  9.76, 22.55 }    
};  
  
// Calculate size of unspecified dimension  
const int cFactories = sizeof TransportCosts /  
                  sizeof( double[cMkts] );  
  
double FindMinToMkt( int Mkt, double myTransportCosts[][cMkts], int mycFacts);  
  
using namespace std;  
  
int main( int argc, char *argv[] ) {  
   double MinCost;  
  
   if (argv[1] == 0) {  
      cout << "You must specify the number of markets." << endl;  
      exit(0);  
   }  
   MinCost = FindMinToMkt( *argv[1] - '0', TransportCosts, cFacts);  
   cout << "The minimum cost to Market " << argv[1] << " is: "  
       << MinCost << "\n";  
}  
  
double FindMinToMkt(int Mkt, double myTransportCosts[][cMkts], int mycFacts) {  
   double MinCost = DBL_MAX;  
  
   for( int i = 0; i < cFacts; ++i )  
      MinCost = (MinCost < TransportCosts[i][Mkt]) ?  
         MinCost : TransportCosts[i][Mkt];  
  
   return MinCost;  
}  
```  
  
```Output  
The minimum cost to Market 3 is: 17.29  
```  
  
## <a name="comments"></a>Komentáře  
 Funkce `FindMinToMkt` je napsán tak, aby přidání nové objekty Factory nevyžaduje změny kódu právě opětovnou kompilaci.  
  
## <a name="see-also"></a>Viz také  
 