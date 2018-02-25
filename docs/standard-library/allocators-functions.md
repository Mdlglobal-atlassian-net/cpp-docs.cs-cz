---
title: "&lt;alokátorů&gt; makra | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- allocators/std::ALLOCATOR_DECL
- allocators/std::CACHE_CHUNKLIST
- allocators/std::CACHE_FREELIST
- allocators/std::CACHE_SUBALLOC
- allocators/std::SYNC_DEFAULT
ms.assetid: 9cb5ee07-1ff9-4594-ae32-3c8c6efb511a
caps.latest.revision: 
manager: ghogen
helpviewer_keywords:
- std::ALLOCATOR_DECL [C++]
- std::CACHE_CHUNKLIST [C++]
- std::CACHE_FREELIST [C++]
- std::CACHE_SUBALLOC [C++]
- std::SYNC_DEFAULT [C++]
ms.openlocfilehash: 7bd292ee2c19c2db90f126d6082854141c3e71fc
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ltallocatorsgt-macros"></a>&lt;alokátorů&gt; makra
||||  
|-|-|-|  
|[ALLOCATOR_DECL](#allocator_decl)|[CACHE_CHUNKLIST](#cache_chunklist)|[CACHE_FREELIST](#cache_freelist)|  
|[CACHE_SUBALLOC](#cache_suballoc)|[SYNC_DEFAULT](#sync_default)|  
  
##  <a name="allocator_decl"></a>  ALLOCATOR_DECL –  
 Vypočítá přidělení třídy šablony.  
  
```
#define ALLOCATOR_DECL(cache, sync, name) <alloc_template>
```  
  
### <a name="remarks"></a>Poznámky  
 Makro vypočítá definice šablony `template <class Type> class name {.....}` a specializace `template <> class name<void> {.....}` která společně definuje třídu allocator šablony, která využívá filtr synchronizace `sync` a mezipaměti typu `cache`.  
  
 Pro kompilátory, které můžete zkompilovat obnovení vazby výsledná definice šablony vypadat třeba takto:  
```  
struct rebind
   {    /* convert a name<Type> to a name<Other> */
   typedef name<Other> other;
   };  
 ```  
 Pro kompilátory, které nelze kompilovat obnovení vazby výsledné definice šablony vypadat třeba takto:  
  
```
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
  
##  <a name="cache_chunklist"></a>  CACHE_CHUNKLIST  
 Vypočítá `stdext::allocators::cache_chunklist<sizeof(Type)>`.  
  
```
#define CACHE_CHUNKLIST <cache_class>
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="cache_freelist"></a>  CACHE_FREELIST –  
 Vypočítá `stdext::allocators::cache_freelist<sizeof(Type), max>`.  
  
```
#define CACHE_FREELIST(max) <cache_class>
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="cache_suballoc"></a>  CACHE_SUBALLOC –  
 Vypočítá `stdext::allocators::cache_suballoc<sizeof(Type)>`.  
  
```
#define CACHE_SUBALLOC <cache_class>
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="sync_default"></a>  SYNC_DEFAULT  
 Vypočítá filtr synchronizace.  
  
```
#define SYNC_DEFAULT <sync_template>
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud kompilátor podporuje kompilace jednovláknové i vícevláknové aplikace, pro aplikace makro vypočítá `stdext::allocators::sync_none`; ve všech ostatních případech bude vrácen `stdext::allocators::sync_shared`.  
  
## <a name="see-also"></a>Viz také  
 [\<allocators>](../standard-library/allocators-header.md)




