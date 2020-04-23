---
title: CDatabase – třída
ms.date: 11/04/2016
f1_keywords:
- CDatabase
- AFXDB/CDatabase
- AFXDB/CDatabase::CDatabase
- AFXDB/CDatabase::BeginTrans
- AFXDB/CDatabase::BindParameters
- AFXDB/CDatabase::Cancel
- AFXDB/CDatabase::CanTransact
- AFXDB/CDatabase::CanUpdate
- AFXDB/CDatabase::Close
- AFXDB/CDatabase::CommitTrans
- AFXDB/CDatabase::ExecuteSQL
- AFXDB/CDatabase::GetBookmarkPersistence
- AFXDB/CDatabase::GetConnect
- AFXDB/CDatabase::GetCursorCommitBehavior
- AFXDB/CDatabase::GetCursorRollbackBehavior
- AFXDB/CDatabase::GetDatabaseName
- AFXDB/CDatabase::IsOpen
- AFXDB/CDatabase::OnSetOptions
- AFXDB/CDatabase::Open
- AFXDB/CDatabase::OpenEx
- AFXDB/CDatabase::Rollback
- AFXDB/CDatabase::SetLoginTimeout
- AFXDB/CDatabase::SetQueryTimeout
- AFXDB/CDatabase::m_hdbc
helpviewer_keywords:
- CDatabase [MFC], CDatabase
- CDatabase [MFC], BeginTrans
- CDatabase [MFC], BindParameters
- CDatabase [MFC], Cancel
- CDatabase [MFC], CanTransact
- CDatabase [MFC], CanUpdate
- CDatabase [MFC], Close
- CDatabase [MFC], CommitTrans
- CDatabase [MFC], ExecuteSQL
- CDatabase [MFC], GetBookmarkPersistence
- CDatabase [MFC], GetConnect
- CDatabase [MFC], GetCursorCommitBehavior
- CDatabase [MFC], GetCursorRollbackBehavior
- CDatabase [MFC], GetDatabaseName
- CDatabase [MFC], IsOpen
- CDatabase [MFC], OnSetOptions
- CDatabase [MFC], Open
- CDatabase [MFC], OpenEx
- CDatabase [MFC], Rollback
- CDatabase [MFC], SetLoginTimeout
- CDatabase [MFC], SetQueryTimeout
- CDatabase [MFC], m_hdbc
ms.assetid: bd0de70a-e3c3-4441-bcaa-bbf434426ca8
ms.openlocfilehash: bc920307e09179dc214710a3b6b19ff27a82749d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754638"
---
# <a name="cdatabase-class"></a>CDatabase – třída

Představuje připojení ke zdroji dat, jehož prostřednictvím můžete pracovat se zdrojem dat.

## <a name="syntax"></a>Syntaxe

