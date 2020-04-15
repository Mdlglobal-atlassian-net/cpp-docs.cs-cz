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
ms.openlocfilehash: c3bbb2ec8ce9a09dd17c4744a80913f95d85bd00
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376913"
---
# <a name="back_insert_iterator-class"></a>back_insert_iterator – třída

Popisuje adaptér iterátoru, který splňuje požadavky výstupního iterátoru. Vloží, spíše než přepíše, prvky do zadní části sekvence a poskytne tak sémantiku, která se liší od sémantiky přepsání poskytnuté iterátory kontejnerů sekvence jazyka C++. Třída `back_insert_iterator` je templatized na typu kontejneru.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Container>
class back_insert_iterator;
```

### <a name="parameters"></a>Parametry

*Kontejner*\
Typ kontejneru, do kterého zadní části prvky `back_insert_iterator`mají být vloženy .

## <a name="remarks"></a>Poznámky

Kontejner musí splňovat požadavky pro sekvenci vložení do zadní části, je-li možné vložit prvky na konec sekvence v amortizovaném konstantním času. C++ Standardní knihovna sekvence kontejnery definované [deque Class](../standard-library/deque-class.md), `push_back` seznam [třídy](../standard-library/list-class.md) a [vektorové třídy](../standard-library/vector-class.md) poskytují potřebnou členské funkce a splňují tyto požadavky. Tyto tři nádoby, stejně jako řetězce `back_insert_iterator`mohou být přizpůsobeny pro použití s. A `back_insert_iterator` musí být vždy inicializována s jeho kontejnerem.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[back_insert_iterator](#back_insert_iterator)|`back_insert_iterator` Konstrukce, která vloží prvky za poslední prvek v kontejneru.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[container_type](#container_type)|Typ, který poskytuje kontejner `back_insert_iterator`pro .|
|[Odkaz](#reference)|Typ, který poskytuje odkaz `back_insert_iterator`na .|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor*](#op_star)|Dereferencing operátor slouží k implementaci výstupního \* `i`  =  `x` iterátoru výraz pro zpět vložení.|
|[operátor++](#op_add_add)|Přírůstky `back_insert_iterator` do dalšího umístění, do kterého může být uložena hodnota.|
|[operátor =](#op_eq)|Operátor přiřazení použitý k implementaci výstupního \* `i`  =  `x` výrazu iterátoru pro zpětný vložení.|

## <a name="requirements"></a>Požadavky

**Záhlaví** \<: iterátor>

**Obor názvů:** std

## <a name="back_insert_iteratorback_insert_iterator"></a><a name="back_insert_iterator"></a>back_insert_iterator::back_insert_iterator

`back_insert_iterator` Konstrukce, která vloží prvky za poslední prvek v kontejneru.

```cpp
explicit back_insert_iterator(Container& _Cont);
```

### <a name="parameters"></a>Parametry

*_Cont*\
Kontejner, který `back_insert_iterator` je vložit prvek do.

### <a name="return-value"></a>Návratová hodnota

A `back_insert_iterator` pro kontejner parametrů.

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

## <a name="back_insert_iteratorcontainer_type"></a><a name="container_type"></a>back_insert_iterator::container_type

Typ, který poskytuje kontejner `back_insert_iterator`pro .

```cpp
typedef Container
container_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro parametr šablony **Container**.

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

## <a name="back_insert_iteratoroperator"></a><a name="op_star"></a>back_insert_iterator::operátor\*

Dereferencing operátor slouží k implementaci výstupního \* iterátoru výraz *i* = *x*.

```cpp
back_insert_iterator<Container>& operator*();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na prvek vložený na zadní straně kontejneru.

### <a name="remarks"></a>Poznámky

Slouží k implementaci výstupního iterátorového = **výrazu** ** \*Iter**value . Pokud **Iter** je iterátor, který řeší prvek v sekvenci, pak ** \*Iter** = **hodnota** nahradí tento prvek s hodnotou a nezmění celkový počet prvků v pořadí.

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

## <a name="back_insert_iteratoroperator"></a><a name="op_add_add"></a>back_insert_iterator::operátor++

Přírůstky `back_insert_iterator` do dalšího umístění, do kterého může být uložena hodnota.

```cpp
back_insert_iterator<Container>& operator++();
back_insert_iterator<Container> operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

Adresování `back_insert_iterator` další umístění, do kterého může být uložena hodnota.

### <a name="remarks"></a>Poznámky

Preincrementation a postincrementation operátory vrátit stejný výsledek.

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

## <a name="back_insert_iteratoroperator"></a><a name="op_eq"></a>back_insert_iterator::operátor=

Připojí nebo odešle hodnotu na zadní konec kontejneru.

```cpp
back_insert_iterator<Container>& operator=(typename Container::const_reference val);
back_insert_iterator<Container>& operator=(typename Container::value_type&& val);
```

### <a name="parameters"></a>Parametry

*Val*\
Hodnota, která má být vložena do kontejneru.

### <a name="return-value"></a>Návratová hodnota

Odkaz na poslední prvek vložený na zadní straně kontejneru.

### <a name="remarks"></a>Poznámky

První členský operátor `Container.push_back( val)`vyhodnotí ,

pak `*this`vrátí . Druhý operátor člena vyhodnotí

`container->push_back((typename Container::value_type&&)val)`,

pak `*this`vrátí .

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

## <a name="back_insert_iteratorreference"></a><a name="reference"></a>back_insert_iterator::odkaz

Typ, který poskytuje odkaz `back_insert_iterator`na .

```cpp
typedef typename Container::reference reference;
```

### <a name="remarks"></a>Poznámky

Typ popisuje odkaz na prvek sekvence řízené přidružené kontejneru.

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

[\<>iterátoru](../standard-library/iterator.md)\
[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referenční příručka standardní knihovny jazyka C++](../standard-library/cpp-standard-library-reference.md)
