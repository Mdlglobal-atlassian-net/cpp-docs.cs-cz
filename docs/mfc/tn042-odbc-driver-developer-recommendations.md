---
title: 'TN042: Doporučení pro vývojáře ovladačů ODBC | Microsoft Docs'
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
ms.openlocfilehash: 35c75f5c5bae3a1b56abe91340de00f373663792
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="tn042-odbc-driver-developer-recommendations"></a>TN042: Doporučení pro vývojáře ovladačů ODBC
> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována vzhledem k tomu, že byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata může být zastaralý nebo není správný. Nejnovější informace se doporučuje, vyhledejte téma týkající se v indexu online dokumentaci.  
  
 Tato poznámka popisuje pokyny pro zapisovače ovladačů ODBC. Ho popisuje obecné požadavky a předpoklady fungování rozhraní ODBC, který třídy MFC databáze a různé očekávané sémantického podrobnosti. Požadované funkce, které pro podporu tří `CRecordset` otevřete režimy (**forwardOnly**, **snímku** a **dynamická sada**) jsou popsány.  
  
## <a name="odbcs-cursor-library"></a>Knihovna kurzorů rozhraní ODBC pro  
 Třídy MFC databáze k dispozici funkce uživateli, které jsou v mnoha případech převyšuje funkce poskytované službou většina ovladače ODBC úrovně 1. Naštěstí knihovna kurzorů rozhraní ODBC pro samotné vrstvy mezi databázové třídy a ovladače a bude automaticky poskytovat většinu tato další funkce.  
  
 Například většina 1.0 ovladače nepodporují zpětné posouvání. Knihovna kurzorů zjistit a bude ukládat do mezipaměti řádků z ovladače a je k dispozici požadované na FETCH_PREV volání v **SQLExtendedFetch**.  
  
 Další důležité příklad závislost knihovna kurzorů je umístěné aktualizace. Většina 1.0 ovladače také nemají umístěné aktualizace, ale knihovna kurzorů vytvoří příkazy aktualizace, které identifikovat cílový řádek ve zdroji dat na základě jeho aktuální hodnoty data uložená v mezipaměti, nebo hodnotu uloženou v mezipaměti časové razítko.  
  
 Knihovny tříd nikdy využívá více sad řádků. Proto několik **SQLSetPos** příkazy se vždycky použijí pro řádek 1 sady řádků.  
  
## <a name="cdatabases"></a>CDatabases  
 Každý `CDatabase` přiděluje jedné **HDBC**. (Pokud `CDatabase`na `ExecuteSQL` při použití funkce **HSTMT** je dočasně přidělen.) Pokud více `CDatabase`je vyžadováno, více **HDBC**s za **HENV** musí podporovat.  
  
 Databázové třídy vyžadují knihovna kurzorů. To se projeví v **SQLSetConnections** volání **SQL_ODBC_CURSORS**, **SQL_CUR_USE_ODBC**.  
  
 **SQLDriverConnect**, **SQL_DRIVER_COMPLETE** používá `CDatabase::Open` k navázání připojení ke zdroji dat.  
  
 Ovladače musí podporovat **SQLGetInfo SQL_ODBC_API_CONFORMANCE** >= **SQL_OAC_LEVEL1**, **SQLGetInfo SQL_ODBC_SQL_CONFORMANCE**  >=  **SQL_OSC_MINIMUM**.  
  
 V pořadí pro transakce podporovaná pro `CDatabase` a jeho závislé sady záznamů, **SQLGetInfo SQL_CURSOR_COMMIT_BEHAVIOR** a **SQL_CURSOR_ROLLBACK_BEHAVIOR** musí mít **SQL_CR_PRESERVE**. Pokusy o provedení transakce řízení, jinak budou ignorovány.  
  
 **SQLGetInfo SQL_DATA_SOURCE_READ_ONLY** musí být podporována. Pokud vrátí hodnotu "Y", žádné operace aktualizace se provede na datovém zdroji.  
  
 Pokud `CDatabase` je otevřen jen pro čtení, pokus o nastavení zdroje dat, přečtěte si bude obsahovat jenom s **SQLSetConnectOption SQL_ACCESS_MODE**, **SQL_MODE_READ_ONLY**.  
  
 Pokud identifikátory vyžadují citací, z ovladač, který se má být vrácen tyto informace **SQLGetInfo SQL_IDENTIFIER_QUOTE_CHAR** volání.  
  
 Pro účely ladění **SQLGetInfo SQL_DBMS_VER** a **SQL_DBMS_NAME** jsou načteny z ovladače.  
  
 **SQLSetStmtOption SQL_QUERY_TIMEOUT** a **SQL_ASYNC_ENABLE** může být volána na `CDatabase`na **HDBC**.  
  
 **Funkce SQLError** může být volána s kterékoli nebo všechny argumenty hodnotu NULL.  
  
 Samozřejmě **SQLAllocEnv**, **SQLAllocConnect**, **SQLDisconnect** a **provedeny příkazy SQLFreeConnect** musí být podporována.  
  
