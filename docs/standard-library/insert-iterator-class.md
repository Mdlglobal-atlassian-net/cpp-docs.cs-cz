---
title: "insert_iterator – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- iterator/std::insert_iterator
- iterator/std::insert_iterator::container_type
- iterator/std::insert_iterator::reference
dev_langs: C++
helpviewer_keywords:
- std::insert_iterator [C++]
- std::insert_iterator [C++], container_type
- std::insert_iterator [C++], reference
ms.assetid: d5d86405-872e-4e3b-9e68-c69a2b7e8221
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c5b893e3c1d30d457d479f5c2dcf42fb97bb978f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="insertiterator-class"></a>insert_iterator – třída
Popisuje adaptér iterátoru, který splňuje požadavky výstupního iterátoru. Vloží, spíše než přepíše, prvky do zadní části sekvence a poskytne tak sémantiku, která se liší od sémantiky přepsání poskytnuté iterátory kontejnerů sekvence jazyka C++ a asociativními kontejnery. `insert_iterator` Třída je převést na šablonu pro typ kontejneru se přizpůsobit.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Container>  
class insert_iterator;
```  
  
#### <a name="parameters"></a>Parametry  
 `Container`  
 Typ kontejneru, do kterého mají vkládat elementy `insert_iterator`.  
  
## <a name="remarks"></a>Poznámky  
 Kontejner typu **kontejneru** musí splňovat podmínky pro kontejner proměnlivé velikosti a mít dva argument vložení členské funkce, kde jsou parametry typu **Container::iterator** a **Container::value_type** a který vrátí typ **Container::iterator**. Standardní knihovna C++ pořadí a seřazené asociativní kontejnery splňovat tyto požadavky a dokáže se přizpůsobit pro použití s `insert_iterator`s. Pro asociativní kontejnery je argument pozice považován za pokyn, který má potenciál zlepšit nebo snížit výkon v závislosti na tom, jak kvalitní nápověda je. `insert_iterator` Musí být vždy inicializovaný s jeho kontejneru.  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[insert_iterator –](#insert_iterator)|Vytvoří `insert_iterator` , element vloží do zadané pozici v kontejneru.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[container_type –](#container_type)|Typ, který představuje kontejner, do kterého má být provedeno obecné vložení.|  
|[referenční dokumentace](#reference)|Typ, který poskytuje odkaz na prvek v sekvenci řízené přiřazeným kontejnerem.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operátor *](#op_star)|Při přesměrování operátor použít k implementaci výraz iterator výstup * `i`  =  `x` pro obecné vložení.|  
|[Operator ++](#op_add_add)|Zvýší `insert_iterator` do následujícího umístění, do které můžou být uložené hodnotu.|  
|[operátor =](#op_eq)|Operátor přiřazení použít k implementaci výraz iterator výstup * `i`  =  `x` pro obecné vložení.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví**: \<iterator >  
  
 **Namespace:** – std  
  
##  <a name="container_type"></a>insert_iterator::container_type  
 Typ, který představuje kontejner, do kterého má být provedeno obecné vložení.  
  
```
typedef Container container_type;
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony **kontejneru**.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// insert_iterator_container_type.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   list<int> L1;  
   insert_iterator<list<int> >::container_type L2 = L1;  
   inserter ( L2, L2.end ( ) ) = 20;  
   inserter ( L2, L2.end ( ) ) = 10;  
   inserter ( L2, L2.begin ( ) ) = 40;  
  
   list <int>::iterator vIter;  
   cout << "The list L2 is: ( ";  
   for ( vIter = L2.begin ( ) ; vIter != L2.end ( ); vIter++ )  
      cout << *vIter << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The list L2 is: ( 40 20 10 ).  
*\  
```  
  
##  <a name="insert_iterator"></a>insert_iterator::insert_iterator  
 Vytvoří `insert_iterator` , element vloží do zadané pozici v kontejneru.  
  
```
insert_iterator(Container& _Cont, typename Container::iterator _It);
```  
  
### <a name="parameters"></a>Parametry  
 `_Cont`  
 Kontejner, do kterého `insert_iterator` je vložit elementy.  
  
 `_It`  
 Pozice pro vložení.  
  
### <a name="remarks"></a>Poznámky  
 Všechny kontejnery mít volá funkci člen vložení `insert_iterator`. Pro kontejnery asociativní je parametr určující pozici jenom návrhu. Vkládací modul funkce představuje pohodlný způsob vložit hodnoty.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// insert_iterator_insert_iterator.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
   list <int>::iterator L_Iter;  
  
   list<int> L;  
   for (i = 1 ; i < 4 ; ++i )    
   {  
      L.push_back ( 10 * i );  
   }  
  
   cout << "The list L is:\n ( ";  
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)  
      cout << *L_Iter << " ";  
   cout << ")." << endl;  
  
   // Using the member function to insert an element  
   inserter ( L, L.begin ( ) ) = 2;  
  
   // Alternatively, you may use the template version  
   insert_iterator< list < int> > Iter(L, L.end ( ) );  
 *Iter = 300;  
  
   cout << "After the insertions, the list L is:\n ( ";  
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )  
      cout << *L_Iter << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The list L is:  
 ( 10 20 30 ).  
After the insertions, the list L is:  
 ( 2 10 20 30 300 ).  
*\  
```  
  
##  <a name="op_star"></a>insert_iterator::Operator *  
 Dereferences iterator vložení vrácení elementu je adresy.  
  
