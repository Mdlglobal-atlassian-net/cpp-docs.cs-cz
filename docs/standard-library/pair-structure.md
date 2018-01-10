---
title: "Pair – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: utility/std::pair
dev_langs: C++
helpviewer_keywords: pair class
ms.assetid: 539d3d67-80a2-4170-b347-783495d42109
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 95da7f8ab71b6336f8baf2441ca210db42110390
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="pair-structure"></a>pair – struktura
Struktura, která poskytuje pro možnost dva objekty považovat za jeden objekt.  
  
## <a name="syntax"></a>Syntaxe  
```  
struct pair
{
    typedef T1 first_type;
    typedef T2 second_type;
    T1 first;
    T2 second;
    constexpr pair();
    constexpr pair(
        const T1& Val1,
        const T2& Val2);

    template <class Other1, class Other2>
    constexpr pair(const pair<Other1, Other2>& Right);

    template <class Other1, class Other2>
    constexpr pair(const pair <Other1 Val1, Other2 Val2>&& Right);

    template <class Other1, class Other2>
    constexpr pair(Other1&& Val1, Other2&& Val2);
};
```  
#### <a name="parameters"></a>Parametry  
 `Val1`  
 Hodnota inicializace první prvek `pair`.  
  
 `Val2`  
 Hodnota inicializace druhého prvku `pair`.  
  
 `Right`  
 Pár, jejichž hodnoty se mají být použita k chybě při inicializaci elementy jinou dvojici.  
  
## <a name="return-value"></a>Návratová hodnota  
 První (výchozí) konstruktor inicializuje první prvek, které odpovídá páru na výchozí hodnoty typu **T1** a druhý prvkem na výchozí typ **T2**.  
  
 Druhý konstruktor inicializuje první prvek, které odpovídá páru k `Val1` a druhý k *hodnota2.*  
  
 Třetí (šablony) konstruktor inicializuje první prvek, které odpovídá páru k `Right`. **první** a druhý k `Right`. **druhý**.  
  
 Čtvrtý konstruktor inicializuje první prvek, které odpovídá páru k `Val1` a druhý k *hodnota2* pomocí [Rvalue – deklarátor odkazu: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
## <a name="remarks"></a>Poznámky  
 Struktura šablony ukládá pár objekty typu **T1** a **T2**, v uvedeném pořadí. Typ **first_type –** je stejný jako parametr šablony **T1** a typ **second_type –** je stejný jako parametr šablony **T2** . **T1** a **T2** každý musí zadat jenom výchozí konstruktor, konstruktor jeden argument a destruktor. Všechny členy typu `pair` nejsou veřejné, protože typ je deklarován jako `struct` spíš než jako **třída**. Jsou dvě nejběžnější používá pro pár jako návratové typy pro funkce, které vrací dvě hodnoty a jako elementy pro třídy asociativní kontejneru [map – třída](../standard-library/map-class.md) a [multimap – třída](../standard-library/multimap-class.md) mají oba klíče a Typ hodnoty přidružené k každý prvek. Splňuje požadavky pro kontejner asociativní pár a má typ hodnoty ve formátu `pair` <  **const**`key_type`, `mapped_type`>.  
  
## <a name="example"></a>Příklad  
  
```cpp  
// utility_pair.cpp  
// compile with: /EHsc  
#include <utility>  
#include <map>  
#include <iomanip>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // Using the constructor to declare and initialize a pair  
   pair <int, double> p1 ( 10, 1.1e-2 );  
  
   // Compare using the helper function to declare and initialize a pair  
   pair <int, double> p2;  
   p2 = make_pair ( 10, 2.22e-1 );  
  
   // Making a copy of a pair  
   pair <int, double> p3 ( p1 );  
  
   cout.precision ( 3 );  
   cout << "The pair p1 is: ( " << p1.first << ", "   
        << p1.second << " )." << endl;  
   cout << "The pair p2 is: ( " << p2.first << ", "   
        << p2.second << " )." << endl;  
   cout << "The pair p3 is: ( " << p3.first << ", "   
        << p3.second << " )." << endl;  
  
   // Using a pair for a map element  
   map <int, int> m1;  
   map <int, int>::iterator m1_Iter;  
  
   typedef pair <int, int> Map_Int_Pair;  
  
   m1.insert ( Map_Int_Pair ( 1, 10 ) );  
   m1.insert ( Map_Int_Pair ( 2, 20 ) );  
   m1.insert ( Map_Int_Pair ( 3, 30 ) );  
  
   cout << "The element pairs of the map m1 are:";  
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )  
      cout << " ( " << m1_Iter -> first << ", "  
           << m1_Iter -> second << " )";  
   cout   << "." << endl;  
  
   // Using pair as a return type for a function  
   pair< map<int,int>::iterator, bool > pr1, pr2;  
   pr1 = m1.insert ( Map_Int_Pair ( 4, 40 ) );  
   pr2 = m1.insert ( Map_Int_Pair (1, 10 ) );  
  
   if( pr1.second == true )  
   {  
      cout << "The element (4,40) was inserted successfully in m1."  
           << endl;  
   }  
   else     
   {  
      cout << "The element with a key value of\n"  
           << " ( (pr1.first) -> first ) = " << ( pr1.first ) -> first   
           << " is already in m1,\n so the insertion failed." << endl;  
   }  
  
   if( pr2.second == true )  
   {  
      cout << "The element (1,10) was inserted successfully in m1."  
           << endl;  
   }  
   else     
   {  
      cout << "The element with a key value of\n"  
           << " ( (pr2.first) -> first ) = " << ( pr2.first ) -> first   
           << " is already in m1,\n so the insertion failed." << endl;  
   }  
}  
\* Output:   
The pair p1 is: ( 10, 0.011 ).  
The pair p2 is: ( 10, 0.222 ).  
The pair p3 is: ( 10, 0.011 ).  
The element pairs of the map m1 are: ( 1, 10 ) ( 2, 20 ) ( 3, 30 ).  
The element (4,40) was inserted successfully in m1.  
The element with a key value of  
 ( (pr2.first) -> first ) = 1 is already in m1,  
 so the insertion failed.  
*\  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<nástroj >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



