---
title: reverse_iterator – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xutility/std::reverse_iterator
- iterator/std::reverse_iterator::difference_type
- iterator/std::reverse_iterator::iterator_type
- iterator/std::reverse_iterator::pointer
- iterator/std::reverse_iterator::reference
- iterator/std::reverse_iterator::base
- iterator/std::reverse_iterator::operator_star
dev_langs:
- C++
helpviewer_keywords:
- std::reverse_iterator [C++]
- std::reverse_iterator [C++], difference_type
- std::reverse_iterator [C++], iterator_type
- std::reverse_iterator [C++], pointer
- std::reverse_iterator [C++], reference
- std::reverse_iterator [C++], base
- std::reverse_iterator [C++], operator_star
ms.assetid: c0b34d04-ae9a-4999-9aff-28b313897ffa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 30151d18126d86256c189355c19f61a694bb3267
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="reverseiterator-class"></a>reverse_iterator – třída

Třída šablony je adaptér iterátoru popisující objekt zpětného iterátoru, který se chová jako obousměrný iterátor nebo iterátor s náhodným přístupem, pouze obráceně. Umožňuje zpětné procházení rozsahu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class RandomIterator>
class reverse_iterator
```

### <a name="parameters"></a>Parametry

RandomIterator typ, který představuje iterator přizpůsobit provoz pozpátku.

## <a name="remarks"></a>Poznámky

Existující standardní knihovna C++ kontejnery také definovat `reverse_iterator` a `const_reverse_iterator` typy a mít členské funkce `rbegin` a `rend` zpětné iterátory, které vracejí. Tyto iterátory mají sémantiku přepisu. `reverse_iterator` Adaptéru doplňují tuto funkci, protože nabízí vložit sémantiku a můžete také použít s datovými proudy.

`reverse_iterator` Vyžadující obousměrného iterator nelze volat, některý člen funkce `operator+=`, `operator+`, `operator-=`, `operator-`, nebo `operator[]`, které lze použít pouze s náhodným přístupem iterátory.

Řada iterace [*první*, *poslední*), kde hranatá závorka na levé straně označuje zahrnutí *první* a označuje závorky na pravé straně zahrnutí elementy než ale s výjimkou *poslední* sám sebe. Stejné prvky jsou zahrnuty v invertovaných pořadí [ **rev** - *první*, **rev** - *poslední*), že pokud *poslední* je element jeden – minulosti--end v sekvenci, pak první prvek **rev** - *první* v invertovaných pořadí odkazuje na \*(*poslední* – 1). Identita, která spojuje všechny obrácené iterátory s jejich základním iterátorem, je:

&\*( **reverse_iterator –** ( *i* )) == &\*( *i* – 1).

V praxi to znamená, že v obrácené sekvenci bude iterátor reverse_iterator ukazovat na prvek o jednu pozici za prvkem (vpravo), na který iterátor ukazoval v původní sekvenci. Pokud iterator řešit element 6 v pořadí, (2, 4, 6, 8), pak se `reverse_iterator` bude adresa element 4 v invertovaných pořadí (8, 6, 4, 2).

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[reverse_iterator](#reverse_iterator)|Vytvoří výchozí `reverse_iterator` nebo `reverse_iterator` ze základní iterator.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[difference_type](#difference_type)|Typ, který poskytuje rozdíl mezi dvěma `reverse_iterator`s odkazy na elementy ve stejném kontejneru.|
|[iterator_type](#iterator_type)|Typ, který poskytuje základní iterator pro `reverse_iterator`.|
|[Ukazatele](#pointer)|Typ, který poskytuje ukazatel na element používala `reverse_iterator`.|
|[Referenční dokumentace](#reference)|Typ, který obsahuje odkaz na element používala `reverse_iterator`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[base](#base)|Obnoví základní iterator z jeho `reverse_iterator`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator_star](#op_star)|Vrátí prvek `reverse_iterator` adresy.|
|[operátor +](#op_add)|Přidá posun do iterovat a vrátí nové `reverse_iterator` adresování vložené element na pozici posunutí nové.|
|[Operator ++](#op_add_add)|Zvýší `reverse_iterator` na další prvek.|
|[operator+=](#op_add_eq)|Přidá zadaný posun od `reverse_iterator`.|
|[Operator –](#operator-)|Odečítá od posun vůči `reverse_iterator` a vrátí `reverse_iterator` adresování na pozici posunutí elementu.|
|[--– operátor](#operator--)|Snižuje `reverse_iterator` do předchozí elementu.|
|[-= – operátor](#operator-_eq)|Odečítá od zadaný posun od `reverse_iterator`.|
|[-> – operátor](#operator-_gt)|Vrací ukazatel na element používala `reverse_iterator`.|
|[operátor&#91;&#93;](#op_at)|Vrátí odkaz na element posun z prvku používala `reverse_iterator` o zadaný počet pozic.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<iterator >

**Namespace:** – std

## <a name="base"></a>  reverse_iterator::Base

Obnoví základní iterator z jeho `reverse_iterator`.

```cpp
RandomIterator base() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterator základní `reverse_iterator`.

