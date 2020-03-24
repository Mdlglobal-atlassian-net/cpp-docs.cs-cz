---
title: Atributy třídy (C++ com)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], class attributes
ms.assetid: fad04ea1-d8ff-46d4-bb42-2b4500a6ab60
ms.openlocfilehash: 5e10b7831e59211b73ce947ac21e43bc1a8af1c9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167313"
---
# <a name="class-attributes"></a>Atributy třídy

Následující atributy platí pro klíčové slovo [Class](../../cpp/class-cpp.md) C++ .

|Atribut|Popis|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Označuje, že třída podporuje agregaci.|
|[aggregates](aggregates.md)|Indikuje, že ovládací prvek agreguje cílovou třídu.|
|[appobject](appobject.md)|Identifikuje třídu typu coclass jako objekt aplikace, který je přidružen k úplné aplikaci. exe, a označuje, že funkce a vlastnosti třídy coclass jsou v této knihovně typů globálně k dispozici.|
|[case](case-cpp.md)|Používá se s atributem [switch_type](switch-type.md) ve sjednocení.|
|[coclass](coclass.md)|Vytvoří ovládací prvek ActiveX.|
|[com_interface_entry](com-interface-entry-cpp.md)|Přidá položku rozhraní do mapy modelu COM.|
|[control](control.md)|Určuje, že uživatelsky definovaný typ je ovládací prvek.|
|[custom](custom-cpp.md)|Umožňuje definovat vlastní atribut.|
|[db_command](db-command.md)|Vytvoří příkaz OLE DB.|
|[db_param](db-param.md)|Přidruží zadanou členskou proměnnou ke vstupnímu nebo výstupnímu parametru a naomezuje proměnnou.|
|[db_source](db-source.md)|Vytvoří připojení ke zdroji dat.|
|[db_table](db-table.md)|Otevře tabulku OLE DB.|
|[default](default-cpp.md)|Indikuje, že vlastní nebo odesílající pole definované v rámci třídy typu coclass představuje výchozí rozhraní programovatelnosti.|
|[defaultvtable](defaultvtable.md)|Definuje rozhraní jako výchozí rozhraní vtable pro ovládací prvek.|
|[event_receiver](event-receiver.md)|Vytvoří přijímač událostí.|
|[event_source](event-source.md)|Vytvoří zdroj události.|
|[helpcontext](helpcontext.md)|Určuje ID kontextu, které uživateli umožňuje zobrazit informace o tomto prvku v souboru **help** .|
|[helpfile](helpfile.md)|Nastaví název souboru s nápovědu pro knihovnu typů.|
|[helpstringcontext](helpstringcontext.md)|Určuje ID tématu nápovědy v souboru HLP nebo CHM.|
|[helpstring](helpstring.md)|Určuje řetězec znaků, který se používá k popisu prvku, na který se vztahuje.|
|[hidden](hidden.md)|Označuje, že položka existuje, ale neměla by se zobrazovat v prohlížeči orientovaném na uživatele.|
|[implements](implements-cpp.md)|Určuje odesílající rozhraní, která musí být členy coclass třídy IDL.|
|[implements_category](implements-category.md)|Určuje implementované kategorie komponent pro třídu.|
|[module](module-cpp.md)|Definuje blok knihovny v souboru. idl.|
|[noncreatable](noncreatable.md)|Definuje objekt, který nemůže být vytvořen sám sebou.|
|[progid](progid.md)|Definuje ProgID pro ovládací prvek.|
|[registration_script](registration-script.md)|Provede zadaný registrační skript.|
|[requestedit](requestedit.md)|Označuje, že vlastnost podporuje oznámení `OnRequestEdit`.|
|[source](source-cpp.md)|Určuje zdrojová rozhraní ovládacího prvku pro body připojení třídy. U vlastnosti nebo metody atribut `source` označuje, že člen vrátí objekt nebo `VARIANT`, který je zdrojem událostí.|
|[support_error_info](support-error-info.md)|Podporuje zasílání zpráv o chybách pro cílový objekt.|
|[threading](threading-cpp.md)|Určuje model vláken pro ovládací prvek.|
|[uuid](uuid-cpp-attributes.md)|Určuje jedinečné ID pro třídu nebo rozhraní.|
|[version](version-cpp.md)|Identifikuje konkrétní verzi z více verzí třídy.|
|[vi_progid](vi-progid.md)|Určuje formu ProgID nezávislou na verzi.|

## <a name="see-also"></a>Viz také

[Atributy podle použití](attributes-by-usage.md)
