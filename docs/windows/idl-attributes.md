---
title: IDL – atributy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], reference topics
- IDL attributes
- .idl files, attributes
- IDL files, attributes
- .idl files
ms.assetid: 04c596f4-c97b-4952-8053-316678b1d0b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5b4207549a5b9992f3c9ac4f99c0b0cac0275772
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43679892"
---
# <a name="idl-attributes"></a>IDL – atributy

Tradičně udržování souboru IDL znamenalo, že jste měli k:

- Se seznámit se strukturou a syntaxe souboru IDL být schopni ho upravit.

- Spolehněte se na průvodce, který mu umožní můžete upravit některé aspekty souboru IDL.

Nyní můžete upravit soubor .idl z v rámci souboru zdrojového kódu pomocí Visual C++ IDL – atributy. V mnoha případech Visual C++ IDL – atributy mají stejný název jako atributy MIDL. Pokud název Visual C++ IDL atribut a atribut MIDL se shodují, znamená to, uvedení v souboru zdrojového kódu jazyka Visual C++ atribut způsobí souboru IDL, který obsahuje atribut namesake MIDL. Atribut Visual C++ IDL však nemusí poskytnout všechny funkce, které jsou součástí atribut MIDL.

Pokud se nepoužívá s [com – atributy](../windows/com-attributes.md), IDL – atributy umožňují definovat rozhraní. Při kompilaci zdrojového kódu, atributy se používají k definování generovaného souboru. Při použití s projektu ATL COM – atributy, některé IDL – atributy, například `coclass`, způsobit vloženy do projektu kódu.

Všimněte si, že [idl_quote –](../windows/idl-quote.md) umožňuje použít MIDL konstrukce, které nejsou podporovány v aktuální verzi jazyka Visual C++. Tato a další atributy, jako [importlib](../windows/importlib.md) a [includelib](../windows/includelib-cpp.md) dozvíte, jak používat existující soubory .idl v aktuálním projektu Visual C++.

