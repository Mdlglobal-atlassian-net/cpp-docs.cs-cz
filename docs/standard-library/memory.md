---
title: '&lt;memory &gt;'
ms.date: 08/04/2019
f1_keywords:
- memory/std::<memory>
- <memory>
- std::<memory>
helpviewer_keywords:
- memory header
ms.openlocfilehash: 4a6383ee94d021373b984122926a5bb73e18f953
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689369"
---
# <a name="ltmemorygt"></a>&lt;memory &gt;

Definuje třídu, operátor a několik šablon, které pomáhají přidělit a uvolnit objekty.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<memory >

**Obor názvů:** std

## <a name="members"></a>Členové

### <a name="functions"></a>Funkce

|||
|-|-|
|[AddressOf](../standard-library/memory-functions.md#addressof)|Získá adresu true objektu.|
|[align](../standard-library/memory-functions.md#align)|Vrací ukazatel na rozsah dané velikosti na základě zadaného zarovnání a počáteční adresy.|
|[allocate_shared](../standard-library/memory-functions.md#allocate_shared)|Vytvoří `shared_ptr` pro objekty, které jsou přiděleny a konstruovány pro daný typ se zadaným přidělováním.|
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
|[const_pointer_cast](../standard-library/memory-functions.md#const_pointer_cast)|Const cast na `shared_ptr`.|
|[declare_no_pointers](../standard-library/memory-functions.md#declare_no_pointers)|Informuje uvolňování paměti, že znaky počínaje zadanou adresu spadající do určené velikosti bloku neobsahují sledovatelné ukazatele.|
|[declare_reachable](../standard-library/memory-functions.md#declare_reachable)|Informuje uvolňování paměti, že je uvedena adresa pro přidělení úložištěm a je k dispozici.|
|[default_delete](../standard-library/memory-functions.md#default_delete)|Odstraní objekty přidělené s `operator new`. Vhodné pro použití s `unique_ptr`.|
|[destroy_at](../standard-library/memory-functions.md#destroy_at)|Zkrácený `destroy` metoda.|
|[způsobit](../standard-library/memory-functions.md#destroy)|Zkrácený `destroy` metoda.|
|[destroy_n](../standard-library/memory-functions.md#destroy_n)|Zkrácený `destroy` metoda.|
|[dynamic_pointer_cast](../standard-library/memory-functions.md#dynamic_pointer_cast)|Dynamické přetypování na `shared_ptr`.|
|[get_deleter](../standard-library/memory-functions.md#get_deleter)|Získat odstranění z `shared_ptr`.|
|[get_pointer_safety](../standard-library/memory-functions.md#get_pointer_safety)|Vrátí typ zabezpečení ukazatele uvedený v rámci uvolňování paměti.|
|[get_temporary_buffer](../standard-library/memory-functions.md#get_temporary_buffer)|Přidělí dočasné úložiště pro řadu prvků, která není větší než zadaný počet prvků.|
|[make_shared](../standard-library/memory-functions.md#make_shared)|Vytvoří a vrátí `shared_ptr`, který odkazuje na přidělený objekt vytvořený z nuly nebo více argumentů pomocí výchozího přidělování.|
|[make_unique](../standard-library/memory-functions.md#make_unique)|Vytvoří a vrátí [unique_ptr](../standard-library/unique-ptr-class.md) , který odkazuje na přidělený objekt vytvořený z nuly nebo více argumentů.|
|[pointer_safety](../standard-library/memory-enums.md#pointer_safety)|Výčet všech možných vrácených hodnot pro `get_pointer_safety`.|
|[return_temporary_buffer](../standard-library/memory-functions.md#return_temporary_buffer)|Zruší přidělení dočasné paměti, která byla přidělena pomocí funkce šablony `get_temporary_buffer`.|
|[static_pointer_cast](../standard-library/memory-functions.md#static_pointer_cast)|Statické přetypování na `shared_ptr`.|
|[adresu](../standard-library/memory-functions.md#swap)|Proměňte dva objekty `shared_ptr` nebo `weak_ptr`.|
|[undeclare_no_pointers](../standard-library/memory-functions.md#undeclare_no_pointers)|Informuje uvolňování paměti, že některé znaky v bloku paměti definované ukazatelem základní adresy a velikostí bloku mohou nyní obsahovat sledovatelné ukazatele.|
|[undeclare_reachable](../standard-library/memory-functions.md#undeclare_reachable)|Informuje `garbage_collector`, že zadané umístění v paměti není dostupné.|
|[uninitialized_copy](../standard-library/memory-functions.md#uninitialized_copy)|Zkopíruje objekty ze zadaného rozsahu vstupu do neinicializované cílové oblasti.|
|[uninitialized_copy_n](../standard-library/memory-functions.md#uninitialized_copy_n)|Vytvoří kopii zadaného počtu prvků ze vstupního iterátoru. Kopie jsou umístěny v dopředném iterátoru.|
|[uninitialized_default_construct](../standard-library/memory-functions.md#uninitialized_default_construct)|Zkrácený `uninitialized_default_construct` metoda.|
|[uninitialized_default_construct_n](../standard-library/memory-functions.md#uninitialized_default_construct_n)|Zkrácený `uninitialized_construct` metoda.|
|[uninitialized_fill](../standard-library/memory-functions.md#uninitialized_fill)|Zkopíruje objekty ze zadané hodnoty do neinicializované cílové oblasti.|
|[uninitialized_fill_n](../standard-library/memory-functions.md#uninitialized_fill_n)|Zkopíruje objekty zadané hodnoty do zadaného počtu neinicializované cílové oblasti.|
|[uninitialized_move](../standard-library/memory-functions.md#uninitialized_move)|Zkrácený `uninitialized_move` metoda.|
|[uninitialized_move_n](../standard-library/memory-functions.md#uninitialized_move_n)|Zkrácený `uninitialized_move` metoda.|
|[uninitialized_value_construct](../standard-library/memory-functions.md#uninitialized_value_construct)|Zkrácený `uninitialized_value_construct` metoda.|
|[uninitialized_value_construct_n](../standard-library/memory-functions.md#uninitialized_value_construct_n)|Zkrácený `uninitialized_value_construct` metoda.|
|[uses_allocator_v](../standard-library/memory-functions.md#uses_allocator_v)||

### <a name="operators"></a>Operátory

|||
|-|-|
|[operator!=](../standard-library/memory-operators.md#op_neq)|Testy pro nerovnost mezi objekty přidělování z dané třídy.|
|[operator = = – operátor](../standard-library/memory-operators.md#op_eq_eq)|Testy pro rovnost mezi objekty přidělování z dané třídy.|
|[operator>=](../standard-library/memory-operators.md#op_gt_eq)|Testy pro jeden objekt přidělování, který je větší nebo roven druhému objektu přidělování z dané třídy.|
|[operátor <](../standard-library/memory-operators.md#op_lt)|Testy pro jeden objekt, který je menší, než druhý objekt z dané třídy.|
|[operátor \< =](../standard-library/memory-operators.md#op_gt_eq)|Testy pro jeden objekt, který je menší nebo roven druhému objektu z dané třídy.|
|[operátor >](../standard-library/memory-operators.md#op_gt)|Testy pro jeden objekt, který je větší, než druhý objekt z dané třídy.|
|[operátor < <](../standard-library/memory-operators.md#op_lt_lt)|`shared_ptr` Inserter.|

### <a name="classes"></a>Třídy

|||
|-|-|
|[allocator](../standard-library/allocator-class.md)|Šablona třídy popisuje objekt, který spravuje přidělování úložiště a uvolnění pro pole **objektů typu typ.**|
|[allocator_traits](../standard-library/allocator-traits-class.md)|Popisuje objekt, který určuje všechny informace požadované kontejnerem s povoleným přidělováním.|
|[auto_ptr](../standard-library/auto-ptr-class.md)|Šablona třídy popisuje objekt, který ukládá ukazatel na přidělený **objekt typu type** <strong>\*</strong> , který zajišťuje, aby objekt, ke kterému se odkazuje, byl odstraněn, když se auto_ptr jeho ohraničujícího objektu pro zničení.|
|[bad_weak_ptr](../standard-library/bad-weak-ptr-class.md)|Nahlásí chybnou výjimku weak_ptr.|
|[enabled_shared_from_this](../standard-library/enable-shared-from-this-class.md)|Pomáhá generovat `shared_ptr`.|
|[pointer_traits](../standard-library/pointer-traits-struct.md)|Poskytuje informace, které jsou vyžadovány objektem typu `allocator_traits` k popisu modulu přidělování s typem ukazatele `Ptr`.|
|[raw_storage_iterator](../standard-library/raw-storage-iterator-class.md)|Třída adaptéru, která je k dispozici pro povolení algoritmů pro ukládání výsledků do neinicializované paměti.|
|[shared_ptr](../standard-library/shared-ptr-class.md)|Zabalí inteligentní ukazatel počítaný odkazy do dynamicky alokovaného objektu.|
|[unique_ptr](../standard-library/unique-ptr-class.md)|Uchovává ukazatel na vlastní objekt. Ukazatel je vlastněn žádným jiným `unique_ptr`. @No__t_0 je zničen při zničení vlastníka.|
|[weak_ptr](../standard-library/weak-ptr-class.md)|Zalomí slabě propojený ukazatel.|

### <a name="structures"></a>Struktury

|||
|-|-|
|[allocator_arg_t](../standard-library/allocator-class.md#allocator_arg_t)||
|[default_delete](../standard-library/default-delete-struct.md)||
|hash|Poskytuje přetížení specializované na `unique_ptr` a `shared_ptr`.|
|[owner_less](../standard-library/memory-functions.md#owner_less)|Umožňuje smíšené porovnání sdílených a slabých ukazatelů na základě vlastnictví.|
|[uses_allocator](../standard-library/allocator-class.md#uses_allocator)||

### <a name="specializations"></a>Specializace

|||
|-|-|
|[> \<void přidělování](../standard-library/allocator-void-class.md)|Specializace přidělování šablon třídy k typu **void**, definující pouze typy členů, které v tomto specializovaném kontextu tvoří smysl.|

## <a name="see-also"></a>Viz také:

@No__t_1 [referenčních souborů hlaviček](../standard-library/cpp-standard-library-header-files.md)
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
