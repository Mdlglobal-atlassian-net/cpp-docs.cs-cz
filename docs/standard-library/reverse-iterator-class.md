---
title: reverse_iterator – třída
ms.date: 03/27/2019
f1_keywords:
- xutility/std::reverse_iterator
- iterator/std::reverse_iterator::difference_type
- iterator/std::reverse_iterator::iterator_type
- iterator/std::reverse_iterator::pointer
- iterator/std::reverse_iterator::reference
- iterator/std::reverse_iterator::base
- iterator/std::reverse_iterator::operator_star
helpviewer_keywords:
- std::reverse_iterator [C++]
- std::reverse_iterator [C++], difference_type
- std::reverse_iterator [C++], iterator_type
- std::reverse_iterator [C++], pointer
- std::reverse_iterator [C++], reference
- std::reverse_iterator [C++], base
- std::reverse_iterator [C++], operator_star
ms.assetid: c0b34d04-ae9a-4999-9aff-28b313897ffa
ms.openlocfilehash: 882d0f7f4930e9d809098a29384a962d0aa8f4ea
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373440"
---
# <a name="reverse_iterator-class"></a>reverse_iterator – třída

Šablona třídy je adaptér iterátoru, který popisuje objekt zpětného iterátoru, který se chová jako náhodný přístup nebo obousměrný iterátor, pouze v opačném směru. Umožňuje zpětné procházení rozsahu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class RandomIterator>
class reverse_iterator
```

### <a name="parameters"></a>Parametry

RandomIterator Typ, který představuje iterátor, který má být přizpůsoben pro provoz v opačném směru.

## <a name="remarks"></a>Poznámky

Existující kontejnery standardní knihovny `reverse_iterator` `const_reverse_iterator` jazyka C++ `rbegin` `rend` také definovat a typy a mají členské funkce a které vracejí zpětné iterátory. Tyto iterátory mají sémantiku přepisu. Adaptér `reverse_iterator` doplňuje tuto funkci, protože nabízí sémantiku vložky a lze jej také použít s datovými proudy.

`reverse_iterator` To, co vyžaduje obousměrný iterátor, nesmí volat `operator+=`žádnou z členských funkcí , `operator+`, `operator-=`, `operator-`nebo `operator[]`, které lze použít pouze s iterátory s náhodným přístupem.

Rozsah iterátoru je [*první*, *poslední*), kde čtvercová závorka vlevo označuje zahrnutí *první* a závorky na pravé straně označují zahrnutí prvků až do samotného, ale s výjimkou *samotného posledního.* Stejné prvky jsou zahrnuty v obrácené sekvenci [ **rev** - *první*, **rev** - *poslední)* tak, že pokud *poslední* je jeden-past-the-end prvek v sekvenci, pak první prvek **rev** - *první* v obrácené sekvenci odkazuje na \*(*poslední* - 1). Identita, která spojuje všechny obrácené iterátory s jejich základním iterátorem, je:

&\***(reverse_iterator** ( *i* ) \*= &( *i* - 1 ).

V praxi to znamená, že v obrácené sekvenci bude iterátor reverse_iterator ukazovat na prvek o jednu pozici za prvkem (vpravo), na který iterátor ukazoval v původní sekvenci. Takže pokud iterátor řešit prvek 6 v pořadí (2, 4, 6, 8), pak `reverse_iterator` bude adresa prvek 4 v obráceném pořadí (8, 6, 4, 2).

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[reverse_iterator](#reverse_iterator)|Vytvoří výchozí `reverse_iterator` nebo `reverse_iterator` z podkladového iterátoru.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[difference_type](#difference_type)|Typ, který poskytuje rozdíl `reverse_iterator`mezi dvěma s odkazující na prvky v rámci stejného kontejneru.|
|[iterator_type](#iterator_type)|Typ, který poskytuje základní iterátor `reverse_iterator`pro .|
|[ukazatel](#pointer)|Typ, který poskytuje ukazatel na prvek `reverse_iterator`adresovaný .|
|[Odkaz](#reference)|Typ, který poskytuje odkaz na prvek `reverse_iterator`adresovaný .|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[base](#base)|Obnoví základní iterátor z `reverse_iterator`jeho .|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator_star](#op_star)|Vrátí prvek, `reverse_iterator` který adresy.|
|[operátor+](#op_add)|Přidá posun do iterátoru a `reverse_iterator` vrátí nové adresování vloženého prvku v nové pozici odsazení.|
|[operátor++](#op_add_add)|Zintáží `reverse_iterator` na další prvek.|
|[operátor+=](#op_add_eq)|Přidá zadaný posun `reverse_iterator`od .|
|[operátor-](#operator-)|Odečte posun od `reverse_iterator` a vrátí `reverse_iterator` adresování prvku v pozici odsazení.|
|[operátora--](#operator--)|Sníží `reverse_iterator` na předchozí prvek.|
|[operátor-=](#operator-_eq)|Odečte zadaný posun `reverse_iterator`od .|
|[operátor->](#op-arrow)|Vrátí ukazatel na prvek, který `reverse_iterator`je adresován rozhraním .|
|[operátor&#91;&#93;](#op_at)|Vrátí odkaz na posun prvku od prvku `reverse_iterator` adresovaného a o zadaný počet pozic.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<> iterátoru

**Obor názvů:** std

## <a name="reverse_iteratorbase"></a><a name="base"></a>reverse_iterator::základna

Obnoví základní iterátor z `reverse_iterator`jeho .

```cpp
RandomIterator base() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor základní `reverse_iterator`.

