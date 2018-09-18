---
title: Programové vytvoření tabulky ve zdroji dat rozhraní ODBC | Dokumentace Microsoftu
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
ms.openlocfilehash: b4db77aae6050f5612c7da14c061e49db142669e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106009"
---
# <a name="data-source-programmatically-creating-a-table-in-an-odbc-data-source"></a>Zdroj dat: Programové vytvoření tabulky ve zdroji dat rozhraní ODBC

Toto téma vysvětluje, jak vytvořit tabulku pro vaše data zdroj, pomocí `ExecuteSQL` členské funkce třídy `CDatabase`, předáním funkci, která obsahuje řetězec **CREATE TABLE** příkaz jazyka SQL.  
  
Obecné informace o zdrojích dat rozhraní ODBC v prostředí MFC naleznete v tématu [datové zdroje (ODBC)](../../data/odbc/data-source-odbc.md). V tématu [zdroj dat: programové nakonfigurování zdroje dat ODBC](../../data/odbc/data-source-programmatically-configuring-an-odbc-data-source.md) popisuje vytváření datového zdroje.  
  
Až budete mít zdroj dat navázat, můžete snadno vytvářet tabulky pomocí `ExecuteSQL` členské funkce a **CREATE TABLE** příkaz jazyka SQL. Pokud jste měli třeba `CDatabase` objektu s názvem `myDB`, můžete použít následující kód knihovny MFC vytvořte tabulku:  
  
```  
myDB.ExecuteSQL("CREATE TABLE OFFICES (OfficeID TEXT(4)" ",   
                         OfficeName TEXT(10))");  
```  
  
Tento příklad kódu vytvoří tabulky nazvané "Pobočky" ve zdroji dat Microsoft Access ve `myDB`; tabulka obsahuje dvě pole "OfficeID" a "OfficeName."  
  
> [!NOTE]
>  Pole typů uvedených v **CREATE TABLE** příkaz SQL se může lišit podle ovladač rozhraní ODBC, kterou používáte. Program Microsoft Query (distribuovat s jazykem Visual C++ 1.5) je jeden způsob, jak zjistit, jaké typy pole jsou k dispozici pro zdroj dat. V aplikaci Microsoft Query, klikněte na tlačítko **souboru**, klikněte na tlačítko **Table_Definition**, vyberte tabulku ze zdroje dat a podívejte se na typ, který ukazuje **typ** – pole se seznamem. Syntaxe SQL existuje také k vytváření indexů.  
  
## <a name="see-also"></a>Viz také  

[Zdroj dat (ODBC)](../../data/odbc/data-source-odbc.md)