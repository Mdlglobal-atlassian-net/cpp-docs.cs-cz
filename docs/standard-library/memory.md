---
title: "&lt;paměť&gt; | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- memory/std::<memory>
- <memory>
- std::<memory>
dev_langs: C++
helpviewer_keywords: memory header
ms.assetid: ef8e38da-7c9d-4037-9ad1-20c99febf5dc
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 21948def2d4c67f14b5342b213754b3b669731d9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltmemorygt"></a>&lt;paměť&gt;
Definuje třídu, operátor a několik šablon, které pomáhají přidělit a uvolnit objekty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <memory>  
  
```  
  
## <a name="members"></a>Členové  
  
### <a name="functions"></a>Funkce  
  
|||  
|-|-|  
|[AddressOf](../standard-library/memory-functions.md#addressof)|Získá adresu true objektu.|  
|[Zarovnat](../standard-library/memory-functions.md#align)|Vrací ukazatel na rozsah dané velikosti na základě zadaného zarovnání a počáteční adresy.|  
|[allocate_shared](../standard-library/memory-functions.md#allocate_shared)|Vytvoří `shared_ptr` na objekty, které jsou přidělené a zkonstruovat pro daný typ s zadaný přidělení.|  
|[const_pointer_cast](../standard-library/memory-functions.md#const_pointer_cast)|Const přetypování na `shared_ptr`.|  
|[declare_no_pointers](../standard-library/memory-functions.md#declare_no_pointers)|Informuje uvolňování paměti, že znaky počínaje zadanou adresu spadající do určené velikosti bloku neobsahují sledovatelné ukazatele.|  
|[declare_reachable](../standard-library/memory-functions.md#declare_reachable)|Informuje uvolňování paměti, že je uvedena adresa pro přidělení úložištěm a je k dispozici.|  
|[default_delete –](../standard-library/memory-functions.md#default_delete)|Odstraní objektů, kterým je přiřazen `operator new`. Vhodné pro použití s `unique_ptr`.|  
|[dynamic_pointer_cast](../standard-library/memory-functions.md#dynamic_pointer_cast)|Dynamické přetypovat `shared_ptr`.|  
|[get_deleter –](../standard-library/memory-functions.md#get_deleter)|Získat metoda odstranění z `shared_ptr`.|  
|[get_pointer_safety](../standard-library/memory-functions.md#get_pointer_safety)|Vrátí typ zabezpečení ukazatele uvedený v rámci uvolňování paměti.|  
|[get_temporary_buffer](../standard-library/memory-functions.md#get_temporary_buffer)|Přidělí dočasné úložiště pro řadu prvků, která není větší než zadaný počet prvků.|  
|[make_shared –](../standard-library/memory-functions.md#make_shared)|Vytvoří a vrátí `shared_ptr` který odkazuje na objekt přidělené vytvářejí na základě počtu nula či více argumentů pomocí přidělujícího modulu výchozí.|  
|[make_unique](../standard-library/memory-functions.md#make_unique)|Vytvoří a vrátí [unique_ptr](../standard-library/unique-ptr-class.md) který odkazuje na objekt přidělené vytvářejí na základě počtu nula či více argumentů.|  
|[owner_less –](../standard-library/memory-functions.md#owner_less)|Umožňuje smíšené porovnání sdílených a slabých ukazatelů na základě vlastnictví.|  
|[pointer_safety –](../standard-library/memory-enums.md#pointer_safety)|Výčet všech možných návratové hodnoty pro `get_pointer_safety`.|  
|[return_temporary_buffer](../standard-library/memory-functions.md#return_temporary_buffer)|Zruší přidělení dočasné paměti, který byl přidělen s použitím `get_temporary_buffer` funkce šablony.|  
|[static_pointer_cast](../standard-library/memory-functions.md#static_pointer_cast)|Statické přetypovat `shared_ptr`.|  
|[swap](../standard-library/memory-functions.md#swap)|Swap dva `shared_ptr` nebo `weak_ptr` objekty.|  
|[undeclare_no_pointers](../standard-library/memory-functions.md#undeclare_no_pointers)|Informuje uvolňování paměti, že některé znaky v bloku paměti definované ukazatelem základní adresy a velikostí bloku mohou nyní obsahovat sledovatelné ukazatele.|  
|[undeclare_reachable](../standard-library/memory-functions.md#undeclare_reachable)|Informuje o tom `garbage_collector` , umístění zadaná paměťová není dostupný.|  
|[uninitialized_copy](../standard-library/memory-functions.md#uninitialized_copy)|Zkopíruje objekty ze zadaného rozsahu vstupu do neinicializované cílové oblasti.|  
|[uninitialized_copy_n](../standard-library/memory-functions.md#uninitialized_copy_n)|Vytvoří kopii zadaného počtu prvků ze vstupního iterátoru. Kopie jsou umístěny v dopředném iterátoru.|  
|[uninitialized_fill](../standard-library/memory-functions.md#uninitialized_fill)|Zkopíruje objekty ze zadané hodnoty do neinicializované cílové oblasti.|  
|[uninitialized_fill_n](../standard-library/memory-functions.md#uninitialized_fill_n)|Zkopíruje objekty zadané hodnoty do zadaného počtu neinicializované cílové oblasti.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[Operator! =](../standard-library/memory-operators.md#op_neq)|Testy pro nerovnost mezi objekty přidělování z dané třídy.|  
|[Operator ==](../standard-library/memory-operators.md#op_eq_eq)|Testy pro rovnost mezi objekty přidělování z dané třídy.|  
|[Operator > =](../standard-library/memory-operators.md#op_gt_eq)|Testy pro jeden objekt přidělování, který je větší nebo roven druhému objektu přidělování z dané třídy.|  
|[operátor <](../standard-library/memory-operators.md#op_lt)|Testy pro jeden objekt, který je menší, než druhý objekt z dané třídy.|  
|[operátor\<=](../standard-library/memory-operators.md#op_gt_eq)|Testy pro jeden objekt, který je menší nebo roven druhému objektu z dané třídy.|  
|[operátor >](../standard-library/memory-operators.md#op_gt)|Testy pro jeden objekt, který je větší, než druhý objekt z dané třídy.|  
|[operátor <<](../standard-library/memory-operators.md#op_lt_lt)|`shared_ptr`Vkládací modul.|  
  
### <a name="classes"></a>Třídy  
  
|||  
|-|-|  
|[Allocator](../standard-library/allocator-class.md)|Šablony třídy popisuje objekt, který spravuje přidělení úložiště a uvolnění pro pole objektů typu **typu**.|  
|[allocator_traits](../standard-library/allocator-traits-class.md)|Popisuje objekt, který určuje všechny informace požadované kontejnerem s povoleným přidělováním.|  
|[auto_ptr](../standard-library/auto-ptr-class.md)|Šablony třídy popisuje objekt, který ukládá ukazatel na objekt přidělené typu **typ \***  zajistí se tak objektu, na která se získá body odstranit při jeho nadřazených auto_ptr získá zničena.|  
|[bad_weak_ptr](../standard-library/bad-weak-ptr-class.md)|Nahlásí chybnou výjimku weak_ptr.|  
|[enabled_shared_from_this](../standard-library/enable-shared-from-this-class.md)|Pomáhá generovat `shared_ptr`.|  
|[pointer_traits](../standard-library/pointer-traits-struct.md)|Poskytuje informace, které je potřeba v objektu třídy šablony `allocator_traits` k popisu allocator s ukazatel typu `Ptr`.|  
|[raw_storage_iterator –](../standard-library/raw-storage-iterator-class.md)|Třída adaptéru, která je k dispozici pro povolení algoritmů pro ukládání výsledků do neinicializované paměti.|  
|[shared_ptr](../standard-library/shared-ptr-class.md)|Zabalí inteligentní ukazatel počítaný odkazy do dynamicky alokovaného objektu.|  
|[unique_ptr](../standard-library/unique-ptr-class.md)|Uchovává ukazatel na vlastní objekt. Vlastní ukazatele žádná jiná `unique_ptr`. `unique_ptr` Zničena když vlastník zničena.|  
|[weak_ptr](../standard-library/weak-ptr-class.md)|Zalomí slabě propojený ukazatel.|  
  
### <a name="specializations"></a>Specializace  
  
|||  
|-|-|  
|[Allocator\<void >](../standard-library/allocator-void-class.md)|Specializace alokátoru třídy šablony pro typování void, definující pouze typy členů, které dávají smysl v tomto specializovaném kontextu.|  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



