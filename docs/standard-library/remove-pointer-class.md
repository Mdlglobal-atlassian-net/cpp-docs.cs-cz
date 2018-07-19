---
title: remove_pointer – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::remove_pointer
dev_langs:
- C++
helpviewer_keywords:
- remove_pointer class
- remove_pointer
ms.assetid: 2cd4e417-32fb-4f53-bd16-4e8a98240832
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d9c8ddf5941394a8979832a753ed73cfda5f0876
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38959121"
---
# <a name="removepointer-class"></a>remove_pointer – třída

Vytvoří typ z ukazatele na typ.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct remove_pointer;

template <class T>
using remove_pointer_t = typename remove_pointer<T>::type;
```

### <a name="parameters"></a>Parametry

*T* typ, který chcete upravit.

## <a name="remarks"></a>Poznámky

Instance `remove_pointer<T>` obsahuje změněný typ, který je `T1` při *T* má formu `T1*`, `T1* const`, `T1* volatile`, nebo `T1* const volatile`, jinak *T*.

## <a name="example"></a>Příklad

```cpp
#include <type_traits>
#include <iostream>

int main()
    {
    int *p = (std::remove_pointer_t<int *> *)0;

    p = p;  // to quiet "unused" warning
    std::cout << "remove_pointer_t<int *> == "
        << typeid(*p).name() << std::endl;

    return (0);
    }
```

```Output
remove_pointer_t<int *> == int
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
[add_pointer – třída](../standard-library/add-pointer-class.md)<br/>
