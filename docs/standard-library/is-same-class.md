---
title: is_same – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_same
helpviewer_keywords:
- is_same class
- is_same
ms.assetid: d9df6c1d-c270-4ec2-802a-af275648dd1d
ms.openlocfilehash: f4e4babeef89960762ebb2ccf0f733f60eadfa47
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450048"
---
# <a name="issame-class"></a>is_same – třída

Testuje, zda jsou dva typy stejné.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty1, class Ty2>
struct is_same;
```

### <a name="parameters"></a>Parametry

*Ty1*\
První typ dotazu.

*TY2*\
Druhý typ pro dotazování.

## <a name="remarks"></a>Poznámky

Instance predikátu typu má hodnotu true, pokud typy *Ty1* a *TY2* mají stejný typ, jinak obsahuje false.

## <a name="example"></a>Příklad

```cpp
// std__type_traits__is_same.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct base
    {
    int val;
    };

struct derived
    : public base
    {
    };

int main()
    {
    std::cout << "is_same<base, base> == " << std::boolalpha
        << std::is_same<base, base>::value << std::endl;
    std::cout << "is_same<base, derived> == " << std::boolalpha
        << std::is_same<base, derived>::value << std::endl;
    std::cout << "is_same<derived, base> == " << std::boolalpha
        << std::is_same<derived, base>::value << std::endl;
    std::cout << "is_same<int, int> == " << std::boolalpha
        << std::is_same<int, int>::value << std::endl;
    std::cout << "is_same<int, const int> == " << std::boolalpha
        << std::is_same<int, const int>::value << std::endl;

    return (0);
    }
```

```Output
is_same<base, base> == true
is_same<base, derived> == false
is_same<derived, base> == false
is_same<int, int> == true
is_same<int, const int> == false
```

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[< type_traits >](../standard-library/type-traits.md)\
[is_convertible – třída](../standard-library/is-convertible-class.md)\
[is_base_of – třída](../standard-library/is-base-of-class.md)
