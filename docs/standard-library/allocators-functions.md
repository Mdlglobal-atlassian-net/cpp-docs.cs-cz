---
title: '&lt;&gt; makra přidělování'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::ALLOCATOR_DECL
- allocators/std::CACHE_CHUNKLIST
- allocators/std::CACHE_FREELIST
- allocators/std::CACHE_SUBALLOC
- allocators/std::SYNC_DEFAULT
ms.assetid: 9cb5ee07-1ff9-4594-ae32-3c8c6efb511a
helpviewer_keywords:
- std::ALLOCATOR_DECL [C++]
- std::CACHE_CHUNKLIST [C++]
- std::CACHE_FREELIST [C++]
- std::CACHE_SUBALLOC [C++]
- std::SYNC_DEFAULT [C++]
ms.openlocfilehash: 10cd1d51c2cd6053dcbaa0f5bf1548f80ed01659
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448230"
---
# <a name="ltallocatorsgt-macros"></a>&lt;&gt; makra přidělování

||||
|-|-|-|
|[ALLOCATOR_DECL](#allocator_decl)|[CACHE_CHUNKLIST](#cache_chunklist)|[CACHE_FREELIST](#cache_freelist)|
|[CACHE_SUBALLOC](#cache_suballoc)|[SYNC_DEFAULT](#sync_default)|

## <a name="allocator_decl"></a>ALLOCATOR_DECL

Poskytne třídu šablony pro přidělování.

```cpp
#define ALLOCATOR_DECL(cache, sync, name) <alloc_template>
```

### <a name="remarks"></a>Poznámky

Makro vytvoří definici `template <class Type> class name {.....}` šablony a specializaci `template <> class name<void> {.....}` , která společně definuje třídu šablony pro přidělování, která používá filtr `sync` synchronizace a mezipaměť typu `cache`.

Pro kompilátory, které mohou kompilovat opětovnou vazby, výsledná definice šablony vypadá takto:

```cpp
struct rebind
   {    /* convert a name<Type> to a name<Other> */
   typedef name<Other> other;
   };
```

Pro kompilátory, které nemohou kompilovat opětovnou vazby výsledné definice šablony, vypadá takto:

```cpp
template <class Type<class name
    : public stdext::allocators::allocator_base<Type,
    sync<stdext::allocators::rts_alloc<cache>>>
{
public:
    name() {}
    template <class Other>
    name(const name<Other>&) {}
    template <class Other>
    name& operator= (const name<Other>&)
    {
        return *this;
    }
};
```

## <a name="cache_chunklist"></a>CACHE_CHUNKLIST

Výnosy `stdext::allocators::cache_chunklist<sizeof(Type)>`.

```cpp
#define CACHE_CHUNKLIST <cache_class>
```

### <a name="remarks"></a>Poznámky

## <a name="cache_freelist"></a>CACHE_FREELIST

Výnosy `stdext::allocators::cache_freelist<sizeof(Type), max>`.

```cpp
#define CACHE_FREELIST(max) <cache_class>
```

### <a name="remarks"></a>Poznámky

## <a name="cache_suballoc"></a>  CACHE_SUBALLOC

Výnosy `stdext::allocators::cache_suballoc<sizeof(Type)>`.

```cpp
#define CACHE_SUBALLOC <cache_class>
```

### <a name="remarks"></a>Poznámky

## <a name="sync_default"></a>SYNC_DEFAULT

Vypočítá filtr synchronizace.

```cpp
#define SYNC_DEFAULT <sync_template>
```

### <a name="remarks"></a>Poznámky

Pokud kompilátor podporuje kompilování vícevláknové i vícevláknové aplikace, pro aplikace s jedním vláknem `stdext::allocators::sync_none` `stdext::allocators::sync_shared`vydává makro; ve všech ostatních případech to vede.

## <a name="see-also"></a>Viz také:

[\<allocators>](../standard-library/allocators-header.md)
