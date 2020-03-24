---
title: Programové vytvoření tabulky ve zdroji dat rozhraní ODBC
ms.date: 11/04/2016
helpviewer_keywords:
- programmatically creating ODBC tables [C++]
- tables [C++]
- ODBC data sources, creating tables in
- tables [C++], creating programmatically
ms.assetid: 9ca68fb5-c3df-424a-a75c-e3fb01cc1b18
ms.openlocfilehash: 25c975560d6a73ce67294d97830b2f5bec9cd635
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213275"
---
# <a name="data-source-programmatically-creating-a-table-in-an-odbc-data-source"></a>Zdroj dat: Programové vytvoření tabulky ve zdroji dat rozhraní ODBC

Toto téma vysvětluje, jak vytvořit tabulku pro zdroj dat pomocí `ExecuteSQL` členské funkce třídy `CDatabase`a předáním funkce řetězec, který obsahuje **Create Table** příkaz SQL.

Obecné informace o zdrojích dat ODBC v knihovně MFC naleznete v tématu [zdroj dat (ODBC)](../../data/odbc/data-source-odbc.md). Téma [zdroj dat: programové nakonfigurování zdroje dat ODBC](../../data/odbc/data-source-programmatically-configuring-an-odbc-data-source.md) popisuje vytváření zdrojů dat.

Pokud máte vytvořený zdroj dat, můžete snadno vytvořit tabulky pomocí členské funkce `ExecuteSQL` a příkazu **Create Table** SQL. Pokud jste například `CDatabase` objekt nazvaný `myDB`, mohli byste pomocí následujícího kódu knihovny MFC vytvořit tabulku:

```
myDB.ExecuteSQL("CREATE TABLE OFFICES (OfficeID TEXT(4)" ",
                         OfficeName TEXT(10))");
```

V tomto příkladu kódu se vytvoří tabulka s názvem "pobočky" v připojení ke zdroji dat Microsoft Access udržované nástrojem `myDB`; tabulka obsahuje dvě pole "OfficeID" a "Office".

> [!NOTE]
>  Typy polí zadané v příkazu jazyka SQL **Create Table** se mohou lišit podle ovladače ODBC, který používáte. Microsoft Query program (distribuováno se sadou C++ Visual 1,5) je jedním ze způsobů, jak zjistit, jaké typy polí jsou k dispozici pro zdroj dat. V Microsoft Query klikněte na **soubor**, klikněte na **Table_Definition**, vyberte tabulku ze zdroje dat a podívejte se na typ uvedený v poli se seznamem **typ** . Syntaxe SQL existuje také k vytváření indexů.

## <a name="see-also"></a>Viz také

[Zdroj dat (ODBC)](../../data/odbc/data-source-odbc.md)
