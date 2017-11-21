---
title: "&lt;alokátorů&gt; | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <allocators>
dev_langs: C++
helpviewer_keywords: allocators header
ms.assetid: 4393a607-4df8-4278-bbb2-c8ec52e60b83
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c4c6ad648aff3503272760675a8db99cd1889d9b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltallocatorsgt"></a>&lt;alokátorů&gt;
Definuje několik šablon, které pomáhají přidělit a volné bloky paměti pro kontejnery založené na uzlu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <allocators>  
```  
  
## <a name="remarks"></a>Poznámky  
 \<Alokátorů > záhlaví poskytuje šesti allocator šablony, které lze použít k výběru strategie správy paměti pro kontejnery založené na uzlu. Pro použití s tyto šablony je také několik různých synchronizace filtrů podle strategie správy paměti, která celou řadu různých multithreading schémata (včetně none). Odpovídající strategie správy paměti pro vzory využití paměti známé a požadavků na synchronizaci, konkrétní aplikace můžete často rychlosti zvýšit nebo snížit požadavky na celkové paměti aplikace.  
  
 Allocator šablony jsou implementovány s opakovaně použitelné součásti, které lze přizpůsobit nebo nahradit zajistit další správa paměti strategie.  
  
 Na základě uzlu kontejnery v standardní knihovna C++ (std::list, std::set, std::multiset, std::map a std::multimap) uložit jejich elementů v jednotlivých uzlech. Všechny uzly pro typ konkrétním kontejneru jsou stejnou velikost, takže není nutné flexibilitu správce pro obecné účely paměti. Protože je v době kompilace velikost každého bloku paměti, správce paměti může být mnohem jednodušší a rychlejší.  
  
 Při použití s kontejnery, které nejsou založené na uzlu (například standardní knihovna C++ kontejnery std::vector std::deque a std::basic_string), šablony alllocator nebude pracovat správně, ale nejsou může zajistit zlepšení výkonu prostřednictvím Výchozí přidělení.  
  
 Přidělení je třída šablony, která popisuje objekt, který spravuje přidělení úložiště a uvolnění pro objekty a pole objektů určené typu. Přidělování objektů jsou používány několik tříd šablon kontejner ve standardní knihovně C++.  
  
 Alokátorů jsou všechny šablony tohoto typu:  
  
 `template<class` `Type` `>`  
  
 `class allocator;`  
  
 kde argument šablony `Type` je typ spravuje allocator instance. Standardní knihovna C++ poskytuje výchozí přidělení, šablony třídy [allocator](../standard-library/allocator-class.md), která je definována v [ \<paměti >](../standard-library/memory.md). \<Alokátorů > záhlaví poskytuje následující alokátorů:  
  
- [allocator_newdel](../standard-library/allocator-newdel-class.md)  
  
- [allocator_unbounded](../standard-library/allocator-unbounded-class.md)  
  
- [allocator_fixed_size](../standard-library/allocator-fixed-size-class.md)  
  
- [allocator_variable_size](../standard-library/allocator-variable-size-class.md)  
  
- [allocator_suballoc](../standard-library/allocator-suballoc-class.md)  
  
- [allocator_chunklist](../standard-library/allocator-chunklist-class.md)  
  
 Při vytváření kontejneru, například následující příklad kódu, použijte příslušné konkretizaci přidělení jako druhý argument typu.  
  
 `#include <list>`  
  
 `#include <allocators>`  
  
 `std::list<int, stdext::allocators::allocator_chunklist<int> > _List0;`  
  
 _List0 přiděluje uzly s `allocator_chunklist` a výchozí filtr synchronizace.  
  
 Použijte makro [allocator_decl –](../standard-library/allocators-functions.md#allocator_decl) vytvoření šablon allocator s filtry synchronizace jiné než výchozí:  
  
 `#include <list>`  
  
 `#include <allocators>`  
  
 `ALLOCATOR_DECL(CACHE_CHUNKLIST, stdext::allocators::sync_per_thread, Alloc);`  
  
 `std::list<int, alloc<int> > _List1;`  
  
 _Lst1 přiděluje uzly s `allocator_chunklist` a [sync_per_thread](../standard-library/sync-per-thread-class.md) filtr synchronizace.  
  
 Allocator bloku je mezipaměť nebo filtr. Mezipaměť je šablona třídu, která přijímá jeden argument std::size_t typu. Definuje allocator bloku, která přiděluje a zruší přidělení bloků paměti jedné velikosti. Je nutné získat paměti pomocí operátoru `new`, ale nemusí díky samostatné volání operátor `new` pro každý blok. Ho může například suballocate z větší bloku nebo mezipaměti navrácena bloky pro následné opakované přidělení.  
  
 Hodnota _Sz argument předaný mezipaměti členské funkce s kompilátorem, který nelze kompilovat obnovení vazby, které se hodnota argumentu std::size_t používá, když šablona byla vytvořena instance není nutně přidělit a navrácení.  
  
 \<alokátorů > poskytuje následující šablony mezipaměti:  
  
- [cache_freelist –](../standard-library/cache-freelist-class.md)  
  
- [cache_suballoc –](../standard-library/cache-suballoc-class.md)  
  
- [cache_chunklist –](../standard-library/cache-chunklist-class.md)  
  
 Filtr je allocator blok, který implementuje jeho členské funkce pomocí jiné allocator blok, který je předán jako argument šablony. Nejběžnější formu filtr je filtr synchronizace, která se vztahuje k řízení přístupu k členské funkce instance jiný blok allocator zásady synchronizace. \<alokátorů > poskytuje následující filtry synchronizace:  
  
- [sync_none](../standard-library/sync-none-class.md)  
  
- [sync_per_container](../standard-library/sync-per-container-class.md)  
  
- [sync_per_thread](../standard-library/sync-per-thread-class.md)  
  
- [sync_shared](../standard-library/sync-shared-class.md)  
  
 \<alokátorů > také poskytuje filtr [rts_alloc](../standard-library/rts-alloc-class.md), který obsahuje více allocator bloku instancí a určuje, kterou instanci chcete použít pro přidělení nebo navrácení za běhu místo v době kompilace. Používá se s kompilátory, které nelze kompilovat obnovení vazby.  
  
 Zásady synchronizace určuje, jak allocator instance zpracovává souběžných požadavků na přidělení a navrácení z více vláken. Nejjednodušší zásad je předat všechny požadavky přímo prostřednictvím základní objekt mezipaměti a správy synchronizace pro uživatele. Složitější zásad může být mutex určený k serializaci přístup k základní objekt mezipaměti.  
  
 Pokud kompilátor podporuje kompilace jednovláknové i vícevláknové aplikace, je výchozí filtr synchronizace pro jednovláknové aplikace `sync_none`; všech ostatních případech je `sync_shared`.  
  
 Šablona mezipaměti `cache_freelist` použije argument maximální – třída, která určuje maximální počet elementů k uložení do seznamu volné.  
  
 \<alokátorů > poskytuje následující maximální třídy:  
  
- [max_none](../standard-library/max-none-class.md)  
  
- [max_unbounded](../standard-library/max-unbounded-class.md)  
  
- [max_fixed_size –](../standard-library/max-fixed-size-class.md)  
  
- [max_variable_size –](../standard-library/max-variable-size-class.md)  
  
### <a name="macros"></a>Makra  
  
|||  
|-|-|  
|[ALLOCATOR_DECL –](../standard-library/allocators-functions.md#allocator_decl)|Vypočítá přidělení třídy šablony.|  
|[CACHE_CHUNKLIST –](../standard-library/allocators-functions.md#cache_chunklist)|Vypočítá `stdext::allocators::cache_chunklist<sizeof(Type)>`.|  
|[CACHE_FREELIST –](../standard-library/allocators-functions.md#cache_freelist)|Vypočítá `stdext::allocators::cache_freelist<sizeof(Type), max>`.|  
|[CACHE_SUBALLOC –](../standard-library/allocators-functions.md#cache_suballoc)|Vypočítá `stdext::allocators::cache_suballoc<sizeof(Type)>`.|  
|[SYNC_DEFAULT –](../standard-library/allocators-functions.md#sync_default)|Vypočítá filtr synchronizace.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[Operator! = (\<alokátorů >)](../standard-library/allocators-operators.md#op_neq)|Testy pro nerovnost mezi objekty přidělování z dané třídy.|  
|[Operator == (\<alokátorů >)](../standard-library/allocators-operators.md#op_eq_eq)|Testy pro rovnost mezi objekty přidělování z dané třídy.|  
  
### <a name="classes"></a>Třídy  
  
|||  
|-|-|  
|[allocator_base –](../standard-library/allocator-base-class.md)|Definuje základní třídu a běžné funkce, které jsou nutné k vytvoření přidělení uživatelem definované z filtr synchronizace.|  
|[allocator_chunklist](../standard-library/allocator-chunklist-class.md)|Popisuje objekt, který spravuje přidělení úložiště a uvolnění objektů pomocí mezipaměti typu [cache_chunklist –](../standard-library/cache-chunklist-class.md).|  
|[allocator_fixed_size](../standard-library/allocator-fixed-size-class.md)|Popisuje objekt, který spravuje přidělení úložiště a uvolnění objektů typu `Type` použití mezipaměti typu [cache_freelist –](../standard-library/cache-freelist-class.md) s délkou spravuje [max_fixed_size](../standard-library/max-fixed-size-class.md).|  
|[allocator_newdel](../standard-library/allocator-newdel-class.md)|Implementuje přidělení, který používá `operator delete` se zrušit přidělení paměti bloku a `operator new` přidělit blok paměti.|  
|[allocator_suballoc](../standard-library/allocator-suballoc-class.md)|Popisuje objekt, který spravuje přidělení úložiště a uvolnění objektů typu `Type` použití mezipaměti typu [cache_suballoc –](../standard-library/cache-suballoc-class.md).|  
|[allocator_unbounded](../standard-library/allocator-unbounded-class.md)|Popisuje objekt, který spravuje přidělení úložiště a uvolnění objektů typu `Type` použití mezipaměti typu [cache_freelist –](../standard-library/cache-freelist-class.md) s délkou spravuje [max_unbounded](../standard-library/max-unbounded-class.md).|  
|[allocator_variable_size](../standard-library/allocator-variable-size-class.md)|Popisuje objekt, který spravuje přidělení úložiště a uvolnění objektů typu `Type` použití mezipaměti typu [cache_freelist –](../standard-library/cache-freelist-class.md) s délkou spravuje [max_variable_size](../standard-library/max-variable-size-class.md).|  
|[cache_chunklist –](../standard-library/cache-chunklist-class.md)|Definuje allocator bloku, která přiděluje a zruší přidělení bloků paměti jedné velikosti.|  
|[cache_freelist –](../standard-library/cache-freelist-class.md)|Definuje allocator bloku, která přiděluje a zruší přidělení bloků paměti jedné velikosti.|  
|[cache_suballoc –](../standard-library/cache-suballoc-class.md)|Definuje allocator bloku, která přiděluje a zruší přidělení bloků paměti jedné velikosti.|  
|[FreeList](../standard-library/freelist-class.md)|Spravuje seznam bloky paměti.|  
|[max_fixed_size –](../standard-library/max-fixed-size-class.md)|Popisuje objekt maximální třídy, která omezuje [freelist](../standard-library/freelist-class.md) objekt, který má pevnou maximální délku.|  
|[max_none](../standard-library/max-none-class.md)|Popisuje objekt maximální třídy, která omezuje [freelist](../standard-library/freelist-class.md) objekt, který má maximální délku nula.|  
|[max_unbounded](../standard-library/max-unbounded-class.md)|Popisuje maximální třídu objektu, který neomezuje maximální délku [freelist](../standard-library/freelist-class.md) objektu.|  
|[max_variable_size –](../standard-library/max-variable-size-class.md)|Popisuje objekt maximální třídy, která omezuje [freelist](../standard-library/freelist-class.md) objekt, který má maximální délku, která je přibližně přímo úměrná počtu přidělené bloky paměti.|  
|[rts_alloc](../standard-library/rts-alloc-class.md)|Rts_alloc – třída šablony popisuje [filtru](../standard-library/allocators-header.md) , obsahuje pole mezipaměti instancí a určuje, kterou instanci chcete použít pro přidělení a navrácení za běhu místo v době kompilace.|  
|[sync_none](../standard-library/sync-none-class.md)|Popisuje synchronizaci filtr, který poskytuje žádná synchronizace.|  
|[sync_per_container](../standard-library/sync-per-container-class.md)|Popisuje synchronizaci filtr, který obsahuje objekt samostatné mezipaměti pro každý objekt přidělení.|  
|[sync_per_thread](../standard-library/sync-per-thread-class.md)|Popisuje synchronizaci filtr, který poskytuje objekt samostatné mezipaměti pro každé vlákno.|  
|[sync_shared](../standard-library/sync-shared-class.md)|Popisuje synchronizaci filtr, který se používá k řízení přístupu k objektu mezipaměti, který je sdílen všechny alokátorů mutex.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<alokátorů >  
  
 **Namespace:** stdext –  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)



