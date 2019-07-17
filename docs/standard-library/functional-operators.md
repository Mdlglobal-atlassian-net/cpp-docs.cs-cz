---
title: '&lt;funkční&gt; operátory'
ms.date: 11/04/2016
f1_keywords:
- functional/std::operator!=
- functional/std::operator==
helpviewer_keywords:
- functional operators
ms.assetid: d4b3c760-f3e2-4b65-bdaa-d42e8dd6f5e1
ms.openlocfilehash: b396e5c692129821c0deb9aef9469a5c54e600b0
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243772"
---
# <a name="ltfunctionalgt-operators"></a>&lt;funkční&gt; operátory

## <a name="op_eq_eq"></a> Operator ==

Testuje, zda je volatelný objekt je prázdný.

```cpp
template <class Fty>
    bool operator==(const function<Fty>& f, null_ptr_type npc);

template <class Fty>
    bool operator==(null_ptr_type npc, const function<Fty>& f);
```

### <a name="parameters"></a>Parametry

*Fty*\
Typ funkce zahrnující.

*F*\
Objekt funkce

*NPC*\
Ukazatel s hodnotou null.

### <a name="remarks"></a>Poznámky

Operátory obou přijímají argument, který je odkaz na `function` objekt a argument, který je konstantní ukazatel s hodnotou null. Oba vracejí hodnotu true pouze v případě, `function` objekt je prázdný.

### <a name="example"></a>Příklad

```cpp
// std__functional__operator_eq.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
{
    return (-val);
}

int main()
{
    std::function<int(int)> fn0;
    std::cout << std::boolalpha << "empty == "
        << (fn0 == 0) << std::endl;

    std::function<int(int)> fn1(neg);
    std::cout << std::boolalpha << "empty == "
        << (fn1 == 0) << std::endl;

    return (0);
}
```

```Output
empty == true
empty == false
```

## <a name="op_neq"></a> Operator! =

Testuje, zda je volatelný objekt není prázdný.

```cpp
template <class Fty>
    bool operator!=(const function<Fty>& f, null_ptr_type npc);

template <class Fty>
    bool operator!=(null_ptr_type npc, const function<Fty>& f);
```

### <a name="parameters"></a>Parametry

*Fty*\
Typ funkce zahrnující.

*F*\
Objekt funkce

*NPC*\
Ukazatel s hodnotou null.

### <a name="remarks"></a>Poznámky

Operátory obou přijímají argument, který je odkaz na `function` objekt a argument, který je konstantní ukazatel s hodnotou null. Oba vracejí hodnotu true pouze v případě, `function` objekt není prázdný.

### <a name="example"></a>Příklad

```cpp
// std__functional__operator_ne.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn0;
    std::cout << std::boolalpha << "not empty == "
        << (fn0 != 0) << std::endl;

    std::function<int (int)> fn1(neg);
    std::cout << std::boolalpha << "not empty == "
        << (fn1 != 0) << std::endl;

    return (0);
    }
```

```Output
not empty == false
not empty == true
```
