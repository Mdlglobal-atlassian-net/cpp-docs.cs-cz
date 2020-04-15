---
title: 'TN042: Doporučení pro vývojáře ovladačů ODBC'
ms.date: 11/04/2016
f1_keywords:
- vc.odbc
helpviewer_keywords:
- ODBC drivers [MFC], writing
- databases [MFC], ODBC
- TN042
ms.assetid: ecc6b5d9-f480-4582-9e22-8309fe561dad
ms.openlocfilehash: 67f7a86a247b60be66dabb0a89f04d39ce76222b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372138"
---
# <a name="tn042-odbc-driver-developer-recommendations"></a>TN042: Doporučení pro vývojáře ovladačů ODBC

> [!NOTE]
> Následující technická poznámka nebyla aktualizována od doby, kdy byla poprvé zahrnuta do online dokumentace. V důsledku toho mohou být některé postupy a témata zastaralé nebo nesprávné. Chcete-li získat nejnovější informace, doporučujeme vyhledat téma zájmu v online indexu dokumentace.

Tato poznámka popisuje pokyny pro autory ovladačů ODBC. Popisuje obecné požadavky a předpoklady funkcí ROZHRANÍ ODBC, které vytvořily třídy databáze knihovny MFC, a různé očekávané sémantické podrobnosti. Jsou popsány požadované funkce `CRecordset` ovladače pro podporu tří režimů Otevření **(forwardOnly**, **snapshot** a **dynaset).**

## <a name="odbcs-cursor-library"></a>Knihovna kurzorů od rozhraní ODBC

Třídy databáze knihovny MFC představují uživateli funkce, které v mnoha případech předčí funkce poskytované většinou ovladačů ODBC úrovně 1. Naštěstí knihovna kurzorů rozhraní ODBC se bude vrstvit mezi třídy databáze a ovladač a automaticky poskytne velkou část této další funkce.

Například většina ovladačů 1.0 nepodporuje zpětné posouvání. Knihovna kurzorů to může zjistit a uloží řádky z ovladače `SQLExtendedFetch`do mezipaměti a zobrazí je podle požadavků na FETCH_PREV volání v .

Dalším důležitým příkladem závislosti na knihovně kurzoru je umístění aktualizací. Většina ovladačů 1.0 také nemají umístěné aktualizace, ale knihovna kurzoru vygeneruje příkazy aktualizace, které identifikují cílový řádek ve zdroji dat na základě aktuálních hodnot dat uložených v mezipaměti nebo hodnoty časového razítka uloženév mezipaměti.

Knihovna tříd nikdy nepoužívá více sad řádků. Proto několik `SQLSetPos` příkazů jsou vždy použity na řádek 1 sady řádků.

## <a name="cdatabases"></a>CDatabáze

