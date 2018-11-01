---
title: '#Importovat atributy (C++)'
ms.date: 11/04/2016
helpviewer_keywords:
- '#import directive, attributes'
ms.assetid: 2a5085e3-82ee-4f83-892b-0aa6cc13863b
ms.openlocfilehash: 3cd1b259270ff8c76ac80ec66000f3c8177140fa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624403"
---
# <a name="import-attributes-c"></a>#import – atributy (C++)
Obsahuje odkazy na atributy použité s `#import` směrnice.

**Specifické pro Microsoft**

Následující atributy jsou k dispozici na `#import` směrnice.

|Atribut|Popis|
|---------------|-----------------|
|[auto_rename](../preprocessor/auto-rename.md)|Přejmenuje vyhrazená slova jazyka C++ přidáním dvou podtržítek (__) k názvu proměnné a vyřeší tak možné konflikty názvů.|
|[auto_search](../preprocessor/auto-search.md)|Určuje, že v případě, kdy je na knihovnu typů odkazováno direktivou #import a sama odkazuje na jinou knihovnu typů, může kompilátor zavést implicitní direktivu #import na tuto jinou knihovnu typů.|
|[embedded_idl](../preprocessor/embedded-idl.md)|Určuje, že knihovna typů je zapsána do souboru .tlh se zachovaným kódem atributem generován.|
|[Vyloučení](../preprocessor/exclude-hash-import.md)|Vyloučí položky z generovaných souborů hlaviček knihoven typů.|
|[high_method_prefix](../preprocessor/high-method-prefix.md)|Určuje předponu pro pojmenování základní vlastnosti a metody.|
|[high_property_prefixes](../preprocessor/high-property-prefixes.md)|Určuje alternativní předpony pro tři metody vlastností.|
|[implementation_only](../preprocessor/implementation-only.md)|Potlačí generování souboru .tlh hlavičky (primární hlavičkový soubor).|
|[include()](../preprocessor/include-parens.md)|Zakáže automatické vyloučení.|
|[inject_statement](../preprocessor/inject-statement.md)|Vloží svůj argument jako zdrojový text do hlavičky knihovny typů.|
|[named_guids](../preprocessor/named-guids.md)|Instruuje kompilátor, aby definovat a inicializaci proměnných identifikátor GUID v původní stylu formuláře `LIBID_MyLib`, `CLSID_MyCoClass`, `IID_MyInterface`, a `DIID_MyDispInterface`.|
|[no_auto_exclude](../preprocessor/no-auto-exclude.md)|Zakáže automatické vyloučení.|
|[no_dual_interfaces](../preprocessor/no-dual-interfaces.md)|Změny způsobu, jakým kompilátor generuje funkce obálky pro duální rozhraní metody.|
|[no_implementation](../preprocessor/no-implementation.md)|Potlačí generování tli hlavičky, která obsahuje implementace členské funkce obálky.|
|[no_namespace](../preprocessor/no-namespace.md)|Určuje, že název oboru názvů není generovaný kompilátorem.|
|[no_registry](../preprocessor/no-registry.md)|Říká kompilátoru, aby v registru nevyhledával knihovny typů.|
|[no_search_namespace](../preprocessor/no-search-namespace.md)|Má stejné funkce jako [no_namespace](../preprocessor/no-namespace.md) atribut, ale je použita v knihovny typů, které můžete použít direktivu #import s [auto_search –](../preprocessor/auto-search.md) atribut.|
|[no_smart_pointers](../preprocessor/no-smart-pointers.md)|Potlačí vytváření inteligentních ukazatelů pro všechna rozhraní v knihovně typů.|
|[raw_dispinterfaces](../preprocessor/raw-dispinterfaces.md)|Instruuje kompilátor, aby generovat funkce nízké úrovně obálky pro dispinterface metody a vlastnosti, které volají `IDispatch::Invoke` a vrátí kód chyby: HRESULT.|
|[raw_interfaces_only](../preprocessor/raw-interfaces-only.md)|Potlačí generování obálky funkce zpracování chyb a [vlastnost](../cpp/property-cpp.md) deklarace, které používají tyto funkce obálky.|
|[raw_method_prefix](../preprocessor/raw-method-prefix.md)|Určuje jinou předponu vyhnete kolize názvů.|
|[raw_native_types](../preprocessor/raw-native-types.md)|Zakáže použití tlačítek třídy pro podporu modelu COM v funkce obálky vysoké úrovně a místo toho vynutí použití nižší úrovně datových typů.|
|[raw_property_prefixes](../preprocessor/raw-property-prefixes.md)|Určuje alternativní předpony pro tři metody vlastností.|
|[Přejmenovat](../preprocessor/rename-hash-import.md)|Funguje kolem problémy kolizí název.|
|[rename_namespace](../preprocessor/rename-namespace.md)|Přejmenuje obor názvů, který obsahuje obsah knihovny typů.|
|[rename_search_namespace](../preprocessor/rename-search-namespace.md)|Má stejné funkce jako [rename_namespace](../preprocessor/rename-namespace.md) atribut, ale je použita v knihovny typů, které můžete použít direktivu #import s [auto_search –](../preprocessor/auto-search.md) atribut.|
|[tlbid](../preprocessor/tlbid.md)|Umožňuje načítání knihoven jiné než primární typ knihovny.|

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)