```
class CDatabase : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDatabase::CDatabáze](#cdatabase)|Vytvoří `CDatabase` objekt. Objekt je nutné inicializovat voláním `OpenEx` nebo `Open`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDatabáze::BeginTrans](#begintrans)|Spustí "transakci" – řadu reverzibilních `AddNew` `Edit`volání `Delete`, `Update` , a `CRecordset` členské funkce třídy – na připojeném zdroji dat. Zdroj dat musí podporovat `BeginTrans` transakce, aby měly nějaký účinek.|
|[CDatabase::BindParameters](#bindparameters)|Umožňuje vázat parametry před `CDatabase::ExecuteSQL`voláním .|
|[CDatabáze::Storno](#cancel)|Zruší asynchronní operaci nebo proces z druhého vlákna.|
|[CDatabáze::CanTransact](#cantransact)|Vrátí nenulovou, pokud zdroj dat podporuje transakce.|
|[CDatabase::CanUpdate](#canupdate)|Vrátí nenulovou, pokud je `CDatabase` objekt aktualizovatelný (není jen pro čtení).|
|[CDatabáze::Zavřít](#close)|Zavře připojení ke zdroji dat.|
|[CDatabase::CommitTrans](#committrans)|Dokončí transakci zahájenou `BeginTrans`programem . Příkazy v transakci, které mění zdroj dat jsou prováděny.|
|[CDatabase::SpustitSQL](#executesql)|Provede příkaz SQL. Nejsou vráceny žádné datové záznamy.|
|[CDatabase::GetBookmarkPersistence](#getbookmarkpersistence)|Identifikuje operace, jejichž prostřednictvím záložky přetrvávají na objektech sady záznamů.|
|[CDatabáze::GetConnect](#getconnect)|Vrátí připojovací řetězec ODBC použitý k připojení objektu `CDatabase` ke zdroji dat.|
|[CDatabase::GetCursorCommitBehavior](#getcursorcommitbehavior)|Určuje vliv potvrzení transakce na objekt otevřené sady záznamů.|
|[CDatabase::GetCursorRollbackBehavior](#getcursorrollbackbehavior)|Určuje vliv vrácení transakce zpět na objekt otevřené sady záznamů.|
|[CDatabase::GetDatabaseName](#getdatabasename)|Vrátí název aktuálně použitelné databáze.|
|[CDatabase::IsOpen](#isopen)|Vrátí nenulovou, pokud je `CDatabase` objekt aktuálně připojen ke zdroji dat.|
|[CDatabase::Možnosti nástupu do aplikace](#onsetoptions)|Volat rámci nastavit standardní možnosti připojení. Výchozí implementace nastaví hodnotu časového limitu dotazu. Tyto možnosti můžete stanovit předem `SetQueryTimeout`voláním .|
|[CDatabáze::Otevřít](#open)|Naváže připojení ke zdroji dat (prostřednictvím ovladače ODBC).|
|[CDatabáze::OpenEx](#openex)|Naváže připojení ke zdroji dat (prostřednictvím ovladače ODBC).|
|[CDatabase::Vrácení zpět](#rollback)|Vrátí změny provedené během aktuální transakce. Zdroj dat se vrátí do předchozího `BeginTrans` stavu, jak je definováno při volání, beze změny.|
|[CDatabase::SetLoginTimeout](#setlogintimeout)|Nastaví počet sekund, po jejichž uplynutí bude časový limit pokusu o připojení zdroje dat.|
|[CDatabase::SetQueryTimeout](#setquerytimeout)|Nastaví počet sekund, po které budou časové limity operací dotazu databáze. Ovlivňuje všechny následující `Open` `AddNew`sady `Edit`záznamů `Delete` , , a volání.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CDatabáze::m_hdbc](#m_hdbc)|Otevřete popisovač připojení připojení k databázi (ODBC) ke zdroji dat. Typ *HDBC*.|

## <a name="remarks"></a>Poznámky

Zdroj dat je specifická instance dat hostovaných některým systémem správy databáze (DBMS). Příklady zahrnují Microsoft SQL Server, Microsoft Access, Borland dBASE a xBASE. V aplikaci můžete `CDatabase` mít aktivní jeden nebo více objektů najednou.

> [!NOTE]
> Pokud pracujete s třídami DAO (Data Access Objects) místo s třídami Open Database Connectivity (ODBC), použijte místo toho třídu [CDaoDatabase.](../../mfc/reference/cdaodatabase-class.md) Další informace naleznete v článku [Přehled: Programování databáze](../../data/data-access-programming-mfc-atl.md).

Chcete-li `CDatabase`použít `CDatabase` , vytvořit `OpenEx` objekt a volat jeho členská funkce. Tím se otevře připojení. Když pak `CRecordset` vytvoříte objekty pro provoz s připojeným zdrojem dat, předejte konstruktoru sady záznamů ukazatel objektu. `CDatabase` Po dokončení pomocí připojení volejte `Close` členská funkce `CDatabase` a zničit objekt. `Close`zavře všechny sady záznamů, které jste dříve nezavřeli.

Další informace `CDatabase`naleznete v článcích [Zdroj dat (ODBC)](../../data/odbc/data-source-odbc.md) a [Přehled: Programování databáze](../../data/data-access-programming-mfc-atl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CDatabase`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="cdatabasebegintrans"></a><a name="begintrans"></a>CDatabáze::BeginTrans

Volání této členské funkce zahájit transakci s připojeným zdrojem dat.

