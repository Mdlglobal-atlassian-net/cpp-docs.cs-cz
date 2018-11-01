---
title: remove_all_extents – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::remove_all_extents
helpviewer_keywords:
- remove_all_extents class
- remove_all_extents
ms.assetid: 548dc536-82e7-423a-b8c1-443d66d9632e
ms.openlocfilehash: 1c8972889272a4621d6357758cde6d174bb2abd7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568074"
---
# <a name="removeallextents-class"></a>remove_all_extents – třída

Vytvoří typ bez pole z typu pole.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct remove_all_extents;

template <class T>
using remove_all_extents_t = typename remove_all_extents<T>::type;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ, který chcete upravit.

## <a name="remarks"></a>Poznámky

Instance `remove_all_extents<T>` obsahuje změněný typ, který je typem elementu pole *T* s odebrány, všechny dimenze pole nebo *T* Pokud *T* není typem pole.

## <a name="example"></a>Příklad

```cpp
#include <type_traits>
#include <iostream>

int main()
    {
    std::cout << "remove_all_extents<int> == "
        << typeid(std::remove_all_extents_t<int>).name()
        << std::endl;
    std::cout << "remove_all_extents_t<int[5]> == "
        << typeid(std::remove_all_extents_t<int[5]>).name()
        << std::endl;
    std::cout << "remove_all_extents_t<int[5][10]> == "
        << typeid(std::remove_all_extents_t<int[5][10]>).name()
        << std::endl;

    return (0);
    }
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_extent – třída](../standard-library/remove-extent-class.md)<br/>
