---
title: SQL
ms.date: 05/09/2019
helpviewer_keywords:
- database classes [C++], SQL statements
- SQL [C++]
- SQL [C++], ODBC
- ODBC [C++], SQL implementation
ms.assetid: e3923bc4-b317-4e0b-afd8-3cd403eb0faf
ms.openlocfilehash: 58c0267728f2b26cf81d048fcf02edd8fc4909ec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212562"
---
# <a name="sql"></a>SQL

SQL (jazyk SQL (Structured Query Language)) je způsob, jak komunikovat s relační databází, která umožňuje definovat, dotazovat, upravovat a řídit data. Pomocí syntaxe SQL můžete vytvořit příkaz, který extrahuje záznamy podle vámi zadaných kritérií.

> [!NOTE]
>  Tyto informace se vztahují na třídy knihovny MFC rozhraní ODBC. Pokud pracujete s třídami knihovny MFC DAO, přečtěte si téma porovnání řešení Microsoft Jet Database Engine SQL a ANSI SQL v nápovědě pro rozhraní DAO.

Příkazy SQL začínají na klíčovém slově, jako je například **Create** nebo **Select**. SQL je velmi výkonný jazyk; jeden příkaz může mít vliv na celou tabulku.

Existuje spousta verzí SQL, z nichž každá se vyvinula s konkrétními systémy DBMS. Třídy databáze knihovny MFC rozpoznávají sadu příkazů SQL, které odpovídají specifikaci SQL konceptu konceptu X/Open a SQL Access Group Common Applications (1991). Informace o syntaxi těchto příkazů naleznete v příloze C v *Referenční příručce programátora* *sady ODBC SDK* na webu MSDN Library.

Toto téma vysvětluje:

- [Vztah mezi rozhraním ODBC a SQL](#_core_open_database_connectivity_.28.odbc.29).

- [Nejběžnější klíčová slova jazyka SQL používaná třídami databáze](#_core_the_database_classes).

- [Jak třídy databáze používají SQL](#_core_how_the_database_classes_use_sql).

##  <a name="open-database-connectivity-odbc"></a><a name="_core_open_database_connectivity_.28.odbc.29"></a>Připojení Open Database (ODBC)

Třídy databáze jsou implementovány pomocí rozhraní ODBC, které používá SQL v rozhraní na úrovni volání namísto vkládání příkazů SQL do kódu. Rozhraní ODBC používá SQL ke komunikaci se [zdrojem dat](../../data/odbc/data-source-odbc.md) prostřednictvím ovladačů rozhraní ODBC. Tyto ovladače interpretují SQL a v případě potřeby ho přeloží pro použití s konkrétním formátem databáze, jako je například Microsoft Access. Další informace o tom, jak rozhraní ODBC používá SQL, najdete v tématu [rozhraní ODBC](../../data/odbc/odbc-basics.md) a *Příručka PROGRAMÁTORA* sady ODBC SDK na disku CD knihovny MSDN.

##  <a name="database-classes"></a><a name="_core_the_database_classes"></a>Databázové třídy

> [!NOTE]
> Průvodce příjemcem knihovny MFC rozhraní ODBC není dostupný v aplikaci Visual Studio 2019 a novějším. Příjemce můžete přesto vytvořit ručně.

Třídy databáze jsou navržené tak, aby vám umožnily manipulovat a aktualizovat data v existujícím [zdroji dat](../../data/odbc/data-source-odbc.md). [Průvodce aplikací knihovny MFC](../../mfc/reference/database-support-mfc-application-wizard.md), [Průvodce příjemcem knihovny MFC rozhraní ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) (k dispozici prostřednictvím příkazu **Přidat třídu**) a databázové třídy sestavují většinu příkazů SQL za vás.

Třídy databáze používají část SQL známou jako jazyk manipulace s daty (DML). Tyto příkazy umožňují pracovat se všemi nebo částmi zdroje dat, přidávat nové záznamy, upravovat záznamy a odstraňovat záznamy. Následující tabulka uvádí nejběžnější klíčová slova jazyka SQL a způsoby, jak je používají databázové třídy.

### <a name="some-common-sql-keywords"></a>Některá společná klíčová slova SQL

|Klíčové slovo SQL|Průvodci a databázové třídy ho používají|
|-----------------|---------------------------------------------|
|**SELECT**|Chcete-li určit, které tabulky a sloupce ve zdroji dat mají být použity.|
|**WHERE**|Chcete-li použít filtr, který zúží výběr.|
|**ORDER BY**|Chcete-li použít pořadí řazení pro sadu záznamů.|
|**INSERT**|K přidání nových záznamů do sady záznamů.|
|**DELETE**|Odstranění záznamů ze sady záznamů.|
|**UPDATE**|Úprava polí záznamu.|

Kromě toho třídy databáze rozpoznávají příkazy **volání** rozhraní ODBC, které lze použít k volání předdefinovaného dotazu (nebo uložené procedury) v některých zdrojích dat. Ovladač databáze rozhraní ODBC tyto příkazy interpretuje a nahrazuje příkaz vhodný pro každý systém DBMS.

> [!NOTE]
>  Ne všechny systémy DBMS podporují příkazy **volání** .

Pokud třídy nerozpoznají uživatelem zadaný příkaz v `CRecordset::Open`, je interpretován jako název tabulky.

Vysvětlení způsobu konstrukce příkazů SQL naleznete v tématu [Sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) a [SQL: Přizpůsobení příkazu SQL sady záznamů (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

Databáze SQL používají datové typy podobné těm, které se používají v C++C a. Diskuzi o těchto podobnostech najdete v tématu [SQL: SQL a C++ datové typy (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).

Další informace o SQL, včetně seznamu podporovaných příkazů SQL, datových typů, gramatiky SQL Core a seznamu pro čtení doporučených publikací o SQL, najdete v tématu *programátor* *sady ODBC SDK* na disku CD knihovny MSDN.

##  <a name="how-the-database-classes-use-sql"></a><a name="_core_how_the_database_classes_use_sql"></a>Jak třídy databáze používají SQL

Sady záznamů, které jsou odvozeny z tříd databáze, používají rozhraní ODBC ke komunikaci se zdrojem dat a rozhraní ODBC načte záznamy ze zdroje dat odesláním příkazů jazyka SQL. Toto téma vysvětluje vztah mezi databázovými třídami a SQL.

Sada záznamů vytvoří příkaz SQL sestavením částí příkazu SQL do `CString`. Řetězec je vytvořen jako příkaz **Select** , který vrací sadu záznamů.

Když sada záznamů volá rozhraní ODBC k odeslání příkazu SQL do zdroje dat, správce ovladačů ODBC předá příkaz ovladači ODBC a ovladač ho pošle základnímu systému DBMS. DBMS vrátí sadu výsledků záznamů a ovladač ODBC vrátí záznamy do aplikace. Třídy databáze umožňují vašemu programu přístup k sadě výsledků v typově bezpečné C++ třídě odvozené z `CRecordset`.

Následující témata obsahují další informace o tom, jak třídy databáze používají SQL:

- [SQL: Přizpůsobení příkazu SQL sady záznamů (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)

- [SQL: Datové typy SQL a C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)

- [SQL: Přímá volání SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)

## <a name="see-also"></a>Viz také

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[ODBC – základy](../../data/odbc/odbc-basics.md)
