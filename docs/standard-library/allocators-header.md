---
title: '&lt;alokátory&gt;'
ms.date: 11/04/2016
f1_keywords:
- <allocators>
helpviewer_keywords:
- allocators header
ms.assetid: 4393a607-4df8-4278-bbb2-c8ec52e60b83
ms.openlocfilehash: f6be154be68cd5e43fd6f934d88c04fb25be9dc5
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754440"
---
# <a name="ltallocatorsgt"></a>&lt;alokátory&gt;

Definuje několik šablon, které pomáhají přidělit a uvolnit paměťové bloky pro kontejnery založené na uzlu.

## <a name="syntax"></a>Syntaxe

```cpp
#include <allocators>
```

> [!NOTE]
> \<alokátory> je zastaralé, počínaje Visual Studio 2019 verze 16.3.

## <a name="remarks"></a>Poznámky

Alokátory \<> záhlaví poskytuje šest alokátor šablony, které lze použít k výběru strategie správy paměti pro kontejnery založené na uzlu. Pro použití s těmito šablonami také poskytuje několik různých filtrů synchronizace přizpůsobit strategii správy paměti na různých schémata více vláken (včetně žádné). Aplikaci můžete urychlit nebo snížit její požadavky na paměť tak, že slovítestrategii správy paměti jejím vzorcům využití paměti a požadavkům na synchronizaci.

Šablony přidělování jsou implementovány s opakovaně použitelnými součástmi, které lze přizpůsobit nebo nahradit tak, aby poskytovaly další strategie správy paměti.

Kontejnery založené na uzlu ve standardní knihovně jazyka C++ (std::list, std::set, std::multiset, std::map a std::multimap) ukládají své prvky do jednotlivých uzlů. Všechny uzly pro konkrétní typ kontejneru mají stejnou velikost, takže flexibilita správce paměti pro obecné účely není potřeba. Vzhledem k tomu, že velikost každého bloku paměti je známa v době kompilace, správce paměti může být mnohem jednodušší a rychlejší.

Při použití s kontejnery, které nejsou založeny na uzlu (například kontejnery standardní knihovny C++std::vector std::deque a std::basic_string), budou šablony přidělování fungovat správně, ale pravděpodobně neposkytují žádné zlepšení výkonu oproti výchozímu alokátoru.

Alokátor je šablona třídy, která popisuje objekt, který spravuje přidělení úložiště a uvolnění pro objekty a pole objektů určeného typu. Objekty alokátoru jsou používány několika šablonami tříd kontejneru ve standardní knihovně jazyka C++.

Alokátory jsou všechny šablony tohoto typu:

```cpp
template<class Type>
class allocator;
```

kde argument `Type` šablony je typ spravovaný instancí alokátoru. Standardní knihovna jazyka C++ poskytuje výchozí alokátor, [alokátor](../standard-library/allocator-class.md)šablony [ \< ](../standard-library/memory.md)třídy , který je definován v paměti>. Alokátory \<> záhlaví poskytuje následující alokátory:

- [allocator_newdel](../standard-library/allocator-newdel-class.md)

- [allocator_unbounded](../standard-library/allocator-unbounded-class.md)

- [allocator_fixed_size](../standard-library/allocator-fixed-size-class.md)

- [allocator_variable_size](../standard-library/allocator-variable-size-class.md)

- [allocator_suballoc](../standard-library/allocator-suballoc-class.md)

- [allocator_chunklist](../standard-library/allocator-chunklist-class.md)

Při vytváření kontejneru použijte vhodnou konkretioncionátoru jako argument druhého typu, například následující příklad kódu.

```cpp
#include <list>
#include <allocators>
std::list<int, stdext::allocators::allocator_chunklist<int> > _List0;
```

_List0 přiděluje `allocator_chunklist` uzly s a výchozí synchronizační filtr.

Pomocí [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) maker můžete vytvářet šablony alokátoru s jinými než výchozími filtry synchronizace:

```cpp
#include <list>
#include <allocators>
ALLOCATOR_DECL(CACHE_CHUNKLIST, stdext::allocators::sync_per_thread, Alloc);
std::list<int, alloc<int> > _List1;
```

_Lst1 přiděluje `allocator_chunklist` uzly s filtrem [synchronizace sync_per_thread.](../standard-library/sync-per-thread-class.md)

