---
title: aligned_union – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- type_traits/std::aligned_union
dev_langs:
- C++
helpviewer_keywords:
- aligned_union
ms.assetid: 9931a44d-3a67-4f29-a0f6-d47a7cf560ac
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a1f6672733773e79a7f0b74b0fb6d7fdf80926f2
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="alignedunion-class"></a>aligned_union – třída

Poskytuje typ POD dostatečně velké a vhodně zarovnaný k ukládání union typ a velikost vyžaduje.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Len, class... Types>
struct aligned_union;

template <std::size_t Len, class... Types>
using aligned_union_t = typename aligned_union<Len, Types...>::type;
```

### <a name="parameters"></a>Parametry

`Len` Zarovnání hodnota pro typ největší ve sjednocení.

`Types` Odlišné typy v základní sjednocení.

## <a name="remarks"></a>Poznámky

Použití třídy šablony potřebná pro ukládání sjednocení Neinicializovaný úložiště velikost a zarovnání. Typedef člen `type` názvy POD zadejte vhodný pro ukládání libovolného typu uvedené v `Types`; je minimální velikost `Len`. Statický člen `alignment_value` typu `std::size_t` obsahuje nejpřísnějším zarovnání od všechny typy uvedené v vyžadují `Types`.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat `aligned_union` přidělit vyrovnávací paměť zarovnaný zásobníku umístit spojení.

```cpp
// std__type_traits__aligned_union.cpp
#include <iostream>
#include <type_traits>

union U_type
{
    int i;
    float f;
    double d;
    U_type(float e) : f(e) {}
};

typedef std::aligned_union<16, int, float, double>::type aligned_U_type;

int main()
{
    // allocate memory for a U_type aligned on a 16-byte boundary
    aligned_U_type au;
    // do placement new in the aligned memory on the stack
    U_type* u = new (&au) U_type(1.0f);
    if (nullptr != u)
    {
        std::cout << "value of u->i is " << u->i << std::endl;
        // must clean up placement objects manually!
        u->~U_type();
    }
}
```

```Output
value of u->i is 1065353216
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[<type_traits>](../standard-library/type-traits.md)<br/>
[alignment_of – třída](../standard-library/alignment-of-class.md)<br/>
