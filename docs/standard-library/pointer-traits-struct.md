---
title: pointer_traits – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 545aecf1-3561-4859-8b34-603c079fe1b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d1485441dbea92f534314dafd9d86ab0ef8a4e69
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856446"
---
# <a name="pointertraits-struct"></a>pointer_traits – struktura

Poskytuje informace, které je potřeba v objektu třídy šablony `allocator_traits` k popisu allocator s ukazatel typu `Ptr`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ptr>
struct pointer_traits;
```

## <a name="remarks"></a>Poznámky

PTR může být nezpracovaná ukazatel typu `Ty *` nebo třídy s následujícími vlastnostmi.

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
|`typedef T2 difference_type`|Typ `T2` je `Ptr::difference_type` pokud existuje tento typ, jinak `ptrdiff_t`. Pokud `Ptr` nezpracovaná ukazatel, typ je `ptrdiff_t`.|
|`typedef T1 element_type`|Typ `T1` je `Ptr::element_type` pokud existuje tento typ, jinak `Ty`. Pokud `Ptr` nezpracovaná ukazatel, typ je `Ty`.|
|`typedef Ptr pointer`|Typ je `Ptr`.|

### <a name="structs"></a>Struktury

|Název|Popis|
|----------|-----------------|
|`pointer_traits::rebind`|Pokusí se převést základní ukazatele na zadaný typ typ.|

### <a name="methods"></a>Metody

|Název|Popis|
|----------|-----------------|
|[pointer_to](#pointer_to)|Převede libovolný odkaz na objekt třídy `Ptr`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<paměti >

**Namespace:** – std

## <a name="pointer_to"></a>  pointer_to

Statickou metodu, která vrací `Ptr::pointer_to(obj)`v případě, že funkce existuje. Jinak, není možné převést libovolný odkaz na objekt třídy `Ptr`. Pokud `Ptr` je nezpracované ukazatel, vrátí tato metoda `addressof(obj)`.

```cpp
static pointer pointer_to(element_type& obj);
```

## <a name="see-also"></a>Viz také

[\<paměť >](../standard-library/memory.md)<br/>
[allocator_traits – třída](../standard-library/allocator-traits-class.md)<br/>
