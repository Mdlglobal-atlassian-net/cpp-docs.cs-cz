---
title: Atributy typedef, Enum, Union a struct (C++ com)
ms.date: 10/02/2018
helpviewer_keywords:
- union attributes
- attributes [C++/CLI], reference topics
ms.assetid: f8a4fe94-dc02-4aed-bc31-3e500d42f4c7
ms.openlocfilehash: fdc380cdc207361a145862f87d809a4bcea01c27
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214471"
---
# <a name="typedef-enum-union-and-struct-attributes"></a>Atributy klíčových slov typedef, enum, union a struct

Následující atributy se vztahují na klíčová slova [typedef](../../cpp/aliases-and-typedefs-cpp.md), [struct](../../cpp/struct-cpp.md)a [Enum](../../cpp/enumerations-cpp.md) C++ .

### <a name="typedef"></a>– definice typedef

|Atribut|Popis|
|---------------|-----------------|
|[case](case-cpp.md)|Používá se s atributem [switch_type](switch-type.md) ve **sjednocení**.|
|[custom](custom-cpp.md)|Umožňuje definovat vlastní atribut.|
|[export](export.md)|Způsobí, že datová struktura bude umístěna v souboru. idl.|
|[first_is](first-is.md)|Určuje index prvního prvku pole, který se má přenést.|
|[helpcontext](helpcontext.md)|Určuje ID kontextu, které uživateli umožňuje zobrazit informace o tomto prvku v souboru Help.|
|[helpfile](helpfile.md)|Nastaví název souboru s nápovědu pro knihovnu typů.|
|[helpstring](helpstring.md)|Určuje řetězec znaků, který se používá k popisu prvku, na který se vztahuje.|
|[library_block](library-block.md)|Umístí konstrukci do bloku knihovny souboru. idl.|
|[ptr](ptr.md)|Určí ukazatel jako úplný ukazatel.|
|[public](public-cpp-attributes.md)|Zajistí, že definice typedef přejde do knihovny typů i v případě, že není odkazována ze souboru. idl.|
|[ref](ref-cpp.md)|Identifikuje ukazatel odkazu.|
|[switch_is](switch-is.md)|Určuje výraz nebo identifikátor fungující jako Discriminant sjednocení, který vybírá člena sjednocení.|
|[switch_type](switch-type.md)|Určuje typ proměnné používané jako Discriminant sjednocení.|
|[unique](unique-cpp.md)|Určuje jedinečný ukazatel.|
|[wire_marshal](wire-marshal.md)|Určuje datový typ, který se použije pro přenos místo datového typu specifického pro aplikaci.|

### <a name="enum"></a>Výčet

|Atribut|Popis|
|---------------|-----------------|
|[custom](custom-cpp.md)|Umožňuje definovat vlastní atribut.|
|[export](export.md)|Způsobí, že datová struktura bude umístěna v souboru. idl.|
|[uuid](uuid-cpp-attributes.md)|Určuje jedinečné ID pro třídu nebo rozhraní.|
|[v1_enum](v1-enum.md)|Směruje, že zadaný typ výčtu se přenáší jako 32á entita, nikoli jako 16bitové výchozí hodnoty.|

### <a name="union"></a>sjednocení

|Atribut|Popis|
|---------------|-----------------|
|[custom](custom-cpp.md)|Umožňuje definovat vlastní atribut.|
|[export](export.md)|Způsobí, že datová struktura bude umístěna v souboru. idl.|
|[first_is](first-is.md)|Určuje index prvního prvku pole, který se má přenést.|
|[last_is](last-is.md)|Určuje index posledního elementu pole, který se má přenést.|
|[length_is](length-is.md)|Určuje počet prvků pole, které mají být přeneseny.|
|[max_is](max-is.md)|Určuje maximální hodnotu pro platný index pole.|
|[size_is](size-is.md)|Určuje velikost paměti přidělené pro bodová ukazatele, velikost ukazatelů na velikost ukazatelů a jedno nebo multidimenzionální pole.|
|[unique](unique-cpp.md)|Určuje jedinečný ukazatel.|
|[uuid](uuid-cpp-attributes.md)|Určuje jedinečné ID pro třídu nebo rozhraní.|