```
BOOL BeginTrans();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud bylo volání úspěšné a změny jsou potvrzeny pouze ručně; jinak 0.

### <a name="remarks"></a>Poznámky

Transakce se skládá z jednoho nebo `AddNew` `Edit`více `Delete`volání `Update` , , `CRecordset` a členské funkce objektu. Před zahájením transakce `CDatabase` musí být objekt již připojen ke zdroji `OpenEx` `Open` dat voláním jeho nebo členské funkce. Chcete-li ukončit transakci, volání [CommitTrans](#committrans) přijmout všechny změny zdroje dat (a provést je) nebo volání [Vrácení zpět](#rollback) přerušit celou transakci. Volání `BeginTrans` po otevření všech sad záznamů zapojených do transakce a co nejblíže k skutečné operace aktualizace, jak je to možné.

> [!CAUTION]
> V závislosti na ovladači ROZHRANÍ ODBC `BeginTrans` může otevření `Rollback`sady záznamů před voláním způsobit problémy při volání . Měli byste zkontrolovat konkrétní ovladač, který používáte. Například při použití ovladače aplikace Microsoft Access zahrnuté v microsoft ODBC Desktop Driver Pack 3.0, je nutné účet pro databázový stroj Jet požadavek, že byste neměli začínat transakce v databázi, která má otevřený kurzor. V databázových třídách knihovny MFC `CRecordset` znamená otevřený kurzor otevřený objekt. Další informace naleznete [v technické poznámce 68](../../mfc/tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver.md).

`BeginTrans`může také uzamknout datové záznamy na serveru, v závislosti na požadované souběžnosti a možnosti zdroje dat. Informace o uzamčení dat naleznete v článku [Sada záznamů: Uzamčení záznamů (ODBC).](../../data/odbc/recordset-locking-records-odbc.md)

Uživatelem definované transakce jsou vysvětleny v článku [Transakce (ODBC)](../../data/odbc/transaction-odbc.md).

`BeginTrans`stanoví stav, do kterého lze sled transakcí vrátit zpět (stornovat). Chcete-li vytvořit nový stav pro vrácení zpět, `BeginTrans` potvrďte všechny aktuální transakce a pak znovu volejte.

> [!CAUTION]
> Volání `BeginTrans` znovu `CommitTrans` bez `Rollback` volání nebo je chyba.

Volání [CanTransact](#cantransact) členské funkce k určení, zda ovladač podporuje transakce pro danou databázi. Měli byste také volat [GetCursorCommitBehavior](#getcursorcommitbehavior) a [GetCursorRollbackBehavior](#getcursorrollbackbehavior) k určení podpory pro zachování kurzoru.

Další informace o transakcích naleznete v článku [Transakce (ODBC).](../../data/odbc/transaction-odbc.md)

### <a name="example"></a>Příklad

  Viz článek [Transakce: Provedení transakce v sadě záznamů (ODBC).](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)

## <a name="cdatabasebindparameters"></a><a name="bindparameters"></a>CDatabase::BindParameters

Přepište, `BindParameters` když potřebujete vázat parametry před voláním [CDatabase::ExecuteSQL](#executesql).

```
virtual void BindParameters(HSTMT hstmt);
```

### <a name="parameters"></a>Parametry

*hstmt*<br/>
Popisovač příkazu ODBC, pro který chcete svázat parametry.

### <a name="remarks"></a>Poznámky

Tento přístup je užitečné, pokud nepotřebujete sadu výsledků z uložené procedury.

V přepsání, `SQLBindParameters` volání a související funkce ODBC svázat parametry. Knihovna MFC před voláním `ExecuteSQL`do aplikace volá přepis. Nemusíte volat `SQLPrepare`; `ExecuteSQL` volá `SQLExecDirect` a ničí *hstmt*, který se používá pouze jednou.

## <a name="cdatabasecancel"></a><a name="cancel"></a>CDatabáze::Storno

Volání této členské funkce požadovat, aby zdroj dat zrušit asynchronní operace probíhá nebo proces z druhého vlákna.

```cpp
void Cancel();
```

### <a name="remarks"></a>Poznámky

Všimněte si, že třídy Knihovny MFC ODBC již nepoužívají asynchronní zpracování. Chcete-li provést asynchronní operaci, musíte přímo volat funkci ROZHRANÍ API ROZHRANÍ ODBC [SQLSetConnectOption](/sql/odbc/reference/syntax/sqlsetconnectoption-function). Další informace naleznete [v tématu Asynchronní spuštění](/sql/odbc/reference/develop-app/asynchronous-execution).

## <a name="cdatabasecantransact"></a><a name="cantransact"></a>CDatabáze::CanTransact

Volání této členské funkce k určení, zda databáze umožňuje transakce.

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud `CDatabase` sady záznamů používající tento objekt umožňují transakce; jinak 0.

### <a name="remarks"></a>Poznámky

Informace o transakcích naleznete v článku [Transakce (ODBC).](../../data/odbc/transaction-odbc.md)

## <a name="cdatabasecanupdate"></a><a name="canupdate"></a>CDatabase::CanUpdate

Volání této členské funkce `CDatabase` k určení, zda objekt umožňuje aktualizace.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, `CDatabase` pokud objekt umožňuje aktualizace; jinak 0, označující buď, že jste předali `CDatabase` TRUE v *bReadOnly* při otevření objektu nebo že samotný zdroj dat je jen pro čtení. Zdroj dat je jen pro čtení, pokud volání `SQLGetInfo` funkce ROZHRANÍ API ROZHRANÍ ODBC pro SQL_DATASOURCE_READ_ONLY vrátí "y".

### <a name="remarks"></a>Poznámky

Aktualizace nepodporují všechny ovladače.

## <a name="cdatabasecdatabase"></a><a name="cdatabase"></a>CDatabase::CDatabáze

Vytvoří `CDatabase` objekt.

```
CDatabase();
```

### <a name="remarks"></a>Poznámky

Po vytvoření objektu je nutné `OpenEx` `Open` volat jeho nebo členská funkce k navázání připojení k zadanému zdroji dat.

Může být vhodné vložit objekt `CDatabase` do třídy dokumentu.

### <a name="example"></a>Příklad

Tento příklad ilustruje `CDatabase` použití `CDocument`v odvozené třídě.

[!code-cpp[NVC_MFCDatabase#9](../../mfc/codesnippet/cpp/cdatabase-class_1.h)]

[!code-cpp[NVC_MFCDatabase#10](../../mfc/codesnippet/cpp/cdatabase-class_2.cpp)]

## <a name="cdatabaseclose"></a><a name="close"></a>CDatabáze::Zavřít

Volání této členské funkce, pokud chcete odpojit od zdroje dat.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Před voláním této členské `CDatabase` funkce je nutné zavřít všechny sady záznamů přidružené k objektu. Protože `Close` nezničí `CDatabase` objekt, můžete objekt znovu použít otevřením nového připojení ke stejnému zdroji dat nebo jinému zdroji dat.

Všechny `AddNew` čekající `Edit` nebo výkazy sad záznamů pomocí databáze jsou zrušeny a všechny čekající transakce jsou vráceny zpět. Všechny sady záznamů `CDatabase` závislé na objektu zůstanou v nedefinovaném stavu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#12](../../mfc/codesnippet/cpp/cdatabase-class_3.cpp)]

## <a name="cdatabasecommittrans"></a><a name="committrans"></a>CDatabase::CommitTrans

Volání této členské funkce po dokončení transakcí.

```
BOOL CommitTrans();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byly aktualizace úspěšně potvrzeny; jinak 0. Pokud `CommitTrans` se nezdaří, stav zdroje dat není definován. Chcete-li určit jejich stav, je nutné zkontrolovat data.