|Atribut|Popis|
|---------------|-----------------|
|[aggregatable](../windows/aggregatable.md)|Označuje, že ovládací prvek se dají agregovat jiný ovládací prvek.|
|[appobject](../windows/appobject.md)|Identifikuje coclass jako objekt aplikace, který je spojen s celou aplikaci EXE a označuje, že funkce a vlastnosti třídy typu coclass jsou globálně k dispozici v této knihovně typů.|
|[async_uuid](../windows/async-uuid.md)|Určuje UUID, který nasměruje definovat synchronní a asynchronní verze rozhraní modelu COM kompilátoru MIDL.|
|[bindable](../windows/bindable.md)|Označuje, že vlastnost podporuje datové vazby.|
|[call_as](../windows/call-as.md)|Povolí funkci nonremotable namapovat na vzdálenou funkci.|
|[případ](../windows/case-cpp.md)|Používá se [switch_type –](../windows/switch-type.md) atribut ve sjednocení.|
|[coclass](../windows/coclass.md)|Definici souboru IDL jako coclass třídy místech.|
|[control](../windows/control.md)|Určuje, jestli je typ uživatelského ovládacího prvku.|
|[cpp_quote](../windows/cpp-quote.md)|Zadaný řetězec bez uvozovek znaků, vysílá do vygenerovaného souboru hlavičky.|
|[defaultbind](../windows/defaultbind.md)|Označuje vlastnost podporující vazby, jednu, která nejlíp reprezentuje objekt.|
|[defaultcollelem](../windows/defaultcollelem.md)|Používá pro optimalizaci kódu jazyka Visual Basic.|
|[defaultvalue](../windows/defaultvalue.md)|Umožňuje specifikace výchozí hodnotu pro zadaný nepovinný parametr.|
|[default](../windows/default-cpp.md)|Označuje, že vlastní nebo dispinterface definované v rámci coclass představuje výchozí programovatelnosti rozhraní.|
|[defaultvtable](../windows/defaultvtable.md)|Definuje rozhraní jako výchozího rozhraní vtable pro ovládací prvek.|
|[dispinterface](../windows/dispinterface.md)|Umístí rozhraní v souboru IDL jako rozhraní odbavení.|
|[displaybind](../windows/displaybind.md)|Určuje vlastnost, která má být zobrazena uživateli jako s možností vazby.|
|[dual](../windows/dual.md)|Umístí rozhraní v souboru IDL jako duální rozhraní.|
|[entry](../windows/entry.md)|Určuje exportované funkce nebo konstanta v modulu určením vstupní bod v knihovně DLL.|
|[first_is](../windows/first-is.md)|Určuje index první prvek pole předávají.|
|[helpcontext](../windows/helpcontext.md)|Určuje ID kontextu, který umožňuje uživateli zobrazit informace o tomto prvku v souboru nápovědy.|
|[helpfile](../windows/helpfile.md)|Nastaví název souboru nápovědy pro knihovnu typů.|
|[helpstringcontext](../windows/helpstringcontext.md)|Určuje ID tématu nápovědy HLP nebo CHM souboru.|
|[helpstringdll](../windows/helpstringdll.md)|Určuje název knihovny DLL použít k provádění vyhledání řetězce dokumentu (lokalizace).|
|[helpstring](../windows/helpstring.md)|Určuje řetězec znaků, který se používá k popisu elementu, ke kterému se vztahuje.|
|[hidden](../windows/hidden.md)|Označuje, že položka existuje, ale nebude se zobrazovat v prohlížeči uživatele.|
|[idl_module](../windows/idl-module.md)|Určuje vstupní bod v knihovně DLL.|
|[idl_quote](../windows/idl-quote.md)|Umožňuje používat atributy nebo IDL konstrukce, které nejsou podporované v aktuální verzi jazyka Visual C++.|
|[id](../windows/id.md)|Určuje identifikátor DISPID pro členské funkce (vlastnost nebo metoda v rozhraní nebo dispinterface).|
|[iid_is](../windows/iid-is.md)|Určuje identifikátor IID rozhraní modelu COM, který ukazuje ukazatel rozhraní.|
|[immediatebind](../windows/immediatebind.md)|Označuje, že databázi budou okamžitě oznamovat všechny změny vlastnosti objektu vázané na data.|
|[importlib](../windows/importlib.md)|Díky typy, které již byly zkompilovány do jiné knihovny typů k dispozici pro vytváření knihovny typů.|
|[import](../windows/import.md)|Určuje jiný soubor .idl, .odl nebo záhlaví obsahující definice, které se má odkazovat ze souboru hlavní IDL.|
|[Zahrnout](../windows/include-cpp.md)|Určuje jeden nebo více souborů záhlaví mají být zahrnuty v souboru generovaného IDL.|
|[includelib –](../windows/includelib-cpp.md)|Způsobí, že soubor IDL nebo .h mají být zahrnuty v souboru generovaného IDL.|
|[in](../windows/in-cpp.md)|Označuje, že je parametr předat z volající procedury do volané procedury.|
|[last_is](../windows/last-is.md)|Určuje index posledního prvku pole předávají.|
|[lcid](../windows/lcid.md)|Umožňuje předat funkci identifikátor národního prostředí.|
|[length_is](../windows/length-is.md)|Určuje počet elementů pole předávají.|
|[licensed](../windows/licensed.md)|Označuje, že je licencován coclass, ke kterému se vztahuje a musí být vytvořena pomocí `IClassFactory2`.|
|[místní](../windows/local-cpp.md)|Umožňuje používat v kompilátoru MIDL jako generátor záhlaví při použití v záhlaví rozhraní. Při použití jednotlivých funkcí, určuje místní postupu, pro které jsou generovány žádné zástupné procedury.|
|[max_is](../windows/max-is.md)|Určuje maximální hodnotu pro pole platný index.|
|[Modul](../windows/module-cpp.md)|Bloku knihovny definuje v souboru IDL.|
|[ms_union](../windows/ms-union.md)|Určuje zarovnání reprezentace dat sítě nonencapsulated sjednocení.|
|[no_injected_text](../windows/no-injected-text.md)|Zabrání kompilátoru vkládání kódu v důsledku použití atributu.|
|[nonbrowsable](../windows/nonbrowsable.md)|Označuje, že člen rozhraní, nebude se zobrazovat v prohlížeči vlastností.|
|[noncreatable](../windows/noncreatable.md)|Definuje objekt, který se nedá vytvořit instance samostatně.|
|[nonextensible](../windows/nonextensible.md)|Určuje, že `IDispatch` implementace obsahuje pouze vlastnosti a metody uvedené v popisu rozhraní a nejde prodloužit s další členy v době běhu.|
|[object](../windows/object-cpp.md)|Určuje vlastní rozhraní; synonymem vlastního atributu.|
|[odl](../windows/odl.md)|Označí rozhraní jako objekt popis jazyka (ODL) rozhraní.|
|[oleautomation](../windows/oleautomation.md)|Označuje, že je kompatibilní s automatizací rozhraní.|
|[Volitelné](../windows/optional-cpp.md)|Určuje volitelný parametr pro členské funkce.|
|[out](../windows/out-cpp.md)|Identifikuje parametry ukazatele, které se vracejí z volané procedury do volající procedury (ze serveru do klienta).|
|[pointer_default](../windows/pointer-default.md)|Určuje výchozí atribut ukazatele pro všechny odkazy s výjimkou ukazatelů nejvyšší úrovně, které se zobrazí v seznamech parametrů.|
|[pragma](../windows/pragma.md)|Zadaný řetězec bez uvozovek znaků, vysílá do generovaného souboru.|
|[progid](../windows/progid.md)|Určuje identifikátor pro objekt modelu COM ProgID.|
|[propget](../windows/propget.md)|Určuje funkci, která vlastnost přístupového objektu (get).|
|[propputref](../windows/propputref.md)|Určuje vlastnost nastavení funkci, která používá odkaz namísto hodnotu.|
|[propput](../windows/propput.md)|Určuje funkci, která nastavení vlastnosti.|
|[ptr](../windows/ptr.md)|Ukazatel se označí jako úplné ukazatel.|
|[public](../windows/public-cpp-attributes.md)|Zajišťuje, že definice typu přejde do knihovny typů, i když to neodkazuje v souboru IDL.|
|[rozsah](../windows/range-cpp.md)|Určuje rozsah povolených hodnot pro argumenty nebo pole, jejichž hodnoty jsou nastavené v době běhu.|
|[readonly](../windows/readonly-cpp.md)|Zakáže přiřazení k proměnné.|
|[ref](../windows/ref-cpp.md)|Určuje referenční ukazatel.|
|[requestedit](../windows/requestedit.md)|Označuje, že vlastnost podporuje `OnRequestEdit` oznámení.|
|[restricted](../windows/restricted.md)|Určuje, že knihovna nebo člen modulu, rozhraní nebo dispinterface nejde volat libovolně.|
|[retval](../windows/retval.md)|Označí parametr, který přijímá návratovou hodnotu člena.|
|[size_is](../windows/size-is.md)|Určuje velikost paměti přidělené pro velikosti ukazatele, velikosti ukazatele na velikosti ukazatele a single - nebo vícedimenzionální pole.|
|[Zdroj](../windows/source-cpp.md)|Označuje, že je členem třídy, vlastnosti nebo metody zdroj událostí.|
|[string](../windows/string-cpp.md)|Označuje, že jednorozměrné pole **char**, **wchar_t**, `byte`, nebo ekvivalentní pole nebo ukazatel na takové pole musí být považované za řetězec.|
|[switch_is](../windows/switch-is.md)|Určuje výraz nebo identifikátor, který funguje jako sjednocení discriminant, který vybere člen sjednocení.|
|[switch_type](../windows/switch-type.md)|Určuje typ proměnné použité jako sjednocení discriminant.|
|[transmit_as](../windows/transmit-as.md)|Instruuje kompilátor, aby přidružení uvedený typ, manipulovat s které klientské a serverové aplikace, přenášená typu.|
|[uidefault](../windows/uidefault.md)|Označuje, že informace o člen typu je výchozí člen pro zobrazení v uživatelském rozhraní.|
|[Jedinečný](../windows/unique-cpp.md)|Určuje jedinečný ukazatel.|
|[usesgetlasterror](../windows/usesgetlasterror.md)|Říká volajícímu, že pokud dojde k chybě při volání této funkce, volající provést zavoláním `GetLastError` načíst kód chyby.|
|[uuid](../windows/uuid-cpp-attributes.md)|Určuje jedinečné ID pro třídu nebo rozhraní.|
|[v1_enum](../windows/v1-enum.md)|Určí, že zadaný výčtového typu předávají jako 32-bit entity, spíše než výchozí 16 bitů.|
|[vararg](../windows/vararg.md)|Určuje, že funkce trvat proměnný počet argumentů.|
|[vi_progid](../windows/vi-progid.md)|Určuje verzi nezávislé formu ProgID.|
|[wire_marshal](../windows/wire-marshal.md)|Určuje datový typ, který se použije pro přenos místo typu dat pro konkrétní aplikace.|

## <a name="see-also"></a>Viz také

[Atributy podle skupin](../windows/attributes-by-group.md)  
