---
title: add_cv – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::add_cv
dev_langs:
- C++
helpviewer_keywords:
- add_cv class
- add_cv
ms.assetid: a5572c78-a097-45d7-b476-ed4876889dea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8b138424f3394c940307b422f590648c661d037d
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38958140"
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

*T* typ, který chcete upravit.

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

**Záhlaví:** \<type_traits > **Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_const – třída](../standard-library/remove-const-class.md)<br/>
[remove_volatile – třída](../standard-library/remove-volatile-class.md)<br/>
