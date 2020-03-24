---
title: Abecedně řazená referenční dokumentace k atributům
ms.custom: index-page
ms.date: 10/02/2018
ms.topic: conceptual
f1_keywords:
- vc.attributes
helpviewer_keywords:
- attributes [C++/CLI]
ms.assetid: fb2216ef-9fbd-44f4-afed-732aa99450e2
ms.openlocfilehash: dbbb406765c0664f2cd332524a61713f9c67cf9e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167508"
---
# <a name="attributes-alphabetical-reference"></a>Abecedně řazená referenční dokumentace k atributům

V kompilátoru Microsoftu C++ jsou k dispozici následující atributy:

|Atribut|Popis|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Označuje, že ovládací prvek lze agregovat jiným ovládacím prvkem.|
|[aggregates](aggregates.md)|Indikuje, že ovládací prvek agreguje cílovou třídu.|
|[appobject](appobject.md)|Identifikuje třídu coclass jako aplikační objekt, který je přidružen k úplné aplikaci EXE a označuje, že funkce a vlastnosti třídy coclass jsou v této knihovně typů globálně dostupné.|
|[async_uuid](async-uuid.md)|Určuje identifikátor UUID, který přesměruje kompilátor MIDL tak, aby definoval synchronní i asynchronní verzi rozhraní modelu COM.|
|[attribute](attribute.md)|Umožňuje vytvořit vlastní atribut.|
|[bindable](bindable.md)|Označuje, že vlastnost podporuje datové vazby.|
|[call_as](call-as.md)|Umožňuje mapování nevzdáleně funkční funkce na vzdálenou funkci.|
|[case](case-cpp.md)|Používá se s atributem [switch_type](switch-type.md) ve sjednocení.|
|[coclass](coclass.md)|Vytvoří objekt modelu COM, který může implementovat rozhraní COM.|
|[com_interface_entry](com-interface-entry-cpp.md)|Přidá položku rozhraní do mapy modelu COM.|
|[control](control.md)|Určuje, že uživatelsky definovaný typ je ovládací prvek.|
|[cpp_quote](cpp-quote.md)|Vygeneruje zadaný řetězec bez znaků uvozovky do vygenerovaného souboru hlaviček.|
|[custom](custom-cpp.md)|Umožňuje definovat vlastní atributy.|
|[db_accessor](db-accessor.md)|Vytvoří vazby sloupců v sadě řádků a vytvoří jejich vazby k odpovídajícím mapám přistupujícímu objektu.|
|[db_column](db-column.md)|Váže zadaný sloupec na sadu řádků.|
|[db_command](db-command.md)|Spustí příkaz OLE DB.|
|[db_param](db-param.md)|Přidruží zadanou členskou proměnnou ke vstupnímu nebo výstupnímu parametru.|
|[db_source](db-source.md)|Vytvoří a zapouzdří připojení prostřednictvím poskytovatele ke zdroji dat.|
|[db_table](db-table.md)|Otevře tabulku OLE DB.|
|[default](default-cpp.md)|Indikuje, že vlastní nebo odesílající pole definované v rámci třídy typu coclass představuje výchozí rozhraní programovatelnosti.|
|[defaultbind](defaultbind.md)|Označuje jedinou vlastnost s možností vazby, která nejlépe představuje objekt.|
|[defaultcollelem](defaultcollelem.md)|Používá se pro Visual Basic optimalizaci kódu.|
|[defaultvalue](defaultvalue.md)|Umožňuje specifikaci výchozí hodnoty pro typový volitelný parametr.|
|[defaultvtable](defaultvtable.md)|Definuje rozhraní jako výchozí rozhraní vtable pro ovládací prvek.|
|[dispinterface](dispinterface.md)|Umístí rozhraní do souboru. idl jako odesílající rozhraní.|
|[displaybind](displaybind.md)|Označuje vlastnost, která se má uživateli zobrazit jako vazba.|
|[dual](dual.md)|Umístí rozhraní do souboru. idl jako duální rozhraní.|
|[emitidl](emitidl.md)|Určuje, zda budou všechny následné atributy IDL zpracovány a umístěny do generovaného souboru IDL.|
|[entry](entry.md)|Určuje exportovanou funkci nebo konstantu v modulu určením vstupního bodu v knihovně DLL.|
|[event_receiver](event-receiver.md)|Vytvoří přijímač událostí.|
|[event_source](event-source.md)|Vytvoří zdroj události.|
|[export](export.md)|Způsobí, že datová struktura bude umístěna v souboru. idl.|
|[first_is](first-is.md)|Určuje index prvního prvku pole, který se má přenést.|
|[helpcontext](helpcontext.md)|Určuje ID kontextu, které uživateli umožňuje zobrazit informace o tomto prvku v souboru Help.|
|[helpfile](helpfile.md)|Nastaví název souboru s nápovědu pro knihovnu typů.|
|[helpstring](helpstring.md)|Určuje ID tématu nápovědy v souboru HLP nebo CHM.|
|[helpstringdll](helpstringdll.md)|Určuje název knihovny DLL, která se má použít k provedení vyhledávání řetězců v dokumentu (lokalizace).|
|[hidden](hidden.md)|Označuje, že položka existuje, ale neměla by se zobrazovat v prohlížeči orientovaném na uživatele.|
|[id](id.md)|Určuje DISPID pro členskou funkci (buď vlastnost nebo metoda, v rozhraní nebo odesílajícím rozhraní).|
|[idl_module](idl-module.md)|Určuje vstupní bod v knihovně DLL.|
|[idl_quote](idl-quote.md)|Umožňuje použít atributy nebo konstrukce IDL, které nejsou podporovány v aktuální verzi vizuálu C++.|
|[iid_is](iid-is.md)|Určuje IID rozhraní modelu COM, na které odkazoval ukazatel rozhraní.|
|[immediatebind](immediatebind.md)|Označuje, že se bude databáze okamžitě informovat o všech změnách vlastnosti objektu vázaného na data.|
|[implements](implements-cpp.md)|Určuje odesílající rozhraní, která musí být členy coclass třídy IDL.|
|[implements_category](implements-category.md)|Určuje implementované kategorie komponent pro třídu.|
|[import](import.md)|Určuje jiný soubor. idl,. odl nebo hlavičkový soubor obsahující definice, na které chcete odkazovat z hlavního souboru. idl.|
|[importidl](importidl.md)|Vloží zadaný soubor. idl do vygenerovaného souboru IDL.|
|[importlib](importlib.md)|Vytvoří typy, které již byly zkompilovány do jiné knihovny typů, které jsou k dispozici pro vytvoření knihovny typů.|
|[in](in-cpp.md)|Označuje, že parametr má být předán z volající procedury do volané procedury.|
|[include](include-cpp.md)|Určuje jeden nebo více hlavičkových souborů, které mají být zahrnuty do vygenerovaného souboru IDL.|
|[includelib](includelib-cpp.md)|Způsobí, že soubor. idl nebo. h bude zahrnut do generovaného souboru IDL.|
|[last_is](last-is.md)|Určuje index posledního elementu pole, který se má přenést.|
|[lcid](lcid.md)|Umožňuje předat identifikátor národního prostředí do funkce.|
|[length_is](length-is.md)|Určuje počet prvků pole, které mají být přeneseny.|
|[library_block](library-block.md)|Umístí konstrukci do bloku knihovny souboru. idl.|
|[licensed](licensed.md)|Označuje, že třída typu coclass, na kterou se vztahuje, je licencovaná a je nutné ji vytvořit pomocí `IClassFactory2`.|
|[local](local-cpp.md)|Umožňuje použití kompilátoru MIDL jako generátoru hlaviček při použití v hlavičce rozhraní. Při použití v individuální funkci určí místní proceduru, pro kterou nejsou vygenerována žádná zástupné procedury.|
|[max_is](max-is.md)|Určuje maximální hodnotu pro platný index pole.|
|[module](module-cpp.md)|Definuje blok knihovny v souboru. idl.|
|[ms_union](ms-union.md)|Řídí zarovnání reprezentace dat v síti pro nezapouzdřené sjednocení.|
|[no_injected_text](no-injected-text.md)|Zabraňuje kompilátoru v vkládání kódu v důsledku použití atributu.|
|[nonbrowsable](nonbrowsable.md)|Indikuje, že by se člen rozhraní neměl zobrazovat v prohlížeči vlastností.|
|[noncreatable](noncreatable.md)|Definuje objekt, který nemůže být vytvořen sám sebou.|
|[nonextensible](nonextensible.md)|Určuje, že implementace `IDispatch` zahrnuje pouze vlastnosti a metody uvedené v popisu rozhraní a nelze je rozšířit o další členy v době běhu.|
|[object](object-cpp.md)|Identifikuje vlastní rozhraní; synonymum s vlastním atributem.|
|[odl](odl.md)|Identifikuje rozhraní jako rozhraní jazyka Description Language (ODL).|
|[oleautomation](oleautomation.md)|Označuje, že rozhraní je kompatibilní s automatizací.|
|[optional](optional-cpp.md)|Určuje volitelný parametr členské funkce.|
|[out](out-cpp.md)|Identifikuje parametry ukazatele, které se vracejí z volané procedury do volající procedury (ze serveru do klienta).|
|[pointer_default](pointer-default.md)|Určuje výchozí atribut ukazatele pro všechny ukazatele s výjimkou ukazatelů nejvyšší úrovně, které se zobrazují v seznamech parametrů.|
|[pragma](pragma.md)|Vygeneruje zadaný řetězec bez znaků uvozovky do generovaného souboru. idl.|
|[progid](progid.md)|Určuje identifikátor ProgID pro objekt modelu COM.|
|[propget](propget.md)|Určuje funkci přistupujícího objektu vlastnosti (Get).|
|[propput](propput.md)|Určuje funkci nastavení vlastnosti.|
|[propputref](propputref.md)|Určuje funkci nastavení vlastnosti, která používá odkaz namísto hodnoty.|
|[ptr](ptr.md)|Určí ukazatel jako úplný ukazatel.|
|[public](public-cpp-attributes.md)|Zajistí, že definice typedef přejde do knihovny typů i v případě, že není odkazována ze souboru. idl.|
|[range](range-cpp.md)|Určuje rozsah přípustných hodnot pro argumenty nebo pole, jejichž hodnoty jsou nastaveny v době běhu.|
|[rdx](rdx.md)|Vytvoří nebo upraví klíč registru.|
|[readonly](readonly-cpp.md)|Zakáže přiřazení proměnné.|
|[ref](ref-cpp.md)|Identifikuje ukazatel odkazu.|
|[registration_script](registration-script.md)|Provede zadaný registrační skript.|
|[requestedit](requestedit.md)|Označuje, že vlastnost podporuje oznámení `OnRequestEdit`.|
|[requires_category](requires-category.md)|Určuje požadované kategorie komponent pro třídu.|
|[restricted](restricted.md)|Určuje, že knihovnu nebo člen modulu, rozhraní nebo odesílajícího rozhraní nelze volat libovolně.|
|[retval](retval.md)|Určuje parametr, který přijímá vrácenou hodnotu člena.|
|[satype](satype.md)|Určuje datový typ `SAFEARRAY`.|
|[size_is](size-is.md)|Určuje velikost paměti přidělené pro bodová ukazatele, velikost ukazatelů na velikost ukazatelů a jedno nebo multidimenzionální pole.|
|[source](source-cpp.md)|Označuje, že člen třídy, vlastnosti nebo metody je zdrojem událostí.|
|[string](string-cpp.md)|Označuje, že jednorozměrné **znaky**, **wchar_t**, `byte`nebo ekvivalentní pole nebo ukazatel na takové pole musí být považovány za řetězec.|
|[support_error_info](support-error-info.md)|Podporuje zasílání zpráv o chybách pro cílový objekt.|
|[switch_is](switch-is.md)|Určuje výraz nebo identifikátor fungující jako Discriminant sjednocení, který vybírá člena sjednocení.|
|[switch_type](switch-type.md)|Určuje typ proměnné používané jako Discriminant sjednocení.|
|[synchronize](synchronize.md)|Synchronizuje přístup k metodě.|
|[threading](threading-cpp.md)|Určuje model dělení na vlákna pro objekt modelu COM.|
|[transmit_as](transmit-as.md)|Instruuje kompilátor, aby přidružil prezentovaný typ, který aplikace klienta a serveru zpracovává, s předaným typem.|
|[uidefault](uidefault.md)|Označuje, že člen informací o typu je výchozím členem pro zobrazení v uživatelském rozhraní.|
|[unique](unique-cpp.md)|Určuje jedinečný ukazatel.|
|[usesgetlasterror](usesgetlasterror.md)|Říká volajícímu, že pokud při volání této funkce dojde k chybě, volající může poté volat `GetLastError` pro načtení kódu chyby.|
|[uuid](uuid-cpp-attributes.md)|Určuje jedinečné ID pro třídu nebo rozhraní.|
|[v1_enum](v1-enum.md)|Směruje, že zadaný typ výčtu se přenáší jako 32á entita, nikoli jako 16bitové výchozí hodnoty.|
|[vararg](vararg.md)|Určuje, že funkce přebírají proměnlivý počet argumentů.|
|[version](version-cpp.md)|Identifikuje konkrétní verzi z více verzí rozhraní nebo třídy.|
|[vi_progid](vi-progid.md)|Určuje formu ProgID nezávislou na verzi.|
|[wire_marshal](wire-marshal.md)|Určuje datový typ, který se použije pro přenos místo datového typu specifického pro aplikaci.|

## <a name="see-also"></a>Viz také

[Atributy C++ pro COM a .NET](cpp-attributes-com-net.md)<br/>
[Atributy podle skupin](attributes-by-group.md)<br/>
[Atributy podle použití](attributes-by-usage.md)
