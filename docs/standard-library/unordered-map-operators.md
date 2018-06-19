---
title: '&lt;unordered_map –&gt; operátory | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- unordered_map/std::operator!=
- unordered_map/std::operator==
dev_langs:
- C++
ms.assetid: 9d5add0b-84bd-4a79-bd82-3f58b55145ed
ms.openlocfilehash: 69a53ae6b54248f5b9938e2c9137a24f441c061d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33859349"
---
# <a name="ltunorderedmapgt-operators"></a>&lt;unordered_map –&gt; operátory

|||||
|-|-|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|[operator!=](#op_neq_multimap)|[operator==](#op_eq_eq_multimap)|

## <a name="op_neq"></a>  Operator! =

Testy jestli [unordered_map](../standard-library/unordered-map-class.md) objekt na levé straně operátoru není stejný jako unordered_map objekt na pravé straně.

```cpp
bool operator!=(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu `unordered_map`.

`right` Objekt typu `unordered_map`.

### <a name="return-value"></a>Návratová hodnota

`true` Pokud unordered_maps není stejný; `false` Pokud jsou stejné.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty unordered_map nemá vliv libovolný pořadí, ve kterém budou ukládat jejich elementů. Pokud mají stejný počet elementů a prvky v jednom kontejneru jsou Permutace elementů v kontejneru další dva unordered_maps jsou si rovny. Jinak nerovné.

### <a name="example"></a>Příklad

```cpp
// unordered_map_op_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_map<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i+1, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i+1 ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i+1, i ) );
   }

   cout << boolalpha;
   cout << "um1 != um2: " << (um1 != um2) << endl;
   cout << "um1 != um3: " << (um1 != um3) << endl;
   cout << "um2 != um3: " << (um2 != um3) << endl;
}

```

**Výstup:**

`um1 != um2: true`

`um1 != um3: false`

`um2 != um3: true`

## <a name="op_eq_eq"></a>  Operator ==

Testy jestli [unordered_map](../standard-library/unordered-map-class.md) objekt na levé straně operátoru rovná unordered_map objekt na pravé straně.

```cpp
bool operator==(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu `unordered_map`.

`right` Objekt typu `unordered_map`.

### <a name="return-value"></a>Návratová hodnota

`true` Pokud unordered_maps stejný; `false` Pokud nejsou stejné.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty unordered_map nemá vliv libovolný pořadí, ve kterém budou ukládat jejich elementů. Pokud mají stejný počet elementů a prvky v jednom kontejneru jsou Permutace elementů v kontejneru další dva unordered_maps jsou si rovny. Jinak nerovné.

### <a name="example"></a>Příklad

```cpp
// unordered_map_op_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_map<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i+1, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i+1 ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i+1, i ) );
   }

   cout << boolalpha;
   cout << "um1 == um2: " << (um1 == um2) << endl;
   cout << "um1 == um3: " << (um1 == um3) << endl;
   cout << "um2 == um3: " << (um2 == um3) << endl;
}

```

**Výstup:**

`um1 == um2: false`

`um1 == um3: true`

`um2 == um3: false`

## <a name="op_neq_multimap"></a>  Operator! =

Testy jestli [unordered_multimap](../standard-library/unordered-multimap-class.md) objekt na levé straně operátoru není stejný jako unordered_multimap objekt na pravé straně.

```cpp
bool operator!=(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu `unordered_multimap`.

`right` Objekt typu `unordered_multimap`.

### <a name="return-value"></a>Návratová hodnota

`true` Pokud unordered_multimaps není stejný; `false` Pokud jsou stejné.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty unordered_multimap nemá vliv libovolný pořadí, ve kterém budou ukládat jejich elementů. Pokud mají stejný počet elementů a prvky v jednom kontejneru jsou Permutace elementů v kontejneru další dva unordered_multimaps jsou si rovny. Jinak nejsou stejné.

### <a name="example"></a>Příklad

```cpp
// unordered_multimap_op_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_multimap<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i, i ) );
   }

   cout << boolalpha;
   cout << "um1 != um2: " << (um1 != um2) << endl;
   cout << "um1 != um3: " << (um1 != um3) << endl;
   cout << "um2 != um3: " << (um2 != um3) << endl;
}

```

**Výstup:**

`um1 != um2: true`

`um1 != um3: false`

`um2 != um3: true`

## <a name="op_eq_eq_multimap"></a>  Operator ==

Testy jestli [unordered_multimap](../standard-library/unordered-multimap-class.md) objekt na levé straně operátoru rovná unordered_multimap objekt na pravé straně.

```cpp
bool operator==(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu `unordered_multimap`.

`right` Objekt typu `unordered_multimap`.

### <a name="return-value"></a>Návratová hodnota

`true` Pokud unordered_multimaps stejný; `false` Pokud nejsou stejné.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty unordered_multimap nemá vliv libovolný pořadí, ve kterém budou ukládat jejich elementů. Pokud mají stejný počet elementů a prvky v jednom kontejneru jsou Permutace elementů v kontejneru další dva unordered_multimaps jsou si rovny. Jinak nerovné.

### <a name="example"></a>Příklad

```cpp
// unordered_multimap_op_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_multimap<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i, i ) );
   }

   cout << boolalpha;
   cout << "um1 == um2: " << (um1 == um2) << endl;
   cout << "um1 == um3: " << (um1 == um3) << endl;
   cout << "um2 == um3: " << (um2 == um3) << endl;
}

```

**Výstup:**

`um1 == um2: false`

`um1 == um3: true`

`um2 == um3: false`

## <a name="see-also"></a>Viz také

[<unordered_map>](../standard-library/unordered-map.md)<br/>
