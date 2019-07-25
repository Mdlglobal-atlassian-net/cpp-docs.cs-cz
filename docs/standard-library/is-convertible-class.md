---
title: is_convertible – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_convertible
helpviewer_keywords:
- is_convertible class
- is_convertible
ms.assetid: 75614008-1894-42ea-bd57-974399628536
ms.openlocfilehash: c90fe5687992e4df49e8655387cfdd14b40aa529
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454614"
---
# <a name="isconvertible-class"></a>is_convertible – třída

Testuje, zda je jeden typ převoditelné na jiný typ.

## <a name="syntax"></a>Syntaxe

```cpp
template <class From, class To>
struct is_convertible;
```

### <a name="parameters"></a>Parametry

*Výsledkem*\
Typ, ze kterého se má převést.

*Ty*\
Typ, na který se má převést.

## <a name="remarks"></a>Poznámky

Instance predikátu typu má hodnotu true, pokud je výraz `To to = from;`, kde `from` je objekt typu `From`, ve správném formátu.

## <a name="example"></a>Příklad

```cpp
// std__type_traits__is_convertible.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_convertible<trivial, int> == " << std::boolalpha
        << std::is_convertible<trivial, int>::value << std::endl;
    std::cout << "is_convertible<trivial, trivial> == " << std::boolalpha
        << std::is_convertible<trivial, trivial>::value << std::endl;
    std::cout << "is_convertible<char, int> == " << std::boolalpha
        << std::is_convertible<char, int>::value << std::endl;

    return (0);
    }
```

```Output
is_convertible<trivial, int> == false
is_convertible<trivial, trivial> == true
is_convertible<char, int> == true
```

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[< type_traits >](../standard-library/type-traits.md)\
[is_base_of – třída](../standard-library/is-base-of-class.md)