### <a name="remarks"></a>Poznámky

Transakce se skládá z řady volání `AddNew` `Edit`, `Delete`, `Update` a členské `CRecordset` funkce objektu, který začal voláním [begintrans](#begintrans) členské funkce. `CommitTrans`potvrdí transakci. Ve výchozím nastavení jsou aktualizace potvrzeny okamžitě; volání `BeginTrans` způsobí, že závazek `CommitTrans` aktualizací bude zpožděn, dokud není volána.

Dokud nezavoláte `CommitTrans` ukončení transakce, můžete volat funkci [Rollback](#rollback) member a přerušit transakci a ponechat zdroj dat v původním stavu. Chcete-li zahájit `BeginTrans` novou transakci, zavolejte znovu.

Další informace o transakcích naleznete v článku [Transakce (ODBC).](../../data/odbc/transaction-odbc.md)

### <a name="example"></a>Příklad

  Viz článek [Transakce: Provedení transakce v sadě záznamů (ODBC).](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)

## <a name="cdatabaseexecutesql"></a><a name="executesql"></a>CDatabase::SpustitSQL

Volání této členské funkce, když potřebujete provést příkaz SQL přímo.

```cpp
void ExecuteSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>Parametry

*Lpszsql*<br/>
Ukazatel na řetězec s ukončeným hodnotou null obsahující platný příkaz SQL, který má být proveden. Můžete předat [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Poznámky

Vytvořte příkaz jako řetězec s nulovým ukončením. `ExecuteSQL`nevrací datové záznamy. Pokud chcete pracovat se záznamy, použijte místo toho objekt sady záznamů.

Většina příkazů pro zdroj dat je vydávána prostřednictvím objektů sady záznamů, které podporují příkazy pro výběr dat, vkládání nových záznamů, odstranění záznamů a úpravy záznamů. Ne všechny funkce ROZHRANÍ ODBC jsou však přímo podporovány třídami databáze, takže `ExecuteSQL`někdy může být nutné provést přímé volání SQL s .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#13](../../mfc/codesnippet/cpp/cdatabase-class_4.cpp)]

## <a name="cdatabasegetbookmarkpersistence"></a><a name="getbookmarkpersistence"></a>CDatabase::GetBookmarkPersistence

Volání této členské funkce k určení trvalosti záložek na objektu sady záznamů po určité operace.

```
DWORD GetBookmarkPersistence() const;
```

### <a name="return-value"></a>Návratová hodnota

Bitová maska, která identifikuje operace, jejichž prostřednictvím záložky přetrvávají na objektu sady záznamů. Podrobnosti naleznete v tématu Poznámky.

### <a name="remarks"></a>Poznámky

Například pokud zavoláte `CRecordset::GetBookmark` a `CRecordset::Requery`potom zavoláte `GetBookmark` , záložka získané z již nemusí být platný. Měli byste `GetBookmarkPersistence` zavolat před voláním `CRecordset::SetBookmark`.

V následující tabulce jsou uvedeny hodnoty bitové masky, které lze kombinovat pro vrácenou hodnotu . `GetBookmarkPersistence`

|Hodnota bitové masky|Trvalost záložky|
|-------------------|--------------------------|
|SQL_BP_CLOSE|Záložky jsou platné `Requery` po operaci.|
|SQL_BP_DELETE|Záložka pro řádek je platná `Delete` po operaci na tomto řádku.|
|SQL_BP_DROP|Záložky jsou platné `Close` po operaci.|
|SQL_BP_SCROLL|Záložky jsou platné `Move` po každé operaci. To jednoduše identifikuje, pokud jsou záložky podporovány `CRecordset::CanBookmark`v sadě záznamů, jak je vráceno .|
|SQL_BP_TRANSACTION|Záložky jsou platné po transakce je potvrzena nebo vrácena zpět.|
|SQL_BP_UPDATE|Záložka pro řádek je platná `Update` po operaci na tomto řádku.|
|SQL_BP_OTHER_HSTMT|Záložky přidružené k jednomu objektu sady záznamů jsou platné pro druhou sadu záznamů.|

Další informace o této vrácené hodnotě `SQLGetInfo` naleznete v části Funkce rozhraní API ROZHRANÍ ODBC v sadě Windows SDK. Další informace o záložkách naleznete v článku [Sada záznamů: Záložky a Absolutní pozice (ODBC).](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)

## <a name="cdatabasegetconnect"></a><a name="getconnect"></a>CDatabáze::GetConnect

Volání této členské funkce k načtení připojovacího řetězce použitého během volání `OpenEx` nebo `Open` připojeného objektu `CDatabase` ke zdroji dat.

```
const CString GetConnect() const;
```

### <a name="return-value"></a>Návratová hodnota

Const **const**[CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahující připojovací řetězec, pokud `OpenEx` nebo `Open` byl volán; v opačném případě prázdný řetězec.

### <a name="remarks"></a>Poznámky

Viz [CDatabase::Open](#open) pro popis, jak je vytvořen připojovací řetězec.

## <a name="cdatabasegetcursorcommitbehavior"></a><a name="getcursorcommitbehavior"></a>CDatabase::GetCursorCommitBehavior

Volání této členské funkce k určení, jak [commitTrans](#committrans) operace ovlivňuje kurzory na objekty open recordset.

```
int GetCursorCommitBehavior() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota označující vliv transakcí na objekty otevřené sady záznamů. Podrobnosti naleznete v tématu Poznámky.

### <a name="remarks"></a>Poznámky

V následující tabulce jsou uvedeny možné vrácené hodnoty pro `GetCursorCommitBehavior` a odpovídající vliv na otevřenou sadu záznamů.

|Návratová hodnota|Vliv na objekty CRecordset|
|------------------|----------------------------------|
|SQL_CB_CLOSE|Volání `CRecordset::Requery` bezprostředně po potvrzení transakce.|
|SQL_CB_DELETE|Volání `CRecordset::Close` bezprostředně po potvrzení transakce.|
|SQL_CB_PRESERVE|Postupujte `CRecordset` normálně s operacemi.|

Další informace o této vrácené hodnotě `SQLGetInfo` naleznete v části Funkce rozhraní API ROZHRANÍ ODBC v sadě Windows SDK. Další informace o transakcích naleznete v článku [Transakce (ODBC).](../../data/odbc/transaction-odbc.md)

## <a name="cdatabasegetcursorrollbackbehavior"></a><a name="getcursorrollbackbehavior"></a>CDatabase::GetCursorRollbackBehavior

Volání této členské funkce k určení, jak operace [vrácení zpět](#rollback) ovlivňuje kurzory na objekty open recordset.

```
int GetCursorRollbackBehavior() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota označující vliv transakcí na objekty otevřené sady záznamů. Podrobnosti naleznete v tématu Poznámky.

### <a name="remarks"></a>Poznámky

V následující tabulce jsou uvedeny možné vrácené hodnoty pro `GetCursorRollbackBehavior` a odpovídající vliv na otevřenou sadu záznamů.

|Návratová hodnota|Vliv na objekty CRecordset|
|------------------|----------------------------------|
|SQL_CB_CLOSE|Volání `CRecordset::Requery` bezprostředně po vrácení transakce.|
|SQL_CB_DELETE|Volání `CRecordset::Close` bezprostředně po vrácení transakce.|
|SQL_CB_PRESERVE|Postupujte `CRecordset` normálně s operacemi.|

Další informace o této vrácené hodnotě `SQLGetInfo` naleznete v části Funkce rozhraní API ROZHRANÍ ODBC v sadě Windows SDK. Další informace o transakcích naleznete v článku [Transakce (ODBC).](../../data/odbc/transaction-odbc.md)

## <a name="cdatabasegetdatabasename"></a><a name="getdatabasename"></a>CDatabase::GetDatabaseName

Volání této členské funkce načíst název aktuálně připojené databáze (za předpokladu, že zdroj dat definuje pojmenovaný objekt s názvem "databáze").

```
CString GetDatabaseName() const;
```

### <a name="return-value"></a>Návratová hodnota

[CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahující název databáze, pokud je úspěšný; v opačném `CString`případě prázdné .

### <a name="remarks"></a>Poznámky

Toto není stejné jako název zdroje dat (DSN) zadaný v `OpenEx` nebo `Open` volání. Co `GetDatabaseName` vrátí závisí na ROZHRANÍ ODBC. Obecně platí, že databáze je kolekce tabulek. Pokud má tato entita název, `GetDatabaseName` vrátí jej.

Tento název můžete například chtít zobrazit v záhlaví. Pokud dojde k chybě při načítání názvu `GetDatabaseName` z ROZHRANÍ `CString`ODBC, vrátí prázdný .

## <a name="cdatabaseisopen"></a><a name="isopen"></a>CDatabase::IsOpen

Volání této členské funkce `CDatabase` k určení, zda je objekt aktuálně připojen ke zdroji dat.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, `CDatabase` pokud je objekt aktuálně připojen; jinak 0.

## <a name="cdatabasem_hdbc"></a><a name="m_hdbc"></a>CDatabáze::m_hdbc

Obsahuje veřejný popisovač připojení zdroje dat ODBC – "popisovač připojení".

### <a name="remarks"></a>Poznámky

Za normálních okolností nebudete mít přímý přístup k této členské proměnné. Místo toho rozhraní přiděluje `OpenEx` popisovač při volání nebo `Open`. Rozhraní framework zruší přidělení popisovače **delete** při volání `CDatabase` operátoru delete na objektu. Všimněte `Close` si, že členská funkce není navrátit popisovač.

Za určitých okolností však možná budete muset použít rukojeť přímo. Například pokud potřebujete volat funkce rozhraní API ROZHRANÍ `CDatabase`ODBC přímo, nikoli prostřednictvím třídy , budete pravděpodobně potřebovat popisovač připojení předat jako parametr. Podívejte se na příklad kódu níže.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#15](../../mfc/codesnippet/cpp/cdatabase-class_5.cpp)]

## <a name="cdatabaseonsetoptions"></a><a name="onsetoptions"></a>CDatabase::Možnosti nástupu do aplikace

Rozhraní Framework volá tuto členská funkci při `ExecuteSQL` přímém provádění příkazu SQL s členovou funkcí.

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Parametry

*hstmt*<br/>
Popisovač příkazu ODBC, pro který jsou nastaveny možnosti.

### <a name="remarks"></a>Poznámky

`CRecordset::OnSetOptions`také volá tuto člennou funkci.

`OnSetOptions`nastaví hodnotu časového limitu přihlášení. Pokud byly předchozí volání `SetQueryTimeout` a členské `OnSetOptions` funkce, odráží aktuální hodnoty; v opačném případě nastaví výchozí hodnoty.

> [!NOTE]
> Před MFC 4.2 `OnSetOptions` také nastavte režim zpracování na snychronní nebo asynchronní. Počínaje knihovnou MFC 4.2 jsou všechny operace synchronní. Chcete-li provést asynchronní operaci, musíte provést přímé volání `SQLSetPos`funkce rozhraní API ROZHRANÍ ODBC .

Není nutné přepsat `OnSetOptions` změnit hodnotu časového času. Místo toho chcete přizpůsobit hodnotu `SetQueryTimeout` časového limitu dotazu, volání před vytvořením sady záznamů; `OnSetOptions` použije novou hodnotu. Nastavené hodnoty platí pro následné operace na všech sadách záznamů nebo přímých voláních SQL.

Přepište, `OnSetOptions` pokud chcete nastavit další možnosti. Přepsání by mělo `OnSetOptions` volat základní třídu před nebo `SQLSetStmtOption`po volání funkce ROZHRANÍ API ROZHRANÍ ODBC . Postupujte podle metody znázorněné v rámci `OnSetOptions`výchozí implementace .

## <a name="cdatabaseopen"></a><a name="open"></a>CDatabáze::Otevřít

Volání této členské funkce k inicializaci nově vytvořený `CDatabase` objekt.

```
virtual BOOL Open(
    LPCTSTR lpszDSN,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T("ODBC;"),
    BOOL bUseCursorLib = TRUE);
```

### <a name="parameters"></a>Parametry

*lpszDSN*<br/>
Určuje název zdroje dat – název registrovaný v odbc prostřednictvím programu Správce ROZHRANÍ ODBC. Pokud je hodnota DSN zadána v *lpszConnect* (ve\<tvaru "DSN => zdroje dat"), nesmí být znovu zadána v *lpszDSN*. V tomto případě *lpszDSN* by měla být NULL. V opačném případě můžete předat hodnotu NULL, pokud chcete uživateli zobrazit dialogové okno Zdroj dat, ve kterém může uživatel vybrat zdroj dat. Další informace naleznete v tématu Poznámky.

*bExkluzivní*<br/>
V této verzi knihovny tříd není podporováno. V současné době kontrolní výraz selže, pokud je tento parametr TRUE. Zdroj dat je vždy otevřen jako sdílený (není výhradní).

*bReadOnly*<br/>
PRAVDA, pokud máte v úmyslu připojení jen pro čtení a zakázat aktualizace zdroje dat. Všechny závislé sady záznamů dědí tento atribut. Výchozí hodnota je FALSE.

*lpszPřipojit*<br/>
Určuje připojovací řetězec. Připojovací řetězec zřetězí informace, případně včetně názvu zdroje dat, ID uživatele platného ve zdroji dat, ověřovacího řetězce uživatele (heslo, pokud zdroj dat vyžaduje) a další informace. Celý připojovací řetězec musí být předponou řetězcem "ODBC;" (velká nebo malá písmena). Řetězec "ODBC;" označuje, že připojení je ke zdroji dat ODBC; To to je pro kompatibilitu směrem nahoru, když budoucí verze knihovny tříd může podporovat jiné zdroje dat NEŽBC.

*bUseCursorLib*<br/>
TRUE, pokud chcete načíst knihovnu DLL knihovny kurzorů ODBC. Knihovna kurzorů maskuje některé funkce základního ovladače ODBC a účinně zabraňuje použití dynasetu (pokud je ovladač podporuje). Pouze kurzory podporované, pokud je načtena knihovna kurzoru jsou statické snímky a kurzory pouze pro předávání. Výchozí hodnota je TRUE. Pokud plánujete vytvořit objekt sady `CRecordset` záznamů přímo z bez odvození z něj, neměli byste načítat knihovnu kurzorů.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je připojení úspěšně provedeno; Jinak 0, pokud uživatel zvolí Zrušit při zobrazení dialogového okna s žádostí o další informace o připojení. Ve všech ostatních případech framework vyvolá výjimku.

### <a name="remarks"></a>Poznámky

Databázový objekt musí být inicializován, než jej můžete použít k vytvoření objektu sady záznamů.

> [!NOTE]
> Volání členské funkce [OpenEx](#openex) je upřednostňovaný způsob připojení ke zdroji dat a inicializaci databázového objektu.

Pokud parametry `Open` volání neobsahují dostatek informací k vytvoření připojení, ovladač ODBC otevře dialogové okno pro získání potřebných informací od uživatele. Při volání `Open`je připojovací řetězec *lpszConnect*uložen `CDatabase` soukromě v objektu a je k dispozici voláním členské funkce [GetConnect.](#getconnect)

Pokud chcete, můžete před voláním `Open` otevřít vlastní dialogové okno, abyste získali informace od uživatele, například heslo, a pak tyto informace přidat do připojovacího řetězce, kterému předáte `Open`. Nebo můžete chtít uložit připojovací řetězec, který předáte, abyste `Open` jej `CDatabase` mohli znovu použít při příštím volání aplikace na objekt.

Připojovací řetězec můžete také použít pro více úrovní `CDatabase` autorizace přihlášení (každá pro jiný objekt) nebo k předávání dalších informací specifických pro zdroj dat. Další informace o připojovacích řetězcích naleznete v kapitole 5 sady Windows SDK.

Je možné, že pokus o připojení časový limit, pokud například hostitel DBMS není k dispozici. Pokud se pokus `Open` o připojení `CDBException`nezdaří, vyvolá .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#14](../../mfc/codesnippet/cpp/cdatabase-class_6.cpp)]

## <a name="cdatabaseopenex"></a><a name="openex"></a>CDatabáze::OpenEx

Volání této členské funkce k inicializaci nově vytvořený `CDatabase` objekt.

```
virtual BOOL OpenEx(
    LPCTSTR lpszConnectString,
    DWORD dwOptions = 0);
```

### <a name="parameters"></a>Parametry

*lpszConnectString*<br/>
Určuje připojovací řetězec ODBC. To zahrnuje název zdroje dat a další volitelné informace, jako je například ID uživatele a heslo. Například "DSN=SQLServer_Source; UID=SA; PWD=abc123" je možný připojovací řetězec. Všimněte si, že pokud předáte hodnotu NULL pro *lpszConnectString*, dialogové okno Zdroj dat vyzve uživatele k výběru zdroje dat.

*Dwoptions*<br/>
Bitová maska, která určuje kombinaci následujících hodnot. Výchozí hodnota je 0, což znamená, že databáze bude otevřena jako sdílená s přístupem pro zápis, knihovna DLL knihovny kurzorů ODBC nebude načtena a dialogové okno připojení ODBC se zobrazí pouze v případě, že není k dispozici dostatek informací pro připojení.

- `CDatabase::openExclusive`V této verzi knihovny tříd není podporováno. Zdroj dat je vždy otevřen jako sdílený (není výhradní). V současné době kontrolní výraz se nezdaří, pokud zadáte tuto možnost.

- `CDatabase::openReadOnly`Otevřete zdroj dat jen pro čtení.

- `CDatabase::useCursorLib`Načtěte knihovnu DLL knihovny kurzorů ROZHRANÍ ODBC. Knihovna kurzorů maskuje některé funkce základního ovladače ODBC a účinně zabraňuje použití dynasetu (pokud je ovladač podporuje). Pouze kurzory podporované, pokud je načtena knihovna kurzoru jsou statické snímky a kurzory pouze pro předávání. Pokud plánujete vytvořit objekt sady `CRecordset` záznamů přímo z bez odvození z něj, neměli byste načítat knihovnu kurzorů.

- `CDatabase::noOdbcDialog`Nezobrazovat dialogové okno připojení ODBC bez ohledu na to, zda je zadáno dostatečné množství informací o připojení.

- `CDatabase::forceOdbcDialog`Vždy zobrazte dialogové okno připojení ODBC.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je připojení úspěšně provedeno; Jinak 0, pokud uživatel zvolí Zrušit při zobrazení dialogového okna s žádostí o další informace o připojení. Ve všech ostatních případech framework vyvolá výjimku.

### <a name="remarks"></a>Poznámky

Databázový objekt musí být inicializován, než jej můžete použít k vytvoření objektu sady záznamů.

Pokud parametr *lpszConnectString* `OpenEx` ve vašem volání neobsahuje dostatek informací k vytvoření připojení, ovladač ODBC otevře dialogové okno pro získání `CDatabase::noOdbcDialog` `CDatabase::forceOdbcDialog` potřebných informací od uživatele za předpokladu, že jste nenastavili nebo v parametru *dwOptions.* Při volání `OpenEx`je připojovací řetězec *lpszConnectString*uložen `CDatabase` soukromě v objektu a je k dispozici voláním členské funkce [GetConnect.](#getconnect)

Pokud chcete, můžete před voláním `OpenEx` otevřít vlastní dialogové okno, abyste získali informace od uživatele, například heslo, `OpenEx`a pak tyto informace přidat do připojovacího řetězce, kterému předáte . Nebo můžete chtít uložit připojovací řetězec, který předáte, abyste `OpenEx` jej `CDatabase` mohli znovu použít při příštím volání aplikace na objekt.

Připojovací řetězec můžete také použít pro více úrovní `CDatabase` autorizace přihlášení (každá pro jiný objekt) nebo k předávání dalších informací specifických pro zdroj dat. Další informace o připojovacích řetězcích naleznete v kapitole 6 v *odkazu programátora ODBC*.

Je možné, že pokus o připojení časový limit, pokud například hostitel DBMS není k dispozici. Pokud se pokus `OpenEx` o připojení `CDBException`nezdaří, vyvolá .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#11](../../mfc/codesnippet/cpp/cdatabase-class_7.cpp)]

## <a name="cdatabaserollback"></a><a name="rollback"></a>CDatabase::Vrácení zpět

Volání této členské funkce stornovat změny provedené během transakce.

```
BOOL Rollback();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla transakce úspěšně stornována; jinak 0. Pokud `Rollback` volání selže, zdroj dat a stavy transakcí nejsou definovány. Pokud `Rollback` vrátí 0, je nutné zkontrolovat zdroj dat k určení jeho stavu.

### <a name="remarks"></a>Poznámky

Všechna `CRecordset` `AddNew` `Edit`, `Delete`, `Update` a volání provedená od posledního [BeginTrans](#begintrans) jsou vráceny zpět do stavu, který existoval v době tohoto volání.

Po volání `Rollback`na , transakce je u `BeginTrans` konce a je nutné volat znovu pro jinou transakci. Záznam, který byl aktuální `BeginTrans` před voláním, `Rollback`se stane aktuálním záznamem znovu po .

Po vrácení zpět, záznam, který byl aktuální před vrácení zpět zůstane aktuální. Podrobnosti o stavu sady záznamů a zdroj dat po vrácení zpět naleznete v článku [Transakce (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Příklad

  Viz článek [Transakce: Provedení transakce v sadě záznamů (ODBC).](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)

## <a name="cdatabasesetlogintimeout"></a><a name="setlogintimeout"></a>CDatabase::SetLoginTimeout

Volání této členské funkce `OpenEx` – `Open` před voláním nebo – přepsat výchozí počet sekund povolených před vypršením doby pokusu o připojení zdroje dat.

```cpp
void SetLoginTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>Parametry

*dwSekundy*<br/>
Počet sekund, které mají být povoleny před vypršením doby pokusu o připojení.

### <a name="remarks"></a>Poznámky

Časový limit může být časový limit, pokud například dbms není k dispozici. Volání `SetLoginTimeout` po vytvoření neinicializovaného `CDatabase` `OpenEx` objektu, ale před voláním nebo `Open`.

Výchozí hodnota pro časové limity přihlášení je 15 sekund. Ne všechny zdroje dat podporují možnost zadat hodnotu časového limitu přihlášení. Pokud zdroj dat nepodporuje časový režim, získáte výstup trasování, ale není výjimkou. Hodnota 0 znamená "nekonečno".

## <a name="cdatabasesetquerytimeout"></a><a name="setquerytimeout"></a>CDatabase::SetQueryTimeout

Volání této členské funkce přepsat výchozí počet sekund povolit před následnými operacemi na připojený zdroj dat časový limit.

```cpp
void SetQueryTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>Parametry

*dwSekundy*<br/>
Počet sekund, které mají být povoleny před vypršením doby pokusu o dotaz.

### <a name="remarks"></a>Poznámky

Operace může časový limit z důvodu problémů s přístupem k síti, nadměrné doby zpracování dotazů a tak dále. Chcete-li změnit hodnotu časového limitu dotazu, `SetQueryTimeout` zavolejte před otevřením sady záznamů nebo před voláním funkcí sady `AddNew`záznamů `Update` nebo `Delete` členských funkcí. Nastavení ovlivní všechny `Open` `AddNew`následující `Update`, `Delete` , a volání všech `CDatabase` sad záznamů přidružených k tomuto objektu. Změna hodnoty časového limitu dotazu pro sadu záznamů po otevření nezmění hodnotu sady záznamů. Například následné `Move` operace nepoužívají novou hodnotu.

Výchozí hodnota pro časové limity dotazu je 15 sekund. Ne všechny zdroje dat podporují možnost nastavit hodnotu časového limitu dotazu. Pokud nastavíte hodnotu časového limitu dotazu 0, nedojde k žádnému časovému limitu; komunikace se zdrojem dat může přestat reagovat. Toto chování může být užitečné během vývoje. Pokud zdroj dat nepodporuje časový režim, získáte výstup trasování, ale není výjimkou.

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)
