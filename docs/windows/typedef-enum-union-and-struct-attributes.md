---
title: – TypeDef, Enum, Union a struct – atributy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- union attributes
- attributes [C++], reference topics
- struct attributes
- typedef attributes
- enum attributes
ms.assetid: f8a4fe94-dc02-4aed-bc31-3e500d42f4c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3c8cca379b9b9ba6498908469761acefce189117
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43686985"
---
# <a name="typedef-enum-union-and-struct-attributes"></a>Atributy klíčových slov typedef, enum, union a struct

Následující atributy se vztahují na [typedef](../cpp/aliases-and-typedefs-cpp.md), [struktura](../cpp/struct-cpp.md), a [výčtu](../cpp/enumerations-cpp.md) klíčová slova jazyka C++.

### <a name="typedef"></a>– definice typedef

|Atribut|Popis|
|---------------|-----------------|
|[případ](../windows/case-cpp.md)|Použít s [switch_type –](../windows/switch-type.md) atribut **sjednocení**.|
|[Vlastní](../windows/custom-cpp.md)|Umožňuje definovat vlastní atribut.|
|[export](../windows/export.md)|Způsobí, že datová struktura budou umístěny v souboru IDL.|
|[first_is](../windows/first-is.md)|Určuje index první prvek pole předávají.|
|[helpcontext](../windows/helpcontext.md)|Určuje ID kontextu, který umožňuje uživateli zobrazit informace o tomto prvku v souboru nápovědy.|
|[helpfile](../windows/helpfile.md)|Nastaví název souboru nápovědy pro knihovnu typů.|
|[helpstring](../windows/helpstring.md)|Určuje řetězec znaků, který se používá k popisu elementu, ke kterému se vztahuje.|
|[library_block](../windows/library-block.md)|Umístí konstrukci uvnitř bloku knihovny souboru IDL.|
|[ptr](../windows/ptr.md)|Ukazatel se označí jako úplné ukazatel.|
|[public](../windows/public-cpp-attributes.md)|Zajišťuje, že definice typu přejde do knihovny typů, i když to neodkazuje v souboru IDL.|
|[ref](../windows/ref-cpp.md)|Určuje referenční ukazatel.|
|[switch_is](../windows/switch-is.md)|Určuje výraz nebo identifikátor, který funguje jako sjednocení discriminant, který vybere člen sjednocení.|
|[switch_type](../windows/switch-type.md)|Určuje typ proměnné použité jako sjednocení discriminant.|
|[Jedinečný](../windows/unique-cpp.md)|Určuje jedinečný ukazatel.|
|[wire_marshal](../windows/wire-marshal.md)|Určuje datový typ, který se použije pro přenos místo typu dat pro konkrétní aplikace.|

### <a name="enum"></a>enum

|Atribut|Popis|
|---------------|-----------------|
|[Vlastní](../windows/custom-cpp.md)|Umožňuje definovat vlastní atribut.|
|[export](../windows/export.md)|Způsobí, že datová struktura budou umístěny v souboru IDL.|
|[uuid](../windows/uuid-cpp-attributes.md)|Určuje jedinečné ID pro třídu nebo rozhraní.|
|[v1_enum](../windows/v1-enum.md)|Určí, že zadaný výčtového typu předávají jako 32-bit entity, spíše než výchozí 16 bitů.|

### <a name="union"></a>sjednocení

|Atribut|Popis|
|---------------|-----------------|
|[Vlastní](../windows/custom-cpp.md)|Umožňuje definovat vlastní atribut.|
|[export](../windows/export.md)|Způsobí, že datová struktura budou umístěny v souboru IDL.|
|[first_is](../windows/first-is.md)|Určuje index první prvek pole předávají.|
|[last_is](../windows/last-is.md)|Určuje index posledního prvku pole předávají.|
|[length_is](../windows/length-is.md)|Určuje počet elementů pole předávají.|
|[max_is](../windows/max-is.md)|Určuje maximální hodnotu pro pole platný index.|
|[size_is](../windows/size-is.md)|Určuje velikost paměti přidělené pro velikosti ukazatele, velikosti ukazatele na velikosti ukazatele a single - nebo vícedimenzionální pole.|
|[Jedinečný](../windows/unique-cpp.md)|Určuje jedinečný ukazatel.|
|[uuid](../windows/uuid-cpp-attributes.md)|Určuje jedinečné ID pro třídu nebo rozhraní.|