### <a name="remarks"></a>Poznámky

Identity, která platí všechny zpětné iterátory pro jejich základní iterátory je:

&\*( `reverse_iterator` ( *i* )) == &\*( *i* – 1).

V praxi, to znamená, že v invertovaných pořadí `reverse_iterator` bude odkazovat na element (napravo) o jednu pozici nad rámec elementu, který měl iterator uvedené v původní pořadí. Pokud iterator řešit element 6 v pořadí, (2, 4, 6, 8), pak se `reverse_iterator` bude adresa element 4 v invertovaných pořadí (8, 6, 4, 2).

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

## <a name="difference_type"></a>  reverse_iterator::difference_type

Typ, který poskytuje rozdíl mezi dvěma `reverse_iterator`s odkazy na elementy ve stejném kontejneru.

```cpp
typedef typename iterator_traits<RandomIterator>::difference_type  difference_type;
```

### <a name="remarks"></a>Poznámky

`reverse_iterator` Typ rozdíl je stejný jako typ iterator rozdíl.

Typ se jedná o synonymum typename znak iterator `iterator_traits` \< **RandomIterator**> **:: ukazatel**.

### <a name="example"></a>Příklad

V tématu [reverse_iterator::operator&#91; &#93; ](#op_at) příklad toho, jak deklarace a používání `difference_type`.

## <a name="iterator_type"></a>  reverse_iterator::iterator_type

Typ, který poskytuje základní iterator pro `reverse_iterator`.

```cpp
typedef RandomIterator iterator_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `Iterator`.

### <a name="example"></a>Příklad

V tématu [reverse_iterator::base](#base) příklad toho, jak deklarace a používání `iterator_type`.

## <a name="op_star"></a>  reverse_iterator::Operator *

Vrátí element, který řeší reverse_iterator –.

```cpp
reference operator*() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota řešené pomocí reverse_iterator – elementy.

### <a name="remarks"></a>Poznámky

Vrátí operátor \*( **aktuální** – 1).

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

## <a name="op_add"></a>  reverse_iterator::Operator +

Přidá posun do iterovat a vrátí nové `reverse_iterator` adresování vložené element na pozici posunutí nové.

```cpp
reverse_iterator<RandomIterator> operator+(difference_type Off) const;
```

### <a name="parameters"></a>Parametry

`Off` Posun mají být přidány do zpětného iterator.

### <a name="return-value"></a>Návratová hodnota

A `reverse_iterator` adresování posunutí elementu.

### <a name="remarks"></a>Poznámky

Tento člen funkce lze použít pouze pokud `reverse_iterator` splňuje požadavky pro iterator náhodný přístup.

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

## <a name="op_add_add"></a>  reverse_iterator::Operator ++

Reverse_iterator – k předchozímu prvku zvýší.

```cpp
reverse_iterator<RandomIterator>& operator++();
reverse_iterator<RandomIterator> operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí první operátor preincremented `reverse_iterator` a druhý, postincrement operátor kopii zvýšena `reverse_iterator`.

### <a name="remarks"></a>Poznámky

Tento člen funkce lze použít pouze pokud `reverse_iterator` splňuje požadavky pro obousměrnou iterator.

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

## <a name="op_add_eq"></a>  reverse_iterator::Operator +=

Přidá zadaný posun z reverse_iterator –.

```cpp
reverse_iterator<RandomIterator>& operator+=(difference_type Off);
```

### <a name="parameters"></a>Parametry

`Off` Posun, podle kterého se zvýší iterator.

### <a name="return-value"></a>Návratová hodnota

Odkaz na element používala `reverse_iterator`.

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

## <a name="reverse_iterator__operator-"></a>  reverse_iterator::Operator-

Odečítá od posun vůči `reverse_iterator` a vrátí `reverse_iterator` adresování na pozici posunutí elementu.

```cpp
reverse_iterator<RandomIterator> operator-(difference_type Off) const;
```

### <a name="parameters"></a>Parametry

`Off` Posun k bude odečítat od reverse_iterator –.

### <a name="return-value"></a>Návratová hodnota

A `reverse_iterator` adresování posunutí elementu.

### <a name="remarks"></a>Poznámky

Tento člen funkce lze použít pouze pokud `reverse_iterator` splňuje požadavky pro iterator náhodný přístup.

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

## <a name="reverse_iterator__operator--"></a>  reverse_iterator::Operator--

Snižuje reverse_iterator – k předchozí elementu.

```cpp
reverse_iterator<RandomIterator>& operator--();
reverse_iterator<RandomIterator> operator--(int);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí první operátor predecremented `reverse_iterator` a druhý, postdecrement operátor kopii odečte `reverse_iterator`.

### <a name="remarks"></a>Poznámky

Tento člen funkce lze použít pouze pokud `reverse_iterator` splňuje požadavky pro obousměrnou iterator.

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

## <a name="reverse_iterator__operator-_eq"></a>  reverse_iterator::Operator-=

Odečítá od zadaný posun od `reverse_iterator`.

```cpp
reverse_iterator<RandomIterator>& operator-=(difference_type Off);
```

### <a name="parameters"></a>Parametry

`Off` Posun bude odečítat od `reverse_iterator`.

### <a name="remarks"></a>Poznámky

Tento člen funkce lze použít pouze pokud `reverse_iterator` splňuje požadavky pro iterator náhodný přístup.

Operátor vyhodnotí **aktuální** + _ *vypnout*. Vrátí  **\*to**.

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

## <a name="op_arrow"></a>  reverse_iterator::Operator-&gt;

Vrací ukazatel na element používala `reverse_iterator`.

```cpp
pointer operator->() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na element používala `reverse_iterator`.

### <a name="remarks"></a>Poznámky

Vrátí operátor  **& \* \*to**.

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

## <a name="op_at"></a>  reverse_iterator::Operator]

Vrátí odkaz na element posun z prvku používala `reverse_iterator` o zadaný počet pozic.

```cpp
reference operator[](difference_type Off) const;
```

### <a name="parameters"></a>Parametry

`Off` Posun od `reverse_iterator` adresu.

### <a name="return-value"></a>Návratová hodnota

Odkaz na element posun.

### <a name="remarks"></a>Poznámky

Vrátí operátor **\***(  **\*to** + `Off`).

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

## <a name="pointer"></a>  reverse_iterator::Pointer

Typ, který poskytuje ukazatel na element používala `reverse_iterator`.

```cpp
typedef typename iterator_traits<RandomIterator>::pointer pointer;
```

### <a name="remarks"></a>Poznámky

Typ se jedná o synonymum typename znak iterator `iterator_traits` \< *RandomIterator*> **:: ukazatel**.

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

## <a name="reference"></a>  reverse_iterator::Reference

Typ, který obsahuje odkaz na element používala reverse_iterator –.

```cpp
typedef typename iterator_traits<RandomIterator>::reference reference;
```

### <a name="remarks"></a>Poznámky

Typ se jedná o synonymum typename znak iterator `iterator_traits` \< *RandomIterator*> **:: odkaz**.

### <a name="example"></a>Příklad

V tématu [reverse_iterator::operator&#91; &#93; ](#op_at) nebo [reverse_iterator::operator *](#op_star) příklady, jak deklarace a používání **odkaz**.

## <a name="reverse_iterator"></a>  reverse_iterator::reverse_iterator

Vytvoří výchozí `reverse_iterator` nebo `reverse_iterator` ze základní iterator.

```cpp
reverse_iterator();
explicit reverse_iterator(RandomIterator right);

template <class Type>
reverse_iterator(const reverse_iterator<Type>& right);
```

### <a name="parameters"></a>Parametry

`right` Iterator, který má být přizpůsobena `reverse_iterator`.

### <a name="return-value"></a>Návratová hodnota

Výchozí `reverse_iterator` nebo `reverse_iterator` přizpůsobení základní iterator.

### <a name="remarks"></a>Poznámky

Identita, která spojuje všechny obrácené iterátory s jejich základním iterátorem, je:

&\*( `reverse_iterator` ( *i* )) == &\*( *i* – 1).

V praxi to znamená, že v obrácené sekvenci bude iterátor reverse_iterator ukazovat na prvek o jednu pozici za prvkem (vpravo), na který iterátor ukazoval v původní sekvenci. Pokud iterator řešit element 6 v pořadí, (2, 4, 6, 8), pak se `reverse_iterator` bude adresa element 4 v invertovaných pořadí (8, 6, 4, 2).

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

[\<iterator >](../standard-library/iterator.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
