---
title: '&lt;unordered_map&gt; operátorů'
ms.date: 11/04/2016
f1_keywords:
- unordered_map/std::operator!=
- unordered_map/std::operator==
ms.assetid: 9d5add0b-84bd-4a79-bd82-3f58b55145ed
ms.openlocfilehash: f062c4fd0332525a8b8940d2d93df41df56d2baa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373128"
---
# <a name="ltunordered_mapgt-operators"></a>&lt;unordered_map&gt; operátorů

|||||
|-|-|-|-|
|[operátor!=](#op_neq)|[operátor==](#op_eq_eq)|[operátor!=](#op_neq_multimap)|[operátor==](#op_eq_eq_multimap)|

## <a name="operator"></a><a name="op_neq"></a>operátor!=

Testuje, zda [unordered_map](../standard-library/unordered-map-class.md) objekt na levé straně operátoru není rovna unordered_map objektu na pravé straně.

```cpp
bool operator!=(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Objekt typu `unordered_map`.

*Právo*\
Objekt typu `unordered_map`.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud unordered_maps nejsou stejné; **false,** pokud jsou si rovni.

### <a name="remarks"></a>Poznámky

Porovnání mezi unordered_map objekty není ovlivněna libovolné pořadí, ve kterém ukládají své prvky. Dvě unordered_maps jsou stejné, pokud mají stejný počet prvků a prvky v jedné nádobě jsou permutace prvků v druhé kontejneru. V opačném případě jsou nerovné.

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

## <a name="operator"></a><a name="op_eq_eq"></a>operátor==

Testuje, zda [unordered_map](../standard-library/unordered-map-class.md) objekt na levé straně operátoru se rovná unordered_map objektu na pravé straně.

```cpp
bool operator==(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Objekt typu `unordered_map`.

*Právo*\
Objekt typu `unordered_map`.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud jsou unordered_maps stejné; **false,** pokud nejsou rovni.

### <a name="remarks"></a>Poznámky

Porovnání mezi unordered_map objekty není ovlivněna libovolné pořadí, ve kterém ukládají své prvky. Dvě unordered_maps jsou stejné, pokud mají stejný počet prvků a prvky v jedné nádobě jsou permutace prvků v druhé kontejneru. V opačném případě jsou nerovné.

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

## <a name="operator"></a><a name="op_neq_multimap"></a>operátor!=

Testuje, zda [unordered_multimap](../standard-library/unordered-multimap-class.md) objekt na levé straně operátoru není rovna unordered_multimap objektu na pravé straně.

```cpp
bool operator!=(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Objekt typu `unordered_multimap`.

*Právo*\
Objekt typu `unordered_multimap`.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud unordered_multimaps nejsou stejné; **false,** pokud jsou si rovni.

### <a name="remarks"></a>Poznámky

Porovnání mezi unordered_multimap objekty není ovlivněna libovolné pořadí, ve kterém ukládají své prvky. Dvě unordered_multimaps jsou stejné, pokud mají stejný počet prvků a prvky v jedné nádobě jsou permutace prvků v druhé kontejneru. V opačném případě nejsou stejné.

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

## <a name="operator"></a><a name="op_eq_eq_multimap"></a>operátor==

Testuje, zda [unordered_multimap](../standard-library/unordered-multimap-class.md) objekt na levé straně operátoru se rovná unordered_multimap objektu na pravé straně.

```cpp
bool operator==(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Objekt typu `unordered_multimap`.

*Právo*\
Objekt typu `unordered_multimap`.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud jsou unordered_multimaps stejné; **false,** pokud nejsou rovni.

### <a name="remarks"></a>Poznámky

Porovnání mezi unordered_multimap objekty není ovlivněna libovolné pořadí, ve kterém ukládají své prvky. Dvě unordered_multimaps jsou stejné, pokud mají stejný počet prvků a prvky v jedné nádobě jsou permutace prvků v druhé kontejneru. V opačném případě jsou nerovné.

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

[<unordered_map>](../standard-library/unordered-map.md)
