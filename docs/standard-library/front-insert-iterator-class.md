---
title: front_insert_iterator – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- iterator/std::front_insert_iterator
- iterator/std::front_insert_iterator::container_type
- iterator/std::front_insert_iterator::reference
dev_langs:
- C++
helpviewer_keywords:
- std::front_insert_iterator [C++]
- std::front_insert_iterator [C++], container_type
- std::front_insert_iterator [C++], reference
ms.assetid: a9a9c075-136a-4419-928b-c4871afa033c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b6a9323a75b18349b0967259ec89dbabd46d88b
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108424"
---
# <a name="frontinsertiterator-class"></a>front_insert_iterator – třída

Popisuje adaptér iterátoru, který splňuje požadavky výstupního iterátoru. Vloží, spíše než přepíše, prvky do přední části sekvence a poskytne tak sémantiku, která se liší od sémantiky přepsání poskytnuté iterátory kontejnerů sekvence jazyka C++. `front_insert_iterator` Třídy je založena na typu kontejneru.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Container>
class front_insert_iterator;
```

### <a name="parameters"></a>Parametry

*Kontejner*<br/>
Typ kontejneru, do front, které mají být vloženy pomocí prvků `front_insert_iterator`.

## <a name="remarks"></a>Poznámky

Kontejner musí splňovat požadavky pro sekvenci vložení do přední části, je-li možné vložit prvky na začátek sekvence v amortizovaném konstantním času. Kontejnery sekvence standardní knihovny C++ definované [třídou deque](../standard-library/deque-class.md) a [list – třída](../standard-library/list-class.md) poskytují potřebnou `push_front` členské funkce a tyto požadavky splňují. Naopak kontejnery sekvence definované [vector – třída](../standard-library/vector-class.md) tyto požadavky nesplňují a nelze je adaptovat k použití s `front_insert_iterator`s. A `front_insert_iterator` je vždy nutné inicializovat s jejím kontejnerem.

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
|[Operator *](#op_star)|Operátor přesměrování používaný k implementaci výrazu výstupního iterátoru \* `i`  =  `x` pro vložení dopředu.|
|[Operator ++](#op_add_add)|Zvýší `front_insert_iterator` do následujícího umístění, do kterého mohou být uloženy hodnotu.|
|[operátor =](#op_eq)|Operátor přiřazení používaný k implementaci výrazu výstupního iterátoru \* `i`  =  `x` pro vložení dopředu.|

## <a name="requirements"></a>Požadavky

**Hlavička**: \<iterátor >

**Namespace:** std

## <a name="container_type"></a>  front_insert_iterator::container_type

Typ, který představuje kontejner, do jehož přední části má být vložení provedeno.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony *kontejneru*.

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
\* Output:
The list L2 is: ( 40 10 20 ).
*\
```

## <a name="front_insert_iterator"></a>  front_insert_iterator::front_insert_iterator

Vytvoří iterátor, který může vložit prvky do přední části zadaného objektu kontejneru.

```cpp
explicit front_insert_iterator(Container& _Cont);
```

### <a name="parameters"></a>Parametry

*_Cont*<br/>
Objekt kontejneru, do kterého `front_insert_iterator` je vložit prvky.

### <a name="return-value"></a>Návratová hodnota

A `front_insert_iterator` pro parametr objektu kontejneru.

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
\* Output:
The list L is:
( -2 0 2 4 6 8 10 12 14 16 ).
After the front insertions, the list L is:
( 30 20 -2 0 2 4 6 8 10 12 14 16 ).
*\
```

## <a name="op_star"></a>  front_insert_iterator::Operator\*

Přístupů přes ukazatel iterátoru vložení vrátí prvek, na který se zaměřuje.

```cpp
front_insert_iterator<Container>& operator*();
```

### <a name="return-value"></a>Návratová hodnota

Členská funkce vrátí hodnotu prvku zákazníky a vyřešené.

### <a name="remarks"></a>Poznámky

Používaný k implementaci výrazu výstupního iterátoru  **\*Iter** = **hodnota**. Pokud `Iter` je iterátor adresující prvek v sekvenci, pak  **\*Iter** = **hodnotu** nahrazuje tento element s hodnotou a nemění celkový počet prvky v sekvenci.

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
\* Output:
The list L is:
( -2 0 2 4 6 8 10 12 14 16 ).
After the front insertions, the list L is:
( 30 20 -2 0 2 4 6 8 10 12 14 16 ).
*\
```

## <a name="op_add_add"></a>  front_insert_iterator::Operator ++

Zvýší `back_insert_iterator` do následujícího umístění, do kterého mohou být uloženy hodnotu.

```cpp
front_insert_iterator<Container>& operator++();

front_insert_iterator<Container> operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

A `front_insert_iterator` adresování další umístění, do kterého mohou být uloženy hodnotu.

### <a name="remarks"></a>Poznámky

Operátory preincrementation a postincrementation vrací stejný výsledek.

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
\* Output:
The list L1 is: ( 30 20 10 ).
*\
```

## <a name="op_eq"></a>  front_insert_iterator::Operator =

Připojí (nabízená oznámení) hodnotu do přední části kontejneru.

```cpp
front_insert_iterator<Container>& operator=(typename Container::const_reference val);

front_insert_iterator<Container>& operator=(typename Container::value_type&& val);
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Hodnota má být přiřazena ke kontejneru.

### <a name="return-value"></a>Návratová hodnota

Odkaz na poslední prvek vložený do přední části kontejneru.

### <a name="remarks"></a>Poznámky

První členský operátor vyhodnotí `container.push_front( val)`, vrátí `*this`.

Vyhodnotí se druhý členský operátor

`container->push_front((typename Container::value_type&&) val)`,

Vrátí `*this`.

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
\* Output:
The list L1 is: ( 30 20 10 ).
*\
```

## <a name="reference"></a>  front_insert_iterator::Reference

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
\* Output:
The list L is: ( 30 20 10 ).
The first element in the list L is: 30.
*\
```

## <a name="see-also"></a>Viz také:

[\<iterátor >](../standard-library/iterator.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
