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
ms.openlocfilehash: aadc5cffd6f88de175ff04f50d6572e38ba05533
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72686574"
---
# <a name="reverse_iterator-class"></a>reverse_iterator – třída

Šablona třídy je adaptér iterátoru, který popisuje objekt reverzního iterátoru, který se chová jako náhodný přístup nebo obousměrný iterátor, pouze v opačném případě. Umožňuje zpětné procházení rozsahu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class RandomIterator>
class reverse_iterator
```

### <a name="parameters"></a>Parametry

RandomIterator typ, který představuje iterátor, který má být přizpůsobený, aby fungoval v opačném případě.

## <a name="remarks"></a>Poznámky

Existující C++ kontejnery standardní knihovny také definují `reverse_iterator` a `const_reverse_iterator` typy a mají členské funkce `rbegin` a `rend`, které vracejí reverzní iterátory. Tyto iterátory mají sémantiku přepisu. @No__t_0 adaptér doplňuje tuto funkci, protože nabízí sémantiku vkládání a lze ji také použít s datovými proudy.

@No__t_0, která vyžaduje obousměrný iterátor, nesmí volat žádné členské funkce `operator+=`, `operator+`, `operator-=`, `operator-` nebo `operator[]`, které lze použít pouze s iterátory s náhodným přístupem.

Rozsah iterátoru je [*First*, *Last*), kde čtvercová závorka vlevo označuje zahrnutí *prvního* a závorky na pravé straně značí zahrnutí prvků až do *posledního* samotného. Stejné prvky jsou zahrnuté do reverzní sekvence [ **rev**  - *first*, **REV**  - *Last*), takže pokud *Poslední* je prvek, který je v sekvenci jednou po konci, pak první element **REV**  -  *první* v obrácené sekvenci ukazuje na 0 (*posledních* -1). Identita, která spojuje všechny obrácené iterátory s jejich základním iterátorem, je:

& \* ( **reverse_iterator** ( *i* )) = = & \* ( *i* -1).

V praxi to znamená, že v obrácené sekvenci bude iterátor reverse_iterator ukazovat na prvek o jednu pozici za prvkem (vpravo), na který iterátor ukazoval v původní sekvenci. Takže pokud iterátor adresující prvek 6 v sekvenci (2, 4, 6, 8), pak `reverse_iterator` adresuje prvek 4 v obrácené sekvenci (8, 6, 4, 2).

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[reverse_iterator](#reverse_iterator)|Vytvoří výchozí `reverse_iterator` nebo `reverse_iterator` ze základního iterátoru.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[difference_type](#difference_type)|Typ, který poskytuje rozdíl mezi dvěma `reverse_iterator`s odkazujícími na prvky v rámci stejného kontejneru.|
|[iterator_type](#iterator_type)|Typ, který poskytuje základní iterátor pro `reverse_iterator`.|
|[ukazatele](#pointer)|Typ, který poskytuje ukazatel na prvek řešený `reverse_iterator`.|
|[odkaz](#reference)|Typ, který poskytuje odkaz na prvek řešený `reverse_iterator`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[base](#base)|Obnoví základní iterátor z jeho `reverse_iterator`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator_star](#op_star)|Vrátí prvek, který `reverse_iterator` adres.|
|[operator + – operátor](#op_add)|Přidá posun k iterátoru a vrátí nový `reverse_iterator` adresování vloženého prvku na nové pozici posunu.|
|[operator + + – operátor](#op_add_add)|Zvýší `reverse_iterator` na další prvek.|
|[operator + = – operátor](#op_add_eq)|Přidá zadaný posun z `reverse_iterator`.|
|[podnikatel](#operator-)|Odečte posun od `reverse_iterator` a vrátí `reverse_iterator` adresující element na pozici posunu.|
|[--– operátor](#operator--)|Sníží `reverse_iterator` na předchozí prvek.|
|[-= – operátor](#operator-_eq)|Odečte zadaný posun od `reverse_iterator`.|
|[operátor->](#op-arrow)|Vrátí ukazatel na prvek řešený `reverse_iterator`.|
|[podnikatel&#91;&#93;](#op_at)|Vrátí odkaz na posun prvku z prvku adresovaný `reverse_iterator` zadaným počtem pozic.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<iterator >

**Obor názvů:** std

## <a name="base"></a>reverse_iterator:: Base

Obnoví základní iterátor z jeho `reverse_iterator`.

```cpp
RandomIterator base() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor podkladové `reverse_iterator`.

