---
title: remove_reference – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::remove_reference
dev_langs:
- C++
helpviewer_keywords:
- remove_reference class
- remove_reference
ms.assetid: 294e1965-3ae3-46ee-bc42-4fdf60c24717
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 343acc8d23e2b67c1e9f7556ffe2268c94bb3c63
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957899"
---
# <a name="removereference-class"></a>remove_reference – třída

Vytvoří typ bez odkazu z typu

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct remove_reference;

template <class T>
using remove_reference_t = typename remove_reference<T>::type;
```

### <a name="parameters"></a>Parametry

*T* typ, který chcete upravit.

## <a name="remarks"></a>Poznámky

Instance `remove_reference<T>` obsahuje změněný typ, který je `T1` při *T* má formu `T1&`, jinak *T*.

## <a name="example"></a>Příklad

```cpp
#include <type_traits>
#include <iostream>

int main()
    {
    int *p = (std::remove_reference_t<int&> *)0;

    p = p;  // to quiet "unused" warning
    std::cout << "remove_reference_t<int&> == "
        << typeid(*p).name() << std::endl;

    return (0);
    }
```

```Output
remove_reference_t<int&> == int
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
[add_lvalue_reference – třída](../standard-library/add-lvalue-reference-class.md)<br/>
