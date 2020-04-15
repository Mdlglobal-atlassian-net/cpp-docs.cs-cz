---
title: SQL
ms.date: 05/09/2019
helpviewer_keywords:
- database classes [C++], SQL statements
- SQL [C++]
- SQL [C++], ODBC
- ODBC [C++], SQL implementation
ms.assetid: e3923bc4-b317-4e0b-afd8-3cd403eb0faf
ms.openlocfilehash: e5ab824f850b6050e11c10734dd709330af416b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376445"
---
# <a name="sql"></a>SQL

SQL (Strukturovaný dotazovací jazyk) je způsob komunikace s relační databáze, která umožňuje definovat, dotaz, upravit a řídit data. Pomocí syntaxe SQL můžete vytvořit příkaz, který extrahuje záznamy podle zadaných kritérií.

> [!NOTE]
> Tyto informace platí pro třídy Knihovny MFC ODBC. Pokud pracujete s třídami MFC DAO, podívejte se na téma Porovnání Microsoft Jet Database Engine SQL a ANSI SQL v nápovědě DAO.

Příkazy SQL začínají slovesem klíčového **slova,** například CREATE nebo **SELECT**. SQL je velmi silný jazyk; jeden příkaz může ovlivnit celou tabulku.

Existuje mnoho verzí SQL, z nichž každá byla vyvinuta s ohledem na konkrétní DBMS. Třídy databáze knihovny MFC rozpoznají sadu příkazů SQL, která odpovídá specifikaci konceptu SQL (X/Open and SQL Access Group Common Applications Environment( CAE) (1991). Informace o syntaxi těchto příkazů naleznete v dodatku C v *odkazu programátora* *sady ODBC SDK* na disku CD-ROM knihovny MSDN.

Toto téma vysvětluje:

- [Vztah mezi rozhraním ODBC a sql](#_core_open_database_connectivity_.28.odbc.29).

- [Nejběžnější klíčová slova SQL používaná třídami databáze](#_core_the_database_classes).

- [Jak třídy databáze používají SQL](#_core_how_the_database_classes_use_sql).

## <a name="open-database-connectivity-odbc"></a><a name="_core_open_database_connectivity_.28.odbc.29"></a>Připojení k otevřené databázi (ODBC)

Třídy databáze jsou implementovány pomocí rozhraní ODBC, které používá SQL v rozhraní na úrovni volání, nikoli vkládání příkazů SQL do kódu. Rozhraní ODBC používá sql ke komunikaci se [zdrojem dat](../../data/odbc/data-source-odbc.md) prostřednictvím ovladačů ODBC. Tyto ovladače interpretovat SQL a přeložit jej, v případě potřeby pro použití s určitým formátem databáze, jako je například Microsoft Access. Další informace o tom, jak rozhraní ODBC používá SQL, naleznete [v tématu ODBC](../../data/odbc/odbc-basics.md) a *reference programátora* sady ODBC SDK na disku CD-ROM knihovny MSDN.

## <a name="database-classes"></a><a name="_core_the_database_classes"></a>Třídy databáze

> [!NOTE]
> Průvodce příjemcem knihovny MFC ODBC není k dispozici v sadě Visual Studio 2019 a novějších. Stále můžete vytvořit příjemce ručně.

Třídy databáze jsou navrženy tak, aby vám umožňují manipulovat s daty v existujícím [zdroji dat](../../data/odbc/data-source-odbc.md)a aktualizovat je . [Průvodce aplikací knihovny MFC](../../mfc/reference/database-support-mfc-application-wizard.md), [Průvodce vytvořením knihovny MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) (přístupný prostřednictvím **add class**) a třídy databáze vytvoří většinu příkazů SQL za vás.

Třídy databáze používají část SQL známou jako jazyk pro manipulaci s daty (DML). Tyto příkazy umožňují pracovat s celým zdrojem dat nebo jeho částí, přidávat nové záznamy, upravovat záznamy a odstraňovat záznamy. V následující tabulce jsou uvedena nejběžnější klíčová slova SQL a způsoby, jakými je používají třídy databáze.

### <a name="some-common-sql-keywords"></a>Některá běžná klíčová slova SQL

|Klíčové slovo SQL|Používají je průvodci a třídy databáze|
|-----------------|---------------------------------------------|
|**Vyberte**|Chcete-li zjistit, které tabulky a sloupce ve zdroji dat mají být použity.|
|**WHERE**|Použití filtru, který výběr zužuje.|
|**ORDER BY**|Použití pořadí řazení na sadu záznamů.|
|**Vložit**|Přidání nových záznamů do sady záznamů.|
|**Odstranit**|Odstranění záznamů ze sady záznamů.|
|**Aktualizace**|Chcete-li upravit pole záznamu.|

Kromě toho třídy databáze rozpoznat PŘÍKAZY ODBC **CALL,** které můžete použít k volání předdefinovaný dotaz (nebo uložená procedura) na některé zdroje dat. Ovladač databáze ROZHRANÍ ODBC interpretuje tyto příkazy a nahrazuje příkaz vhodný pro každý dbms.

> [!NOTE]
> Ne všechny dbmss podporují **příkazy CALL.**

Pokud třídy nemohou rozpoznat příkaz `CRecordset::Open`dodaný uživatelem v aplikaci , je interpretován jako název tabulky.

Vysvětlení, jak rozhraní framework vytváří příkazy SQL, naleznete v [tématu Recordset: How Recordsets Select Records (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) a [SQL: Customizing Your Recordset's SQL Statement (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

Databáze SQL používají datové typy podobné těm, které se používají v jazycích C a C++. Diskuse o těchto podobností naleznete v tématu [SQL: SQL a C++ datové typy (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).

Další informace o SQL, včetně seznamu podporovaných příkazů SQL, datových typů, základní gramatiky SQL a seznamu doporučených publikací o SQL, naleznete v *odkazu programátora* *SADY ODBC SDK* na disku CD-ROM knihovny MSDN.

## <a name="how-the-database-classes-use-sql"></a><a name="_core_how_the_database_classes_use_sql"></a>Jak databázové třídy používají SQL

Sady záznamů odvozené z tříd databáze používají ke komunikaci se zdrojem dat rozhraní ODBC a rozhraní ODBC načítá záznamy ze zdroje dat odesláním příkazů SQL. Toto téma vysvětluje vztah mezi třídami databáze a SQL.

Sada záznamů vytvoří příkaz SQL tím, že vytvoří části `CString`příkazu SQL do . Řetězec je vytvořen jako **příkaz SELECT,** který vrací sadu záznamů.

Když sada záznamů volá odbc k odeslání příkazu SQL do zdroje dat, Správce ovladačů ODBC předá příkaz ovladači ODBC a ovladač jej odešle podkladovému systému DBMS. DbMS vrátí sadu výsledků záznamů a ovladač ODBC vrátí záznamy do aplikace. Třídy databáze umožňují programu přístup k sadě výsledků ve třídě C++ typu bezpečné z aplikace `CRecordset`.

Následující témata poskytují další informace o tom, jak třídy databáze používají SQL:

- [SQL: Přizpůsobení příkazu SQL sady záznamů (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)

- [SQL: Datové typy SQL a C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)

- [SQL: Přímá volání SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)

## <a name="see-also"></a>Viz také

[Připojení k otevřené databázi (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Základy rozhraní ODBC](../../data/odbc/odbc-basics.md)
