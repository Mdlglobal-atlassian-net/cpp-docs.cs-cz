---
title: pointer_traits – struktura
ms.date: 11/04/2016
f1_keywords:
- memory/std::pointer_traits::element_type
- memory/std::pointer_traits::pointer
- memory/std::pointer_traits
- memory/std::pointer_traits::difference_type
- memory/std::pointer_traits::rebind
- xmemory0/std::pointer_traits::element_type
- xmemory0/std::pointer_traits::pointer
- xmemory0/std::pointer_traits
- xmemory0/std::pointer_traits::difference_type
- xmemory0/std::pointer_traits::rebind
- memory/std::pointer_traits::pointer_to
ms.assetid: 545aecf1-3561-4859-8b34-603c079fe1b3
ms.openlocfilehash: 109e51ad9eba54f31b90da9b8b85bec105c7dce6
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240430"
---
# <a name="pointertraits-struct"></a>pointer_traits – struktura

Poskytuje informace, které je potřeba pro objekt třídy šablony `allocator_traits` k popisu přidělování s ukazatelem typu `Ptr`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ptr>
    struct pointer_traits;
```

## <a name="remarks"></a>Poznámky

PTR může být nezpracovaný ukazatel typu `Ty *` nebo třídu s následujícími vlastnostmi.

```cpp
struct Ptr
{ // describes a pointer type usable by allocators
   typedef Ptr pointer;
   typedef T1 element_type; // optional
   typedef T2 difference_type; // optional
   template <class Other>
   using rebind = typename Ptr<Other, Rest...>; // optional
   static pointer pointer_to(element_type& obj); // optional
};
```

## <a name="members"></a>Členové

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|`typedef T2 difference_type`|Typ `T2` je `Ptr::difference_type` Pokud daný typ existuje, jinak `ptrdiff_t`. Pokud `Ptr` je nezpracovaný ukazatel, je typ `ptrdiff_t`.|
|`typedef T1 element_type`|Typ `T1` je `Ptr::element_type` Pokud daný typ existuje, jinak `Ty`. Pokud `Ptr` je nezpracovaný ukazatel, je typ `Ty`.|
|`typedef Ptr pointer`|Typ je `Ptr`.|

### <a name="structs"></a>Struktury

|||
|-|-|
|`rebind`|Typ, který zadaného typu pokusí převést základního ukazatele.|

### <a name="methods"></a>Metody

|Name|Popis|
|----------|-----------------|
|[pointer_to](#pointer_to)|Převede libovolného odkazu na objekt třídy `Ptr`.|

### <a name="pointer_to"></a> pointer_to

Statická metoda, která vrátí `Ptr::pointer_to(obj)`, pokud existuje, že fungují. V opačném případě není možné převést libovolný odkaz na objekt třídy `Ptr`. Pokud `Ptr` je nezpracovaný ukazatel, vrátí tato metoda `addressof(obj)`.

```cpp
static pointer pointer_to(element_type& obj);
```
