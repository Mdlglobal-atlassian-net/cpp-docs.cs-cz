---
title: SQL | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- database classes [C++], SQL statements
- SQL [C++]
- SQL [C++], ODBC
- ODBC [C++], SQL implementation
ms.assetid: e3923bc4-b317-4e0b-afd8-3cd403eb0faf
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0c4283e73b800ac0fd4d448d5137372807f893d5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="sql"></a>SQL
SQL (Structured Query Language) je způsob, jak komunikovat s relační databázi, která umožňuje definovat, dotaz, úpravě a řídit data. Pomocí syntaxe jazyka SQL, můžete vytvořit příkaz, který extrahuje záznamy podle zadaných kritérií.  
  
> [!NOTE]
>  Tyto informace platí pro třídy MFC rozhraní ODBC. Pokud pracujete s tříd MFC rozhraní DAO, najdete v tématu porovnání z Microsoft Jet Database Engine SQL a ANSI SQL v nápovědě rozhraní DAO.  
  
 SQL příkazy začínají – klíčové slovo slovesem, například **vytvořit** nebo **vyberte**. SQL je velmi výkonný jazyk; jediný příkaz může ovlivnit celou tabulku.  
  
 Existuje mnoho verzí SQL, každý vyvinuté pomocí konkrétní databázového systému v paměti. Databázové třídy MFC rozpoznat sadu příkazů SQL, které odpovídá X / otevřít a SQL přístup skupiny běžné aplikace prostředí (CAE) SQL konceptu specifikace (1991). Informace o syntaxi těchto příkazech najdete v tématu v dodatku C *ODBC SDK* *referenční informace pro programátory* na disku CD knihovny MSDN.  
  
 Toto téma vysvětluje:  
  
-   [Vztah mezi ODBC a jazyku SQL](#_core_open_database_connectivity_.28.odbc.29).  
  
-   [Nejběžnější klíčová slova SQL používá databázové třídy](#_core_the_database_classes).  
  
-   [Jak použít databázové třídy SQL](#_core_how_the_database_classes_use_sql).  
  
##  <a name="_core_open_database_connectivity_.28.odbc.29"></a>Open Database Connectivity (ODBC)  
 Databázové třídy jsou implementované s rozhraním ODBC, která používá SQL v volání úrovni rozhraní namísto vložení příkazů SQL v kódu. ODBC používá ke komunikaci s SQL [zdroj dat](../../data/odbc/data-source-odbc.md) prostřednictvím ovladače ODBC. Tyto ovladače interpretovat SQL a přeloží ji, případně pro použití s formátem konkrétní databáze, jako je například Microsoft Access. Další informace o tom, jak ODBC používá SQL najdete v tématu [ODBC](../../data/odbc/odbc-basics.md) a sady SDK rozhraní ODBC *referenční informace pro programátory* na disku CD knihovny MSDN.  
  
##  <a name="_core_the_database_classes"></a>Databázové třídy  
 Databázové třídy jsou navrženy tak, abyste mohli upravit a aktualizovat data v existující [zdroj dat](../../data/odbc/data-source-odbc.md). [Průvodce aplikací knihovny MFC](../../mfc/reference/database-support-mfc-application-wizard.md), [průvodce příjemcem knihovny MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) (přístupných prostřednictvím **přidat třídu**), a databázové třídy sestavují většinu příkazů SQL pro vás.  
  
 Databázové třídy použijte část SQL známé jako jazyk Data manipulaci (DML). Tyto příkazy umožňují pracovat s nebo její část zdroje dat, přidat nové záznamy, upravit záznamy a odstranit záznamy. Následující tabulka uvádí nejběžnější klíčová slova SQL a způsobů, jak použít databázové třídy je.  
  
### <a name="some-common-sql-keywords"></a>Některé běžné SQL klíčová slova  
  
|SQL – klíčové slovo|Průvodci a databázové třídy použít|  
|-----------------|---------------------------------------------|  
|**SELECT**|K identifikaci, které tabulky a sloupce ve zdroji dat mají být použita.|  
|**WHERE**|Pokud chcete použít filtr, který zúží výběr.|  
|**ORDER BY**|Chcete použít řazení pro sady záznamů.|  
|**VLOŽENÍ**|Přidání nových záznamů do sady záznamů.|  
|**ODSTRANIT**|Při odstraňování záznamů z sady záznamů.|  
|**AKTUALIZACE**|Chcete-li upravit polí záznamu.|  
  
 Kromě toho rozpoznají databázové třídy ODBC **volání** příkazy, které můžete použít pro volání předdefinovaný dotaz (nebo uložené proceduře) pro některé zdroje dat. Ovladač ODBC databáze interpretuje tyto příkazy a nahradí příkaz, který je vhodný pro každý databázového systému.  
  
> [!NOTE]
>  Ne všechny systémy DBMS podporu **volání** příkazy.  
  
 Pokud třídy nemůže rozpoznat uživatelem dodaný příkaz v `CRecordset::Open`, interpretuje se to jako název tabulky.  
  
 Další informace o tom, jak rozhraní framework vytvoří příkazy SQL, najdete v části [sada záznamů: Jak sady záznamů vyberte záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) a [SQL: přizpůsobení vaše SQL příkazu záznamů (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).  
  
 Databáze SQL pomocí datové typy, které jsou podobné těm, které jsou používány C a C++. Informace o těchto podobnost, najdete v části [SQL: SQL a datové typy C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).  
  
 Můžete najít další informace o SQL, včetně seznam podporovaných příkazů jazyka SQL, datové typy, SQL základní gramatiky a čtení seznam doporučených publikací o SQL, *ODBC SDK* *referenční informace pro programátory*  na disku CD knihovny MSDN.  
  
##  <a name="_core_how_the_database_classes_use_sql"></a>Jak použít databázové třídy SQL  
 Sady záznamů, které je odvozena od třídy databáze používat pro komunikaci se zdroji dat rozhraní ODBC a rozhraní ODBC načte záznamy ze zdroje dat pomocí odesílání příkazů SQL. Toto téma popisuje vztah mezi třídami databází a SQL.  
  
 Sady záznamů vytvoří sestavením částí do jednoho příkazu jazyka SQL do příkazu jazyka SQL `CString`. Řetězec sestavený jako **vyberte** příkaz, který vrací sadu záznamů.  
  
 Při volání sady záznamů rozhraní ODBC pro odeslání příkazu SQL pro zdroj dat, správce ovladačů ODBC předá příkaz ovladač ODBC a ovladače, odešle ji do základní databázového systému. Databázového systému vrátí výslednou sadu záznamů a ovladač ODBC vrátí záznamy do aplikace. Databázové třídy nechat program přístup do sady výsledků v C++ třídu bezpečnost typů získané z `CRecordset`.  
  
 Následující témata obsahují další informace o tom, jak použít databázové třídy SQL:  
  
-   [SQL: Přizpůsobení příkazu SQL sady záznamů (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)  
  
-   [SQL: Datové typy SQL a C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)  
  
-   [SQL: Přímá volání SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)  
  
## <a name="see-also"></a>Viz také  
 [Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)   
 [ODBC – základy](../../data/odbc/odbc-basics.md)