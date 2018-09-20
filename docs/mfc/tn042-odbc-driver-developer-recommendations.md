---
title: 'TN042: Doporučení pro vývojáře ovladačů ODBC | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.odbc
dev_langs:
- C++
helpviewer_keywords:
- ODBC drivers [MFC], writing
- databases [MFC], ODBC
- TN042
ms.assetid: ecc6b5d9-f480-4582-9e22-8309fe561dad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 87e31fa0884adc78d3f1026afc59dd0b46ac7602
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375252"
---
# <a name="tn042-odbc-driver-developer-recommendations"></a>TN042: Doporučení pro vývojáře ovladačů ODBC

> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována, protože byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata mohou být nesprávné nebo zastaralé. Nejnovější informace se doporučuje vyhledat téma zájmu v dokumentaci online index.

Tato poznámka popisuje pokyny pro zápis ovladač ODBC. Obsahuje obecné požadavky a předpoklady ODBC funkce, díky kterému třídy databází MFC a různé očekávané sémantické podrobnosti. Vyžaduje ovladač funkce, které podporují tři `CRecordset` otevřete režimy (**forwardOnly**, **snímku** a **dynamická sada**) jsou popsány.

## <a name="odbcs-cursor-library"></a>Knihovna kurzorů rozhraní ODBC.

Třídy databází MFC k dispozici funkce pro uživatele, který v mnoha případech převyšuje funkce poskytované službou většina ODBC – ovladače úrovně 1. Naštěstí knihovna kurzorů rozhraní ODBC pro samotný vrstvy mezi databázové třídy a ovladače a bude automaticky poskytovat většinu této další funkce.

Například většina 1.0 ovladačů nepodporují zpětně posouvání. Knihovna kurzorů rozhraní můžete zjišťovat a bude ukládat do mezipaměti řádků z ovladače a prezentovat podle požadavku na FETCH_PREV volání v `SQLExtendedFetch`.

Dalším příkladem důležité závislosti knihovny kurzoru je umístěné aktualizace. Většina 1.0 ovladačů také nemají umístěné aktualizace, ale knihovna kurzorů rozhraní bude generovat příkazy aktualizace, které identifikují cílové řádek ve zdroji dat na základě své aktuální hodnoty data uložená v mezipaměti, nebo hodnoty časového razítka v mezipaměti.

Knihovna tříd nikdy využívá více sad řádků. Proto, několik `SQLSetPos` příkazů jsou vždy aplikovány na řádku 1 sady řádků.

## <a name="cdatabases"></a>CDatabases

Každý `CDatabase` přiděluje jediného **HDBC**. (Pokud `CDatabase`společnosti `ExecuteSQL` se používá funkce, **HSTMT** dočasně přidělené.) Pokud více `CDatabase`společnosti jsou povinné, více **HDBC**za sekundu na **HENV** musí podporovat.

Databázové třídy vyžadují knihovna kurzorů rozhraní. Toto je zohledněno v `SQLSetConnections` volání **SQL_ODBC_CURSORS**, **SQL_CUR_USE_ODBC**.

`SQLDriverConnect`, **SQL_DRIVER_COMPLETE** používá `CDatabase::Open` k navázání připojení ke zdroji dat.

Ovladače musí podporovat `SQLGetInfo SQL_ODBC_API_CONFORMANCE`  >=  **SQL_OAC_LEVEL1**, `SQLGetInfo SQL_ODBC_SQL_CONFORMANCE`  >=  **SQL_OSC_MINIMUM**.

Aby transakce budeme podporovat `CDatabase` a jeho závislé sady záznamů `SQLGetInfo SQL_CURSOR_COMMIT_BEHAVIOR` a **SQL_CURSOR_ROLLBACK_BEHAVIOR** musí mít **SQL_CR_PRESERVE**. V opačném případě pokusů o provedení řídicí transakce se budou ignorovat.

`SQLGetInfo SQL_DATA_SOURCE_READ_ONLY` musí se podporovat. Vrátí "Y",-li žádné operace aktualizace se provede na zdroj dat.

Pokud `CDatabase` je otevřen jen pro čtení, pokus o nastavení zdroje dat číst pouze bude proveden s `SQLSetConnectOption SQL_ACCESS_MODE`, **SQL_MODE_READ_ONLY**.

Identifikátory vyžadují uvozovky u,-li tyto informace má být vrácen z ovladače s `SQLGetInfo SQL_IDENTIFIER_QUOTE_CHAR` volání.

Pro účely ladění `SQLGetInfo SQL_DBMS_VER` a **SQL_DBMS_NAME** jsou načteny z ovladače.

`SQLSetStmtOption SQL_QUERY_TIMEOUT` a **SQL_ASYNC_ENABLE** může být volána na `CDatabase`společnosti **HDBC**.

`SQLError` může být volána s některé nebo všechny argumenty hodnotu NULL.

