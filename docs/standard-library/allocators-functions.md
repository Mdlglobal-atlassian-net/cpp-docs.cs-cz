---
title: '&lt;alokátory&gt; makra'
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
ms.openlocfilehash: a8b988511d0cdd46ae7f41bce29eb26f593a57c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364974"
---
# <a name="ltallocatorsgt-macros"></a>&lt;alokátory&gt; makra

||||
|-|-|-|
|[ALLOCATOR_DECL](#allocator_decl)|[CACHE_CHUNKLIST](#cache_chunklist)|[CACHE_FREELIST](#cache_freelist)|
|[CACHE_SUBALLOC](#cache_suballoc)|[SYNC_DEFAULT](#sync_default)|

## <a name="allocator_decl"></a><a name="allocator_decl"></a>ALLOCATOR_DECL

Dává šablonu třídy přidělování.

```cpp
#define ALLOCATOR_DECL(cache, sync, name) <alloc_template>
```

### <a name="remarks"></a>Poznámky

Makro poskytuje `template <class Type> class name {.....}` definici šablony a `template <> class name<void> {.....}` specializaci, která společně definuje šablonu třídy `sync` přidělování, která `cache`používá filtr synchronizace a mezipaměť typu .

Pro kompilátory, které mohou kompilovat rebind, výsledná definice šablony vypadá takto:

```cpp
struct rebind
   {    /* convert a name<Type> to a name<Other> */
   typedef name<Other> other;
   };
```

Pro kompilátory, které nemohou zkompilovat rebind výsledná definice šablony vypadá takto:

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

## <a name="cache_chunklist"></a><a name="cache_chunklist"></a>CACHE_CHUNKLIST

Výnosy `stdext::allocators::cache_chunklist<sizeof(Type)>`.

```cpp
#define CACHE_CHUNKLIST <cache_class>
```

### <a name="remarks"></a>Poznámky

## <a name="cache_freelist"></a><a name="cache_freelist"></a>CACHE_FREELIST

Výnosy `stdext::allocators::cache_freelist<sizeof(Type), max>`.

```cpp
#define CACHE_FREELIST(max) <cache_class>
```

### <a name="remarks"></a>Poznámky

## <a name="cache_suballoc"></a><a name="cache_suballoc"></a>CACHE_SUBALLOC

Výnosy `stdext::allocators::cache_suballoc<sizeof(Type)>`.

```cpp
#define CACHE_SUBALLOC <cache_class>
```

### <a name="remarks"></a>Poznámky

## <a name="sync_default"></a><a name="sync_default"></a>SYNC_DEFAULT

Poskytuje filtr synchronizace.

```cpp
#define SYNC_DEFAULT <sync_template>
```

### <a name="remarks"></a>Poznámky

Pokud kompilátor podporuje kompilaci aplikací s jedním vláknem i více vlákny, pro `stdext::allocators::sync_none`jednovláknové aplikace výtěžek maker ; ve všech ostatních `stdext::allocators::sync_shared`případech dává .

## <a name="see-also"></a>Viz také

[\<alokátory>](../standard-library/allocators-header.md)
