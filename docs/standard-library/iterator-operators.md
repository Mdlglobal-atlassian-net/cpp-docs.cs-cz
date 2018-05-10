---
title: '&lt;iterator&gt; operátory | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- xutility/std::operator!=
- xutility/std::operator&gt;
- xutility/std::operator&gt;=
- xutility/std::operator&lt;
- xutility/std::operator&lt;=
- xutility/std::operator+
- xutility/std::operator-
- xutility/std::operator==
dev_langs:
- C++
ms.assetid: b7c664f0-49d4-4993-b5d1-9ac4859fdddc
helpviewer_keywords:
- std::operator!= (iterator)
- std::operator&gt; (iterator)
- std::operator&gt;= (iterator)
- std::operator&lt; (iterator)
- std::operator&lt;= (iterator), std::operator== (iterator)
ms.openlocfilehash: 411fcf8969ba13c4f50360c3db151f0801fd5a28
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="ltiteratorgt-operators"></a>&lt;iterator&gt; operátory

||||
|-|-|-|
|[operator!=](#op_neq)|[Operátor&gt;](#op_gt)|[Operátor&gt;=](#op_gt_eq)|
|[Operátor&lt;](#op_lt)|[Operátor&lt;=](#op_lt_eq)|[operátor +](#op_add)|
|[Operator –](#operator-)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>  Operator! =

Testuje, zda je objekt iterátoru na levé straně operátoru není roven objektu iterátoru na pravé straně.

```cpp
template <class RandomIterator>
bool operator!=(const reverse_iterator<RandomIterator>& left, const reverse_iterator<RandomIterator>& right);

template <class Type, class CharType, class Traits, class Distance>
bool operator!=(const istream_iterator<Type, CharType, Traits, Distance>& left, const istream_iterator<Type, CharType, Traits, Distance>& right);

template <class CharType, class Tr>
bool operator!=(const istreambuf_iterator<CharType, Traits>& left, const istreambuf_iterator<CharType, Traits>& right);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu **iterator**.

`right` Objekt typu **iterator**.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud iterator objekty nejsou stejné; **false** Pokud iterator objekty jsou stejné.

### <a name="remarks"></a>Poznámky

Jeden objekt iterator se rovná jiné, pokud se adresa stejné prvky v kontejneru. Pokud se dva iterátory bodu na různé elementy v kontejneru, pak nejsou stejné.

### <a name="example"></a>Příklad

```cpp
// iterator_op_ne.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 9 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the last element
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),
           rVPOS2 = vec.rbegin ( );

   cout << "The iterator rVPOS1 initially points to the first "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   if ( rVPOS1 != rVPOS2 )
      cout << "The iterators are not equal." << endl;
   else
      cout << "The iterators are equal." << endl;

   rVPOS1++;
   cout << "The iterator rVPOS1 now points to the second "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   if ( rVPOS1 != rVPOS2 )
      cout << "The iterators are not equal." << endl;
   else
      cout << "The iterators are equal." << endl;
}
```

```Output
The vector vec is: ( 1 2 3 4 5 6 7 8 ).
The iterator rVPOS1 initially points to the first element
 in the reversed sequence: 8.
The iterators are equal.
The iterator rVPOS1 now points to the second element
 in the reversed sequence: 7.
The iterators are not equal.
```

## <a name="op_eq_eq"></a>  Operator ==

Testuje, zda je objekt iterátoru na levé straně operátoru roven objektu iterátoru na pravé straně.

```cpp
template <class RandomIterator1, class RandomIterator2>
bool operator==(
    const move_iterator<RandomIterator1>& left,
    const move_iterator<RandomIterator2>& right);

template <class RandomIterator1, class RandomIterator2>
bool operator==(
    const reverse_iterator<RandomIterator1>& left,
    const reverse_iterator<RandomIterator2>& right);

template <class Type, class CharType, class Traits, class Distance>
bool operator==(
    const istream_iterator<Type, CharType, Traits, Distance>& left,
    const istream_iterator<Type, CharType, Traits, Distance>& right);

template <class CharType, class Tr>
bool operator==(
    const istreambuf_iterator<CharType, Traits>& left,
    const istreambuf_iterator<CharType, Traits>& right);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu iterator.

`right` Objekt typu iterator.

### <a name="return-value"></a>Návratová hodnota

`true` Pokud jsou objekty iterator rovna; `false` Pokud iterator objekty nejsou stejné.

### <a name="remarks"></a>Poznámky

Jeden objekt iterator se rovná jiné, pokud se adresa stejné prvky v kontejneru. Pokud se dva iterátory bodu na různé elementy v kontejneru, pak nejsou stejné.

První dvě šablony operátory vrátí hodnotu true, pouze pokud obě `left` a `right` ukládání stejné iterator. Vrátí hodnotu true, pouze pokud obě třetí operátor šablony `left` a `right` úložiště stejný datový proud ukazatele. Vrátí čtvrtou operátor šablony ` left.equal ( right)`.

### <a name="example"></a>Příklad

```cpp
// iterator_op_eq.cpp
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
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the last element
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),
           rVPOS2 = vec.rbegin ( );

   cout << "The iterator rVPOS1 initially points to the first "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   if ( rVPOS1 == rVPOS2 )
      cout << "The iterators are equal." << endl;
   else
      cout << "The iterators are not equal." << endl;

   rVPOS1++;
   cout << "The iterator rVPOS1 now points to the second "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   if ( rVPOS1 == rVPOS2 )
      cout << "The iterators are equal." << endl;
   else
      cout << "The iterators are not equal." << endl;
}
```

```Output
The vector vec is: ( 2 4 6 8 10 ).
The iterator rVPOS1 initially points to the first element
 in the reversed sequence: 10.
The iterators are equal.
The iterator rVPOS1 now points to the second element
 in the reversed sequence: 8.
The iterators are not equal.
```

## <a name="op_lt"></a>  Operátor&lt;

Testuje, zda je objekt iterátoru na levé straně operátoru menší než objekt iterátoru na pravé straně.

```cpp
template <class RandomIterator>
bool operator<(const reverse_iterator<RandomIterator>& left, const reverse_iterator<RandomIterator>& right);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu **iterator**.

`right` Objekt typu **iterator**.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud iterator na levé straně výrazu je menší než iterator na pravé straně výrazu; **false** Pokud je větší než nebo rovna hodnotě iterator na pravé straně.

### <a name="remarks"></a>Poznámky

Jeden objekt iterator je menší než jiné, pokud ho adresy element, který nastane dříve v kontejneru než element používala jiné iterator objektu. Jeden objekt iterator není menší než jiná Pokud zaměřuje se na stejný element jako druhý objekt iterator nebo element, který později v kontejneru než element používala druhý objekt iterator dojde.

### <a name="example"></a>Příklad

```cpp
// iterator_op_lt.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 0 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;

   cout << "The initial vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the last element
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),
           rVPOS2 = vec.rbegin ( );

   cout << "The iterators rVPOS1& rVPOS2 initially point to the "
           << "first element\n in the reversed sequence: "
           << *rVPOS1 << "." << endl;

   if ( rVPOS1 < rVPOS2 )
      cout << "The iterator rVPOS1 is less than"
              << " the iterator rVPOS2." << endl;
   else
      cout << "The iterator rVPOS1 is not less than"
              << " the iterator rVPOS2." << endl;

   rVPOS2++;
   cout << "The iterator rVPOS2 now points to the second "
           << "element\n in the reversed sequence: "
           << *rVPOS2 << "." << endl;

   if ( rVPOS1 < rVPOS2 )
      cout << "The iterator rVPOS1 is less than"
              << " the iterator rVPOS2." << endl;
   else
      cout << "The iterator rVPOS1 is not less than"
              << " the iterator rVPOS2." << endl;
}
```

```Output
The initial vector vec is: ( 0 2 4 6 8 10 ).
The iterators rVPOS1& rVPOS2 initially point to the first element
 in the reversed sequence: 10.
