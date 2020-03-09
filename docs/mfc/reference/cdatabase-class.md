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
ms.openlocfilehash: ebc36d82af9bfe12ab30a86214e58610b5eaab95
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866267"
---
# <a name="cdatabase-class"></a>CDatabase – třída

Představuje připojení ke zdroji dat, pomocí kterého můžete pracovat na zdroji dat.

## <a name="syntax"></a>Syntaxe

```
class CDatabase : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDatabase:: CDatabase](#cdatabase)|Vytvoří objekt `CDatabase`. Je nutné inicializovat objekt voláním `OpenEx` nebo `Open`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDatabase:: BeginTrans](#begintrans)|Spustí "transakci" – řada vratných volání do `AddNew`, `Edit`, `Delete`a `Update` členské funkce třídy `CRecordset` – na připojeném zdroji dat. Zdroj dat musí podporovat transakce, pro které `BeginTrans` mít nějaký účinek.|
|[CDatabase:: BindParameters](#bindparameters)|Umožňuje navázání parametrů před voláním `CDatabase::ExecuteSQL`.|
|[CDatabase:: Cancel](#cancel)|Zruší asynchronní operaci nebo proces z druhého vlákna.|
|[CDatabase:: CanTransact](#cantransact)|Vrátí nenulovou hodnotu, pokud zdroj dat podporuje transakce.|
|[CDatabase:: CanUpdate](#canupdate)|Vrátí nenulovou hodnotu, pokud je objekt `CDatabase` možné aktualizovat (není jen pro čtení).|
|[CDatabase:: Close](#close)|Zavře připojení ke zdroji dat.|
|[CDatabase:: CommitTrans](#committrans)|Dokončí transakci zahájenou `BeginTrans`. Příkazy v transakci, které mění zdroj dat, jsou prováděny.|
|[CDatabase:: ExecuteSQL](#executesql)|Provede příkaz SQL. Nevrátí se žádné datové záznamy.|
|[CDatabase:: GetBookmarkPersistence](#getbookmarkpersistence)|Identifikuje operace, kterými se záložky ukládají v objektech sady záznamů.|
|[CDatabase:: GetConnect](#getconnect)|Vrátí připojovací řetězec ODBC, který se používá pro připojení objektu `CDatabase` ke zdroji dat.|
|[CDatabase:: GetCursorCommitBehavior](#getcursorcommitbehavior)|Určuje účinek potvrzení transakce v otevřeném objektu sady záznamů.|
|[CDatabase:: GetCursorRollbackBehavior](#getcursorrollbackbehavior)|Určuje účinek vrácení transakce zpět k otevřenému objektu sady záznamů.|
|[CDatabase:: getdatabase](#getdatabasename)|Vrátí název databáze, která se právě používá.|
|[CDatabase:: Open](#isopen)|Vrátí nenulovou hodnotu, pokud je objekt `CDatabase` aktuálně připojen ke zdroji dat.|
|[CDatabase:: OnSetOptions](#onsetoptions)|Volá se rozhraním, aby se nastavily standardní možnosti připojení. Výchozí implementace nastavuje hodnotu časového limitu dotazu. Tyto možnosti můžete vytvořit před časem voláním `SetQueryTimeout`.|
|[CDatabase:: Open](#open)|Naváže připojení ke zdroji dat (prostřednictvím ovladače ODBC).|
|[CDatabase:: OpenEx](#openex)|Naváže připojení ke zdroji dat (prostřednictvím ovladače ODBC).|
|[CDatabase:: Rollback](#rollback)|Obrátí změny provedené během aktuální transakce. Zdroj dat se vrátí do předchozího stavu, jak je definováno ve volání `BeginTrans`, nezměněno.|
|[CDatabase:: SetLoginTimeout](#setlogintimeout)|Nastaví počet sekund, po jejichž uplynutí vyprší časový limit pokusu o připojení ke zdroji dat.|
|[CDatabase:: SetQueryTimeout](#setquerytimeout)|Nastaví počet sekund, po jejichž uplynutí vyprší platnost operací databázového dotazu. Má vliv na všechny následné sady záznamů `Open`, `AddNew`, `Edit`a `Delete` volání.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CDatabase:: m_hdbc](#m_hdbc)|Popisovač připojení rozhraní ODBC (Open Database Connectivity) ke zdroji dat. Zadejte *HDBC*.|

## <a name="remarks"></a>Poznámky

Zdroj dat je konkrétní instance dat hostovaných některými systémy správy databáze (DBMS). Mezi příklady patří Microsoft SQL Server, Microsoft Access, Borland dBASE a xBASE. Můžete mít v aplikaci aktivní jeden nebo více objektů `CDatabase`.

> [!NOTE]
>  Pokud pracujete s třídami objektů pro přístup k datům (DAO), nikoli s třídami rozhraní ODBC (Open Database Connectivity), místo toho použijte třídu [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) . Další informace najdete v článku [Přehled: programování databáze](../../data/data-access-programming-mfc-atl.md).

Chcete-li použít `CDatabase`, Sestavte objekt `CDatabase` a zavolejte jeho členskou funkci `OpenEx`. Tím se otevře připojení. Když potom vytvoříte `CRecordset` objektů pro práci na připojeném zdroji dat, předejte konstruktoru sady záznamů ukazatel na objekt `CDatabase`. Po dokončení používání připojení Zavolejte členskou funkci `Close` a odstraňte objekt `CDatabase`. `Close` zavře všechny sady záznamů, které jste předtím nezavřeli.

Další informace o `CDatabase`najdete v článcích [zdroj dat (ODBC)](../../data/odbc/data-source-odbc.md) a [Přehled: programování databáze](../../data/data-access-programming-mfc-atl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CDatabase`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFXDB. h