### <a name="nonencapsulated-union"></a>Nonencapsulated sjednocení

|Atribut|Popis|
|---------------|-----------------|
|[ms_union](../windows/ms-union.md)|Určuje zarovnání reprezentace dat sítě nonencapsulated sjednocení.|
|[no_injected_text](../windows/no-injected-text.md)|Zabrání kompilátoru vkládání kódu v důsledku použití atributu.|

### <a name="struct"></a>struct 

|Atribut|Popis|
|---------------|-----------------|
|[aggregatable](../windows/aggregatable.md)|Označuje, že třída podporuje agregaci.|
|[aggregates](../windows/aggregates.md)|Označuje, že ovládací prvek agreguje cílové třídy.|
|[appobject](../windows/appobject.md)|Identifikuje coclass jako objekt aplikace, který je přidružen k aplikaci úplné .exe a označuje, že funkce a vlastnosti třídy typu coclass jsou globálně k dispozici v této knihovně typů.|
|[coclass](../windows/coclass.md)|Vytvoří ovládací prvek ActiveX.|
|[COM_INTERFACE_ENTRY](../windows/com-interface-entry-cpp.md)|Přidá položku do rozhraní COM mapy.|
|[control](../windows/control.md)|Určuje, jestli je typ uživatelského ovládacího prvku.|
|[Vlastní](../windows/custom-cpp.md)|Umožňuje definovat vlastní atribut.|
|[db_column](../windows/db-column.md)|Zadaný sloupec se váže k dané sadě řádků.|
|[db_command](../windows/db-command.md)|Vytvoří příkaz OLE DB.|
|[db_param](../windows/db-param.md)|Přidruží zadaný členskou proměnnou vstupní nebo výstupní parametr a odděluje citaci proměnné.|
|[db_source](../windows/db-source.md)|Vytvoří připojení ke zdroji dat.|
|[db_table](../windows/db-table.md)|Otevře se tabulku OLE DB.|
|[default](../windows/default-cpp.md)|Označuje, že vlastní nebo dispinterface definované v rámci coclass představuje výchozí programovatelnosti rozhraní.|
|[defaultvtable](../windows/defaultvtable.md)|Definuje rozhraní jako výchozího rozhraní vtable pro ovládací prvek.|
|[event_receiver](../windows/event-receiver.md)|Vytvoří přijímače událostí.|
|[event_source](../windows/event-source.md)|Vytvoří zdroj událostí.|
|[export](../windows/export.md)|Způsobí, že datová struktura budou umístěny v souboru IDL.|
|[first_is](../windows/first-is.md)|Určuje index první prvek pole předávají.|
|[hidden](../windows/hidden.md)|Označuje, že položka existuje, ale nebude se zobrazovat v prohlížeči uživatele.|
|[implements_category](../windows/implements-category.md)|Určuje kategorie implementované součásti pro třídu.|
|[last_is](../windows/last-is.md)|Určuje index posledního prvku pole předávají.|
|[length_is](../windows/length-is.md)|Určuje počet elementů pole předávají.|
|[max_is](../windows/max-is.md)|Určuje maximální hodnotu pro pole platný index.|
|[requires_category](../windows/requires-category.md)|Určuje požadovanou součást kategorie cílové třídy.|
|[size_is](../windows/size-is.md)|Určuje velikost paměti přidělené pro velikosti ukazatele, velikosti ukazatele na velikosti ukazatele a single - nebo vícedimenzionální pole.|
|[Zdroj](../windows/source-cpp.md)|Třídy určuje rozhraní zdrojového objektu modelu COM pro spojovací body. Na vlastnost nebo metoda označuje, že členu vrátí objekt nebo VARIANTU, která je zdrojem událostí.|
|[Dělení na vlákna](../windows/threading-cpp.md)|Určuje model vláken pro objekt modelu COM.|
|[Jedinečný](../windows/unique-cpp.md)|Určuje jedinečný ukazatel.|
|[uuid](../windows/uuid-cpp-attributes.md)|Určuje jedinečné ID pro třídu nebo rozhraní.|
|[Verze](../windows/version-cpp.md)|Určuje konkrétní verzi napříč několika verzemi třídu.|
|[vi_progid](../windows/vi-progid.md)|Určuje verzi nezávislé formu ProgID.|

## <a name="see-also"></a>Viz také

[Atributy podle použití](../windows/attributes-by-usage.md)