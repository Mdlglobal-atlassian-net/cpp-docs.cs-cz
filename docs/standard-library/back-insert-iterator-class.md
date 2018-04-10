---
title: back_insert_iterator – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- iterator/std::back_insert_iterator
- iterator/std::back_insert_iterator::container_type
- iterator/std::back_insert_iterator::reference
dev_langs:
- C++
helpviewer_keywords:
- std::back_insert_iterator [C++]
- std::back_insert_iterator [C++], container_type
- std::back_insert_iterator [C++], reference
ms.assetid: a1ee07f2-cf9f-46a1-8608-cfaf207f9713
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7646b26c1651ccf93fcc3bcb6828ae402ea5ca07
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/10/2018
---
# <a name="backinsertiterator-class"></a>back_insert_iterator – třída
Popisuje adaptér iterátoru, který splňuje požadavky výstupního iterátoru. Vloží, spíše než přepíše, prvky do zadní části sekvence a poskytne tak sémantiku, která se liší od sémantiky přepsání poskytnuté iterátory kontejnerů sekvence jazyka C++. `back_insert_iterator` Třída je převést na šablonu pro typ kontejneru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Container>  
class back_insert_iterator;  
```  
  
#### <a name="parameters"></a>Parametry  
 `Container`  
 Typ kontejneru na zadní straně prvky, které se mají vložit, `back_insert_iterator`.  
  
## <a name="remarks"></a>Poznámky  
 Kontejner musí splňovat požadavky pro sekvenci vložení do zadní části, je-li možné vložit prvky na konec sekvence v amortizovaném konstantním času. Kontejnery pořadí standardní knihovny C++ definované [deque – třída](../standard-library/deque-class.md), [list – třída](../standard-library/list-class.md) a [vector – třída](../standard-library/vector-class.md) poskytují potřebné `push_back` – členská funkce a splňovat tyto požadavky. Tyto tři kontejnery, jakož i řetězce mohou být každý upraveny pro použití s `back_insert_iterator`s. A `back_insert_iterator` musí být vždy inicializovaný s jeho kontejneru.  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[back_insert_iterator](#back_insert_iterator)|Vytvoří `back_insert_iterator` , vloží elementy po posledním prvkem v kontejneru.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[container_type](#container_type)|Typ, který poskytuje kontejner pro `back_insert_iterator`.|  
|[reference](#reference)|Typ, který poskytuje odkaz pro `back_insert_iterator`.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operator*](#op_star)|Při přesměrování operátor použít k implementaci výraz iterator výstup * `i`  =  `x` pro zpětné vložení.|  
|[operator++](#op_add_add)|Zvýší `back_insert_iterator` do následujícího umístění, do které můžou být uložené hodnotu.|  
|[operator=](#op_eq)|Operátor přiřazení použít k implementaci výraz iterator výstup * `i`  =  `x` pro zpětné vložení.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví**: \<iterator >  
  
 **Namespace:** – std  
  
##  <a name="back_insert_iterator"></a>  back_insert_iterator::back_insert_iterator  
 Vytvoří `back_insert_iterator` , vloží elementy po posledním prvkem v kontejneru.  
  
```   
explicit back_insert_iterator(Container& _Cont);
```  
  
### <a name="parameters"></a>Parametry  
 `_Cont`  
 Kontejner, `back_insert_iterator` je vložit do elementu.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `back_insert_iterator` parametr kontejneru.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// back_insert_iterator_back_insert_iterator.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for ( i = 1 ; i < 4 ; ++i )    
   {  
      vec.push_back ( i );  
   }  
  
   vector <int>::iterator vIter;  
   cout << "The initial vector vec is: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   // Insertions with member function  
   back_inserter ( vec ) = 40;  
   back_inserter ( vec ) = 50;  
  
   // Alternatively, insertions can be done with template function  
   back_insert_iterator<vector<int> > backiter ( vec );  
 *backiter = 600;  
   backiter++;  
 *backiter = 700;  
  
   cout << "After the insertions, the vector vec is: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
The initial vector vec is: ( 1 2 3 ).  
After the insertions, the vector vec is: ( 1 2 3 40 50 600 700 ).  
```  
  
##  <a name="container_type"></a>  back_insert_iterator::container_type  
 Typ, který poskytuje kontejner pro `back_insert_iterator`.  
  
```   
typedef Container  
container_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony **kontejneru**.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// back_insert_iterator_container_type.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 1 ; i < 4 ; ++i )    
   {  
      vec.push_back (  i );  
   }  
  
   vector <int>::iterator vIter;  
   cout << "The original vector vec is: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   back_insert_iterator<vector<int> >::container_type vec1 = vec;  
   back_inserter ( vec1 ) = 40;  
  
   cout << "After the insertion, the vector is: ( ";  
   for ( vIter = vec1.begin ( ) ; vIter != vec1.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
The original vector vec is: ( 1 2 3 ).  
After the insertion, the vector is: ( 1 2 3 40 ).  
```  
  
