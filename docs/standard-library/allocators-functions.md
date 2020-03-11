---
title: '&lt;přidělování&gt; maker'
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
ms.openlocfilehash: 5355661e370daf8826541c036f7301e5c25788d7
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78875920"
---
# <a name="ltallocatorsgt-macros"></a>&lt;přidělování&gt; maker

||||
|-|-|-|
|[ALLOCATOR_DECL](#allocator_decl)|[CACHE_CHUNKLIST](#cache_chunklist)|[CACHE_FREELIST](#cache_freelist)|
|[CACHE_SUBALLOC](#cache_suballoc)|[SYNC_DEFAULT](#sync_default)|

## <a name="allocator_decl"></a>ALLOCATOR_DECL

Poskytne šablonu třídy přidělování.

```cpp
#define ALLOCATOR_DECL(cache, sync, name) <alloc_template>
```

### <a name="remarks"></a>Poznámky

Makro vytvoří definici šablony `template <class Type> class name {.....}` a specializace `template <> class name<void> {.....}`, která společně definuje šablonu třídy přidělování, která používá `sync` filtru synchronizace a mezipaměť typu `cache`.

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

Vypočítá `stdext::allocators::cache_chunklist<sizeof(Type)>`.

```cpp
#define CACHE_CHUNKLIST <cache_class>
```

### <a name="remarks"></a>Poznámky

## <a name="cache_freelist"></a>CACHE_FREELIST

Vypočítá `stdext::allocators::cache_freelist<sizeof(Type), max>`.

```cpp
#define CACHE_FREELIST(max) <cache_class>
```

### <a name="remarks"></a>Poznámky

## <a name="cache_suballoc"></a>CACHE_SUBALLOC

Vypočítá `stdext::allocators::cache_suballoc<sizeof(Type)>`.

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

Pokud kompilátor podporuje kompilování vícevláknové i vícevláknové aplikace, pro aplikace s jedním vláknem, které makro vrací `stdext::allocators::sync_none`; ve všech ostatních případech poskytuje `stdext::allocators::sync_shared`.

## <a name="see-also"></a>Viz také

[\<přidělování >](../standard-library/allocators-header.md)
