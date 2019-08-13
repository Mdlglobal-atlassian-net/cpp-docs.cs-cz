---
title: '&lt;rezident&gt;'
ms.date: 08/04/2019
f1_keywords:
- memory/std::<memory>
- <memory>
- std::<memory>
helpviewer_keywords:
- memory header
ms.openlocfilehash: 869a7590d880beba7ccc1d324fd1ba227eeac4e0
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957092"
---
# <a name="ltmemorygt"></a>&lt;rezident&gt;

Definuje třídu, operátor a několik šablon, které pomáhají přidělit a uvolnit objekty.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> paměti

**Obor názvů:** std

## <a name="members"></a>Členové

### <a name="functions"></a>Funkce

|||
|-|-|
|[addressof](../standard-library/memory-functions.md#addressof)|Získá adresu true objektu.|
|[align](../standard-library/memory-functions.md#align)|Vrací ukazatel na rozsah dané velikosti na základě zadaného zarovnání a počáteční adresy.|
|[allocate_shared](../standard-library/memory-functions.md#allocate_shared)|`shared_ptr` Vytvoří objekty, které jsou přiděleny a konstruovány pro daný typ se zadaným přidělováním.|
|[atomic_compare_exchange_strong](../standard-library/memory-functions.md#atomic_compare_exchange_strong)||
|[atomic_compare_exchange_weak](../standard-library/memory-functions.md#atomic_compare_exchange_weak)||
|[atomic_compare_exchange_strong_explicit](../standard-library/memory-functions.md#atomic_compare_exchange_strong_explicit)||
|[atomic_compare_exchange_weak_explicit](../standard-library/memory-functions.md#atomic_compare_exchange_weak_explicit)||
|[atomic_exchange](../standard-library/memory-functions.md#atomic_exchange)||
|[atomic_exchange_explicit](../standard-library/memory-functions.md#atomic_exchange_explicit)||
|[atomic_is_lock_free](../standard-library/memory-functions.md#atomic_is_lock_free)||
|[atomic_load](../standard-library/memory-functions.md#atomic_load)||
|[atomic_load_explicit](../standard-library/memory-functions.md#atomic_load_explicit)||
|[atomic_store](../standard-library/memory-functions.md#atomic_store)||
|[atomic_store_explicit](../standard-library/memory-functions.md#atomic_store_explicit)||
|[const_pointer_cast](../standard-library/memory-functions.md#const_pointer_cast)|Const Cast `shared_ptr`na.|
|[declare_no_pointers](../standard-library/memory-functions.md#declare_no_pointers)|Informuje uvolňování paměti, že znaky počínaje zadanou adresu spadající do určené velikosti bloku neobsahují sledovatelné ukazatele.|
|[declare_reachable](../standard-library/memory-functions.md#declare_reachable)|Informuje uvolňování paměti, že je uvedena adresa pro přidělení úložištěm a je k dispozici.|
|[default_delete](../standard-library/memory-functions.md#default_delete)|Odstraní objekty, které `operator new`jsou přiděleny pomocí. Vhodný pro použití s `unique_ptr`nástrojem.|
|[destroy_at](../standard-library/memory-functions.md#destroy_at)|Metoda `destroy` zkrácených.|
|[způsobit](../standard-library/memory-functions.md#destroy)|Metoda `destroy` zkrácených.|
|[destroy_n](../standard-library/memory-functions.md#destroy_n)|Metoda `destroy` zkrácených.|
|[dynamic_pointer_cast](../standard-library/memory-functions.md#dynamic_pointer_cast)|Dynamické přetypování `shared_ptr`na.|
|[get_deleter](../standard-library/memory-functions.md#get_deleter)|Získat odstranění z `shared_ptr`.|
|[get_pointer_safety](../standard-library/memory-functions.md#get_pointer_safety)|Vrátí typ zabezpečení ukazatele uvedený v rámci uvolňování paměti.|
|[get_temporary_buffer](../standard-library/memory-functions.md#get_temporary_buffer)|Přidělí dočasné úložiště pro řadu prvků, která není větší než zadaný počet prvků.|
|[make_shared](../standard-library/memory-functions.md#make_shared)|Vytvoří a vrátí `shared_ptr` , který odkazuje na přidělený objekt vytvořený z nuly nebo více argumentů pomocí výchozího přidělování.|
|[make_unique](../standard-library/memory-functions.md#make_unique)|Vytvoří a vrátí [unique_ptr](../standard-library/unique-ptr-class.md) , který odkazuje na přidělený objekt vytvořený z nuly nebo více argumentů.|
|[pointer_safety](../standard-library/memory-enums.md#pointer_safety)|Výčet všech možných vrácených hodnot pro `get_pointer_safety`.|
|[return_temporary_buffer](../standard-library/memory-functions.md#return_temporary_buffer)|Zruší přidělení dočasné paměti, která byla přidělena pomocí `get_temporary_buffer` funkce šablony.|
|[static_pointer_cast](../standard-library/memory-functions.md#static_pointer_cast)|Statické přetypování `shared_ptr`na.|
|[swap](../standard-library/memory-functions.md#swap)|Proměňte `shared_ptr` dva `weak_ptr` objekty nebo.|
|[undeclare_no_pointers](../standard-library/memory-functions.md#undeclare_no_pointers)|Informuje uvolňování paměti, že některé znaky v bloku paměti definované ukazatelem základní adresy a velikostí bloku mohou nyní obsahovat sledovatelné ukazatele.|
|[undeclare_reachable](../standard-library/memory-functions.md#undeclare_reachable)|Informuje o `garbage_collector` tom, že zadané umístění v paměti není dostupné.|
|[uninitialized_copy](../standard-library/memory-functions.md#uninitialized_copy)|Zkopíruje objekty ze zadaného rozsahu vstupu do neinicializované cílové oblasti.|
|[uninitialized_copy_n](../standard-library/memory-functions.md#uninitialized_copy_n)|Vytvoří kopii zadaného počtu prvků ze vstupního iterátoru. Kopie jsou umístěny v dopředném iterátoru.|
|[uninitialized_default_construct](../standard-library/memory-functions.md#uninitialized_default_construct)|Metoda `uninitialized_default_construct` zkrácených.|
|[uninitialized_default_construct_n](../standard-library/memory-functions.md#uninitialized_default_construct_n)|Metoda `uninitialized_construct` zkrácených.|
|[uninitialized_fill](../standard-library/memory-functions.md#uninitialized_fill)|Zkopíruje objekty ze zadané hodnoty do neinicializované cílové oblasti.|
|[uninitialized_fill_n](../standard-library/memory-functions.md#uninitialized_fill_n)|Zkopíruje objekty zadané hodnoty do zadaného počtu neinicializované cílové oblasti.|
|[uninitialized_move](../standard-library/memory-functions.md#uninitialized_move)|Metoda `uninitialized_move` zkrácených.|
|[uninitialized_move_n](../standard-library/memory-functions.md#uninitialized_move_n)|Metoda `uninitialized_move` zkrácených.|
|[uninitialized_value_construct](../standard-library/memory-functions.md#uninitialized_value_construct)|Metoda `uninitialized_value_construct` zkrácených.|
|[uninitialized_value_construct_n](../standard-library/memory-functions.md#uninitialized_value_construct_n)|Metoda `uninitialized_value_construct` zkrácených.|
|[uses_allocator_v](../standard-library/memory-functions.md#uses_allocator_v)||

### <a name="operators"></a>Operátory

|||
|-|-|
|[operator!=](../standard-library/memory-operators.md#op_neq)|Testy pro nerovnost mezi objekty přidělování z dané třídy.|
|[operator==](../standard-library/memory-operators.md#op_eq_eq)|Testy pro rovnost mezi objekty přidělování z dané třídy.|
|[operator>=](../standard-library/memory-operators.md#op_gt_eq)|Testy pro jeden objekt přidělování, který je větší nebo roven druhému objektu přidělování z dané třídy.|
|[operátor <](../standard-library/memory-operators.md#op_lt)|Testy pro jeden objekt, který je menší, než druhý objekt z dané třídy.|
|[podnikatel\<=](../standard-library/memory-operators.md#op_gt_eq)|Testy pro jeden objekt, který je menší nebo roven druhému objektu z dané třídy.|
|[operátor >](../standard-library/memory-operators.md#op_gt)|Testy pro jeden objekt, který je větší, než druhý objekt z dané třídy.|
|[operátor < <](../standard-library/memory-operators.md#op_lt_lt)|`shared_ptr`Inserter.|

### <a name="classes"></a>Třídy

|||
|-|-|
|[allocator](../standard-library/allocator-class.md)|Třída šablony popisuje objekt, který spravuje přidělování úložiště a uvolnění pro pole objektů typu typ.|
|[allocator_traits](../standard-library/allocator-traits-class.md)|Popisuje objekt, který určuje všechny informace požadované kontejnerem s povoleným přidělováním.|
|[auto_ptr](../standard-library/auto-ptr-class.md)|Třída šablony popisuje objekt, který ukládá ukazatel na přidělený objekt typu typ <strong>\*</strong> , který zajišťuje, že objekt, ke kterému se odkazuje, bude odstraněn, když je jeho ohraničující auto_ptr zničen.|
|[bad_weak_ptr](../standard-library/bad-weak-ptr-class.md)|Nahlásí chybnou výjimku weak_ptr.|
|[enabled_shared_from_this](../standard-library/enable-shared-from-this-class.md)|Pomáhá generovat `shared_ptr`.|
|[pointer_traits](../standard-library/pointer-traits-struct.md)|Poskytuje informace, které jsou vyžadovány objektem třídy `allocator_traits` šablony pro popis přidělování s typem `Ptr`ukazatele.|
|[raw_storage_iterator](../standard-library/raw-storage-iterator-class.md)|Třída adaptéru, která je k dispozici pro povolení algoritmů pro ukládání výsledků do neinicializované paměti.|
|[shared_ptr](../standard-library/shared-ptr-class.md)|Zabalí inteligentní ukazatel počítaný odkazy do dynamicky alokovaného objektu.|
|[unique_ptr](../standard-library/unique-ptr-class.md)|Uchovává ukazatel na vlastní objekt. Ukazatel není ve vlastnictví žádné jiné `unique_ptr`. `unique_ptr` Je zničen při zničení vlastníka.|
|[weak_ptr](../standard-library/weak-ptr-class.md)|Zalomí slabě propojený ukazatel.|

### <a name="structures"></a>Struktury

|||
|-|-|
|[allocator_arg_t](../standard-library/allocator-class.md#allocator_arg_t)||
|[default_delete](../standard-library/default-delete-struct.md)||
|hash|Poskytuje přetížení specializované na `unique_ptr` a. `shared_ptr`|
|[owner_less](../standard-library/memory-functions.md#owner_less)|Umožňuje smíšené porovnání sdílených a slabých ukazatelů na základě vlastnictví.|
|[uses_allocator](../standard-library/allocator-class.md#uses_allocator)||

### <a name="specializations"></a>Specializace

|||
|-|-|
|[>\<přidělování anulování](../standard-library/allocator-void-class.md)|Specializace přidělování tříd šablon k typu **void**, definující pouze typy členů, které mají smysl v tomto specializovaném kontextu.|

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