### <a name="remarks"></a>Poznámky

Identita, která se vztahuje všechny reverzní iterátory na jejich základní iterátory je:

&\*( `reverse_iterator` ( *i* ) \*= &( *i* - 1 ).

V praxi to znamená, že `reverse_iterator` v obráceném pořadí bude odkazovat na prvek o jednu pozici za (vpravo od) prvek, který iterátor odkazoval v původním pořadí. Takže pokud iterátor řešit prvek 6 v pořadí (2, 4, 6, 8), pak `reverse_iterator` bude adresa prvek 4 v obráceném pořadí (8, 6, 4, 2).

### <a name="example"></a>Příklad

```cpp
// reverse_iterator_base.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   vector <int>::iterator pos, bpos;
   pos = find ( vec.begin ( ), vec.end ( ), 6 );
   cout << "The iterator pos points to: " << *pos << "." << endl;

   typedef reverse_iterator<vector<int>::iterator>::iterator_type it_vec_int_type;

   reverse_iterator<it_vec_int_type> rpos ( pos );
   cout << "The reverse_iterator rpos points to: " << *rpos
        << "." << endl;

   bpos = rpos.base ( );
   cout << "The iterator underlying rpos is bpos & it points to: "
        << *bpos << "." << endl;
}
```

## <a name="reverse_iteratordifference_type"></a><a name="difference_type"></a>reverse_iterator::difference_type

Typ, který poskytuje rozdíl `reverse_iterator`mezi dvěma s odkazující na prvky v rámci stejného kontejneru.

```cpp
typedef typename iterator_traits<RandomIterator>::difference_type  difference_type;
```

### <a name="remarks"></a>Poznámky

Typ `reverse_iterator` rozdílu je stejný jako typ rozdílu iterátoru.

Typ je synonymem pro iterátor znak `iterator_traits` \< typename **RandomIterator**> **::pointer**.

### <a name="example"></a>Příklad

Příklad deklarace a používání `difference_type`viz [reverse_iterator::operátor&#91;&#93;.](#op_at)

## <a name="reverse_iteratoriterator_type"></a><a name="iterator_type"></a>reverse_iterator::iterator_type

Typ, který poskytuje základní iterátor `reverse_iterator`pro .

```cpp
typedef RandomIterator iterator_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro `Iterator`parametr šablony .

### <a name="example"></a>Příklad

Příklad deklarace a používání `iterator_type`viz [reverse_iterator::base.](#base)

## <a name="reverse_iteratoroperator"></a><a name="op_star"></a>reverse_iterator::operátor\*

Vrátí prvek, který reverse_iterator adresy.

```cpp
reference operator*() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota prvků, kterými se reverse_iterator.

### <a name="remarks"></a>Poznámky

Operátor se \*vrátí ( **proud** - 1).

### <a name="example"></a>Příklad

```cpp
// reverse_iterator_op_ref.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   vector <int>::iterator pos, bpos;
   pos = find ( vec.begin ( ), vec.end ( ), 6 );

   // Declare a difference type for a parameter
   // declare a reference return type
   reverse_iterator<vector<int>::iterator>::reference refpos = *pos;
   cout << "The iterator pos points to: " << refpos << "." << endl;
}
```

## <a name="reverse_iteratoroperator"></a><a name="op_add"></a>reverse_iterator::operátor+

Přidá posun do iterátoru a `reverse_iterator` vrátí nové adresování vloženého prvku v nové pozici odsazení.

```cpp
reverse_iterator<RandomIterator> operator+(difference_type Off) const;
```

### <a name="parameters"></a>Parametry

*Vypnuto*\
Posun, který má být přidán do zpětného iterátoru.

### <a name="return-value"></a>Návratová hodnota

Adresování `reverse_iterator` prvek posun.

### <a name="remarks"></a>Poznámky

Tato členská funkce může `reverse_iterator` být použita pouze v případě, že splňuje požadavky pro iterátor náhodného přístupu.

### <a name="example"></a>Příklad

```cpp
// reverse_iterator_op_add.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the first element
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( );

   cout << "The iterator rVPOS1 initially points to the first "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   vector <int>::reverse_iterator rVPOS2 =rVPOS1 + 2; // offset added
   cout << "After the +2 offset, the iterator rVPOS2 points\n"
        << " to the 3rd element in the reversed sequence: "
        << *rVPOS2 << "." << endl;
}
```

```Output
The vector vec is: ( 2 4 6 8 10 ).
The vector vec reversed is: ( 10 8 6 4 2 ).
The iterator rVPOS1 initially points to the first element
in the reversed sequence: 10.
After the +2 offset, the iterator rVPOS2 points
to the 3rd element in the reversed sequence: 6.
```

## <a name="reverse_iteratoroperator"></a><a name="op_add_add"></a>reverse_iterator::operátor++

Zintáží reverse_iterator k předchozímu prvku.

```cpp
reverse_iterator<RandomIterator>& operator++();
reverse_iterator<RandomIterator> operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

První operátor vrátí preincremented `reverse_iterator` a druhý, operátor postincrement, vrátí kopii `reverse_iterator`přírůstku .

### <a name="remarks"></a>Poznámky

Tato členská funkce může `reverse_iterator` být použita pouze v případě, že splňuje požadavky na obousměrný iterátor.

### <a name="example"></a>Příklad

```cpp
// reverse_iterator_op_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i - 1 );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the last element
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin( );

   cout << "The iterator rVPOS1 initially points to the first "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   rVPOS1++;  // postincrement, preincrement: ++rVPSO1

   cout << "After incrementing, the iterator rVPOS1 points\n"
        << " to the second element in the reversed sequence: "
        << *rVPOS1 << "." << endl;
}
```

```Output
The vector vec is: ( 1 3 5 7 9 ).
The vector vec reversed is: ( 9 7 5 3 1 ).
The iterator rVPOS1 initially points to the first element
in the reversed sequence: 9.
After incrementing, the iterator rVPOS1 points
to the second element in the reversed sequence: 7.
```

## <a name="reverse_iteratoroperator"></a><a name="op_add_eq"></a>reverse_iterator::operátor+=

Přidá zadaný posun od reverse_iterator.

```cpp
reverse_iterator<RandomIterator>& operator+=(difference_type Off);
```

### <a name="parameters"></a>Parametry

*Vypnuto*\
Posun, o který chcete posít iterátor.

### <a name="return-value"></a>Návratová hodnota

Odkaz na prvek, na `reverse_iterator`který se vztahuje rozhraní .

### <a name="example"></a>Příklad

```cpp
// reverse_iterator_op_addoff.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the last element
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( );

   cout << "The iterator rVPOS1 initially points to the first "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   rVPOS1+=2;   // addition of an offset
   cout << "After the +2 offset, the iterator rVPOS1 now points\n"
        << " to the third element in the reversed sequence: "
        << *rVPOS1 << "." << endl;
}
```

```Output
The vector vec is: ( 2 4 6 8 10 ).
The vector vec reversed is: ( 10 8 6 4 2 ).
The iterator rVPOS1 initially points to the first element
in the reversed sequence: 10.
After the +2 offset, the iterator rVPOS1 now points
to the third element in the reversed sequence: 6.
```

## <a name="reverse_iteratoroperator-"></a><a name="operator-"></a>reverse_iterator::operátor-

Odečte posun od `reverse_iterator` a vrátí `reverse_iterator` adresování prvku v pozici odsazení.

```cpp
reverse_iterator<RandomIterator> operator-(difference_type Off) const;
```

### <a name="parameters"></a>Parametry

*Vypnuto*\
Posun, který má být odečten od reverse_iterator.

### <a name="return-value"></a>Návratová hodnota

Adresování `reverse_iterator` prvek posun.

### <a name="remarks"></a>Poznámky

Tato členská funkce může `reverse_iterator` být použita pouze v případě, že splňuje požadavky pro iterátor náhodného přístupu.

### <a name="example"></a>Příklad

```cpp
// reverse_iterator_op_sub.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 3 * i );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the first element
   vector <int>::reverse_iterator rVPOS1 = vec.rend ( ) - 1;

   cout << "The iterator rVPOS1 initially points to the last "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   vector <int>::reverse_iterator rVPOS2 =rVPOS1 - 2; // offset subtracted
   cout << "After the -2 offset, the iterator rVPOS2 points\n"
        << " to the 2nd element from the last in the reversed sequence: "
        << *rVPOS2 << "." << endl;
}
```

```Output
The vector vec is: ( 3 6 9 12 15 ).
The vector vec reversed is: ( 15 12 9 6 3 ).
The iterator rVPOS1 initially points to the last element
in the reversed sequence: 3.
After the -2 offset, the iterator rVPOS2 points
to the 2nd element from the last in the reversed sequence: 9.
```

## <a name="reverse_iteratoroperator--"></a><a name="operator--"></a>reverse_iterator::operátor--

Sníží reverse_iterator předchozí prvek.

```cpp
reverse_iterator<RandomIterator>& operator--();
reverse_iterator<RandomIterator> operator--(int);
```

### <a name="return-value"></a>Návratová hodnota

První operátor vrátí predecremented `reverse_iterator` a druhý, operátor postdecrement, vrátí kopii `reverse_iterator`dekreed .

### <a name="remarks"></a>Poznámky

Tato členská funkce může `reverse_iterator` být použita pouze v případě, že splňuje požadavky na obousměrný iterátor.

### <a name="example"></a>Příklad

```cpp
// reverse_iterator_op_decr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i - 1 );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the first element
   vector <int>::reverse_iterator rVPOS1 = vec.rend ( ) - 1;

   cout << "The iterator rVPOS1 initially points to the last "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;
   rVPOS1--;  // postdecrement, predecrement: --rVPSO1

   cout << "After the decrement, the iterator rVPOS1 points\n"
        << " to the next-to-last element in the reversed sequence: "
        << *rVPOS1 << "." << endl;
}
```

```Output
The vector vec is: ( 1 3 5 7 9 ).
The vector vec reversed is: ( 9 7 5 3 1 ).
The iterator rVPOS1 initially points to the last element
in the reversed sequence: 1.
After the decrement, the iterator rVPOS1 points
to the next-to-last element in the reversed sequence: 3.
```

## <a name="reverse_iteratoroperator-"></a><a name="operator-_eq"></a>reverse_iterator::operátor-=

Odečte zadaný posun `reverse_iterator`od .

```cpp
reverse_iterator<RandomIterator>& operator-=(difference_type Off);
```

### <a name="parameters"></a>Parametry

*Vypnuto*\
Posun, který má být `reverse_iterator`odečten od .

### <a name="remarks"></a>Poznámky

Tato členská funkce může `reverse_iterator` být použita pouze v případě, že splňuje požadavky pro iterátor náhodného přístupu.

Operátor vyhodnotí **aktuální** + *Off* a vrátí ** \*toto**.

### <a name="example"></a>Příklad

```cpp
// reverse_iterator_op_suboff.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 3 * i );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the first element
   vector <int>::reverse_iterator rVPOS1 = vec.rend ( ) - 1;

   cout << "The iterator rVPOS1 initially points to the last "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   rVPOS1-=2;      // Subtraction of an offset
   cout << "After the -2 offset, the iterator rVPOS1 now points\n"
        << " to the 2nd element from the last in the reversed sequence: "
        << *rVPOS1 << "." << endl;
}
```

```Output
The vector vec is: ( 3 6 9 12 15 ).
The vector vec reversed is: ( 15 12 9 6 3 ).
The iterator rVPOS1 initially points to the last element
in the reversed sequence: 3.
After the -2 offset, the iterator rVPOS1 now points
to the 2nd element from the last in the reversed sequence: 9.
```

## <a name="reverse_iteratoroperator-gt"></a><a name="op-arrow"></a>reverse_iterator::operátor-&gt;

Vrátí ukazatel na prvek, který `reverse_iterator`je adresován rozhraním .

```cpp
pointer operator->() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na prvek, který `reverse_iterator`je adresován rozhraním .

