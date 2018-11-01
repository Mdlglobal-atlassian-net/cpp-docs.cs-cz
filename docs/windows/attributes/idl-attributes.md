---
title: IDL – atributy (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- IDL attributes
- .idl files [C++], attributes
- IDL files [C++], attributes
- .idl files [C++]
ms.assetid: 04c596f4-c97b-4952-8053-316678b1d0b6
ms.openlocfilehash: 6e88edf114e180a118d0467d5425d16e50d7c216
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593489"
---
# <a name="idl-attributes"></a>IDL – atributy

Tradičně udržování souboru IDL znamenalo, že jste měli k:

- Se seznámit se strukturou a syntaxe souboru IDL být schopni ho upravit.

- Spolehněte se na průvodce, který mu umožní můžete upravit některé aspekty souboru IDL.

Nyní můžete upravit soubor .idl z v rámci souboru zdrojového kódu pomocí Visual C++ IDL – atributy. V mnoha případech Visual C++ IDL – atributy mají stejný název jako atributy MIDL. Pokud název Visual C++ IDL atribut a atribut MIDL se shodují, znamená to, uvedení v souboru zdrojového kódu jazyka Visual C++ atribut způsobí souboru IDL, který obsahuje atribut namesake MIDL. Atribut Visual C++ IDL však nemusí poskytnout všechny funkce, které jsou součástí atribut MIDL.

Pokud se nepoužívá s [com – atributy](com-attributes.md), IDL – atributy umožňují definovat rozhraní. Při kompilaci zdrojového kódu, atributy se používají k definování generovaného souboru. Při použití s projektu ATL COM – atributy, některé IDL – atributy, například `coclass`, způsobit vloženy do projektu kódu.

Všimněte si, že [idl_quote –](idl-quote.md) umožňuje použít MIDL konstrukce, které nejsou podporovány v aktuální verzi jazyka Visual C++. Tato a další atributy, jako [importlib](importlib.md) a [includelib](includelib-cpp.md) dozvíte, jak používat existující soubory .idl v aktuálním projektu Visual C++.

|Atribut|Popis|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Označuje, že ovládací prvek se dají agregovat jiný ovládací prvek.|
|[appobject](appobject.md)|Identifikuje coclass jako objekt aplikace, který je spojen s celou aplikaci EXE a označuje, že funkce a vlastnosti třídy typu coclass jsou globálně k dispozici v této knihovně typů.|
|[async_uuid](async-uuid.md)|Určuje UUID, který nasměruje definovat synchronní a asynchronní verze rozhraní modelu COM kompilátoru MIDL.|
|[bindable](bindable.md)|Označuje, že vlastnost podporuje datové vazby.|
|[call_as](call-as.md)|Povolí funkci nonremotable namapovat na vzdálenou funkci.|
|[case](case-cpp.md)|Používá se [switch_type –](switch-type.md) atribut ve sjednocení.|
|[coclass](coclass.md)|Definici souboru IDL jako coclass třídy místech.|
|[control](control.md)|Určuje, jestli je typ uživatelského ovládacího prvku.|
|[cpp_quote](cpp-quote.md)|Zadaný řetězec bez uvozovek znaků, vysílá do vygenerovaného souboru hlavičky.|
|[defaultbind](defaultbind.md)|Označuje vlastnost podporující vazby, jednu, která nejlíp reprezentuje objekt.|
|[defaultcollelem](defaultcollelem.md)|Používá pro optimalizaci kódu jazyka Visual Basic.|
|[defaultvalue](defaultvalue.md)|Umožňuje specifikace výchozí hodnotu pro zadaný nepovinný parametr.|
|[default](default-cpp.md)|Označuje, že vlastní nebo dispinterface definované v rámci coclass představuje výchozí programovatelnosti rozhraní.|
|[defaultvtable](defaultvtable.md)|Definuje rozhraní jako výchozího rozhraní vtable pro ovládací prvek.|
|[dispinterface](dispinterface.md)|Umístí rozhraní v souboru IDL jako rozhraní odbavení.|
|[displaybind](displaybind.md)|Určuje vlastnost, která má být zobrazena uživateli jako s možností vazby.|
|[dual](dual.md)|Umístí rozhraní v souboru IDL jako duální rozhraní.|
|[entry](entry.md)|Určuje exportované funkce nebo konstanta v modulu určením vstupní bod v knihovně DLL.|
|[first_is](first-is.md)|Určuje index první prvek pole předávají.|
|[helpcontext](helpcontext.md)|Určuje ID kontextu, který umožňuje uživateli zobrazit informace o tomto prvku v souboru nápovědy.|
|[helpfile](helpfile.md)|Nastaví název souboru nápovědy pro knihovnu typů.|
|[helpstringcontext](helpstringcontext.md)|Určuje ID tématu nápovědy HLP nebo CHM souboru.|
|[helpstringdll](helpstringdll.md)|Určuje název knihovny DLL použít k provádění vyhledání řetězce dokumentu (lokalizace).|
|[helpstring](helpstring.md)|Určuje řetězec znaků, který se používá k popisu elementu, ke kterému se vztahuje.|
|[hidden](hidden.md)|Označuje, že položka existuje, ale nebude se zobrazovat v prohlížeči uživatele.|
|[idl_module](idl-module.md)|Určuje vstupní bod v knihovně DLL.|
|[idl_quote](idl-quote.md)|Umožňuje používat atributy nebo IDL konstrukce, které nejsou podporované v aktuální verzi jazyka Visual C++.|
|[id](id.md)|Určuje identifikátor DISPID pro členské funkce (vlastnost nebo metoda v rozhraní nebo dispinterface).|
|[iid_is](iid-is.md)|Určuje identifikátor IID rozhraní modelu COM, který ukazuje ukazatel rozhraní.|
|[immediatebind](immediatebind.md)|Označuje, že databázi budou okamžitě oznamovat všechny změny vlastnosti objektu vázané na data.|
|[importlib](importlib.md)|Díky typy, které již byly zkompilovány do jiné knihovny typů k dispozici pro vytváření knihovny typů.|
|[import](import.md)|Určuje jiný soubor .idl, .odl nebo záhlaví obsahující definice, které se má odkazovat ze souboru hlavní IDL.|
|[include](include-cpp.md)|Určuje jeden nebo více souborů záhlaví mají být zahrnuty v souboru generovaného IDL.|
|[includelib](includelib-cpp.md)|Způsobí, že soubor IDL nebo .h mají být zahrnuty v souboru generovaného IDL.|
|[in](in-cpp.md)|Označuje, že je parametr předat z volající procedury do volané procedury.|
|[last_is](last-is.md)|Určuje index posledního prvku pole předávají.|
|[lcid](lcid.md)|Umožňuje předat funkci identifikátor národního prostředí.|
|[length_is](length-is.md)|Určuje počet elementů pole předávají.|
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
|[propputref](propputref.md)|Určuje vlastnost nastavení funkci, která používá odkaz namísto hodnotu.|
|[propput](propput.md)|Určuje funkci, která nastavení vlastnosti.|
|[ptr](ptr.md)|Ukazatel se označí jako úplné ukazatel.|
|[public](public-cpp-attributes.md)|Zajišťuje, že definice typu přejde do knihovny typů, i když to neodkazuje v souboru IDL.|
|[range](range-cpp.md)|Určuje rozsah povolených hodnot pro argumenty nebo pole, jejichž hodnoty jsou nastavené v době běhu.|
|[readonly](readonly-cpp.md)|Zakáže přiřazení k proměnné.|
|[ref](ref-cpp.md)|Určuje referenční ukazatel.|
|[requestedit](requestedit.md)|Označuje, že vlastnost podporuje `OnRequestEdit` oznámení.|
|[restricted](restricted.md)|Určuje, že knihovna nebo člen modulu, rozhraní nebo dispinterface nejde volat libovolně.|
|[retval](retval.md)|Označí parametr, který přijímá návratovou hodnotu člena.|
|[size_is](size-is.md)|Určuje velikost paměti přidělené pro velikosti ukazatele, velikosti ukazatele na velikosti ukazatele a single - nebo vícedimenzionální pole.|
|[source](source-cpp.md)|Označuje, že je členem třídy, vlastnosti nebo metody zdroj událostí.|
|[string](string-cpp.md)|Označuje, že jednorozměrné pole **char**, **wchar_t**, `byte`, nebo ekvivalentní pole nebo ukazatel na takové pole musí být považované za řetězec.|
|[switch_is](switch-is.md)|Určuje výraz nebo identifikátor, který funguje jako sjednocení discriminant, který vybere člen sjednocení.|
|[switch_type](switch-type.md)|Určuje typ proměnné použité jako sjednocení discriminant.|
|[transmit_as](transmit-as.md)|Instruuje kompilátor, aby přidružení uvedený typ, manipulovat s které klientské a serverové aplikace, přenášená typu.|
|[uidefault](uidefault.md)|Označuje, že informace o člen typu je výchozí člen pro zobrazení v uživatelském rozhraní.|
|[unique](unique-cpp.md)|Určuje jedinečný ukazatel.|
|[usesgetlasterror](usesgetlasterror.md)|Říká volajícímu, že pokud dojde k chybě při volání této funkce, volající provést zavoláním `GetLastError` načíst kód chyby.|
|[uuid](uuid-cpp-attributes.md)|Určuje jedinečné ID pro třídu nebo rozhraní.|
|[v1_enum](v1-enum.md)|Určí, že zadaný výčtového typu předávají jako 32-bit entity, spíše než výchozí 16 bitů.|
|[vararg](vararg.md)|Určuje, že funkce trvat proměnný počet argumentů.|
|[vi_progid](vi-progid.md)|Určuje verzi nezávislé formu ProgID.|
|[wire_marshal](wire-marshal.md)|Určuje datový typ, který se použije pro přenos místo typu dat pro konkrétní aplikace.|

## <a name="see-also"></a>Viz také

[Atributy podle skupin](attributes-by-group.md)
