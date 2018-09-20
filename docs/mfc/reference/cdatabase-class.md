---
title: CDatabase – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb101179cff40d79ab142e55b4fc46cc8941d126
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399545"
---
# <a name="cdatabase-class"></a>CDatabase – třída

Reprezentuje připojení ke zdroji dat, pomocí kterého můžete pracovat ve zdroji dat.

## <a name="syntax"></a>Syntaxe

```
class CDatabase : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDatabase::CDatabase](#cdatabase)|Vytvoří `CDatabase` objektu. Je třeba inicializovat objekt voláním `OpenEx` nebo `Open`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDatabase::BeginTrans](#begintrans)|Spustí "transakci" – řadu reverzibilního volání `AddNew`, `Edit`, `Delete`, a `Update` členské funkce třídy `CRecordset` – na připojených zdrojů dat. Zdroj dat musí podporovat transakce pro `BeginTrans` nemá žádný vliv.|
|[CDatabase::BindParameters](#bindparameters)|Umožňuje svázání parametrů před voláním `CDatabase::ExecuteSQL`.|
|[CDatabase::Cancel](#cancel)|Zruší asynchronní operace nebo proces z druhého vlákna.|
|[CDatabase::CanTransact](#cantransact)|Vrátí nenulovou hodnotu, pokud zdroj dat podporuje transakce.|
|[CDatabase::CanUpdate](#canupdate)|Vrátí nenulovou hodnotu, pokud `CDatabase` aktualizovatelný objekt (ne jen pro čtení).|
|[CDatabase::Close](#close)|Zavře připojení ke zdroji dat.|
|[CDatabase::CommitTrans](#committrans)|Dokončení transakce zahájené `BeginTrans`. Příkazy v rámci transakce, které mění zdroje dat jsou prováděny.|
|[CDatabase::ExecuteSQL](#executesql)|Provádí příkaz jazyka SQL. Nejsou vráceny žádné datové záznamy.|
|[CDatabase::GetBookmarkPersistence](#getbookmarkpersistence)|Jsou uvedeny operace, pomocí kterých záložky zachovat na objekty sady záznamů.|
|[CDatabase::getconnect byla](#getconnect)|Vrátí řetězec připojení ODBC použitý k připojení `CDatabase` ke zdroji dat objektu.|
|[CDatabase::GetCursorCommitBehavior](#getcursorcommitbehavior)|Určuje efekt potvrzování transakce v objektu otevřít sadu záznamů.|
|[CDatabase::GetCursorRollbackBehavior](#getcursorrollbackbehavior)|Identifikuje vliv vrácení transakce zpět na objekt otevřít sadu záznamů.|
|[CDatabase::GetDatabaseName](#getdatabasename)|Vrátí název databáze aktuálně používá.|
|[CDatabase::IsOpen](#isopen)|Vrátí nenulovou hodnotu, pokud `CDatabase` objekt je nyní připojen ke zdroji dat.|
|[CDatabase::OnSetOptions](#onsetoptions)|Volá se rozhraním, chcete-li nastavit možnosti standardní připojení. Výchozí implementace nastaví hodnotu časového limitu dotazu. Tyto možnosti předem vám pomůže zajistit voláním `SetQueryTimeout`.|
|[CDatabase::Open](#open)|Naváže připojení ke zdroji dat (prostřednictvím ovladače rozhraní ODBC).|
|[CDatabase::OpenEx](#openex)|Naváže připojení ke zdroji dat (prostřednictvím ovladače rozhraní ODBC).|
|[CDatabase::Rollback](#rollback)|Vrátí zpět změny provedené v průběhu aktuální transakce. Tento zdroj dat vrátí do předchozího stavu, jak je definováno v `BeginTrans` volání v nezměněném stavu.|
|[CDatabase::SetLoginTimeout](#setlogintimeout)|Nastaví dobu v sekundách, po jejichž uplynutí pokus o připojení zdroje dat, vyprší časový limit.|
|[CDatabase::SetQueryTimeout](#setquerytimeout)|Nastaví počet sekund, po kterou databázi dotazovat operace vyprší časový limit. Ovlivňuje všechny následné záznamů `Open`, `AddNew`, `Edit`, a `Delete` volání.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CDatabase::m_hdbc](#m_hdbc)|Otevřít databázové připojení (ODBC) připojení ke zdroji dat. Typ *HDBC*.|

## <a name="remarks"></a>Poznámky

Zdroj dat je konkrétní instanci datům hostovaným v některých systém správy databáze (DBMS). Mezi příklady patří Microsoft SQL Server, Microsoft Access, Borlandu dBASE a xBASE. Můžete mít jednu nebo více `CDatabase` objektů active současně ve vaší aplikaci.

> [!NOTE]
>  Pokud pracujete s třídami objektů DAO (Data Access), a ne třídy připojení ODBC (Open Database), použijte třídu [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) místo. Další informace najdete v článku [přehled: databáze programování](../../data/data-access-programming-mfc-atl.md).

Použití `CDatabase`, sestavit `CDatabase` objektu a volání jeho `OpenEx` členskou funkci. Tím se otevře připojení. Když potom vytvoříte `CRecordset` objekty pro provoz ve zdroji dat předat konstruktoru sady záznamů ukazatel na váš `CDatabase` objektu. Volat po dokončení práce připojení `Close` členské funkce a zničit `CDatabase` objektu. `Close` Zavře všechny sady záznamů, které nebyly uzavřeny dříve.

Další informace o `CDatabase`, najdete v článcích [datové zdroje (ODBC)](../../data/odbc/data-source-odbc.md) a [přehled: databáze programování](../../data/data-access-programming-mfc-atl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CDatabase`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