### <a name="remarks"></a>Poznámky

Operátor vrátí ** & \* \*toto**.

### <a name="example"></a>Příklad

```cpp
// reverse_iterator_ptrto.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <utility>
#include <iostream>

int main( )
{
   using namespace std;

   typedef vector<pair<int,int> > pVector;
   pVector vec;
   vec.push_back(pVector::value_type(1,2));
   vec.push_back(pVector::value_type(3,4));
   vec.push_back(pVector::value_type(5,6));

   pVector::iterator pvIter;
   cout << "The vector vec of integer pairs is:\n( ";
   for ( pvIter = vec.begin ( ) ; pvIter != vec.end ( ); pvIter++)
      cout << "( " << pvIter -> first << ", " << pvIter -> second << ") ";
   cout << ")" << endl << endl;

   pVector::reverse_iterator rpvIter;
   cout << "The vector vec reversed is:\n( ";
   for ( rpvIter = vec.rbegin( ) ; rpvIter != vec.rend( ); rpvIter++ )
      cout << "( " << rpvIter -> first << ", " << rpvIter -> second << ") ";
   cout << ")" << endl << endl;

   pVector::iterator pos = vec.begin ( );
   pos++;
   cout << "The iterator pos points to:\n( " << pos -> first << ", "
   << pos -> second << " )" << endl << endl;

   pVector::reverse_iterator rpos (pos);

   // Use operator -> with return type: why type int and not int*
   int fint = rpos -> first;
   int sint = rpos -> second;

   cout << "The reverse_iterator rpos points to:\n( " << fint << ", "
   << sint << " )" << endl;
}
```

