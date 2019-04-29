---
title: extent – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::extent
helpviewer_keywords:
- extent class
- extent
ms.assetid: 6d16263d-90b2-4330-9ec7-b59ed898792d
ms.openlocfilehash: 7463b424d15ee86f851b7d81953abf3fe1c98fee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393971"
---
# <a name="extent-class"></a>extent – třída

Získá rozměr pole.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty, unsigned I = 0>
struct extent;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ, na který chcete odeslat dotaz.

*I*<br/>
Pole vázané k dotazování.

## <a name="remarks"></a>Poznámky

Pokud *Ty* je typ pole, které mají alespoň *můžu* dimenze, typ dotazu obsahuje počet prvků v dimenzi určené *můžu*. Pokud *Ty* není typem pole nebo jeho pořadí je menší než *můžu*, nebo pokud *můžu* je nula a *Ty* je typu "mez pole neznámé `U` ", dotaz typu obsahuje hodnotu 0.

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

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_all_extents – třída](../standard-library/remove-all-extents-class.md)<br/>
[remove_extent – třída](../standard-library/remove-extent-class.md)<br/>