##  <a name="begintrans"></a>  CDatabase::BeginTrans

Voláním této členské funkce začít transakci s připojeného zdroje dat.

```
BOOL BeginTrans();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo volání úspěšné a se změny potvrdí pouze ručně. jinak 0.

### <a name="remarks"></a>Poznámky

Transakce se skládá z jednoho nebo více volání `AddNew`, `Edit`, `Delete`, a `Update` členské funkce `CRecordset` objektu. Před zahájením transakce, `CDatabase` objektu musí již byla připojena k zdroji dat po zavolání jeho `OpenEx` nebo `Open` členskou funkci. Chcete-li ukončit transakci, zavolejte [CommitTrans](#committrans) potvrďte všechny změny do zdroje dat (a provádět) nebo volání [vrácení zpět](#rollback) přerušit celá transakce. Volání `BeginTrans` po otevření libovolné sady záznamů účastnící se transakce a jako blízko skutečnou aktualizovat operace nejvíce.

> [!CAUTION]
>  V závislosti na váš ovladač rozhraní ODBC otevření sady záznamů před zavoláním funkce `BeginTrans` může způsobit problémy při volání metody `Rollback`. Měli byste zkontrolovat konkrétní ovladač, který používáte. Například při použití ovladače Microsoft Access, které jsou součástí Microsoft ODBC Desktopu ovladač Pack 3.0, musíte vzít v úvahu pro modul databáze Jet požadavek, že by neměl spustit transakci na všechny databáze, které se má otevřít kurzor. V databázových tříd MFC otevřít kurzor znamená, že otevřený `CRecordset` objektu. Další informace najdete v tématu [Technická poznámka 68](../../mfc/tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver.md).

`BeginTrans` může také uzamknout datových záznamů na serveru, v závislosti na možnosti zdroje dat a požadovaný souběžnosti. Informace o uzamčení data, najdete v článku [sada záznamů: zamykání záznamů (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).

Uživatelské transakce jsou vysvětlené v článku [transakce (ODBC)](../../data/odbc/transaction-odbc.md).

`BeginTrans` Vytvoří stavu, ke kterému můžete být posloupnost transakce vrácena zpět (vrátit). K vytvoření nového stavu pro vrácení změn, potvrzení aktuální transakci, zavolejte `BeginTrans` znovu.

> [!CAUTION]
>  Volání `BeginTrans` znovu bez volání `CommitTrans` nebo `Rollback` chybu.

Volání [CanTransact](#cantransact) členskou funkci k určení, jestli ovladač podporuje transakce pro danou databázi. Měli byste také zavolat [GetCursorCommitBehavior](#getcursorcommitbehavior) a [GetCursorRollbackBehavior](#getcursorrollbackbehavior) určit podporu pro zachování kurzoru.

Další informace o transakcích, najdete v článku [transakce (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Příklad

  Přečtěte si článek [transakce: provádění transakcí v sadě záznamů (rozhraní ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

##  <a name="bindparameters"></a>  CDatabase::BindParameters

Přepsat `BindParameters` když potřebujete pro svázání parametrů před voláním [CDatabase::ExecuteSQL](#executesql).

```
virtual void BindParameters(HSTMT hstmt);
```

### <a name="parameters"></a>Parametry

*HSTMT*<br/>
Popisovač příkazu ODBC, pro které chcete pro svázání parametrů.

### <a name="remarks"></a>Poznámky

Tento přístup je užitečný, když výsledek není nutné nastavit z uložené procedury.

Přepsání, volejte `SQLBindParameters` a související funkce ODBC k vytvoření vazby parametrů. MFC volá přepsání před volání `ExecuteSQL`. Není potřeba volat `SQLPrepare`; `ExecuteSQL` volání `SQLExecDirect` a odstraní *hstmt*, který se používá pouze jednou.

##  <a name="cancel"></a>  CDatabase::Cancel

Voláním této členské funkce požadovat, že zdroj dat zrušit probíhá asynchronní operace nebo proces z druhého vlákna.

```
void Cancel();
```

### <a name="remarks"></a>Poznámky

Mějte na paměti, že třídy knihovny MFC rozhraní ODBC již nebudete používat asynchronní zpracování. k provádění asynchronní operace, musíte přímo zavolat funkci rozhraní API ODBC [SQLSetConnectOption](/previous-versions/windows/desktop/ms713564\(v=vs.85\)). Další informace najdete v tématu [asynchronní provádění](/previous-versions/windows/desktop/ms713563\(v=vs.85\)) v sadě Windows SDK.

##  <a name="cantransact"></a>  CDatabase::CanTransact

Voláním této členské funkce k určení, zda databáze umožňuje transakce.

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulovou hodnotu, pokud pomocí této sady záznamů `CDatabase` povolit transakce objektu; jinak 0.

### <a name="remarks"></a>Poznámky

Informace o transakcích, najdete v článku [transakce (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="canupdate"></a>  CDatabase::CanUpdate

Voláním této členské funkce k určení, zda `CDatabase` objektu umožňuje instalaci aktualizací.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulovou hodnotu, pokud `CDatabase` objektu umožňuje instalaci aktualizací; jinak 0 označující buď, kterou jste předány nastavena hodnota TRUE v *bReadOnly* při otevření `CDatabase` objektu nebo že zdroj dat samotného je jen pro čtení. Zdroj dat je určeno jen pro čtení, pokud je volání funkce ODBC API `SQLGetInfo` pro SQL_DATASOURCE_READ_ONLY vrátí "y".

### <a name="remarks"></a>Poznámky

Ne všechny ovladače podporovat aktualizace.

##  <a name="cdatabase"></a>  CDatabase::CDatabase

Vytvoří `CDatabase` objektu.

```
CDatabase();
```

### <a name="remarks"></a>Poznámky

Po vytvoření objektu, je nutné volat jeho `OpenEx` nebo `Open` členskou funkci k navázání připojení ke zdroji zadaná data.

Možná bude vhodné vložit `CDatabase` objekt ve své třídě dokumentu.

### <a name="example"></a>Příklad

Tento příklad ukazuje použití `CDatabase` v `CDocument`-odvozené třídy.

[!code-cpp[NVC_MFCDatabase#9](../../mfc/codesnippet/cpp/cdatabase-class_1.h)]

[!code-cpp[NVC_MFCDatabase#10](../../mfc/codesnippet/cpp/cdatabase-class_2.cpp)]

##  <a name="close"></a>  CDatabase::Close

Pokud se chcete odpojit od zdroje dat zavolejte tuto členskou funkci.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Je nutné zavřít všechny přidružené sadě záznamů s `CDatabase` objekt před voláním této členské funkce. Protože `Close` nezničí `CDatabase` objektu, můžete znovu použít objekt otevřením nového připojení ke stejnému zdroji dat nebo jinému zdroji dat.

Všechna nevyřízená `AddNew` nebo `Edit` zrušení příkazů sad záznamů pomocí databáze a všechny čekající transakce jsou vrácena zpět. Žádné sady záznamů závisí `CDatabase` objektu jsou ponechány ve stavu nedefinovaný.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#12](../../mfc/codesnippet/cpp/cdatabase-class_3.cpp)]

##  <a name="committrans"></a>  CDatabase::CommitTrans

Voláním této členské funkce po dokončení transakce.

```
BOOL CommitTrans();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se aktualizace byly úspěšně potvrzeny; jinak 0. Pokud `CommitTrans` nezdaří, stav zdroje dat není definován. Je nutné zkontrolovat dat k určení stavu.