```Output
The vector vec of integer pairs is:
( ( 1, 2) ( 3, 4) ( 5, 6) )

The vector vec reversed is:
( ( 5, 6) ( 3, 4) ( 1, 2) )

The iterator pos points to:
( 3, 4 )

The reverse_iterator rpos points to:
( 1, 2 )
```

## <a name="reverse_iteratoroperator"></a><a name="op_at"></a>reverse_iterator::operátor[]

Vrátí odkaz na posun prvku od prvku `reverse_iterator` adresovaného a o zadaný počet pozic.

```cpp
reference operator[](difference_type Off) const;
```

### <a name="parameters"></a>Parametry

*Vypnuto*\
Posun od `reverse_iterator` adresy.

### <a name="return-value"></a>Návratová hodnota

Odkaz na posun prvku.

### <a name="remarks"></a>Poznámky

Operátor vrátí <strong>\*</strong>( ** \*toto** + `Off`).

### <a name="example"></a>Příklad

```cpp
// reverse_iterator_ret_ref.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   vector <int>::iterator pos;
   pos = find ( vec.begin ( ), vec.end ( ), 8 );
   reverse_iterator<vector<int>::iterator> rpos ( pos );

   // Declare a difference type for a parameter
   reverse_iterator<vector<int>::iterator>::difference_type diff = 2;

   cout << "The iterator pos points to: " << *pos << "." << endl;
   cout << "The iterator rpos points to: " << *rpos << "." << endl;

   // Declare a reference return type & use operator[]
   reverse_iterator<vector<int>::iterator>::reference refrpos = rpos [diff];
   cout << "The iterator rpos now points to: " << refrpos << "." << endl;
}
```

