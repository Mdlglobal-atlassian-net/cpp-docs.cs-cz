---
title: Atributy metody | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- method attributes
- attributes [C++], reference topics
ms.assetid: b2313352-480d-488b-8c35-6242ffd3a549
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f2413543e7638f47db13799e0549a415ee92c1c2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="method-attributes"></a>Atributy metody
Následující atributy se používají metody ve třídě, třída typu coclass nebo rozhraní.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|[bindable](../windows/bindable.md)|Označuje, že vlastnost podporuje datovou vazbu.|  
|[call_as](../windows/call-as.md)|Umožňuje nonremotable funkce nejde mapovat na vzdálené funkce.|  
|[vlastní](../windows/custom-cpp.md)|Umožňuje definovat vlastní atribut.|  
|[db_column](../windows/db-column.md)|Vytvoří vazbu zadaný sloupec sady řádků.|  
|[db_command](../windows/db-command.md)|Vytvoří příkaz OLE DB.|  
|[db_param](../windows/db-param.md)|Přidruží zadané členské proměnné vstupní nebo výstupní parametr a vymezuje proměnnou.|  
|[db_source](../windows/db-source.md)|Vytvoří připojení ke zdroji dat.|  
|[db_table](../windows/db-table.md)|Otevře se tabulce OLE DB.|  
|[defaultbind](../windows/defaultbind.md)|Určuje jeden, vazbu vlastnosti, která nejlépe představuje objekt.|  
|[defaultcollelem](../windows/defaultcollelem.md)|Používá pro optimalizaci kód jazyka Visual Basic.|  
|[displaybind](../windows/displaybind.md)|Určuje vlastnosti, která má být zobrazena uživateli jako vazbu.|  
|[helpcontext](../windows/helpcontext.md)|Určuje Identifikátor kontext, který umožňuje uživateli zobrazit informace o tomto prvku v souboru nápovědy.|  
|[helpfile](../windows/helpfile.md)|Nastaví název souboru nápovědy knihovny typů.|  
|[helpstring](../windows/helpstring.md)|Určuje řetězec znaků, který se používá k popisu elementu, na který se vztahuje.|  
|[helpstringcontext](../windows/helpstringcontext.md)|Určuje ID tématu nápovědy v souboru HLP nebo CHM.|  
|[helpstringdll](../windows/helpstringdll.md)|Určuje název knihovny DLL používat k provádění vyhledávací řetězec dokumentu (lokalizace).|  
|[hidden](../windows/hidden.md)|Určuje, že položka existuje, ale by se neměly zobrazovat v prohlížeči uživatele.|  
|[id](../windows/id.md)|Určuje DISPID pro členské funkce (vlastnost nebo metodu, v rozhraní nebo dispinterface).|  
|[immediatebind](../windows/immediatebind.md)|Označuje, že databáze bude okamžitě informováni o všechny změny vlastností objektu vázané na data.|  
|[in](../windows/in-cpp.md)|Označuje, že parametr je mají být předány z volání procedury volané procedury.|  
|[místní](../windows/local-cpp.md)|Umožňuje použít MIDL kompilátoru jako generátor záhlaví při použití v hlavičce rozhraní. Při použití v jednotlivé funkce, označí místní postupu, pro které jsou generovány žádné zástupných procedur.|  
|[nonbrowsable](../windows/nonbrowsable.md)|Označuje, že člena rozhraní by se neměly zobrazovat v prohlížeči vlastností.|  
|[propget](../windows/propget.md)|Určuje funkci přistupujícího objektu vlastnosti.|  
|[propput](../windows/propput.md)|Určuje nastavení vlastnosti funkce.|  
|[propputref](../windows/propputref.md)|Určuje nastavení vlastnosti funkci, která používá odkaz místo hodnotu.|  
|[ptr](../windows/ptr.md)|Ukazatel se označí jako úplné ukazatel.|  
|[rozsah](../windows/range-cpp.md)|Určuje rozsah povolených hodnot pro argumenty nebo pole, jejichž hodnoty jsou nastaveny v době běhu.|  
|[requestedit](../windows/requestedit.md)|Označuje, že vlastnost podporuje **OnRequestEdit, viz** oznámení.|  
|[restricted](../windows/restricted.md)|Určuje, že členem modulu, rozhraní nebo dispinterface nelze volat libovolně.|  
|[satype](../windows/satype.md)|Určuje datový typ **SAFEARRAY** struktura.|  
|[zdroj](../windows/source-cpp.md)|Určuje zdroj rozhraní ovládacího prvku pro spojovací body na třídu. Na vlastnosti nebo metody **zdroj** atribut označuje, že člen vrátí objekt, nebo typu VARIANT, která je zdroj událostí systému.|  
|[synchronize](../windows/synchronize.md)|Synchronizuje přístup k cílové metody.|  
|[vararg](../windows/vararg.md)|Určuje, že funkce trvat proměnný počet argumentů.|  
  
## <a name="see-also"></a>Viz také  
 [Atributy podle použití](../windows/attributes-by-usage.md)