---
title: '#<a name="import-attributes-c--microsoft-docs"></a>Import atributy (C++) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: '#import directive, attributes'
ms.assetid: 2a5085e3-82ee-4f83-892b-0aa6cc13863b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fd11326e33ff783b3868215794f9803e97d41c55
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="import-attributes-c"></a>#import – atributy (C++)
Obsahuje odkazy na atributy používané s #import – direktiva.  
  
 **Konkrétní Microsoft**  
  
 Následující atributy jsou k dispozici #import – direktiva.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|[auto_rename –](../preprocessor/auto-rename.md)|Přejmenuje vyhrazená slova jazyka C++ přidáním dvou podtržítek (__) k názvu proměnné a vyřeší tak možné konflikty názvů.|  
|[auto_search –](../preprocessor/auto-search.md)|Určuje, že v případě, kdy je na knihovnu typů odkazováno direktivou #import a sama odkazuje na jinou knihovnu typů, může kompilátor zavést implicitní direktivu #import na tuto jinou knihovnu typů.|  
|[embedded_idl –](../preprocessor/embedded-idl.md)|Určuje, že knihovny typů je zapsán do souboru .tlh kódem generované atribut zachovaná.|  
|[vyloučení](../preprocessor/exclude-hash-import.md)|Vyloučí položky z generovaných souborů hlaviček knihoven typů.|  
|[high_method_prefix –](../preprocessor/high-method-prefix.md)|Určuje předpony v názvu základní vlastnosti a metody.|  
|[high_property_prefixes –](../preprocessor/high-property-prefixes.md)|Určuje alternativní předpony pro tři metody vlastností.|  
|[implementation_only –](../preprocessor/implementation-only.md)|Potlačí generování hlavičkový soubor .tlh (primární hlavičkový soubor).|  
|[include()](../preprocessor/include-parens.md)|Zakáže automatické vyloučení.|  
|[inject_statement –](../preprocessor/inject-statement.md)|Vloží svůj argument jako zdrojový text do hlavičky knihovny typů.|  
|[named_guids –](../preprocessor/named-guids.md)|Určuje, kompilátor definovat a inicializace proměnné identifikátor GUID v původní styl, formuláře **LIBID_MyLib**, **CLSID_MyCoClass**, **IID_MyInterface**, a **DIID _MyDispInterface**.|  
|[no_auto_exclude –](../preprocessor/no-auto-exclude.md)|Zakáže automatické vyloučení.|  
|[no_dual_interfaces –](../preprocessor/no-dual-interfaces.md)|Změny způsob kompilátor generuje funkce obálku pro metody duální rozhraní.|  
|[no_implementation –](../preprocessor/no-implementation.md)|Potlačí generování .tli hlavičky, která obsahuje implementace členských funkcí obálku.|  
|[no_namespace –](../preprocessor/no-namespace.md)|Určuje, že název oboru názvů není generované kompilátorem.|  
|[no_registry –](../preprocessor/no-registry.md)|Určuje, kompilátor není v registru pro knihovny typů.|  
|[no_search_namespace –](../preprocessor/no-search-namespace.md)|Má stejné funkce jako [no_namespace –](../preprocessor/no-namespace.md) atribut ale se používá na knihovny typů, které používají #import – direktiva s [auto_search –](../preprocessor/auto-search.md) atribut.|  
|[no_smart_pointers –](../preprocessor/no-smart-pointers.md)|Potlačí vytvoření chytré ukazatele pro všechna rozhraní v knihovně typů.|  
|[raw_dispinterfaces –](../preprocessor/raw-dispinterfaces.md)|Určuje, kompilátor generovat funkce nízké úrovně obálku pro dispinterface metody a vlastnosti, které volají **volání metody IDispatch::Invoke** a vrátíte se `HRESULT` kód chyby.|  
|[raw_interfaces_only –](../preprocessor/raw-interfaces-only.md)|Potlačí generování funkce obálky zpracování chyb a [vlastnost](../cpp/property-cpp.md) deklarace, které používají tyto funkce obálku.|  
|[raw_method_prefix –](../preprocessor/raw-method-prefix.md)|Určuje předponu různých předejdete kolize názvů.|  
|[raw_native_types –](../preprocessor/raw-native-types.md)|Zakáže použití třídy, které podporují COM v funkce vysoké úrovně obálku a místo toho vynutí používání nízké úrovně datových typů.|  
|[raw_property_prefixes –](../preprocessor/raw-property-prefixes.md)|Určuje alternativní předpony pro tři metody vlastností.|  
|[Přejmenování](../preprocessor/rename-hash-import.md)|Funguje kolem název kolizí problémy.|  
|[rename_namespace –](../preprocessor/rename-namespace.md)|Přejmenuje obor názvů, který obsahuje obsah knihovny typů.|  
|[rename_search_namespace –](../preprocessor/rename-search-namespace.md)|Má stejné funkce jako [rename_namespace –](../preprocessor/rename-namespace.md) atribut ale se používá na knihovny typů, které používají #import – direktiva s [auto_search –](../preprocessor/auto-search.md) atribut.|  
|[TLBID –](../preprocessor/tlbid.md)|Umožňuje načítání knihoven než knihovny primární typů.|  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [#import – direktiva](../preprocessor/hash-import-directive-cpp.md)