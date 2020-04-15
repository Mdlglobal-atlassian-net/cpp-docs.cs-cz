---
title: insert_iterator – třída
ms.date: 11/04/2016
f1_keywords:
- iterator/std::insert_iterator
- iterator/std::insert_iterator::container_type
- iterator/std::insert_iterator::reference
helpviewer_keywords:
- std::insert_iterator [C++]
- std::insert_iterator [C++], container_type
- std::insert_iterator [C++], reference
ms.assetid: d5d86405-872e-4e3b-9e68-c69a2b7e8221
ms.openlocfilehash: 2865db023425fa301ad5440a0dc8ed491213f33f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368060"
---
# <a name="insert_iterator-class"></a>insert_iterator – třída

Popisuje adaptér iterátoru, který splňuje požadavky výstupního iterátoru. Vloží, spíše než přepíše, prvky do zadní části sekvence a poskytne tak sémantiku, která se liší od sémantiky přepsání poskytnuté iterátory kontejnerů sekvence jazyka C++ a asociativními kontejnery. Třída `insert_iterator` je templatized na typu kontejneru, který je přizpůsoben.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Container>
class insert_iterator;
```

### <a name="parameters"></a>Parametry

*Kontejner*\
Typ kontejneru, do kterého mají být `insert_iterator`prvky vloženy .

## <a name="remarks"></a>Poznámky

Kontejner `Container` typu musí splňovat požadavky na kontejner proměnné velikosti a mít dvouargumentovou člennou funkci `Container::iterator` `Container::value_type` insert, kde `Container::iterator`jsou parametry typu a který vrací typ . C++ Standardní knihovna sekvence a seřazené asociativní `insert_iterator`kontejnery splňují tyto požadavky a mohou být přizpůsobeny pro použití s. Pro asociativní kontejnery je argument pozice považován za pokyn, který má potenciál zlepšit nebo snížit výkon v závislosti na tom, jak kvalitní nápověda je. Musí `insert_iterator` být vždy inicializováns jeho kontejneru.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[insert_iterator](#insert_iterator)|`insert_iterator` Vytvoří, který vloží prvek do zadané pozice v kontejneru.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[container_type](#container_type)|Typ, který představuje kontejner, do kterého má být provedeno obecné vložení.|
|[Odkaz](#reference)|Typ, který poskytuje odkaz na prvek v sekvenci řízené přiřazeným kontejnerem.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor*](#op_star)|Dereferencing operátor slouží k implementaci výstupního `i`  =  `x` iterátoru výraz * pro obecné vložení.|
|[operátor++](#op_add_add)|Přírůstky `insert_iterator` do dalšího umístění, do kterého může být uložena hodnota.|
|[operátor =](#op_eq)|Operátor přiřazení použitý k implementaci výstupního `i`  =  `x` výrazu iterátoru * pro obecné vložení.|

## <a name="requirements"></a>Požadavky

**Záhlaví** \<: iterátor>

**Obor názvů:** std

## <a name="insert_iteratorcontainer_type"></a><a name="container_type"></a>insert_iterator::container_type

Typ, který představuje kontejner, do kterého má být provedeno obecné vložení.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro parametr šablony *Container*.

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
/* Output:
The list L2 is: ( 40 20 10 ).
*/
```

## <a name="insert_iteratorinsert_iterator"></a><a name="insert_iterator"></a>insert_iterator::insert_iterator

`insert_iterator` Vytvoří, který vloží prvek do zadané pozice v kontejneru.

```cpp
insert_iterator(Container& _Cont, typename Container::iterator _It);
```

### <a name="parameters"></a>Parametry

*_Cont*\
Kontejner, `insert_iterator` do kterého je vložit prvky.

*_It*\
Pozice pro vložení.

### <a name="remarks"></a>Poznámky

Všechny kontejnery mají vložit člennou funkci volanou `insert_iterator`. Pro asociativní kontejnery je parametr pozice pouze návrhem. Funkce vložení poskytuje pohodlný způsob vložení do hodnot.

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
/* Output:
The list L is:
( 10 20 30 ).
After the insertions, the list L is:
( 2 10 20 30 300 ).
*/
```

## <a name="insert_iteratoroperator"></a><a name="op_star"></a>insert_iterator::operátor*

Dereferences vložit iterátor vrácení prvku je adresy.

```cpp
insert_iterator<Container>& operator*();
```

### <a name="return-value"></a>Návratová hodnota

Členská funkce vrátí hodnotu adresovaného prvku.

### <a name="remarks"></a>Poznámky

Slouží k implementaci výstupního iterátorového = **výrazu** ** \*Iter**value . Pokud `Iter` je iterátor, který řeší prvek v sekvenci, pak ** \*Iter** = **hodnota** nahradí tento prvek s hodnotou a nezmění celkový počet prvků v sekvenci.

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
/* Output:
The original list L is:
( 0 2 4 6 ).
After the insertions, the list L is:
( 10 20 30 0 2 4 6 ).
*/
```

## <a name="insert_iteratoroperator"></a><a name="op_add_add"></a>insert_iterator::operátor++

Přírůstky `insert_iterator` do dalšího umístění, do kterého může být uložena hodnota.

```cpp
insert_iterator<Container>& operator++();

insert_iterator<Container> operator++(int);
```

### <a name="parameters"></a>Parametry

Adresování `insert_iterator` další umístění, do kterého může být uložena hodnota.

### <a name="remarks"></a>Poznámky

Preincrementation a postincrementation operátory vrátit stejný výsledek.

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
/* Output:
The vector vec is:
( 1 2 3 4 ).
After the insertions, the vector vec becomes:
( 30 40 50 1 2 3 4 ).
*/
```

## <a name="insert_iteratoroperator"></a><a name="op_eq"></a>insert_iterator::operátor=

Vloží hodnotu do kontejneru a vrátí iterátor aktualizován tak, aby přecšit na nový prvek.

```cpp
insert_iterator<Container>& operator=(
    typename Container::const_reference val,);

insert_iterator<Container>& operator=(
    typename Container::value_type&& val);
```

### <a name="parameters"></a>Parametry

*Val*\
Hodnota, která má být přiřazena ke kontejneru.

### <a name="return-value"></a>Návratová hodnota

Odkaz na prvek vložený do kontejneru.

### <a name="remarks"></a>Poznámky

První operátor člena vyhodnotí

`Iter = container->insert(Iter, val)`;

`++Iter;`

pak `*this`vrátí .

Druhý operátor člena vyhodnotí

`Iter = container->insert(Iter, std::move(val));`

`++Iter;`

pak `*this`vrátí .

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
/* Output:
The original list L is:
( 0 2 4 6 ).
After the insertions, the list L is:
( 10 20 30 0 2 4 6 ).
*/
```

## <a name="insert_iteratorreference"></a><a name="reference"></a>insert_iterator::odkaz

Typ, který poskytuje odkaz na prvek v sekvenci řízené přiřazeným kontejnerem.

```cpp
typedef typename Container::reference reference;
```

### <a name="remarks"></a>Poznámky

Typ popisuje odkaz na prvek sekvence řízené přidružené kontejneru.

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
/* Output:
The list L is: ( 10 20 30 ).
The first element in the list L is: 10.
*/
```

## <a name="see-also"></a>Viz také

[\<>iterátoru](../standard-library/iterator.md)\
[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referenční příručka standardní knihovny jazyka C++](../standard-library/cpp-standard-library-reference.md)
