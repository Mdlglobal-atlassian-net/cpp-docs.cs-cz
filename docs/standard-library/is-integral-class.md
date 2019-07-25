---
title: is_integral – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_integral
helpviewer_keywords:
- is_integral class
- is_integral
ms.assetid: fe9279d0-4495-4e88-bf23-153cc6602397
ms.openlocfilehash: a367bb06f49dd2c9c64f0c257a3573add5645efe
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456241"
---
# <a name="isintegral-class"></a>is_integral – třída

Testuje, zda je typ integrální.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_integral;
```

### <a name="parameters"></a>Parametry

*Ty*\
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu má hodnotu true, *Pokud typ,* který je jedním z celočíselných typů, nebo `cv-qualified` forma jednoho z celočíselných typů, v opačném případě obsahuje hodnotu false.

Celočíselný typ je jeden z hodnot **bool**, **char**, **unsigned char**, **signed char**, **wchar_t**, **short**, **unsigned short**, **int**, **unsigned int**, **Long**a **unsigned long**. Kromě toho s kompilátory, které je poskytují, celočíselný typ může být jeden z **dlouhých**Long, **unsigned long long**, **__int64**a **unsigned __int64**.

## <a name="example"></a>Příklad

```cpp
// std__type_traits__is_integral.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_integral<trivial> == " << std::boolalpha
        << std::is_integral<trivial>::value << std::endl;
    std::cout << "is_integral<int> == " << std::boolalpha
        << std::is_integral<int>::value << std::endl;
    std::cout << "is_integral<float> == " << std::boolalpha
        << std::is_integral<float>::value << std::endl;

    return (0);
    }
```

```Output
is_integral<trivial> == false
is_integral<int> == true
is_integral<float> == false
```

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[< type_traits >](../standard-library/type-traits.md)\
[is_enum – třída](../standard-library/is-enum-class.md)\
[is_floating_point – třída](../standard-library/is-floating-point-class.md)
