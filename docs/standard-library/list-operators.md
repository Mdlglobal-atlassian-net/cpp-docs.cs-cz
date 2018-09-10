---
title: '&lt;seznam&gt; operátory | Dokumentace Microsoftu'
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
ms.openlocfilehash: e61fe4895026881d4d4db63b9617018fbe12d889
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44317209"
---
# <a name="ltlistgt-operators"></a>&lt;seznam&gt; operátory

||||
|-|-|-|
|[operator!=](#op_neq)|[– Operátor&gt;](#op_gt)|[– Operátor&gt;=](#op_gt_eq)|
|[– Operátor&lt;](#op_lt)|[– Operátor&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>  Operator! =

Testuje, zda je objekt seznamu na levé straně operátoru není roven objektu seznamu na pravé straně.

```cpp
bool operator!=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `list`.

*doprava*<br/>
Objekt typu `list`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud nejsou stejné; seznamy **false** Pokud seznamy jsou si rovny.

### <a name="remarks"></a>Poznámky

Porovnání mezi seznam objektů podle pairwise porovnání jejich prvky. Pokud mají stejný počet prvků a jejich odpovídající elementy mají stejné hodnoty dva seznamy jsou si rovny. V opačném případě nerovnost.

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
/* Output:
Lists not equal.
*/
```

## <a name="op_lt"></a>  – Operátor&lt;

Testuje, zda je objekt seznamu na levé straně operátoru menší než objekt seznamu na pravé straně.

```cpp
bool operator<(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `list`.

*doprava*<br/>
Objekt typu `list`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** -li v seznamu na levé straně operátoru menší než, ale není v seznamu na pravé straně operátoru roven; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi seznam objektů podle pairwise porovnání jejich prvky. Větší-než vztah mezi dvěma objekty je založen na porovnání první pár prvků nerovnost.

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
/* Output:
List c1 is less than list c2.
*/
```

## <a name="op_lt_eq"></a>  – Operátor&lt;=

Testuje, zda je objekt v seznamu na levé straně operátoru je menší než nebo roven objektu seznamu na pravé straně.

```cpp
bool operator<=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `list`.

*doprava*<br/>
Objekt typu `list`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** -li v seznamu na levé straně operátoru menší než nebo rovna hodnotě v seznamu na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi seznam objektů podle pairwise porovnání jejich prvky. Je menší než nebo rovna na vztah mezi dvěma objekty podle porovnání první pár prvků nerovnost.

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
/* Output:
List c1 is less than or equal to list c2.
*/
```

## <a name="op_eq_eq"></a>  Operator ==

Testuje, zda je objekt seznamu na levé straně operátoru roven objektu seznamu na pravé straně.

```cpp
bool operator==(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `list`.

*doprava*<br/>
Objekt typu `list`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud je seznam na levé straně operátoru roven seznamu na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi seznam objektů podle pairwise porovnání jejich prvky. Pokud mají stejný počet prvků a jejich odpovídající elementy mají stejné hodnoty dva seznamy jsou si rovny. V opačném případě nerovnost.

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
/* Output:
The lists are equal.
*/
```

## <a name="op_gt"></a>  – Operátor&gt;

Testuje, zda je objekt seznamu na levé straně operátoru větší než objekt seznamu na pravé straně.

```cpp
bool operator>(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `list`.

*doprava*<br/>
Objekt typu `list`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud je v seznamu na levé straně operátoru větší než v seznamu na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi seznam objektů podle pairwise porovnání jejich prvky. Větší-než vztah mezi dvěma objekty je založen na porovnání první pár prvků nerovnost.

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
/* Output:
List c1 is greater than list c2.
*/
```

## <a name="op_gt_eq"></a>  – Operátor&gt;=

Testuje, zda je objekt seznamu na levé straně operátoru větší než nebo roven objektu seznamu na pravé straně.

```cpp
bool operator>=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `list`.

*doprava*<br/>
Objekt typu `list`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud je v seznamu na levé straně operátoru větší než nebo rovna hodnotě v seznamu na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi seznam objektů podle pairwise porovnání jejich prvky. Větší než nebo rovna hodnotě vztah mezi dvěma objekty podle porovnání první pár prvků nerovnost.

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
/* Output:
List c1 is greater than or equal to list c2.
*/
```

## <a name="see-also"></a>Viz také:

[\<Seznam >](../standard-library/list.md)<br/>
