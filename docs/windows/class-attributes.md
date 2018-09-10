---
title: Třídy atributů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 60243373ea6b34ebceffd6f1ae21723e71e11bbb
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313595"
---
# <a name="class-attributes"></a>Atributy třídy

Následující atributy se vztahují na [třídy](../cpp/class-cpp.md) – klíčové slovo C++.

|Atribut|Popis|
|---------------|-----------------|
|[aggregatable](../windows/aggregatable.md)|Označuje, že třída podporuje agregaci.|
|[aggregates](../windows/aggregates.md)|Označuje, že ovládací prvek agreguje cílové třídy.|
|[appobject](../windows/appobject.md)|Identifikuje coclass jako objekt aplikace, který je přidružen k aplikaci úplné .exe a označuje, že funkce a vlastnosti třídy typu coclass jsou globálně k dispozici v této knihovně typů.|
|[případ](../windows/case-cpp.md)|Používá se [switch_type –](../windows/switch-type.md) atribut ve sjednocení.|
|[coclass](../windows/coclass.md)|Vytvoří ovládací prvek ActiveX.|
|[COM_INTERFACE_ENTRY](../windows/com-interface-entry-cpp.md)|Přidá položku do rozhraní COM mapy.|
|[control](../windows/control.md)|Určuje, jestli je typ uživatelského ovládacího prvku.|
|[Vlastní](../windows/custom-cpp.md)|Umožňuje definovat vlastní atribut.|
|[db_command](../windows/db-command.md)|Vytvoří příkaz OLE DB.|
|[db_param](../windows/db-param.md)|Přidruží zadaný členskou proměnnou vstupní nebo výstupní parametr a odděluje citaci proměnné.|
|[db_source](../windows/db-source.md)|Vytvoří připojení ke zdroji dat.|
|[db_table](../windows/db-table.md)|Otevře se tabulku OLE DB.|
|[default](../windows/default-cpp.md)|Označuje, že vlastní nebo dispinterface definované v rámci coclass představuje výchozí programovatelnosti rozhraní.|
|[defaultvtable](../windows/defaultvtable.md)|Definuje rozhraní jako výchozího rozhraní vtable pro ovládací prvek.|
|[event_receiver](../windows/event-receiver.md)|Vytvoří přijímače událostí.|
|[event_source](../windows/event-source.md)|Vytvoří zdroj událostí.|
|[helpcontext](../windows/helpcontext.md)|Určuje ID kontextu, který umožňuje uživateli zobrazit informace o tomto elementu v **pomáhají** souboru.|
|[helpfile](../windows/helpfile.md)|Nastaví název souboru nápovědy pro knihovnu typů.|
|[helpstringcontext](../windows/helpstringcontext.md)|Určuje ID tématu nápovědy HLP nebo CHM souboru.|
|[helpstring](../windows/helpstring.md)|Určuje řetězec znaků, který se používá k popisu elementu, ke kterému se vztahuje.|
|[hidden](../windows/hidden.md)|Označuje, že položka existuje, ale nebude se zobrazovat v prohlížeči uživatele.|
|[Implementuje](../windows/implements-cpp.md)|Určuje odesílajících rozhraních, které se musí být členy třídy typu IDL coclass.|
|[implements_category](../windows/implements-category.md)|Určuje kategorie implementované součásti pro třídu.|
|[Modul](../windows/module-cpp.md)|Bloku knihovny definuje v souboru IDL.|
|[noncreatable](../windows/noncreatable.md)|Definuje objekt, který se nedá vytvořit instance samostatně.|
|[progid](../windows/progid.md)|Definuje identifikátor ProgID ovládacího prvku.|
|[registration_script](../windows/registration-script.md)|Provede zadanou registraci skript.|
|[requestedit](../windows/requestedit.md)|Označuje, že vlastnost podporuje `OnRequestEdit` oznámení.|
|[Zdroj](../windows/source-cpp.md)|Určuje třídu rozhraní ovládacího prvku zdroje pro spojovací body. Na vlastnosti nebo metody `source` atribut označuje, že člen vrací objekt nebo `VARIANT` , který je zdrojem událostí.|
|[support_error_info](../windows/support-error-info.md)|Podporuje odesílání sestav chyb pro cílový objekt.|
|[Dělení na vlákna](../windows/threading-cpp.md)|Určuje model vláken pro ovládací prvek.|
|[uuid](../windows/uuid-cpp-attributes.md)|Určuje jedinečné ID pro třídu nebo rozhraní.|
|[Verze](../windows/version-cpp.md)|Určuje konkrétní verzi napříč několika verzemi třídu.|
|[vi_progid](../windows/vi-progid.md)|Určuje verzi nezávislé formu ProgID.|

## <a name="see-also"></a>Viz také

[Atributy podle použití](../windows/attributes-by-usage.md)