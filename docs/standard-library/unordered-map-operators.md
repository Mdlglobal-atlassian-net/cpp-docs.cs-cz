---
title: '&lt;unordered_map&gt; operátory'
ms.date: 11/04/2016
f1_keywords:
- unordered_map/std::operator!=
- unordered_map/std::operator==
ms.assetid: 9d5add0b-84bd-4a79-bd82-3f58b55145ed
ms.openlocfilehash: fe4877bc5b371a2570c18950bac36a003078ccc7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454770"
---
# <a name="ltunorderedmapgt-operators"></a>&lt;unordered_map&gt; operátory

|||||
|-|-|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|[operator!=](#op_neq_multimap)|[operator==](#op_eq_eq_multimap)|

## <a name="op_neq"></a>! = – operátor

Testuje, zda objekt [unordered_map](../standard-library/unordered-map-class.md) na levé straně operátoru není roven objektu unordered_map na pravé straně.

```cpp
bool operator!=(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*zbývá*\
Objekt typu `unordered_map`.

*Kliknutím*\
Objekt typu `unordered_map`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud se unordered_maps nerovná; **false** , pokud jsou stejné.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty unordered_map není ovlivněno libovolným pořadím, ve kterém ukládají jejich prvky. Dva unordered_maps jsou stejné, pokud mají stejný počet prvků a prvky v jednom kontejneru jsou permutací prvků v druhém kontejneru. V opačném případě jsou nerovné.

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

## <a name="op_eq_eq"></a>operator = = – operátor

Testuje, zda je objekt [unordered_map](../standard-library/unordered-map-class.md) na levé straně operátoru roven objektu unordered_map na pravé straně.

```cpp
bool operator==(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*zbývá*\
Objekt typu `unordered_map`.

*Kliknutím*\
Objekt typu `unordered_map`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud jsou unordered_maps stejné; **false** , pokud se neshodují.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty unordered_map není ovlivněno libovolným pořadím, ve kterém ukládají jejich prvky. Dva unordered_maps jsou stejné, pokud mají stejný počet prvků a prvky v jednom kontejneru jsou permutací prvků v druhém kontejneru. V opačném případě jsou nerovné.

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

## <a name="op_neq_multimap"></a>! = – operátor

Testuje, zda objekt [unordered_multimap](../standard-library/unordered-multimap-class.md) na levé straně operátoru není roven objektu unordered_multimap na pravé straně.

```cpp
bool operator!=(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*zbývá*\
Objekt typu `unordered_multimap`.

*Kliknutím*\
Objekt typu `unordered_multimap`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud se unordered_multimaps nerovná; **false** , pokud jsou stejné.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty unordered_multimap není ovlivněno libovolným pořadím, ve kterém ukládají jejich prvky. Dva unordered_multimaps jsou stejné, pokud mají stejný počet prvků a prvky v jednom kontejneru jsou permutací prvků v druhém kontejneru. V opačném případě se neshodují.

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

## <a name="op_eq_eq_multimap"></a>operator = = – operátor

Testuje, zda je objekt [unordered_multimap](../standard-library/unordered-multimap-class.md) na levé straně operátoru roven objektu unordered_multimap na pravé straně.

```cpp
bool operator==(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*zbývá*\
Objekt typu `unordered_multimap`.

*Kliknutím*\
Objekt typu `unordered_multimap`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud jsou unordered_multimaps stejné; **false** , pokud se neshodují.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty unordered_multimap není ovlivněno libovolným pořadím, ve kterém ukládají jejich prvky. Dva unordered_multimaps jsou stejné, pokud mají stejný počet prvků a prvky v jednom kontejneru jsou permutací prvků v druhém kontejneru. V opačném případě jsou nerovné.

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

## <a name="see-also"></a>Viz také:

[<unordered_map>](../standard-library/unordered-map.md)
