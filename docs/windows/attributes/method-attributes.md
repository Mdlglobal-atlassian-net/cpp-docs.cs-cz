---
title: Atributy metody (C++ COM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
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
ms.openlocfilehash: 8f5f9af9e302b9346b2bd42acdf1e268a59113f7
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789378"
---
# <a name="method-attributes"></a>Atributy metody

Následující atributy se vztahují na metody ve třídě, coclass nebo rozhraní.

|Atribut|Popis|
|---------------|-----------------|
|[bindable](bindable.md)|Označuje, že vlastnost podporuje datové vazby.|
|[call_as](call-as.md)|Povolí funkci nonremotable namapovat na vzdálenou funkci.|
|[Vlastní](custom-cpp.md)|Umožňuje definovat vlastní atribut.|
|[db_column](db-column.md)|Zadaný sloupec se váže k dané sadě řádků.|
|[db_command](db-command.md)|Vytvoří příkaz OLE DB.|
|[db_param](db-param.md)|Přidruží zadaný členskou proměnnou vstupní nebo výstupní parametr a odděluje citaci proměnné.|
|[db_source](db-source.md)|Vytvoří připojení ke zdroji dat.|
|[db_table](db-table.md)|Otevře se tabulku OLE DB.|
|[defaultbind](defaultbind.md)|Označuje vlastnost podporující vazby, jednu, která nejlíp reprezentuje objekt.|
|[defaultcollelem](defaultcollelem.md)|Používá pro optimalizaci kódu jazyka Visual Basic.|
|[displaybind](displaybind.md)|Určuje vlastnost, která má být zobrazena uživateli jako s možností vazby.|
|[helpcontext](helpcontext.md)|Určuje ID kontextu, který umožňuje uživateli zobrazit informace o tomto elementu v **pomáhají** souboru.|
|[helpfile](helpfile.md)|Nastaví název **pomáhají** soubor pro knihovnu typů.|
|[helpstring](helpstring.md)|Určuje řetězec znaků, který se používá k popisu elementu, ke kterému se vztahuje.|
|[helpstringcontext](helpstringcontext.md)|Určuje ID tématu nápovědy HLP nebo CHM souboru.|
|[helpstringdll](helpstringdll.md)|Určuje název knihovny DLL použít k provádění vyhledání řetězce dokumentu (lokalizace).|
|[hidden](hidden.md)|Označuje, že položka existuje, ale nebude se zobrazovat v prohlížeči uživatele.|
|[id](id.md)|Určuje identifikátor DISPID pro členské funkce (vlastnost nebo metoda v rozhraní nebo dispinterface).|
|[immediatebind](immediatebind.md)|Označuje, že databázi budou okamžitě oznamovat všechny změny vlastnosti objektu vázané na data.|
|[in](in-cpp.md)|Označuje, že je parametr předat z volající procedury do volané procedury.|
|[místní](local-cpp.md)|Umožňuje používat v kompilátoru MIDL jako generátor záhlaví při použití v záhlaví rozhraní. Při použití jednotlivých funkcí, určuje místní postupu, pro které jsou generovány žádné zástupné procedury.|
|[nonbrowsable](nonbrowsable.md)|Označuje, že člen rozhraní, nebude se zobrazovat v prohlížeči vlastností.|
|[propget](propget.md)|Určuje funkci, která přistupujícího objektu vlastnosti.|
|[propput](propput.md)|Určuje funkci, která nastavení vlastnosti.|
|[propputref](propputref.md)|Určuje nastavení vlastnosti funkce, která používá odkaz místo hodnoty.|
|[ptr](ptr.md)|Ukazatel se označí jako úplné ukazatel.|
|[rozsah](range-cpp.md)|Určuje rozsah povolených hodnot pro argumenty nebo pole, jejichž hodnoty jsou nastavené v době běhu.|
|[requestedit](requestedit.md)|Označuje, že vlastnost podporuje `OnRequestEdit` oznámení.|
|[restricted](restricted.md)|Určuje, že modul, rozhraní nebo dispinterface nejde volat libovolně.|
|[satype](satype.md)|Určuje datový typ `SAFEARRAY` struktury.|
|[Zdroj](source-cpp.md)|Určuje třídu rozhraní ovládacího prvku zdroje pro spojovací body. Na vlastnosti nebo metody `source` atribut označuje, že člen vrací objekt nebo VARIANTU, která je zdrojem událostí.|
|[synchronize](synchronize.md)|Synchronizuje přístup k cílové metody.|
|[vararg](vararg.md)|Určuje, že funkce trvat proměnný počet argumentů.|

## <a name="see-also"></a>Viz také

[Atributy podle použití](attributes-by-usage.md)