### <a name="remarks"></a>Poznámky

Transakce se skládá z řady volání `AddNew`, `Edit`, `Delete`, a `Update` členské funkce `CRecordset` objekt, který začal s voláním [BeginTrans](#begintrans) členskou funkci. `CommitTrans` potvrzení transakce. Ve výchozím nastavení se aktualizace potvrdí okamžitě; volání `BeginTrans` způsobí, že závazku aktualizace odložena až do `CommitTrans` je volána.

Až do okamžiku volání `CommitTrans` k ukončení transakce, můžete volat [vrácení zpět](#rollback) členskou funkci pro přerušení transakce a ponechání zdroje dat do původního stavu. Chcete-li spustit novou transakci, zavolejte `BeginTrans` znovu.

Další informace o transakcích, najdete v článku [transakce (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Příklad

  Přečtěte si článek [transakce: provádění transakcí v sadě záznamů (rozhraní ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

##  <a name="executesql"></a>  CDatabase::ExecuteSQL

Když budete potřebovat ke spuštění příkazu SQL přímo Zavolejte tuto členskou funkci.

```
void ExecuteSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>Parametry

*Ipszsql*<br/>
Ukazatel na řetězec zakončený hodnotou null obsahující platný příkaz SQL pro spuštění. Můžete předat [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Poznámky

Vytvoření příkazu jako řetězec zakončený hodnotou null. `ExecuteSQL` nevrátí datových záznamů. Pokud chcete použít pro záznamy, použijte objekt sady záznamů.

Většina příkazů pro zdroj dat jsou vydávány prostřednictvím objektů sady záznamů, které podporují příkazy pro výběr data, vkládání nových záznamů, odstranění záznamů a úpravy záznamů. Ale ne všechny funkce ODBC se přímo nepodporuje databázové třídy, v některých případech je nutné provést přímého volání SQL s `ExecuteSQL`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#13](../../mfc/codesnippet/cpp/cdatabase-class_4.cpp)]

##  <a name="getbookmarkpersistence"></a>  CDatabase::GetBookmarkPersistence

Voláním této členské funkce k určení trvalost záložky na objekt sady záznamů po určité operace.

```
DWORD GetBookmarkPersistence() const;
```

### <a name="return-value"></a>Návratová hodnota

Bitová maska, která jsou uvedeny operace, pomocí kterých záložky zachovat na objekt sady záznamů. Podrobnosti najdete v tématu poznámky.

### <a name="remarks"></a>Poznámky

Například, pokud zavoláte `CRecordset::GetBookmark` a následně zavolat `CRecordset::Requery`, Záložka získané z `GetBookmark` nemusí být platný. Měli byste zavolat `GetBookmarkPersistence` před voláním `CRecordset::SetBookmark`.

V následující tabulce jsou uvedeny hodnoty bitové masky, které mohou být kombinovány pro vrácenou hodnotu `GetBookmarkPersistence`.

|Hodnota bitové masky|Trvalost (záložky)|
|-------------------|--------------------------|
|SQL_BP_CLOSE|Záložky jsou platné po `Requery` operace.|
|SQL_BP_DELETE|Záložka pro řádek je platný po `Delete` operace na daném řádku.|
|SQL_BP_DROP|Záložky jsou platné po `Close` operace.|
|SQL_BP_SCROLL|Záložky jsou platné po všech `Move` operace. To jednoduše Určuje, zda v sadě záznamů, jsou podporovány záložky vrácené `CRecordset::CanBookmark`.|
|SQL_BP_TRANSACTION|Záložky jsou platné po je transakce potvrzena nebo vrácena zpět.|
|SQL_BP_UPDATE|Záložka pro řádek je platný po `Update` operace na daném řádku.|
|SQL_BP_OTHER_HSTMT|Záložky spojených s jedním objektem sady záznamů jsou platné v druhé sady záznamů.|

Další informace o tomto návratovou hodnotu, najdete v části funkce ODBC API `SQLGetInfo` v sadě Windows SDK. Další informace o záložky, najdete v článku [sada záznamů: záložky a absolutní pozice (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

##  <a name="getconnect"></a>  CDatabase::getconnect byla

Voláním této členské funkce se načíst připojovací řetězec použitý při volání `OpenEx` nebo `Open` připojeného `CDatabase` objekt ke zdroji dat.

```
const CString GetConnect() const;
```

### <a name="return-value"></a>Návratová hodnota

A **const**[CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahuje připojovací řetězec, pokud `OpenEx` nebo `Open` byl volaný; v opačném případě prázdný řetězec.

### <a name="remarks"></a>Poznámky

Zobrazit [CDatabase::Open](#open) popis vytvoření připojovacího řetězce.

##  <a name="getcursorcommitbehavior"></a>  CDatabase::GetCursorCommitBehavior

Voláním této členské funkce k určení jak [CommitTrans](#committrans) operace má vliv na ukazatele na objekty otevřít sadu záznamů.

```
int GetCursorCommitBehavior() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota označující vliv transakcí na objektech otevřít sadu záznamů. Podrobnosti najdete v tématu poznámky.

### <a name="remarks"></a>Poznámky

Následující tabulka obsahuje seznam možných vrácených hodnot pro `GetCursorCommitBehavior` a odpovídající vliv na Otevřít sadu záznamů.

|Návratová hodnota|Vliv na CRecordset – objekty|
|------------------|----------------------------------|
|SQL_CB_CLOSE|Volání `CRecordset::Requery` hned za potvrzení transakce.|
|SQL_CB_DELETE|Volání `CRecordset::Close` hned za potvrzení transakce.|
|SQL_CB_PRESERVE|Normálně pokračovat `CRecordset` operace.|

Další informace o tomto návratovou hodnotu, najdete v části funkce ODBC API `SQLGetInfo` v sadě Windows SDK. Další informace o transakcích, najdete v článku [transakce (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="getcursorrollbackbehavior"></a>  CDatabase::GetCursorRollbackBehavior

Voláním této členské funkce k určení jak [vrácení zpět](#rollback) operace má vliv na ukazatele na objekty otevřít sadu záznamů.

```
int GetCursorRollbackBehavior() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota označující vliv transakcí na objektech otevřít sadu záznamů. Podrobnosti najdete v tématu poznámky.

### <a name="remarks"></a>Poznámky

Následující tabulka obsahuje seznam možných vrácených hodnot pro `GetCursorRollbackBehavior` a odpovídající vliv na Otevřít sadu záznamů.

|Návratová hodnota|Vliv na CRecordset – objekty|
|------------------|----------------------------------|
|SQL_CB_CLOSE|Volání `CRecordset::Requery` ihned po vrácení transakce.|
|SQL_CB_DELETE|Volání `CRecordset::Close` ihned po vrácení transakce.|
|SQL_CB_PRESERVE|Normálně pokračovat `CRecordset` operace.|

Další informace o tomto návratovou hodnotu, najdete v části funkce ODBC API `SQLGetInfo` v sadě Windows SDK. Další informace o transakcích, najdete v článku [transakce (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="getdatabasename"></a>  CDatabase::GetDatabaseName

Voláním této členské funkce, aby se načetl název aktuálně připojené databáze (za předpokladu, že zdroje dat definuje objekt s názvem "databázi").

```
CString GetDatabaseName() const;
```

### <a name="return-value"></a>Návratová hodnota

A [CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahující název databáze v případě úspěchu; jinak, prázdná `CString`.

### <a name="remarks"></a>Poznámky

Toto není stejný jako název zdroje dat (DSN) podle `OpenEx` nebo `Open` volání. Co `GetDatabaseName` vrátí závisí na rozhraní ODBC. Obecně platí databázi je kolekce tabulek. Pokud tato entita má název, `GetDatabaseName` vrátí jej.

Můžete například zobrazit tento název v záhlaví. Pokud dojde k chybě při načítání názvu z rozhraní ODBC, `GetDatabaseName` vrátí prázdnou `CString`.

##  <a name="isopen"></a>  CDatabase::IsOpen

Voláním této členské funkce k určení, zda `CDatabase` objekt je nyní připojen ke zdroji dat.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulovou hodnotu, pokud `CDatabase` je aktuálně připojený objekt; jinak 0.

##  <a name="m_hdbc"></a>  CDatabase::m_hdbc

Obsahuje veřejné popisovač připojení ke zdroji dat rozhraní ODBC – "popisovač připojení".

### <a name="remarks"></a>Poznámky

Za normálních okolností bude mít přímý přístup k této proměnné člena není nutné. Místo toho rozhraní přiděluje úchytu při volání `OpenEx` nebo `Open`. Rozhraní framework zruší přidělení úchytu při volání **odstranit** operátoru u `CDatabase` objektu. Všimněte si, že `Close` členská funkce není uvolnit popisovač.

Za určitých okolností však budete muset použít popisovač přímo. Například, pokud je potřeba volat funkce rozhraní API ODBC přímo a nikoli v rámci třídy `CDatabase`, možná bude nutné předat jako parametr popisovač připojení. Najdete v následujícím příkladu kódu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#15](../../mfc/codesnippet/cpp/cdatabase-class_5.cpp)]

##  <a name="onsetoptions"></a>  CDatabase::OnSetOptions

Rozhraní volá tuto členskou funkci, pokud přímo spouštění příkazu SQL s `ExecuteSQL` členskou funkci.

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Parametry

*HSTMT*<br/>
Popisovač příkazu ODBC, pro které jsou nastavené možnosti.

### <a name="remarks"></a>Poznámky

`CRecordset::OnSetOptions` volá také tato členská funkce.

`OnSetOptions` Nastaví hodnotu časového limitu přihlášení. Pokud byly předchozí volání `SetQueryTimeout` a členskou funkci, `OnSetOptions` odráží aktuální hodnoty; jinak nastaví výchozí hodnoty.

> [!NOTE]
>  Před MFC 4.2 `OnSetOptions` také nastavit režim zpracování buď snychronous nebo asynchronní. Od verze 4.2 knihovny MFC, všechny operace jsou synchronní. K provádění asynchronní operace, je třeba přímého volání rozhraní API ODBC funkce `SQLSetPos`.

Není potřeba přepsat `OnSetOptions` Chcete-li změnit hodnotu časového limitu. Namísto toho pokud chcete přizpůsobit časový limit dotazu, zavolejte metodu `SetQueryTimeout` před vytvořením záznamů; `OnSetOptions` budou používat novou hodnotu. Sada hodnot platí pro následné operace na všech sad záznamů nebo přímá volání SQL.

Přepsat `OnSetOptions` Pokud chcete nastavit další možnosti. Přepsání by měly volat základní třídy `OnSetOptions` před nebo po volání funkce ODBC API `SQLSetStmtOption`. Postupujte podle metody v rozhraní framework výchozí implementace `OnSetOptions`.

##  <a name="open"></a>  CDatabase::Open

Voláním této členské funkce inicializace nově vytvořeného `CDatabase` objektu.

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
Určuje název zdroje dat – název registrovaný s rozhraním ODBC prostřednictvím programu Správce rozhraní ODBC. Pokud je zadaná hodnota názvu zdroje dat v *lpszConnect* (ve formě "DSN =\<zdroj dat >"), nemůže být zadán znovu v *lpszDSN*. V takovém případě *lpszDSN* by měl mít hodnotu NULL. Pokud chcete uživateli zprostředkovali dialogovému oknu zdroj dat, ve kterém může uživatel vybrat zdroj dat, v opačném případě můžete předat hodnotu NULL. Další informace najdete v tématu poznámky.

*bExclusive*<br/>
Není podporováno v této verzi knihovny tříd. V současné době kontrolní výraz selže, pokud tento parametr má hodnotu TRUE. Zdroj dat je vždy otevřít, protože sdílí (není výhradní).

*bReadOnly*<br/>
Hodnota TRUE, pokud máte v úmyslu připojení jen pro čtení a aktualizace zdroje dat můžete zakázat. Všechny závislé sady záznamů zdědí tento atribut. Výchozí hodnota je FALSE.

*lpszConnect*<br/>
Určuje připojovací řetězec. Připojovací řetězec zřetězí informace, včetně názvu zdroje dat, ID uživatele platné na zdroj dat, řetězec ověření uživatele (heslo, pokud je zdroj dat vyžaduje jednu) a další informace. Celý připojovací řetězec musí mít předponu řetězec "ODBC;" (malá i velká). "ODBC;" řetězec se používá k označení, zda je připojení ke zdroji dat rozhraní ODBC; To je z důvodu kompatibility stoupající při budoucích verzích knihovna tříd může podporovat zdroje dat – rozhraní ODBC.

*bUseCursorLib*<br/>
TRUE, pokud chcete, aby ODBC kurzor knihovna DLL, který se má načíst. Knihovna kurzorů rozhraní zakrývá některé funkce základní ovladač ODBC efektivně zabránit používání dynamické sady (Pokud ovladač je podporuje). Dopřednými kurzory podporována, pokud je načtena knihovna kurzorů rozhraní jsou statické snímků a dopředné kurzory. Výchozí hodnota je TRUE. Pokud chcete vytvořit objekt sady záznamů přímo z `CRecordset` bez odvození z něj, nesmí načítat knihovna kurzorů rozhraní.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud připojení úspěšné; v opačném případě 0, pokud uživatel vybere možnost zrušit převedou dialogové okno s žádostí o další informace o připojení. Ve všech ostatních případech rozhraní vyvolá výjimku.

### <a name="remarks"></a>Poznámky

Databázový objekt musí inicializovat před slouží k vytvoření objektu sady záznamů.

> [!NOTE]
>  Volání [OpenEx](#openex) členská funkce je preferovaný způsob, jak se připojit ke zdroji dat a inicializovat databázový objekt.

Pokud parametrům ve vaší `Open` volání neobsahují dostatek informací k vytvoření připojení, ovladač ODBC se otevře dialogové okno pro získání potřebných informací od uživatele. Při volání `Open`, připojovací řetězec *lpszConnect*, uložená ve skrytém `CDatabase` objektu a je k dispozici prostřednictvím volání [GetConnect](#getconnect) členskou funkci.

Pokud chcete, můžete otevřít dialogové okno Vlastní před voláním `Open` k získání informací od uživatele, jako jsou hesla, zadejte tyto informace na připojovací řetězec můžete předat `Open`. Nebo můžete chtít uložit připojovací řetězec předat, znovu ho můžete použít další čas volání aplikace `Open` na `CDatabase` objektu.

Připojovací řetězec můžete použít také pro několik úrovní autorizace přihlášení (každou pro jiný `CDatabase` objekt) nebo jiné informace specifické pro zdroj dat. Další informace o připojovacích řetězcích naleznete v kapitole 5 v sadě Windows SDK.

Je možné pro pokus o připojení k vypršení časového limitu, pokud je například DBMS hostitele není k dispozici. Pokud se nezdaří pokus o připojení, `Open` vyvolá `CDBException`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#14](../../mfc/codesnippet/cpp/cdatabase-class_6.cpp)]

##  <a name="openex"></a>  CDatabase::OpenEx

Voláním této členské funkce inicializace nově vytvořeného `CDatabase` objektu.

```
virtual BOOL OpenEx(
    LPCTSTR lpszConnectString,
    DWORD dwOptions = 0);
```

### <a name="parameters"></a>Parametry

*lpszConnectString*<br/>
Určuje připojovací řetězec ODBC. To zahrnuje název zdroje dat, stejně jako ostatní volitelné informace, jako je například ID uživatele a heslo. Například "DSN = SQLServer_Source; UID = SA; PWD = abc123 "je možné připojovací řetězec. Všimněte si, že pokud předáte hodnotu NULL *lpszConnectString*, dialogové okno zdroje dat se zobrazí výzva k výběru zdroje dat.

*dwOptions*<br/>
Bitová maska, které určuje kombinaci z následujících hodnot. Výchozí hodnota je 0, což znamená, že databáze se otevřou jako sdílí s oprávněním k zápisu, ODBC kurzor knihovna DLL se nenačte a dialogové okno připojení ODBC se zobrazí pouze v případě, že není k dispozici dostatek informací k vytvoření připojení.

- `CDatabase::openExclusive` Není podporováno v této verzi knihovny tříd. Zdroj dat je vždy otevřít, protože sdílí (není výhradní). V současné době kontrolní výraz selže, pokud zadáte tuto možnost.

- `CDatabase::openReadOnly` Otevřete zdroj dat jen pro čtení.

- `CDatabase::useCursorLib` Načtěte knihovna kurzorů rozhraní ODBC knihovny DLL. Knihovna kurzorů rozhraní zakrývá některé funkce základní ovladač ODBC efektivně zabránit používání dynamické sady (Pokud ovladač je podporuje). Dopřednými kurzory podporována, pokud je načtena knihovna kurzorů rozhraní jsou statické snímků a dopředné kurzory. Pokud chcete vytvořit objekt sady záznamů přímo z `CRecordset` bez odvození z něj, nesmí načítat knihovna kurzorů rozhraní.

- `CDatabase::noOdbcDialog` Nezobrazovat ODBC dialogovém okně připojení, bez ohledu na to, zda je zadaný dostatek informací o připojení.

- `CDatabase::forceOdbcDialog` Vždy zobrazte dialogové okno připojení ODBC.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud připojení úspěšné; v opačném případě 0, pokud uživatel vybere možnost zrušit převedou dialogové okno s žádostí o další informace o připojení. Ve všech ostatních případech rozhraní vyvolá výjimku.

### <a name="remarks"></a>Poznámky

Databázový objekt musí inicializovat před slouží k vytvoření objektu sady záznamů.

Pokud *lpszConnectString* parametr ve vaší `OpenEx` volání neobsahuje dostatek informací k vytvoření připojení, ovladač ODBC otevře dialogové okno k získání potřebných informací od uživatele, pokud ne Nastavte `CDatabase::noOdbcDialog` nebo `CDatabase::forceOdbcDialog` v *dwOptions* parametru. Při volání `OpenEx`, připojovací řetězec *lpszConnectString*, uložená ve skrytém `CDatabase` objektu a je k dispozici prostřednictvím volání [GetConnect](#getconnect) členskou funkci.

Pokud chcete, můžete otevřít dialogové okno Vlastní před voláním `OpenEx` k získání informací od uživatele, jako jsou hesla a pak přidejte tyto informace na připojovací řetězec můžete předat `OpenEx`. Nebo můžete chtít uložit připojovací řetězec předat, znovu ho můžete použít další čas volání aplikace `OpenEx` na `CDatabase` objektu.

Připojovací řetězec můžete použít také pro několik úrovní autorizace přihlášení (každou pro jiný `CDatabase` objekt) nebo jiné informace specifické pro zdroj dat. Další informace o připojovacích řetězcích naleznete v kapitole 6 v *ODBC programátora*.

Je možné pro pokus o připojení k vypršení časového limitu, pokud je například DBMS hostitele není k dispozici. Pokud se nezdaří pokus o připojení, `OpenEx` vyvolá `CDBException`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#11](../../mfc/codesnippet/cpp/cdatabase-class_7.cpp)]

##  <a name="rollback"></a>  CDatabase::Rollback

Voláním této členské funkce vrátit změny provedené během transakce.

```
BOOL Rollback();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud transakce byla úspěšně vrátit; jinak 0. Pokud `Rollback` volání selže, zdroje dat a transakce nejsou definovány stavy. Pokud `Rollback` vrátí hodnotu 0, je nutné zkontrolovat zdroje dat k určení stavu.

### <a name="remarks"></a>Poznámky

Všechny `CRecordset` `AddNew`, `Edit`, `Delete`, a `Update` volání provést, protože poslední [BeginTrans](#begintrans) se vrátí zpět do stavu, který existoval v okamžiku tohoto volání.

Po volání `Rollback`transakce je nad a je nutné volat `BeginTrans` znovu pro jinou transakcí. Záznam, který byl aktuální předtím, než jste volali `BeginTrans` se stává aktuálním záznamem znovu po `Rollback`.

Po vrácení zpět zůstane aktuální záznam, který byl aktuální před vrácení změn. Podrobnosti o stavu sady záznamů a zdroji dat po vrácení zpět, najdete v článku [transakce (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Příklad

  Přečtěte si článek [transakce: provádění transakcí v sadě záznamů (rozhraní ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

##  <a name="setlogintimeout"></a>  CDatabase::SetLoginTimeout

Voláním této členské funkce – před voláním `OpenEx` nebo `Open` – Chcete-li přepsat výchozí počet sekund může uplynout před pokus o datové připojení ke zdroji vyprší časový limit.

```
void SetLoginTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>Parametry

*dwSeconds*<br/>
Počet sekund před pokus o připojení vyprší časový limit.

### <a name="remarks"></a>Poznámky

Pokus o připojení může být vypršení časového limitu, je-li například systému DBMS není k dispozici. Volání `SetLoginTimeout` po sestavení neinicializovaného `CDatabase` objektu, ale před voláním `OpenEx` nebo `Open`.

Výchozí hodnota pro vypršení časového limitu pro přihlašovací jméno je 15 sekund. Ne všechny zdroje dat podporují možnost zadat hodnotu časového limitu přihlášení. Pokud zdroj dat nepodporuje časový limit, získáte výstup trasování, ale ne výjimku. Hodnota 0 znamená "nekonečné."

##  <a name="setquerytimeout"></a>  CDatabase::SetQueryTimeout

Voláním této členské funkce přepsat výchozí počet sekund před následné operace s připojené datové zdroje časový limit.

```
void SetQueryTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>Parametry

*dwSeconds*<br/>
Počet sekund před pokusu o dotaz vyprší časový limit.

### <a name="remarks"></a>Poznámky

Operace může časový limit z důvodu problémů s přístupem k síti, doba zpracování nadměrné dotazu a tak dále. Volání `SetQueryTimeout` před otevřením sady záznamů nebo před voláním sady záznamů `AddNew`, `Update` nebo `Delete` členské funkce, pokud chcete změnit hodnotu vypršení časového limitu dotazu. Toto nastavení ovlivňuje všechny následné `Open`, `AddNew`, `Update`, a `Delete` volání jakékoli sady záznamů přidružený k tomuto `CDatabase` objektu. Změna časový limit dotazu pro sadu záznamů po otevření nezmění hodnotu pro sady záznamů. Například následující `Move` operace nepoužívejte novou hodnotu.

Výchozí hodnota pro vypršení časového limitu dotazu je 15 sekund. Ne všechny zdroje dat podporují možnost nastavit hodnotu časového limitu dotazu. Pokud nastavíte hodnotu časového limitu dotazu 0, dojde k žádný časový limit; komunikace se zdrojem dat může přestat reagovat. Toto chování může být užitečné během vývoje. Pokud zdroj dat nepodporuje časový limit, získáte výstup trasování, ale ne výjimku.

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)
