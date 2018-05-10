---
title: Třídy atributů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], class attributes
- class attributes
ms.assetid: fad04ea1-d8ff-46d4-bb42-2b4500a6ab60
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8a932fdb1ef1d9e2af2acace901feaa95b6216d1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="class-attributes"></a>Atributy třídy
Následující atributy se používají na [třída](../cpp/class-cpp.md) C++ – klíčové slovo.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|[aggregatable](../windows/aggregatable.md)|Označuje, že třída podporuje agregace.|  
|[aggregates](../windows/aggregates.md)|Označuje, že ovládacího prvku agreguje cílové třídy.|  
|[appobject](../windows/appobject.md)|Identifikuje třída typu coclass jako objekt aplikace, který je přidružen k aplikaci úplné .exe a označuje, že funkce a vlastnosti coclass jsou globálně dostupnou v této knihovně typu.|  
|[Případ](../windows/case-cpp.md)|Používá se [switch_type –](../windows/switch-type.md) atribut v spojení.|  
|[coclass](../windows/coclass.md)|Vytvoří ovládacího prvku ActiveX.|  
|[COM_INTERFACE_ENTRY –](../windows/com-interface-entry-cpp.md)|Přidá položku rozhraní COM mapu.|  
|[control](../windows/control.md)|Určuje, že je uživatelem definovaný typ ovládacího prvku.|  
|[Vlastní](../windows/custom-cpp.md)|Umožňuje definovat vlastní atribut.|  
|[db_command](../windows/db-command.md)|Vytvoří příkaz OLE DB.|  
|[db_param](../windows/db-param.md)|Přidruží zadané členské proměnné vstupní nebo výstupní parametr a vymezuje proměnnou.|  
|[db_source](../windows/db-source.md)|Vytvoří připojení ke zdroji dat.|  
|[db_table](../windows/db-table.md)|Otevře se tabulce OLE DB.|  
|[default](../windows/default-cpp.md)|Označuje, že vlastní a odesílající rozhraní definované v rámci coclass představuje výchozí programovatelnosti rozhraní.|  
|[defaultvtable](../windows/defaultvtable.md)|Definuje rozhraní jako výchozí vtable rozhraní pro ovládací prvek.|  
|[event_receiver](../windows/event-receiver.md)|Vytvoří přijímače událostí.|  
|[event_source](../windows/event-source.md)|Vytvoří zdroje událostí.|  
|[helpcontext](../windows/helpcontext.md)|Určuje Identifikátor kontext, který umožňuje uživateli zobrazit informace o tomto prvku v souboru nápovědy.|  
|[helpfile](../windows/helpfile.md)|Nastaví název souboru nápovědy knihovny typů.|  
|[helpstringcontext](../windows/helpstringcontext.md)|Určuje ID tématu nápovědy v souboru HLP nebo CHM.|  
|[helpstring](../windows/helpstring.md)|Určuje řetězec znaků, který se používá k popisu elementu, na který se vztahuje.|  
|[hidden](../windows/hidden.md)|Určuje, že položka existuje, ale by se neměly zobrazovat v prohlížeči uživatele.|  
|[Implementuje](../windows/implements-cpp.md)|Určuje odesílání rozhraní, které mají být členy třída typu coclass IDL vynuceně přesunuty.|  
|[implements_category](../windows/implements-category.md)|Určuje implementovaná součást kategorie pro třídu.|  
|[Modul](../windows/module-cpp.md)|Knihovna bloku definuje v souboru.|  
|[noncreatable](../windows/noncreatable.md)|Definuje objekt, který nelze vytvořit instanci samostatně.|  
|[progid](../windows/progid.md)|Definuje ProgID pro ovládací prvek.|  
|[registration_script](../windows/registration-script.md)|Spustí skript zadanou registraci.|  
|[requestedit](../windows/requestedit.md)|Označuje, že vlastnost podporuje **OnRequestEdit, viz** oznámení.|  
|[Zdroj](../windows/source-cpp.md)|Určuje zdroj rozhraní ovládacího prvku pro spojovací body na třídu. Na vlastnosti nebo metody **zdroj** atribut označuje, že člen vrátí objekt, nebo typu VARIANT, která je zdroj událostí systému.|  
|[support_error_info](../windows/support-error-info.md)|Podporuje odesílání sestav chyb pro cílový objekt.|  
|[Dělení na vlákna](../windows/threading-cpp.md)|Určuje model vláken pro ovládací prvek.|  
|[uuid](../windows/uuid-cpp-attributes.md)|Určuje jedinečné ID pro třídy nebo rozhraní.|  
|[Verze](../windows/version-cpp.md)|Identifikuje na konkrétní verzi mezi více verzí třídy.|  
|[vi_progid](../windows/vi-progid.md)|Určuje nezávislé na verzi forma identifikátor ProgID.|  
  
## <a name="see-also"></a>Viz také  
 [Atributy podle použití](../windows/attributes-by-usage.md)