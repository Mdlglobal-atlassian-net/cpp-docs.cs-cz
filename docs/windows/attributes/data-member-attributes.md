---
title: Atributy datového členu (C++ COM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- data members [C++], attributes
- data members [C++]
ms.assetid: 95b2397d-1daf-4ae4-8cd0-06956d005b13
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5019503bed9dd0012d8aafc1ade4abd3107335ac
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789365"
---
# <a name="data-member-attributes"></a>Atributy datového členu

Následující atributy se vztahují na datové členy ve třídě, coclass nebo rozhraní.

|Atribut|Popis|
|---------------|-----------------|
|[db_accessor](db-accessor.md)|Skupiny `db_column` atributy, které jsou součástí `IAccessor`– na základě vazby.|
|[db_column](db-column.md)|Zadaný sloupec se váže k dané sadě řádků.|
|[db_command](db-command.md)|Vytvoří příkaz OLE DB.|
|[db_param](db-param.md)|Přidruží zadaný členskou proměnnou vstupní nebo výstupní parametr a odděluje citaci proměnné.|
|[db_source](db-source.md)|Vytvoří připojení ke zdroji dat.|
|[db_table](db-table.md)|Otevře se tabulku OLE DB.|
|[defaultbind](defaultbind.md)|Označuje vlastnost podporující vazby, jednu, která nejlíp reprezentuje objekt.|
|[displaybind](displaybind.md)|Určuje vlastnost, která má být zobrazena uživateli jako s možností vazby.|
|[id](id.md)|Určuje identifikátor DISPID pro členské funkce (vlastnost nebo metoda v rozhraní nebo dispinterface).|
|[rozsah](range-cpp.md)|Určuje rozsah povolených hodnot pro argumenty nebo pole, jejichž hodnoty jsou nastavené v době běhu.|
|[rdx](rdx.md)|Vytvoří klíč registru nebo upraví stávající klíč registru.|
|[readonly](readonly-cpp.md)|Zakáže přiřazení na datový člen.|
|[requestedit](requestedit.md)|Označuje, že vlastnost podporuje `OnRequestEdit` oznámení.|

## <a name="see-also"></a>Viz také

[Atributy podle použití](attributes-by-usage.md)