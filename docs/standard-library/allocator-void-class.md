---
title: Allocator&lt;void&gt; třídy
ms.date: 11/04/2016
f1_keywords:
- memory/std::allocator<void>
- allocator<void>
helpviewer_keywords:
- allocator<void> class
ms.assetid: abfb40f5-c600-46a6-b130-f42c6535b2bd
ms.openlocfilehash: 5591570527946895d1e0456b23327d7fabc4bef5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646099"
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

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<paměti >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
