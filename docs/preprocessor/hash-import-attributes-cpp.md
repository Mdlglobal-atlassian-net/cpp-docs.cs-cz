---
title: '#Import atributů (C++)'
ms.date: 08/29/2019
helpviewer_keywords:
- '#import directive, attributes'
ms.assetid: 2a5085e3-82ee-4f83-892b-0aa6cc13863b
ms.openlocfilehash: 7e0de241bd27269d7d758c49bc54c4bf435cf383
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220103"
---
# <a name="import-attributes-c"></a>Atributy #import (C++)

Obsahuje odkazy na atributy používané s `#import` direktivou.

**Specifické pro společnost Microsoft**

Následující atributy jsou k dispozici pro `#import` direktivu.

|Atribut|Popis|
|---------------|-----------------|
|[auto_rename](../preprocessor/auto-rename.md)|Přejmenuje vyhrazená slova jazyka C++ přidáním dvou podtržítek (__) k názvu proměnné a vyřeší tak možné konflikty názvů.|
|[auto_search](../preprocessor/auto-search.md)|Určuje, že v případě, kdy je na knihovnu typů odkazováno direktivou #import a sama odkazuje na jinou knihovnu typů, může kompilátor zavést implicitní direktivu #import na tuto jinou knihovnu typů.|
|[embedded_idl](../preprocessor/embedded-idl.md)|Určuje, že knihovna typů je zapsána do souboru. tlh s zachovaným kódem generovaným atributem.|
|[slevy](../preprocessor/exclude-hash-import.md)|Vyloučí položky z generovaných souborů hlaviček knihoven typů.|
|[high_method_prefix](../preprocessor/high-method-prefix.md)|Určuje předponu, která se má použít při pojmenování vlastností a metod na vysoké úrovni.|
|[high_property_prefixes](../preprocessor/high-property-prefixes.md)|Určuje alternativní předpony pro tři metody vlastností.|
|[implementation_only](../preprocessor/implementation-only.md)|Potlačí generování hlavičkového souboru. tlh (primární hlavičkový soubor).|
|[include()](../preprocessor/include-parens.md)|Zakáže automatické vyloučení.|
|[inject_statement](../preprocessor/inject-statement.md)|Vloží svůj argument jako zdrojový text do hlavičky knihovny typů.|
|[named_guids](../preprocessor/named-guids.md)|Instruuje kompilátor, aby definoval a inicializoval proměnné GUID `LIBID_MyLib`ve starém stylu formuláře, `CLSID_MyCoClass`, `IID_MyInterface`a `DIID_MyDispInterface`.|
|[no_auto_exclude](../preprocessor/no-auto-exclude.md)|Zakáže automatické vyloučení.|
|[no_dual_interfaces](../preprocessor/no-dual-interfaces.md)|Mění způsob, jakým kompilátor generuje obálkové funkce pro metody duálního rozhraní.|
|[no_implementation](../preprocessor/no-implementation.md)|Potlačí generování hlavičky. tli, která obsahuje implementace členských funkcí obálky.|
|[no_namespace](../preprocessor/no-namespace.md)|Určuje, že kompilátor negeneruje název oboru názvů.|
|[no_registry](../preprocessor/no-registry.md)|Instruuje kompilátor, aby nehledal v registru knihovny typů.|
|[no_search_namespace](../preprocessor/no-search-namespace.md)|Má stejné funkce jako atribut [no_namespace](../preprocessor/no-namespace.md) , ale používá se pro knihovny typů, které používají direktivu #import s atributem [auto_search](../preprocessor/auto-search.md) .|
|[no_smart_pointers](../preprocessor/no-smart-pointers.md)|Potlačí vytváření inteligentních ukazatelů pro všechna rozhraní v knihovně typů.|
|[raw_dispinterfaces](../preprocessor/raw-dispinterfaces.md)|Instruuje kompilátor, aby vygeneroval funkce obálky nízké úrovně pro metody a vlastnosti pro vyvolání `IDispatch::Invoke` a vrátí kód chyby HRESULT.|
|[raw_interfaces_only](../preprocessor/raw-interfaces-only.md)|Potlačí generování obálkových funkcí zpracování chyb a deklarací [vlastností](../cpp/property-cpp.md) , které používají tyto funkce obálky.|
|[raw_method_prefix](../preprocessor/raw-method-prefix.md)|Určuje jinou předponu, aby se předešlo kolizím názvů.|
|[raw_native_types](../preprocessor/raw-native-types.md)|Zakáže použití tříd podpory modelu COM v obálkových funkcích vysoké úrovně a vynutí místo toho použití datových typů nízké úrovně.|
|[raw_property_prefixes](../preprocessor/raw-property-prefixes.md)|Určuje alternativní předpony pro tři metody vlastností.|
|[Změňte](../preprocessor/rename-hash-import.md)|Funguje kolem problémů kolize názvů.|
|[rename_namespace](../preprocessor/rename-namespace.md)|Přejmenuje obor názvů, který obsahuje obsah knihovny typů.|
|[rename_search_namespace](../preprocessor/rename-search-namespace.md)|Má stejné funkce jako atribut [rename_namespace](../preprocessor/rename-namespace.md) , ale používá se pro knihovny typů, které používají direktivu #import s atributem [auto_search](../preprocessor/auto-search.md) .|
|[tlbid](../preprocessor/tlbid.md)|Umožňuje načíst knihovny jiné než primární typ knihovny.|

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[#import direktiva](../preprocessor/hash-import-directive-cpp.md)