## <a name="executesql"></a>ExecuteSQL  
 Kromě přidělování a uvolnění dočasného **HSTMT**, `ExecuteSQL` volání **SQLExecDirect**, **SQLFetch**, **SQLNumResultCol**a `SQLMoreResults`. **SQLCancel** může být volána na **HSTMT**.  
  
## <a name="getdatabasename"></a>GetDatabaseName  
 **SQLGetInfo SQL_DATABASE_NAME** bude volána.  
  
## <a name="begintrans-committrans-rollback"></a>Metody BeginTrans, CommitTrans, vrácení zpět  
 **SQLSetConnectOption SQL_AUTOCOMMIT** a **SQLTransact SQL_COMMIT**, **SQL_ROLLBACK** a **SQL_AUTOCOMMIT** bude volána, pokud transakce požadavků jsou vytvářeny.  
  
## <a name="crecordsets"></a>CRecordsets  
 **SQLAllocStmt**, **SQLPrepare**, **SQLExecute** (pro **otevřete** a **Requery –**), **SQLExecDirect**  (pro operace aktualizace), **SQLFreeStmt** musí být podporována. **SQLNumResultCols** a **zda** bude volána na výsledcích nastavit v různé časy.  
  
 **SQLSetParam** se velmi často používá pro vytvoření vazby dat parametru a **DATA_AT_EXEC** funkce.  
  
 **SQLBindCol** se velmi často používá k registraci výstupní umístění úložiště dat sloupce s rozhraním ODBC.  
  
 Dva **SQLGetData** volání slouží k načtení **SQL_LONG_VARCHAR** a **SQL_LONG_VARBINARY** data. První volání pokusí se najít celková délka hodnotu ve sloupci voláním **SQLGetData** s cbMaxValue 0, ale s platnou pcbValue. Pokud obsahuje pcbValue **SQL_NO_TOTAL**, je vyvolána výjimka. Jinak `HGLOBAL` je přidělen a jiné **SQLGetData** volání načíst celý výsledky.  
  
## <a name="updating"></a>Aktualizace  
 Pokud se vyžaduje pesimistické zamykání, **SQLGetInfo SQL_LOCK_TYPES** bude dotaz. Pokud **SQL_LCK_EXCLUSIVE** se nepodporuje, bude vyvolána výjimka.  
  
 Pokusí aktualizovat `CRecordset` (**snímku** nebo **dynamická sada**) způsobí, že druhý **HSTMT** přidělování. Pro ovladače, které nepodporují druhé **HSTMT**, knihovna kurzorů bude simulovat tuto funkci. Bohužel se to někdy znamená vynucení aktuální dotaz na první **HSTMT** dokončen před zpracováním druhý **HSTMT**požadavku uživatele.  
  
 **SQLFreeStmt SQL_CLOSE** a **SQL_RESET_PARAMS** a **SQLGetCursorName** bude volána během operace aktualizace.  
  
 Pokud jsou **CLongBinarys** v **outputColumns**, rozhraní ODBC je **DATA_AT_EXEC** funkce musí být podporována. To zahrnuje vrácení **SQL_NEED_DATA** z **SQLExecDirect**, **SQLParamData** a **SQLPutData**.  
  
 **SQL** je volána po provedení ověření, že byl aktualizován pouze 1 záznam **SQLExecDirect**.  
  
## <a name="forwardonly-cursors"></a>Kurzory ForwardOnly  
 Pouze **SQLFetch** vyžaduje **přesunout** operace. Všimněte si, že **forwardOnly** kurzory nepodporují aktualizaci.  
  
## <a name="snapshot-cursors"></a>Kurzory snímku  
 Vyžaduje funkcí snímků **SQLExtendedFetch** podporovat. Jak jsme uvedli výše, bude knihovny kurzorů ODBC rozpoznat, kdy se ovladač nepodporuje **SQLExtendedFetch**a poskytovat podporu potřebné, sám sebe.  
  
 **SQLGetInfo**, **SQL_SCROLL_OPTIONS** musí podporovat **SQL_SO_STATIC**.  
  
## <a name="dynaset-cursors"></a>Dynamická sada kurzory  
 Dále je potřeba otevřít dynamickou sadu minimální podporu:  
  
 **SQLGetInfo**, **SQL_ODBC_VER** musí vracet > "01".  
  
 **SQLGetInfo**, **SQL_SCROLL_OPTIONS** musí podporovat **SQL_SO_KEYSET_DRIVEN**.  
  
 **SQLGetInfo**, **SQL_ROW_UPDATES** musí vracet "Y".  
  
 **SQLGetInfo**, **SQL_POSITIONED_UPDATES** musí podporovat **SQL_PS_POSITIONED_DELETE** a **SQL_PS_POSITIONED_UPDATE**.  
  
 Kromě toho, pokud se požaduje pesimistické zamykání volání **SQLSetPos** s irow 1, fRefresh FALSE a hejna **SQL_LCK_EXCLUSIVE** budou provedeny.  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

