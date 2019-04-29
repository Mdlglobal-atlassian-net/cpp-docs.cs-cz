---
title: back_insert_iterator – třída
ms.date: 11/04/2016
f1_keywords:
- iterator/std::back_insert_iterator
- iterator/std::back_insert_iterator::container_type
- iterator/std::back_insert_iterator::reference
helpviewer_keywords:
- std::back_insert_iterator [C++]
- std::back_insert_iterator [C++], container_type
- std::back_insert_iterator [C++], reference
ms.assetid: a1ee07f2-cf9f-46a1-8608-cfaf207f9713
ms.openlocfilehash: 2a0510b6df656b7925fd42a4c97d768336537424
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62376442"
---
# <a name="backinsertiterator-class"></a>back_insert_iterator – třída

Popisuje adaptér iterátoru, který splňuje požadavky výstupního iterátoru. Vloží, spíše než přepíše, prvky do zadní části sekvence a poskytne tak sémantiku, která se liší od sémantiky přepsání poskytnuté iterátory kontejnerů sekvence jazyka C++. `back_insert_iterator` Třídy je založena na typu kontejneru.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Container>
class back_insert_iterator;
```

### <a name="parameters"></a>Parametry

*Kontejner*<br/>
Typ kontejneru, do zadní prvky, které mají být vloženy podle `back_insert_iterator`.

## <a name="remarks"></a>Poznámky

Kontejner musí splňovat požadavky pro sekvenci vložení do zadní části, je-li možné vložit prvky na konec sekvence v amortizovaném konstantním času. Kontejnery sekvence standardní knihovny C++ definované [třídou deque](../standard-library/deque-class.md), [list – třída](../standard-library/list-class.md) a [vector – třída](../standard-library/vector-class.md) poskytují potřebnou `push_back` členské funkce a Tyto požadavky splňují. Tyto tři kontejnery stejně jako řetězce lze jednotlivě adaptovat k použití s `back_insert_iterator`s. A `back_insert_iterator` je vždy nutné inicializovat s jejím kontejnerem.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[back_insert_iterator](#back_insert_iterator)|Vytvoří `back_insert_iterator` , která vloží prvky za posledním prvkem v kontejneru.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[container_type](#container_type)|Typ, který poskytuje kontejner pro `back_insert_iterator`.|
|[Referenční dokumentace](#reference)|Typ, který poskytuje odkaz pro `back_insert_iterator`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[Operator *](#op_star)|Operátor přesměrování používaný k implementaci výrazu výstupního iterátoru \* `i`  =  `x` pro zpětné vložení.|
|[Operator ++](#op_add_add)|Zvýší `back_insert_iterator` do následujícího umístění, do kterého mohou být uloženy hodnotu.|
|[operátor =](#op_eq)|Operátor přiřazení používaný k implementaci výrazu výstupního iterátoru \* `i`  =  `x` pro zpětné vložení.|

## <a name="requirements"></a>Požadavky

**Hlavička**: \<iterátor >

**Namespace:** std

## <a name="back_insert_iterator"></a>  back_insert_iterator::back_insert_iterator

Vytvoří `back_insert_iterator` , která vloží prvky za posledním prvkem v kontejneru.

```cpp
explicit back_insert_iterator(Container& _Cont);
```

### <a name="parameters"></a>Parametry

*_Cont*<br/>
Kontejner, který `back_insert_iterator` je pro vložení elementu do.

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

## <a name="container_type"></a>  back_insert_iterator::container_type

Typ, který poskytuje kontejner pro `back_insert_iterator`.

```cpp
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

## <a name="op_star"></a>  back_insert_iterator::Operator\*

Operátor přesměrování používaný k implementaci výrazu výstupního iterátoru \* *můžu* = *x*.

```cpp
back_insert_iterator<Container>& operator*();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na element vloží zádi kontejneru.

### <a name="remarks"></a>Poznámky

Používaný k implementaci výrazu výstupního iterátoru  **\*Iter** = **hodnota**. Pokud **Iter** je iterátor adresující prvek v sekvenci, pak  **\*Iter** = **hodnotu** nahrazuje tento element s hodnotou a ne Změňte celkový počet prvků v sekvenci.

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

## <a name="op_add_add"></a>  back_insert_iterator::Operator ++

Zvýší `back_insert_iterator` do následujícího umístění, do kterého mohou být uloženy hodnotu.

```cpp
back_insert_iterator<Container>& operator++();
back_insert_iterator<Container> operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

A `back_insert_iterator` adresování další umístění, do kterého mohou být uloženy hodnotu.

### <a name="remarks"></a>Poznámky

Operátory preincrementation a postincrementation vrací stejný výsledek.

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

## <a name="op_eq"></a>  back_insert_iterator::Operator =

Připojí nebo vložení hodnoty do back-endu kontejneru.

```cpp
back_insert_iterator<Container>& operator=(typename Container::const_reference val);
back_insert_iterator<Container>& operator=(typename Container::value_type&& val);
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Hodnota má být vložen do kontejneru.

### <a name="return-value"></a>Návratová hodnota

Odkaz na poslední prvek vložený zádi kontejneru.

### <a name="remarks"></a>Poznámky

První členský operátor vyhodnotí `Container.push_back( val)`,

Vrátí `*this`. Vyhodnotí se druhý členský operátor

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

## <a name="reference"></a>  back_insert_iterator::Reference

Typ, který poskytuje odkaz pro `back_insert_iterator`.

```cpp
typedef typename Container::reference reference;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje odkaz na element sekvenci řízené přiřazeným kontejnerem.

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

## <a name="see-also"></a>Viz také:

[\<iterator>](../standard-library/iterator.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
