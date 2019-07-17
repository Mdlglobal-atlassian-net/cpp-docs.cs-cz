---
title: '&lt;Paměť&gt;'
ms.date: 04/04/2019
f1_keywords:
- memory/std::<memory>
- <memory>
- std::<memory>
helpviewer_keywords:
- memory header
ms.openlocfilehash: d2776e658b511208d9a295cd84a961d7691d29e0
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246812"
---
# <a name="ltmemorygt"></a>&lt;Paměť&gt;

Definuje třídu, operátor a několik šablon, které pomáhají přidělit a uvolnit objekty.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<paměti >

**Namespace:** std

## <a name="members"></a>Členové

### <a name="functions"></a>Funkce

|||
|-|-|
|[addressof](../standard-library/memory-functions.md#addressof)|Získá adresu true objektu.|
|[align](../standard-library/memory-functions.md#align)|Vrací ukazatel na rozsah dané velikosti na základě zadaného zarovnání a počáteční adresy.|
|[allocate_shared](../standard-library/memory-functions.md#allocate_shared)|Vytvoří `shared_ptr` na objekty, které jsou přiděleny a konstruovány s alokátorem určeným pro daného typu.|
|[atomic_compare_exchange_strong](../standard-library/memory-functions.md#atomic_compare_exchange_strong)||
|[atomic_compare_exchange_weak](../standard-library/memory-functions.md#atomic_compare_exchange_weak)||
|[atomic_compare_exchange_strong_explicit](../standard-library/memory-functions.md#atomic_compare_exchange_strong_explicit)||
|[atomic_compare_exchange_weak_explicit](../standard-library/memory-functions.md#atomic_compare_exchange_weak_explicit)||
|[atomic_exchange](../standard-library/memory-functions.md#atomic_exchange)||
|[atomic_exchange_explicit](../standard-library/memory-functions.md#atomic_exchange_explicit)||
|[atomic_is_lock_free](../standard-library/memory-functions.md#atomic_is_lock_free)||
|[atomic_load –](../standard-library/memory-functions.md#atomic_load)||
|[atomic_load_explicit](../standard-library/memory-functions.md#atomic_load_explicit)||
|[atomic_store](../standard-library/memory-functions.md#atomic_store)||
|[atomic_store_explicit](../standard-library/memory-functions.md#atomic_store_explicit)||
|[const_pointer_cast](../standard-library/memory-functions.md#const_pointer_cast)|Const cast na `shared_ptr`.|
|[declare_no_pointers](../standard-library/memory-functions.md#declare_no_pointers)|Informuje uvolňování paměti, že znaky počínaje zadanou adresu spadající do určené velikosti bloku neobsahují sledovatelné ukazatele.|
|[declare_reachable](../standard-library/memory-functions.md#declare_reachable)|Informuje uvolňování paměti, že je uvedena adresa pro přidělení úložištěm a je k dispozici.|
|[default_delete](../standard-library/memory-functions.md#default_delete)|Odstraní objektů přidělených s `operator new`. Vhodný pro použití s `unique_ptr`.|
|[destroy_at](../standard-library/memory-functions.md#destroy_at)|Zkrácený tvar vlastností `destroy` metody.|
|[zrušení](../standard-library/memory-functions.md#destroy)|Zkrácený tvar vlastností `destroy` metody.|
|[destroy_n](../standard-library/memory-functions.md#destroy_n)|Zkrácený tvar vlastností `destroy` metody.|
|[dynamic_pointer_cast](../standard-library/memory-functions.md#dynamic_pointer_cast)|Dynamic cast na `shared_ptr`.|
|[get_deleter](../standard-library/memory-functions.md#get_deleter)|Získat odstraňovač z `shared_ptr`.|
|[get_pointer_safety](../standard-library/memory-functions.md#get_pointer_safety)|Vrátí typ zabezpečení ukazatele uvedený v rámci uvolňování paměti.|
|[get_temporary_buffer](../standard-library/memory-functions.md#get_temporary_buffer)|Přidělí dočasné úložiště pro řadu prvků, která není větší než zadaný počet prvků.|
|[make_shared](../standard-library/memory-functions.md#make_shared)|Vytvoří a vrátí `shared_ptr` odkazující na přiřazený objekt vytvořený z nuly nebo více argumentů pomocí výchozího přidělujícího modulu.|
|[make_unique](../standard-library/memory-functions.md#make_unique)|Vytvoří a vrátí [unique_ptr](../standard-library/unique-ptr-class.md) odkazující na přiřazený objekt vytvořený z nuly nebo více argumentů.|
|[pointer_safety](../standard-library/memory-enums.md#pointer_safety)|Výčet všech možných vrácených hodnot pro `get_pointer_safety`.|
|[return_temporary_buffer](../standard-library/memory-functions.md#return_temporary_buffer)|Zruší přidělení dočasné paměti, která byla přidělena pomocí `get_temporary_buffer` šablony funkce.|
|[static_pointer_cast](../standard-library/memory-functions.md#static_pointer_cast)|Statický zápis to `shared_ptr`.|
|[swap](../standard-library/memory-functions.md#swap)|Zaměňte dva `shared_ptr` nebo `weak_ptr` objekty.|
|[undeclare_no_pointers](../standard-library/memory-functions.md#undeclare_no_pointers)|Informuje uvolňování paměti, že některé znaky v bloku paměti definované ukazatelem základní adresy a velikostí bloku mohou nyní obsahovat sledovatelné ukazatele.|
|[undeclare_reachable](../standard-library/memory-functions.md#undeclare_reachable)|Informuje `garbage_collector` , že zadané umístění v paměti není dostupný.|
|[uninitialized_copy](../standard-library/memory-functions.md#uninitialized_copy)|Zkopíruje objekty ze zadaného rozsahu vstupu do neinicializované cílové oblasti.|
|[uninitialized_copy_n](../standard-library/memory-functions.md#uninitialized_copy_n)|Vytvoří kopii zadaného počtu prvků ze vstupního iterátoru. Kopie jsou umístěny v dopředném iterátoru.|
|[uninitialized_default_construct](../standard-library/memory-functions.md#uninitialized_default_construct)|Zkrácený tvar vlastností `uninitialized_default_construct` metody.|
|[uninitialized_default_construct_n](../standard-library/memory-functions.md#uninitialized_default_construct_n)|Zkrácený tvar vlastností `uninitialized_construct` metody.|
|[uninitialized_fill](../standard-library/memory-functions.md#uninitialized_fill)|Zkopíruje objekty ze zadané hodnoty do neinicializované cílové oblasti.|
|[uninitialized_fill_n](../standard-library/memory-functions.md#uninitialized_fill_n)|Zkopíruje objekty zadané hodnoty do zadaného počtu neinicializované cílové oblasti.|
|[uninitialized_move](../standard-library/memory-functions.md#uninitialized_move)|Zkrácený tvar vlastností `uninitialized_move` metody.|
|[uninitialized_move_n](../standard-library/memory-functions.md#uninitialized_move_n)|Zkrácený tvar vlastností `uninitialized_move` metody.|
|[uninitialized_value_construct](../standard-library/memory-functions.md#uninitialized_value_construct)|Zkrácený tvar vlastností `uninitialized_value_construct` metody.|
|[uninitialized_value_construct_n](../standard-library/memory-functions.md#uninitialized_value_construct_n)|Zkrácený tvar vlastností `uninitialized_value_construct` metody.|
|[uses_allocator_v](../standard-library/memory-functions.md#uses_allocator_v)||

### <a name="operators"></a>Operátory

|||
|-|-|
|[operator!=](../standard-library/memory-operators.md#op_neq)|Testy pro nerovnost mezi objekty přidělování z dané třídy.|
|[operator==](../standard-library/memory-operators.md#op_eq_eq)|Testy pro rovnost mezi objekty přidělování z dané třídy.|
|[operator>=](../standard-library/memory-operators.md#op_gt_eq)|Testy pro jeden objekt přidělování, který je větší nebo roven druhému objektu přidělování z dané třídy.|
|[Operator <](../standard-library/memory-operators.md#op_lt)|Testy pro jeden objekt, který je menší, než druhý objekt z dané třídy.|
|[– Operátor\<=](../standard-library/memory-operators.md#op_gt_eq)|Testy pro jeden objekt, který je menší nebo roven druhému objektu z dané třídy.|
|[Operator >](../standard-library/memory-operators.md#op_gt)|Testy pro jeden objekt, který je větší, než druhý objekt z dané třídy.|
|[operátor <<](../standard-library/memory-operators.md#op_lt_lt)|`shared_ptr` Vkládací modul.|

### <a name="classes"></a>Třídy

|||
|-|-|
|[allocator](../standard-library/allocator-class.md)|Třída šablony popisuje objekt, který spravuje rozdělení úložiště a uvolnění pro pole objektů typu **typ**.|
|[allocator_traits –](../standard-library/allocator-traits-class.md)|Popisuje objekt, který určuje všechny informace požadované kontejnerem s povoleným přidělováním.|
|[auto_ptr](../standard-library/auto-ptr-class.md)|Třída šablony popisuje objekt, který uchovává ukazatel na přidělený objekt typu **typ** <strong>\*</strong> , který zajišťuje, že objekt, na který odkazuje, se odstraní při jeho nadřazeného auto_ptr zničení.|
|[bad_weak_ptr](../standard-library/bad-weak-ptr-class.md)|Nahlásí chybnou výjimku weak_ptr.|
|[enabled_shared_from_this](../standard-library/enable-shared-from-this-class.md)|Pomáhá generovat `shared_ptr`.|
|[pointer_traits](../standard-library/pointer-traits-struct.md)|Poskytuje informace, které je potřeba pro objekt třídy šablony `allocator_traits` k popisu přidělování s ukazatelem typu `Ptr`.|
|[raw_storage_iterator](../standard-library/raw-storage-iterator-class.md)|Třída adaptéru, která je k dispozici pro povolení algoritmů pro ukládání výsledků do neinicializované paměti.|
|[shared_ptr](../standard-library/shared-ptr-class.md)|Zabalí inteligentní ukazatel počítaný odkazy do dynamicky alokovaného objektu.|
|[unique_ptr](../standard-library/unique-ptr-class.md)|Uchovává ukazatel na vlastní objekt. Ukazatel je ve vlastnictví žádné jiné `unique_ptr`. `unique_ptr` Je zničen při zničení vlastníka.|
|[weak_ptr](../standard-library/weak-ptr-class.md)|Zalomí slabě propojený ukazatel.|

### <a name="structures"></a>Struktury

|||
|-|-|
|[allocator_arg_t](../standard-library/allocator-class.md#allocator_arg_t)||
|[default_delete](../standard-library/default-delete-struct.md)||
|[Hodnota hash]()||
|[owner_less](../standard-library/memory-functions.md#owner_less)|Umožňuje smíšené porovnání sdílených a slabých ukazatelů na základě vlastnictví.|
|[uses_allocator –](../standard-library/allocator-class.md#uses_allocator)||

### <a name="specializations"></a>Specializace

|||
|-|-|
|[Allocator\<void >](../standard-library/allocator-void-class.md)|Specializace alokátoru třídy šablony pro typování void, definující pouze typy členů, které dávají smysl v tomto specializovaném kontextu.|

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