##  <a name="op_star"></a>  back_insert_iterator::Operator *  
 Při přesměrování operátor použít k implementaci výraz iterator výstup \* *i* = *x*.  
  
```  
back_insert_iterator<Container>& operator*();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na element vložen za kontejnerem.  
  
### <a name="remarks"></a>Poznámky  
 Použít k implementaci výraz iterator výstup  **\*Iter** = **hodnotu**. Pokud **Iter** je iterátor, která řeší prvku v sekvenci, pak  **\*Iter** = **hodnotu** nahrazen hodnotou tohoto prvku a není Celkový počet elementů v pořadí změňte.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// back_insert_iterator_back_insert.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 1 ; i < 4 ; ++i )    
   {  
      vec.push_back ( i );  
   }  
  
   vector <int>::iterator vIter;  
   cout << "The vector vec is: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   back_insert_iterator<vector<int> > backiter ( vec );  
 *backiter = 10;  
   backiter++;      // Increment to the next element  
 *backiter = 20;  
   backiter++;  
  
   cout << "After the insertions, the vector vec becomes: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
The vector vec is: ( 1 2 3 ).  
After the insertions, the vector vec becomes: ( 1 2 3 10 20 ).  
```  
  
##  <a name="op_add_add"></a>  back_insert_iterator::Operator ++  
 Zvýší `back_insert_iterator` do následujícího umístění, do které můžou být uložené hodnotu.  
  
```  
back_insert_iterator<Container>& operator++();
back_insert_iterator<Container> operator++(int);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `back_insert_iterator` adresování další umístění, do které můžou být uložené hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Operátory preincrementation a postincrementation vrátí stejný výsledek.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// back_insert_iterator_op_incre.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 1 ; i < 3 ; ++i )    
   {  
      vec.push_back ( 10 * i );  
   }  
  
   vector <int>::iterator vIter;  
   cout << "The vector vec is: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   back_insert_iterator<vector<int> > backiter ( vec );  
 *backiter = 30;  
   backiter++;      // Increment to the next element  
 *backiter = 40;  
   backiter++;  
  
   cout << "After the insertions, the vector vec becomes: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
The vector vec is: ( 10 20 ).  
After the insertions, the vector vec becomes: ( 10 20 30 40 ).  
```  
  
##  <a name="op_eq"></a>  back_insert_iterator::operator=  
 Připojí nebo nabízených oznámení hodnotu na back-end kontejneru.  
  
```  
back_insert_iterator<Container>& operator=(typename Container::const_reference val);
back_insert_iterator<Container>& operator=(typename Container::value_type&& val);
```  
  
### <a name="parameters"></a>Parametry  
 `val`  
 Hodnota, která má být vložen do kontejneru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na posledním elementem vložen za kontejnerem.  
  
### <a name="remarks"></a>Poznámky  
 První člen operátor vyhodnotí `Container.push_back( val)`,  
  
 Vrátí `*this`. Vyhodnotí druhý operátor členů  
  
 `container->push_back((typename Container::value_type&&)val)`,  
  
 Vrátí `*this`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// back_insert_iterator_op_assign.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 1 ; i < 4 ; ++i )    
   {  
      vec.push_back ( i );  
   }  
  
   vector <int>::iterator vIter;  
   cout << "The vector vec is: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   back_insert_iterator<vector<int> > backiter ( vec );  
 *backiter = 10;  
   backiter++;      // Increment to the next element  
 *backiter = 20;  
   backiter++;  
  
   cout << "After the insertions, the vector vec becomes: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="reference"></a>  back_insert_iterator::Reference  
 Typ, který poskytuje odkaz pro `back_insert_iterator`.  
  
```  
typedef typename Container::reference reference;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ popisuje odkaz na element pořadí řízené přidružené kontejneru.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// back_insert_iterator_reference.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 1 ; i < 4 ; ++i )    
   {  
      vec.push_back ( i );  
   }  
  
   vector <int>::iterator vIter;  
   cout << "The vector vec is: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   back_insert_iterator<vector<int> >::reference   
        RefLast = *(vec.end ( ) - 1 );  
   cout << "The last element in the vector vec is: "   
        << RefLast << "." << endl;  
}  
```  
  
```Output  
The vector vec is: ( 1 2 3 ).  
The last element in the vector vec is: 3.  
```  
  
## <a name="see-also"></a>Viz také  
 [\<iterator>](../standard-library/iterator.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)

