---
title: operátory &lt;unordered_set&gt;
ms.date: 11/04/2016
f1_keywords:
- unordered_set/std::operator!=
- unordered_set/std::operator==
ms.assetid: 8653eea6-12f2-4dd7-aa2f-db38a71599a0
ms.openlocfilehash: 59a7154ed46ac788516bc9f42c3385ec8f07dcf1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78890726"
---
# <a name="ltunordered_setgt-operators"></a>operátory &lt;unordered_set&gt;

## <a name="op_neq"></a>! = – operátor

Testuje, zda [unordered_set](../standard-library/unordered-set-class.md) objekt na levé straně operátoru není roven objektu unordered_set na pravé straně.

```cpp
bool operator!=(const unordered_set <Key, Hash, Pred, Allocator>& left, const unordered_set <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `unordered_set`.

*pravé*\
Objekt typu `unordered_set`.

### <a name="return-value"></a>Návratová hodnota

**true** , Pokud unordered_sets nejsou stejné; **false** , pokud jsou stejné.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty unordered_set není ovlivněno libovolným pořadím, ve kterém ukládají jejich prvky. Dva unordered_sets jsou stejné, pokud mají stejný počet prvků a prvky v jednom kontejneru jsou permutací prvků v druhém kontejneru. V opačném případě jsou nerovné.

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

**Výkonem**

`c1 != c2: true`

`c1 != c3: false`

`c2 != c3: true`

## <a name="op_eq_eq"></a>operator = = – operátor

Testuje, zda je objekt [unordered_set](../standard-library/unordered-set-class.md) na levé straně operátoru roven objektu unordered_set na pravé straně.

```cpp
bool operator==(const unordered_set <Key, Hash, Pred, Allocator>& left, const unordered_set <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `unordered_set`.

*pravé*\
Objekt typu `unordered_set`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud se unordered_sets rovnají; **false** , pokud se neshodují.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty unordered_set není ovlivněno libovolným pořadím, ve kterém ukládají jejich prvky. Dva unordered_sets jsou stejné, pokud mají stejný počet prvků a prvky v jednom kontejneru jsou permutací prvků v druhém kontejneru. V opačném případě jsou nerovné.

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

## <a name="op_neq_unordered_multiset"></a>! = – operátor

Testuje, zda [unordered_multiset](../standard-library/unordered-multiset-class.md) objekt na levé straně operátoru není roven objektu unordered_multiset na pravé straně.

```cpp
bool operator!=(const unordered_multiset <Key, Hash, Pred, Allocator>& left, const unordered_multiset <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `unordered_multiset`.

*pravé*\
Objekt typu `unordered_multiset`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud unordered_multisets nejsou stejné; **false** , pokud jsou stejné.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty unordered_multiset není ovlivněno libovolným pořadím, ve kterém ukládají jejich prvky. Dva unordered_multisets jsou stejné, pokud mají stejný počet prvků a prvky v jednom kontejneru jsou permutací prvků v druhém kontejneru. V opačném případě jsou nerovné.

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

## <a name="op_eq_eq_unordered_multiset"></a>operator = = – operátor

Testuje, zda je objekt [unordered_multiset](../standard-library/unordered-multiset-class.md) na levé straně operátoru roven objektu unordered_multiset na pravé straně.

```cpp
bool operator==(const unordered_multiset <Key, Hash, Pred, Allocator>& left, const unordered_multiset <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `unordered_multiset`.

*pravé*\
Objekt typu `unordered_multiset`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud se unordered_multisets rovnají; **false** , pokud se neshodují.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty unordered_multiset není ovlivněno libovolným pořadím, ve kterém ukládají jejich prvky. Dva unordered_multisets jsou stejné, pokud mají stejný počet prvků a prvky v jednom kontejneru jsou permutací prvků v druhém kontejneru. V opačném případě jsou nerovné.

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