##  <a name="begintrans"></a>CDatabase:: BeginTrans

Zavolejte tuto členskou funkci pro zahájení transakce s připojeným zdrojem dat.

```
BOOL BeginTrans();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo volání úspěšné a změny jsou potvrzeny pouze ručně; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Transakce se skládá z jednoho nebo více volání `AddNew`, `Edit`, `Delete`a `Update` členské funkce objektu `CRecordset`. Před zahájením transakce již musí být objekt `CDatabase` připojen ke zdroji dat voláním jeho členské funkce `OpenEx` nebo `Open`. Chcete-li ukončit transakci, zavolejte metodu [CommitTrans](#committrans) , aby přijímala všechny změny zdroje dat (a převedla je), nebo zavolejte [zpět](#rollback) pro přerušení celé transakce. Po otevření všech sad záznamů, které jsou součástí transakce, zavolejte `BeginTrans` a co nejblíže skutečným operacím aktualizace.

> [!CAUTION]
>  V závislosti na ovladači ODBC otevření sady záznamů před voláním `BeginTrans` může způsobit problémy při volání `Rollback`. Měli byste si ověřit konkrétní ovladač, který používáte. Například při použití ovladače Microsoft Access, který je součástí sady Microsoft ODBC Desktop Driver Pack 3,0, je nutné uvést požadavek databázového stroje Jet, že byste neměli začínat transakci v žádné databázi, která má otevřený kurzor. Ve třídách databáze knihovny MFC představuje otevřený kurzor objekt Open `CRecordset`. Další informace najdete v části [Technická poznámka 68](../../mfc/tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver.md).

`BeginTrans` může také Uzamknout datové záznamy na serveru v závislosti na požadované souběžnosti a funkcích zdroje dat. Informace o uzamykání dat naleznete v článku [Sada záznamů: zamykání záznamů (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).

Uživatelsky definované transakce jsou vysvětleny v článku [transakce (ODBC)](../../data/odbc/transaction-odbc.md).

`BeginTrans` stanoví stav, ve kterém lze posloupnost transakcí vrátit zpět (obráceně). Chcete-li vytvořit nový stav pro vrácení zpět, potvrďte všechny aktuální transakce a potom zavolejte `BeginTrans` znovu.

> [!CAUTION]
>  Volání `BeginTrans` bez volání `CommitTrans` nebo `Rollback` je chyba.

Zavolejte členskou funkci [CanTransact](#cantransact) , abyste zjistili, jestli váš ovladač podporuje transakce pro danou databázi. Měli byste také volat [GetCursorCommitBehavior](#getcursorcommitbehavior) a [GetCursorRollbackBehavior](#getcursorrollbackbehavior) k určení podpory pro zachování kurzoru.

Další informace o transakcích naleznete v článku [transakce (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Příklad

  Viz článek [transakce: provádění transakce v sadě záznamů (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

##  <a name="bindparameters"></a>CDatabase:: BindParameters

Před voláním metody [CDatabase:: ExecuteSQL](#executesql)popište `BindParameters`, když potřebujete vytvořit vazby parametrů.

```
virtual void BindParameters(HSTMT hstmt);
```

### <a name="parameters"></a>Parametry

*hstmt*<br/>
Popisovač příkazu ODBC, pro který chcete vytvořit vazby parametrů.

### <a name="remarks"></a>Poznámky

Tento přístup je užitečný, pokud nepotřebujete sadu výsledků z uložené procedury.

Ve vašem přepsání volejte `SQLBindParameters` a související funkce rozhraní ODBC, abyste navázali parametry. Knihovna MFC volá vaše přepsání před voláním `ExecuteSQL`. Nemusíte volat `SQLPrepare`; `ExecuteSQL` volá `SQLExecDirect` a zničí *HSTMT*, který se používá jenom jednou.

##  <a name="cancel"></a>CDatabase:: Cancel

Tuto členskou funkci volejte pro vyžádání, že zdroj dat zruší buď probíhající asynchronní operaci, nebo proces z druhého vlákna.

```
void Cancel();
```

### <a name="remarks"></a>Poznámky

Všimněte si, že třídy knihovny MFC rozhraní ODBC již nepoužívají asynchronní zpracování; k provedení asynchronní operace je nutné přímo zavolat funkci rozhraní ODBC API [SQLSetConnectOption](/sql/odbc/reference/syntax/sqlsetconnectoption-function). Další informace najdete v tématu [asynchronní provádění](/sql/odbc/reference/develop-app/asynchronous-execution).

##  <a name="cantransact"></a>CDatabase:: CanTransact

Voláním této členské funkce určíte, zda databáze povoluje transakce.

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud sady záznamů používající tento objekt `CDatabase` povolují transakce; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Informace o transakcích naleznete v článku [transakce (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="canupdate"></a>CDatabase:: CanUpdate

Voláním této členské funkce určíte, zda objekt `CDatabase` povoluje aktualizace.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud objekt `CDatabase` povoluje aktualizace. jinak 0, což znamená, že při otevření objektu `CDatabase` nebo v samotném zdroji dat, který je jen pro čtení, jste předali hodnotu TRUE v *bReadOnly* . Zdroj dat je jen pro čtení, pokud volání funkce rozhraní ODBC API `SQLGetInfo` pro SQL_DATASOURCE_READ_ONLY vrátí "y".

### <a name="remarks"></a>Poznámky

Ne všechny ovladače podporují aktualizace.

##  <a name="cdatabase"></a>CDatabase:: CDatabase

Vytvoří objekt `CDatabase`.

```
CDatabase();
```

### <a name="remarks"></a>Poznámky

Po sestavení objektu je nutné zavolat jeho `OpenEx` nebo `Open` členské funkce k navázání připojení k zadanému zdroji dat.

Je možné, že bude vhodné vložit objekt `CDatabase` do třídy dokumentu.

### <a name="example"></a>Příklad

Tento příklad ukazuje použití `CDatabase` v třídě odvozené `CDocument`.

[!code-cpp[NVC_MFCDatabase#9](../../mfc/codesnippet/cpp/cdatabase-class_1.h)]

[!code-cpp[NVC_MFCDatabase#10](../../mfc/codesnippet/cpp/cdatabase-class_2.cpp)]

##  <a name="close"></a>CDatabase:: Close

Pokud se chcete odpojit od zdroje dat, zavolejte tuto členskou funkci.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Před voláním této členské funkce je nutné zavřít všechny sady záznamů spojené s objektem `CDatabase`. Vzhledem k tomu, že `Close` nezničí objekt `CDatabase`, můžete znovu použít objekt otevřením nového připojení ke stejnému zdroji dat nebo jinému zdroji dat.

Všechny nevyřízené `AddNew` nebo `Edit` příkazy sady záznamů používající databázi jsou zrušeny a všechny probíhající transakce jsou vráceny zpět. Jakékoli sady záznamů závislé na objektu `CDatabase` jsou ponechány v nedefinovaném stavu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#12](../../mfc/codesnippet/cpp/cdatabase-class_3.cpp)]

##  <a name="committrans"></a>CDatabase:: CommitTrans

Po dokončení transakcí volejte tuto členskou funkci.

```
BOOL CommitTrans();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byly aktualizace úspěšně potvrzeny; v opačném případě 0. Pokud `CommitTrans` dojde k chybě, stav zdroje dat není definován. Chcete-li zjistit stav, je nutné ověřit data.

