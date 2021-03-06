---
title: aligned_union – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::aligned_union
helpviewer_keywords:
- aligned_union
ms.assetid: 9931a44d-3a67-4f29-a0f6-d47a7cf560ac
ms.openlocfilehash: ae03802549f7791e51dccf1ea98a7b18929a4a4b
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72690112"
---
# <a name="aligned_union-class"></a>aligned_union – třída

Poskytuje typ POD dostatečně velký a vhodně zarovnaný k uložení typu sjednocení a požadované velikosti.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Len, class... Types>
struct aligned_union;

template <std::size_t Len, class... Types>
using aligned_union_t = typename aligned_union<Len, Types...>::type;
```

### <a name="parameters"></a>Parametry

*Délka* \
Hodnota zarovnání pro největší typ ve sjednocení.

@No__t_1 *typů*
Různé typy v základním sjednocení.

## <a name="remarks"></a>Poznámky

Pomocí šablony třídy získáte zarovnání a velikost potřebnou k uložení sjednocení do neinicializovaného úložiště. Definice typedef člena `type` pojmenovává typ POD, který je vhodný pro úložiště libovolného typu uvedeného v *typech*. minimální velikost je *len*. Statický člen `alignment_value` typu `std::size_t` obsahuje nejpřísnější zarovnání vyžadované všemi typy uvedenými v *typech*.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít `aligned_union` k přidělení vyrovnávací paměti zarovnané zásobníku pro vložení sjednocení.

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

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[< type_traits >](../standard-library/type-traits.md) \
[alignment_of – třída](../standard-library/alignment-of-class.md)
