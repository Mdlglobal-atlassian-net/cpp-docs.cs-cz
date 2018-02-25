---
title: "ostream_iterator – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- iterator/std::ostream_iterator
- iterator/std::ostream_iterator::char_type
- iterator/std::ostream_iterator::ostream_type
- iterator/std::ostream_iterator::traits_type
dev_langs:
- C++
helpviewer_keywords:
- std::ostream_iterator [C++]
- std::ostream_iterator [C++], char_type
- std::ostream_iterator [C++], ostream_type
- std::ostream_iterator [C++], traits_type
ms.assetid: 24d842d3-9f45-4bf6-a697-62f5968f5a03
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c857ef1dc58bf1494e340382fbb56081374eaaab
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ostreamiterator-class"></a>ostream_iterator – třída
Ostream_iterator – třída šablony popisuje objekt iterator výstup, který zapíše do výstupního datového proudu s extrahování následných elementy **operátor <<**.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Type class CharType = char class Traits = char_traits <CharType>>  
class ostream_iterator
```  
  
#### <a name="parameters"></a>Parametry  
 Typ  
 Typ objektu, který má být vložen do výstupního toku.  
  
 `CharType`  
 Typ, který představuje typ znaku pro `ostream_iterator`. Tento argument je volitelný a výchozí hodnota je `char`.  
  
 `Traits`  
 Typ, který představuje typ znaku pro `ostream_iterator`. Tento argument je volitelný a výchozí hodnota je `char_traits` \< *CharType >.*  
  
 Třída ostream_iterator musí splňovat požadavky na výstupní iterátor. Algoritmy lze zapisovat přímo do výstupní datové proudy pomocí `ostream_iterator`.  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[ostream_iterator](#ostream_iterator)|Vytvoří `ostream_iterator` tedy inicializovaného a oddělovači k zápisu do výstupního datového proudu.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type](#char_type)|Typ, který poskytuje pro typ znak `ostream_iterator`.|  
|[ostream_type](#ostream_type)|Typ, který poskytuje pro typ datového proudu `ostream_iterator`.|  
|[traits_type](#traits_type)|Typ, který poskytuje pro typ vlastnosti znak `ostream_iterator`.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operátor *](#op_star)|Při přesměrování operátor použít k implementaci výraz iterator výstup * `i`  =  `x`.|  
|[operator++](#op_add_add)|Operátor přírůstku funkční, který vrátí `ostream_iterator` ke stejnému objektu řešit předtím, než byla volána operace.|  
|[operator=](#op_eq)|Operátor přiřazení použít k implementaci výraz iterator výstup * `i`  =  `x` k zápisu do výstupního proudu.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<iterator >  
  
 **Namespace:** – std  
  
##  <a name="char_type"></a>  ostream_iterator::char_type  
 Typ, který poskytuje pro typ znak iteraci.  
  
```
typedef CharType char_type;
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony **CharType**.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// ostream_iterator_char_type.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   typedef ostream_iterator<int>::char_type CHT1;  
   typedef ostream_iterator<int>::traits_type CHTR1;  
  
   // ostream_iterator for stream cout  
   // with new line delimiter:  
    ostream_iterator<int, CHT1, CHTR1> intOut ( cout , "\n" );  
  
   // Standard iterator interface for writing  
   // elements to the output stream:  
   cout << "The integers written to the output stream\n"  
        << "by intOut are:" << endl;  
 *intOut = 10;  
 *intOut = 20;  
 *intOut = 30;  
}  
\* Output:   
The integers written to the output stream  
by intOut are:  
10  
20  
30  
*\  
```  
  
##  <a name="op_star"></a>  ostream_iterator::operator*  
 Při přesměrování operátor použít k implementaci výraz iterator výstup \* *ii* = *x*.  
  
```
ostream_iterator<Type, CharType, Traits>& operator*();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na `ostream_iterator`.  
  
