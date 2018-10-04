---
title: – TypeDef, Enum, Union a struct – atributy (C++ COM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- union attributes
- attributes [C++/CLI], reference topics
ms.assetid: f8a4fe94-dc02-4aed-bc31-3e500d42f4c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 89e1511df2aeabe7cbd63549a1dca6e53944fbe2
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789392"
---
# <a name="typedef-enum-union-and-struct-attributes"></a>Atributy klíčových slov typedef, enum, union a struct

Následující atributy se vztahují na [typedef](../../cpp/aliases-and-typedefs-cpp.md), [struktura](../../cpp/struct-cpp.md), a [výčtu](../../cpp/enumerations-cpp.md) klíčová slova jazyka C++.

### <a name="typedef"></a>– definice typedef

|Atribut|Popis|
|---------------|-----------------|
|[případ](case-cpp.md)|Použít s [switch_type –](switch-type.md) atribut **sjednocení**.|
|[Vlastní](custom-cpp.md)|Umožňuje definovat vlastní atribut.|
|[export](export.md)|Způsobí, že datová struktura budou umístěny v souboru IDL.|
|[first_is](first-is.md)|Určuje index první prvek pole předávají.|
|[helpcontext](helpcontext.md)|Určuje ID kontextu, který umožňuje uživateli zobrazit informace o tomto prvku v souboru nápovědy.|
|[helpfile](helpfile.md)|Nastaví název souboru nápovědy pro knihovnu typů.|
|[helpstring](helpstring.md)|Určuje řetězec znaků, který se používá k popisu elementu, ke kterému se vztahuje.|
|[library_block](library-block.md)|Umístí konstrukci uvnitř bloku knihovny souboru IDL.|
|[ptr](ptr.md)|Ukazatel se označí jako úplné ukazatel.|
|[public](public-cpp-attributes.md)|Zajišťuje, že definice typu přejde do knihovny typů, i když to neodkazuje v souboru IDL.|
|[ref](ref-cpp.md)|Určuje referenční ukazatel.|
|[switch_is](switch-is.md)|Určuje výraz nebo identifikátor, který funguje jako sjednocení discriminant, který vybere člen sjednocení.|
|[switch_type](switch-type.md)|Určuje typ proměnné použité jako sjednocení discriminant.|
|[Jedinečný](unique-cpp.md)|Určuje jedinečný ukazatel.|
|[wire_marshal](wire-marshal.md)|Určuje datový typ, který se použije pro přenos místo typu dat pro konkrétní aplikace.|

### <a name="enum"></a>enum

|Atribut|Popis|
|---------------|-----------------|
|[Vlastní](custom-cpp.md)|Umožňuje definovat vlastní atribut.|
|[export](export.md)|Způsobí, že datová struktura budou umístěny v souboru IDL.|
|[uuid](uuid-cpp-attributes.md)|Určuje jedinečné ID pro třídu nebo rozhraní.|
|[v1_enum](v1-enum.md)|Určí, že zadaný výčtového typu předávají jako 32-bit entity, spíše než výchozí 16 bitů.|

### <a name="union"></a>sjednocení

|Atribut|Popis|
|---------------|-----------------|
|[Vlastní](custom-cpp.md)|Umožňuje definovat vlastní atribut.|
|[export](export.md)|Způsobí, že datová struktura budou umístěny v souboru IDL.|
|[first_is](first-is.md)|Určuje index první prvek pole předávají.|
|[last_is](last-is.md)|Určuje index posledního prvku pole předávají.|
|[length_is](length-is.md)|Určuje počet elementů pole předávají.|
|[max_is](max-is.md)|Určuje maximální hodnotu pro pole platný index.|
|[size_is](size-is.md)|Určuje velikost paměti přidělené pro velikosti ukazatele, velikosti ukazatele na velikosti ukazatele a single - nebo vícedimenzionální pole.|
|[Jedinečný](unique-cpp.md)|Určuje jedinečný ukazatel.|
|[uuid](uuid-cpp-attributes.md)|Určuje jedinečné ID pro třídu nebo rozhraní.|

### <a name="nonencapsulated-union"></a>Nonencapsulated sjednocení

|Atribut|Popis|
|---------------|-----------------|
|[ms_union](ms-union.md)|Určuje zarovnání reprezentace dat sítě nonencapsulated sjednocení.|
|[no_injected_text](no-injected-text.md)|Zabrání kompilátoru vkládání kódu v důsledku použití atributu.|

### <a name="struct"></a>struct 

|Atribut|Popis|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Označuje, že třída podporuje agregaci.|
|[aggregates](aggregates.md)|Označuje, že ovládací prvek agreguje cílové třídy.|
|[appobject](appobject.md)|Identifikuje coclass jako objekt aplikace, který je přidružen k aplikaci úplné .exe a označuje, že funkce a vlastnosti třídy typu coclass jsou globálně k dispozici v této knihovně typů.|
|[coclass](coclass.md)|Vytvoří ovládací prvek ActiveX.|
|[COM_INTERFACE_ENTRY](com-interface-entry-cpp.md)|Přidá položku do rozhraní COM mapy.|
|[control](control.md)|Určuje, jestli je typ uživatelského ovládacího prvku.|
|[Vlastní](custom-cpp.md)|Umožňuje definovat vlastní atribut.|
|[db_column](db-column.md)|Zadaný sloupec se váže k dané sadě řádků.|
|[db_command](db-command.md)|Vytvoří příkaz OLE DB.|
|[db_param](db-param.md)|Přidruží zadaný členskou proměnnou vstupní nebo výstupní parametr a odděluje citaci proměnné.|
|[db_source](db-source.md)|Vytvoří připojení ke zdroji dat.|
|[db_table](db-table.md)|Otevře se tabulku OLE DB.|
|[default](default-cpp.md)|Označuje, že vlastní nebo dispinterface definované v rámci coclass představuje výchozí programovatelnosti rozhraní.|
|[defaultvtable](defaultvtable.md)|Definuje rozhraní jako výchozího rozhraní vtable pro ovládací prvek.|
|[event_receiver](event-receiver.md)|Vytvoří přijímače událostí.|
|[event_source](event-source.md)|Vytvoří zdroj událostí.|
|[export](export.md)|Způsobí, že datová struktura budou umístěny v souboru IDL.|
|[first_is](first-is.md)|Určuje index první prvek pole předávají.|
|[hidden](hidden.md)|Označuje, že položka existuje, ale nebude se zobrazovat v prohlížeči uživatele.|
|[implements_category](implements-category.md)|Určuje kategorie implementované součásti pro třídu.|
|[last_is](last-is.md)|Určuje index posledního prvku pole předávají.|
|[length_is](length-is.md)|Určuje počet elementů pole předávají.|
|[max_is](max-is.md)|Určuje maximální hodnotu pro pole platný index.|
|[requires_category](requires-category.md)|Určuje požadovanou součást kategorie cílové třídy.|
|[size_is](size-is.md)|Určuje velikost paměti přidělené pro velikosti ukazatele, velikosti ukazatele na velikosti ukazatele a single - nebo vícedimenzionální pole.|
|[Zdroj](source-cpp.md)|Třídy určuje rozhraní zdrojového objektu modelu COM pro spojovací body. Na vlastnost nebo metoda označuje, že členu vrátí objekt nebo VARIANTU, která je zdrojem událostí.|
|[Dělení na vlákna](threading-cpp.md)|Určuje model vláken pro objekt modelu COM.|
|[Jedinečný](unique-cpp.md)|Určuje jedinečný ukazatel.|
|[uuid](uuid-cpp-attributes.md)|Určuje jedinečné ID pro třídu nebo rozhraní.|
|[Verze](version-cpp.md)|Určuje konkrétní verzi napříč několika verzemi třídu.|
|[vi_progid](vi-progid.md)|Určuje verzi nezávislé formu ProgID.|

## <a name="see-also"></a>Viz také

[Atributy podle použití](attributes-by-usage.md)