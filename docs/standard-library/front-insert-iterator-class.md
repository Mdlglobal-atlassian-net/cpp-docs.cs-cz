---
title: front_insert_iterator – třída
ms.date: 11/04/2016
f1_keywords:
- iterator/std::front_insert_iterator
- iterator/std::front_insert_iterator::container_type
- iterator/std::front_insert_iterator::reference
helpviewer_keywords:
- std::front_insert_iterator [C++]
- std::front_insert_iterator [C++], container_type
- std::front_insert_iterator [C++], reference
ms.assetid: a9a9c075-136a-4419-928b-c4871afa033c
ms.openlocfilehash: 176fac8053d352d6a7a72ce62d5a8ee7a64b9811
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454124"
---
# <a name="frontinsertiterator-class"></a>front_insert_iterator – třída

Popisuje adaptér iterátoru, který splňuje požadavky výstupního iterátoru. Vloží, spíše než přepíše, prvky do přední části sekvence a poskytne tak sémantiku, která se liší od sémantiky přepsání poskytnuté iterátory kontejnerů sekvence jazyka C++. `front_insert_iterator` Třída je založena na typu kontejneru.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Container>
class front_insert_iterator;
```

### <a name="parameters"></a>Parametry

*Vnitřního*\
Typ kontejneru na začátek, který prvky mají být vloženy `front_insert_iterator`.

## <a name="remarks"></a>Poznámky

Kontejner musí splňovat požadavky pro sekvenci vložení do přední části, je-li možné vložit prvky na začátek sekvence v amortizovaném konstantním času. Standardní kontejnery sekvence knihovny definované [třídou deque](../standard-library/deque-class.md) a třídou [seznamu](../standard-library/list-class.md) poskytují potřebnou `push_front` členskou funkci a splňují tyto požadavky. C++ Naproti tomu kontejnery sekvence definované třídou [Vector](../standard-library/vector-class.md) tyto požadavky nesplňují a nelze je přizpůsobit pro použití s `front_insert_iterator`. Objekt `front_insert_iterator` musí být vždy inicializován s jeho kontejnerem.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[front_insert_iterator](#front_insert_iterator)|Vytvoří iterátor, který může vložit prvky do přední části zadaného objektu kontejneru.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[container_type](#container_type)|Typ, který představuje kontejner, do jehož přední části má být vložení provedeno.|
|[Referenční dokumentace](#reference)|Typ, který poskytuje odkaz na prvek v sekvenci řízené přiřazeným kontejnerem.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[podnikatel](#op_star)|Operátor přesměrování \* používaný k implementaci výrazu `i`  =  `x` výstupního iterátoru pro vložení dopředu.|
|[operator + + – operátor](#op_add_add)|`front_insert_iterator` Zvýší na další místo, do kterého může být hodnota uložená.|
|[operátor =](#op_eq)|Operátor přiřazení \* používaný k implementaci výrazu `i`  =  `x` výstupního iterátoru pro vložení do popředí.|

## <a name="requirements"></a>Požadavky

**Záhlaví**: \<iterátor >

**Obor názvů:** std

## <a name="container_type"></a>front_insert_iterator::container_type

Typ, který představuje kontejner, do jehož přední části má být vložení provedeno.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro *kontejner*parametrů šablony.

### <a name="example"></a>Příklad

```cpp
// front_insert_iterator_container_type.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L1;
   front_insert_iterator<list<int> >::container_type L2 = L1;
   front_inserter ( L2 ) = 20;
   front_inserter ( L2 ) = 10;
   front_inserter ( L2 ) = 40;

   list <int>::iterator vIter;
   cout << "The list L2 is: ( ";
   for ( vIter = L2.begin ( ) ; vIter != L2.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The list L2 is: ( 40 10 20 ).
*/
```

## <a name="front_insert_iterator"></a>front_insert_iterator::front_insert_iterator

Vytvoří iterátor, který může vložit prvky do přední části zadaného objektu kontejneru.

```cpp
explicit front_insert_iterator(Container& _Cont);
```

### <a name="parameters"></a>Parametry

*_Cont*\
Objekt kontejneru, do kterého `front_insert_iterator` má být vložen element.

### <a name="return-value"></a>Návratová hodnota

`front_insert_iterator` Pro objekt kontejneru parametru.

### <a name="example"></a>Příklad

```cpp
// front_insert_iterator_front_insert_iterator.cpp
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
   for (i = -1 ; i < 9 ; ++i )
   {
      L.push_back ( 2 * i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   // Using the member function to insert an element
   front_inserter ( L ) = 20;

   // Alternatively, one may use the template function
   front_insert_iterator< list < int> > Iter(L);
*Iter = 30;

   cout << "After the front insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The list L is:
( -2 0 2 4 6 8 10 12 14 16 ).
After the front insertions, the list L is:
( 30 20 -2 0 2 4 6 8 10 12 14 16 ).
*/
```

## <a name="op_star"></a>front_insert_iterator:: operator\*

Vyřeší iterátor vložení, který vrací element, na který odkazuje.

```cpp
front_insert_iterator<Container>& operator*();
```

### <a name="return-value"></a>Návratová hodnota

Členská funkce vrací hodnotu prvku, který je adresován.

### <a name="remarks"></a>Poznámky

Slouží k implementaci**hodnoty**  **\*ITER** = výrazu výstupního iterátoru. Pokud `Iter` je iterátor, který adresuje prvek v sekvenci, pak  **\*** **hodnota** ITER = nahrazuje tento prvek hodnotou a nemění celkový počet prvků v sekvenci.

### <a name="example"></a>Příklad

```cpp
// front_insert_iterator_deref.cpp
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
   for ( i = -1 ; i < 9 ; ++i )
   {
      L.push_back ( 2 * i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   front_insert_iterator< list < int> > Iter(L);
*Iter = 20;

   // Alternatively, you may use
   front_inserter ( L ) = 30;

   cout << "After the front insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The list L is:
( -2 0 2 4 6 8 10 12 14 16 ).
After the front insertions, the list L is:
( 30 20 -2 0 2 4 6 8 10 12 14 16 ).
*/
```

## <a name="op_add_add"></a>front_insert_iterator:: operator + +

`back_insert_iterator` Zvýší na další místo, do kterého může být hodnota uložená.

```cpp
front_insert_iterator<Container>& operator++();

front_insert_iterator<Container> operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

`front_insert_iterator` Adresování dalšího umístění, do kterého může být uložena hodnota.

### <a name="remarks"></a>Poznámky

Jak předpřírůstkový operátor, tak operátory postincrementation vrací stejný výsledek.

### <a name="example"></a>Příklad

```cpp
// front_insert_iterator_op_incre.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L1;
   front_insert_iterator<list<int> > iter ( L1 );
*iter = 10;
   iter++;
*iter = 20;
   iter++;
*iter = 30;
   iter++;

   list <int>::iterator vIter;
   cout << "The list L1 is: ( ";
   for ( vIter = L1.begin ( ) ; vIter != L1.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The list L1 is: ( 30 20 10 ).
*/
```

## <a name="op_eq"></a>front_insert_iterator:: operator =

Připojí na začátek kontejneru hodnotu (push).

```cpp
front_insert_iterator<Container>& operator=(typename Container::const_reference val);

front_insert_iterator<Container>& operator=(typename Container::value_type&& val);
```

### <a name="parameters"></a>Parametry

*počítává*\
Hodnota, která má být přiřazena kontejneru.

### <a name="return-value"></a>Návratová hodnota

Odkaz na poslední prvek vložený na začátek kontejneru.

### <a name="remarks"></a>Poznámky

První operátor členu vyhodnotí `container.push_front( val)`a potom vrátí. `*this`

Druhý členský operátor vyhodnocuje

`container->push_front((typename Container::value_type&&) val)`,

pak vrátí `*this`.

### <a name="example"></a>Příklad

```cpp
// front_insert_iterator_op_assign.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L1;
   front_insert_iterator<list<int> > iter ( L1 );
*iter = 10;
   iter++;
*iter = 20;
   iter++;
*iter = 30;
   iter++;

   list <int>::iterator vIter;
   cout << "The list L1 is: ( ";
   for ( vIter = L1.begin ( ) ; vIter != L1.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The list L1 is: ( 30 20 10 ).
*/
```

## <a name="reference"></a>front_insert_iterator:: Reference

Typ, který poskytuje odkaz na prvek v sekvenci řízené přiřazeným kontejnerem.

```cpp
typedef typename Container::reference reference;
```

### <a name="example"></a>Příklad

```cpp
// front_insert_iterator_reference.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L;
   front_insert_iterator<list<int> > fiivIter( L );
*fiivIter = 10;
*fiivIter = 20;
*fiivIter = 30;

   list<int>::iterator LIter;
   cout << "The list L is: ( ";
   for ( LIter = L.begin ( ) ; LIter != L.end ( ); LIter++)
      cout << *LIter << " ";
   cout << ")." << endl;

   front_insert_iterator<list<int> >::reference
        RefFirst = *(L.begin ( ));
   cout << "The first element in the list L is: "
        << RefFirst << "." << endl;
}
/* Output:
The list L is: ( 30 20 10 ).
The first element in the list L is: 30.
*/
```

## <a name="see-also"></a>Viz také:

[\<iterátor >](../standard-library/iterator.md)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
