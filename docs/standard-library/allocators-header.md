---
title: '&lt;alokátory&gt; | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <allocators>
dev_langs:
- C++
helpviewer_keywords:
- allocators header
ms.assetid: 4393a607-4df8-4278-bbb2-c8ec52e60b83
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dcda07b5d2ab499a769c389538e8f272fd8441a6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713164"
---
# <a name="ltallocatorsgt"></a>&lt;alokátory:&gt;

Definuje několik šablon, které pomáhají přidělit a uvolnit bloky paměti pro kontejnery založené na uzlu.

## <a name="syntax"></a>Syntaxe

```cpp
#include <allocators>
```

## <a name="remarks"></a>Poznámky

\<Alokátorů > záhlaví obsahuje šest allocator šablony, které slouží k výběru strategie správy paměti pro kontejnery založené na uzlu. Pro použití s těmito šablonami poskytuje také několik různých synchronizace filtrů pro přizpůsobení strategie správy paměti, která širokou škálu různých multithreading schémata (včetně žádný). Často odpovídající strategie správy paměti vzorů využití paměti známé a požadavky na synchronizaci, konkrétní aplikace může zvýšit rychlost nebo snižte celkové požadavky na paměť aplikace.

Allocator šablony jsou implementovány pomocí opakovaně použitelné komponenty, které můžete přizpůsobit nebo nahradit, aby poskytují další správa paměti strategie.

Kontejnery založené na uzlu ve standardní knihovně C++ (std::list, std::set, std::multiset, std::map a std::multimap) ukládají jejich prvky v jednotlivých uzlech. Všechny uzly konkrétní typy kontejnerů mají stejnou velikost, takže není potřeba flexibilitu správce paměti pro obecné účely. Protože každý blok paměti velikosti je znám v době kompilace, správce paměti může být mnohem jednodušší a rychlejší.

Při použití s kontejnery, které nejsou založené na uzlu (například std::deque std::vector kontejnery standardní knihovny C++ a std::basic_string), šablony alllocator bude správně fungovat, ale nejsou pravděpodobně kvůli zlepšení výkonu za výchozího přidělujícího modulu.

Přidělování je třída šablony popisující objekt, který spravuje rozdělení úložiště a uvolnění pro objekty a pole objektů určeného typu. Přidělování objektů používá několik tříd šablon kontejneru ve standardní knihovně jazyka C++.

Alokátorů jsou všechny šablony tohoto typu:

```cpp
template<class Type>
class allocator;
```

Pokud argument šablony `Type` je typ spravovaných instancí alokátoru. Standardní knihovny C++ poskytuje výchozího přidělujícího modulu, třídy šablony [alokátoru](../standard-library/allocator-class.md), který je definován v [ \<paměti >](../standard-library/memory.md). \<Alokátorů > záhlaví obsahuje následující alokátory:

- [allocator_newdel](../standard-library/allocator-newdel-class.md)

- [allocator_unbounded –](../standard-library/allocator-unbounded-class.md)

- [allocator_fixed_size](../standard-library/allocator-fixed-size-class.md)

- [allocator_variable_size –](../standard-library/allocator-variable-size-class.md)

- [allocator_suballoc](../standard-library/allocator-suballoc-class.md)

- [allocator_chunklist](../standard-library/allocator-chunklist-class.md)

Používejte příslušné instance alokátoru jako druhý argument typu při vytváření kontejneru, jako v následujícím příkladu kódu.

`#include <list>`

`#include <allocators>`

`std::list<int, stdext::allocators::allocator_chunklist<int> > _List0;`

_List0 přiděluje uzly s `allocator_chunklist` a výchozí filtr synchronizace.

Použijte makro [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) k vytvoření šablony allocator s filtry synchronizace jiné než výchozí:

`#include <list>`

`#include <allocators>`

`ALLOCATOR_DECL(CACHE_CHUNKLIST, stdext::allocators::sync_per_thread, Alloc);`

`std::list<int, alloc<int> > _List1;`

_Lst1 přiděluje uzly s `allocator_chunklist` a [sync_per_thread –](../standard-library/sync-per-thread-class.md) filtr synchronizace.

