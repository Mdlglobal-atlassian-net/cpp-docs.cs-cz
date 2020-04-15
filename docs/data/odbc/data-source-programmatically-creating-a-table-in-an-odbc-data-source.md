---
title: Programově vytvoření tabulky ve zdroji dat ODBC
ms.date: 11/04/2016
helpviewer_keywords:
- programmatically creating ODBC tables [C++]
- tables [C++]
- ODBC data sources, creating tables in
- tables [C++], creating programmatically
ms.assetid: 9ca68fb5-c3df-424a-a75c-e3fb01cc1b18
ms.openlocfilehash: 6cf26cad7fe39f374daf371902525087b446658c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358841"
---
# <a name="data-source-programmatically-creating-a-table-in-an-odbc-data-source"></a>Zdroj dat: Programové vytvoření tabulky ve zdroji dat rozhraní ODBC

Toto téma vysvětluje, jak vytvořit tabulku pro `ExecuteSQL` zdroj dat `CDatabase`pomocí členské funkce třídy , předání funkce řetězec, který obsahuje **příkaz CREATE TABLE** SQL.

Obecné informace o zdrojích dat ROZHRANÍ ODBC v knihovně MFC naleznete v [tématu Zdroj dat (ODBC).](../../data/odbc/data-source-odbc.md) Téma [Zdroj dat: Programová konfigurace zdroje dat ODBC](../../data/odbc/data-source-programmatically-configuring-an-odbc-data-source.md) popisuje vytváření zdrojů dat.

Když máte vytvořený zdroj dat, můžete snadno `ExecuteSQL` vytvářet tabulky pomocí členské funkce a příkazu **CREATE TABLE** SQL. Pokud jste například `CDatabase` měli `myDB`objekt s názvem , můžete k vytvoření tabulky použít následující kód knihovny MFC:

```
myDB.ExecuteSQL("CREATE TABLE OFFICES (OfficeID TEXT(4)" ",
                         OfficeName TEXT(10))");
```

Tento příklad kódu vytvoří tabulku s názvem "KANCELÁŘE" v `myDB`připojení zdroje dat aplikace Microsoft Access udržovaného společností ; tabulka obsahuje dvě pole OfficeID a OfficeName.

> [!NOTE]
> Typy polí zadané v příkazu **CREATE TABLE** SQL se mohou lišit v závislosti na ovladači ODBC, který používáte. Program aplikace Microsoft Query (distribuovaný s aplikací Visual C++ 1.5) představuje jeden ze způsobů, jak zjistit, jaké typy polí jsou k dispozici pro zdroj dat. V aplikaci Microsoft Query klepněte na **položku Soubor**, klepněte na **tlačítko Table_Definition**, vyberte tabulku ze zdroje dat a podívejte se na typ zobrazený v poli **Typ** se seznamem. Syntaxe SQL také existuje k vytvoření indexů.

## <a name="see-also"></a>Viz také

[Zdroj dat (ODBC)](../../data/odbc/data-source-odbc.md)
