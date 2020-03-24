---
title: Atributy metody (C++ com)
ms.date: 10/02/2018
helpviewer_keywords:
- method attributes
- attributes [C++/CLI], reference topics
ms.assetid: b2313352-480d-488b-8c35-6242ffd3a549
ms.openlocfilehash: c9823869be96f53a3c4fbc36c7b56e1bea0a1303
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166767"
---
# <a name="method-attributes"></a>Atributy metody

Následující atributy se vztahují na metody ve třídě, kotřídě nebo rozhraní.

|Atribut|Popis|
|---------------|-----------------|
|[bindable](bindable.md)|Označuje, že vlastnost podporuje datové vazby.|
|[call_as](call-as.md)|Umožňuje mapování nevzdáleně funkční funkce na vzdálenou funkci.|
|[custom](custom-cpp.md)|Umožňuje definovat vlastní atribut.|
|[db_column](db-column.md)|Váže zadaný sloupec na sadu řádků.|
|[db_command](db-command.md)|Vytvoří příkaz OLE DB.|
|[db_param](db-param.md)|Přidruží zadanou členskou proměnnou ke vstupnímu nebo výstupnímu parametru a naomezuje proměnnou.|
|[db_source](db-source.md)|Vytvoří připojení ke zdroji dat.|
|[db_table](db-table.md)|Otevře tabulku OLE DB.|
|[defaultbind](defaultbind.md)|Označuje jedinou vlastnost s možností vazby, která nejlépe představuje objekt.|
|[defaultcollelem](defaultcollelem.md)|Používá se pro Visual Basic optimalizaci kódu.|
|[displaybind](displaybind.md)|Označuje vlastnost, která se má uživateli zobrazit jako vazba.|
|[helpcontext](helpcontext.md)|Určuje ID kontextu, které uživateli umožňuje zobrazit informace o tomto prvku v souboru **help** .|
|[helpfile](helpfile.md)|Nastaví název souboru s **nápovědu** pro knihovnu typů.|
|[helpstring](helpstring.md)|Určuje řetězec znaků, který se používá k popisu prvku, na který se vztahuje.|
|[helpstringcontext](helpstringcontext.md)|Určuje ID tématu nápovědy v souboru HLP nebo CHM.|
|[helpstringdll](helpstringdll.md)|Určuje název knihovny DLL, která se má použít k provedení vyhledávání řetězců v dokumentu (lokalizace).|
|[hidden](hidden.md)|Označuje, že položka existuje, ale neměla by se zobrazovat v prohlížeči orientovaném na uživatele.|
|[id](id.md)|Určuje DISPID pro členskou funkci (buď vlastnost nebo metoda, v rozhraní nebo odesílajícím rozhraní).|
|[immediatebind](immediatebind.md)|Označuje, že se bude databáze okamžitě informovat o všech změnách vlastnosti objektu vázaného na data.|
|[in](in-cpp.md)|Označuje, že parametr má být předán z volající procedury do volané procedury.|
|[local](local-cpp.md)|Umožňuje použití kompilátoru MIDL jako generátoru hlaviček při použití v hlavičce rozhraní. Při použití v individuální funkci určí místní proceduru, pro kterou nejsou vygenerována žádná zástupné procedury.|
|[nonbrowsable](nonbrowsable.md)|Indikuje, že by se člen rozhraní neměl zobrazovat v prohlížeči vlastností.|
|[propget](propget.md)|Určuje funkci přistupujícího objektu vlastnosti.|
|[propput](propput.md)|Určuje funkci nastavení vlastností.|
|[propputref](propputref.md)|Určuje funkci nastavení vlastností, která používá odkaz namísto hodnoty.|
|[ptr](ptr.md)|Určí ukazatel jako úplný ukazatel.|
|[range](range-cpp.md)|Určuje rozsah přípustných hodnot pro argumenty nebo pole, jejichž hodnoty jsou nastaveny v době běhu.|
|[requestedit](requestedit.md)|Označuje, že vlastnost podporuje oznámení `OnRequestEdit`.|
|[restricted](restricted.md)|Určuje, že člen modulu, rozhraní nebo odesílajícího rozhraní nelze volat libovolně.|
|[satype](satype.md)|Určuje datový typ struktury `SAFEARRAY`.|
|[source](source-cpp.md)|Určuje zdrojová rozhraní ovládacího prvku pro body připojení třídy. U vlastnosti nebo metody atribut `source` označuje, že člen vrátí objekt nebo VARIANTu, který je zdrojem událostí.|
|[synchronize](synchronize.md)|Synchronizuje přístup k cílové metodě.|
|[vararg](vararg.md)|Určuje, že funkce přebírají proměnlivý počet argumentů.|

## <a name="see-also"></a>Viz také

[Atributy podle použití](attributes-by-usage.md)
