---
title: '&lt;Paměť&gt;'
ms.date: 11/04/2016
f1_keywords:
- memory/std::<memory>
- <memory>
- std::<memory>
helpviewer_keywords:
- memory header
ms.assetid: ef8e38da-7c9d-4037-9ad1-20c99febf5dc
ms.openlocfilehash: c63421995fdabc94a7e6495df8d9937049dbba9d
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51521932"
---
# <a name="ltmemorygt"></a>&lt;Paměť&gt;

Definuje třídu, operátor a několik šablon, které pomáhají přidělit a uvolnit objekty.

## <a name="syntax"></a>Syntaxe

```cpp
#include <memory>
```

## <a name="members"></a>Členové

### <a name="functions"></a>Funkce

|Funkce|Popis|
|-|-|
|[addressof](../standard-library/memory-functions.md#addressof)|Získá adresu true objektu.|
|[align](../standard-library/memory-functions.md#align)|Vrací ukazatel na rozsah dané velikosti na základě zadaného zarovnání a počáteční adresy.|
|[allocate_shared](../standard-library/memory-functions.md#allocate_shared)|Vytvoří `shared_ptr` na objekty, které jsou přiděleny a konstruovány s alokátorem určeným pro daného typu.|
|[const_pointer_cast](../standard-library/memory-functions.md#const_pointer_cast)|Const cast na `shared_ptr`.|
|[declare_no_pointers](../standard-library/memory-functions.md#declare_no_pointers)|Informuje uvolňování paměti, že znaky počínaje zadanou adresu spadající do určené velikosti bloku neobsahují sledovatelné ukazatele.|
|[declare_reachable](../standard-library/memory-functions.md#declare_reachable)|Informuje uvolňování paměti, že je uvedena adresa pro přidělení úložištěm a je k dispozici.|
|[default_delete](../standard-library/memory-functions.md#default_delete)|Odstraní objektů přidělených s `operator new`. Vhodný pro použití s `unique_ptr`.|
|[dynamic_pointer_cast](../standard-library/memory-functions.md#dynamic_pointer_cast)|Dynamic cast na `shared_ptr`.|
|[get_deleter](../standard-library/memory-functions.md#get_deleter)|Získat odstraňovač z `shared_ptr`.|
|[get_pointer_safety](../standard-library/memory-functions.md#get_pointer_safety)|Vrátí typ zabezpečení ukazatele uvedený v rámci uvolňování paměti.|
|[get_temporary_buffer](../standard-library/memory-functions.md#get_temporary_buffer)|Přidělí dočasné úložiště pro řadu prvků, která není větší než zadaný počet prvků.|
|[make_shared](../standard-library/memory-functions.md#make_shared)|Vytvoří a vrátí `shared_ptr` odkazující na přiřazený objekt vytvořený z nuly nebo více argumentů pomocí výchozího přidělujícího modulu.|
|[make_unique](../standard-library/memory-functions.md#make_unique)|Vytvoří a vrátí [unique_ptr](../standard-library/unique-ptr-class.md) odkazující na přiřazený objekt vytvořený z nuly nebo více argumentů.|
|[owner_less](../standard-library/memory-functions.md#owner_less)|Umožňuje smíšené porovnání sdílených a slabých ukazatelů na základě vlastnictví.|
|[pointer_safety](../standard-library/memory-enums.md#pointer_safety)|Výčet všech možných vrácených hodnot pro `get_pointer_safety`.|
|[return_temporary_buffer](../standard-library/memory-functions.md#return_temporary_buffer)|Zruší přidělení dočasné paměti, která byla přidělena pomocí `get_temporary_buffer` šablony funkce.|
|[static_pointer_cast](../standard-library/memory-functions.md#static_pointer_cast)|Statický zápis to `shared_ptr`.|
|[Prohození](../standard-library/memory-functions.md#swap)|Zaměňte dva `shared_ptr` nebo `weak_ptr` objekty.|
|[undeclare_no_pointers](../standard-library/memory-functions.md#undeclare_no_pointers)|Informuje uvolňování paměti, že některé znaky v bloku paměti definované ukazatelem základní adresy a velikostí bloku mohou nyní obsahovat sledovatelné ukazatele.|
|[undeclare_reachable](../standard-library/memory-functions.md#undeclare_reachable)|Informuje `garbage_collector` , že zadané umístění v paměti není dostupný.|
|[uninitialized_copy](../standard-library/memory-functions.md#uninitialized_copy)|Zkopíruje objekty ze zadaného rozsahu vstupu do neinicializované cílové oblasti.|
|[uninitialized_copy_n](../standard-library/memory-functions.md#uninitialized_copy_n)|Vytvoří kopii zadaného počtu prvků ze vstupního iterátoru. Kopie jsou umístěny v dopředném iterátoru.|
|[uninitialized_fill](../standard-library/memory-functions.md#uninitialized_fill)|Zkopíruje objekty ze zadané hodnoty do neinicializované cílové oblasti.|
|[uninitialized_fill_n](../standard-library/memory-functions.md#uninitialized_fill_n)|Zkopíruje objekty zadané hodnoty do zadaného počtu neinicializované cílové oblasti.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator!=](../standard-library/memory-operators.md#op_neq)|Testy pro nerovnost mezi objekty přidělování z dané třídy.|
|[operator==](../standard-library/memory-operators.md#op_eq_eq)|Testy pro rovnost mezi objekty přidělování z dané třídy.|
|[operator>=](../standard-library/memory-operators.md#op_gt_eq)|Testy pro jeden objekt přidělování, který je větší nebo roven druhému objektu přidělování z dané třídy.|
|[Operator <](../standard-library/memory-operators.md#op_lt)|Testy pro jeden objekt, který je menší, než druhý objekt z dané třídy.|
|[– Operátor\<=](../standard-library/memory-operators.md#op_gt_eq)|Testy pro jeden objekt, který je menší nebo roven druhému objektu z dané třídy.|
|[Operator >](../standard-library/memory-operators.md#op_gt)|Testy pro jeden objekt, který je větší, než druhý objekt z dané třídy.|
|[operátor <<](../standard-library/memory-operators.md#op_lt_lt)|`shared_ptr` Vkládací modul.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[Allocator –](../standard-library/allocator-class.md)|Třída šablony popisuje objekt, který spravuje rozdělení úložiště a uvolnění pro pole objektů typu **typ**.|
|[allocator_traits –](../standard-library/allocator-traits-class.md)|Popisuje objekt, který určuje všechny informace požadované kontejnerem s povoleným přidělováním.|
|[auto_ptr](../standard-library/auto-ptr-class.md)|Třída šablony popisuje objekt, který uchovává ukazatel na přidělený objekt typu **typ** <strong>\*</strong> , který zajišťuje, že objekt, na který odkazuje, se odstraní při jeho nadřazeného auto_ptr zničení.|
|[bad_weak_ptr](../standard-library/bad-weak-ptr-class.md)|Nahlásí chybnou výjimku weak_ptr.|
|[enabled_shared_from_this](../standard-library/enable-shared-from-this-class.md)|Pomáhá generovat `shared_ptr`.|
|[pointer_traits](../standard-library/pointer-traits-struct.md)|Poskytuje informace, které je potřeba pro objekt třídy šablony `allocator_traits` k popisu přidělování s ukazatelem typu `Ptr`.|
|[raw_storage_iterator](../standard-library/raw-storage-iterator-class.md)|Třída adaptéru, která je k dispozici pro povolení algoritmů pro ukládání výsledků do neinicializované paměti.|
|[shared_ptr](../standard-library/shared-ptr-class.md)|Zabalí inteligentní ukazatel počítaný odkazy do dynamicky alokovaného objektu.|
|[unique_ptr](../standard-library/unique-ptr-class.md)|Uchovává ukazatel na vlastní objekt. Ukazatel je ve vlastnictví žádné jiné `unique_ptr`. `unique_ptr` Je zničen při zničení vlastníka.|
|[weak_ptr](../standard-library/weak-ptr-class.md)|Zalomí slabě propojený ukazatel.|

### <a name="specializations"></a>Specializace

|||
|-|-|
|[Allocator\<void >](../standard-library/allocator-void-class.md)|Specializace alokátoru třídy šablony pro typování void, definující pouze typy členů, které dávají smysl v tomto specializovaném kontextu.|

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
