---
title: '&lt;seznam&gt; operátory | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- list/std::operator!=
- list/std::operator&gt;
- list/std::operator&gt;=
- list/std::operator&lt;
- list/std::operator&lt;=
- list/std::operator==
dev_langs:
- C++
ms.assetid: 8103d8f2-c30f-49ad-ac50-b3ba6a907ebe
helpviewer_keywords:
- std::operator!= (list)
- std::operator&gt; (list)
- std::operator&gt;= (list)
- std::operator&lt; (list)
- std::operator&lt;= (list)
- std::operator== (list)
ms.openlocfilehash: b2647cf836fb565115b8a582085b6108c01a3420
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="ltlistgt-operators"></a>&lt;seznam&gt; operátory

||||
|-|-|-|
|[operator!=](#op_neq)|[Operátor&gt;](#op_gt)|[Operátor&gt;=](#op_gt_eq)|
|[Operátor&lt;](#op_lt)|[Operátor&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>  Operator! =

Testy, pokud objekt seznamu na levé straně operátoru není stejný jako seznam objekt na pravé straně.

```cpp
bool operator!=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu **seznamu**.

`right` Objekt typu **seznamu**.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud seznamy není stejný; **false** Pokud seznamy jsou stejné.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty seznamu je založena na pairwise porovnání jejich součástí. Dva seznamy jsou stejné, pokud mají stejný počet elementů a jejich odpovídajících elementy mají stejné hodnoty. Jinak nerovné.

### <a name="example"></a>Příklad

```cpp
// list_op_ne.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
using namespace std;
list <int> c1, c2;
c1.push_back( 1 );
c2.push_back( 2 );

if ( c1 != c2 )
cout << "Lists not equal." << endl;
else
cout << "Lists equal." << endl;
}
\* Output:
Lists not equal.
*\
```

## <a name="op_lt"></a>  Operátor&lt;

Testy, pokud objekt seznamu na levé straně operátoru je menší než list objekt na pravé straně.

```cpp
bool operator<(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu **seznamu**.

`right` Objekt typu **seznamu**.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud v seznamu na levé straně operátor je menší než, ale není v seznamu na pravé straně operátoru rovná; jinak hodnota **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty seznamu je založena na pairwise porovnání jejich součástí. Je menší – než vztah mezi dvěma objekty je založen na porovnání první pár nerovné elementů.

### <a name="example"></a>Příklad

```cpp
// list_op_lt.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2;
   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 4 );

   c2.push_back( 1 );
   c2.push_back( 3 );

   if ( c1 < c2 )
      cout << "List c1 is less than list c2." << endl;
   else
      cout << "List c1 is not less than list c2." << endl;
}
\* Output:
List c1 is less than list c2.
*\
```

## <a name="op_lt_eq"></a>  Operátor&lt;=

Pokud v seznamu objekt na levé straně operátoru testů je menší než nebo rovna hodnotě list objekt na pravé straně.

```cpp
bool operator<=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu **seznamu**.

`right` Objekt typu **seznamu**.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud v seznamu na levé straně operátor je menší než nebo rovna hodnotě v seznamu na pravé straně operátoru; jinak hodnota **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty seznamu je založena na pairwise porovnání jejich součástí. Je menší než nebo rovna na relaci mezi dvěma objekty je založena na porovnání první pár nerovné elementů.

### <a name="example"></a>Příklad

```cpp
// list_op_le.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2;
   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 4 );

   c2.push_back( 1 );
   c2.push_back( 3 );

   if ( c1 <= c2 )
      cout << "List c1 is less than or equal to list c2." << endl;
   else
      cout << "List c1 is greater than list c2." << endl;
}
\* Output:
List c1 is less than or equal to list c2.
*\
```

## <a name="op_eq_eq"></a>  Operator ==

Testy, pokud se objekt seznamu na levé straně operátoru rovná objektu seznamu na pravé straně.

```cpp
bool operator==(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu **seznamu**.

`right` Objekt typu **seznamu**.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud v seznamu na levé straně operátoru rovná v seznamu na pravé straně operátoru; jinak hodnota **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty seznamu je založena na pairwise porovnání jejich součástí. Dva seznamy jsou stejné, pokud mají stejný počet elementů a jejich odpovídajících elementy mají stejné hodnoty. Jinak nerovné.

### <a name="example"></a>Příklad

```cpp
// list_op_eq.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
int main( )
{
   using namespace std;

   list <int> c1, c2;
   c1.push_back( 1 );
   c2.push_back( 1 );

   if ( c1 == c2 )
      cout << "The lists are equal." << endl;
   else
      cout << "The lists are not equal." << endl;
}
\* Output:
The lists are equal.
*\
```

## <a name="op_gt"></a>  Operátor&gt;

Testy, pokud objekt seznamu na levé straně operátoru je větší než list objekt na pravé straně.

```cpp
bool operator>(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu **seznamu**.

`right` Objekt typu **seznamu**.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud v seznamu na levé straně operátor je větší než v seznamu na pravé straně operátoru jinak **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty seznamu je založena na pairwise porovnání jejich součástí. Delší – než vztah mezi dvěma objekty je založen na porovnání první pár nerovné elementů.

### <a name="example"></a>Příklad

```cpp
// list_op_gt.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
int main( )
{
   using namespace std;
   list <int> c1, c2;
   c1.push_back( 1 );
   c1.push_back( 3 );
   c1.push_back( 1 );

   c2.push_back( 1 );
   c2.push_back( 2 );
   c2.push_back( 2 );

   if ( c1 > c2 )
      cout << "List c1 is greater than list c2." << endl;
   else
      cout << "List c1 is not greater than list c2." << endl;
}
\* Output:
List c1 is greater than list c2.
*\
```

## <a name="op_gt_eq"></a>  Operátor&gt;=

Testy, pokud je seznam objekt na levé straně operátoru větší než nebo rovna hodnotě list objekt na pravé straně.

```cpp
bool operator>=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu **seznamu**.

`right` Objekt typu **seznamu**.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud v seznamu na levé straně operátor je větší než nebo rovna hodnotě v seznamu na pravé straně operátoru; jinak hodnota **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty seznamu je založena na pairwise porovnání jejich součástí. Větší než nebo rovna hodnotě vztah mezi dvěma objekty podle porovnání první pár nerovné elementů.

### <a name="example"></a>Příklad

```cpp
// list_op_ge.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2;
   c1.push_back( 1 );
   c1.push_back( 3 );
   c1.push_back( 1 );

   c2.push_back( 1 );
   c2.push_back( 2 );
   c2.push_back( 2 );

   if ( c1 >= c2 )
      cout << "List c1 is greater than or equal to list c2." << endl;
   else
      cout << "List c1 is less than list c2." << endl;
}
\* Output:
List c1 is greater than or equal to list c2.
*\
```

## <a name="see-also"></a>Viz také

[\<Seznam >](../standard-library/list.md)<br/>