The iterator rVPOS1 is not less than the iterator rVPOS2.
The iterator rVPOS2 now points to the second element
 in the reversed sequence: 8.
The iterator rVPOS1 is less than the iterator rVPOS2.
```

## <a name="op_lt_eq"></a>  Operátor&lt;=

Testuje, zda je objekt iterátoru na levé straně operátoru menší než nebo roven objektu iterátoru na pravé straně.

```cpp
template <class RandomIterator>
bool operator<=(const reverse_iterator<RandomIterator>& left, const reverse_iterator<RandomIterator>& right);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu iterator.

`right` Objekt typu iterator.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud iterator na levé straně výrazu je menší než nebo rovna iterator na pravé straně výrazu; **false** Pokud je větší než iterator na pravé straně.

### <a name="remarks"></a>Poznámky

Jeden objekt iterator je menší než nebo rovna hodnotě jiného, pokud zaměřuje se na stejný element nebo element, který nastane dříve v kontejneru než element používala jiné iterator objektu. Jeden objekt iterator je větší než jiné, pokud ji adresy element, který později v kontejneru než element používala druhý objekt iterator dojde.

### <a name="example"></a>Příklad

```cpp
// iterator_op_le.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 0 ; i < 6 ; ++i )  {
      vec.push_back ( 2 * i );
      }

   vector <int>::iterator vIter;

   cout << "The initial vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ) + 1,
           rVPOS2 = vec.rbegin ( );

   cout << "The iterator rVPOS1 initially points to the "
           << "second element\n in the reversed sequence: "
           << *rVPOS1 << "." << endl;

   cout << "The iterator rVPOS2 initially points to the "
           << "first element\n in the reversed sequence: "
           << *rVPOS2 << "." << endl;

   if ( rVPOS1 <= rVPOS2 )
      cout << "The iterator rVPOS1 is less than or "
              << "equal to the iterator rVPOS2." << endl;
   else
      cout << "The iterator rVPOS1 is greater than "
              << "the iterator rVPOS2." << endl;

   rVPOS2++;
   cout << "The iterator rVPOS2 now points to the second "
           << "element\n in the reversed sequence: "
           << *rVPOS2 << "." << endl;

   if ( rVPOS1 <= rVPOS2 )
      cout << "The iterator rVPOS1 is less than or "
              << "equal to the iterator rVPOS2." << endl;
   else
      cout << "The iterator rVPOS1 is greater than "
              << "the iterator rVPOS2." << endl;
}
```

