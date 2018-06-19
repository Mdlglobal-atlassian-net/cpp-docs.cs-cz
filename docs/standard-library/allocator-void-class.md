---
title: Allocator&lt;void&gt; třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- memory/std::allocator<void>
- allocator<void>
dev_langs:
- C++
helpviewer_keywords:
- allocator<void> class
ms.assetid: abfb40f5-c600-46a6-b130-f42c6535b2bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c4179ddae0506d21ca3969559b05c618ab4d73e0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33846542"
---
# <a name="allocatorltvoidgt-class"></a>Allocator&lt;void&gt; – třída

Specializace allocator – třída šablony na typ `void`, definování typů, které dávají smysl v tomto kontextu.

## <a name="syntax"></a>Syntaxe

```cpp
template <>
class allocator<void> {
    typedef void *pointer;
    typedef const void *const_pointer;
    typedef void value_type;
    template <class Other>
    struct rebind;
    allocator();
    allocator(const allocator<void>&);

    template <class Other>
    allocator(const allocator<Other>&);

    template <class Other>
    allocator<void>& operator=(const allocator<Other>&);
};
```

## <a name="remarks"></a>Poznámky

Třída explicitně se specializuje šablony třídy [allocator](../standard-library/allocator-class.md) pro typ *void.* Jeho konstruktory a operátor přiřazení chovají stejně jako u šablony třídy, ale definuje jen následující typy:

- [const_pointer –](../standard-library/allocator-class.md#const_pointer).

- [ukazatel](../standard-library/allocator-class.md#pointer).

- [value_type](../standard-library/allocator-class.md#value_type).

- [rebind](../standard-library/allocator-class.md#rebind), vnořené třídy šablony.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<paměti >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
