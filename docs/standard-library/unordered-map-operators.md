---
title: '&lt;unordered_map –&gt; operátory | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- unordered_map/std::operator!=
- unordered_map/std::operator==
dev_langs:
- C++
ms.assetid: 9d5add0b-84bd-4a79-bd82-3f58b55145ed
ms.openlocfilehash: d74eaf0c0f2a431bc481341ce5160d07ee0a4bb5
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45701425"
---
# <a name="ltunorderedmapgt-operators"></a>&lt;unordered_map –&gt; operátory

|||||
|-|-|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|[operator!=](#op_neq_multimap)|[operator==](#op_eq_eq_multimap)|

## <a name="op_neq"></a>  Operator! =

Testy, jestli [unordered_map](../standard-library/unordered-map-class.md) objekt na levé straně operátoru není roven objektu unordered_map na pravé straně.

```cpp
bool operator!=(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `unordered_map`.

*doprava*<br/>
Objekt typu `unordered_map`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud unordered_maps nejsou stejné; **false** jestli jsou shodné.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty unordered_map nemá vliv libovolného pořadí, ve kterém jsou v nich uložené jejich prvky. Pokud mají stejný počet prvků a elementů do jednoho kontejneru jsou permutaci prvků v jiném kontejneru dvě unordered_maps jsou si rovny. V opačném případě nerovnost.

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

Testy, jestli [unordered_map](../standard-library/unordered-map-class.md) je objekt na levé straně operátoru roven objektu unordered_map na pravé straně.

```cpp
bool operator==(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `unordered_map`.

*doprava*<br/>
Objekt typu `unordered_map`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud unordered_maps rovnají. **false** Pokud nejsou stejné.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty unordered_map nemá vliv libovolného pořadí, ve kterém jsou v nich uložené jejich prvky. Pokud mají stejný počet prvků a elementů do jednoho kontejneru jsou permutaci prvků v jiném kontejneru dvě unordered_maps jsou si rovny. V opačném případě nerovnost.

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

Testy, jestli [unordered_multimap](../standard-library/unordered-multimap-class.md) objekt na levé straně operátoru není roven objektu unordered_multimap na pravé straně.

```cpp
bool operator!=(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `unordered_multimap`.

*doprava*<br/>
Objekt typu `unordered_multimap`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud unordered_multimaps nejsou stejné; **false** jestli jsou shodné.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty unordered_multimap nemá vliv libovolného pořadí, ve kterém jsou v nich uložené jejich prvky. Pokud mají stejný počet prvků a elementů do jednoho kontejneru jsou permutaci prvků v jiném kontejneru dvě unordered_multimaps jsou si rovny. V opačném případě nejsou stejné.

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

Testy, jestli [unordered_multimap](../standard-library/unordered-multimap-class.md) je objekt na levé straně operátoru roven objektu unordered_multimap na pravé straně.

```cpp
bool operator==(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `unordered_multimap`.

*doprava*<br/>
Objekt typu `unordered_multimap`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud unordered_multimaps rovnají. **false** Pokud nejsou stejné.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty unordered_multimap nemá vliv libovolného pořadí, ve kterém jsou v nich uložené jejich prvky. Pokud mají stejný počet prvků a elementů do jednoho kontejneru jsou permutaci prvků v jiném kontejneru dvě unordered_multimaps jsou si rovny. V opačném případě nerovnost.

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

[<unordered_map>](../standard-library/unordered-map.md)<br/>
