---
title: add_pointer – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_pointer
helpviewer_keywords:
- add_pointer class
- add_pointer
ms.assetid: d8095cb0-6578-4143-b78f-87f82485298c
ms.openlocfilehash: fda2bcbd3484b9244d69358aac3e9baf5d37a4ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566007"
---
# <a name="addpointer-class"></a>add_pointer – třída

Vytvoří ukazatel na typ z určeného typu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct add_pointer;

template <class T>
using add_pointer_t = typename add_pointer<T>::type;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ, který chcete upravit.

## <a name="remarks"></a>Poznámky

Člen **typedef** `type` pojmenovává stejný typ jako `remove_reference<T>::type*`. Alias `add_pointer_t` je zástupce pro přístup k členu **typedef** `type`.

Protože je vytvořit ukazatel z odkazu, `add_pointer` odebere odkaz, pokud existuje, z určeného typu dříve, než se provede ukazatel na typ. V důsledku toho můžete použít typ s `add_pointer` bez nutnosti zabývat o tom, zda je typ odkaz.

## <a name="example"></a>Příklad

Následující příklad ukazuje, že `add_pointer` typu je stejné jako ukazatel na typu.

```cpp
#include <type_traits>
#include <iostream>

int main()
{
    std::add_pointer_t<int> *p = (int **)0;

    p = p;  // to quiet "unused" warning
    std::cout << "add_pointer_t<int> == "
        << typeid(*p).name() << std::endl;

    return (0);
}
```

```Output
add_pointer_t<int> == int *
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_pointer – třída](../standard-library/remove-pointer-class.md)<br/>
