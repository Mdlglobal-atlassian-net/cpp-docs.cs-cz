---
title: '&lt;alokátorů&gt; makra | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: a24b854ac37dc0dfed44aec33fc1fb7e0bedcfc5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33842661"
---
# <a name="ltallocatorsgt-macros"></a>&lt;alokátorů&gt; makra

||||
|-|-|-|
|[ALLOCATOR_DECL –](#allocator_decl)|[CACHE_CHUNKLIST](#cache_chunklist)|[CACHE_FREELIST](#cache_freelist)|
|[CACHE_SUBALLOC –](#cache_suballoc)|[SYNC_DEFAULT –](#sync_default)|

## <a name="allocator_decl"></a>  ALLOCATOR_DECL –

Vypočítá přidělení třídy šablony.

```cpp
#define ALLOCATOR_DECL(cache, sync, name) <alloc_template>
```

### <a name="remarks"></a>Poznámky

Makro vypočítá definice šablony `template <class Type> class name {.....}` a specializace `template <> class name<void> {.....}` která společně definuje třídu allocator šablony, která využívá filtr synchronizace `sync` a mezipaměti typu `cache`.

Pro kompilátory, které můžete zkompilovat obnovení vazby výsledná definice šablony vypadat třeba takto:

```cpp
struct rebind
   {    /* convert a name<Type> to a name<Other> */
   typedef name<Other> other;
   };
```

Pro kompilátory, které nelze kompilovat obnovení vazby výsledné definice šablony vypadat třeba takto:

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

## <a name="cache_chunklist"></a>  CACHE_CHUNKLIST –

Vypočítá `stdext::allocators::cache_chunklist<sizeof(Type)>`.

```cpp
#define CACHE_CHUNKLIST <cache_class>
```

### <a name="remarks"></a>Poznámky

## <a name="cache_freelist"></a>  CACHE_FREELIST –

Vypočítá `stdext::allocators::cache_freelist<sizeof(Type), max>`.

```cpp
#define CACHE_FREELIST(max) <cache_class>
```

### <a name="remarks"></a>Poznámky

## <a name="cache_suballoc"></a>  CACHE_SUBALLOC –

Vypočítá `stdext::allocators::cache_suballoc<sizeof(Type)>`.

```cpp
#define CACHE_SUBALLOC <cache_class>
```

### <a name="remarks"></a>Poznámky

## <a name="sync_default"></a>  SYNC_DEFAULT –

Vypočítá filtr synchronizace.

```cpp
#define SYNC_DEFAULT <sync_template>
```

### <a name="remarks"></a>Poznámky

Pokud kompilátor podporuje kompilace jednovláknové i vícevláknové aplikace, pro aplikace makro vypočítá `stdext::allocators::sync_none`; ve všech ostatních případech bude vrácen `stdext::allocators::sync_shared`.

## <a name="see-also"></a>Viz také

[\<alokátorů >](../standard-library/allocators-header.md)<br/>
