---
title: add_pointer – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::add_pointer
dev_langs:
- C++
helpviewer_keywords:
- add_pointer class
- add_pointer
ms.assetid: d8095cb0-6578-4143-b78f-87f82485298c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 85efc646daf6ddb55f37c1f46157671eda2f13a8
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963573"
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

*T* typ, který chcete upravit.

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
