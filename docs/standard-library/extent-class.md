---
title: Extent – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::extent
dev_langs:
- C++
helpviewer_keywords:
- extent class
- extent
ms.assetid: 6d16263d-90b2-4330-9ec7-b59ed898792d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7fb721b23f473c59051e72edc969e5de38f1c984
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="extent-class"></a>extent – třída

Získá rozměru pole.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty, unsigned I = 0>
struct extent;
```

### <a name="parameters"></a>Parametry

`Ty` Typ k dotazu.

`I` Pole vázán k dotazu.

## <a name="remarks"></a>Poznámky

Pokud `Ty` je typ pole, která má nejméně `I` dimenze typu dotaz obsahuje počet elementů v dimenzi určeného `I`. Pokud `Ty` není typu pole nebo je jeho pořadí menší než `I`, nebo pokud `I` rovná nule a `Ty` je typu "pole Neznámý hranice elementu `U`", typ dotazu obsahuje hodnotu 0.

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

**Namespace:** – std

## <a name="see-also"></a>Viz také

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_all_extents – třída](../standard-library/remove-all-extents-class.md)<br/>
[remove_extent – třída](../standard-library/remove-extent-class.md)<br/>