### <a name="remarks"></a>Poznámky

Identita, která se vztahuje na všechny reverzní iterátory na své základní iterátory, je:

& \* (`reverse_iterator` ( *i* )) = = & \* ( *i* -1).

V praxi to znamená, že v obrácené sekvenci `reverse_iterator` odkaz na element, který překračuje (napravo od) prvku, na který iterátor odkazoval v původní sekvenci. Takže pokud iterátor adresující prvek 6 v sekvenci (2, 4, 6, 8), pak `reverse_iterator` adresuje prvek 4 v obrácené sekvenci (8, 6, 4, 2).

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

## <a name="difference_type"></a>reverse_iterator::d ifference_type

Typ, který poskytuje rozdíl mezi dvěma `reverse_iterator`s odkazujícími na prvky v rámci stejného kontejneru.

```cpp
typedef typename iterator_traits<RandomIterator>::difference_type  difference_type;
```

### <a name="remarks"></a>Poznámky

Typ rozdílu `reverse_iterator` je stejný jako typ rozdílu iterátoru.

Typ je synonymum pro vlastnost TypeName typu iterátor `iterator_traits` \< **RandomIterator** >  **::p ointer**.

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat `difference_type`, naleznete v tématu [reverse_iterator:: operator&#91; ](#op_at) .

## <a name="iterator_type"></a>reverse_iterator::iterator_type

Typ, který poskytuje základní iterátor pro `reverse_iterator`.

```cpp
typedef RandomIterator iterator_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `Iterator`.

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat `iterator_type`, naleznete v tématu [reverse_iterator:: Base](#base) .

## <a name="op_star"></a>reverse_iterator:: operator \*

Vrátí prvek, který je reverse_iterator adresami.

```cpp
reference operator*() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota prvků, které jsou adresovány reverse_iterator.

### <a name="remarks"></a>Poznámky

Operátor vrátí \* ( **Current** -1).

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

## <a name="op_add"></a>reverse_iterator:: operator + – operátor

Přidá posun k iterátoru a vrátí nový `reverse_iterator` adresování vloženého prvku na nové pozici posunu.

```cpp
reverse_iterator<RandomIterator> operator+(difference_type Off) const;
```

### <a name="parameters"></a>Parametry

*Vypnuto* \
Posun, který má být přidán do reverzního iterátoru.

### <a name="return-value"></a>Návratová hodnota

@No__t_0 adresování posunutí elementu.

### <a name="remarks"></a>Poznámky

Tato členská funkce se dá použít jenom v případě, že `reverse_iterator` splňuje požadavky pro iterátor náhodného přístupu.

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

## <a name="op_add_add"></a>reverse_iterator:: operator + +

Zvýší reverse_iterator na předchozí prvek.

```cpp
reverse_iterator<RandomIterator>& operator++();
reverse_iterator<RandomIterator> operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

První operátor vrátí předpřírůstkové `reverse_iterator` a druhý postinkrement operátor vrátí kopii přírůstku `reverse_iterator`.

### <a name="remarks"></a>Poznámky

Tato členská funkce se dá použít jenom v případě, že `reverse_iterator` splňuje požadavky pro obousměrný iterátor.

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

## <a name="op_add_eq"></a>reverse_iterator:: operator + =

Přidá zadaný posun z reverse_iterator.

```cpp
reverse_iterator<RandomIterator>& operator+=(difference_type Off);
```

### <a name="parameters"></a>Parametry

*Vypnuto* \
Posun, o který se má zvýšit iterátor

### <a name="return-value"></a>Návratová hodnota

Odkaz na prvek řešený `reverse_iterator`.

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

## <a name="operator-"></a>reverse_iterator:: operator-

Odečte posun od `reverse_iterator` a vrátí `reverse_iterator` adresující element na pozici posunu.

```cpp
reverse_iterator<RandomIterator> operator-(difference_type Off) const;
```

### <a name="parameters"></a>Parametry

*Vypnuto* \
Posun, který má být odečten od reverse_iterator.

### <a name="return-value"></a>Návratová hodnota

@No__t_0 adresování posunutí elementu.

### <a name="remarks"></a>Poznámky

Tato členská funkce se dá použít jenom v případě, že `reverse_iterator` splňuje požadavky pro iterátor náhodného přístupu.

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

## <a name="operator--"></a>reverse_iterator:: operator--

Sníží reverse_iterator na předchozí prvek.

```cpp
reverse_iterator<RandomIterator>& operator--();
reverse_iterator<RandomIterator> operator--(int);
```

### <a name="return-value"></a>Návratová hodnota

První operátor vrátí `reverse_iterator` a druhý operátor postdekrement a vrátí kopii sníženého `reverse_iterator`.

### <a name="remarks"></a>Poznámky

Tato členská funkce se dá použít jenom v případě, že `reverse_iterator` splňuje požadavky pro obousměrný iterátor.

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

## <a name="operator-_eq"></a>reverse_iterator:: operator-=

Odečte zadaný posun od `reverse_iterator`.

```cpp
reverse_iterator<RandomIterator>& operator-=(difference_type Off);
```

### <a name="parameters"></a>Parametry

*Vypnuto* \
Posun, který má být odečten od `reverse_iterator`.

### <a name="remarks"></a>Poznámky

Tato členská funkce se dá použít jenom v případě, že `reverse_iterator` splňuje požadavky pro iterátor náhodného přístupu.

Operátor vyhodnocuje **aktuální** *+ _.* pak vrátí **\*this**.

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

## <a name="op-arrow"></a>reverse_iterator:: operator-&gt;

Vrátí ukazatel na prvek řešený `reverse_iterator`.

```cpp
pointer operator->() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na prvek řešený `reverse_iterator`.

### <a name="remarks"></a>Poznámky

Operátor vrací **& \* \*this**.

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

## <a name="op_at"></a>reverse_iterator:: operator [] – operátor

Vrátí odkaz na posun prvku z prvku adresovaný `reverse_iterator` zadaným počtem pozic.

```cpp
reference operator[](difference_type Off) const;
```

### <a name="parameters"></a>Parametry

*Vypnuto* \
Posun od `reverse_iterator` adresy.

### <a name="return-value"></a>Návratová hodnota

Odkaz na posunutí elementu.

### <a name="remarks"></a>Poznámky

Operátor vrátí <strong>\*</strong>( **\*this**  +  `Off`).

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

## <a name="pointer"></a>reverse_iterator::p ointer

Typ, který poskytuje ukazatel na prvek řešený `reverse_iterator`.

```cpp
typedef typename iterator_traits<RandomIterator>::pointer pointer;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro vlastnost TypeName typu iterátor `iterator_traits` \< *RandomIterator* >  **::p ointer**.

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

## <a name="reference"></a>reverse_iterator:: Reference

Typ, který poskytuje odkaz na prvek řešený objektem reverse_iterator.

```cpp
typedef typename iterator_traits<RandomIterator>::reference reference;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro vlastnost TypeName typu iterátoru `iterator_traits` \< *RandomIterator* >  **:: Reference**.

### <a name="example"></a>Příklad

Příklady, jak deklarovat a používat `reference`, naleznete v tématu [reverse_iterator:: operator&#91; ](#op_at) nebo [reverse_iterator:: operator *](#op_star) .

## <a name="reverse_iterator"></a>reverse_iterator::reverse_iterator

Vytvoří výchozí `reverse_iterator` nebo `reverse_iterator` ze základního iterátoru.

```cpp
reverse_iterator();
explicit reverse_iterator(RandomIterator right);

template <class Type>
reverse_iterator(const reverse_iterator<Type>& right);
```

### <a name="parameters"></a>Parametry

*pravé* \
Iterátor, který má být přizpůsoben `reverse_iterator`.

### <a name="return-value"></a>Návratová hodnota

Výchozí `reverse_iterator` nebo `reverse_iterator` přizpůsobování podkladového iterátoru.

### <a name="remarks"></a>Poznámky

Identita, která spojuje všechny obrácené iterátory s jejich základním iterátorem, je:

& \* (`reverse_iterator` ( *i* )) = = & \* ( *i* -1).

V praxi to znamená, že v obrácené sekvenci bude iterátor reverse_iterator ukazovat na prvek o jednu pozici za prvkem (vpravo), na který iterátor ukazoval v původní sekvenci. Takže pokud iterátor adresující prvek 6 v sekvenci (2, 4, 6, 8), pak `reverse_iterator` adresuje prvek 4 v obrácené sekvenci (8, 6, 4, 2).

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

## <a name="see-also"></a>Viz také:

[\<iterator >](../standard-library/iterator.md) \
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md) \
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
