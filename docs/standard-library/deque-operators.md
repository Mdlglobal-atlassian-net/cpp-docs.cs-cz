---
title: '&lt;deque&gt; operátory | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- deque/std::operator!=
- deque/std::operator&gt;
- deque/std::operator&gt;=
- deque/std::operator&lt;
- deque/std::operator&lt;=
- deque/std::operator==
dev_langs:
- C++
ms.assetid: 482d7c92-54c7-493b-99e6-2a73617481a5
caps.latest.revision: 7
manager: ghogen
helpviewer_keywords:
- std::operator!= (deque)
- std::operator&gt; (deque)
- std::operator&gt;= (deque)
- std::operator&lt; (deque)
- std::operator&lt;= (deque)
- std::operator== (deque)
ms.openlocfilehash: 4cc8784c30615a9cb580aa27c072a035c7ec4951
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="ltdequegt-operators"></a>&lt;deque&gt; operátory

||||
|-|-|-|
|[operator!=](#op_neq)|[Operátor&gt;](#op_gt)|[Operátor&gt;=](#op_gt_eq)|
|[Operátor&lt;](#op_lt)|[Operátor&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>  Operator! =

Testy, pokud deque objekt na levé straně operátoru není stejný jako deque objekt na pravé straně.

```cpp
bool operator!=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu `deque`.

`right` Objekt typu `deque`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud deque objekty nejsou stejné; **false** Pokud deque objekty jsou stejné.

### <a name="remarks"></a>Poznámky

Porovnání mezi deque – objekty je založena na pairwise porovnání jejich součástí. Deque – dva objekty jsou stejné, pokud mají stejný počet elementů a jejich odpovídajících elementy mají stejné hodnoty. Jinak nerovné.

### <a name="example"></a>Příklad

```cpp
// deque_op_ne.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c2.push_back( 2 );

   if ( c1 != c2 )
      cout << "The deques are not equal." << endl;
   else
      cout << "The deques are equal." << endl;
}
\* Output:
The deques are not equal.
*\
```

## <a name="op_lt"></a>  Operátor&lt;

Testy, pokud deque objekt na levé straně operátor je menší než deque objekt na pravé straně.

```cpp
bool operator<(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu `deque`.

`right` Objekt typu `deque`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud deque na levé straně operátoru je menší než a není rovno deque na pravé straně operátoru; jinak hodnota **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi deque – objekty je založena na pairwise porovnání jejich součástí. Je menší – než vztah mezi dvěma objekty je založen na porovnání první pár nerovné elementů.

### <a name="example"></a>Příklad

```cpp
// deque_op_lt.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 4 );

   c2.push_back( 1 );
   c2.push_back( 3 );

   if ( c1 < c2 )
      cout << "Deque c1 is less than deque c2." << endl;
   else
      cout << "Deque c1 is not less than deque c2." << endl;
}
\* Output:
Deque c1 is less than deque c2.
*\
```

## <a name="op_lt_eq"></a>  Operátor&lt;=

Pokud deque objekt na levé straně operátoru testů je menší než nebo rovna hodnotě deque objekt na pravé straně.

```cpp
bool operator<=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu `deque`.

`right` Objekt typu `deque`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud deque na levé straně operátoru je menší než nebo rovná deque na pravé straně operátoru; jinak hodnota **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi deque – objekty je založena na pairwise porovnání jejich součástí. Je menší než nebo rovna na relaci mezi dvěma objekty je založena na porovnání první pár nerovné elementů.

### <a name="example"></a>Příklad

```cpp
// deque_op_le.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 4 );

   c2.push_back( 1 );
   c2.push_back( 3 );

   if ( c1 <= c2 )
      cout << "Deque c1 is less than or equal to deque c2." << endl;
   else
      cout << "Deque c1 is greater than deque c2." << endl;
}
\* Output:
Deque c1 is less than or equal to deque c2.
*\

```

## <a name="op_eq_eq"></a>  Operator ==

Testy, pokud deque objekt na levé straně operátoru rovná deque objekt na pravé straně.

```cpp
bool operator==(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu `deque`.

`right` Objekt typu `deque`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud deque na levé straně operátoru rovná deque na pravé straně operátoru; jinak hodnota **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi deque – objekty je založena na pairwise porovnání jejich součástí. Dva deques jsou stejné, pokud mají stejný počet elementů a jejich odpovídajících elementy mají stejné hodnoty. Jinak nerovné.

### <a name="example"></a>Příklad

```cpp
// deque_op_eq.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c2.push_back( 1 );

   if ( c1 == c2 )
      cout << "The deques are equal." << endl;
   else
      cout << "The deques are not equal." << endl;

   c1.push_back( 1 );
   if ( c1 == c2 )
      cout << "The deques are equal." << endl;
   else
      cout << "The deques are not equal." << endl;
}
\* Output:
The deques are equal.
The deques are not equal.
*\

```

## <a name="op_gt"></a>  Operátor&gt;

Testy, pokud deque objekt na levé straně operátoru je větší než deque objekt na pravé straně.

```cpp
bool operator>(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu `deque`.

`right` Objekt typu `deque`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud deque na levé straně operátoru je větší než deque na pravé straně operátoru jinak **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi deque – objekty je založena na pairwise porovnání jejich součástí. Delší – než vztah mezi dvěma objekty je založen na porovnání první pár nerovné elementů.

### <a name="example"></a>Příklad

```cpp
// deque_op_gt.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 3 );
   c1.push_back( 1 );

   c2.push_back( 1 );
   c2.push_back( 2 );
   c2.push_back( 2 );

   if ( c1 > c2 )
      cout << "Deque c1 is greater than deque c2." << endl;
   else
      cout << "Deque c1 is not greater than deque c2." << endl;
}
\* Output:
Deque c1 is greater than deque c2.
*\

```

## <a name="op_gt_eq"></a>  Operátor&gt;=

Testy, pokud je deque objekt na levé straně operátoru větší než nebo rovna hodnotě deque objekt na pravé straně.

```cpp
bool operator>=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu `deque`.

`right` Objekt typu `deque`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud deque na levé straně operátoru je větší než nebo rovná deque na pravé straně operátoru; jinak hodnota **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi deque – objekty je založena na pairwise porovnání jejich součástí. Větší než nebo rovna hodnotě vztah mezi dvěma objekty podle porovnání první pár nerovné elementů.

### <a name="example"></a>Příklad

```cpp
// deque_op_ge.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 3 );
   c1.push_back( 1 );

   c2.push_back( 1 );
   c2.push_back( 2 );
   c2.push_back( 2 );

   if ( c1 >= c2 )
      cout << "Deque c1 is greater than or equal to deque c2." << endl;
   else
      cout << "Deque c1 is less than deque c2." << endl;
}
\* Output:
Deque c1 is greater than or equal to deque c2.
*\
```

## <a name="see-also"></a>Viz také

[\<deque >](../standard-library/deque.md)<br/>
