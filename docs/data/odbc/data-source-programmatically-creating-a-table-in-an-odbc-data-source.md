---
title: Programové vytvoření tabulky ve zdroji dat rozhraní ODBC
ms.date: 11/04/2016
helpviewer_keywords:
- programmatically creating ODBC tables [C++]
- tables [C++]
- ODBC data sources, creating tables in
- tables [C++], creating programmatically
ms.assetid: 9ca68fb5-c3df-424a-a75c-e3fb01cc1b18
ms.openlocfilehash: 61d3f3e39362db27d1e3abc00fa3cb9ea82b86e2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395926"
---
# <a name="data-source-programmatically-creating-a-table-in-an-odbc-data-source"></a>Zdroj dat: Programové vytvoření tabulky ve zdroji dat rozhraní ODBC

Toto téma vysvětluje, jak vytvořit tabulku pro vaše data zdroj, pomocí `ExecuteSQL` členské funkce třídy `CDatabase`, předáním funkci, která obsahuje řetězec **CREATE TABLE** příkaz jazyka SQL.

Obecné informace o zdrojích dat rozhraní ODBC v prostředí MFC naleznete v tématu [datové zdroje (ODBC)](../../data/odbc/data-source-odbc.md). Téma [zdroj dat: Programová konfigurace zdroje dat ODBC](../../data/odbc/data-source-programmatically-configuring-an-odbc-data-source.md) popisuje vytváření datového zdroje.

Až budete mít zdroj dat navázat, můžete snadno vytvářet tabulky pomocí `ExecuteSQL` členské funkce a **CREATE TABLE** příkaz jazyka SQL. Pokud jste měli třeba `CDatabase` objektu s názvem `myDB`, můžete použít následující kód knihovny MFC vytvořte tabulku:

```
myDB.ExecuteSQL("CREATE TABLE OFFICES (OfficeID TEXT(4)" ",
                         OfficeName TEXT(10))");
```

Tento příklad kódu vytvoří tabulky nazvané "Pobočky" ve zdroji dat Microsoft Access ve `myDB`; tabulka obsahuje dvě pole "OfficeID" a "OfficeName."

> [!NOTE]
>  Pole typů uvedených v **CREATE TABLE** příkaz SQL se může lišit podle ovladač rozhraní ODBC, kterou používáte. Program Microsoft Query (distribuovat s jazykem Visual C++ 1.5) je jeden způsob, jak zjistit, jaké typy pole jsou k dispozici pro zdroj dat. V aplikaci Microsoft Query, klikněte na tlačítko **souboru**, klikněte na tlačítko **Table_Definition**, vyberte tabulku ze zdroje dat a podívejte se na typ, který ukazuje **typ** – pole se seznamem. Syntaxe SQL existuje také k vytváření indexů.

## <a name="see-also"></a>Viz také:

[Zdroj dat (ODBC)](../../data/odbc/data-source-odbc.md)