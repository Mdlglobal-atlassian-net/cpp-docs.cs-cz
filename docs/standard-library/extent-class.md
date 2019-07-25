---
title: extent – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::extent
helpviewer_keywords:
- extent class
- extent
ms.assetid: 6d16263d-90b2-4330-9ec7-b59ed898792d
ms.openlocfilehash: 0cd53ba8537e706a68ffdcf08df998108266ad20
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457794"
---
# <a name="extent-class"></a>extent – třída

Získá rozměr pole.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty, unsigned I = 0>
struct extent;
```

### <a name="parameters"></a>Parametry

*Ty*\
Typ, na který chcete odeslat dotaz.

*DOŠLO*\
Pole svázané s dotazem

## <a name="remarks"></a>Poznámky

Pokud *je* to typ pole, který má *alespoň dimenzi,* dotaz typu obsahuje počet prvků v dimenzi určené parametrem *I*. Pokud *ty* nejsou typu pole nebo je jeho pořadí menší než *i*, *nebo pokud je* *nula a má* `U`typ "pole neznámé hranice", dotaz typu obsahuje hodnotu 0.

## <a name="example"></a>Příklad

```cpp
// std__type_traits__extent.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main()
    {
    std::cout << "extent 0 == "
        << std::extent<int[5][10]>::value << std::endl;
    std::cout << "extent 1 == "
        << std::extent<int[5][10], 1>::value << std::endl;

    return (0);
    }
```

```Output
extent 0 == 5
extent 1 == 10
```

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[< type_traits >](../standard-library/type-traits.md)\
[remove_all_extents – třída](../standard-library/remove-all-extents-class.md)\
[remove_extent – třída](../standard-library/remove-extent-class.md)
