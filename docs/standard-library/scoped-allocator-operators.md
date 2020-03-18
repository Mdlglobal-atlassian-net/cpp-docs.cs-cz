---
title: operátory &lt;scoped_allocator&gt;
ms.date: 11/04/2016
f1_keywords:
- scoped_allocator/std::operator!=
- scoped_allocator/std::operator==
ms.assetid: 4dfe0805-cc6e-479f-887f-a1c164f73837
ms.openlocfilehash: 071fc3b73cd3378b110d6d412bb7575e35a77478
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419558"
---
# <a name="ltscoped_allocatorgt-operators"></a>operátory &lt;scoped_allocator&gt;

|||
|-|-|
|[operator!=](#op_neq)|[operator = = – operátor](#op_eq_eq)|

## <a name="op_neq"></a>! = – operátor

Testuje dva objekty `scoped_allocator_adaptor` pro nerovnost.

```cpp
template <class Outer, class... Inner>
bool operator!=(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>Parametry

*levý*\
Levý objekt `scoped_allocator_adaptor`.

*pravé*\
Pravý objekt `scoped_allocator_adaptor`.

### <a name="return-value"></a>Návratová hodnota

`!(left == right)`

## <a name="op_eq_eq"></a>operator = = – operátor

Testuje dva objekty `scoped_allocator_adaptor` pro rovnost.

```cpp
template <class Outer, class... Inner>
bool operator==(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>Parametry

*levý*\
Levý objekt `scoped_allocator_adaptor`.

*pravé*\
Pravý objekt `scoped_allocator_adaptor`.

### <a name="return-value"></a>Návratová hodnota

`left.outer_allocator() == right.outer_allocator() && left.inner_allocator() == right.inner_allocator()`

## <a name="see-also"></a>Viz také

[<scoped_allocator>](../standard-library/scoped-allocator.md)