```Output
The initial vector vec is: ( 0 2 4 6 8 10 ).
The iterator rVPOS1 initially points to the second element
 in the reversed sequence: 8.
The iterator rVPOS2 initially points to the first element
 in the reversed sequence: 10.
The iterator rVPOS1 is greater than the iterator rVPOS2.
The iterator rVPOS2 now points to the second element
 in the reversed sequence: 8.
The iterator rVPOS1 is less than or equal to the iterator rVPOS2.
```

## <a name="op_gt"></a>  Operátor&gt;

Testuje, zda je objekt iterátoru na levé straně operátoru větší než objekt iterátoru na pravé straně.

```cpp
template <class RandomIterator>
bool operator>(const reverse_iterator<RandomIterator>& left, const reverse_iterator<RandomIterator>& right);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu iterator.

`right` Objekt typu iterator.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud iterator na levé straně výrazu je větší než iterator na pravé straně výrazu; **false** Pokud je menší než nebo rovna iterator na pravé straně.

### <a name="remarks"></a>Poznámky

Jeden objekt iterator je větší než jiné, pokud ji adresy element, který později v kontejneru než element používala druhý objekt iterator dojde. Jeden objekt iterator není větší než jiné, pokud ji adresy stejného elementu jako druhý objekt iterator nebo element, který nastane dříve v kontejneru než element používala jiné iterator objektu.

### <a name="example"></a>Příklad

```cpp
// iterator_op_gt.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 0 ; i < 6 ; ++i )  {
      vec.push_back ( 2 * i );
      }

   vector <int>::iterator vIter;

   cout << "The initial vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),
           rVPOS2 = vec.rbegin ( );

   cout << "The iterators rVPOS1 & rVPOS2 initially point to "
           << "the first element\n in the reversed sequence: "
           << *rVPOS1 << "." << endl;

   if ( rVPOS1 > rVPOS2 )
      cout << "The iterator rVPOS1 is greater than "
              << "the iterator rVPOS2." << endl;
   else
      cout << "The iterator rVPOS1 is less than or "
              << "equal to the iterator rVPOS2." << endl;

   rVPOS1++;
   cout << "The iterator rVPOS1 now points to the second "
           << "element\n in the reversed sequence: "
           << *rVPOS1 << "." << endl;

   if ( rVPOS1 > rVPOS2 )
      cout << "The iterator rVPOS1 is greater than "
              << "the iterator rVPOS2." << endl;
   else
      cout << "The iterator rVPOS1 is less than or "
              << "equal to the iterator rVPOS2." << endl;
}
```

```Output
The initial vector vec is: ( 0 2 4 6 8 10 ).
The iterators rVPOS1 & rVPOS2 initially point to the first element
 in the reversed sequence: 10.
