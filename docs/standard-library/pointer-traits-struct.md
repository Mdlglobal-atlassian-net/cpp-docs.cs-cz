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
ms.openlocfilehash: b661d4b36ce48a08faba6638c5114f3f4e6981a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434785"
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
   static pointer pointer_to(element_type& obj);
   // optional
   };
```

### <a name="typedefs"></a>Typedefs

|Název|Popis|
|----------|-----------------|
|`typedef T2 difference_type`|Typ `T2` je `Ptr::difference_type` Pokud daný typ existuje, jinak `ptrdiff_t`. Pokud `Ptr` je nezpracovaný ukazatel, je typ `ptrdiff_t`.|
|`typedef T1 element_type`|Typ `T1` je `Ptr::element_type` Pokud daný typ existuje, jinak `Ty`. Pokud `Ptr` je nezpracovaný ukazatel, je typ `Ty`.|
|`typedef Ptr pointer`|Typ je `Ptr`.|

### <a name="structs"></a>Struktury

|Název|Popis|
|----------|-----------------|
|`pointer_traits::rebind`|Typ, který zadaného typu pokusí převést základního ukazatele.|

### <a name="methods"></a>Metody

|Název|Popis|
|----------|-----------------|
|[pointer_to](#pointer_to)|Převede libovolného odkazu na objekt třídy `Ptr`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<paměti >

**Namespace:** std

## <a name="pointer_to"></a>  pointer_to

Statická metoda, která vrátí `Ptr::pointer_to(obj)`, pokud existuje, že fungují. V opačném případě není možné převést libovolný odkaz na objekt třídy `Ptr`. Pokud `Ptr` je nezpracovaný ukazatel, vrátí tato metoda `addressof(obj)`.

```cpp
static pointer pointer_to(element_type& obj);
```

## <a name="see-also"></a>Viz také:

[\<paměť >](../standard-library/memory.md)<br/>
[allocator_traits – třída](../standard-library/allocator-traits-class.md)<br/>
