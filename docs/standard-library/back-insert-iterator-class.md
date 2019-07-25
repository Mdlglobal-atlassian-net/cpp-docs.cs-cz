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
ms.openlocfilehash: d8f48b1f714697aff63a4ee658a69fce6dab8041
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459526"
---
# <a name="backinsertiterator-class"></a>back_insert_iterator – třída

Popisuje adaptér iterátoru, který splňuje požadavky výstupního iterátoru. Vloží, spíše než přepíše, prvky do zadní části sekvence a poskytne tak sémantiku, která se liší od sémantiky přepsání poskytnuté iterátory kontejnerů sekvence jazyka C++. `back_insert_iterator` Třída je založena na typu kontejneru.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Container>
class back_insert_iterator;
```

### <a name="parameters"></a>Parametry

*Vnitřního*\
Typ kontejneru na pozadí, které prvky mají být vloženy `back_insert_iterator`.

## <a name="remarks"></a>Poznámky

Kontejner musí splňovat požadavky pro sekvenci vložení do zadní části, je-li možné vložit prvky na konec sekvence v amortizovaném konstantním času. C++Standardní kontejnery sekvence knihovny definované třídou [deque](../standard-library/deque-class.md), třída [seznamu](../standard-library/list-class.md) a [Třída Vector](../standard-library/vector-class.md) poskytují potřebnou `push_back` členskou funkci a splňují tyto požadavky. Tyto tři kontejnery i řetězce můžou být přizpůsobené pro použití s `back_insert_iterator`. Objekt `back_insert_iterator` musí být vždy inicializován s jeho kontejnerem.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[back_insert_iterator](#back_insert_iterator)|Vytvoří objekt `back_insert_iterator` , který vloží prvky za poslední prvek v kontejneru.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[container_type](#container_type)|Typ, který poskytuje kontejner pro `back_insert_iterator`.|
|[Referenční dokumentace](#reference)|Typ, který poskytuje odkaz pro `back_insert_iterator`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[podnikatel](#op_star)|Operátor přesměrování \* používaný k implementaci výrazu `i`  =  `x` výstupního iterátoru pro zpětné vložení.|
|[operator + + – operátor](#op_add_add)|`back_insert_iterator` Zvýší na další místo, do kterého může být hodnota uložená.|
|[operátor =](#op_eq)|Operátor přiřazení \* používaný k implementaci výrazu `i`  =  `x` výstupního iterátoru pro zpětné vložení.|

## <a name="requirements"></a>Požadavky

**Záhlaví**: \<iterátor >

**Obor názvů:** std

## <a name="back_insert_iterator"></a>back_insert_iterator::back_insert_iterator

Vytvoří objekt `back_insert_iterator` , který vloží prvky za poslední prvek v kontejneru.

```cpp
explicit back_insert_iterator(Container& _Cont);
```

### <a name="parameters"></a>Parametry

*_Cont*\
Kontejner, do kterého `back_insert_iterator` má být vložen element.

### <a name="return-value"></a>Návratová hodnota

`back_insert_iterator` Pro kontejner parametru.

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

## <a name="container_type"></a>back_insert_iterator::container_type

Typ, který poskytuje kontejner pro `back_insert_iterator`.

```cpp
typedef Container
container_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro **kontejner**parametrů šablony.

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

## <a name="op_star"></a>back_insert_iterator:: operator\*

Operátor přesměrování používaný k \* implementaci výrazu výstupního iterátoru *i* = *x*.

```cpp
back_insert_iterator<Container>& operator*();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na element vložený na pozadí kontejneru.

### <a name="remarks"></a>Poznámky

Slouží k implementaci**hodnoty**  **\*ITER** = výrazu výstupního iterátoru. Pokud **ITER** je iterátor, který adresuje prvek v sekvenci, pak  **\*** **hodnota** ITER = nahradí tento prvek hodnotou a nezmění celkový počet prvků v sekvenci.

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

## <a name="op_add_add"></a>back_insert_iterator:: operator + +

`back_insert_iterator` Zvýší na další místo, do kterého může být hodnota uložená.

```cpp
back_insert_iterator<Container>& operator++();
back_insert_iterator<Container> operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

`back_insert_iterator` Adresování dalšího umístění, do kterého může být uložena hodnota.

### <a name="remarks"></a>Poznámky

Jak předpřírůstkový operátor, tak operátory postincrementation vrací stejný výsledek.

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

## <a name="op_eq"></a>back_insert_iterator:: operator =

Připojí nebo vloží hodnotu do back-endu kontejneru.

```cpp
back_insert_iterator<Container>& operator=(typename Container::const_reference val);
back_insert_iterator<Container>& operator=(typename Container::value_type&& val);
```

### <a name="parameters"></a>Parametry

*počítává*\
Hodnota, která má být vložena do kontejneru.

### <a name="return-value"></a>Návratová hodnota

Odkaz na poslední prvek vložený na pozadí kontejneru.

### <a name="remarks"></a>Poznámky

První operátor členu vyhodnotí `Container.push_back( val)`,

pak vrátí `*this`. Druhý členský operátor vyhodnocuje

`container->push_back((typename Container::value_type&&)val)`,

pak vrátí `*this`.

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

## <a name="reference"></a>back_insert_iterator:: Reference

Typ, který poskytuje odkaz pro `back_insert_iterator`.

```cpp
typedef typename Container::reference reference;
```

### <a name="remarks"></a>Poznámky

Typ popisuje odkaz na prvek sekvence řízené přidruženým kontejnerem.

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

[\<iterátor >](../standard-library/iterator.md)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
