---
title: Atributy abecedně řazená referenční dokumentace | Dokumentace Microsoftu
ms.custom: index-page
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.attributes
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI]
ms.assetid: fb2216ef-9fbd-44f4-afed-732aa99450e2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 431ca9e88e644bd7a7c38f9ab4a1c3faeab6f9bb
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2018
ms.locfileid: "49328399"
---
# <a name="attributes-alphabetical-reference"></a>Abecedně řazená referenční dokumentace k atributům

Následující atributy jsou k dispozici v kompilátoru C++ společnosti Microsoft:

|Atribut|Popis|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Označuje, že ovládací prvek se dají agregovat jiný ovládací prvek.|
|[aggregates](aggregates.md)|Označuje, že ovládací prvek agreguje cílové třídy.|
|[appobject](appobject.md)|Identifikuje coclass jako objekt aplikace, který je spojen s celou aplikaci EXE a označuje, že funkce a vlastnosti třídy typu coclass jsou globálně k dispozici v této knihovně typů.|
|[async_uuid](async-uuid.md)|Určuje UUID, který nasměruje definovat synchronní a asynchronní verze rozhraní modelu COM kompilátoru MIDL.|
|[attribute](attribute.md)|Umožňuje vytvořit vlastní atribut.|
|[bindable](bindable.md)|Označuje, že vlastnost podporuje datové vazby.|
|[call_as](call-as.md)|Povolí funkci nonremotable namapovat na vzdálenou funkci.|
|[case](case-cpp.md)|Používá se [switch_type –](switch-type.md) atribut ve sjednocení.|
|[coclass](coclass.md)|Vytvoří objekt modelu COM, které můžete implementovat rozhraní modelu COM.|
|[com_interface_entry](com-interface-entry-cpp.md)|Přidá položku do rozhraní COM mapy.|
|[control](control.md)|Určuje, jestli je typ uživatelského ovládacího prvku.|
|[cpp_quote](cpp-quote.md)|Zadaný řetězec bez uvozovek znaků, vysílá do vygenerovaného souboru hlavičky.|
|[custom](custom-cpp.md)|Umožňuje definovat vlastní atributy.|
|[db_accessor](db-accessor.md)|Vytvoří vazbu sloupců v sadě řádků a sváže s odpovídající přístupového objektu map.|
|[db_column](db-column.md)|Zadaný sloupec se váže k dané sadě řádků.|
|[db_command](db-command.md)|Provede příkaz OLE DB.|
|[db_param](db-param.md)|Přidruží zadaný členskou proměnnou vstupní nebo výstupní parametr.|
|[db_source](db-source.md)|Vytvoří a zapouzdřuje připojení prostřednictvím poskytovatele ke zdroji dat.|
|[db_table](db-table.md)|Otevře se tabulku OLE DB.|
|[default](default-cpp.md)|Označuje, že vlastní nebo dispinterface definované v rámci coclass představuje výchozí programovatelnosti rozhraní.|
|[defaultbind](defaultbind.md)|Označuje vlastnost podporující vazby, jednu, která nejlíp reprezentuje objekt.|
|[defaultcollelem](defaultcollelem.md)|Používá pro optimalizaci kódu jazyka Visual Basic.|
|[defaultvalue](defaultvalue.md)|Umožňuje specifikace výchozí hodnotu pro zadaný nepovinný parametr.|
|[defaultvtable](defaultvtable.md)|Definuje rozhraní jako výchozího rozhraní vtable pro ovládací prvek.|
|[dispinterface](dispinterface.md)|Umístí rozhraní v souboru IDL jako rozhraní odbavení.|
|[displaybind](displaybind.md)|Určuje vlastnost, která má být zobrazena uživateli jako s možností vazby.|
|[dual](dual.md)|Umístí rozhraní v souboru IDL jako duální rozhraní.|
|[emitidl](emitidl.md)|Určuje, zda všechny následné IDL – atributy zpracování, který se umístí do generovaného souboru.|
|[entry](entry.md)|Určuje exportované funkce nebo konstanta v modulu určením vstupní bod v knihovně DLL.|
|[event_receiver](event-receiver.md)|Vytvoří přijímače událostí.|
|[event_source](event-source.md)|Vytvoří zdroj událostí.|
|[export](export.md)|Způsobí, že datová struktura budou umístěny v souboru IDL.|
|[first_is](first-is.md)|Určuje index první prvek pole předávají.|
|[helpcontext](helpcontext.md)|Určuje ID kontextu, který umožňuje uživateli zobrazit informace o tomto prvku v souboru nápovědy.|
|[helpfile](helpfile.md)|Nastaví název souboru nápovědy pro knihovnu typů.|
|[helpstring](helpstring.md)|Určuje ID tématu nápovědy HLP nebo CHM souboru.|
|[helpstringdll](helpstringdll.md)|Určuje název knihovny DLL použít k provádění vyhledání řetězce dokumentu (lokalizace).|
|[hidden](hidden.md)|Označuje, že položka existuje, ale nebude se zobrazovat v prohlížeči uživatele.|
|[id](id.md)|Určuje identifikátor DISPID pro členské funkce (vlastnost nebo metoda v rozhraní nebo dispinterface).|
|[idl_module](idl-module.md)|Určuje vstupní bod v knihovně DLL.|
|[idl_quote](idl-quote.md)|Umožňuje používat atributy nebo IDL konstrukce, které nejsou podporované v aktuální verzi jazyka Visual C++.|
|[iid_is](iid-is.md)|Určuje identifikátor IID rozhraní modelu COM, který ukazuje ukazatel rozhraní.|
|[immediatebind](immediatebind.md)|Označuje, že databázi budou okamžitě oznamovat všechny změny vlastnosti objektu vázané na data.|
|[implements](implements-cpp.md)|Určuje odesílajících rozhraních, které se musí být členy třídy typu IDL coclass.|
|[implements_category](implements-category.md)|Určuje kategorie implementované součásti pro třídu.|
|[import](import.md)|Určuje jiný soubor .idl, .odl nebo záhlaví obsahující definice, které se má odkazovat ze souboru hlavní IDL.|
|[importidl](importidl.md)|Vloží zadaný souboru do generovaného souboru.|
|[importlib](importlib.md)|Díky typy, které již byly zkompilovány do jiné knihovny typů k dispozici pro vytváření knihovny typů.|
|[in](in-cpp.md)|Označuje, že je parametr předat z volající procedury do volané procedury.|
|[include](include-cpp.md)|Určuje jeden nebo více souborů záhlaví mají být zahrnuty v souboru generovaného IDL.|
|[includelib](includelib-cpp.md)|Způsobí, že soubor IDL nebo .h mají být zahrnuty v souboru generovaného IDL.|
|[last_is](last-is.md)|Určuje index posledního prvku pole předávají.|
|[lcid](lcid.md)|Umožňuje předat funkci identifikátor národního prostředí.|
|[length_is](length-is.md)|Určuje počet elementů pole předávají.|
|[library_block](library-block.md)|Umístí konstrukci uvnitř bloku knihovny souboru IDL.|
|[licensed](licensed.md)|Označuje, že je licencován coclass, ke kterému se vztahuje a musí být vytvořena pomocí `IClassFactory2`.|
|[local](local-cpp.md)|Umožňuje používat v kompilátoru MIDL jako generátor záhlaví při použití v záhlaví rozhraní. Při použití jednotlivých funkcí, určuje místní postupu, pro které jsou generovány žádné zástupné procedury.|
|[max_is](max-is.md)|Určuje maximální hodnotu pro pole platný index.|
|[module](module-cpp.md)|Bloku knihovny definuje v souboru IDL.|
|[ms_union](ms-union.md)|Určuje zarovnání reprezentace dat sítě nonencapsulated sjednocení.|
|[no_injected_text](no-injected-text.md)|Zabrání kompilátoru vkládání kódu v důsledku použití atributu.|
|[nonbrowsable](nonbrowsable.md)|Označuje, že člen rozhraní, nebude se zobrazovat v prohlížeči vlastností.|
|[noncreatable](noncreatable.md)|Definuje objekt, který se nedá vytvořit instance samostatně.|
|[nonextensible](nonextensible.md)|Určuje, že `IDispatch` implementace obsahuje pouze vlastnosti a metody uvedené v popisu rozhraní a nejde prodloužit s další členy v době běhu.|
|[object](object-cpp.md)|Určuje vlastní rozhraní; synonymem vlastního atributu.|
|[odl](odl.md)|Označí rozhraní jako objekt popis jazyka (ODL) rozhraní.|
|[oleautomation](oleautomation.md)|Označuje, že je kompatibilní s automatizací rozhraní.|
|[optional](optional-cpp.md)|Určuje volitelný parametr pro členské funkce.|
|[out](out-cpp.md)|Identifikuje parametry ukazatele, které se vracejí z volané procedury do volající procedury (ze serveru do klienta).|
|[pointer_default](pointer-default.md)|Určuje výchozí atribut ukazatele pro všechny odkazy s výjimkou ukazatelů nejvyšší úrovně, které se zobrazí v seznamech parametrů.|
|[pragma](pragma.md)|Zadaný řetězec bez uvozovek znaků, vysílá do generovaného souboru.|
|[progid](progid.md)|Určuje identifikátor pro objekt modelu COM ProgID.|
|[propget](propget.md)|Určuje funkci, která vlastnost přístupového objektu (get).|
|[propput](propput.md)|Určuje funkci, která nastavení vlastnosti.|
|[propputref](propputref.md)|Určuje vlastnost nastavení funkci, která používá odkaz namísto hodnotu.|
|[ptr](ptr.md)|Ukazatel se označí jako úplné ukazatel.|
|[public](public-cpp-attributes.md)|Zajišťuje, že definice typu přejde do knihovny typů, i když to neodkazuje v souboru IDL.|
|[range](range-cpp.md)|Určuje rozsah povolených hodnot pro argumenty nebo pole, jejichž hodnoty jsou nastavené v době běhu.|
|[rdx](rdx.md)|Vytvoří nebo změní klíče registru.|
|[readonly](readonly-cpp.md)|Zakáže přiřazení k proměnné.|
|[ref](ref-cpp.md)|Určuje referenční ukazatel.|
|[registration_script](registration-script.md)|Provede zadanou registraci skript.|
|[requestedit](requestedit.md)|Označuje, že vlastnost podporuje `OnRequestEdit` oznámení.|
|[requires_category](requires-category.md)|Určuje požadovanou součást kategorie pro třídu.|
|[restricted](restricted.md)|Určuje, že knihovna nebo člen modulu, rozhraní nebo dispinterface nejde volat libovolně.|
|[retval](retval.md)|Označí parametr, který přijímá návratovou hodnotu člena.|
|[satype](satype.md)|Určuje datový typ `SAFEARRAY`.|
|[size_is](size-is.md)|Určuje velikost paměti přidělené pro velikosti ukazatele, velikosti ukazatele na velikosti ukazatele a single - nebo vícedimenzionální pole.|
|[source](source-cpp.md)|Označuje, že je členem třídy, vlastnosti nebo metody zdroj událostí.|
|[string](string-cpp.md)|Označuje, že jednorozměrné pole **char**, **wchar_t**, `byte`, nebo ekvivalentní pole nebo ukazatel na takové pole musí být považované za řetězec.|
|[support_error_info](support-error-info.md)|Podporuje odesílání sestav chyb pro cílový objekt.|
|[switch_is](switch-is.md)|Určuje výraz nebo identifikátor, který funguje jako sjednocení discriminant, který vybere člen sjednocení.|
|[switch_type](switch-type.md)|Určuje typ proměnné použité jako sjednocení discriminant.|
|[synchronize](synchronize.md)|Synchronizuje přístup k metodě.|
|[threading](threading-cpp.md)|Určuje model vláken pro objekt modelu COM.|
|[transmit_as](transmit-as.md)|Instruuje kompilátor, aby přidružení uvedený typ, manipulovat s které klientské a serverové aplikace, přenášená typu.|
|[uidefault](uidefault.md)|Označuje, že informace o člen typu je výchozí člen pro zobrazení v uživatelském rozhraní.|
|[unique](unique-cpp.md)|Určuje jedinečný ukazatel.|
|[usesgetlasterror](usesgetlasterror.md)|Říká volajícímu, že pokud dojde k chybě při volání této funkce, volající provést zavoláním `GetLastError` načíst kód chyby.|
|[uuid](uuid-cpp-attributes.md)|Určuje jedinečné ID pro třídu nebo rozhraní.|
|[v1_enum](v1-enum.md)|Určí, že zadaný výčtového typu předávají jako 32-bit entity, spíše než výchozí 16 bitů.|
|[vararg](vararg.md)|Určuje, že funkce trvat proměnný počet argumentů.|
|[version](version-cpp.md)|Určuje konkrétní verzi napříč několika verzemi rozhraní nebo tříd.|
|[vi_progid](vi-progid.md)|Určuje verzi nezávislé formu ProgID.|
|[wire_marshal](wire-marshal.md)|Určuje datový typ, který se použije pro přenos místo typu dat pro konkrétní aplikace.|

## <a name="see-also"></a>Viz také

[Atributy C++ pro COM a .NET](cpp-attributes-com-net.md)<br/>
[Atributy podle skupin](attributes-by-group.md)<br/>
[Atributy podle použití](attributes-by-usage.md)