The iterator rVPOS1 is less than or equal to the iterator rVPOS2.
The iterator rVPOS1 now points to the second element
 in the reversed sequence: 8.
The iterator rVPOS1 is greater than the iterator rVPOS2.
```

## <a name="op_gt_eq"></a>  Operátor&gt;=

Testuje, zda je objekt iterátoru na levé straně operátoru větší než nebo roven objektu iterátoru na pravé straně.

```cpp
template <class RandomIterator>
bool operator>=(const reverse_iterator<RandomIterator>& left, const reverse_iterator<RandomIterator>& right);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu iterator.

`right` Objekt typu iterator.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud iterator na levé straně výrazu je větší než nebo rovno iterator na pravé straně výrazu; **false** Pokud je menší než iterator na pravé straně.

### <a name="remarks"></a>Poznámky

Jeden objekt iterator je větší než nebo rovna hodnotě jiného, pokud zaměřuje se na stejný element nebo element, který v kontejneru než element používala jiné iterator objekt dojde později. Jeden objekt iterator je menší než jiné, pokud ho adresy element, který nastane dříve v kontejneru než element používala jiné iterator objektu.

### <a name="example"></a>Příklad

```cpp
// iterator_op_ge.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 0 ; i < 6 ; ++i )  {
      vec.push_back ( 2 * i );
      }

   vector <int>::iterator vIter;

   cout << "The initial vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),
           rVPOS2 = vec.rbegin ( ) + 1;

   cout << "The iterator rVPOS1 initially points to the "
           << "first element\n in the reversed sequence: "
           << *rVPOS1 << "." << endl;

   cout << "The iterator rVPOS2 initially points to the "
           << "second element\n in the reversed sequence: "
           << *rVPOS2 << "." << endl;

   if ( rVPOS1 >= rVPOS2 )
      cout << "The iterator rVPOS1 is greater than or "
              << "equal to the iterator rVPOS2." << endl;
   else
      cout << "The iterator rVPOS1 is less than "
              << "the iterator rVPOS2." << endl;

   rVPOS1++;
   cout << "The iterator rVPOS1 now points to the second "
           << "element\n in the reversed sequence: "
           << *rVPOS1 << "." << endl;

   if ( rVPOS1 >= rVPOS2 )
      cout << "The iterator rVPOS1 is greater than or "
              << "equal to the iterator rVPOS2." << endl;
   else
      cout << "The iterator rVPOS1 is less than "
              << "the iterator rVPOS2." << endl;
}
```

```Output
The initial vector vec is: ( 0 2 4 6 8 10 ).
The iterator rVPOS1 initially points to the first element
 in the reversed sequence: 10.
The iterator rVPOS2 initially points to the second element
 in the reversed sequence: 8.
The iterator rVPOS1 is less than the iterator rVPOS2.
The iterator rVPOS1 now points to the second element
 in the reversed sequence: 8.
The iterator rVPOS1 is greater than or equal to the iterator rVPOS2.
```

