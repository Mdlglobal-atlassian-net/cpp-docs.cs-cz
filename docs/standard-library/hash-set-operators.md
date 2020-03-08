---
title: operátory &lt;hash_set&gt;
ms.date: 03/27/2019
f1_keywords:
- hash_set/std::operator!=
- hash_set/std::operator==
ms.assetid: 403d8e4e-0b3f-43fb-bc5a-8100c4f331c5
ms.openlocfilehash: 3900e9c6e4fb7f5a163279165a51b440d138a8e5
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883838"
---
# <a name="lthash_setgt-operators"></a>operátory &lt;hash_set&gt;

||||
|-|-|-|
|[operator!=](#op_neq)|[operator! = (hash_multiset) – operátor](#op_neq_hash_multiset)|[operator = = – operátor](#op_eq_eq)|
|[operator = = (hash_multiset) – operátor](#op_eq_eq_hash_multiset)|

## <a name="op_neq"></a>! = – operátor

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_set třídy](../standard-library/unordered-set-class.md).

Testuje, zda hash_set objekt na levé straně operátoru není roven objektu hash_set na pravé straně.

```cpp
bool operator!=(const hash_set <Key, Traits, Allocator>& left, const hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `hash_set`.

*pravé*\
Objekt typu `hash_set`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud hash_sets nejsou stejné; **false** , pokud je hash_sets rovna.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty hash_set je založeno na porovnávacím porovnání mezi jejich prvky. Dva hash_sets jsou stejné, pokud mají stejný počet prvků a jejich příslušné prvky mají stejné hodnoty. V opačném případě jsou nerovné.

V [oboru názvů stdext](../standard-library/stdext-namespace.md)jsou členové [< hash_map >](../standard-library/hash-map.md) a < soubory hlaviček [hash_set >](../standard-library/hash-set.md) .

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

## <a name="op_eq_eq"></a>operator = = – operátor

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_set třídy](../standard-library/unordered-set-class.md).

Testuje, zda je objekt hash_set na levé straně operátoru roven objektu hash_set na pravé straně.

```cpp
bool operator!==(const hash_set <Key, Traits, Allocator>& left, const hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `hash_set`.

*pravé*\
Objekt typu `hash_set`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je hash_set na levé straně operátoru rovno hash_set na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi hash_set objekty je založeno na porovnávacím porovnání jejich prvků. Dva hash_sets jsou stejné, pokud mají stejný počet prvků a jejich příslušné prvky mají stejné hodnoty. V opačném případě jsou nerovné.

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

## <a name="op_neq_hash_multiset"></a>operator! = (hash_multiset) – operátor

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_set třídy](../standard-library/unordered-set-class.md).

Testuje, zda hash_multiset objekt na levé straně operátoru není roven objektu hash_multiset na pravé straně.

```cpp
bool operator!=(const hash_multiset <Key, Traits, Allocator>& left, const hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `hash_multiset`.

*pravé*\
Objekt typu `hash_multiset`.

### <a name="return-value"></a>Návratová hodnota

**true** , Pokud hash_multisets nejsou stejné; **false** , pokud je hash_multisets rovna.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty hash_multiset je založeno na porovnávacím porovnání mezi jejich prvky. Dva hash_multisets jsou stejné, pokud mají stejný počet prvků a jejich příslušné prvky mají stejné hodnoty. V opačném případě jsou nerovné.

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

## <a name="op_eq_eq_hash_multiset"></a>operator = = (hash_multiset) – operátor

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_set třídy](../standard-library/unordered-set-class.md).

Testuje, zda je objekt hash_multiset na levé straně operátoru roven objektu hash_multiset na pravé straně.

```cpp
bool operator!==(const hash_multiset <Key, Traits, Allocator>& left, const hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `hash_multiset`.

*pravé*\
Objekt typu `hash_multiset`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je hash_multiset na levé straně operátoru rovno hash_multiset na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi hash_multiset objekty je založeno na porovnávacím porovnání jejich prvků. Dva hash_multisets jsou stejné, pokud mají stejný počet prvků a jejich příslušné prvky mají stejné hodnoty. V opačném případě jsou nerovné.

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
