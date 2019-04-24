---
title: SQL
ms.date: 11/04/2016
helpviewer_keywords:
- database classes [C++], SQL statements
- SQL [C++]
- SQL [C++], ODBC
- ODBC [C++], SQL implementation
ms.assetid: e3923bc4-b317-4e0b-afd8-3cd403eb0faf
ms.openlocfilehash: 8f93d97530068695359273b523e7d2ae46de01cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62329884"
---
# <a name="sql"></a>SQL

SQL (Structured Query Language) je způsob, jak komunikovat s relační databázi, která umožňuje definovat dotaz, upravovat a řídit data. Pomocí syntaxe SQL, můžete vytvořit příkaz, který extrahuje záznamy podle zadaných kritérií.

> [!NOTE]
>  Tyto informace platí pro třídy knihovny MFC rozhraní ODBC. Pokud pracujete s tříd DAO knihovny MFC, najdete v tématu porovnání z Microsoft Jet stroj SQL Database a SQL ANSI v nápovědě rozhraní DAO.

Příkazy SQL začínat sloveso – klíčové slovo jako například **vytvořit** nebo **vyberte**. SQL je velmi výkonný jazyk; jeden příkaz může mít vliv na celou tabulku.

Existuje mnoho verzí SQL, každý vyvinuté pomocí určité DBMS v úvahu. MFC – databázové třídy rozpoznat sadu příkazů SQL, které odpovídá x / otevřít a specifikace konceptu SQL přístup skupiny běžné aplikace prostředí (CAE) SQL (1991). Informace o syntaxi tyto příkazy, naleznete v dodatku C *ODBC SDK* *referenční informace pro programátory* na disku CD knihovny MSDN.

Toto téma vysvětluje:

- [Vztah mezi ODBC a jazyku SQL](#_core_open_database_connectivity_.28.odbc.29).

- [Nejběžnější klíčová slova SQL používané v rámci tříd databáze](#_core_the_database_classes).

- [Použití databázových tříd SQL](#_core_how_the_database_classes_use_sql).

##  <a name="_core_open_database_connectivity_.28.odbc.29"></a> Otevřete připojení k databázi (ODBC)

Databázové třídy jsou implementovány s rozhraním ODBC, který používá SQL v rozhraní úroveň volání namísto vložení příkazy SQL v kódu. Rozhraní ODBC používá ke komunikaci s SQL [zdroj dat](../../data/odbc/data-source-odbc.md) prostřednictvím ovladače rozhraní ODBC. Tyto ovladače interpretovat SQL a přeloží ji, pokud je to nutné pro použití s formátem konkrétní databáze, jako je například aplikace Microsoft Access. Další informace o tom, jak ODBC používá SQL najdete v tématu [ODBC](../../data/odbc/odbc-basics.md) a sady SDK rozhraní ODBC *referenční informace pro programátory* na disku CD knihovny MSDN.

##  <a name="_core_the_database_classes"></a> Databázové třídy

Databázové třídy jsou navržena tak, aby manipulaci a aktualizovat data v existujícím [zdroj dat](../../data/odbc/data-source-odbc.md). [Průvodce aplikací knihovny MFC](../../mfc/reference/database-support-mfc-application-wizard.md), [průvodce příjemcem MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) (přístupná prostřednictvím **přidat třídu**), a databázové třídy většinu příkazů SQL vytvořit za vás.

Databázové třídy použijte část SQL označované jako jazyk manipulace dat (DML). Tyto příkazy umožňují pracovat s část nebo celý zdroj dat, přidat nové záznamy, upravovat záznamy a odstraňovat záznamy. Následující tabulka uvádí nejběžnější klíčová slova SQL a způsoby, kterými databázové třídy jejich použití.

### <a name="some-common-sql-keywords"></a>Některé běžné klíčová slova SQL

|SQL – klíčové slovo|Průvodci a databázové třídy pomocí|
|-----------------|---------------------------------------------|
|**SELECT**|Chcete-li určit, které tabulky a sloupce ve zdroji dat se mají použít.|
|**WHERE**|Chcete-li použít filtr, který způsobí zúžení výběru.|
|**ORDER BY**|Chcete-li použít pořadí řazení na sadu záznamů.|
|**VLOŽIT**|Přidání nových záznamů do sady záznamů.|
|**DELETE**|Chcete-li odstranit záznamy ze sady záznamů.|
|**AKTUALIZACE**|Chcete-li změnit pole záznamu.|

Kromě toho databázové třídy rozpoznat ODBC **volání** příkazy, které můžete použít pro volání předdefinovaný dotaz (nebo uložená procedura) na některé zdroje dat. Ovladač ODBC databáze interpretuje tyto příkazy a nahradí příkazu vhodného pro každý systém DBMS.

> [!NOTE]
>  Ne všechny systémy DBMS podporu **volání** příkazy.

Pokud třídy nelze rozpoznat uživatelem zadané v příkazu `CRecordset::Open`, je interpretován jako název tabulky.

Vysvětlení, jak rozhraní sestavují SQL příkazy, najdete v článku [sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) a [SQL: Přizpůsobení příkazu SQL sady záznamů (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

Databáze SQL pomocí datových typů, které jsou podobné těm, které jsou použity v jazyce C a C++. Informace o těchto podobnost, naleznete v tématu [SQL: SQL a datové typy C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).

Můžete najít další informace o SQL, včetně seznam podporovaných příkazů SQL, datových typů, core gramatika SQL a čtení seznam doporučených publikací o SQL, *ODBC SDK* *Programátorská referenční dokumentace*  na disku CD knihovny MSDN.

##  <a name="_core_how_the_database_classes_use_sql"></a> Použití databázových tříd SQL

Sady záznamů, které jsou odvozeny z databázových tříd použití rozhraní ODBC ke komunikaci se zdrojem dat a ODBC načte záznamy ze zdroje dat odesláním příkazů jazyka SQL. Toto téma popisuje vztah mezi třídami database a SQL.

Sada záznamů sestavuje příkaz SQL sestavením, které byly příkaz jazyka SQL do `CString`. Řetězec je zkonstruován jako **vyberte** příkaz, který vrátí sadu záznamů.

Při volání sady záznamů rozhraní ODBC pro odesílání příkazu SQL pro zdroj dat, správce ovladačů ODBC předá příkaz ovladač ODBC a ovladači odesílá je do základní DBMS. Systém DBMS vrátí výsledek sadu záznamů a ovladač ODBC vrací záznamy k aplikaci. Databázové třídy umožní váš přístup k programu sadu výsledků ve třídu C++ zajišťující bezpečnost typů odvozených z `CRecordset`.

Další informace o použití databázových tříd SQL naleznete v následujících tématech:

- [SQL: Přizpůsobení příkazu SQL sady záznamů (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)

- [SQL: SQL a datové typy C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)

- [SQL: Přímá volání SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)

## <a name="see-also"></a>Viz také:

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[ODBC – základy](../../data/odbc/odbc-basics.md)