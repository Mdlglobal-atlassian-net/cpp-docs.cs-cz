---
title: "TypeDef, Enum, Union a Struct – atributy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- union attributes
- attributes [C++], reference topics
- struct attributes
- typedef attributes
- enum attributes
ms.assetid: f8a4fe94-dc02-4aed-bc31-3e500d42f4c7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2087d4ff4e4905324f9bbdfaa954287f033feafe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="typedef-enum-union-and-struct-attributes"></a>Atributy klíčových slov typedef, enum, union a struct
Následující atributy se používají na [typedef](http://msdn.microsoft.com/en-us/cc96cf26-ba93-4179-951e-695d1f5fdcf1), [struktura](../cpp/struct-cpp.md), a [výčtu](../cpp/enumerations-cpp.md) klíčová slova jazyka C++.  
  
### <a name="typedef"></a>– definice typedef  
  
|Atribut|Popis|  
|---------------|-----------------|  
|[případ](../windows/case-cpp.md)|Použít s [switch_type –](../windows/switch-type.md) atribut **sjednocení**.|  
|[vlastní](../windows/custom-cpp.md)|Umožňuje definovat vlastní atribut.|  
|[export](../windows/export.md)|Způsobí, že datová struktura umístit do souboru.|  
|[first_is](../windows/first-is.md)|Určuje index první prvek pole má být přenesen.|  
|[helpcontext](../windows/helpcontext.md)|Určuje Identifikátor kontext, který umožňuje uživateli zobrazit informace o tomto prvku v souboru nápovědy.|  
|[helpfile](../windows/helpfile.md)|Nastaví název souboru nápovědy knihovny typů.|  
|[helpstring](../windows/helpstring.md)|Určuje řetězec znaků, který se používá k popisu elementu, na který se vztahuje.|  
|[library_block](../windows/library-block.md)|Umístí konstrukce uvnitř bloku souboru IDL knihovny.|  
|[ptr](../windows/ptr.md)|Ukazatel se označí jako úplné ukazatel.|  
|[public](../windows/public-cpp-attributes.md)|Zajišťuje, že definice typu přejde do knihovny typů, i když neodkazuje z v rámci tohoto souboru .idl.|  
|[ref](../windows/ref-cpp.md)|Identifikuje ukazatel odkaz.|  
|[switch_is](../windows/switch-is.md)|Určuje výraz nebo identifikátor, který funguje jako union discriminant, která vybere položku členů sjednocení.|  
|[switch_type](../windows/switch-type.md)|Určuje typ proměnnou použít jako union discriminant.|  
|[jedinečné](../windows/unique-cpp.md)|Určuje jedinečný ukazatel.|  
|[wire_marshal](../windows/wire-marshal.md)|Určuje datový typ, který se použije pro přenos místo specifické pro aplikaci datového typu.|  
  
### <a name="enum"></a>enum  
  
|Atribut|Popis|  
|---------------|-----------------|  
|[vlastní](../windows/custom-cpp.md)|Umožňuje definovat vlastní atribut.|  
|[export](../windows/export.md)|Způsobí, že datová struktura umístit do souboru.|  
|[UUID](../windows/uuid-cpp-attributes.md)|Určuje jedinečné ID pro třídy nebo rozhraní.|  
|[v1_enum](../windows/v1-enum.md)|Přesměruje, že zadaného výčtového typu předávají jako 32bitová verze entity, nikoli výchozí 16 bitů.|  
  
### <a name="union"></a>sjednocení  
  
|Atribut|Popis|  
|---------------|-----------------|  
|[vlastní](../windows/custom-cpp.md)|Umožňuje definovat vlastní atribut.|  
|[export](../windows/export.md)|Způsobí, že datová struktura umístit do souboru.|  
|[first_is](../windows/first-is.md)|Určuje index první prvek pole má být přenesen.|  
|[last_is](../windows/last-is.md)|Určuje index posledním elementem pole přenášet.|  
|[length_is](../windows/length-is.md)|Určuje počet elementů pole přenášet.|  
|[max_is](../windows/max-is.md)|Určuje maximální hodnotu platné pole indexu.|  
|[size_is](../windows/size-is.md)|Určuje velikost paměti přidělené velikostí ukazatele, velikost ukazatele na velikosti ukazatele a jedním - nebo vícerozměrná pole.|  
|[jedinečné](../windows/unique-cpp.md)|Určuje jedinečný ukazatel.|  
|[UUID](../windows/uuid-cpp-attributes.md)|Určuje jedinečné ID pro třídy nebo rozhraní.|  
  
### <a name="nonencapsulated-union"></a>Nonencapsulated sjednocení  
  
|Atribut|Popis|  
|---------------|-----------------|  
|[ms_union](../windows/ms-union.md)|Určuje zarovnání reprezentace dat sítě nonencapsulated sjednocení.|  
|[no_injected_text](../windows/no-injected-text.md)|Kompilátor brání vložení kódu v důsledku použití atributu.|  
  
### <a name="struct"></a>struct   
  
|Atribut|Popis|  
|---------------|-----------------|  
|[aggregatable](../windows/aggregatable.md)|Označuje, že třída podporuje agregace.|  
|[aggregates](../windows/aggregates.md)|Označuje, že ovládacího prvku agreguje cílové třídy.|  
|[appobject](../windows/appobject.md)|Identifikuje třída typu coclass jako objekt aplikace, který je přidružen k aplikaci úplné .exe a označuje, že funkce a vlastnosti coclass jsou globálně dostupnou v této knihovně typu.|  
|[coclass](../windows/coclass.md)|Vytvoří ovládacího prvku ActiveX.|  
|[COM_INTERFACE_ENTRY –](../windows/com-interface-entry-cpp.md)|Přidá položku rozhraní COM mapu.|  
|[control](../windows/control.md)|Určuje, že je uživatelem definovaný typ ovládacího prvku.|  
|[vlastní](../windows/custom-cpp.md)|Umožňuje definovat vlastní atribut.|  
|[db_column](../windows/db-column.md)|Vytvoří vazbu zadaný sloupec sady řádků.|  
|[db_command](../windows/db-command.md)|Vytvoří příkaz OLE DB.|  
|[db_param](../windows/db-param.md)|Přidruží zadané členské proměnné vstupní nebo výstupní parametr a vymezuje proměnnou.|  
|[db_source](../windows/db-source.md)|Vytvoří připojení ke zdroji dat.|  
|[db_table](../windows/db-table.md)|Otevře se tabulce OLE DB.|  
|[default](../windows/default-cpp.md)|Označuje, že vlastní a odesílající rozhraní definované v rámci coclass představuje výchozí programovatelnosti rozhraní.|  
|[defaultvtable](../windows/defaultvtable.md)|Definuje rozhraní jako výchozí vtable rozhraní pro ovládací prvek.|  
|[event_receiver](../windows/event-receiver.md)|Vytvoří přijímače událostí.|  
|[event_source](../windows/event-source.md)|Vytvoří zdroje událostí.|  
|[export](../windows/export.md)|Způsobí, že datová struktura umístit do souboru.|  
|[first_is](../windows/first-is.md)|Určuje index první prvek pole má být přenesen.|  
|[hidden](../windows/hidden.md)|Určuje, že položka existuje, ale by se neměly zobrazovat v prohlížeči uživatele.|  
|[implements_category](../windows/implements-category.md)|Určuje implementovaná součást kategorie pro třídu.|  
|[last_is](../windows/last-is.md)|Určuje index posledním elementem pole přenášet.|  
|[length_is](../windows/length-is.md)|Určuje počet elementů pole přenášet.|  
|[max_is](../windows/max-is.md)|Určuje maximální hodnotu platné pole indexu.|  
|[requires_category](../windows/requires-category.md)|Určuje požadovanou součást kategorie cílové třídy.|  
|[size_is](../windows/size-is.md)|Určuje velikost paměti přidělené velikostí ukazatele, velikost ukazatele na velikosti ukazatele a jedním - nebo vícerozměrná pole.|  
|[zdroj](../windows/source-cpp.md)|Na třídu určuje rozhraní zdrojového objektu COM pro spojovací body. Na vlastnosti nebo metody označuje, že člen vrátí objekt, nebo typu VARIANT, která je zdroj událostí systému.|  
|[dělení na vlákna](../windows/threading-cpp.md)|Určuje model vláken pro objekt COM.|  
|[jedinečné](../windows/unique-cpp.md)|Určuje jedinečný ukazatel.|  
|[UUID](../windows/uuid-cpp-attributes.md)|Určuje jedinečné ID pro třídy nebo rozhraní.|  
|[verze](../windows/version-cpp.md)|Identifikuje na konkrétní verzi mezi více verzí třídy.|  
|[vi_progid](../windows/vi-progid.md)|Určuje nezávislé na verzi forma identifikátor ProgID.|  
  
## <a name="see-also"></a>Viz také  
 [Atributy podle použití](../windows/attributes-by-usage.md)