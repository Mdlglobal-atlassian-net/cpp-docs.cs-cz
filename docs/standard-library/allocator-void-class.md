---
title: Allocator&lt;void&gt; třídy
ms.date: 11/04/2016
f1_keywords:
- memory/std::allocator<void>
- allocator<void>
helpviewer_keywords:
- allocator<void> class
ms.assetid: abfb40f5-c600-46a6-b130-f42c6535b2bd
ms.openlocfilehash: 7ac7fbaa8c50eb13457271cf96ddc3412733c833
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245871"
---
# <a name="allocatorltvoidgt-class"></a>Allocator&lt;void&gt; třídy

Specializace alokátoru třídy šablony na typ **void**, definice typů, které dávají smysl v tomto kontextu.

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

Třída šablony třídy se explicitně specializuje [alokátoru](../standard-library/allocator-class.md) pro typ **void**. Jejích konstruktorů a operátor přiřazení se chová stejně jako u šablony třídy, ale definuje pouze následující typy:

- [const_pointer](../standard-library/allocator-class.md#const_pointer).

- [ukazatel](../standard-library/allocator-class.md#pointer).

- [value_type](../standard-library/allocator-class.md#value_type).

- [rebind](../standard-library/allocator-class.md#rebind), vnořené šablony třídy.
