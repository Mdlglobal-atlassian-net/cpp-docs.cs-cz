---
title: '&lt;allocators &gt;'
ms.date: 11/04/2016
f1_keywords:
- <allocators>
helpviewer_keywords:
- allocators header
ms.assetid: 4393a607-4df8-4278-bbb2-c8ec52e60b83
ms.openlocfilehash: 3619f3810f167fef291ad3def4a2b94f9a6b9b1a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688481"
---
# <a name="ltallocatorsgt"></a>&lt;allocators &gt;

Definuje několik šablon, které pomůžou přidělit a uvolnit bloky paměti pro kontejnery založené na uzlech.

## <a name="syntax"></a>Syntaxe

```cpp
#include <allocators>
```

## <a name="remarks"></a>Poznámky

Hlavička \<allocators > poskytuje šest šablon přidělování, které se dají použít k výběru strategií pro správu paměti pro kontejnery založené na uzlech. Pro použití s těmito šablonami poskytuje také několik různých synchronizačních filtrů, pomocí kterých můžete přizpůsobit strategii pro správu paměti pro celou řadu různých schémat s více vlákny (včetně žádné). Přiřazení strategie správy paměti ke známým vzorům využití paměti a požadavkům na synchronizaci konkrétní aplikace může často zvýšit rychlost nebo snížit celkové nároky na paměť aplikace.

Šablony přidělování jsou implementovány s opakovaně použitelnými součástmi, které lze přizpůsobit nebo nahradit, aby poskytovaly další strategie správy paměti.

Kontejnery založené na uzlech ve C++ standardní knihovně (std:: list, std:: set, std:: multiset, std:: map a std:: multimap) ukládají jejich prvky do jednotlivých uzlů. Všechny uzly pro určitý typ kontejneru mají stejnou velikost, takže není potřeba flexibilita správce paměti pro obecné účely. Vzhledem k tomu, že velikost každého bloku paměti je známa v době kompilace, může být správce paměti mnohem jednodušší a rychlejší.

Při použití s kontejnery, které nejsou založené na uzlu (například C++ standardní kontejnery knihovny std:: Vector std::d eque a std:: basic_string), budou šablony alllocator fungovat správně, ale neposkytují lepší zlepšení výkonu. výchozí Alokátor.

Alokátor je šablona třídy, která popisuje objekt, který spravuje přidělování úložiště a uvolňuje pro objekty a pole objektů určeného typu. Objekty přidělování jsou používány několika šablonami třídy kontejneru ve C++ standardní knihovně.

Přidělování jsou všechny šablony tohoto typu:

```cpp
template<class Type>
class allocator;
```

kde argument šablony `Type` je typ spravovaný instancí přidělování. C++ Standardní knihovna poskytuje výchozí přidělování, [přidělování](../standard-library/allocator-class.md)šablon třídy, které je definováno v [\<memory >](../standard-library/memory.md). Hlavička \<allocators > poskytuje následující přidělování:

- [allocator_newdel](../standard-library/allocator-newdel-class.md)

- [allocator_unbounded](../standard-library/allocator-unbounded-class.md)

- [allocator_fixed_size](../standard-library/allocator-fixed-size-class.md)

- [allocator_variable_size](../standard-library/allocator-variable-size-class.md)

- [allocator_suballoc](../standard-library/allocator-suballoc-class.md)

- [allocator_chunklist](../standard-library/allocator-chunklist-class.md)

Použijte při vytváření kontejneru vhodné vytvoření instance přidělování jako druhý argument typu, například následující příklad kódu.

```cpp
#include <list>
#include <allocators>
std::list<int, stdext::allocators::allocator_chunklist<int> > _List0;
```

_List0 přiděluje uzly pomocí `allocator_chunklist` a výchozího synchronizačního filtru.

Použijte makro [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) k vytvoření šablon přidělování s výjimkou výchozích filtrů synchronizace:

```cpp
#include <list>
#include <allocators>
ALLOCATOR_DECL(CACHE_CHUNKLIST, stdext::allocators::sync_per_thread, Alloc);
std::list<int, alloc<int> > _List1;
```

_Lst1 přiděluje uzly pomocí `allocator_chunklist` a filtru synchronizace [sync_per_thread](../standard-library/sync-per-thread-class.md) .