```
insert_iterator<Container>& operator*();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Členská funkce vrátí hodnotu elementu řešit.  
  
### <a name="remarks"></a>Poznámky  
 Použít k implementaci výraz iterator výstup  **\*Iter** = **hodnotu**. Pokud **Iter** je iterátor, která řeší prvku v sekvenci, pak  **\*Iter** = **hodnotu** nahrazen hodnotou tohoto prvku a není Celkový počet elementů v pořadí změňte.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// insert_iterator_op_deref.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
   list <int>::iterator L_Iter;  
  
   list<int> L;  
   for (i = 0 ; i < 4 ; ++i )    
   {  
      L.push_back ( 2 * i );  
   }  
  
   cout << "The original list L is:\n ( ";  
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )  
      cout << *L_Iter << " ";  
   cout << ")." << endl;  
  
   insert_iterator< list < int> > Iter(L, L.begin ( ) );  
 *Iter = 10;  
 *Iter = 20;  
 *Iter = 30;  
  
   cout << "After the insertions, the list L is:\n ( ";  
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )  
      cout << *L_Iter << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The original list L is:  
 ( 0 2 4 6 ).  
After the insertions, the list L is:  
 ( 10 20 30 0 2 4 6 ).  
*\  
```  
  
##  <a name="op_add_add"></a>insert_iterator::Operator ++  
 Zvýší **insert_iterator** do následujícího umístění, do které můžou být uložené hodnotu.  
  
```
insert_iterator<Container>& operator++();

insert_iterator<Container> operator++(int);
```  
  
### <a name="parameters"></a>Parametry  
 A `insert_iterator` adresování další umístění, do které můžou být uložené hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Operátory preincrementation a postincrementation vrátí stejný výsledek.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// insert_iterator_op_incr.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 1 ; i < 5 ; ++i )   
   {  
      vec.push_back (  i );  
   }  
  
   vector <int>::iterator vIter;  
   cout << "The vector vec is:\n ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   insert_iterator<vector<int> > ii ( vec, vec.begin ( ) );  
 *ii = 30;  
   ii++;  
 *ii = 40;  
   ii++;  
 *ii = 50;  
  
   cout << "After the insertions, the vector vec becomes:\n ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )  
      cout << *vIter << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The vector vec is:  
 ( 1 2 3 4 ).  
After the insertions, the vector vec becomes:  
 ( 30 40 50 1 2 3 4 ).  
*\  
```  
  
##  <a name="op_eq"></a>insert_iterator::Operator =  
 Vloží hodnotu do kontejneru a vrátí iterator aktualizovat tak, aby odkazoval na nový element.  
  
```
insert_iterator<Container>& operator=(
    typename Container::const_reference val,);

insert_iterator<Container>& operator=(
    typename Container::value_type&& val);
```  
  
### <a name="parameters"></a>Parametry  
 `val`  
 Hodnota pro přiřazení ke kontejneru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na element vložen do kontejneru.  
  
### <a name="remarks"></a>Poznámky  
 Vyhodnotí první operátor členů  
  
 `Iter = container->insert(Iter, val)`;  
  
 `++Iter;`  
  
 Vrátí `*this`.  
  
 Vyhodnotí druhý operátor členů  
  
 `Iter = container->insert(Iter, std::move(val));`  
  
 `++Iter;`  
  
 Vrátí `*this`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// insert_iterator_op_assign.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
   list <int>::iterator L_Iter;  
  
   list<int> L;  
   for (i = 0 ; i < 4 ; ++i )   
   {  
      L.push_back ( 2 * i );  
   }  
  
   cout << "The original list L is:\n ( ";  
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )  
      cout << *L_Iter << " ";  
   cout << ")." << endl;  
  
   insert_iterator< list < int> > Iter(L, L.begin ( ) );  
 *Iter = 10;  
 *Iter = 20;  
 *Iter = 30;  
  
   cout << "After the insertions, the list L is:\n ( ";  
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )  
      cout << *L_Iter << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The original list L is:  
 ( 0 2 4 6 ).  
After the insertions, the list L is:  
 ( 10 20 30 0 2 4 6 ).  
*\  
```  
  
##  <a name="reference"></a>insert_iterator::Reference  
 Typ, který poskytuje odkaz na prvek v sekvenci řízené přiřazeným kontejnerem.  
  
```
typedef typename Container::reference reference;
```  
  
### <a name="remarks"></a>Poznámky  
 Typ popisuje odkaz na element pořadí řízené přidružené kontejneru.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// insert_iterator_container_reference.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   list<int> L;  
   insert_iterator<list<int> > iivIter( L , L.begin ( ) );  
 *iivIter = 10;  
 *iivIter = 20;  
 *iivIter = 30;  
  
   list<int>::iterator LIter;  
   cout << "The list L is: ( ";  
   for ( LIter = L.begin ( ) ; LIter != L.end ( ); LIter++ )  
      cout << *LIter << " ";  
   cout << ")." << endl;  
  
   insert_iterator<list<int> >::reference   
        RefFirst = *(L.begin ( ));  
   cout << "The first element in the list L is: "   
        << RefFirst << "." << endl;  
}  
\* Output:   
The list L is: ( 10 20 30 ).  
The first element in the list L is: 10.  
*\  
```  
  
## <a name="see-also"></a>Viz také  
 [\<iterator >](../standard-library/iterator.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)