Allocator bloku je mezipaměť nebo filtru. Mezipaměť je třída šablony, která přijímá jeden argument typu std::size_t. Definuje bloku alokátoru, který přiděluje a zruší přidělení bloků paměti z jednoho velikost. Je nutné získat paměť pomocí operátoru **nové**, ale nemusí díky samostatné volání operátoru **nové** pro každý blok. To může například suballocate z větší bloku nebo přidělení bloků pro následné realokace mezipaměti.

Hodnota _Sz argument předaný do mezipaměti členské funkce s kompilátorem, který nejde zkompilovat obnovení vazby hodnoty argumentu std::size_t při šablona byla vytvořena instance, není nutně přidělit a uvolnit.

\<alokátory > poskytuje následující šablony mezipaměti:

- [cache_freelist](../standard-library/cache-freelist-class.md)

- [cache_suballoc](../standard-library/cache-suballoc-class.md)

- [cache_chunklist](../standard-library/cache-chunklist-class.md)

Filtr je blok alokátoru, který implementuje její členské funkce pomocí jiného bloku alokátoru, který se předá jako argument šablony. Nejběžnější forma filtru je filtr synchronizace, který použije synchronizace zásady řízení přístupu na členské funkce instance jiného bloku alokátoru. \<alokátory > poskytuje následující filtry synchronizace:

- [sync_none](../standard-library/sync-none-class.md)

- [sync_per_container](../standard-library/sync-per-container-class.md)

- [sync_per_thread](../standard-library/sync-per-thread-class.md)

- [sync_shared](../standard-library/sync-shared-class.md)

\<alokátory > také obsahuje filtr [rts_alloc –](../standard-library/rts-alloc-class.md), který obsahuje více bloku přidělování instancí a určuje, kterou instanci chcete použít pro přidělení nebo zrušení přidělení v době běhu místo v době kompilace. Používá se s kompilátory, které nelze zkompilovat obnovení vazby.

Synchronizace zásad určuje, jak allocator instance zpracovává souběžné požadavky na přidělování a navracení zpět z více vláken. Nejjednodušší zásad je předat všechny požadavky přímo prostřednictvím základní objekt mezipaměti byste museli opustit správu synchronizace pro uživatele. Určený objekt mutex k serializaci přístup k základní objekt mezipaměti může být složitější zásady.

Pokud kompilátor podporuje kompilace s jedním vláknem i vícevláknové aplikace, je výchozí filtr synchronizace pro aplikace s jedním vláknem `sync_none`; u všech ostatních případech je `sync_shared`.

Šablonu mezipaměti `cache_freelist` přijímá argument maximální třídy, která určuje maximální počet prvků, které mají být uloženy v seznamu zdarma.

\<alokátory > obsahuje následující třídy, max:

- [max_none](../standard-library/max-none-class.md)

- [max_unbounded](../standard-library/max-unbounded-class.md)

- [max_fixed_size](../standard-library/max-fixed-size-class.md)

- [max_variable_size](../standard-library/max-variable-size-class.md)

### <a name="macros"></a>Makra

