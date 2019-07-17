---
title: '&lt;unordered_set –&gt; operátory'
ms.date: 11/04/2016
f1_keywords:
- unordered_set/std::operator!=
- unordered_set/std::operator==
ms.assetid: 8653eea6-12f2-4dd7-aa2f-db38a71599a0
ms.openlocfilehash: 59a7154ed46ac788516bc9f42c3385ec8f07dcf1
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243422"
---
# <a name="ltunorderedsetgt-operators"></a>&lt;unordered_set –&gt; operátory

## <a name="op_neq"></a> Operator! =

Testy, jestli [unordered_set](../standard-library/unordered-set-class.md) objekt na levé straně operátoru není roven objektu unordered_set na pravé straně.

```cpp
bool operator!=(const unordered_set <Key, Hash, Pred, Allocator>& left, const unordered_set <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*\
Objekt typu `unordered_set`.

*doprava*\
Objekt typu `unordered_set`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud unordered_sets nejsou stejné; **false** jestli jsou shodné.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty unordered_set – nemá vliv libovolného pořadí, ve kterém jsou v nich uložené jejich prvky. Pokud mají stejný počet prvků a elementů do jednoho kontejneru jsou permutaci prvků v jiném kontejneru dvě unordered_sets jsou si rovny. V opačném případě nerovnost.

### <a name="example"></a>Příklad

```cpp
// unordered_set_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_set<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 != c2: " << (c1 != c2) << endl;
   cout << "c1 != c3: " << (c1 != c3) << endl;
   cout << "c2 != c3: " << (c2 != c3) << endl;

    return (0);
}
```

**Výstup:**

`c1 != c2: true`

`c1 != c3: false`

`c2 != c3: true`

## <a name="op_eq_eq"></a> Operator ==

Testy, jestli [unordered_set](../standard-library/unordered-set-class.md) je objekt na levé straně operátoru roven objektu unordered_set na pravé straně.

```cpp
bool operator==(const unordered_set <Key, Hash, Pred, Allocator>& left, const unordered_set <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*\
Objekt typu `unordered_set`.

*doprava*\
Objekt typu `unordered_set`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud unordered_sets rovnají. **false** Pokud nejsou stejné.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty unordered_set – nemá vliv libovolného pořadí, ve kterém jsou v nich uložené jejich prvky. Pokud mají stejný počet prvků a elementů do jednoho kontejneru jsou permutaci prvků v jiném kontejneru dvě unordered_sets jsou si rovny. V opačném případě nerovnost.

### <a name="example"></a>Příklad

```cpp
// unordered_set_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_set<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 == c2: " << (c1 == c2) << endl;
   cout << "c1 == c3: " << (c1 == c3) << endl;
   cout << "c2 == c3: " << (c2 == c3) << endl;

    return (0);
}
```

```Output
c1 == c2: false
c1 == c3: true
c2 == c3: false
```

## <a name="op_neq_unordered_multiset"></a> Operator! =

Testy, jestli [unordered_multiset](../standard-library/unordered-multiset-class.md) objekt na levé straně operátoru není roven objektu unordered_multiset na pravé straně.

```cpp
bool operator!=(const unordered_multiset <Key, Hash, Pred, Allocator>& left, const unordered_multiset <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*\
Objekt typu `unordered_multiset`.

*doprava*\
Objekt typu `unordered_multiset`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud unordered_multisets nejsou stejné; **false** jestli jsou shodné.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty unordered_multiset – nemá vliv libovolného pořadí, ve kterém jsou v nich uložené jejich prvky. Pokud mají stejný počet prvků a elementů do jednoho kontejneru jsou permutaci prvků v jiném kontejneru dvě unordered_multisets jsou si rovny. V opačném případě nerovnost.

### <a name="example"></a>Příklad

```cpp
// unordered_multiset_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_multiset<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');
    c1.insert('c');

    c2.insert('c');
    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 != c2: " << (c1 != c2) << endl;
   cout << "c1 != c3: " << (c1 != c3) << endl;
   cout << "c2 != c3: " << (c2 != c3) << endl;

    return (0);
}
```

```Output
c1 != c2: true
c1 != c3: false
c2 != c3: true
```

## <a name="op_eq_eq_unordered_multiset"></a> Operator ==

Testy, jestli [unordered_multiset](../standard-library/unordered-multiset-class.md) je objekt na levé straně operátoru roven objektu unordered_multiset na pravé straně.

```cpp
bool operator==(const unordered_multiset <Key, Hash, Pred, Allocator>& left, const unordered_multiset <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*\
Objekt typu `unordered_multiset`.

*doprava*\
Objekt typu `unordered_multiset`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud unordered_multisets rovnají. **false** Pokud nejsou stejné.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty unordered_multiset – nemá vliv libovolného pořadí, ve kterém jsou v nich uložené jejich prvky. Pokud mají stejný počet prvků a elementů do jednoho kontejneru jsou permutaci prvků v jiném kontejneru dvě unordered_multisets jsou si rovny. V opačném případě nerovnost.

### <a name="example"></a>Příklad

```cpp
// unordered_multiset_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_multiset<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');
    c1.insert('c');

    c2.insert('c');
    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 == c2: " << (c1 == c2) << endl;
   cout << "c1 == c3: " << (c1 == c3) << endl;
   cout << "c2 == c3: " << (c2 == c3) << endl;

    return (0);
}
```

```Output
c1 == c2: false
c1 == c3: true
c2 == c3: false
```
