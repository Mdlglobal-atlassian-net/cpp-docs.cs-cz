---
title: '&lt;funkčních&gt;ch operátorů'
ms.date: 11/04/2016
f1_keywords:
- functional/std::operator!=
- functional/std::operator==
helpviewer_keywords:
- functional operators
ms.assetid: d4b3c760-f3e2-4b65-bdaa-d42e8dd6f5e1
ms.openlocfilehash: b396e5c692129821c0deb9aef9469a5c54e600b0
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876345"
---
# <a name="ltfunctionalgt-operators"></a>&lt;funkčních&gt;ch operátorů

## <a name="op_eq_eq"></a>operator = = – operátor

Testuje, zda je objekt pro vyvýšení prázdný.

```cpp
template <class Fty>
    bool operator==(const function<Fty>& f, null_ptr_type npc);

template <class Fty>
    bool operator==(null_ptr_type npc, const function<Fty>& f);
```

### <a name="parameters"></a>Parametry

*Fty*\
Typ funkce, která se má zabalit

\ *f*
Objekt funkce

*npc*\
Ukazatel s hodnotou null.

### <a name="remarks"></a>Poznámky

Operátory přebírají argument, který je odkazem na objekt `function` a argument, který je konstantou s ukazatelem NULL. Vrátí hodnotu true pouze v případě, že objekt `function` je prázdný.

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

## <a name="op_neq"></a>! = – operátor

Testuje, zda je objekt pro vyvýšení neprázdný.

```cpp
template <class Fty>
    bool operator!=(const function<Fty>& f, null_ptr_type npc);

template <class Fty>
    bool operator!=(null_ptr_type npc, const function<Fty>& f);
```

### <a name="parameters"></a>Parametry

*Fty*\
Typ funkce, která se má zabalit

\ *f*
Objekt funkce

*npc*\
Ukazatel s hodnotou null.

### <a name="remarks"></a>Poznámky

Operátory přebírají argument, který je odkazem na objekt `function` a argument, který je konstantou s ukazatelem NULL. Vrátí hodnotu true pouze v případě, že objekt `function` není prázdný.

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