Samozřejmě `SQLAllocEnv`, `SQLAllocConnect`, `SQLDisconnect` a `SQLFreeConnect` musí podporovat.

## <a name="executesql"></a>ExecuteSQL

Kromě přidělení a uvolnění dočasný **HSTMT**, `ExecuteSQL` volání `SQLExecDirect`, `SQLFetch`, `SQLNumResultCol` a `SQLMoreResults`. `SQLCancel` může být volána na **HSTMT**.

## <a name="getdatabasename"></a>GetDatabaseName

`SQLGetInfo SQL_DATABASE_NAME` bude volána.

## <a name="begintrans-committrans-rollback"></a>Metody BeginTrans CommitTrans, vrácení zpět

`SQLSetConnectOption SQL_AUTOCOMMIT` a `SQLTransact SQL_COMMIT`, **SQL_ROLLBACK** a **SQL_AUTOCOMMIT** bude volána, pokud transakce, požadavky přicházejí.

## <a name="crecordsets"></a>CRecordsets

`SQLAllocStmt`, `SQLPrepare`, `SQLExecute` (Pro `Open` a `Requery`), `SQLExecDirect` (pro operace update), `SQLFreeStmt` musí podporovat. `SQLNumResultCols` a `SQLDescribeCol` bude volána při výsledky, nastavte v různých časech.

`SQLSetParam` je často používána pro svázání parametrů dat a **DATA_AT_EXEC** funkce.

`SQLBindCol` je často používána k registraci výstupní umístění úložiště dat sloupce s rozhraním ODBC.

Dvě `SQLGetData` volání slouží k načtení **SQL_LONG_VARCHAR** a **SQL_LONG_VARBINARY** data. První volání, pokusí se najít celková délka sloupce voláním `SQLGetData` se cbMaxValue 0, ale s platnou pcbValue. Pokud obsahuje pcbValue **SQL_NO_TOTAL**, je vyvolána výjimka. V opačném případě **HGLOBAL** je přidělena a další `SQLGetData` volání k načtení celého výsledku.

## <a name="updating"></a>Aktualizace

Pokud o to požádá pesimistické zamykání `SQLGetInfo SQL_LOCK_TYPES` budou dotazovat. Pokud **SQL_LCK_EXCLUSIVE** se nepodporuje, bude vyvolána výjimka.

Aktualizaci `CRecordset` (**snímku** nebo **dynamická sada**) způsobí, že druhý **HSTMT** mají být přiděleny. Ovladače, které nepodporují druhá **HSTMT**, knihovna kurzorů rozhraní budou simulovat tuto funkci. Bohužel to může v některých případech to znamenat vynucení aktuální dotaz na první **HSTMT** dokončen před zpracováním druhý **HSTMT**požadavku uživatele.

`SQLFreeStmt SQL_CLOSE` a **SQL_RESET_PARAMS** a `SQLGetCursorName` bude volána během operace aktualizace.

Pokud existují **CLongBinarys** v **outputColumns**, ODBC **DATA_AT_EXEC** funkce musí být podporována. Jedná se o vrácení **SQL_NEED_DATA** z `SQLExecDirect`, `SQLParamData` a `SQLPutData`.

`SQLRowCount` je volána po provedení ověření, že byla aktualizována pouze 1 záznam `SQLExecDirect`.

## <a name="forwardonly-cursors"></a>Kurzory ForwardOnly

Pouze `SQLFetch` , je třeba `Move` operace. Všimněte si, že **forwardOnly** kurzory aktualizace nepodporují.

## <a name="snapshot-cursors"></a>Kurzory snímku

Vyžaduje funkcí snímků `SQLExtendedFetch` podporovat. Jak bylo uvedeno výše, knihovna kurzorů rozhraní ODBC se rozpoznat, kdy se ovladač nepodporuje `SQLExtendedFetch`a podporují nezbytné, samotného.

`SQLGetInfo`, **SQL_SCROLL_OPTIONS** musí podporovat **SQL_SO_STATIC**.

## <a name="dynaset-cursors"></a>Dynamická sada kurzory

Níže je minimální podporu k otevření dynamická sada vyžaduje:

`SQLGetInfo`, **SQL_ODBC_VER** musí vracet > "01".

`SQLGetInfo`, **SQL_SCROLL_OPTIONS** musí podporovat **SQL_SO_KEYSET_DRIVEN**.

`SQLGetInfo`, **SQL_ROW_UPDATES** musí vracet "Y".

`SQLGetInfo`, **SQL_POSITIONED_UPDATES** musí podporovat **SQL_PS_POSITIONED_DELETE** a **SQL_PS_POSITIONED_UPDATE**.

Kromě toho, pokud o to požádá pesimistické zamykání volání `SQLSetPos` irow 1, fRefresh FALSE a hejna **SQL_LCK_EXCLUSIVE** bude proveden.

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

