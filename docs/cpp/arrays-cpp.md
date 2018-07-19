---
title: Pole (C++) | Dokumentace Microsoftu
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
ms.openlocfilehash: 60c7baaaf20158c29c34aea364e70c0d040a42e3
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947613"
---
# <a name="arrays-c"></a>Pole (C++)
Pole je kolekce podobných objektů. Nejjednodušší případ pole je vektor, který může být deklarován následující sekvencí:  
  
```  
  
decl-specifier identifier [ constant-expression ]  
decl-specifier identifier []  
decl-specifier identifer [][ constant-expression] . . .  
decl-specifier identifier [ constant-expression ]  
[ constant-expression ] . . .  
```  
  
 1. Specifikátor deklarace:  
  
-   Volitelný specifikátor paměťové třídy.  
  
-   Volitelné **const** a/nebo **volatile** specifikátorů.  
  
-   Název typu prvků pole.  
  
 2. Deklarátor:  
  
-   Identifikátor.  
  
-   Konstantní výraz integrálního typu uzavřený v závorkách, **[]**. Pokud více dimenzí jsou deklarovány pomocí dalších závorky, můžete na první sadu závorek vynechat konstantní výraz.  
  
-   Volitelně přidejte hranaté závorky ohraničující konstantní výrazy.  
  
 3. Volitelný inicializátor.  Zobrazit [inicializátory](../cpp/initializers.md).  
  
 Počet prvků v poli je dán konstantní výraz. První prvek v poli je 0. prvkem a poslední prvek je (*n*-1) elementu, kde *n* je počet elementů pole může obsahovat. *Konstantní výraz* musí být integrálního typu a musí být větší než 0. Pole s nulovou velikostí je platný jenom v případě pole je posledním polem **struktura** nebo **sjednocení** a když jsou povolena rozšíření společnosti Microsoft (/Ze).  
  
 Následující příklad ukazuje, jak definovat pole za běhu:  
  
```cpp 
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
  
 Pole jsou odvozené typy a lze je tedy sestavit z jiného odvozeného nebo základního typu kromě funkcí, odkazů, a **void**.  
  
 Pole vyrobena z jiných polí, jsou vícerozměrná pole. Tato vícedimenzová pole jsou určena umístěním více konstantní výrazy v závorkách v sekvenci. Zvažte například tuto deklaraci:  
  
```cpp 
int i2[5][7];  
```  
  
 Určuje pole typu **int**koncepčně uspořádané v dvojrozměrné matici po pěti řádcích a sedmi sloupcích, jak je znázorněno na následujícím obrázku:  
  
 ![Rámcové rozložení vícenásobné&#45;jednorozměrné pole](../cpp/media/vc38rc1.gif "vc38RC1")  
Rámcové rozložení vícerozměrného pole  
  
 V deklaracích vícerozměrných polí, která mají seznam inicializátorů (jak je popsáno v [inicializátory](../cpp/initializers.md)), konstantní výraz, který určuje hranice pro první dimenzi lze vynechat. Příklad:  
  
```cpp 
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
  
 Předchozí prohlášení definuje pole, které má tři řádky a čtyři sloupce. Řádky představují továrny a sloupce představují trhy, na které továrny dodávají. Hodnoty jsou náklady na dopravu z továren na trhy. První dimenze pole je vynechána, ale kompilátor ji doplní porovnáním inicializátoru.  
  
 Témata v této části:  
  
-   [Používání polí](../cpp/using-arrays-cpp.md)  
  
-   [Pole ve výrazech](../cpp/arrays-in-expressions.md)  
  
-   [Interpretace operátoru podskriptu](../cpp/interpretation-of-subscript-operator.md)  
  
-   [Indirekce u typů polí](../cpp/indirection-on-array-types.md)  
  
-   [Pořadí polí jazyka C++](../cpp/ordering-of-cpp-arrays.md)  
  
## <a name="example"></a>Příklad  
 Metodu vynechání specifikace hranice pro první dimenzi vícerozměrného pole lze také v deklaracích funkcí následujícím způsobem:  
  
```cpp 
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
 Funkce `FindMinToMkt` je zapsán tak, že přidání nové továrny nevyžaduje změnu kódu, stačí provést rekompilaci.  
  
## <a name="see-also"></a>Viz také  
 