Přidělování bloků je mezipaměť nebo filtr. Mezipaměť je šablona třídy, která přijímá jeden argument typu std:: size_t. Definuje přidělování bloků, které přiděluje a naděluje bloky paměti pro jedinou velikost. Musí získat paměť pomocí operátoru **New**, ale nemusí učinit samostatné volání operátoru **New** pro každý blok. Může být například rozdělení z většího bloku nebo nepřidělené bloky mezipaměti pro následné přerozdělení.

S kompilátorem, který nelze zkompilovat znovu s hodnotou argumentu std:: size_t použitého při vytváření instance šablony, není nutně hodnota argumentu _Sz předaná do členských funkcí mezipaměti allocate a unallocate.

\<allocators > poskytuje následující šablony mezipaměti:

- [cache_freelist](../standard-library/cache-freelist-class.md)

- [cache_suballoc](../standard-library/cache-suballoc-class.md)

- [cache_chunklist](../standard-library/cache-chunklist-class.md)

Filtr je Alokátor bloku, který implementuje své členské funkce pomocí jiného přidělování bloků, který je předán jako argument šablony. Nejběžnější forma filtru je filtr synchronizace, který pro řízení přístupu k členským funkcím instance jiného přidělování bloků používá zásady synchronizace. \<allocators > poskytuje následující filtry synchronizace:

- [sync_none](../standard-library/sync-none-class.md)

- [sync_per_container](../standard-library/sync-per-container-class.md)

- [sync_per_thread](../standard-library/sync-per-thread-class.md)

- [sync_shared](../standard-library/sync-shared-class.md)

\<allocators > také poskytuje filtr [rts_alloc](../standard-library/rts-alloc-class.md), který obsahuje více instancí přidělování bloků a určuje, která instance má být použita pro přidělení nebo zrušení přidělení za běhu místo v době kompilace. Používá se s kompilátory, které nemohou kompilovat opětovnou vazby.

Zásady synchronizace určují, jak instance přidělování zpracovává souběžné žádosti o přidělení a zrušení přidělení z více vláken. Nejjednodušší zásada je předat všechny požadavky přímo do podkladového objektu mezipaměti a zachová správu synchronizace pro uživatele. Složitější zásada by mohla použít mutex k serializaci přístupu k základnímu objektu mezipaměti.

Pokud kompilátor podporuje kompilování vícevláknové i vícevláknové aplikace, je výchozí filtr synchronizace pro aplikace s jedním vláknem `sync_none`; pro všechny ostatní případy je `sync_shared`.

Šablona mezipaměti `cache_freelist` přijímá maximální argument třídy, který určuje maximální počet prvků, které mají být uloženy v seznamu Free.

\<allocators > poskytuje následující maximální třídy:

- [max_none](../standard-library/max-none-class.md)

- [max_unbounded](../standard-library/max-unbounded-class.md)

- [max_fixed_size](../standard-library/max-fixed-size-class.md)

- [max_variable_size](../standard-library/max-variable-size-class.md)

### <a name="macros"></a>Makra

