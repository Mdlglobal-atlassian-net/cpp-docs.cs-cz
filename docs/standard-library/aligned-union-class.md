---
title: aligned_union – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::aligned_union
helpviewer_keywords:
- aligned_union
ms.assetid: 9931a44d-3a67-4f29-a0f6-d47a7cf560ac
ms.openlocfilehash: 1a26675879c50440a4955989aca178dbe5049fdf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411107"
---
# <a name="alignedunion-class"></a>aligned_union – třída

Poskytuje typ POD dostatečně velké a vhodně zarovnaný pro uložení typu union a požadovanou velikost.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Len, class... Types>
struct aligned_union;

template <std::size_t Len, class... Types>
using aligned_union_t = typename aligned_union<Len, Types...>::type;
```

### <a name="parameters"></a>Parametry

*Délka*<br/>
Hodnota zarovnání největšího typu ve sjednocení.

*Typy*<br/>
Odlišné typy v podkladové sjednocení.

## <a name="remarks"></a>Poznámky

Třída šablony používají k získávání zarovnání a velikost potřebná k ukládání sjednocení neinicializované úložiště. Definice typu člena `type` názvy POD zadejte vhodný pro uložení libovolného typu, které jsou uvedeny v *typy*; minimální velikost je *Len*. Statický člen `alignment_value` typu `std::size_t` obsahuje nejpřísnější zarovnání požadované pro všechny typy uvedené v *typy*.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat `aligned_union` přidělit vyrovnávací paměť zarovnané zásobníku umístit sjednocení.

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

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
[alignment_of – třída](../standard-library/alignment-of-class.md)<br/>
