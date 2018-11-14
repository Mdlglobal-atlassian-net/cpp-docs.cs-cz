---
title: is_integral – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_integral
helpviewer_keywords:
- is_integral class
- is_integral
ms.assetid: fe9279d0-4495-4e88-bf23-153cc6602397
ms.openlocfilehash: c7d0d8b8572c26bfa75b9fab81900c0ae21fb932
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51520696"
---
# <a name="isintegral-class"></a>is_integral – třída

Testuje, zda je typ je nedílnou součástí.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_integral;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *Ty* je jedním z celočíselných typů nebo `cv-qualified` formě integrální typy, jinak má hodnotu false.

Celočíselný typ je jednou z **bool**, **char**, **unsigned char**, **podepsané char**, **wchar_t**, **krátký**, **unsigned short**, **int**, **unsigned int**, **dlouhé**a **unsigned long**. Kromě toho s kompilátory, které získají, integrálový typ může být jeden z **long long**, **unsigned long long.**, **__int64**, a **unsigned __int64**.

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

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_enum – třída](../standard-library/is-enum-class.md)<br/>
[is_floating_point – třída](../standard-library/is-floating-point-class.md)<br/>