Blok přidělování je mezipaměť nebo filtr. Mezipaměť je šablona třídy, která přebírá jeden argument typu std::size_t. Definuje blok přidělování, který přiděluje a navrací paměťové bloky jedné velikosti. Musí získat paměť pomocí **operátoru new**, ale nemusí provést samostatné volání **operátoru nové** pro každý blok. Může například přidělit z větší blok nebo mezipaměti přidělené bloky pro následné přerozdělení.

S kompilátorem, který nemůže znovu vytvořit vazbu hodnotu argumentu std::size_t použitého při vytvoření instance šablony, nemusí být nutně hodnota argumentu, _Sz předána členským funkcím mezipaměti přidělit a navrátit.

\<alokátory> poskytuje následující šablony mezipaměti:

- [cache_freelist](../standard-library/cache-freelist-class.md)

- [cache_suballoc](../standard-library/cache-suballoc-class.md)

- [cache_chunklist](../standard-library/cache-chunklist-class.md)

Filtr je alokátor bloků, který implementuje své členské funkce pomocí jiného alokátoru bloků, který je mu předán jako argument šablony. Nejběžnější formou filtru je filtr synchronizace, který používá zásady synchronizace pro řízení přístupu k členským funkcím instance jiného alokátoru bloku. \<alokátory> poskytuje následující filtry synchronizace:

- [sync_none](../standard-library/sync-none-class.md)

- [sync_per_container](../standard-library/sync-per-container-class.md)

- [sync_per_thread](../standard-library/sync-per-thread-class.md)

- [sync_shared](../standard-library/sync-shared-class.md)

\<alokátory> také poskytuje filtr [rts_alloc](../standard-library/rts-alloc-class.md), který obsahuje více instancí alokátoru bloku a určuje, kterou instanci použít pro přidělení nebo deallocation za běhu namísto v době kompilace. Používá se s kompilátory, které nelze zkompilovat rebind.

Zásady synchronizace určuje, jak instance přidělování zpracovává souběžné požadavky na přidělení a přidělení z více vláken. Nejjednodušší zásadou je předat všechny požadavky přímo do základního objektu mezipaměti a ponechat správu synchronizace uživateli. Složitější zásadou může být použití objektu mutex k serializaci přístupu k podkladovému objektu mezipaměti.

Pokud kompilátor podporuje kompilaci aplikací s jedním vláknem i více vlákny, je `sync_none`výchozím filtrem synchronizace pro jednovláknové aplikace ; pro všechny ostatní `sync_shared`případy je .

Šablona `cache_freelist` mezipaměti přebírá argument třídy max, který určuje maximální počet prvků, které mají být uloženy v seznamu volných.

\<alokátory> poskytuje následující max třídy:

- [max_none](../standard-library/max-none-class.md)

- [max_unbounded](../standard-library/max-unbounded-class.md)

- [max_fixed_size](../standard-library/max-fixed-size-class.md)

- [max_variable_size](../standard-library/max-variable-size-class.md)

### <a name="macros"></a>Makra

