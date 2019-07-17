---
title: '&lt;deque –&gt; operátory'
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
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245650"
---
# <a name="ltdequegt-operators"></a>&lt;deque –&gt; operátory

## <a name="op_neq"></a> Operator! =

Testuje, zda je objekt deque na levé straně operátoru není roven objektu deque na pravé straně.

```cpp
bool operator!=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*\
Objekt typu `deque`.

*doprava*\
Objekt typu `deque`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud nejsou stejné; deque – objekty **false** Pokud deque – objekty rovnají.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty deque vychází pairwise porovnání jejich prvky. Pokud mají stejný počet prvků a jejich odpovídající elementy mají stejné hodnoty jsou deque – objekty rovnocenné. V opačném případě nerovnost.

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

## <a name="op_lt"></a> – Operátor&lt;

Testuje, zda je objekt deque na levé straně operátoru menší než objekt deque na pravé straně.

```cpp
bool operator<(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*\
Objekt typu `deque`.

*doprava*\
Objekt typu `deque`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud deque na levé straně operátoru menší než a není rovno deque na pravé straně operátoru; jinak vrátí **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty deque vychází pairwise porovnání jejich prvky. Větší-než vztah mezi dvěma objekty je založen na porovnání první pár prvků nerovnost.

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

## <a name="op_lt_eq"></a> – Operátor&lt;=

Testuje, zda je deque objekt na levé straně operátoru je menší než nebo roven objektu deque na pravé straně.

```cpp
bool operator<=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*\
Objekt typu `deque`.

*doprava*\
Objekt typu `deque`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud deque na levé straně operátoru menší než nebo rovna hodnotě deque na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty deque vychází pairwise porovnání jejich prvky. Je menší než nebo rovna na vztah mezi dvěma objekty podle porovnání první pár prvků nerovnost.

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

## <a name="op_eq_eq"></a> Operator ==

Testuje, zda objekt deque na levé straně operátoru roven objektu deque na pravé straně.

```cpp
bool operator==(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*\
Objekt typu `deque`.

*doprava*\
Objekt typu `deque`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** deque na levé straně operátoru je jinak deque na pravé straně operátoru roven **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty deque vychází pairwise porovnání jejich prvky. Pokud mají stejný počet prvků a jejich odpovídající elementy mají stejné hodnoty dvou deques jsou si rovny. V opačném případě nerovnost.

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

## <a name="op_gt"></a> – Operátor&gt;

Testuje, zda je objekt deque na levé straně operátoru větší než deque objekt na pravé straně.

```cpp
bool operator>(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*\
Objekt typu `deque`.

*doprava*\
Objekt typu `deque`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud deque na levé straně operátoru větší než deque na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty deque vychází pairwise porovnání jejich prvky. Větší-než vztah mezi dvěma objekty je založen na porovnání první pár prvků nerovnost.

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

## <a name="op_gt_eq"></a> – Operátor&gt;=

Testuje, zda je objekt deque na levé straně operátoru větší než nebo rovna hodnotě deque objekt na pravé straně.

```cpp
bool operator>=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*\
Objekt typu `deque`.

*doprava*\
Objekt typu `deque`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud deque na levé straně operátoru větší než nebo rovna hodnotě deque na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty deque vychází pairwise porovnání jejich prvky. Větší než nebo rovna hodnotě vztah mezi dvěma objekty podle porovnání první pár prvků nerovnost.

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
