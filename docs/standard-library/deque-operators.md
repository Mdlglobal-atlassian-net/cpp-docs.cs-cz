---
title: '&lt;operátory&gt; deque'
ms.date: 11/04/2016
f1_keywords:
- deque/std::operator!=
- deque/std::operator&gt;
- deque/std::operator&gt;=
- deque/std::operator&lt;
- deque/std::operator&lt;=
- deque/std::operator==
ms.assetid: 482d7c92-54c7-493b-99e6-2a73617481a5
helpviewer_keywords:
- std::operator!= (deque)
- std::operator&gt; (deque)
- std::operator&gt;= (deque)
- std::operator&lt; (deque)
- std::operator&lt;= (deque)
- std::operator== (deque)
ms.openlocfilehash: 868909ac4346a59cade3660f288a0f0e71bc4ed0
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883793"
---
# <a name="ltdequegt-operators"></a>&lt;operátory&gt; deque

## <a name="op_neq"></a>! = – operátor

Testuje, zda objekt deque na levé straně operátoru není roven objektu deque na pravé straně.

```cpp
bool operator!=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `deque`.

*pravé*\
Objekt typu `deque`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud nejsou objekty deque stejné; **false** , pokud jsou objekty deque stejné.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty deque je založeno na párovým porovnání jejich prvků. Dva objekty deque jsou stejné, pokud mají stejný počet prvků a jejich příslušné prvky mají stejné hodnoty. V opačném případě jsou nerovné.

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
```

```Output
The deques are not equal.
```

## <a name="op_lt"></a>operátor&lt;

Testuje, zda je objekt deque na levé straně operátoru menší než objekt deque na pravé straně.

```cpp
bool operator<(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `deque`.

*pravé*\
Objekt typu `deque`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je deque na levé straně operátoru menší než a není rovno deque na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty deque je založeno na párovým porovnání jejich prvků. Vztah menší než je mezi dvěma objekty je založen na porovnání první dvojice nerovnosti prvků.

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
```

```Output
Deque c1 is less than deque c2.
```

## <a name="op_lt_eq"></a>operátor&lt;=

Testuje, zda je objekt deque na levé straně operátoru menší než nebo roven objektu deque na pravé straně.

```cpp
bool operator<=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `deque`.

*pravé*\
Objekt typu `deque`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je deque na levé straně operátoru menší než nebo rovno deque na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty deque je založeno na párovým porovnání jejich prvků. Vztah menší nebo rovno mezi dvěma objekty je založen na porovnání první dvojice nerovnosti prvků.

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
```

```Output
Deque c1 is less than or equal to deque c2.
```

## <a name="op_eq_eq"></a>operator = = – operátor

Testuje, zda je objekt deque na levé straně operátoru roven objektu deque na pravé straně.

```cpp
bool operator==(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `deque`.

*pravé*\
Objekt typu `deque`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je deque na levé straně operátoru rovno deque na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty deque je založeno na párovým porovnání jejich prvků. Dva deques jsou stejné, pokud mají stejný počet prvků a jejich příslušné prvky mají stejné hodnoty. V opačném případě jsou nerovné.

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
```

```Output
The deques are equal.
The deques are not equal.
```

## <a name="op_gt"></a>operátor&gt;

Testuje, zda je objekt deque na levé straně operátoru větší než objekt deque na pravé straně.

```cpp
bool operator>(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `deque`.

*pravé*\
Objekt typu `deque`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je deque na levé straně operátoru větší než deque na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty deque je založeno na párovým porovnání jejich prvků. Větší vztah mezi dvěma objekty je založen na porovnání první dvojice nerovnosti prvků.

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
```

```Output
Deque c1 is greater than deque c2.
```

## <a name="op_gt_eq"></a>operátor&gt;=

Testuje, zda je objekt deque na levé straně operátoru větší než nebo roven objektu deque na pravé straně.

```cpp
bool operator>=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `deque`.

*pravé*\
Objekt typu `deque`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je deque na levé straně operátoru větší než nebo rovno deque na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty deque je založeno na párovým porovnání jejich prvků. Relace větší než nebo rovna mezi dvěma objekty je založena na porovnání první dvojice nerovnosti prvků.

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
```

```Output
Deque c1 is greater than or equal to deque c2.
```
