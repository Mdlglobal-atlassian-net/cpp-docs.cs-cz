---
title: Třídy atributů (C++ COM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], class attributes
ms.assetid: fad04ea1-d8ff-46d4-bb42-2b4500a6ab60
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a727bcf53a11e98ffd7e037037452c6bbdc4fe8a
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789368"
---
# <a name="class-attributes"></a>Atributy třídy

Následující atributy se vztahují na [třídy](../../cpp/class-cpp.md) – klíčové slovo C++.

|Atribut|Popis|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Označuje, že třída podporuje agregaci.|
|[aggregates](aggregates.md)|Označuje, že ovládací prvek agreguje cílové třídy.|
|[appobject](appobject.md)|Identifikuje coclass jako objekt aplikace, který je přidružen k aplikaci úplné .exe a označuje, že funkce a vlastnosti třídy typu coclass jsou globálně k dispozici v této knihovně typů.|
|[případ](case-cpp.md)|Používá se [switch_type –](switch-type.md) atribut ve sjednocení.|
|[coclass](coclass.md)|Vytvoří ovládací prvek ActiveX.|
|[COM_INTERFACE_ENTRY](com-interface-entry-cpp.md)|Přidá položku do rozhraní COM mapy.|
|[control](control.md)|Určuje, jestli je typ uživatelského ovládacího prvku.|
|[Vlastní](custom-cpp.md)|Umožňuje definovat vlastní atribut.|
|[db_command](db-command.md)|Vytvoří příkaz OLE DB.|
|[db_param](db-param.md)|Přidruží zadaný členskou proměnnou vstupní nebo výstupní parametr a odděluje citaci proměnné.|
|[db_source](db-source.md)|Vytvoří připojení ke zdroji dat.|
|[db_table](db-table.md)|Otevře se tabulku OLE DB.|
|[default](default-cpp.md)|Označuje, že vlastní nebo dispinterface definované v rámci coclass představuje výchozí programovatelnosti rozhraní.|
|[defaultvtable](defaultvtable.md)|Definuje rozhraní jako výchozího rozhraní vtable pro ovládací prvek.|
|[event_receiver](event-receiver.md)|Vytvoří přijímače událostí.|
|[event_source](event-source.md)|Vytvoří zdroj událostí.|
|[helpcontext](helpcontext.md)|Určuje ID kontextu, který umožňuje uživateli zobrazit informace o tomto elementu v **pomáhají** souboru.|
|[helpfile](helpfile.md)|Nastaví název souboru nápovědy pro knihovnu typů.|
|[helpstringcontext](helpstringcontext.md)|Určuje ID tématu nápovědy HLP nebo CHM souboru.|
|[helpstring](helpstring.md)|Určuje řetězec znaků, který se používá k popisu elementu, ke kterému se vztahuje.|
|[hidden](hidden.md)|Označuje, že položka existuje, ale nebude se zobrazovat v prohlížeči uživatele.|
|[Implementuje](implements-cpp.md)|Určuje odesílajících rozhraních, které se musí být členy třídy typu IDL coclass.|
|[implements_category](implements-category.md)|Určuje kategorie implementované součásti pro třídu.|
|[Modul](module-cpp.md)|Bloku knihovny definuje v souboru IDL.|
|[noncreatable](noncreatable.md)|Definuje objekt, který se nedá vytvořit instance samostatně.|
|[progid](progid.md)|Definuje identifikátor ProgID ovládacího prvku.|
|[registration_script](registration-script.md)|Provede zadanou registraci skript.|
|[requestedit](requestedit.md)|Označuje, že vlastnost podporuje `OnRequestEdit` oznámení.|
|[Zdroj](source-cpp.md)|Určuje třídu rozhraní ovládacího prvku zdroje pro spojovací body. Na vlastnosti nebo metody `source` atribut označuje, že člen vrací objekt nebo `VARIANT` , který je zdrojem událostí.|
|[support_error_info](support-error-info.md)|Podporuje odesílání sestav chyb pro cílový objekt.|
|[Dělení na vlákna](threading-cpp.md)|Určuje model vláken pro ovládací prvek.|
|[uuid](uuid-cpp-attributes.md)|Určuje jedinečné ID pro třídu nebo rozhraní.|
|[Verze](version-cpp.md)|Určuje konkrétní verzi napříč několika verzemi třídu.|
|[vi_progid](vi-progid.md)|Určuje verzi nezávislé formu ProgID.|

## <a name="see-also"></a>Viz také

[Atributy podle použití](attributes-by-usage.md)