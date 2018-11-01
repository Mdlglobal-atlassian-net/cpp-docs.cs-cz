---
title: add_cv – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_cv
helpviewer_keywords:
- add_cv class
- add_cv
ms.assetid: a5572c78-a097-45d7-b476-ed4876889dea
ms.openlocfilehash: 37001815710b197ec77ed0d45a16ea971ad1edce
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613191"
---
# <a name="addcv-class"></a>add_cv – třída

Díky **const volatile** typ z typu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct add_cv;

template <class T>
using add_cv_t = typename add_cv<T>::type;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ, který chcete upravit.

## <a name="remarks"></a>Poznámky

Instance typu upravené `add_cv<T>` má `type` člen **– typedef** ekvivalentní *T* upravil obě [add_volatile –](../standard-library/add-volatile-class.md) a [ add_const –](../standard-library/add-const-class.md), není-li *T* již obsahuje kvalifikátory cv, odkazem nebo je funkce.

`add_cv_t<T>` Pomocné rutiny typ je zkratka pro přístup k `add_cv<T>` definice typu člena `type`.

## <a name="example"></a>Příklad

```cpp
// add_cv.cpp
// compile by using: cl /EHsc /W4 add_cv.cpp
#include <type_traits>
#include <iostream>

struct S {
    void f() {
        std::cout << "invoked non-cv-qualified S.f()" << std::endl;
    }
    void f() const {
        std::cout << "invoked const S.f()" << std::endl;
    }
    void f() volatile {
        std::cout << "invoked volatile S.f()" << std::endl;
    }
    void f() const volatile {
        std::cout << "invoked const volatile S.f()" << std::endl;
    }
};

template <class T>
void invoke() {
    T t;
    ((T *)&t)->f();
}

int main()
{
    invoke<S>();
    invoke<std::add_const<S>::type>();
    invoke<std::add_volatile<S>::type>();
    invoke<std::add_cv<S>::type>();
}
```

```Output
invoked non-cv-qualified S.f()
invoked const S.f()
invoked volatile S.f()
invoked const volatile S.f()
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_const – třída](../standard-library/remove-const-class.md)<br/>
[remove_volatile – třída](../standard-library/remove-volatile-class.md)<br/>