Každý `CDatabase` přiděluje jeden **HDBC**. (Pokud `CDatabase`je `ExecuteSQL` použita funkce 's, **hstmt** je dočasně přidělen.) Takže pokud `CDatabase`je vyžadováno více 's, musí být podporováno více **HDBC**s na **HENV.**

Třídy databáze vyžadují knihovnu kurzorů. To se odráží `SQLSetConnections` ve volání **SQL_ODBC_CURSORS**, **SQL_CUR_USE_ODBC**.

`SQLDriverConnect`, **SQL_DRIVER_COMPLETE** slouží `CDatabase::Open` k navázání připojení ke zdroji dat.

Řidič musí `SQLGetInfo SQL_ODBC_API_CONFORMANCE`  >= podporovat **SQL_OAC_LEVEL1**, `SQLGetInfo SQL_ODBC_SQL_CONFORMANCE`  >=  **SQL_OSC_MINIMUM**.

Aby byly transakce podporovány pro `CDatabase` a jeho závislé `SQLGetInfo SQL_CURSOR_COMMIT_BEHAVIOR` sady záznamů a **SQL_CURSOR_ROLLBACK_BEHAVIOR** musí **mít SQL_CR_PRESERVE**. V opačném případě budou pokusy o provedení řízení transakcí ignorovány.

`SQLGetInfo SQL_DATA_SOURCE_READ_ONLY`musí být podporovány. Pokud vrátí "Y", žádné operace aktualizace budou provedeny na zdroj dat.

Pokud `CDatabase` je otevřen readonly, pokus o nastavení zdroje dat `SQLSetConnectOption SQL_ACCESS_MODE`jen pro čtení bude provedena s , **SQL_MODE_READ_ONLY**.

Pokud identifikátory vyžadují citací, tyto informace `SQLGetInfo SQL_IDENTIFIER_QUOTE_CHAR` by měly být vráceny z ovladače s voláním.

Pro účely ladění `SQLGetInfo SQL_DBMS_VER` a **SQL_DBMS_NAME** jsou načteny z ovladače.

`SQLSetStmtOption SQL_QUERY_TIMEOUT`a **SQL_ASYNC_ENABLE** mohou být `CDatabase`volány na **'s HDBC**.

`SQLError`může být volána s některé nebo všechny argumenty NULL.

Samozřejmě, `SQLAllocEnv` `SQLAllocConnect`, `SQLDisconnect` `SQLFreeConnect` a musí být podporovány.

## <a name="executesql"></a>Executesql

Kromě přidělování a osvobozování dočasného `ExecuteSQL` **HSTMT**volání `SQLExecDirect`, `SQLFetch`a `SQLNumResultCol` `SQLMoreResults`. `SQLCancel`může být volána na **HSTMT**.

## <a name="getdatabasename"></a>GetDatabaseName

`SQLGetInfo SQL_DATABASE_NAME`bude volána.

## <a name="begintrans-committrans-rollback"></a>BeginTrans, CommitTrans, Vrácení zpět

`SQLSetConnectOption SQL_AUTOCOMMIT`a `SQLTransact SQL_COMMIT` **SQL_ROLLBACK** a **SQL_AUTOCOMMIT** budou volány, pokud jsou podány žádosti o transakci.

## <a name="crecordsets"></a>Sady crekordérech

`SQLAllocStmt`, `SQLPrepare` `SQLExecute` , `Open` (For a `Requery`), `SQLExecDirect` `SQLFreeStmt` (pro operace aktualizace), musí být podporovány. `SQLNumResultCols`a `SQLDescribeCol` budou vyzváni k výsledkům nastaveným v různých časech.

`SQLSetParam`se používá značně pro data vazby parametrů a **DATA_AT_EXEC** funkce.

`SQLBindCol`se používá značně k registraci výstupních umístění úložiště sloupcových dat pomocí rozhraní ODBC.

Dvě `SQLGetData` volání se používají k načtení **SQL_LONG_VARCHAR** a **SQL_LONG_VARBINARY** dat. První volání se pokusí najít celkovou délku `SQLGetData` hodnoty sloupce voláním s cbMaxValue 0, ale s platnou hodnotou pcbValue. Pokud pcbValue obsahuje **SQL_NO_TOTAL**, je vyvolána výjimka. V opačném případě **HGLOBAL** je `SQLGetData` přidělena a jiné volání provést načíst celý výsledek.

## <a name="updating"></a>Aktualizace

Pokud pesimistické `SQLGetInfo SQL_LOCK_TYPES` uzamčení je požadováno, bude dotazován. Pokud **SQL_LCK_EXCLUSIVE** není podporována, bude vyvolána výjimka.

Pokusy o `CRecordset` aktualizaci (**snímek** nebo **dynaset**) způsobí, že druhý **HSTMT,** které mají být přiděleny. Pro ovladače, které nepodporují druhý **HSTMT**, knihovna kurzoru bude simulovat tuto funkci. Bohužel to může někdy znamenat vynucení aktuální dotaz na první **HSTMT** k dokončení před zpracováním druhé **HSTMT**'s požadavek.

`SQLFreeStmt SQL_CLOSE`a **SQL_RESET_PARAMS** SQL_RESET_PARAMS `SQLGetCursorName` a bude volána během operací aktualizace.

Pokud jsou v **outputColumns** **clongbinarys** , musí být podporována **funkce DATA_AT_EXEC** rozhraní ODBC. To zahrnuje **SQL_NEED_DATA** vrácení `SQLExecDirect`SQL_NEED_DATA `SQLParamData` `SQLPutData`z , a .

`SQLRowCount`je volána po spuštění k ověření, že `SQLExecDirect`pouze 1 záznam byl aktualizován .

## <a name="forwardonly-cursors"></a>Pouze kurzory vpřed

Pro `SQLFetch` operace je `Move` vyžadováno pouze. Všimněte si, že **forwardOnly** kurzory nepodporují aktualizace.

## <a name="snapshot-cursors"></a>Kurzory snímků

Funkce snímku `SQLExtendedFetch` vyžaduje podporu. Jak je uvedeno výše, knihovna kurzorů ROZHRANÍ `SQLExtendedFetch`ODBC zjistí, kdy ovladač nepodporuje , a poskytne potřebnou podporu sám.

`SQLGetInfo`musí **SQL_SO_STATIC** **podporovat SQL_SCROLL_OPTIONS** .

## <a name="dynaset-cursors"></a>Kurzory dynasad

Níže je minimální podpora potřebná k otevření dynasetu:

`SQLGetInfo`, **SQL_ODBC_VER** se musí vrátit > "01".

`SQLGetInfo`musí **SQL_SCROLL_OPTIONS** podporovat **SQL_SO_KEYSET_DRIVEN**.

`SQLGetInfo`, **SQL_ROW_UPDATES** musí vrátit "Y".

`SQLGetInfo`musí **SQL_POSITIONED_UPDATES** podporovat **SQL_PS_POSITIONED_DELETE** a **SQL_PS_POSITIONED_UPDATE**.

Kromě toho, pokud pesimistické uzamčení je požadováno, bude provedeno volání `SQLSetPos` s irow 1, fRefresh FALSE a fLock **SQL_LCK_EXCLUSIVE.**

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
