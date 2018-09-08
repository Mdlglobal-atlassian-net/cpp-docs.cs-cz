---
title: '&lt;Nastavte&gt; operátory | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- set/std::operator!=
- set/std::operator&gt;
- set/std::operator&gt;=
- set/std::operator&lt;
- set/std::operator&lt;=
- set/std::operator==
dev_langs:
- C++
ms.assetid: b4256ebc-c449-4688-95db-fced42d20d4d
helpviewer_keywords:
- std::operator!= (set)
- std::operator&gt; (set)
- std::operator&gt;= (set)
- std::operator&lt; (set)
- std::operator&lt;= (set)
- std::operator== (set)
ms.openlocfilehash: 43ee5b62bcda9a38946bfd61c3ed3efbc8d89523
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44110068"
---
# <a name="ltsetgt-operators"></a>&lt;Nastavte&gt; operátory

||||
|-|-|-|
|[Operator! = (set)](#op_neq)|[operátor&gt; (set)](#op_gt)|[operátor&gt;= (set)](#eq)|
|[operátor&lt; (set)](#op_lt)|[operátor&lt;= (set)](#eq)|[Operator == (set)](#op_eq_eq)|
|[Operator! = (multiset)](#op_neq_multiset)|[operátor&gt; (multiset)](#op_gt_multiset)|[operátor&gt;= (multiset)](#op_gt_eq_multiset)|
|[operátor&lt; (multiset)](#op_lt_multiset)|[operátor&lt;= (multiset)](#op_lt_eq_multiset)|[operator== (multiset)](#op_eq_eq_multiset)|

## <a name="op_neq"></a>  Operator! = (set)

Testuje, zda je objekt set na levé straně operátoru není roven objektu set na pravé straně.

```cpp
bool operator!=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `set`.

*doprava*<br/>
Objekt typu `set`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud sady nejsou stejné; **false** Pokud sady jsou stejné.

### <a name="remarks"></a>Poznámky

Porovnání mezi sadu objektů podle pairwise srovnání jejich prvky. Dvě sady jsou stejné, pokud mají stejný počet prvků a jejich odpovídající elementy mají stejné hodnoty. V opačném případě nerovnost.

### <a name="example"></a>Příklad

```cpp
// set_op_ne.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 != s2 )
      cout << "The sets s1 and s2 are not equal." << endl;
   else
      cout << "The sets s1 and s2 are equal." << endl;

   if ( s1 != s3 )
      cout << "The sets s1 and s3 are not equal." << endl;
   else
      cout << "The sets s1 and s3 are equal." << endl;
}
\* Output:
The sets s1 and s2 are not equal.
The sets s1 and s3 are equal.
*\
```

## <a name="op_lt"></a>  operátor&lt; (set)

Testuje, zda je objekt set na levé straně operátoru menší než objekt set na pravé straně.

```cpp
bool operator<(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `set`.

*doprava*<br/>
Objekt typu `set`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud sada na levé straně operátoru není striktně menší než sada na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi sadu objektů podle pairwise porovnání jejich prvky. Větší-než vztah mezi dvěma objekty je založen na porovnání první pár prvků nerovnost.

### <a name="example"></a>Příklad

```cpp
// set_op_lt.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
   }

   if ( s1 < s2 )
      cout << "The set s1 is less than the set s2." << endl;
   else
      cout << "The set s1 is not less than the set s2." << endl;

   if ( s1 < s3 )
      cout << "The set s1 is less than the set s3." << endl;
   else
      cout << "The set s1 is not less than the set s3." << endl;
}
\* Output:
The set s1 is less than the set s2.
The set s1 is not less than the set s3.
*\
```

## <a name="op_lt_eq"></a>  operátor&lt;= (set)

Testuje, zda je sada objekt na levé straně operátoru je menší než nebo roven objektu set na pravé straně.

```cpp
bool operator!<=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `set`.

*doprava*<br/>
Objekt typu `set`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud je sada na levé straně operátoru menší než nebo rovna sada na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi sadu objektů podle pairwise porovnání jejich prvky. Je menší než nebo rovna na vztah mezi dvěma objekty podle porovnání první pár prvků nerovnost.

### <a name="example"></a>Příklad

```cpp
// set_op_le.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3, s4;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
      s4.insert ( i );
   }

   if ( s1 <= s2 )
      cout << "Set s1 is less than or equal to the set s2." << endl;
   else
      cout << "The set s1 is greater than the set s2." << endl;

   if ( s1 <= s3 )
      cout << "Set s1 is less than or equal to the set s3." << endl;
   else
      cout << "The set s1 is greater than the set s3." << endl;

   if ( s1 <= s4 )
      cout << "Set s1 is less than or equal to the set s4." << endl;
   else
      cout << "The set s1 is greater than the set s4." << endl;
}
\* Output:
Set s1 is less than or equal to the set s2.
The set s1 is greater than the set s3.
Set s1 is less than or equal to the set s4.
*\
```

## <a name="op_eq_eq"></a>  Operator == (set)

Testuje, zda je objekt set na levé straně operátoru roven objektu set na pravé straně.

```cpp
bool operator!==(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `set`.

*doprava*<br/>
Objekt typu `set`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud je sada na levé straně operátoru roven sada na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi sadu objektů podle pairwise porovnání jejich prvky. Dvě sady jsou stejné, pokud mají stejný počet prvků a jejich odpovídající elementy mají stejné hodnoty. V opačném případě nerovnost.

### <a name="example"></a>Příklad

```cpp
// set_op_eq.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 == s2 )
      cout << "The sets s1 and s2 are equal." << endl;
   else
      cout << "The sets s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The sets s1 and s3 are equal." << endl;
   else
      cout << "The sets s1 and s3 are not equal." << endl;
}
\* Output:
The sets s1 and s2 are not equal.
The sets s1 and s3 are equal.
*\
```

## <a name="op_gt"></a>  operátor&gt; (set)

Testuje, zda je objekt set na levé straně operátoru větší než objekt set na pravé straně.

```cpp
bool operator>(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `set`.

*doprava*<br/>
Objekt typu `set`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud je sada na levé straně operátoru větší než sada na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi sadu objektů podle pairwise porovnání jejich prvky. Větší-než vztah mezi dvěma objekty je založen na porovnání první pár prvků nerovnost.

### <a name="example"></a>Příklad

```cpp
// set_op_gt.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
   }

   if ( s1 > s2 )
      cout << "The set s1 is greater than the set s2." << endl;
   else
      cout << "The set s1 is not greater than the set s2." << endl;

   if ( s1 > s3 )
      cout << "The set s1 is greater than the set s3." << endl;
   else
      cout << "The set s1 is not greater than the set s3." << endl;
}
\* Output:
The set s1 is not greater than the set s2.
The set s1 is greater than the set s3.
*\
```

## <a name="op_gt_eq"></a>  operátor&gt;= (set)

Testuje, zda je objekt set na levé straně operátoru větší než nebo roven objektu set na pravé straně.

```cpp
bool operator!>=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `set`.

*doprava*<br/>
Objekt typu `set`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud je sada na levé straně operátoru větší než nebo rovna hodnotě sada na pravé straně seznamu; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi sadu objektů podle pairwise porovnání jejich prvky. Větší než nebo rovna hodnotě vztah mezi dvěma objekty podle porovnání první pár prvků nerovnost.

### <a name="example"></a>Příklad

```cpp
// set_op_ge.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3, s4;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
      s4.insert ( i );
   }

   if ( s1 >= s2 )
      cout << "Set s1 is greater than or equal to set s2." << endl;
   else
      cout << "The set s1 is less than the set s2." << endl;

   if ( s1 >= s3 )
      cout << "Set s1 is greater than or equal to set s3." << endl;
   else
      cout << "The set s1 is less than the set s3." << endl;

   if ( s1 >= s4 )
      cout << "Set s1 is greater than or equal to set s4." << endl;
   else
      cout << "The set s1 is less than the set s4." << endl;
}
\* Output:
The set s1 is less than the set s2.
Set s1 is greater than or equal to set s3.
Set s1 is greater than or equal to set s4.
*\
```

## <a name="op_neq_multiset"></a>  Operator! = (multiset)

Testuje, zda je objekt multiset – na levé straně operátoru není roven multiset – objekt na pravé straně.

```cpp
bool operator!=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `multiset`.

*doprava*<br/>
Objekt typu `multiset`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud sady nebo multisets nejsou stejné; **false** Pokud sady nebo multisets jsou si rovny.

### <a name="remarks"></a>Poznámky

Porovnání mezi multiset – objekty podle pairwise srovnání jejich prvky. Dvě sady nebo multisets jsou stejné, pokud mají stejný počet prvků a jejich odpovídající elementy mají stejné hodnoty. V opačném případě nerovnost.

### <a name="example"></a>Příklad

```cpp
// multiset_op_ne.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 != s2 )
      cout << "The multisets s1 and s2 are not equal." << endl;
   else
      cout << "The multisets s1 and s2 are equal." << endl;

   if ( s1 != s3 )
      cout << "The multisets s1 and s3 are not equal." << endl;
   else
      cout << "The multisets s1 and s3 are equal." << endl;
}
\* Output:
The multisets s1 and s2 are not equal.
The multisets s1 and s3 are equal.
*\
```

## <a name="op_lt_multiset"></a>  operátor&lt; (multiset)

Testuje, zda je objekt multiset – na levé straně operátoru menší než multiset – objekt na pravé straně.

```cpp
bool operator<(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `multiset`.

*doprava*<br/>
Objekt typu `multiset`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud multiset na levé straně operátoru je striktně menší než multiset na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi multiset – objekty podle pairwise porovnání jejich prvky. Větší-než vztah mezi dvěma objekty je založen na porovnání první pár prvků nerovnost.

### <a name="example"></a>Příklad

```cpp
// multiset_op_lt.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
   }

   if ( s1 < s2 )
      cout << "The multiset s1 is less than "
           << "the multiset s2." << endl;
   else
      cout << "The multiset s1 is not less than "
           << "the multiset s2." << endl;

   if ( s1 < s3 )
      cout << "The multiset s1 is less than "
           << "the multiset s3." << endl;
   else
      cout << "The multiset s1 is not less than "
           << "the multiset s3." << endl;
}
\* Output:
The multiset s1 is less than the multiset s2.
The multiset s1 is not less than the multiset s3.
*\
```

## <a name="op_lt_eq_multiset"></a>  operátor&lt;= (multiset)

Testuje, zda je třída multiset objekt na levé straně operátoru je menší než nebo rovna hodnotě multiset – objekt na pravé straně.

```cpp
bool operator!<=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `multiset`.

*doprava*<br/>
Objekt typu `multiset`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud multiset na levé straně operátoru menší než nebo rovna hodnotě multiset na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi multiset – objekty podle pairwise porovnání jejich prvky. Je menší než nebo rovna na vztah mezi dvěma objekty podle porovnání první pár prvků nerovnost.

### <a name="example"></a>Příklad

```cpp
// multiset_op_le.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3, s4;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
      s4.insert ( i );
   }

   if ( s1 <= s2 )
      cout << "The multiset s1 is less than "
           << "or equal to the multiset s2." << endl;
   else
      cout << "The multiset s1 is greater than "
           << "the multiset s2." << endl;

   if ( s1 <= s3 )
      cout << "The multiset s1 is less than "
           << "or equal to the multiset s3." << endl;
   else
      cout << "The multiset s1 is greater than "
           << "the multiset s3." << endl;

   if ( s1 <= s4 )
      cout << "The multiset s1 is less than "
           << "or equal to the multiset s4." << endl;
   else
      cout << "The multiset s1 is greater than "
           << "the multiset s4." << endl;
}
\* Output:
The multiset s1 is less than or equal to the multiset s2.
The multiset s1 is greater than the multiset s3.
The multiset s1 is less than or equal to the multiset s4.
*\
```

## <a name="op_eq_eq_multiset"></a>  Operator == (multiset)

Testuje, zda je objekt multiset – na levé straně operátoru rovná multiset – objekt na pravé straně.

```cpp
bool operator!==(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `multiset`.

*doprava*<br/>
Objekt typu `multiset`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** multiset na levé straně operátoru je jinak multiset na pravé straně operátoru roven **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi multiset – objekty podle pairwise porovnání jejich prvky. Dvě sady nebo multisets jsou stejné, pokud mají stejný počet prvků a jejich odpovídající elementy mají stejné hodnoty. V opačném případě nerovnost.

### <a name="example"></a>Příklad

```cpp
// multiset_op_eq.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 == s2 )
      cout << "The multisets s1 and s2 are equal." << endl;
   else
      cout << "The multisets s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The multisets s1 and s3 are equal." << endl;
   else
      cout << "The multisets s1 and s3 are not equal." << endl;
}
\* Output:
The multisets s1 and s2 are not equal.
The multisets s1 and s3 are equal.
*\
```

## <a name="op_gt_multiset"></a>  operátor&gt; (multiset)

Testuje, zda je objekt multiset – na levé straně operátoru větší než multiset – objekt na pravé straně.

```cpp
bool operator>(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `multiset`.

*doprava*<br/>
Objekt typu `multiset`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud multiset na levé straně operátoru větší než multiset na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi multiset – objekty podle pairwise porovnání jejich prvky. Větší-než vztah mezi dvěma objekty je založen na porovnání první pár prvků nerovnost.

### <a name="example"></a>Příklad

```cpp
// multiset_op_gt.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
   }

   if ( s1 > s2 )
      cout << "The multiset s1 is greater than "
           << "the multiset s2." << endl;
   else
      cout << "The multiset s1 is not greater "
           << "than the multiset s2." << endl;

   if ( s1 > s3 )
      cout << "The multiset s1 is greater than "
           << "the multiset s3." << endl;
   else
      cout << "The multiset s1 is not greater than "
           << "the multiset s3." << endl;
}
\* Output:
The multiset s1 is not greater than the multiset s2.
The multiset s1 is greater than the multiset s3.
*\
```

## <a name="op_gt_eq_multiset"></a>  operátor&gt;= (multiset)

Testuje, zda je objekt multiset – na levé straně operátoru větší než nebo rovna hodnotě multiset – objekt na pravé straně.

```cpp
bool operator!>=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `multiset`.

