---
title: '&lt;hash_map&gt; operátorů'
ms.date: 11/04/2016
f1_keywords:
- hash_map/std::operator!=
- hash_map/std::operator==
ms.assetid: 24b9bb9e-e983-4060-bce5-2c7c8161ee61
ms.openlocfilehash: ed143349f3afc7a27ad565c1cc929c6ecb5f6ad8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375452"
---
# <a name="lthash_mapgt-operators"></a>&lt;hash_map&gt; operátorů

|||
|-|-|
|[operátor!=](#op_neq)|[operátor!= (multimap)](#op_neq_mm)|
|[operátor==](#op_eq_eq)|[operator== (multimap)](#op_eq_eq_mm)|

## <a name="operator"></a><a name="op_neq"></a>operátor!=

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](unordered-map-class.md).

Testy, pokud hash_map objekt na levé straně operátoru není rovna hash_map objektu na pravé straně.

```cpp
bool operator!=(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Objekt typu `hash_map`.

*Právo*\
Objekt typu `hash_map`.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud hash_maps nejsou stejné; **false,** pokud hash_maps jsou stejné.

### <a name="remarks"></a>Poznámky

Porovnání mezi hash_map objekty je založena na párové porovnání jejich prvků. Dvě hash_maps jsou stejné, pokud mají stejný počet prvků a jejich příslušné prvky mají stejné hodnoty. V opačném případě jsou nerovné.

Členové [<hash_map>](hash-map.md) a<hash_set [>](hash-set.md) hlavičkových souborů v oboru [názvů stdext](stdext-namespace.md).

### <a name="example"></a>Příklad

```cpp
// hash_map_op_ne.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2, hm3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hm1.insert ( Int_Pair ( i, i ) );
      hm2.insert ( Int_Pair ( i, i * i ) );
      hm3.insert ( Int_Pair ( i, i ) );
   }

   if ( hm1 != hm2 )
      cout << "The hash_maps hm1 and hm2 are not equal." << endl;
   else
      cout << "The hash_maps hm1 and hm2 are equal." << endl;

   if ( hm1 != hm3 )
      cout << "The hash_maps hm1 and hm3 are not equal." << endl;
   else
      cout << "The hash_maps hm1 and hm3 are equal." << endl;
}
```

```Output
The hash_maps hm1 and hm2 are not equal.
The hash_maps hm1 and hm3 are equal.
```

## <a name="operator"></a><a name="op_eq_eq"></a>operátor==

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_map](unordered-map-class.md).

Testy, pokud hash_map objekt na levé straně operátoru se rovná hash_map objektu na pravé straně.

```cpp
bool operator==(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Objekt typu `hash_map`.

*Právo*\
Objekt typu `hash_map`.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud hash_map na levé straně obsluhy se rovná hash_map na pravé straně obsluhy; jinak **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi hash_map objekty je založena na párové porovnání jejich prvků. Dvě hash_maps jsou stejné, pokud mají stejný počet prvků a jejich příslušné prvky mají stejné hodnoty. V opačném případě jsou nerovné.

### <a name="example"></a>Příklad

```cpp
// hash_map_op_eq.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2, hm3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hm1.insert ( Int_Pair ( i, i ) );
      hm2.insert ( Int_Pair ( i, i * i ) );
      hm3.insert ( Int_Pair ( i, i ) );
   }

   if ( hm1 == hm2 )
      cout << "The hash_maps hm1 and hm2 are equal." << endl;
   else
      cout << "The hash_maps hm1 and hm2 are not equal." << endl;

   if ( hm1 == hm3 )
      cout << "The hash_maps hm1 and hm3 are equal." << endl;
   else
      cout << "The hash_maps hm1 and hm3 are not equal." << endl;
}
```

```Output
The hash_maps hm1 and hm2 are not equal.
The hash_maps hm1 and hm3 are equal.
```

## <a name="operator-hash_multimap"></a><a name="op_neq_mm"></a>operátor!= (hash_multimap)

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](unordered-multimap-class.md).

Testy, pokud hash_multimap objekt na levé straně operátoru se nerovná hash_multimap objektu na pravé straně.

```cpp
bool operator!=(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Objekt typu `hash_multimap`.

*Právo*\
Objekt typu `hash_multimap`.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud hash_multimaps nejsou stejné; **false,** pokud hash_multimaps jsou si rovni.

### <a name="remarks"></a>Poznámky

Porovnání mezi hash_multimap objekty je založena na párové porovnání jejich prvků. Dva hash_multimaps jsou stejné, pokud mají stejný počet prvků a jejich příslušné prvky mají stejné hodnoty. V opačném případě jsou nerovné.

### <a name="example"></a>Příklad

```cpp
// hash_multimap_op_ne.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1, hm2, hm3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hm1.insert ( Int_Pair ( i, i ) );
      hm2.insert ( Int_Pair ( i, i * i ) );
      hm3.insert ( Int_Pair ( i, i ) );
   }

   if ( hm1 != hm2 )
      cout << "The hash_multimaps hm1 and hm2 are not equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm2 are equal." << endl;

   if ( hm1 != hm3 )
      cout << "The hash_multimaps hm1 and hm3 are not equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm3 are equal." << endl;
}
```

```Output
The hash_multimaps hm1 and hm2 are not equal.
The hash_multimaps hm1 and hm3 are equal.
```

## <a name="operator--hash_multimap"></a><a name="op_eq_eq_mm"></a>operátor== (hash_multimap)

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [třída unordered_multimap](unordered-multimap-class.md).

Testy, pokud hash_multimap objekt na levé straně operátoru se rovná hash_multimap objektu na pravé straně.

```cpp
bool operator==(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Objekt typu `hash_multimap`.

*Právo*\
Objekt typu `hash_multimap`.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud hash_multimap na levé straně obsluhy se rovná hash_multimap na pravé straně obsluhy; jinak **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi hash_multimap objekty je založena na párové porovnání jejich prvků. Dva hash_multimaps jsou stejné, pokud mají stejný počet prvků a jejich příslušné prvky mají stejné hodnoty. V opačném případě jsou nerovné.

### <a name="example"></a>Příklad

```cpp
// hash_multimap_op_eq.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap<int, int> hm1, hm2, hm3;
   int i;
   typedef pair<int, int> Int_Pair;

   for (i = 0; i < 3; i++)
   {
      hm1.insert(Int_Pair(i, i));
      hm2.insert(Int_Pair(i, i*i));
      hm3.insert(Int_Pair(i, i));
   }

   if ( hm1 == hm2 )
      cout << "The hash_multimaps hm1 and hm2 are equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm2 are not equal." << endl;

   if ( hm1 == hm3 )
      cout << "The hash_multimaps hm1 and hm3 are equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm3 are not equal." << endl;
}
```

```Output
The hash_multimaps hm1 and hm2 are not equal.
The hash_multimaps hm1 and hm3 are equal.
```

## <a name="see-also"></a>Viz také

[<hash_map>](hash-map.md)
