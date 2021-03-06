---
title: default_delete – struktura
ms.date: 04/04/2019
f1_keywords:
- memory/std::default_delete
helpviewer_keywords:
- default_delete struct
ms.openlocfilehash: e9e1fcc68539e55486f4ea27e6dd5c49bed11fdf
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268132"
---
# <a name="defaultdelete-struct"></a>default_delete – struktura

Předdefinovaný objekt funkce, který provádí operace dělení (`operator/`) na svých argumentů.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
    struct default_delete
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<paměti >

**Namespace:** std

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[default_delete](#default_delete)|Konstruktor pro objekty typu `default_delete`.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operator()](#op_paren)|Reference – operátor pro přístup k `default_delete`.|

## <a name="default_delete"></a> default_delete

Konstruktor pro objekty typu `default_delete`.

```cpp
constexpr default_delete() noexcept = default;
template <class U>
    default_delete(const default_delete<U>&) noexcept;
```

## <a name="op_paren"></a> Operator()

Reference – operátor pro přístup k `default_delete`.

```cpp
void operator()(T*) const;
```

## <a name="see-also"></a>Viz také:

[\<memory>](../standard-library/memory.md)
