---
title: add_lvalue_reference – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_lvalue_reference
helpviewer_keywords:
- add_lvalue_reference
ms.assetid: 9933afc2-ad0d-465d-98fe-7d547fa3efe2
ms.openlocfilehash: 6317b6665adb7f3a06da564fcf049d0b64eb42e8
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456564"
---
# <a name="addlvaluereference-class"></a>add_lvalue_reference – třída

Vytvoří odkaz na typ z typu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct add_lvalue_reference;

template <class T>
using add_lvalue_reference_t = typename add_lvalue_reference<T>::type;
```

### <a name="parameters"></a>Parametry

*Š*\
Typ, který chcete upravit.

## <a name="remarks"></a>Poznámky

Instance modifikátoru typu obsahuje upravený typ, který je *t* , pokud *t* je odkaz lvalue, jinak `T&`.

## <a name="example"></a>Příklad

```cpp
#include <type_traits>
#include <iostream>

using namespace std;
int main()
{
    int val = 0;
    add_lvalue_reference_t<int> p = (int&)val;
    p = p;  // to quiet "unused" warning
    cout << "add_lvalue_reference_t<int> == "
        << typeid(p).name() << endl;

    return (0);
}
```

```Output
add_lvalue_reference_t<int> == int
```

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[< type_traits >](../standard-library/type-traits.md)\
[remove_reference – třída](../standard-library/remove-reference-class.md)
