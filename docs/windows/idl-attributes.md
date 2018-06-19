---
title: IDL – atributy | Microsoft Docs
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
ms.openlocfilehash: 5c522c039a0471240ba319561485e8cc7f348aaa
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33881546"
---
# <a name="idl-attributes"></a>IDL – atributy
Zachování souboru IDL tradičně, znamenalo, že jste měl na:  
  
-   Znát strukturu a syntaxe souboru IDL mohli upravit ho.  
  
-   Spoléhají na průvodce, který by umožňují měnit některé aspekty souboru IDL.  
  
 Nyní můžete upravit .idl souboru v rámci souboru zdrojového kódu, pomocí Visual C++ IDL – atributy. V mnoha případech Visual C++ IDL – atributy mít stejný název jako MIDL atributy. Když jméno Visual C++ IDL atribut a atribut MIDL jsou stejné, znamená to, že uvedení atribut Visual C++ ve zdrojovém kódu souboru dojde v souboru IDL, která obsahuje atribut MIDL jeho namesake. Visual C++ IDL atribut však nemusí být všechny funkce MIDL atributu.  
  
 Pokud se nepoužívá s [COM – atributy](../windows/com-attributes.md), IDL – atributy umožňují definovat rozhraní. Při kompilaci zdrojového kódu atributy slouží k určení generovaného .idl souboru. Při použití s COM – atributy v projektu knihovny ATL, některé IDL atributů, jako je například **třída typu coclass**, způsobit, že kód vložit do projektu.  
  
 Všimněte si, že [idl_quote –](../windows/idl-quote.md) umožňuje použít konstrukce MIDL, které nejsou podporované v aktuální verzi Visual C++. Tato a další atributy, jako [importlib –](../windows/importlib.md) a [includelib –](../windows/includelib-cpp.md) umožňují použít existující soubory .idl v aktuálním projektu Visual C++.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|[aggregatable](../windows/aggregatable.md)|Označuje, že ovládacího prvku se dají agregovat v další ovládací prvek.|  
