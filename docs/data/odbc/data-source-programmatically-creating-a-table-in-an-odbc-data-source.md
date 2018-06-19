---
title: Programové vytvoření tabulky ve zdroji dat rozhraní ODBC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- programmatically creating ODBC tables [C++]
- tables [C++]
- ODBC data sources, creating tables in
- tables [C++], creating programmatically
ms.assetid: 9ca68fb5-c3df-424a-a75c-e3fb01cc1b18
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5ea8ddc8e683c0e5f0681bdf98cbddca180e4023
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090507"
---
# <a name="data-source-programmatically-creating-a-table-in-an-odbc-data-source"></a>Zdroj dat: Programové vytvoření tabulky ve zdroji dat rozhraní ODBC
Toto téma vysvětluje, jak vytvořit tabulku pro vaše data zdroje, pomocí `ExecuteSQL` funkce člena třídy `CDatabase`, předávání řetězec, který obsahuje funkce **CREATE TABLE** příkaz jazyka SQL.  
  
 Obecné informace o zdroje dat ODBC v prostředí MFC najdete v tématu [datové zdroje (ODBC)](../../data/odbc/data-source-odbc.md). Téma [zdroj dat: programové nakonfigurování zdroje dat ODBC](../../data/odbc/data-source-programmatically-configuring-an-odbc-data-source.md) popisuje vytvoření datové zdroje.  
  
 Až budete mít stanovený zdroj dat, můžete snadno vytvořit tabulky pomocí `ExecuteSQL` – členská funkce a **CREATE TABLE** příkaz jazyka SQL. Například pokud jste měli `CDatabase` objektu s názvem `myDB`, můžete použít následující kód MFC a vytvořte tabulku:  
  
```  
myDB.ExecuteSQL("CREATE TABLE OFFICES (OfficeID TEXT(4)" ",   
                         OfficeName TEXT(10))");  
```  
  
 Tento příklad kódu vytvoří tabulku nazvané "Pobočky" ve zdroji dat Microsoft Access podle `myDB`; tabulka obsahuje dvě pole "OfficeID" a "OfficeName".  
  
> [!NOTE]
>  Typy polí uvedených v **CREATE TABLE** příkaz jazyka SQL se může lišit podle ovladač ODBC, kterou používáte. Program Microsoft Query (distribuované s Visual C++ 1.5) je jeden způsob, jak zjistit, jaké typy polí jsou k dispozici pro zdroj dat. V aplikaci Microsoft Query, klikněte na tlačítko **soubor**, klikněte na tlačítko **Table_Definition**, vyberte tabulku ze zdroje dat a podívejte se na typy uvedené v **typ** – pole se seznamem. Syntaxe SQL existuje také k vytvoření indexů.  
  
## <a name="see-also"></a>Viz také  
 [Zdroj dat (ODBC)](../../data/odbc/data-source-odbc.md)