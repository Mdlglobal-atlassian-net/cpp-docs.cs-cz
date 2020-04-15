---
title: '&lt;hash_set&gt; operátory'
ms.date: 03/27/2019
f1_keywords:
- hash_set/std::operator!=
- hash_set/std::operator==
ms.assetid: 403d8e4e-0b3f-43fb-bc5a-8100c4f331c5
ms.openlocfilehash: 5830c9e459c0d778e85c5ab5900d39c3190df178
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368575"
---
# <a name="lthash_setgt-operators"></a>&lt;hash_set&gt; operátory

||||
|-|-|-|
|[operátor!=](#op_neq)|[operátor!= (hash_multiset)](#op_neq_hash_multiset)|[operátor==](#op_eq_eq)|
|[operátor== (hash_multiset)](#op_eq_eq_hash_multiset)|

## <a name="operator"></a><a name="op_neq"></a>operátor!=

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Testuje, zda hash_set objekt na levé straně operátoru není rovna hash_set objektu na pravé straně.

```cpp
bool operator!=(const hash_set <Key, Traits, Allocator>& left, const hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Objekt typu `hash_set`.

*Právo*\
Objekt typu `hash_set`.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud hash_sets nejsou stejné; **false,** pokud hash_sets jsou stejné.

### <a name="remarks"></a>Poznámky

Porovnání mezi hash_set objekty je založena na párové porovnání mezi jejich prvky. Dva hash_sets jsou stejné, pokud mají stejný počet prvků a jejich příslušné prvky mají stejné hodnoty. V opačném případě jsou nerovné.

Členové [<hash_map>](../standard-library/hash-map.md) a<hash_set [>](../standard-library/hash-set.md) hlavičkových souborů jsou v oboru [názvů stdext](../standard-library/stdext-namespace.md).

### <a name="example"></a>Příklad

```cpp
// hash_set_op_ne.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1, hs2, hs3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hs1.insert ( i );
      hs2.insert ( i * i );
      hs3.insert ( i );
   }

   if ( hs1 != hs2 )
      cout << "The hash_sets hs1 and hs2 are not equal." << endl;
   else
      cout << "The hash_sets hs1 and hs2 are equal." << endl;

   if ( hs1 != hs3 )
      cout << "The hash_sets hs1 and hs3 are not equal." << endl;
   else
      cout << "The hash_sets hs1 and hs3 are equal." << endl;
}
```

```Output
The hash_sets hs1 and hs2 are not equal.
The hash_sets hs1 and hs3 are equal.
```

## <a name="operator"></a><a name="op_eq_eq"></a>operátor==

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Testy, pokud hash_set objekt na levé straně operátoru se rovná hash_set objektu na pravé straně.

```cpp
bool operator!==(const hash_set <Key, Traits, Allocator>& left, const hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Objekt typu `hash_set`.

*Právo*\
Objekt typu `hash_set`.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud hash_set na levé straně obsluhy se rovná hash_set na pravé straně obsluhy; jinak **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi hash_set objekty je založena na párové porovnání jejich prvků. Dva hash_sets jsou stejné, pokud mají stejný počet prvků a jejich příslušné prvky mají stejné hodnoty. V opačném případě jsou nerovné.

### <a name="example"></a>Příklad

```cpp
// hash_set_op_eq.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 == s2 )
      cout << "The hash_sets s1 and s2 are equal." << endl;
   else
      cout << "The hash_sets s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The hash_sets s1 and s3 are equal." << endl;
   else
      cout << "The hash_sets s1 and s3 are not equal." << endl;
}
```

```Output
The hash_sets s1 and s2 are not equal.
The hash_sets s1 and s3 are equal.
```

## <a name="operator-hash_multiset"></a><a name="op_neq_hash_multiset"></a>operátor!= (hash_multiset)

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Testy, pokud hash_multiset objekt na levé straně operátoru se nerovná hash_multiset objektu na pravé straně.

```cpp
bool operator!=(const hash_multiset <Key, Traits, Allocator>& left, const hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Objekt typu `hash_multiset`.

*Právo*\
Objekt typu `hash_multiset`.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud hash_multisets nejsou stejné; **false,** pokud hash_multisets jsou stejné.

### <a name="remarks"></a>Poznámky

Porovnání mezi hash_multiset objekty je založena na párové porovnání mezi jejich prvky. Dva hash_multisets jsou stejné, pokud mají stejný počet prvků a jejich příslušné prvky mají stejné hodnoty. V opačném případě jsou nerovné.

### <a name="example"></a>Příklad

```cpp
// hashset_op_ne.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1, hs2, hs3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hs1.insert ( i );
      hs2.insert ( i * i );
      hs3.insert ( i );
   }

   if ( hs1 != hs2 )
      cout << "The hash_multisets hs1 and hs2 are not equal." << endl;
   else
      cout << "The hash_multisets hs1 and hs2 are equal." << endl;

   if ( hs1 != hs3 )
      cout << "The hash_multisets hs1 and hs3 are not equal." << endl;
   else
      cout << "The hash_multisets hs1 and hs3 are equal." << endl;
}
```

```Output
The hash_multisets hs1 and hs2 are not equal.
The hash_multisets hs1 and hs3 are equal.
```

## <a name="operator-hash_multiset"></a><a name="op_eq_eq_hash_multiset"></a>operátor== (hash_multiset)

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set class](../standard-library/unordered-set-class.md).

Testy, pokud hash_multiset objekt na levé straně operátoru se rovná hash_multiset objektu na pravé straně.

```cpp
bool operator!==(const hash_multiset <Key, Traits, Allocator>& left, const hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Objekt typu `hash_multiset`.

*Právo*\
Objekt typu `hash_multiset`.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud hash_multiset na levé straně obsluhy se rovná hash_multiset na pravé straně obsluhy; jinak **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi hash_multiset objekty je založena na párové porovnání jejich prvků. Dva hash_multisets jsou stejné, pokud mají stejný počet prvků a jejich příslušné prvky mají stejné hodnoty. V opačném případě jsou nerovné.

### <a name="example"></a>Příklad

```cpp
// hash_multiset_op_eq.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 == s2 )
      cout << "The hash_multisets s1 and s2 are equal." << endl;
   else
      cout << "The hash_multisets s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The hash_multisets s1 and s2 are equal." << endl;
   else
      cout << "The hash_multisets s1 and s2 are not equal." << endl;
}
```

```Output
The hash_multisets s1 and s2 are not equal.
The hash_multisets s1 and s2 are equal.
```

## <a name="see-also"></a>Viz také

[<hash_set>](../standard-library/hash-set.md)