```Output
The vector vec is: ( 2 4 6 8 10 ).
The vector vec reversed is: ( 10 8 6 4 2 ).
The iterator pos points to: 8.
The iterator rpos points to: 6.
The iterator rpos now points to: 2.
```

## <a name="reverse_iteratorpointer"></a><a name="pointer"></a>reverse_iterator::pointer

Typ, který poskytuje ukazatel na prvek `reverse_iterator`adresovaný .

```cpp
typedef typename iterator_traits<RandomIterator>::pointer pointer;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro iterátor znak `iterator_traits` \< typename *RandomIterator*> **::pointer**.

### <a name="example"></a>Příklad

```cpp
// reverse_iterator_pointer.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <utility>
#include <iostream>

int main( )
{
   using namespace std;

   typedef vector<pair<int,int> > pVector;
   pVector vec;
   vec.push_back( pVector::value_type( 1,2 ) );
   vec.push_back( pVector::value_type( 3,4 ) );
   vec.push_back( pVector::value_type( 5,6 ) );

   pVector::iterator pvIter;
   cout << "The vector vec of integer pairs is:\n" << "( ";
   for ( pvIter = vec.begin ( ) ; pvIter != vec.end ( ); pvIter++)
      cout << "( " << pvIter -> first << ", " << pvIter -> second << ") ";
   cout << ")" << endl;

   pVector::reverse_iterator rpvIter;
   cout << "\nThe vector vec reversed is:\n" << "( ";
   for ( rpvIter = vec.rbegin( ) ; rpvIter != vec.rend( ); rpvIter++)
      cout << "( " << rpvIter -> first << ", " << rpvIter -> second << ") ";
   cout << ")" << endl;

   pVector::iterator pos = vec.begin ( );
   pos++;
   cout << "\nThe iterator pos points to:\n"
        << "( " << pos -> first << ", "
        << pos -> second << " )" << endl;

   pVector::reverse_iterator rpos (pos);
   cout << "\nThe iterator rpos points to:\n"
        << "( " << rpos -> first << ", "
        << rpos -> second << " )" << endl;
}
```

```Output
The vector vec of integer pairs is:
( ( 1, 2) ( 3, 4) ( 5, 6) )