*doprava*<br/>
Objekt typu `multiset`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud multiset na levé straně operátoru větší než nebo rovna hodnotě multiset na pravé straně seznamu; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi multiset – objekty podle pairwise porovnání jejich prvky. Větší než nebo rovna hodnotě vztah mezi dvěma objekty podle porovnání první pár prvků nerovnost.

### <a name="example"></a>Příklad

```cpp
// multiset_op_ge.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3, s4;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
      s4.insert ( i );
   }

   if ( s1 >= s2 )
      cout << "The multiset s1 is greater than "
           << "or equal to the multiset s2." << endl;
   else
      cout << "The multiset s1 is less than "
           << "the multiset s2." << endl;

   if ( s1 >= s3 )
      cout << "The multiset s1 is greater than "
           << "or equal to the multiset s3." << endl;
   else
      cout << "The multiset s1 is less than "
           << "the multiset s3." << endl;

   if ( s1 >= s4 )
      cout << "The multiset s1 is greater than "
           << "or equal to the multiset s4." << endl;
   else
      cout << "The multiset s1 is less than "
           << "the multiset s4." << endl;
}
\* Output:
The multiset s1 is less than the multiset s2.
The multiset s1 is greater than or equal to the multiset s3.
The multiset s1 is greater than or equal to the multiset s4.
*\
```

## <a name="see-also"></a>Viz také:

[\<set>](../standard-library/set.md)<br/>