|Makro|Popis|
|-|-|
|[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)|Dává šablonu třídy přidělování.|
|[CACHE_CHUNKLIST](../standard-library/allocators-functions.md#cache_chunklist)|Výnosy `stdext::allocators::cache_chunklist<sizeof(Type)>`.|
|[CACHE_FREELIST](../standard-library/allocators-functions.md#cache_freelist)|Výnosy `stdext::allocators::cache_freelist<sizeof(Type), max>`.|
|[CACHE_SUBALLOC](../standard-library/allocators-functions.md#cache_suballoc)|Výnosy `stdext::allocators::cache_suballoc<sizeof(Type)>`.|
|[SYNC_DEFAULT](../standard-library/allocators-functions.md#sync_default)|Poskytuje filtr synchronizace.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor!=\<( alokátory>)](../standard-library/allocators-operators.md#op_neq)|Testy pro nerovnost mezi objekty přidělování z dané třídy.|
|[operator==\<( alokátory>)](../standard-library/allocators-operators.md#op_eq_eq)|Testy pro rovnost mezi objekty přidělování z dané třídy.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[allocator_base](../standard-library/allocator-base-class.md)|Definuje základní třídu a běžné funkce potřebné k vytvoření uživatelem definovaného alokátoru z filtru synchronizace.|
|[allocator_chunklist](../standard-library/allocator-chunklist-class.md)|Popisuje objekt, který spravuje přidělení úložiště a uvolnění pro objekty pomocí mezipaměti typu [cache_chunklist](../standard-library/cache-chunklist-class.md).|
|[allocator_fixed_size](../standard-library/allocator-fixed-size-class.md)|Popisuje objekt, který spravuje přidělení úložiště a uvolnění `Type` pro objekty typu pomocí mezipaměti typu [cache_freelist](../standard-library/cache-freelist-class.md) s délkou spravovanou [max_fixed_size](../standard-library/max-fixed-size-class.md).|
|[allocator_newdel](../standard-library/allocator-newdel-class.md)|Implementuje přidělování, který používá **operátor delete** navrátit blok paměti a **operátor nový** přidělit blok paměti.|
|[allocator_suballoc](../standard-library/allocator-suballoc-class.md)|Popisuje objekt, který spravuje přidělení úložiště a uvolnění `Type` pro objekty typu pomocí mezipaměti typu [cache_suballoc](../standard-library/cache-suballoc-class.md).|
|[allocator_unbounded](../standard-library/allocator-unbounded-class.md)|Popisuje objekt, který spravuje přidělení úložiště a uvolnění `Type` pro objekty typu pomocí mezipaměti typu [cache_freelist](../standard-library/cache-freelist-class.md) s délkou spravovanou [max_unbounded](../standard-library/max-unbounded-class.md).|
|[allocator_variable_size](../standard-library/allocator-variable-size-class.md)|Popisuje objekt, který spravuje přidělení úložiště a uvolnění `Type` pro objekty typu pomocí mezipaměti typu [cache_freelist](../standard-library/cache-freelist-class.md) s délkou spravovanou [max_variable_size](../standard-library/max-variable-size-class.md).|
|[cache_chunklist](../standard-library/cache-chunklist-class.md)|Definuje blok přidělování, který přiděluje a navrací paměťové bloky jedné velikosti.|
|[cache_freelist](../standard-library/cache-freelist-class.md)|Definuje blok přidělování, který přiděluje a navrací paměťové bloky jedné velikosti.|
|[cache_suballoc](../standard-library/cache-suballoc-class.md)|Definuje blok přidělování, který přiděluje a navrací paměťové bloky jedné velikosti.|
|[volný seznam](../standard-library/freelist-class.md)|Spravuje seznam paměťových bloků.|
|[max_fixed_size](../standard-library/max-fixed-size-class.md)|Popisuje objekt třídy max, který omezuje [objekt freelistu](../standard-library/freelist-class.md) na pevnou maximální délku.|
|[max_none](../standard-library/max-none-class.md)|Popisuje objekt třídy max, který omezuje objekt [freelist](../standard-library/freelist-class.md) na maximální délku nula.|
|[max_unbounded](../standard-library/max-unbounded-class.md)|Popisuje objekt třídy max, který neomezuje maximální délku [objektu freelist.](../standard-library/freelist-class.md)|
|[max_variable_size](../standard-library/max-variable-size-class.md)|Popisuje objekt třídy max, který omezuje [objekt freelist](../standard-library/freelist-class.md) na maximální délku, která je zhruba úměrná počtu přidělených bloků paměti.|
|[rts_alloc](../standard-library/rts-alloc-class.md)|Šablona třídy rts_alloc popisuje [filtr,](../standard-library/allocators-header.md) který obsahuje pole instancí mezipaměti a určuje, kterou instanci použít pro přidělení a deallocation za běhu namísto v době kompilace.|
|[sync_none](../standard-library/sync-none-class.md)|Popisuje filtr synchronizace, který neposkytuje žádnou synchronizaci.|
|[sync_per_container](../standard-library/sync-per-container-class.md)|Popisuje filtr synchronizace, který poskytuje samostatný objekt mezipaměti pro každý objekt přidělování.|
|[sync_per_thread](../standard-library/sync-per-thread-class.md)|Popisuje filtr synchronizace, který poskytuje samostatný objekt mezipaměti pro každé vlákno.|
|[sync_shared](../standard-library/sync-shared-class.md)|Popisuje filtr synchronizace, který používá objekt mutex k řízení přístupu k objektu mezipaměti, který je sdílen všemi alokátory.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<alokátory>

**Obor názvů:** stdext

## <a name="see-also"></a>Viz také

[Odkaz na soubory záhlaví](../standard-library/cpp-standard-library-header-files.md)