The vector vec reversed is:
( ( 5, 6) ( 3, 4) ( 1, 2) )

The iterator pos points to:
( 3, 4 )

The iterator rpos points to:
( 1, 2 )
```

## <a name="reverse_iteratorreference"></a><a name="reference"></a>reverse_iterator::odkaz

Typ, který poskytuje odkaz na prvek adresovaný reverse_iterator.

```cpp
typedef typename iterator_traits<RandomIterator>::reference reference;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro iterátor znak `iterator_traits` \< typename *RandomIterator*> **::reference**.

### <a name="example"></a>Příklad

Viz [reverse_iterator::operátor&#91;&#93;](#op_at) nebo [reverse_iterator::operator*](#op_star) příklady, `reference`jak deklarovat a používat .

## <a name="reverse_iteratorreverse_iterator"></a><a name="reverse_iterator"></a>reverse_iterator::reverse_iterator

Vytvoří výchozí `reverse_iterator` nebo `reverse_iterator` z podkladového iterátoru.

```cpp
reverse_iterator();
explicit reverse_iterator(RandomIterator right);

template <class Type>
reverse_iterator(const reverse_iterator<Type>& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Iterátor, který má být přizpůsoben `reverse_iterator`.

### <a name="return-value"></a>Návratová hodnota

Výchozí `reverse_iterator` nebo `reverse_iterator` přizpůsobení podkladového iterátoru.

### <a name="remarks"></a>Poznámky

Identita, která spojuje všechny obrácené iterátory s jejich základním iterátorem, je:

&\*( `reverse_iterator` ( *i* ) \*= &( *i* - 1 ).

V praxi to znamená, že v obrácené sekvenci bude iterátor reverse_iterator ukazovat na prvek o jednu pozici za prvkem (vpravo), na který iterátor ukazoval v původní sekvenci. Takže pokud iterátor řešit prvek 6 v pořadí (2, 4, 6, 8), pak `reverse_iterator` bude adresa prvek 4 v obráceném pořadí (8, 6, 4, 2).

### <a name="example"></a>Příklad

```cpp
// reverse_iterator_reverse_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   vector <int>::iterator pos;
   pos = find ( vec.begin ( ), vec.end ( ), 4 );
   cout << "The iterator pos = " << *pos << "." << endl;

   vector <int>::reverse_iterator rpos ( pos );
   cout << "The reverse_iterator rpos = " << *rpos
        << "." << endl;
}
```

## <a name="see-also"></a>Viz také

[\<>iterátoru](../standard-library/iterator.md)\
[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referenční příručka standardní knihovny jazyka C++](../standard-library/cpp-standard-library-reference.md)
