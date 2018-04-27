---
title: add_const – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- type_traits/std::add_const
dev_langs:
- C++
helpviewer_keywords:
- add_const class
- add_const
ms.assetid: 1262a1eb-8c9c-4dd6-9f43-88ba280182f1
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 949b6fae3148aa12bee001a57fb92189f9ade0ed
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="addconst-class"></a>add_const – třída

Díky const typ z typu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct add_const;
```

### <a name="parameters"></a>Parametry

`Ty` Typ, který chcete upravit.

## <a name="remarks"></a>Poznámky

Instance typu modifikátor obsahuje upravit – typ, který je `Ty` Pokud `Ty` je odkaz, funkci nebo kvalifikovaný const typu, jinak `const Ty`.

## <a name="example"></a>Příklad

```cpp
// std__type_traits__add_const.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main()
{
    std::add_const<int>::type *p = (const int *)0;

    p = p;  // to quiet "unused" warning
    std::cout << "add_const<int> == "
        << typeid(*p).name() << std::endl;

    return (0);
}
```

```Output
add_const<int> == int
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_const – třída](../standard-library/remove-const-class.md)<br/>
