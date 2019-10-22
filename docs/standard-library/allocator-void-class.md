---
title: Třída přidělování &lt;void &gt;
ms.date: 11/04/2016
f1_keywords:
- memory/std::allocator<void>
- allocator<void>
helpviewer_keywords:
- allocator<void> class
ms.assetid: abfb40f5-c600-46a6-b130-f42c6535b2bd
ms.openlocfilehash: c8d787fe03dfe6f67fb8e228308ec74b6e7f620a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688520"
---
# <a name="allocatorltvoidgt-class"></a>Třída přidělování &lt;void &gt;

Specializace přidělování šablon třídy k typu **void**, definující typy, které mají smysl v tomto kontextu.

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

Třída explicitně specializuje [přidělování](../standard-library/allocator-class.md) šablon tříd pro typ **void**. Jeho konstruktory a operátor přiřazení se chovají stejně jako pro šablonu třídy, ale definují pouze následující typy:

- [const_pointer](../standard-library/allocator-class.md#const_pointer).

- [ukazatel](../standard-library/allocator-class.md#pointer).

- [value_type](../standard-library/allocator-class.md#value_type).

- [vytvoření vazby](../standard-library/allocator-class.md#rebind)šablony vnořené třídy.