### <a name="remarks"></a>Poznámky  
 Požadavky na výstup iterace, `ostream_iterator` musí splňovat vyžadovat pouze výraz \* *ii* = *t* platné a nevyjadřuje **operátor** nebo `operator=` samostatně. Vrátí operátor členů v této implementaci  **\*to**.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// ostream_iterator_op_deref.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // ostream_iterator for stream cout  
   // with new line delimiter  
   ostream_iterator<int> intOut ( cout , "\n" );  
  
   // Standard iterator interface for writing  
   // elements to the output stream  
   cout << "Elements written to output stream:" << endl;  
 *intOut = 10;  
   intOut++;      // No effect on iterator position  
 *intOut = 20;  
 *intOut = 30;  
}  
\* Output:   
Elements written to output stream:  
10  
20  
30  
*\  
```  
  
##  <a name="op_add_add"></a>  ostream_iterator::Operator ++  
 Operátor přírůstku funkční, který vrátí `ostream_iterator` ke stejnému objektu řešit předtím, než byla volána operace.  
  
```
ostream_iterator<Type, CharType, Traits>& operator++();
ostream_iterator<Type, CharType, Traits> operator++(int);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na `ostream_iterator`.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí tyto operátory členy obou  **\*to**.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// ostream_iterator_op_incr.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // ostream_iterator for stream cout  
   // with new line delimiter  
   ostream_iterator<int> intOut ( cout , "\n" );  
  
   // standard iterator interface for writing  
   // elements to the output stream  
   cout << "Elements written to output stream:" << endl;  
 *intOut = 10;  
   intOut++;      // No effect on iterator position  
 *intOut = 20;  
 *intOut = 30;  
}  
\* Output:   
Elements written to output stream:  
10  
20  
30  
*\  
```  
  
##  <a name="op_eq"></a>  ostream_iterator::operator=  
 Operátor přiřazení použít k implementaci výraz output_iterator * `i`  =  `x` k zápisu do výstupního proudu.  
  
```
ostream_iterator<Type, CharType, Traits>& operator=(const Type& val);
```  
  
### <a name="parameters"></a>Parametry  
 `val`  
 Hodnota typu objektu `Type` má být vložena do výstupního datového proudu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Operátor vložení `val` do výstupního datového proudu přidružená k objektu, za nímž následuje oddělovač zadaný v [ostream_iterator – konstruktor](#ostream_iterator) (pokud existuje) a vrátí odkaz na `ostream_iterator`.  
  
### <a name="remarks"></a>Poznámky  
 Požadavky na výstup iterace, `ostream_iterator` musí splňovat vyžadovat pouze výraz * `ii`  =  `t` platné a nevyjadřuje operátor nebo operátor = samostatně. Tento člen operátor vrátí `*this`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// ostream_iterator_op_assign.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // ostream_iterator for stream cout  
   // with new line delimiter  
   ostream_iterator<int> intOut ( cout , "\n" );  
  
   // Standard iterator interface for writing  
   // elements to the output stream  
   cout << "Elements written to output stream:" << endl;  
 *intOut = 10;  
   intOut++;      // No effect on iterator position  
 *intOut = 20;  
 *intOut = 30;  
}  
\* Output:   
Elements written to output stream:  
10  
20  
30  
*\  
```  
  
##  <a name="ostream_iterator"></a>  ostream_iterator::ostream_iterator  
 Vytvoří `ostream_iterator` tedy inicializovaného a oddělovači k zápisu do výstupního datového proudu.  
  
```
ostream_iterator(
    ostream_type& _Ostr);

ostream_iterator(
    ostream_type& _Ostr,
    const CharType* _Delimiter);
```  
  
### <a name="parameters"></a>Parametry  
 `_Ostr`  
 Výstupní datový proud typu [ostream_iterator::ostream_type](#ostream_type) k být vstupní přes.  
  
 `_Delimiter`  
 Oddělovač, který je vložen do výstupního datového proudu mezi hodnotami.  
  
### <a name="remarks"></a>Poznámky  
 První konstruktor inicializuje ukazatel výstupní datový proud s `&_Ostr`. Ukazatel řetězec oddělovač označí prázdný řetězec.  
  
 Druhý konstruktor inicializuje ukazatel výstupní datový proud s `&_Ostr` a ukazatel řetězec oddělovač pomocí `_Delimiter`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// ostream_iterator_ostream_iterator.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // ostream_iterator for stream cout  
   ostream_iterator<int> intOut ( cout , "\n" );  
 *intOut = 10;  
   intOut++;  
 *intOut = 20;  
   intOut++;  
  
   int i;  
   vector<int> vec;  
   for ( i = 1 ; i < 7 ; ++i )  
   {  
      vec.push_back (  i );  
   }  
  
   // Write elements to standard output stream  
   cout << "Elements output without delimiter: ";  
   copy ( vec.begin ( ), vec.end ( ),  
          ostream_iterator<int> ( cout ) );  
   cout << endl;  
  
   // Write elements with delimiter " : " to output stream  
   cout << "Elements output with delimiter: ";  
   copy ( vec.begin ( ), vec.end ( ),  
          ostream_iterator<int> ( cout, " : " ) );  
   cout << endl;  
}  
\* Output:   
10  
20  
Elements output without delimiter: 123456  
Elements output with delimiter: 1 : 2 : 3 : 4 : 5 : 6 :   
*\  
```  
  
##  <a name="ostream_type"></a>  ostream_iterator::ostream_type  
 Typ, který poskytuje pro typ datového proudu iteraci.  
  
```
typedef basic_ostream<CharType, Traits> ostream_type;
```  
  
### <a name="remarks"></a>Poznámky  
 Typ se jedná o synonymum [basic_ostream](../standard-library/basic-ostream-class.md)< `CharType`, `Traits`>, stream – třída iostream hierarchie, který definuje objekty, které lze použít pro zápis.  
  
### <a name="example"></a>Příklad  
  V tématu [ostream_iterator](#ostream_iterator) příklad toho, jak deklarace a používání `ostream_type`.  
  
##  <a name="traits_type"></a>  ostream_iterator::traits_type  
 Typ, který poskytuje pro typ vlastnosti znak iteraci.  
  
```
typedef Traits traits_type;
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony **vlastnosti**.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// ostream_iterator_traits_type.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // The following not OK, but are just the default values:  
   typedef ostream_iterator<int>::char_type CHT1;  
   typedef ostream_iterator<int>::traits_type CHTR1;  
  
   // ostream_iterator for stream cout  
   // with new line delimiter:  
    ostream_iterator<int, CHT1, CHTR1> intOut ( cout , "\n" );  
  
   // Standard iterator interface for writing  
   // elements to the output stream:  
   cout << "The integers written to output stream\n"  
        << "by intOut are:" << endl;  
 *intOut = 1;  
 *intOut = 10;  
 *intOut = 100;  
}  
\* Output:   
The integers written to output stream  
by intOut are:  
1  
10  
100  
*\  
```  
  
## <a name="see-also"></a>Viz také  
 [\<iterator>](../standard-library/iterator.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)



