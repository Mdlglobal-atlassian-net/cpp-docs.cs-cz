---
title: Atributy metody | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- method attributes
- attributes [C++/CLI], reference topics
ms.assetid: b2313352-480d-488b-8c35-6242ffd3a549
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 27540db2da7aecbe7a4b70b786bbf05bf608e889
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44317430"
---
# <a name="method-attributes"></a>Atributy metody

Následující atributy se vztahují na metody ve třídě, coclass nebo rozhraní.

|Atribut|Popis|
|---------------|-----------------|
|[bindable](../windows/bindable.md)|Označuje, že vlastnost podporuje datové vazby.|
|[call_as](../windows/call-as.md)|Povolí funkci nonremotable namapovat na vzdálenou funkci.|
|[Vlastní](../windows/custom-cpp.md)|Umožňuje definovat vlastní atribut.|
|[db_column](../windows/db-column.md)|Zadaný sloupec se váže k dané sadě řádků.|
|[db_command](../windows/db-command.md)|Vytvoří příkaz OLE DB.|
|[db_param](../windows/db-param.md)|Přidruží zadaný členskou proměnnou vstupní nebo výstupní parametr a odděluje citaci proměnné.|
|[db_source](../windows/db-source.md)|Vytvoří připojení ke zdroji dat.|
|[db_table](../windows/db-table.md)|Otevře se tabulku OLE DB.|
|[defaultbind](../windows/defaultbind.md)|Označuje vlastnost podporující vazby, jednu, která nejlíp reprezentuje objekt.|
|[defaultcollelem](../windows/defaultcollelem.md)|Používá pro optimalizaci kódu jazyka Visual Basic.|
|[displaybind](../windows/displaybind.md)|Určuje vlastnost, která má být zobrazena uživateli jako s možností vazby.|
|[helpcontext](../windows/helpcontext.md)|Určuje ID kontextu, který umožňuje uživateli zobrazit informace o tomto elementu v **pomáhají** souboru.|
|[helpfile](../windows/helpfile.md)|Nastaví název **pomáhají** soubor pro knihovnu typů.|
|[helpstring](../windows/helpstring.md)|Určuje řetězec znaků, který se používá k popisu elementu, ke kterému se vztahuje.|
|[helpstringcontext](../windows/helpstringcontext.md)|Určuje ID tématu nápovědy HLP nebo CHM souboru.|
|[helpstringdll](../windows/helpstringdll.md)|Určuje název knihovny DLL použít k provádění vyhledání řetězce dokumentu (lokalizace).|
|[hidden](../windows/hidden.md)|Označuje, že položka existuje, ale nebude se zobrazovat v prohlížeči uživatele.|
|[id](../windows/id.md)|Určuje identifikátor DISPID pro členské funkce (vlastnost nebo metoda v rozhraní nebo dispinterface).|
|[immediatebind](../windows/immediatebind.md)|Označuje, že databázi budou okamžitě oznamovat všechny změny vlastnosti objektu vázané na data.|
|[in](../windows/in-cpp.md)|Označuje, že je parametr předat z volající procedury do volané procedury.|
|[místní](../windows/local-cpp.md)|Umožňuje používat v kompilátoru MIDL jako generátor záhlaví při použití v záhlaví rozhraní. Při použití jednotlivých funkcí, určuje místní postupu, pro které jsou generovány žádné zástupné procedury.|
|[nonbrowsable](../windows/nonbrowsable.md)|Označuje, že člen rozhraní, nebude se zobrazovat v prohlížeči vlastností.|
|[propget](../windows/propget.md)|Určuje funkci, která přistupujícího objektu vlastnosti.|
|[propput](../windows/propput.md)|Určuje funkci, která nastavení vlastnosti.|
|[propputref](../windows/propputref.md)|Určuje nastavení vlastnosti funkce, která používá odkaz místo hodnoty.|
|[ptr](../windows/ptr.md)|Ukazatel se označí jako úplné ukazatel.|
|[rozsah](../windows/range-cpp.md)|Určuje rozsah povolených hodnot pro argumenty nebo pole, jejichž hodnoty jsou nastavené v době běhu.|
|[requestedit](../windows/requestedit.md)|Označuje, že vlastnost podporuje `OnRequestEdit` oznámení.|
|[restricted](../windows/restricted.md)|Určuje, že modul, rozhraní nebo dispinterface nejde volat libovolně.|
|[satype](../windows/satype.md)|Určuje datový typ `SAFEARRAY` struktury.|
|[Zdroj](../windows/source-cpp.md)|Určuje třídu rozhraní ovládacího prvku zdroje pro spojovací body. Na vlastnosti nebo metody `source` atribut označuje, že člen vrací objekt nebo VARIANTU, která je zdrojem událostí.|
|[synchronize](../windows/synchronize.md)|Synchronizuje přístup k cílové metody.|
|[vararg](../windows/vararg.md)|Určuje, že funkce trvat proměnný počet argumentů.|

## <a name="see-also"></a>Viz také

[Atributy podle použití](../windows/attributes-by-usage.md)