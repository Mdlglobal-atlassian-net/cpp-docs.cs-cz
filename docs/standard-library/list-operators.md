---
title: operátory seznamu&gt; &lt;
ms.date: 11/04/2016
f1_keywords:
- list/std::operator!=
- list/std::operator&gt;
- list/std::operator&gt;=
- list/std::operator&lt;
- list/std::operator&lt;=
- list/std::operator==
ms.assetid: 8103d8f2-c30f-49ad-ac50-b3ba6a907ebe
helpviewer_keywords:
- std::operator!= (list)
- std::operator&gt; (list)
- std::operator&gt;= (list)
- std::operator&lt; (list)
- std::operator&lt;= (list)
- std::operator== (list)
ms.openlocfilehash: 7b0b7540c1b9a55140405a55e8e034f9c6ec646c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78874423"
---
# <a name="ltlistgt-operators"></a>operátory seznamu&gt; &lt;

## <a name="op_neq"></a>! = – operátor

Testuje, zda se objekt seznamu na levé straně operátoru nerovná objektu seznamu na pravé straně.

```cpp
bool operator!=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `list`.

*pravé*\
Objekt typu `list`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud se seznamy neshodují; **false** , pokud jsou seznamy stejné.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty seznamu je založeno na porovnávacím porovnání jejich prvků. Dva seznamy jsou stejné, pokud mají stejný počet prvků a jejich příslušné prvky mají stejné hodnoty. V opačném případě jsou nerovné.

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

## <a name="op_lt"></a>operátor&lt;

Testuje, zda je objekt seznamu na levé straně operátoru menší než objekt seznamu na pravé straně.

```cpp
bool operator<(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `list`.

*pravé*\
Objekt typu `list`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je seznam na levé straně operátoru menší než, ale není rovno seznamu na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty seznamu je založeno na porovnávacím porovnání jejich prvků. Vztah menší než je mezi dvěma objekty je založen na porovnání první dvojice nerovnosti prvků.

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

## <a name="op_lt_eq"></a>operátor&lt;=

Testuje, zda je objekt seznamu na levé straně operátoru menší než nebo roven objektu seznamu na pravé straně.

```cpp
bool operator<=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `list`.

*pravé*\
Objekt typu `list`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je seznam na levé straně operátoru menší než nebo rovný seznamu na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty seznamu je založeno na porovnávacím porovnání jejich prvků. Vztah menší nebo rovno mezi dvěma objekty je založen na porovnání první dvojice nerovnosti prvků.

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

## <a name="op_eq_eq"></a>operator = = – operátor

Testuje, zda je objekt seznamu na levé straně operátoru roven objektu seznamu na pravé straně.

```cpp
bool operator==(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `list`.

*pravé*\
Objekt typu `list`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je seznam na levé straně operátoru stejný jako seznam na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty seznamu je založeno na porovnávacím porovnání jejich prvků. Dva seznamy jsou stejné, pokud mají stejný počet prvků a jejich příslušné prvky mají stejné hodnoty. V opačném případě jsou nerovné.

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

## <a name="op_gt"></a>operátor&gt;

Testuje, zda je objekt seznamu na levé straně operátoru větší než objekt seznamu na pravé straně.

```cpp
bool operator>(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `list`.

*pravé*\
Objekt typu `list`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je seznam na levé straně operátoru větší než seznam na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty seznamu je založeno na porovnávacím porovnání jejich prvků. Větší vztah mezi dvěma objekty je založen na porovnání první dvojice nerovnosti prvků.

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

## <a name="op_gt_eq"></a>operátor&gt;=

Testuje, zda je objekt seznamu na levé straně operátoru větší než nebo roven objektu seznamu na pravé straně.

```cpp
bool operator>=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `list`.

*pravé*\
Objekt typu `list`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je seznam na levé straně operátoru větší než nebo roven seznamu na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty seznamu je založeno na porovnávacím porovnání jejich prvků. Relace větší než nebo rovna mezi dvěma objekty je založena na porovnání první dvojice nerovnosti prvků.

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