|[appobject](../windows/appobject.md)|Identifikuje třída typu coclass jako objekt aplikace, který je přidružen k úplné EXE aplikaci a označuje, že funkce a vlastnosti coclass jsou globálně dostupnou v této knihovně typu.|  
|[async_uuid](../windows/async-uuid.md)|Určuje identifikátor UUID, který přesměruje MIDL kompilátoru k definování synchronní a asynchronní verzích rozhraní modelu COM.|  
|[bindable](../windows/bindable.md)|Označuje, že vlastnost podporuje datovou vazbu.|  
|[call_as](../windows/call-as.md)|Umožňuje nonremotable funkce nejde mapovat na vzdálené funkce.|  
|[Případ](../windows/case-cpp.md)|Používá se [switch_type –](../windows/switch-type.md) atribut v spojení.|  
|[coclass](../windows/coclass.md)|Definici do souboru IDL jako třída typu coclass třídy místech.|  
|[control](../windows/control.md)|Určuje, že je uživatelem definovaný typ ovládacího prvku.|  
|[cpp_quote](../windows/cpp-quote.md)|Zadaný řetězec bez znaky uvozovek za sebou vysílá do souboru generovaného záhlaví.|  
|[defaultbind](../windows/defaultbind.md)|Určuje jeden, vazbu vlastnosti, která nejlépe představuje objekt.|  
|[defaultcollelem](../windows/defaultcollelem.md)|Používá pro optimalizaci kód jazyka Visual Basic.|  
|[defaultvalue](../windows/defaultvalue.md)|Umožňuje specifikaci výchozí hodnota pro typové volitelný parametr.|  
|[default](../windows/default-cpp.md)|Označuje, že vlastní a odesílající rozhraní definované v rámci coclass představuje výchozí programovatelnosti rozhraní.|  
|[defaultvtable](../windows/defaultvtable.md)|Definuje rozhraní jako výchozí vtable rozhraní pro ovládací prvek.|  
|[dispinterface](../windows/dispinterface.md)|Umístí rozhraní v souboru IDL jako rozhraní odesílání.|  
|[displaybind](../windows/displaybind.md)|Určuje vlastnosti, která má být zobrazena uživateli jako vazbu.|  
|[dual](../windows/dual.md)|Umístí rozhraní v souboru IDL jako duální rozhraní.|  
|[entry](../windows/entry.md)|V modulu určením vstupní bod v knihovně DLL Určuje exportované funkce nebo konstanta.|  
|[first_is](../windows/first-is.md)|Určuje index první prvek pole má být přenesen.|  
|[helpcontext](../windows/helpcontext.md)|Určuje Identifikátor kontext, který umožňuje uživateli zobrazit informace o tomto prvku v souboru nápovědy.|  
|[helpfile](../windows/helpfile.md)|Nastaví název souboru nápovědy knihovny typů.|  
|[helpstringcontext](../windows/helpstringcontext.md)|Určuje ID tématu nápovědy v souboru HLP nebo CHM.|  
|[helpstringdll](../windows/helpstringdll.md)|Určuje název knihovny DLL používat k provádění vyhledávací řetězec dokumentu (lokalizace).|  
|[helpstring](../windows/helpstring.md)|Určuje řetězec znaků, který se používá k popisu elementu, na který se vztahuje.|  
|[hidden](../windows/hidden.md)|Určuje, že položka existuje, ale by se neměly zobrazovat v prohlížeči uživatele.|  
|[idl_module](../windows/idl-module.md)|Určuje vstupní bod v knihovně DLL.|  
|[idl_quote](../windows/idl-quote.md)|Umožňuje použít atributy nebo IDL vytvoří, které nejsou podporovány v aktuální verzi Visual C++.|  
|[id](../windows/id.md)|Určuje DISPID pro členské funkce (vlastnost nebo metodu, v rozhraní nebo dispinterface).|  
|[iid_is](../windows/iid-is.md)|Určuje identifikátory IID rozhraní modelu COM, na kterou ukazatele rozhraní odkazuje.|  
|[immediatebind](../windows/immediatebind.md)|Označuje, že databáze bude okamžitě informováni o všechny změny vlastností objektu vázané na data.|  
|[importlib](../windows/importlib.md)|Díky typy, které již byly kompilovány do jiného typu knihovny k dispozici pro knihovny typů vytváří.|  
|[import](../windows/import.md)|Určuje jiný .idl, .odl nebo hlavičce soubor obsahující definice, které chcete odkazovat z hlavní .idl souboru.|  
|[Zahrnout](../windows/include-cpp.md)|Určuje jeden nebo více soubory hlaviček, které mají být zahrnuty v souboru generovaného .idl.|  
|[includelib –](../windows/includelib-cpp.md)|Způsobí, že mají být zahrnuty v souboru generovaného .idl .idl nebo .h soubor.|  
|[in](../windows/in-cpp.md)|Označuje, že parametr je mají být předány z volání procedury volané procedury.|  
|[last_is](../windows/last-is.md)|Určuje index posledním elementem pole přenášet.|  
|[lcid](../windows/lcid.md)|Umožňuje předat funkci identifikátor národního prostředí.|  
|[length_is](../windows/length-is.md)|Určuje počet elementů pole přenášet.|  
|[licensed](../windows/licensed.md)|Označuje, že třída typu coclass, které se má licenci a musí být vytvořena pomocí **IClassFactory2**.|  
|[místní](../windows/local-cpp.md)|Umožňuje použít MIDL kompilátoru jako generátor záhlaví při použití v hlavičce rozhraní. Při použití v jednotlivé funkce, označí místní postupu, pro které jsou generovány žádné zástupných procedur.|  
|[max_is](../windows/max-is.md)|Určuje maximální hodnotu platné pole indexu.|  
|[Modul](../windows/module-cpp.md)|Knihovna bloku definuje v souboru.|  
|[ms_union](../windows/ms-union.md)|Určuje zarovnání reprezentace dat sítě nonencapsulated sjednocení.|  
|[no_injected_text](../windows/no-injected-text.md)|Kompilátor brání vložení kódu v důsledku použití atributu.|  
|[nonbrowsable](../windows/nonbrowsable.md)|Označuje, že člena rozhraní by se neměly zobrazovat v prohlížeči vlastností.|  
|[noncreatable](../windows/noncreatable.md)|Definuje objekt, který nelze vytvořit instanci samostatně.|  
|[nonextensible](../windows/nonextensible.md)|Určuje, že `IDispatch` implementace obsahuje pouze vlastnosti a metody uvedené v popisu rozhraní a nelze ji rozšířit s další členy v době běhu.|  
|[object](../windows/object-cpp.md)|Určuje vlastní rozhraní; shodný s vlastních atributů.|  
|[odl](../windows/odl.md)|Identifikuje rozhraní jako objekt popis jazyk (ODL) rozhraní.|  
|[oleautomation](../windows/oleautomation.md)|Označuje, že rozhraní je kompatibilní s automatizace.|  
|[Volitelné](../windows/optional-cpp.md)|Určuje volitelný parametr členské funkce.|  
|[out](../windows/out-cpp.md)|Identifikuje ukazatel parametry, které jsou vráceny z volané procedury volání procedury (ze serveru do klienta).|  
|[pointer_default](../windows/pointer-default.md)|Určuje výchozí atribut ukazatele pro všechny ukazatele s výjimkou ukazatele nejvyšší úrovně, které se zobrazují v seznamy parametrů.|  
|[pragma](../windows/pragma.md)|Do souboru generovaného .idl vysílá zadaný řetězec bez znaky uvozovek za sebou.|  
|[progid](../windows/progid.md)|Určuje identifikátor ProgID pro objekt COM.|  
|[propget](../windows/propget.md)|Určuje funkce vlastnosti přístupového objektu (get).|  
|[propputref](../windows/propputref.md)|Určuje nastavení funkce vlastnost, která používá odkaz místo hodnotu.|  
|[propput](../windows/propput.md)|Určuje nastavení funkce vlastnost.|  
|[ptr](../windows/ptr.md)|Ukazatel se označí jako úplné ukazatel.|  
|[public](../windows/public-cpp-attributes.md)|Zajišťuje, že definice typu přejde do knihovny typů, i když neodkazuje z v rámci tohoto souboru .idl.|  
|[rozsah](../windows/range-cpp.md)|Určuje rozsah povolených hodnot pro argumenty nebo pole, jejichž hodnoty jsou nastaveny v době běhu.|  
|[readonly](../windows/readonly-cpp.md)|Přiřazení proměnné zakáže.|  
|[ref](../windows/ref-cpp.md)|Identifikuje ukazatel odkaz.|  
|[requestedit](../windows/requestedit.md)|Označuje, že vlastnost podporuje **OnRequestEdit, viz** oznámení.|  
|[restricted](../windows/restricted.md)|Určuje, že knihovna, nebo člen modulu, rozhraní nebo dispinterface nelze volat libovolně.|  
|[retval](../windows/retval.md)|Označí parametr, který obdrží hodnotu vrácenou člena.|  
|[size_is](../windows/size-is.md)|Určuje velikost paměti přidělené velikostí ukazatele, velikost ukazatele na velikosti ukazatele a jedním - nebo vícerozměrná pole.|  
|[Zdroj](../windows/source-cpp.md)|Označuje, že je členem třídy, vlastnosti nebo metody zdroj událostí systému.|  
|[string](../windows/string-cpp.md)|Určuje, že jednorozměrná `char`, `wchar_t`, **bajtů**, nebo ekvivalentní pole nebo má ukazatel na takové pole musí být považované za řetězec.|  
|[switch_is](../windows/switch-is.md)|Určuje výraz nebo identifikátor, který funguje jako union discriminant, která vybere položku členů sjednocení.|  
|[switch_type](../windows/switch-type.md)|Určuje typ proměnnou použít jako union discriminant.|  
|[transmit_as](../windows/transmit-as.md)|Dá pokyn kompilátoru k vidění typu, které klientské a serverové aplikace manipulaci, přidružení přenášená typu.|  
|[uidefault](../windows/uidefault.md)|Označuje, že je člen informace typu výchozího člena pro zobrazení v uživatelském rozhraní.|  
|[Jedinečné](../windows/unique-cpp.md)|Určuje jedinečný ukazatel.|  
|[usesgetlasterror](../windows/usesgetlasterror.md)|Informuje volající, pokud dojde k chybě při volání této funkce, volající potom může volat `GetLastError` načíst kód chyby.|  
|[uuid](../windows/uuid-cpp-attributes.md)|Určuje jedinečné ID pro třídy nebo rozhraní.|  
|[v1_enum](../windows/v1-enum.md)|Přesměruje, že zadaného výčtového typu předávají jako 32bitová verze entity, nikoli výchozí 16 bitů.|  
|[vararg](../windows/vararg.md)|Určuje, že funkce trvat proměnný počet argumentů.|  
|[vi_progid](../windows/vi-progid.md)|Určuje nezávislé na verzi forma identifikátor ProgID.|  
|[wire_marshal](../windows/wire-marshal.md)|Určuje datový typ, který se použije pro přenos místo specifické pro aplikaci datového typu.|  
  
## <a name="see-also"></a>Viz také  
 [Atributy podle skupin](../windows/attributes-by-group.md)   
 [Atribut omezení](http://msdn.microsoft.com/en-us/6e6c4329-f667-4869-b991-cbe9cb7a8f61)