## <a name="op_add"></a>  operátor +

Přidá posun do iterovat a vrátí `move_iterator` nebo `reverse_iterator` adresování vložené element na pozici posunutí nové.

```cpp
template <class RandomIterator, class Diff>
move_iterator<RandomIterator>
operator+(
    Diff _Off,
    const move_iterator<RandomIterator>& right);

template <class RandomIterator>
reverse_iterator<RandomIterator>
operator+(
    Diff _Off,
    const reverse_iterator<RandomIterator>& right);
```

### <a name="parameters"></a>Parametry

`_Off` Počet pozic const move_iterator nebo const reverse_iterator – je posunuty.

`right` Iterator k posunuty.

### <a name="return-value"></a>Návratová hodnota

Vrátí součet `right`  +  `_Off`.

### <a name="example"></a>Příklad

```cpp
// iterator_op_insert.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 0 ; i < 6 ; ++i )  {
      vec.push_back ( 2 * i );
      }

   vector <int>::iterator vIter;

   cout << "The initial vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( );

   cout << "The iterator rVPOS1 initially points to "
           << "the first element\n in the reversed sequence: "
           << *rVPOS1 << "." << endl;

   vector<int>::difference_type diff = 4;
   rVPOS1 = diff +rVPOS1;

   cout << "The iterator rVPOS1 now points to the fifth "
           << "element\n in the reversed sequence: "
           << *rVPOS1 << "." << endl;
}
```

```Output
The initial vector vec is: ( 0 2 4 6 8 10 ).
The iterator rVPOS1 initially points to the first element
 in the reversed sequence: 10.
The iterator rVPOS1 now points to the fifth element
 in the reversed sequence: 2.
```

## <a name="operator-"></a>  Operator –

Odečte jeden iterátor od druhého a vrátí rozdíl.

```cpp
template <class RandomIterator1, class RandomIterator2>
Tdiff operator-(
    const move_iterator<RandomIterator1>& left,
    const move_iterator<RandomIterator2>& right);

template <class RandomIterator1, class RandomIterator2>
Tdiff operator-(
    const reverse_iterator<RandomIterator1>& left,
    const reverse_iterator<RandomIterator2>& right);
```

### <a name="parameters"></a>Parametry

`left` Iterator.

`right` Iterator.

### <a name="return-value"></a>Návratová hodnota

Rozdíl mezi dvěma iterátory `.`

### <a name="remarks"></a>Poznámky

Vrátí první operátor šablony `left.base() - right.base()`.

Vrátí druhou šablonu operátor `right.current - left.current`.

`Tdiff` je určen podle typ vrácený výrazu. Jinak je `RandomIterator1::difference_type`.

### <a name="example"></a>Příklad

```cpp
// iterator_op_sub.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 0 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;

   cout << "The initial vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),
          rVPOS2 = vec.rbegin ( );

   cout << "The iterators rVPOS1 & rVPOS2 initially point to "
        << "the first element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   for (i = 1; i < 5; ++i)
   {
      rVPOS2++;
   }
   cout << "The iterator rVPOS2 now points to the fifth "
        << "element\n in the reversed sequence: "
        << *rVPOS2 << "." << endl;

   vector<int>::difference_type diff = rVPOS2 - rVPOS1;
   cout << "The difference: rVPOS2 - rVPOS1= "
        << diff << "." << endl;
}
```

```Output
The initial vector vec is: ( 0 2 4 6 8 10 ).
The iterators rVPOS1 & rVPOS2 initially point to the first element
 in the reversed sequence: 10.
The iterator rVPOS2 now points to the fifth element
 in the reversed sequence: 2.
The difference: rVPOS2 - rVPOS1= 4.
```

## <a name="see-also"></a>Viz také

[\<iterator >](../standard-library/iterator.md)<br/>