|– Makro|Popis|
|-|-|
|[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)|Vrací alokátoru třídy šablony.|
|[CACHE_CHUNKLIST](../standard-library/allocators-functions.md#cache_chunklist)|Vrací `stdext::allocators::cache_chunklist<sizeof(Type)>`.|
|[CACHE_FREELIST](../standard-library/allocators-functions.md#cache_freelist)|Vrací `stdext::allocators::cache_freelist<sizeof(Type), max>`.|
|[CACHE_SUBALLOC –](../standard-library/allocators-functions.md#cache_suballoc)|Vrací `stdext::allocators::cache_suballoc<sizeof(Type)>`.|
|[SYNC_DEFAULT](../standard-library/allocators-functions.md#sync_default)|Vrací filtr synchronizace.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[Operator! = (\<alokátorů >)](../standard-library/allocators-operators.md#op_neq)|Testy pro nerovnost mezi objekty přidělování z dané třídy.|
|[Operator == (\<alokátorů >)](../standard-library/allocators-operators.md#op_eq_eq)|Testy pro rovnost mezi objekty přidělování z dané třídy.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[allocator_base –](../standard-library/allocator-base-class.md)|Definuje základní třídu a běžné funkce potřebné k vytváření alokátorem definovaný uživatelem z filtru synchronizace.|
|[allocator_chunklist](../standard-library/allocator-chunklist-class.md)|Popisuje objekt, který spravuje rozdělení úložiště a uvolnění objektů použití mezipaměti typu [cache_chunklist –](../standard-library/cache-chunklist-class.md).|
|[allocator_fixed_size](../standard-library/allocator-fixed-size-class.md)|Popisuje objekt, který spravuje rozdělení úložiště a uvolnění pro objekt typu `Type` použití mezipaměti typu [cache_freelist –](../standard-library/cache-freelist-class.md) s délkou spravuje [max_fixed_size –](../standard-library/max-fixed-size-class.md).|
|[allocator_newdel](../standard-library/allocator-newdel-class.md)|Implementuje alokátoru, který používá **operátor delete** k uvolnění paměti bloku a **operátor new** přidělení bloku paměti.|
|[allocator_suballoc](../standard-library/allocator-suballoc-class.md)|Popisuje objekt, který spravuje rozdělení úložiště a uvolnění pro objekt typu `Type` použití mezipaměti typu [cache_suballoc –](../standard-library/cache-suballoc-class.md).|
|[allocator_unbounded –](../standard-library/allocator-unbounded-class.md)|Popisuje objekt, který spravuje rozdělení úložiště a uvolnění pro objekt typu `Type` použití mezipaměti typu [cache_freelist –](../standard-library/cache-freelist-class.md) s délkou spravuje [max_unbounded –](../standard-library/max-unbounded-class.md).|
|[allocator_variable_size –](../standard-library/allocator-variable-size-class.md)|Popisuje objekt, který spravuje rozdělení úložiště a uvolnění pro objekt typu `Type` použití mezipaměti typu [cache_freelist –](../standard-library/cache-freelist-class.md) s délkou spravuje [max_variable_size –](../standard-library/max-variable-size-class.md).|
|[cache_chunklist](../standard-library/cache-chunklist-class.md)|Definuje bloku alokátoru, který přiděluje a zruší přidělení bloků paměti z jednoho velikost.|
|[cache_freelist](../standard-library/cache-freelist-class.md)|Definuje bloku alokátoru, který přiděluje a zruší přidělení bloků paměti z jednoho velikost.|
|[cache_suballoc](../standard-library/cache-suballoc-class.md)|Definuje bloku alokátoru, který přiděluje a zruší přidělení bloků paměti z jednoho velikost.|
|[FreeList –](../standard-library/freelist-class.md)|Spravuje seznam bloky paměti.|
|[max_fixed_size](../standard-library/max-fixed-size-class.md)|Popisuje objekt maximální třídy, která omezuje [freelist](../standard-library/freelist-class.md) objektu na pevnou maximální délku.|
|[max_none](../standard-library/max-none-class.md)|Popisuje objekt maximální třídy, která omezuje [freelist](../standard-library/freelist-class.md) objekt má maximální délku nula.|
|[max_unbounded](../standard-library/max-unbounded-class.md)|Popisuje maximální třídu objektu, který neomezuje maximální délku [freelist](../standard-library/freelist-class.md) objektu.|
|[max_variable_size](../standard-library/max-variable-size-class.md)|Popisuje objekt maximální třídy, která omezuje [freelist](../standard-library/freelist-class.md) objekt má maximální délku, která je přibližně úměrný počtu přidělených paměťových bloků.|
|[rts_alloc](../standard-library/rts-alloc-class.md)|Rts_alloc – třída šablony popisuje [filtr](../standard-library/allocators-header.md) , který obsahuje celou řadu mezipaměti instancí a určuje, kterou instanci chcete použít pro přidělování a navracení zpět za běhu místo v době kompilace.|
|[sync_none](../standard-library/sync-none-class.md)|Popisuje synchronizaci filtr, který poskytuje žádná synchronizace.|
|[sync_per_container](../standard-library/sync-per-container-class.md)|Popisuje synchronizaci filtr, který poskytuje objekt samostatné mezipaměti pro každý objekt alokátoru.|
|[sync_per_thread](../standard-library/sync-per-thread-class.md)|Popisuje synchronizaci filtr, který poskytuje objekt samostatné mezipaměti pro každé vlákno.|
|[sync_shared](../standard-library/sync-shared-class.md)|Popisuje synchronizaci filtr, který se používá k řízení přístupu pro objekt z mezipaměti, jež jsou sdílena všechny alokátory mutex.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<alokátorů >

**Namespace:** stdext

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