### <a name="nonencapsulated-union"></a>Nezapouzdřené sjednocení

|Atribut|Popis|
|---------------|-----------------|
|[ms_union](ms-union.md)|Řídí zarovnání reprezentace dat v síti pro nezapouzdřené sjednocení.|
|[no_injected_text](no-injected-text.md)|Zabraňuje kompilátoru v vkládání kódu v důsledku použití atributu.|

### <a name="struct"></a>– Struktura

|Atribut|Popis|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Označuje, že třída podporuje agregaci.|
|[aggregates](aggregates.md)|Indikuje, že ovládací prvek agreguje cílovou třídu.|
|[appobject](appobject.md)|Identifikuje třídu typu coclass jako objekt aplikace, který je přidružen k úplné aplikaci. exe, a označuje, že funkce a vlastnosti třídy coclass jsou v této knihovně typů globálně k dispozici.|
|[coclass](coclass.md)|Vytvoří ovládací prvek ActiveX.|
|[com_interface_entry](com-interface-entry-cpp.md)|Přidá položku rozhraní do mapy modelu COM.|
|[control](control.md)|Určuje, že uživatelsky definovaný typ je ovládací prvek.|
|[custom](custom-cpp.md)|Umožňuje definovat vlastní atribut.|
|[db_column](db-column.md)|Váže zadaný sloupec na sadu řádků.|
|[db_command](db-command.md)|Vytvoří příkaz OLE DB.|
|[db_param](db-param.md)|Přidruží zadanou členskou proměnnou ke vstupnímu nebo výstupnímu parametru a naomezuje proměnnou.|
|[db_source](db-source.md)|Vytvoří připojení ke zdroji dat.|
|[db_table](db-table.md)|Otevře tabulku OLE DB.|
|[default](default-cpp.md)|Indikuje, že vlastní nebo odesílající pole definované v rámci třídy typu coclass představuje výchozí rozhraní programovatelnosti.|
|[defaultvtable](defaultvtable.md)|Definuje rozhraní jako výchozí rozhraní vtable pro ovládací prvek.|
|[event_receiver](event-receiver.md)|Vytvoří přijímač událostí.|
|[event_source](event-source.md)|Vytvoří zdroj události.|
|[export](export.md)|Způsobí, že datová struktura bude umístěna v souboru. idl.|
|[first_is](first-is.md)|Určuje index prvního prvku pole, který se má přenést.|
|[hidden](hidden.md)|Označuje, že položka existuje, ale neměla by se zobrazovat v prohlížeči orientovaném na uživatele.|
|[implements_category](implements-category.md)|Určuje implementované kategorie komponent pro třídu.|
|[last_is](last-is.md)|Určuje index posledního elementu pole, který se má přenést.|
|[length_is](length-is.md)|Určuje počet prvků pole, které mají být přeneseny.|
|[max_is](max-is.md)|Určuje maximální hodnotu pro platný index pole.|
|[requires_category](requires-category.md)|Určuje požadované kategorie součásti cílové třídy.|
|[size_is](size-is.md)|Určuje velikost paměti přidělené pro bodová ukazatele, velikost ukazatelů na velikost ukazatelů a jedno nebo multidimenzionální pole.|
|[source](source-cpp.md)|U třídy určuje zdrojové rozhraní objektu COM pro body připojení. U vlastnosti nebo metody označuje, že člen vrací objekt nebo VARIANTu, který je zdrojem událostí.|
|[threading](threading-cpp.md)|Určuje model dělení na vlákna pro objekt modelu COM.|
|[unique](unique-cpp.md)|Určuje jedinečný ukazatel.|
|[uuid](uuid-cpp-attributes.md)|Určuje jedinečné ID pro třídu nebo rozhraní.|
|[version](version-cpp.md)|Identifikuje konkrétní verzi z více verzí třídy.|
|[vi_progid](vi-progid.md)|Určuje formu ProgID nezávislou na verzi.|

## <a name="see-also"></a>Viz také

[Atributy podle použití](attributes-by-usage.md)