### <a name="remarks"></a>Poznámky

Transakce se skládá z řady volání `AddNew`, `Edit`, `Delete`a `Update` členské funkce objektu `CRecordset`, který začal voláním členské funkce [BeginTrans](#begintrans) . `CommitTrans` potvrdí transakci. Ve výchozím nastavení se aktualizace potvrdí hned; volání `BeginTrans` způsobí, že se aktualizace budou zpozdit až do zavolání `CommitTrans`.

Dokud nebudete volat `CommitTrans` pro ukončení transakce, můžete zavolat členskou funkci [vrácení zpět](#rollback) pro přerušení transakce a ponechat zdroj dat v původním stavu. Chcete-li zahájit novou transakci, zavolejte `BeginTrans` znovu.

Další informace o transakcích naleznete v článku [transakce (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Příklad

  Viz článek [transakce: provádění transakce v sadě záznamů (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

##  <a name="executesql"></a>CDatabase:: ExecuteSQL

Tuto členskou funkci volejte, pokud potřebujete přímo spustit příkaz SQL.

```
void ExecuteSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>Parametry

*Ipszsql*<br/>
Ukazatel na řetězec zakončený hodnotou null obsahující platný příkaz SQL, který má být proveden. Můžete předat [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Poznámky

Vytvořte příkaz jako řetězec zakončený hodnotou null. `ExecuteSQL` nevrací datové záznamy. Pokud chcete pracovat se záznamy, použijte místo toho objekt sady záznamů.

Většina příkazů pro zdroj dat je vydávána prostřednictvím objektů sady záznamů, které podporují příkazy pro výběr dat, vkládání nových záznamů, odstraňování záznamů a úpravy záznamů. Ne všechny funkce rozhraní ODBC jsou však přímo podporovány databázovými třídami, takže možná budete muset vytvořit přímé volání SQL pomocí `ExecuteSQL`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#13](../../mfc/codesnippet/cpp/cdatabase-class_4.cpp)]

##  <a name="getbookmarkpersistence"></a>CDatabase:: GetBookmarkPersistence

Zavolejte tuto členskou funkci pro určení Persistence záložek objektu Recordset po určitých operacích.

```
DWORD GetBookmarkPersistence() const;
```

### <a name="return-value"></a>Návratová hodnota

Bitová maska, která identifikuje operace, pomocí kterých záložky zůstávají v objektu sady záznamů trvalé. Podrobnosti najdete v tématu poznámky.

### <a name="remarks"></a>Poznámky

Například pokud zavoláte `CRecordset::GetBookmark` a potom zavoláte `CRecordset::Requery`, záložka získaná z `GetBookmark` již nemusí být platná. Před voláním `CRecordset::SetBookmark`byste měli volat `GetBookmarkPersistence`.

Následující tabulka uvádí hodnoty bitových kopií, které lze kombinovat pro návratovou hodnotu `GetBookmarkPersistence`.

|Hodnota maskování|Trvalost záložky|
|-------------------|--------------------------|
|SQL_BP_CLOSE|Záložky jsou po operaci `Requery` platné.|
|SQL_BP_DELETE|Záložka pro řádek je platná po `Delete` operaci na daném řádku.|
|SQL_BP_DROP|Záložky jsou po operaci `Close` platné.|
|SQL_BP_SCROLL|Záložky jsou platné po `Move` operaci. To jednoduše identifikuje, zda jsou záložky podporovány v sadě záznamů, jak jsou vráceny `CRecordset::CanBookmark`.|
|SQL_BP_TRANSACTION|Záložky jsou platné poté, co je transakce potvrzena nebo vrácena zpět.|
|SQL_BP_UPDATE|Záložka pro řádek je platná po `Update` operaci na daném řádku.|
|SQL_BP_OTHER_HSTMT|Záložky přidružené k jednomu objektu sady záznamů jsou platné pro druhou sadu záznamů.|

Další informace o této vrácené hodnotě najdete v tématu funkce rozhraní ODBC API `SQLGetInfo` v Windows SDK. Další informace o záložkách naleznete v článku [Sada záznamů: záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

##  <a name="getconnect"></a>CDatabase:: GetConnect

Zavolejte tuto členskou funkci pro načtení připojovacího řetězce použitého při volání `OpenEx` nebo `Open`, který objekt `CDatabase` připojil ke zdroji dat.

```
const CString GetConnect() const;
```

### <a name="return-value"></a>Návratová hodnota

**Const**[CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahující připojovací řetězec, pokud byla volána `OpenEx` nebo `Open`; v opačném případě prázdný řetězec.

### <a name="remarks"></a>Poznámky

Popis způsobu vytvoření připojovacího řetězce naleznete v tématu [CDatabase:: Open](#open) .

##  <a name="getcursorcommitbehavior"></a>CDatabase:: GetCursorCommitBehavior

Voláním této členské funkce určíte, jak operace [CommitTrans](#committrans) ovlivňuje kurzory v otevřených objektech sady záznamů.

```
int GetCursorCommitBehavior() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která označuje účinek transakcí v otevřených objektech sady záznamů. Podrobnosti najdete v tématu poznámky.

### <a name="remarks"></a>Poznámky

V následující tabulce jsou uvedeny možné návratové hodnoty pro `GetCursorCommitBehavior` a odpovídající účinek na otevřené sady záznamů.

|Návratová hodnota|Efekt u objektů CRecordset|
|------------------|----------------------------------|
|SQL_CB_CLOSE|Ihned po potvrzení transakce zavolejte `CRecordset::Requery`.|
|SQL_CB_DELETE|Ihned po potvrzení transakce zavolejte `CRecordset::Close`.|
|SQL_CB_PRESERVE|Donormálně pokračujte s operacemi `CRecordset`.|

Další informace o této vrácené hodnotě najdete v tématu funkce rozhraní ODBC API `SQLGetInfo` v Windows SDK. Další informace o transakcích naleznete v článku [transakce (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="getcursorrollbackbehavior"></a>CDatabase:: GetCursorRollbackBehavior

Voláním této členské funkce určíte, jak operace [vrácení zpět](#rollback) ovlivní kurzory v otevřených objektech sady záznamů.

```
int GetCursorRollbackBehavior() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která označuje účinek transakcí v otevřených objektech sady záznamů. Podrobnosti najdete v tématu poznámky.

### <a name="remarks"></a>Poznámky

V následující tabulce jsou uvedeny možné návratové hodnoty pro `GetCursorRollbackBehavior` a odpovídající účinek na otevřené sady záznamů.

|Návratová hodnota|Efekt u objektů CRecordset|
|------------------|----------------------------------|
|SQL_CB_CLOSE|Ihned po vrácení transakce zavolejte `CRecordset::Requery`.|
|SQL_CB_DELETE|Ihned po vrácení transakce zavolejte `CRecordset::Close`.|
|SQL_CB_PRESERVE|Donormálně pokračujte s operacemi `CRecordset`.|

Další informace o této vrácené hodnotě najdete v tématu funkce rozhraní ODBC API `SQLGetInfo` v Windows SDK. Další informace o transakcích naleznete v článku [transakce (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="getdatabasename"></a>CDatabase:: getdatabase

Voláním této členské funkce načtěte název aktuálně připojené databáze (za předpokladu, že zdroj dat definuje pojmenovaný objekt s názvem "Database").

```
CString GetDatabaseName() const;
```

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu obsahuje [CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahující název databáze. v opačném případě prázdný `CString`.

### <a name="remarks"></a>Poznámky

Nejedná se o stejný název jako název zdroje dat (DSN) zadaný ve `OpenEx` nebo `Open` volání. To, co `GetDatabaseName` vrátí, závisí na rozhraní ODBC. Obecně je databáze kolekce tabulek. Pokud má tato entita název, `GetDatabaseName` ji vrátí.

Například můžete chtít zobrazit tento název v záhlaví. Pokud při načítání názvu z rozhraní ODBC dojde k chybě, `GetDatabaseName` vrátí prázdnou `CString`.

##  <a name="isopen"></a>CDatabase:: Open

Voláním této členské funkce určíte, zda je objekt `CDatabase` aktuálně připojen ke zdroji dat.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je objekt `CDatabase` aktuálně připojen; v opačném případě 0.

##  <a name="m_hdbc"></a>CDatabase:: m_hdbc

Obsahuje veřejný popisovač připojení ke zdroji dat ODBC – "popisovač připojení".

### <a name="remarks"></a>Poznámky

Obvykle nebude nutné přistupovat k této členské proměnné přímo. Místo toho rozhraní přiděluje popisovač při volání `OpenEx` nebo `Open`. Rozhraní uvolní popisovač při volání operátoru **Delete** u objektu `CDatabase`. Všimněte si, že členská funkce `Close` neuvolní popisovač.

Za určitých okolností ale možná budete muset použít popisovač přímo. Například pokud potřebujete volat funkce rozhraní ODBC API přímo, nikoli prostřednictvím třídy `CDatabase`, budete pravděpodobně potřebovat popisovač připojení, který bude předat jako parametr. Podívejte se na příklad kódu níže.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#15](../../mfc/codesnippet/cpp/cdatabase-class_5.cpp)]

##  <a name="onsetoptions"></a>CDatabase:: OnSetOptions

Rozhraní volá tuto členskou funkci při přímém spuštění příkazu jazyka SQL pomocí členské funkce `ExecuteSQL`.

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Parametry

*hstmt*<br/>
Popisovač příkazu ODBC, pro který mají být nastaveny možnosti.

### <a name="remarks"></a>Poznámky

`CRecordset::OnSetOptions` také volá tuto členskou funkci.

`OnSetOptions` nastaví hodnotu časového limitu přihlášení. Pokud jste nastavili předchozí volání `SetQueryTimeout` a členské funkce, `OnSetOptions` odráží aktuální hodnoty; v opačném případě nastaví výchozí hodnoty.

> [!NOTE]
>  Před knihovnou MFC 4,2 `OnSetOptions` také nastavit režim zpracování na hodnotu snychronous nebo asynchronní. Počínaje knihovnou MFC 4,2 jsou všechny operace synchronní. K provedení asynchronní operace je nutné provést přímé volání funkce rozhraní ODBC API `SQLSetPos`.

Pro změnu hodnoty timeout není nutné přepsat `OnSetOptions`. Místo toho pro přizpůsobení hodnoty časového limitu dotazu volejte `SetQueryTimeout` před vytvořením sady záznamů. `OnSetOptions` použije novou hodnotu. Hodnoty nastavené na další operace se vztahují na všechny sady záznamů nebo přímo volání SQL.

Pokud chcete nastavit další možnosti, popište `OnSetOptions`. Vaše přepsání by mělo volat základní třídu `OnSetOptions` buď před, nebo po volání funkce rozhraní ODBC API `SQLSetStmtOption`. Postupujte podle metody popsané ve výchozí implementaci `OnSetOptions`rozhraní.

##  <a name="open"></a>CDatabase:: Open

Zavolejte tuto členskou funkci pro inicializaci nově vytvořeného objektu `CDatabase`.

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
Určuje název zdroje dat – název zaregistrovaný v rozhraní ODBC prostřednictvím programu Správce rozhraní ODBC. Pokud je v *lpszConnect* zadána hodnota DSN (ve formě "DSN =\<data-source >"), nesmí být zadána znovu v *lpszDSN*. V takovém případě by měl mít *lpszDSN* hodnotu null. Jinak můžete předat hodnotu NULL, pokud chcete uživateli prezentovat dialogové okno zdroje dat, ve kterém může uživatel vybrat zdroj dat. Další informace najdete v tématu poznámky.

*bExclusive*<br/>
Nepodporováno v této verzi knihovny tříd. V současné době se kontrolní výraz nezdařil, pokud je tento parametr TRUE. Zdroj dat je vždy otevřen jako sdílený (neexkluzivní).

*bReadOnly*<br/>
Hodnota TRUE, pokud chcete, aby připojení bylo jen pro čtení a aby bylo zakázáno aktualizace zdroje dat. Všechny závislé sady záznamů dědí tento atribut. Výchozí hodnota je FALSE (NEPRAVDA).

*lpszConnect*<br/>
Určuje připojovací řetězec. Připojovací řetězec zřetězí informace, například název zdroje dat, ID uživatele platný ve zdroji dat, ověřovací řetězec uživatele (heslo, pokud zdroj dat vyžaduje jednu) a další informace. Celý připojovací řetězec musí být předponou řetězcem "ODBC;". (velká a malá písmena). Řetězec "ODBC;" slouží k označení toho, že připojení je zdrojem dat ODBC; Jedná se o kompatibilitu směrem nahoru, pokud budoucí verze knihovny tříd mohou podporovat zdroje dat, které nejsou typu ODBC.

*bUseCursorLib*<br/>
TRUE, pokud chcete načíst knihovnu DLL knihovny kurzorů rozhraní ODBC. Knihovna kurzorů maskuje některé funkce základního ovladače ODBC, což efektivně zabraňuje použití dynamických sad (Pokud je ovladač podporuje). Pouze kurzory jsou podporovány, pokud je knihovna kurzorů načtena, statickými snímky a kurzory, které jsou pouze dopředné. Výchozí hodnota je TRUE (pravda). Pokud máte v úmyslu vytvořit objekt sady záznamů přímo z `CRecordset` bez jeho odvozování, neměli byste načíst knihovnu kurzorů.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo připojení úspěšně provedeno; v opačném případě 0, pokud uživatel vybere možnost zrušit, když se zobrazí dialogové okno s žádostí o další informace o připojení. Ve všech ostatních případech rozhraní vyvolá výjimku.

### <a name="remarks"></a>Poznámky

Aby bylo možné vytvořit objekt sady záznamů, je nutné inicializovat objekt databáze.

> [!NOTE]
>  Volání členské funkce [OpenEx](#openex) je preferovaným způsobem, jak se připojit ke zdroji dat a inicializovat databázový objekt.

Pokud parametry ve volání `Open` neobsahují dostatek informací pro vytvoření připojení, ovladač ODBC otevře dialogové okno, které získá informace potřebné od uživatele. Při volání `Open`je připojovací řetězec *lpszConnect*uložen soukromě v objektu `CDatabase` a je k dispozici voláním členské funkce [GetConnect](#getconnect) .

Pokud chcete, můžete otevřít vlastní dialogové okno před voláním `Open` a získat informace od uživatele, jako je třeba heslo, a pak tyto informace přidat do připojovacího řetězce, který předáte do `Open`. Nebo můžete chtít uložit připojovací řetězec, který předáte, abyste ho mohli znovu použít při příštím volání aplikace `Open` na objektu `CDatabase`.

Můžete také použít připojovací řetězec pro více úrovní autorizace přihlášení (každý pro jiný objekt `CDatabase`) nebo předat jiné informace specifické pro zdroj dat. Další informace o připojovacích řetězcích naleznete v kapitole 5 v Windows SDK.

Je možné, že se pokus o připojení vyprší, pokud například není k dispozici hostitel DBMS. Pokud se pokus o připojení nezdaří, `Open` vyvolá `CDBException`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#14](../../mfc/codesnippet/cpp/cdatabase-class_6.cpp)]

##  <a name="openex"></a>CDatabase:: OpenEx

Zavolejte tuto členskou funkci pro inicializaci nově vytvořeného objektu `CDatabase`.

```
virtual BOOL OpenEx(
    LPCTSTR lpszConnectString,
    DWORD dwOptions = 0);
```

### <a name="parameters"></a>Parametry

*lpszConnectString*<br/>
Určuje připojovací řetězec ODBC. To zahrnuje název zdroje dat i další volitelné informace, jako je ID uživatele a heslo. Například "DSN = SQLServer_Source; UID = SA; PWD = abc123 "je možný připojovací řetězec. Všimněte si, že pokud předáte hodnotu NULL pro *lpszConnectString*, dialogové okno zdroje dat vyzve uživatele k výběru zdroje dat.

*dwOptions*<br/>
Bitová maska, která určuje kombinaci následujících hodnot. Výchozí hodnota je 0, což znamená, že databáze bude otevřena jako sdílená s přístupem pro zápis, knihovna DLL knihovny kurzorů ODBC nebude načtena a dialogové okno připojení ODBC se zobrazí pouze v případě, že k vytvoření připojení není dostatek informací.

- `CDatabase::openExclusive` není v této verzi knihovny tříd podporován. Zdroj dat je vždy otevřen jako sdílený (neexkluzivní). V současné době se kontrolní výraz při zadání této možnosti nezdařil.

- `CDatabase::openReadOnly` otevřít zdroj dat jen pro čtení.

- `CDatabase::useCursorLib` načíst knihovnu DLL knihovny kurzorů rozhraní ODBC. Knihovna kurzorů maskuje některé funkce základního ovladače ODBC, což efektivně zabraňuje použití dynamických sad (Pokud je ovladač podporuje). Pouze kurzory jsou podporovány, pokud je knihovna kurzorů načtena, statickými snímky a kurzory, které jsou pouze dopředné. Pokud máte v úmyslu vytvořit objekt sady záznamů přímo z `CRecordset` bez jeho odvozování, neměli byste načíst knihovnu kurzorů.

- `CDatabase::noOdbcDialog` dialogové okno připojení ODBC se nezobrazují bez ohledu na to, zda jsou dodány dostatečné informace o připojení.

- `CDatabase::forceOdbcDialog` vždy zobrazovat dialogové okno připojení ODBC.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo připojení úspěšně provedeno; v opačném případě 0, pokud uživatel vybere možnost zrušit, když se zobrazí dialogové okno s žádostí o další informace o připojení. Ve všech ostatních případech rozhraní vyvolá výjimku.

### <a name="remarks"></a>Poznámky

Aby bylo možné vytvořit objekt sady záznamů, je nutné inicializovat objekt databáze.

Pokud parametr *lpszConnectString* ve vašem volání `OpenEx` neobsahuje dostatek informací pro vytvoření připojení, ovladač ODBC otevře dialogové okno pro získání informací potřebných od uživatele, pokud jste v parametru *dwoptions* nezadali `CDatabase::noOdbcDialog` nebo `CDatabase::forceOdbcDialog`. Při volání `OpenEx`je připojovací řetězec *lpszConnectString*uložen soukromě v objektu `CDatabase` a je k dispozici voláním členské funkce [GetConnect](#getconnect) .

Pokud chcete, můžete otevřít vlastní dialogové okno před voláním `OpenEx` a získat informace od uživatele, jako je například heslo, a pak tyto informace přidat do připojovacího řetězce, který předáte do `OpenEx`. Nebo můžete chtít uložit připojovací řetězec, který předáte, abyste ho mohli znovu použít při příštím volání aplikace `OpenEx` na objektu `CDatabase`.

Můžete také použít připojovací řetězec pro více úrovní autorizace přihlášení (každý pro jiný objekt `CDatabase`) nebo předat jiné informace specifické pro zdroj dat. Další informace o připojovacích řetězcích naleznete v kapitole 6 v *Referenční příručce programátora ODBC*.

Je možné, že se pokus o připojení vyprší, pokud například není k dispozici hostitel DBMS. Pokud se pokus o připojení nezdaří, `OpenEx` vyvolá `CDBException`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#11](../../mfc/codesnippet/cpp/cdatabase-class_7.cpp)]

##  <a name="rollback"></a>CDatabase:: Rollback

Zavolejte tuto členskou funkci pro vrácení změn provedených během transakce.

```
BOOL Rollback();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla transakce úspěšně stornována; v opačném případě 0. Pokud se `Rollback` nezdařil, není definován stav zdroje dat a transakce. Pokud `Rollback` vrátí hodnotu 0, je nutné zjistit stav zdroje dat.

### <a name="remarks"></a>Poznámky

Všechna `CRecordset` volání `AddNew`, `Edit`, `Delete`a `Update` spouštěná od poslední [BeginTrans](#begintrans) jsou vrácena zpět do stavu, který existoval v době volání.

Po volání `Rollback`je transakce překročena a je nutné volat `BeginTrans` znovu pro jinou transakci. Záznam, který byl aktuální předtím, než jste volali `BeginTrans` bude aktuální záznam po `Rollback`znovu.

Po vrácení zpět zůstane záznam, který byl aktuální před vrácením změn, aktuální. Podrobnosti o stavu sady záznamů a zdroji dat po vrácení zpět naleznete v článku [transakce (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Příklad

  Viz článek [transakce: provádění transakce v sadě záznamů (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

##  <a name="setlogintimeout"></a>CDatabase:: SetLoginTimeout

Volejte tuto členskou funkci – před voláním `OpenEx` nebo `Open` – pro přepsání výchozího počtu sekund povolených, než vyprší časový limit připojení ke zdroji dat.

```
void SetLoginTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>Parametry

*dwSeconds*<br/>
Počet sekund povolených před vypršením časového limitu pokusu o připojení.

### <a name="remarks"></a>Poznámky

Při pokusu o připojení by například systém DBMS není k dispozici. Po vytvoření neinicializovaného objektu `CDatabase` zavolejte `SetLoginTimeout`, ale před voláním `OpenEx` nebo `Open`.

Výchozí hodnota pro časový limit přihlášení je 15 sekund. Ne všechny zdroje dat podporují možnost zadat hodnotu časového limitu přihlášení. Pokud zdroj dat nepodporuje časový limit, získáte výstup trasování, ale nikoli výjimku. Hodnota 0 znamená "nekonečno".

##  <a name="setquerytimeout"></a>CDatabase:: SetQueryTimeout

Tuto členskou funkci zavolejte, pokud chcete přepsat výchozí počet sekund, který se povolí předtím, než dojde k vypršení časového limitu dalších operací na připojeném zdroji dat.

```
void SetQueryTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>Parametry

*dwSeconds*<br/>
Počet sekund povolených před vypršením časového limitu dotazu.

### <a name="remarks"></a>Poznámky

Kvůli problémům s přístupem k síti, nadměrnému zpracování dotazů a tak dále může dojít k vypršení časového limitu operace. Chcete-li změnit hodnotu časového limitu dotazu, zavolejte `SetQueryTimeout` před otevřením sady záznamů nebo před voláním `AddNew`, `Update` nebo `Delete` členských funkcí sady záznamů. Toto nastavení má vliv na všechny následné `Open`, `AddNew`, `Update`a `Delete` volání do jakékoli sady záznamů přidružené k tomuto `CDatabase` objektu. Změna hodnoty časového limitu dotazu pro sadu záznamů po otevření nemění hodnotu sady záznamů. Například následné operace `Move` nepoužívají novou hodnotu.

Výchozí hodnota pro vypršení časového limitu dotazu je 15 sekund. Ne všechny zdroje dat podporují možnost nastavit hodnotu časového limitu dotazu. Pokud nastavíte hodnotu časového limitu dotazu 0, nedojde k žádnému vypršení časového limitu. komunikace se zdrojem dat může přestat reagovat. Toto chování může být užitečné při vývoji. Pokud zdroj dat nepodporuje časový limit, získáte výstup trasování, ale nikoli výjimku.

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)
