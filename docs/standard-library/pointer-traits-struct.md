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
ms.openlocfilehash: 6d89348867982bfb86c0bf2404a017f6a448d1a1
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687143"
---
# <a name="pointer_traits-struct"></a>pointer_traits – struktura

Poskytuje informace, které jsou vyžadovány objektem typu `allocator_traits` k popisu modulu přidělování s typem ukazatele `Ptr`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ptr>
    struct pointer_traits;
```

## <a name="remarks"></a>Poznámky

PTR může být nezpracovaným ukazatelem typu `Ty *` nebo třídou s následujícími vlastnostmi.

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
|`typedef T2 difference_type`|Typ `T2` je `Ptr::difference_type`, pokud tento typ existuje, jinak `ptrdiff_t`. Pokud je `Ptr` nezpracovaný ukazatel, je typ `ptrdiff_t`.|
|`typedef T1 element_type`|Typ `T1` je `Ptr::element_type`, pokud tento typ existuje, jinak `Ty`. Pokud je `Ptr` nezpracovaný ukazatel, je typ `Ty`.|
|`typedef Ptr pointer`|Typ je `Ptr`.|

### <a name="structs"></a>Struktury

|||
|-|-|
|`rebind`|Pokusí se převést základní typ ukazatele na zadaný typ.|

### <a name="methods"></a>Metody

|Name|Popis|
|----------|-----------------|
|[pointer_to](#pointer_to)|Převede libovolný odkaz na objekt třídy `Ptr`.|

### <a name="pointer_to"></a>pointer_to

Statická metoda, která vrací `Ptr::pointer_to(obj)`, pokud tato funkce existuje. V opačném případě není možné převést libovolný odkaz na objekt třídy `Ptr`. Pokud `Ptr` je nezpracovaný ukazatel, tato metoda vrátí `addressof(obj)`.

```cpp
static pointer pointer_to(element_type& obj);
```