|Podokně|Popis|
|-|-|
|[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)|Poskytne šablonu třídy přidělování.|
|[CACHE_CHUNKLIST](../standard-library/allocators-functions.md#cache_chunklist)|Vypočítá `stdext::allocators::cache_chunklist<sizeof(Type)>`.|
|[CACHE_FREELIST](../standard-library/allocators-functions.md#cache_freelist)|Vypočítá `stdext::allocators::cache_freelist<sizeof(Type), max>`.|
|[CACHE_SUBALLOC](../standard-library/allocators-functions.md#cache_suballoc)|Vypočítá `stdext::allocators::cache_suballoc<sizeof(Type)>`.|
|[SYNC_DEFAULT](../standard-library/allocators-functions.md#sync_default)|Vypočítá filtr synchronizace.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator! = (\<allocators >)](../standard-library/allocators-operators.md#op_neq)|Testy pro nerovnost mezi objekty přidělování z dané třídy.|
|[operator = = (\<allocators >)](../standard-library/allocators-operators.md#op_eq_eq)|Testy pro rovnost mezi objekty přidělování z dané třídy.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[allocator_base](../standard-library/allocator-base-class.md)|Definuje základní třídu a běžné funkce potřebné k vytvoření uživatelem definovaného přidělování z filtru synchronizace.|
|[allocator_chunklist](../standard-library/allocator-chunklist-class.md)|Popisuje objekt, který spravuje přidělování úložiště a uvolňuje pro objekty pomocí mezipaměti typu [cache_chunklist](../standard-library/cache-chunklist-class.md).|
|[allocator_fixed_size](../standard-library/allocator-fixed-size-class.md)|Popisuje objekt, který spravuje přidělování úložiště a uvolňuje pro objekty typu `Type` pomocí mezipaměti typu [cache_freelist](../standard-library/cache-freelist-class.md) s délkou spravovanou [max_fixed_size](../standard-library/max-fixed-size-class.md).|
|[allocator_newdel](../standard-library/allocator-newdel-class.md)|Implementuje Alokátor, který používá **operátor delete** k navrácení bloku paměti a **operátoru new** pro přidělení bloku paměti.|
|[allocator_suballoc](../standard-library/allocator-suballoc-class.md)|Popisuje objekt, který spravuje přidělování úložiště a uvolňuje pro objekty typu `Type` pomocí mezipaměti typu [cache_suballoc](../standard-library/cache-suballoc-class.md).|
|[allocator_unbounded](../standard-library/allocator-unbounded-class.md)|Popisuje objekt, který spravuje přidělování úložiště a uvolňuje pro objekty typu `Type` pomocí mezipaměti typu [cache_freelist](../standard-library/cache-freelist-class.md) s délkou spravovanou [max_unbounded](../standard-library/max-unbounded-class.md).|
|[allocator_variable_size](../standard-library/allocator-variable-size-class.md)|Popisuje objekt, který spravuje přidělování úložiště a uvolňuje pro objekty typu `Type` pomocí mezipaměti typu [cache_freelist](../standard-library/cache-freelist-class.md) s délkou spravovanou [max_variable_size](../standard-library/max-variable-size-class.md).|
|[cache_chunklist](../standard-library/cache-chunklist-class.md)|Definuje přidělování bloků, které přiděluje a odděluje bloky paměti s jednou velikostí.|
|[cache_freelist](../standard-library/cache-freelist-class.md)|Definuje přidělování bloků, které přiděluje a odděluje bloky paměti s jednou velikostí.|
|[cache_suballoc](../standard-library/cache-suballoc-class.md)|Definuje přidělování bloků, které přiděluje a odděluje bloky paměti s jednou velikostí.|
|[freelist –](../standard-library/freelist-class.md)|Spravuje seznam bloků paměti.|
|[max_fixed_size](../standard-library/max-fixed-size-class.md)|Popisuje maximální objekt třídy, který omezuje objekt [freelist –](../standard-library/freelist-class.md) na pevnou maximální délku.|
|[max_none](../standard-library/max-none-class.md)|Popisuje maximální objekt třídy, který omezuje objekt [freelist –](../standard-library/freelist-class.md) na maximální délku nula.|
|[max_unbounded](../standard-library/max-unbounded-class.md)|Popisuje maximální objekt třídy, který neomezuje maximální délku objektu [freelist –](../standard-library/freelist-class.md) .|
|[max_variable_size](../standard-library/max-variable-size-class.md)|Popisuje objekt maximální třídy, který omezuje objekt [freelist –](../standard-library/freelist-class.md) na maximální délku, která je zhruba úměrná počtu přidělených bloků paměti.|
|[rts_alloc](../standard-library/rts-alloc-class.md)|Šablona třídy rts_alloc popisuje [Filtr](../standard-library/allocators-header.md) , který obsahuje pole instancí mezipaměti a určuje, která instance má být použita pro přidělení a zrušení přidělení za běhu místo v době kompilace.|
|[sync_none](../standard-library/sync-none-class.md)|Popisuje filtr synchronizace, který neposkytuje žádnou synchronizaci.|
|[sync_per_container](../standard-library/sync-per-container-class.md)|Popisuje filtr synchronizace, který poskytuje samostatný objekt mezipaměti pro každý objekt přidělování.|
|[sync_per_thread](../standard-library/sync-per-thread-class.md)|Popisuje filtr synchronizace, který poskytuje samostatný objekt mezipaměti pro každé vlákno.|
|[sync_shared](../standard-library/sync-shared-class.md)|Popisuje filtr synchronizace, který používá mutex k řízení přístupu k objektu mezipaměti, který je sdílen všemi přidělování.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<allocators >

**Obor názvů:** stdext

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)
