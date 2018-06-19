---
title: '&lt;funkční&gt; operátory | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- functional/std::operator!=
- functional/std::operator==
dev_langs:
- C++
helpviewer_keywords:
- functional operators
ms.assetid: d4b3c760-f3e2-4b65-bdaa-d42e8dd6f5e1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e84ed8ed97a529d67c6d136fd8464cd13c8a502
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845216"
---
# <a name="ltfunctionalgt-operators"></a>&lt;funkční&gt; operátory

|||
|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|

## <a name="op_eq_eq"></a>  Operator ==

Testy, pokud je možné volat objektu prázdný.

```cpp
template <class Fty>
bool operator==(const function<Fty>& f, null_ptr_type npc);

template <class Fty>
bool operator==(null_ptr_type npc, const function<Fty>& f);
```

### <a name="parameters"></a>Parametry

`Fty` Typ funkce zabalit.

`f` Objekt – funkce

`npc` Ukazatel s hodnotou null.

### <a name="remarks"></a>Poznámky

Operátory obou trvat argument, který je odkaz na `function` objekt a argument, který je konstanta ukazatele null. Obě vrací hodnotu true pouze v případě `function` objekt je prázdný.

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

## <a name="op_neq"></a>  Operator! =

Testy, pokud je možné volat objekt není prázdný.

```cpp
template <class Fty>
bool operator!=(const function<Fty>& f, null_ptr_type npc);

template <class Fty>
bool operator!=(null_ptr_type npc, const function<Fty>& f);
```

### <a name="parameters"></a>Parametry

`Fty` Typ funkce zabalit.

`f` Objekt – funkce

`npc` Ukazatel s hodnotou null.

### <a name="remarks"></a>Poznámky

Operátory obou trvat argument, který je odkaz na `function` objekt a argument, který je konstanta ukazatele null. Obě vrací hodnotu true pouze v případě `function` objekt není prázdný.

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

## <a name="see-also"></a>Viz také

[\<funkční >](../standard-library/functional.md)<br/>
