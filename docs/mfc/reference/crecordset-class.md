---
title: CRecordset – třída
ms.date: 11/04/2016
f1_keywords:
- CRecordset
- AFXDB/CRecordset
- AFXDB/CRecordset::CRecordset
- AFXDB/CRecordset::AddNew
- AFXDB/CRecordset::CanAppend
- AFXDB/CRecordset::CanBookmark
- AFXDB/CRecordset::Cancel
- AFXDB/CRecordset::CancelUpdate
- AFXDB/CRecordset::CanRestart
- AFXDB/CRecordset::CanScroll
- AFXDB/CRecordset::CanTransact
- AFXDB/CRecordset::CanUpdate
- AFXDB/CRecordset::CheckRowsetError
- AFXDB/CRecordset::Close
- AFXDB/CRecordset::Delete
- AFXDB/CRecordset::DoBulkFieldExchange
- AFXDB/CRecordset::DoFieldExchange
- AFXDB/CRecordset::Edit
- AFXDB/CRecordset::FlushResultSet
- AFXDB/CRecordset::GetBookmark
- AFXDB/CRecordset::GetDefaultConnect
- AFXDB/CRecordset::GetDefaultSQL
- AFXDB/CRecordset::GetFieldValue
- AFXDB/CRecordset::GetODBCFieldCount
- AFXDB/CRecordset::GetODBCFieldInfo
- AFXDB/CRecordset::GetRecordCount
- AFXDB/CRecordset::GetRowsetSize
- AFXDB/CRecordset::GetRowsFetched
- AFXDB/CRecordset::GetRowStatus
- AFXDB/CRecordset::GetSQL
- AFXDB/CRecordset::GetStatus
- AFXDB/CRecordset::GetTableName
- AFXDB/CRecordset::IsBOF
- AFXDB/CRecordset::IsDeleted
- AFXDB/CRecordset::IsEOF
- AFXDB/CRecordset::IsFieldDirty
- AFXDB/CRecordset::IsFieldNull
- AFXDB/CRecordset::IsFieldNullable
- AFXDB/CRecordset::IsOpen
- AFXDB/CRecordset::Move
- AFXDB/CRecordset::MoveFirst
- AFXDB/CRecordset::MoveLast
- AFXDB/CRecordset::MoveNext
- AFXDB/CRecordset::MovePrev
- AFXDB/CRecordset::OnSetOptions
- AFXDB/CRecordset::OnSetUpdateOptions
- AFXDB/CRecordset::Open
- AFXDB/CRecordset::RefreshRowset
- AFXDB/CRecordset::Requery
- AFXDB/CRecordset::SetAbsolutePosition
- AFXDB/CRecordset::SetBookmark
- AFXDB/CRecordset::SetFieldDirty
- AFXDB/CRecordset::SetFieldNull
- AFXDB/CRecordset::SetLockingMode
- AFXDB/CRecordset::SetParamNull
- AFXDB/CRecordset::SetRowsetCursorPosition
- AFXDB/CRecordset::SetRowsetSize
- AFXDB/CRecordset::Update
- AFXDB/CRecordset::m_hstmt
- AFXDB/CRecordset::m_nFields
- AFXDB/CRecordset::m_nParams
- AFXDB/CRecordset::m_pDatabase
- AFXDB/CRecordset::m_strFilter
- AFXDB/CRecordset::m_strSort
helpviewer_keywords:
- CRecordset [MFC], CRecordset
- CRecordset [MFC], AddNew
- CRecordset [MFC], CanAppend
- CRecordset [MFC], CanBookmark
- CRecordset [MFC], Cancel
- CRecordset [MFC], CancelUpdate
- CRecordset [MFC], CanRestart
- CRecordset [MFC], CanScroll
- CRecordset [MFC], CanTransact
- CRecordset [MFC], CanUpdate
- CRecordset [MFC], CheckRowsetError
- CRecordset [MFC], Close
- CRecordset [MFC], Delete
- CRecordset [MFC], DoBulkFieldExchange
- CRecordset [MFC], DoFieldExchange
- CRecordset [MFC], Edit
- CRecordset [MFC], FlushResultSet
- CRecordset [MFC], GetBookmark
- CRecordset [MFC], GetDefaultConnect
- CRecordset [MFC], GetDefaultSQL
- CRecordset [MFC], GetFieldValue
- CRecordset [MFC], GetODBCFieldCount
- CRecordset [MFC], GetODBCFieldInfo
- CRecordset [MFC], GetRecordCount
- CRecordset [MFC], GetRowsetSize
- CRecordset [MFC], GetRowsFetched
- CRecordset [MFC], GetRowStatus
- CRecordset [MFC], GetSQL
- CRecordset [MFC], GetStatus
- CRecordset [MFC], GetTableName
- CRecordset [MFC], IsBOF
- CRecordset [MFC], IsDeleted
- CRecordset [MFC], IsEOF
- CRecordset [MFC], IsFieldDirty
- CRecordset [MFC], IsFieldNull
- CRecordset [MFC], IsFieldNullable
- CRecordset [MFC], IsOpen
- CRecordset [MFC], Move
- CRecordset [MFC], MoveFirst
- CRecordset [MFC], MoveLast
- CRecordset [MFC], MoveNext
- CRecordset [MFC], MovePrev
- CRecordset [MFC], OnSetOptions
- CRecordset [MFC], OnSetUpdateOptions
- CRecordset [MFC], Open
- CRecordset [MFC], RefreshRowset
- CRecordset [MFC], Requery
- CRecordset [MFC], SetAbsolutePosition
- CRecordset [MFC], SetBookmark
- CRecordset [MFC], SetFieldDirty
- CRecordset [MFC], SetFieldNull
- CRecordset [MFC], SetLockingMode
- CRecordset [MFC], SetParamNull
- CRecordset [MFC], SetRowsetCursorPosition
- CRecordset [MFC], SetRowsetSize
- CRecordset [MFC], Update
- CRecordset [MFC], m_hstmt
- CRecordset [MFC], m_nFields
- CRecordset [MFC], m_nParams
- CRecordset [MFC], m_pDatabase
- CRecordset [MFC], m_strFilter
- CRecordset [MFC], m_strSort
ms.assetid: dd89a21d-ef39-4aab-891b-1e373d67c855
ms.openlocfilehash: 1ebdb18254171d28b5d5e02367596b79142df284
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626193"
---
# <a name="crecordset-class"></a>CRecordset – třída

Představuje sadu záznamů vybraných ze zdroje dat.

## <a name="syntax"></a>Syntaxe

```
class CRecordset : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CRecordset:: CRecordset](#crecordset)|Vytvoří objekt `CRecordset`. Vaše odvozená třída musí poskytovat konstruktor, který volá tuto třídu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CRecordset:: AddNew](#addnew)|Připraví pro přidání nového záznamu. Dokončete přidání voláním `Update`.|
|[CRecordset:: CanAppend](#canappend)|Vrátí nenulovou hodnotu, pokud je možné přidat nové záznamy do sady záznamů prostřednictvím členské funkce `AddNew`.|
|[CRecordset:: CanBookmark](#canbookmark)|Vrátí nenulovou hodnotu, pokud sada záznamů podporuje záložky.|
|[CRecordset:: Cancel](#cancel)|Zruší asynchronní operaci nebo proces z druhého vlákna.|
|[CRecordset:: CancelUpdate](#cancelupdate)|Zruší všechny probíhající aktualizace z důvodu operace `AddNew` nebo `Edit`.|
|[CRecordset:: CanRestart](#canrestart)|Vrátí nenulovou hodnotu, pokud je možné volat `Requery` pro opětovné spuštění dotazu sady záznamů.|
|[CRecordset:: CanScroll](#canscroll)|Vrátí nenulovou hodnotu, pokud můžete procházet záznamy.|
|[CRecordset:: CanTransact](#cantransact)|Vrátí nenulovou hodnotu, pokud zdroj dat podporuje transakce.|
|[CRecordset:: CanUpdate](#canupdate)|Vrátí nenulovou hodnotu, pokud může být sada záznamů aktualizována (můžete přidat, aktualizovat nebo odstranit záznamy).|
|[CRecordset:: CheckRowsetError](#checkrowseterror)|Volá se, aby se zpracovaly chyby generované při načítání záznamu.|
|[CRecordset:: Close](#close)|Zavře sadu záznamů a HSTMT rozhraní ODBC, které je k němu přidružené.|
|[CRecordset::D dstranit](#delete)|Odstraní aktuální záznam ze sady záznamů. Po odstranění musíte explicitně přejít na jiný záznam.|
|[CRecordset::D oBulkFieldExchange](#dobulkfieldexchange)|Volá se, aby se vyměnily hromadné řádky dat ze zdroje dat do sady záznamů. Implementuje hromadnou výměnu pole záznamu (Bulk RFX).|
|[CRecordset::D oFieldExchange](#dofieldexchange)|Volá se k výměně dat (v obou směrech) mezi datovými členy pole sady záznamů a odpovídajícím záznamem ve zdroji dat. Implementuje výměnu pole záznamu (RFX).|
|[CRecordset:: Edit](#edit)|Připraví změny aktuálního záznamu. Pro dokončení úpravy zavolejte `Update`.|
|[CRecordset:: FlushResultSet](#flushresultset)|Vrátí nenulovou hodnotu, pokud existuje další sada výsledků, která má být načtena při použití předdefinovaného dotazu.|
|[CRecordset:: GetBookmark](#getbookmark)|Přiřadí hodnotu záložky záznamu k objektu Parameter.|
|[CRecordset:: GetDefaultConnect](#getdefaultconnect)|Volá se, aby se získal výchozí připojovací řetězec.|
|[CRecordset:: GetDefaultSQL](#getdefaultsql)|Volá se, aby se získal výchozí řetězec SQL, který se má provést.|
|[CRecordset:: GetFieldValue –](#getfieldvalue)|Vrátí hodnotu pole v sadě záznamů.|
|[CRecordset:: GetODBCFieldCount](#getodbcfieldcount)|Vrátí počet polí v sadě záznamů.|
|[CRecordset:: GetODBCFieldInfo](#getodbcfieldinfo)|Vrátí konkrétní druhy informací o polích v sadě záznamů.|
|[CRecordset:: GetRecordCount](#getrecordcount)|Vrátí počet záznamů v sadě záznamů.|
|[CRecordset:: GetRowsetSize](#getrowsetsize)|Vrátí počet záznamů, které chcete načíst během jednoho načtení.|
|[CRecordset:: GetRowsFetched](#getrowsfetched)|Vrátí skutečný počet řádků načtených během načítání.|
|[CRecordset:: GetRowStatus](#getrowstatus)|Vrátí stav řádku po načtení.|
|[CRecordset:: GetSQL](#getsql)|Získá řetězec SQL, který slouží k výběru záznamů pro sadu záznamů.|
|[CRecordset:: GetStatus](#getstatus)|Získá stav sady záznamů: index aktuálního záznamu a zda byl získán konečný počet záznamů.|
|[CRecordset:: GetTable.](#gettablename)|Získá název tabulky, na které je založena sada záznamů.|
|[CRecordset:: IsBOF](#isbof)|Vrátí nenulovou hodnotu, pokud byla sada záznamů umístěna před první záznam. Neexistuje aktuální záznam.|
|[CRecordset:: IsDeleted odstraněno](#isdeleted)|Vrátí nenulovou hodnotu, pokud je sada záznamů umístěna na odstraněný záznam.|
|[CRecordset:: IsEOF](#iseof)|Vrátí nenulovou hodnotu, pokud byla sada záznamů umístěna za posledním záznamem. Neexistuje aktuální záznam.|
|[CRecordset:: IsFieldDirty](#isfielddirty)|Vrátí nenulovou hodnotu, pokud je zadané pole v aktuálním záznamu změněno.|
|[CRecordset:: IsFieldNull](#isfieldnull)|Vrátí nenulovou hodnotu, pokud zadané pole v aktuálním záznamu má hodnotu null (nemá žádnou hodnotu).|
|[CRecordset:: IsFieldNullable](#isfieldnullable)|Vrátí nenulovou hodnotu, pokud zadané pole v aktuálním záznamu může být nastaveno na hodnotu null (bez hodnoty).|
|[CRecordset:: Open](#isopen)|Vrátí nenulovou hodnotu, pokud byla dříve volána `Open`.|
|[CRecordset:: Move](#move)|Umístí sadu záznamů na zadaný počet záznamů z aktuálního záznamu v obou směrech.|
|[CRecordset:: MoveFirst](#movefirst)|Umístí aktuální záznam na první záznam v sadě záznamů. Nejprve otestujte `IsBOF`.|
|[CRecordset:: MoveLast](#movelast)|Umístí aktuální záznam na poslední záznam nebo poslední sadu řádků. Nejprve otestujte `IsEOF`.|
|[CRecordset:: MoveNext](#movenext)|Umístí aktuální záznam na další záznam nebo na další sadu řádků. Nejprve otestujte `IsEOF`.|
|[CRecordset:: MovePrev](#moveprev)|Umístí aktuální záznam na předchozí záznam nebo na předchozí sadu řádků. Nejprve otestujte `IsBOF`.|
|[CRecordset:: OnSetOptions](#onsetoptions)|Volá se, aby se nastavily možnosti (používané pro výběr) pro zadaný příkaz ODBC.|
|[CRecordset:: OnSetUpdateOptions](#onsetupdateoptions)|Volá se, aby se nastavily možnosti (používané při aktualizaci) pro zadaný příkaz ODBC.|
|[CRecordset:: Open](#open)|Otevře sadu záznamů načtením tabulky nebo provedením dotazu, který sada záznamů představuje.|
|[CRecordset:: RefreshRowset](#refreshrowset)|Aktualizuje data a stav zadaných řádků.|
|[CRecordset:: Requery](#requery)|Spustí znovu dotaz sady záznamů pro aktualizaci vybraných záznamů.|
|[CRecordset:: SetAbsolutePosition](#setabsoluteposition)|Umístí sadu záznamů na záznamu odpovídající zadanému číslu záznamu.|
|[CRecordset:: SetBookmark](#setbookmark)|Umístí sadu záznamů na záznam určený záložkou.|
|[CRecordset:: SetFieldDirty](#setfielddirty)|Označí zadané pole v aktuálním záznamu jako změněné.|
|[CRecordset:: SetFieldNull](#setfieldnull)|Nastaví hodnotu zadaného pole v aktuálním záznamu na hodnotu null (bez hodnoty).|
|[CRecordset:: SetLockingMode](#setlockingmode)|Nastaví režim uzamykání na "optimistické" zamykání (výchozí) nebo "pesimistické" zamykání. Určuje způsob uzamčení záznamů pro aktualizace.|
|[CRecordset:: SetParamNull](#setparamnull)|Nastaví zadaný parametr na hodnotu null (nemá žádnou hodnotu).|
|[CRecordset:: SetRowsetCursorPosition](#setrowsetcursorposition)|Umístí kurzor na zadaný řádek v rámci sady řádků.|
|[CRecordset:: SetRowsetSize](#setrowsetsize)|Určuje počet záznamů, které chcete načíst během načítání.|
|[CRecordset:: Update](#update)|Dokončí operaci `AddNew` nebo `Edit` uložením nových nebo upravených dat ve zdroji dat.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CRecordset:: m_hstmt](#m_hstmt)|Obsahuje popisovač příkazu ODBC pro sadu záznamů. Zadejte `HSTMT`.|
|[CRecordset:: m_nFields](#m_nfields)|Obsahuje počet datových členů pole v sadě záznamů. Zadejte `UINT`.|
|[CRecordset:: m_nParams](#m_nparams)|Obsahuje počet datových členů parametrů v sadě záznamů. Zadejte `UINT`.|
|[CRecordset:: m_pDatabase](#m_pdatabase)|Obsahuje ukazatel na objekt `CDatabase`, pomocí kterého je sada záznamů připojena ke zdroji dat.|
|[CRecordset:: m_strFilter](#m_strfilter)|Obsahuje `CString`, který určuje klauzuli `WHERE` jazyk SQL (Structured Query Language) (SQL). Slouží jako filtr k výběru pouze těch záznamů, které splňují určitá kritéria.|
|[CRecordset:: m_strSort](#m_strsort)|Obsahuje `CString`, který určuje klauzuli SQL `ORDER BY`. Slouží k řízení způsobu řazení záznamů.|

## <a name="remarks"></a>Mark

Známé jako "sady záznamů", "`CRecordset` objekty jsou obvykle používány ve dvou formách: dynamické sady a snímky. Dynamická sada zůstane synchronizovaná s aktualizacemi dat provedenými ostatními uživateli. Snímek je statické zobrazení dat. Každý formulář představuje sadu záznamů, které jsou opraveny v okamžiku otevření sady záznamů, ale při posunu na záznam v dynamické sadě odrážejí změny provedené v záznamu, a to buď jinými uživateli, nebo jinými sadami záznamů ve vaší aplikaci.

> [!NOTE]
>  Pokud pracujete s třídami objektů pro přístup k datům (DAO), nikoli s třídami rozhraní ODBC (Open Database Connectivity), místo toho použijte třídu [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) . Další informace najdete v článku [Přehled: programování databáze](../../data/data-access-programming-mfc-atl.md).

Chcete-li pracovat s libovolným druhem sady záznamů, obvykle je odvozena třída sady záznamů specifická pro aplikaci z `CRecordset`. Sady záznamů vybírají záznamy ze zdroje dat a pak můžete:

- Procházejte záznamy.

- Aktualizujte záznamy a zadejte režim uzamykání.

- Filtrováním sady záznamů omezíte, které záznamy vybírají z těch, které jsou k dispozici ve zdroji dat.

- Seřaďte sadu záznamů.

- Parametrizovat sadu záznamů pro přizpůsobení jejího výběru s informacemi, které nejsou známy až do doby běhu.

Chcete-li použít třídu, otevřete databázi a vytvořte objekt sady záznamů a předejte konstruktoru ukazatel na objekt `CDatabase`. Pak zavolejte členskou funkci `Open` sady záznamů, kde můžete určit, zda je objekt sadou a snímkem. Volání `Open` vybere data ze zdroje dat. Po otevření objektu sady záznamů použijte jeho členské funkce a datové členy pro procházení záznamů a jejich provoz. Dostupné operace závisí na tom, zda je objekt sadou funkcí nebo snímku, zda je možné jej aktualizovat nebo je jen pro čtení (to závisí na schopnosti zdroje dat ODBC (Open Database Connectivity)) a zda jste implementovali hromadné načítání řádků. Chcete-li aktualizovat záznamy, které mohly být změněny nebo přidány od volání `Open`, zavolejte členskou funkci objektu `Requery`. Voláním členské funkce objektu `Close` a zničením objektu po jeho dokončení.

V odvozené `CRecordset` třídě, výměna pole záznamu (RFX) nebo hromadná výměna pole záznamu (Bulk RFX) slouží k podpoře čtení a aktualizace polí záznamu.

Další informace o sadách záznamů a výměně polí záznamů naleznete v článku Přehled článků [: programování databáze](../../data/data-access-programming-mfc-atl.md), [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md), [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)a [záznam výměny pole (RFX)](../../data/odbc/record-field-exchange-rfx.md). Chcete-li se zaměřit na dynamické sady a snímky, přečtěte si článek [dynamická sada](../../data/odbc/dynaset.md) a [snímek](../../data/odbc/snapshot.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CRecordset`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFXDB. h

##  <a name="addnew"></a>CRecordset:: AddNew

Připraví pro přidání nového záznamu do tabulky.

```
virtual void AddNew();
```

### <a name="remarks"></a>Poznámky

Chcete-li zobrazit nově přidaný záznam, je nutné zavolat členskou funkci [Requery](#requery) . Pole záznamu mají počáteční hodnotu null. (V terminologii databáze hodnota null znamená "nemá žádnou hodnotu" a není shodná s hodnotou NULL v C++.) K dokončení této operace je nutné zavolat členskou funkci [Update](#update) . `Update` uloží změny do zdroje dat.

> [!NOTE]
>  Pokud jste implementovali hromadné načítání řádků, nemůžete volat `AddNew`. Výsledkem bude selhání kontrolního výrazu. I když `CRecordset` třídy neposkytuje mechanismus pro aktualizaci hromadných řádků dat, můžete napsat vlastní funkce pomocí funkce rozhraní ODBC API `SQLSetPos`. Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`AddNew` připraví nový prázdný záznam pomocí datových členů pole sady záznamů. Po volání `AddNew`nastavte požadované hodnoty v datových členech pole sady záznamů. (Není nutné volat členskou funkci [Edit](#edit) pro tento účel; použijte `Edit` pouze pro existující záznamy.) Když následně zavoláte `Update`, změněné hodnoty v polích datových členů jsou uloženy ve zdroji dat.

> [!CAUTION]
>  Pokud se posunete k novému záznamu před voláním `Update`, nový záznam bude ztracen a nebude zadáno žádné upozornění.

Pokud zdroj dat podporuje transakce, můžete provést `AddNew` volání části transakce. Další informace o transakcích naleznete v tématu Class [CDatabase](../../mfc/reference/cdatabase-class.md). Všimněte si, že před voláním `AddNew`byste měli zavolat metodu [CDatabase:: BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) .

> [!NOTE]
>  Pro dynamické sady jsou do sady záznamů přidány nové záznamy jako poslední záznam. Přidané záznamy se do snímků nepřidaly. Chcete-li aktualizovat sadu záznamů, je nutné volat `Requery`.

Je neplatné volat `AddNew` pro sadu záznamů, jejíž členská funkce `Open` nebyla volána. `CDBException` je vyvolána, pokud zavoláte `AddNew` pro sadu záznamů, ke které nelze připojit. Můžete určit, zda lze sadu záznamů aktualizovat voláním [CanAppend](#canappend).

Další informace naleznete v následujících článcích: [Sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md), [Sada záznamů: Přidání, aktualizace a odstranění záznamů (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)a [transakce (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Příklad

Viz článek [transakce: provádění transakce v sadě záznamů (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

##  <a name="canappend"></a>CRecordset:: CanAppend

Určuje, zda je dříve otevřená sada záznamů povolena k přidání nových záznamů.

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud sada záznamů povoluje přidávání nových záznamů; v opačném případě 0. `CanAppend` vrátí 0, pokud jste sadu záznamů otevřeli jako jen pro čtení.

##  <a name="canbookmark"></a>CRecordset:: CanBookmark

Určuje, zda sada záznamů umožňuje označovat záznamy pomocí záložek.

```
BOOL CanBookmark() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud sada záznamů podporuje záložky; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato funkce je nezávislá na možnosti `CRecordset::useBookmarks` v parametru *dwOptions* v [otevřené](#open) členské funkci. `CanBookmark` určuje, zda daný typ ovladače ODBC a kurzor podporují záložky. `CRecordset::useBookmarks` určuje, zda budou k dispozici záložky za předpokladu, že jsou podporovány.

> [!NOTE]
>  Záložky nejsou podporovány pro sady záznamů s dopřednou podporou.

Další informace o záložkách a navigaci v sadě záznamů naleznete v článcích [Sada záznamů: záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) a [Sada záznamů: posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

##  <a name="cancel"></a>CRecordset:: Cancel

Požaduje, aby zdroj dat zrušil buď probíhající asynchronní operaci, nebo proces z druhého vlákna.

```
void Cancel();
```

### <a name="remarks"></a>Poznámky

Všimněte si, že třídy knihovny MFC rozhraní ODBC již nepoužívají asynchronní zpracování; k provedení operace asynchronní je nutné přímo zavolat funkci rozhraní ODBC API `SQLSetConnectOption`. Další informace naleznete v tématu "spouštění funkcí asynchronně" v *příručce programátora sady ODBC SDK*.

##  <a name="cancelupdate"></a>CRecordset:: CancelUpdate

Před voláním metody [Update](#update) zruší všechny probíhající aktualizace způsobené operací [Edit](#edit) nebo [AddNew](#addnew) .

```
void CancelUpdate();
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Tato členská funkce se nedá použít pro sady záznamů, které používají hromadné načítání řádků, protože takové sady záznamů nemohou volat `Edit`, `AddNew`nebo `Update`. Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Je-li povolena automatická kontrola nevyřízených polí, `CancelUpdate` obnoví členské proměnné na hodnoty, které existovaly před voláním `Edit` nebo `AddNew`. v opačném případě budou všechny změny hodnot zůstat. Ve výchozím nastavení je automatická kontrola polí povolena při otevření sady záznamů. Chcete-li jej zakázat, je nutné zadat `CRecordset::noDirtyFieldCheck` v parametru *dwOptions* funkce [otevřít](#open) členskou funkci.

Další informace o aktualizaci dat naleznete v článku [Sada záznamů: Přidání, aktualizace a odstranění záznamů (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md).

##  <a name="canrestart"></a>CRecordset:: CanRestart

Určuje, zda sada záznamů umožňuje restartování dotazu (pro aktualizaci svých záznamů) voláním členské funkce `Requery`.

```
BOOL CanRestart() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je povoleno opakované dotazování; v opačném případě 0.

##  <a name="canscroll"></a>CRecordset:: CanScroll

Určuje, zda sada záznamů umožňuje posouvání.

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud sada záznamů umožňuje posouvání; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Další informace o posouvání naleznete v článku [Sada záznamů: posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

##  <a name="cantransact"></a>CRecordset:: CanTransact

Určuje, zda sada záznamů povoluje transakce.

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud sada záznamů povoluje transakce; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Další informace najdete v článku [transakce (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="canupdate"></a>CRecordset:: CanUpdate

Určuje, zda může být sada záznamů aktualizována.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je možné sadu záznamů aktualizovat; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Sada záznamů může být pouze pro čtení, pokud je podkladový zdroj dat určen jen pro čtení, nebo pokud jste zadali `CRecordset::readOnly` v parametru *dwOptions* při otevření sady záznamů.

##  <a name="checkrowseterror"></a>CRecordset:: CheckRowsetError

Volá se, aby se zpracovaly chyby generované při načítání záznamu.

```
virtual void CheckRowsetError(RETCODE nRetCode);
```

### <a name="parameters"></a>Parametry

*nRetCode*<br/>
Návratový kód funkce rozhraní API ODBC. Podrobnosti najdete v tématu poznámky.

### <a name="remarks"></a>Poznámky

Tato virtuální členská funkce zpracovává chyby, ke kterým dochází při načítání záznamů, a je užitečné při hromadném načítání řádků. Možná budete chtít zvážit přepsání `CheckRowsetError` k implementaci vlastního zpracování chyb.

`CheckRowsetError` se zavolá automaticky v navigační operaci kurzoru, jako je například `Open`, `Requery`nebo jakákoli `Move` operace. Je předána návratovou hodnotou funkce rozhraní ODBC API `SQLExtendedFetch`. Následující tabulka uvádí možné hodnoty parametru *nRetCode* .

|nRetCode|Popis|
|--------------|-----------------|
|SQL_SUCCESS|Funkce byla úspěšně dokončena; žádné další informace nejsou k dispozici.|
|SQL_SUCCESS_WITH_INFO|Funkce byla úspěšně dokončena, pravděpodobně s nezávažnou chybou. Další informace lze získat voláním `SQLError`.|
|SQL_NO_DATA_FOUND|Byly načteny všechny řádky ze sady výsledků dotazu.|
|SQL_ERROR|Funkce se nezdařila. Další informace lze získat voláním `SQLError`.|
|SQL_INVALID_HANDLE|Funkce se nezdařila kvůli neplatnému popisovači prostředí, popisovači připojení nebo popisovači příkazů. To znamená chybu při programování. Z `SQLError`nejsou k dispozici žádné další informace.|
|SQL_STILL_EXECUTING|Funkce, která byla spuštěna asynchronně, je stále prováděna. Všimněte si, že ve výchozím nastavení nebude knihovna MFC nikdy předána tuto hodnotu do `CheckRowsetError`; Knihovna MFC bude pokračovat v volání `SQLExtendedFetch`, dokud již nevrátí SQL_STILL_EXECUTING.|

Další informace o `SQLError`najdete v Windows SDK. Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="close"></a>CRecordset:: Close

Zavře sadu záznamů.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Rozhraní ODBC HSTMT a veškerá paměť rozhraní, které je přiděleno rozhraní pro sadu záznamů, se oddělují. Obvykle po volání `Close`odstraníte objekt C++ Recordset, pokud byl přidělen s **novým**.

Po volání `Close`můžete volat `Open` znovu. To umožňuje znovu použít objekt sady záznamů. Alternativou je volání `Requery`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#17](../../mfc/codesnippet/cpp/crecordset-class_1.cpp)]

##  <a name="crecordset"></a>CRecordset:: CRecordset

Vytvoří objekt `CRecordset`.

```
CRecordset(CDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>Parametry

*pDatabase*<br/>
Obsahuje ukazatel na objekt `CDatabase` nebo hodnotu NULL. Pokud hodnota není NULL a členská funkce `CDatabase`ho objektu `Open` nebyla volána pro jeho připojení ke zdroji dat, sada záznamů se ji pokusí otevřít během vlastního volání `Open`. Pokud předáte hodnotu NULL, objekt `CDatabase` je vytvořen a připojen k vám pomocí informací o zdroji dat, které jste zadali při odvození třídy sady záznamů pomocí ClassWizard.

### <a name="remarks"></a>Poznámky

Můžete buď použít `CRecordset` přímo nebo odvodit třídu specifickou pro aplikaci z `CRecordset`. Pomocí ClassWizard můžete odvodit vaše třídy sady záznamů.

> [!NOTE]
>  Odvozená třída *musí* poskytovat svůj vlastní konstruktor. V konstruktoru odvozené třídy volejte `CRecordset::CRecordset`konstruktoru a předejte příslušné parametry spolu s ním.

Předat hodnotu NULL konstruktoru sady záznamů, aby měl objekt `CDatabase` vytvořen a připojen automaticky. Toto je užitečnou zkratku, která nevyžaduje vytvoření a připojení objektu `CDatabase` před sestavením sady záznamů.

### <a name="example"></a>Příklad

Další informace naleznete v článku [Sada záznamů: Deklarování třídy pro tabulku (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).

##  <a name="delete"></a>CRecordset::D dstranit

Odstraní aktuální záznam.

```
virtual void Delete();
```

### <a name="remarks"></a>Poznámky

Po úspěšném odstranění jsou datové členy pole sady záznamů nastaveny na hodnotu null a je nutné explicitně volat jednu z `Move` funkcí, aby bylo možné přesunout odstraněný záznam. Po přesunutí odstraněného záznamu není možné se k němu vrátit. Pokud zdroj dat podporuje transakce, můžete provést `Delete` volání části transakce. Další informace najdete v článku [transakce (ODBC)](../../data/odbc/transaction-odbc.md).

> [!NOTE]
>  Pokud jste implementovali hromadné načítání řádků, nemůžete volat `Delete`. Výsledkem bude selhání kontrolního výrazu. I když `CRecordset` třídy neposkytuje mechanismus pro aktualizaci hromadných řádků dat, můžete napsat vlastní funkce pomocí funkce rozhraní ODBC API `SQLSetPos`. Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!CAUTION]
>  Sada záznamů musí být aktualizovatelná a při volání `Delete`musí být aktuální záznam v sadě záznamů platný. v opačném případě dojde k chybě. Pokud například odstraníte záznam, ale nebudete se posouvat k novému záznamu předtím, než `Delete` znovu zavoláte, `Delete` vyvolá výjimku [CDBException](../../mfc/reference/cdbexception-class.md).

Na rozdíl od metody [AddNew](#addnew) a [Edit](#edit)není volání `Delete` následováno voláním metody [Update](#update). Pokud se `Delete` volání nezdařilo, datové členy pole zůstanou beze změny.

### <a name="example"></a>Příklad

Tento příklad ukazuje sadu záznamů vytvořenou v rámci funkce. Příklad předpokládá existenci `m_dbCust`, členská proměnná typu `CDatabase` již byla připojena ke zdroji dat.

[!code-cpp[NVC_MFCDatabase#18](../../mfc/codesnippet/cpp/crecordset-class_2.cpp)]

##  <a name="dobulkfieldexchange"></a>CRecordset::D oBulkFieldExchange

Volá se, aby se vyměnily hromadné řádky dat ze zdroje dat do sady záznamů. Implementuje hromadnou výměnu pole záznamu (Bulk RFX).

```
virtual void DoBulkFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel na objekt [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) . Rozhraní již nastaví tento objekt pro určení kontextu operace výměny pole.

### <a name="remarks"></a>Poznámky

Když je implementováno hromadné načítání řádků, volá rozhraní tuto členskou funkci, aby automaticky přenesla data ze zdroje dat do objektu sady záznamů. `DoBulkFieldExchange` také váže datové členy parametrů, pokud existují, na zástupné symboly parametrů v řetězci příkazu SQL pro výběr sady záznamů.

Pokud není implementováno hromadné načítání řádků, rozhraní volá metodu [DoFieldExchange](#dofieldexchange). Chcete-li implementovat hromadné načítání řádků, je nutné zadat možnost `CRecordset::useMultiRowFetch` parametru *dwOptions* v [otevřené](#open) členské funkci.

> [!NOTE]
> `DoBulkFieldExchange` je k dispozici pouze v případě, že používáte třídu odvozenou z `CRecordset`. Pokud jste vytvořili objekt sady záznamů přímo z `CRecordset`, je nutné zavolat členskou funkci [GetFieldValue –](#getfieldvalue) pro načtení dat.

Hromadná výměna pole záznamu (Bulk RFX) se podobá výměně pole záznamu (RFX). Data se automaticky přenesou ze zdroje dat do objektu sady záznamů. Nemůžete však volat `AddNew`, `Edit`, `Delete`nebo `Update` pro přenos změn zpět do zdroje dat. Třída `CRecordset` v současné době neposkytuje mechanismus pro aktualizaci hromadných řádků dat; pomocí `SQLSetPos`funkce rozhraní ODBC API ale můžete napsat vlastní funkce.

Všimněte si, že ClassWizard nepodporuje hromadnou výměnu pole záznamu; Proto je nutné přepsat `DoBulkFieldExchange` ručně zápisem volání funkcí hromadného RFX. Další informace o těchto funkcích najdete v tématu [funkce výměny pole záznamu](../../mfc/reference/record-field-exchange-functions.md)v tématu.

Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Související informace naleznete v článku [Výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md).

##  <a name="dofieldexchange"></a>CRecordset::D oFieldExchange

Volá se k výměně dat (v obou směrech) mezi datovými členy pole sady záznamů a odpovídajícím záznamem ve zdroji dat. Implementuje výměnu pole záznamu (RFX).

```
virtual void DoFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel na objekt [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) . Rozhraní již nastaví tento objekt pro určení kontextu operace výměny pole.

### <a name="remarks"></a>Poznámky

Pokud není implementováno hromadné načítání řádků, volá rozhraní tuto členskou funkci, aby automaticky vyměnila data mezi poli datových členů objektu Recordset a odpovídající sloupce aktuálního záznamu ve zdroji dat. `DoFieldExchange` také váže datové členy parametrů, pokud existují, na zástupné symboly parametrů v řetězci příkazu SQL pro výběr sady záznamů.

Pokud je implementováno hromadné načítání řádků, volá rozhraní [DoBulkFieldExchange](#dobulkfieldexchange). Chcete-li implementovat hromadné načítání řádků, je nutné zadat možnost `CRecordset::useMultiRowFetch` parametru *dwOptions* v [otevřené](#open) členské funkci.

> [!NOTE]
> `DoFieldExchange` je k dispozici pouze v případě, že používáte třídu odvozenou z `CRecordset`. Pokud jste vytvořili objekt sady záznamů přímo z `CRecordset`, je nutné zavolat členskou funkci [GetFieldValue –](#getfieldvalue) pro načtení dat.

Výměna dat polí označovaná jako výměna pole záznamu (RFX), funguje v obou směrech: z datových členů pole objektu sady záznamů do polí záznamu ve zdroji dat a ze záznamu ve zdroji dat do objektu sady záznamů.

Jediná akce, kterou je třeba obvykle provést k implementaci `DoFieldExchange` pro odvozenou třídu sady záznamů, je vytvoření třídy pomocí ClassWizard a určení názvů a datových typů datových členů pole. Můžete také přidat kód, který zapisuje ClassWizard zápisy pro určení parametrů datových členů nebo pro práci s dalšími sloupci, které svážete dynamicky. Další informace naleznete v článku [Sada záznamů: dynamické vazby datových sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Při deklaraci odvozené třídy sady záznamů pomocí ClassWizard průvodce zapíše přepsání `DoFieldExchange` pro vás, které se podobá následujícímu příkladu:

[!code-cpp[NVC_MFCDatabase#19](../../mfc/codesnippet/cpp/crecordset-class_3.cpp)]

Další informace o funkcích RFX naleznete v tématu [funkce výměny pole záznamu](../../mfc/reference/record-field-exchange-functions.md)v tématu.

Další příklady a podrobnosti o `DoFieldExchange`najdete v článku [Výměna pole záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Obecné informace o RFX najdete v článku [Výměna pole záznamu](../../data/odbc/record-field-exchange-rfx.md).

##  <a name="edit"></a>CRecordset:: Edit

Umožňuje změny v aktuálním záznamu.

```
virtual void Edit();
```

### <a name="remarks"></a>Poznámky

Po volání `Edit`můžete změnit datové členy pole přímo obnovením jejich hodnot. Operace je dokončena, pokud následně zavoláte členskou funkci [Update](#update) pro uložení změn ve zdroji dat.

> [!NOTE]
>  Pokud jste implementovali hromadné načítání řádků, nemůžete volat `Edit`. Výsledkem bude selhání kontrolního výrazu. I když `CRecordset` třídy neposkytuje mechanismus pro aktualizaci hromadných řádků dat, můžete napsat vlastní funkce pomocí funkce rozhraní ODBC API `SQLSetPos`. Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`Edit` ukládá hodnoty datových členů sady záznamů. Pokud voláte `Edit`, proveďte změny a zavolejte `Edit` znovu, hodnoty záznamu budou obnoveny na to, co byly před prvním `Edit` volání.

V některých případech můžete chtít sloupec aktualizovat tak, že ho nastavíte na hodnotu null (neobsahuje žádná data). Uděláte to tak, že zavoláte [SetFieldNull](#setfieldnull) s parametrem true k označení pole null. tím také dojde k aktualizaci sloupce. Pokud chcete, aby pole bylo zapsáno do zdroje dat, i když se jeho hodnota nezměnila, zavolejte [SetFieldDirty](#setfielddirty) s parametrem true. To funguje i v případě, že pole má hodnotu null.

Pokud zdroj dat podporuje transakce, můžete provést `Edit` volání části transakce. Všimněte si, že před voláním `Edit` a po otevření sady záznamů byste měli zavolat metodu [CDatabase:: BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) . Všimněte si také, že volání [CDatabase:: CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) není náhradou za volání `Update` k dokončení operace `Edit`. Další informace o transakcích naleznete v tématu Class [CDatabase](../../mfc/reference/cdatabase-class.md).

V závislosti na aktuálním režimu uzamykání může být aktualizovaný záznam zamčený `Edit` dokud nebudete volat `Update` nebo posuňte na jiný záznam, nebo může být uzamčen pouze během `Edit` volání. Režim uzamykání můžete změnit pomocí [SetLockingMode](#setlockingmode).

Předchozí hodnota aktuálního záznamu se obnoví, pokud se před voláním `Update`posunete k novému záznamu. Pokud zavoláte `Edit` pro sadu záznamů, kterou nelze aktualizovat, nebo pokud neexistuje žádný aktuální záznam, je vyvolána `CDBException`.

Další informace najdete v článcích [transakce (ODBC)](../../data/odbc/transaction-odbc.md) a [Sada záznamů: zamykání záznamů (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#20](../../mfc/codesnippet/cpp/crecordset-class_4.cpp)]

##  <a name="flushresultset"></a>CRecordset:: FlushResultSet

Načte další sadu výsledků předdefinovaného dotazu (uložené procedury), pokud existuje více sad výsledků.

```
BOOL FlushResultSet();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud existuje více sad výsledků, které mají být načteny; v opačném případě 0.

### <a name="remarks"></a>Poznámky

`FlushResultSet` byste měli volat pouze v případě, že jste úplně dokončili kurzor na aktuální sadě výsledků dotazu. Všimněte si, že při načítání další sady výsledků voláním `FlushResultSet`není ukazatel platný v této sadě výsledků. Po volání `FlushResultSet`byste měli zavolat členskou funkci [MoveNext](#movenext) .

Pokud předdefinovaný dotaz používá výstupní parametr nebo vstupní/výstupní parametry, je nutné volat `FlushResultSet`, dokud nevrátí hodnotu `FALSE` (hodnota 0), aby bylo možné získat tyto hodnoty parametrů.

`FlushResultSet` volá funkci rozhraní ODBC API `SQLMoreResults`. Pokud `SQLMoreResults` Vrátí SQL_ERROR nebo SQL_INVALID_HANDLE, pak `FlushResultSet` vyvolá výjimku. Další informace o `SQLMoreResults`najdete v Windows SDK.

Vaše uložená procedura musí mít vázaná pole, pokud chcete volat `FlushResultSet`.

### <a name="example"></a>Příklad

Následující kód předpokládá, že `COutParamRecordset` je objekt odvozený `CRecordset`na základě předdefinovaného dotazu se vstupním parametrem a výstupním parametrem a má více sad výsledků. Všimněte si struktury přepsání [DoFieldExchange](#dofieldexchange) .

[!code-cpp[NVC_MFCDatabase#21](../../mfc/codesnippet/cpp/crecordset-class_5.cpp)]

[!code-cpp[NVC_MFCDatabase#22](../../mfc/codesnippet/cpp/crecordset-class_6.cpp)]

##  <a name="getbookmark"></a>CRecordset:: GetBookmark

Získá hodnotu záložky pro aktuální záznam.

```
void GetBookmark(CDBVariant& varBookmark);
```

### <a name="parameters"></a>Parametry

*varBookmark*<br/>
Odkaz na objekt [CDBVariant –](../../mfc/reference/cdbvariant-class.md) představující záložku na aktuálním záznamu.

### <a name="remarks"></a>Poznámky

Chcete-li zjistit, zda jsou záložky v sadě záznamů podporovány, zavolejte [CanBookmark](#canbookmark). Chcete-li zpřístupnit záložky, pokud jsou podporovány, je nutné nastavit možnost `CRecordset::useBookmarks` v parametru *dwOptions* pro [otevřenou](#open) členskou funkci.

> [!NOTE]
>  Pokud záložky nejsou podporovány nebo nejsou k dispozici, volání `GetBookmark` bude mít za následek vyvolanou výjimku. Záložky nejsou podporovány pro sady záznamů s dopřednou podporou.

`GetBookmark` přiřadí hodnotu záložky pro aktuální záznam do objektu `CDBVariant`. Chcete-li se k záznamu vrátit kdykoli po přesunu na jiný záznam, zavolejte [SetBookmark](#setbookmark) s odpovídajícím objektem `CDBVariant`.

> [!NOTE]
>  Po určitých operacích sady záznamů již nemusí být záložky platné. Například pokud voláte `GetBookmark` následovaný `Requery`, pravděpodobně se nebudete moci vrátit k záznamu pomocí `SetBookmark`. Voláním [CDatabase:: GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) zkontrolujete, jestli můžete bezpečně volat `SetBookmark`.

Další informace o záložkách a navigaci v sadě záznamů naleznete v článcích [Sada záznamů: záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) a [Sada záznamů: posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

##  <a name="getdefaultconnect"></a>CRecordset:: GetDefaultConnect

Volá se, aby se získal výchozí připojovací řetězec.

```
virtual CString GetDefaultConnect();
```

### <a name="return-value"></a>Návratová hodnota

`CString`, který obsahuje výchozí připojovací řetězec.

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto členskou funkci, aby získala výchozí připojovací řetězec pro zdroj dat, na kterém je založena sada záznamů. ClassWizard implementuje tuto funkci za vás tím, že identifikuje stejný zdroj dat, který používáte v ClassWizard, aby získal informace o tabulkách a sloupcích. Pravděpodobně bude vhodné spoléhat na toto výchozí připojení při vývoji aplikace. Výchozí připojení ale nemusí být vhodné pro uživatele vaší aplikace. V takovém případě byste měli tuto funkci znovu implementovat a zahodí verzi ClassWizard. Další informace o připojovacích řetězcích najdete v článku [zdroj dat (ODBC)](../../data/odbc/data-source-odbc.md).

##  <a name="getdefaultsql"></a>CRecordset:: GetDefaultSQL

Volá se, aby se získal výchozí řetězec SQL, který se má provést.

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>Návratová hodnota

`CString`, který obsahuje výchozí příkaz SQL.

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto členskou funkci, aby získala výchozí příkaz SQL, na kterém je sada záznamů založena. Může se jednat o název tabulky nebo příkaz SQL **Select** .

Nebudete nepřímo definovat výchozí příkaz SQL deklarováním třídy sady záznamů pomocí ClassWizard a ClassWizard tuto úlohu provede za vás.

Pokud potřebujete řetězec příkazu SQL pro vlastní použití, zavolejte `GetSQL`, která vrátí příkaz jazyka SQL, který se používá k výběru záznamů sady záznamů při jejich otevření. Můžete upravit výchozí řetězec SQL v přepsání třídy `GetDefaultSQL`. Například můžete zadat volání předdefinovaného dotazu pomocí příkazu **volání** . (Upozorňujeme však, že pokud `GetDefaultSQL`upravíte, budete také muset upravit `m_nFields` tak, aby odpovídalo počtu sloupců ve zdroji dat.)

Další informace naleznete v článku [Sada záznamů: Deklarování třídy pro tabulku (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).

> [!CAUTION]
>  Název tabulky bude prázdný, pokud rozhraní neidentifikovalo název tabulky, pokud bylo zadáno více názvů tabulek, nebo pokud příkaz **volání** nelze interpretovat. Všimněte si, že při použití příkazu **volání** není nutné vkládat prázdné znaky mezi složenou závorku a klíčové slovo **volání** , ani vkládat prázdné znaky před složenou závorku nebo před klíčovým slovem **Select** v příkazu **Select** .

##  <a name="getfieldvalue"></a>CRecordset:: GetFieldValue –

Načte data pole v aktuálním záznamu.

```
void GetFieldValue(
    LPCTSTR lpszName,
    CDBVariant& varValue,
    short nFieldType = DEFAULT_FIELD_TYPE);

void GetFieldValue(
    short nIndex,
    CDBVariant& varValue,
    short nFieldType = DEFAULT_FIELD_TYPE);

void GetFieldValue(
    short nIndex,
    CStringA& strValue);

void GetFieldValue(
    short nIndex,
    CStringW& strValue);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Název pole.

*varValu*e odkaz na objekt [CDBVariant –](../../mfc/reference/cdbvariant-class.md) , který bude uchovávat hodnotu pole.

*nFieldType*<br/>
Datový typ ODBC C daného pole. Použití výchozí hodnoty, DEFAULT_FIELD_TYPE, vynutí `GetFieldValue` určovat datový typ C z SQL data typu na základě následující tabulky. V opačném případě můžete zadat datový typ přímo nebo zvolit kompatibilní datový typ. do SQL_C_CHAR můžete například uložit libovolný datový typ.

|Datový typ C|Datový typ SQL|
|-----------------|-------------------|
|SQL_C_BIT|SQL_BIT|
|SQL_C_UTINYINT|SQL_TINYINT|
|SQL_C_SSHORT|SQL_SMALLINT|
|SQL_C_SLONG|SQL_INTEGER|
|SQL_C_FLOAT|SQL_REAL|
|SQL_C_DOUBLE|SQL_FLOATSQL_DOUBLE|
|SQL_C_TIMESTAMP|SQL_DATESQL_TIMESQL_TIMESTAMP|
|SQL_C_CHAR|SQL_NUMERICSQL_DECIMALSQL_BIGINTSQL_CHARSQL_VARCHARSQL_LONGVARCHAR|
|SQL_C_BINARY|SQL_BINARYSQL_VARBINARYSQL_LONGVARBINARY|

Další informace o datových typech ODBC naleznete v tématech "datové typy SQL" a "C Data Types" v příloze D Windows SDK.

*nIndex*<br/>
Index pole založený na nule.

*strValue*<br/>
Odkaz na objekt [CString](../../atl-mfc-shared/reference/cstringt-class.md) , který bude uchovávat hodnotu pole převedenou na text bez ohledu na datový typ pole.

### <a name="remarks"></a>Poznámky

Můžete vyhledat pole buď podle názvu, nebo podle indexu. Hodnotu pole můžete uložit buď do objektu `CDBVariant`, nebo do objektu `CString`.

Pokud jste implementovali hromadné načítání řádků, aktuální záznam je vždy umístěn na prvním záznamu v sadě řádků. Chcete-li použít `GetFieldValue` pro záznam v rámci dané sady řádků, je nutné nejprve zavolat členskou funkci [SetRowsetCursorPosition](#setrowsetcursorposition) pro přesunutí kurzoru na požadovaný řádek v rámci této sady řádků. Potom pro tento řádek zavolejte `GetFieldValue`. Chcete-li implementovat hromadné načítání řádků, je nutné zadat možnost `CRecordset::useMultiRowFetch` parametru *dwOptions* v [otevřené](#open) členské funkci.

Můžete použít `GetFieldValue` k dynamickému načítání polí v době běhu, a ne staticky je svázat v době návrhu. Například pokud jste deklarovali objekt sady záznamů přímo z `CRecordset`, je nutné použít `GetFieldValue` k načtení dat polí; Výměna pole záznamu (RFX) nebo hromadná výměna pole záznamu (Bulk RFX) není implementována.

> [!NOTE]
>  Pokud deklarujete objekt sady záznamů bez odvození od `CRecordset`, nemusíte mít nahranou knihovnu kurzorů rozhraní ODBC. Knihovna kurzorů vyžaduje, aby sada záznamů měla alespoň jeden vázaný sloupec; Pokud však použijete `CRecordset` přímo, žádný ze sloupců není svázán. Členské funkce [CDatabase:: OpenEx](../../mfc/reference/cdatabase-class.md#openex) a [CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open) určují, zda bude načtena knihovna kurzorů.

`GetFieldValue` volá funkci rozhraní ODBC API `SQLGetData`. Pokud Váš ovladač vypíše hodnotu SQL_NO_TOTAL pro skutečnou délku hodnoty pole, `GetFieldValue` vyvolá výjimku. Další informace o `SQLGetData`najdete v Windows SDK.

### <a name="example"></a>Příklad

Následující vzorový kód ilustruje volání `GetFieldValue` pro objekt sady záznamů deklarované přímo z `CRecordset`.

[!code-cpp[NVC_MFCDatabase#23](../../mfc/codesnippet/cpp/crecordset-class_7.cpp)]

> [!NOTE]
>  Na rozdíl od třídy DAO `CDaoRecordset``CRecordset` nemá `SetFieldValue` členskou funkci. Pokud vytvoříte objekt přímo z `CRecordset`, je pro něj efektivně jen pro čtení.

Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="getodbcfieldcount"></a>CRecordset:: GetODBCFieldCount

Načte celkový počet polí v objektu sady záznamů.

```
short GetODBCFieldCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet polí v sadě záznamů.

### <a name="remarks"></a>Poznámky

Další informace o vytváření sad záznamů naleznete v článku [Sada záznamů: vytváření a uzavírání sad záznamů (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).

##  <a name="getodbcfieldinfo"></a>CRecordset:: GetODBCFieldInfo

Získává informace o polích v sadě záznamů.

```
void GetODBCFieldInfo(
    LPCTSTR lpszName,
    CODBCFieldInfo& fieldinfo);

void GetODBCFieldInfo(
    short nIndex,
    CODBCFieldInfo& fieldinfo);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Název pole.

*FieldInfo*<br/>
Odkaz na strukturu `CODBCFieldInfo`.

*nIndex*<br/>
Index pole založený na nule.

### <a name="remarks"></a>Poznámky

Jedna verze funkce vám umožní vyhledat pole podle názvu. Druhá verze umožňuje vyhledat pole podle indexu.

Popis vrácených informací najdete v tématu struktura [codbcfieldinfo –](../../mfc/reference/codbcfieldinfo-structure.md) .

Další informace o vytváření sad záznamů naleznete v článku [Sada záznamů: vytváření a uzavírání sad záznamů (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).

##  <a name="getrecordcount"></a>CRecordset:: GetRecordCount

Určuje velikost sady záznamů.

```
long GetRecordCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet záznamů v sadě záznamů; 0, pokud sada záznamů neobsahuje žádné záznamy; nebo-1, pokud nelze určit počet záznamů.

### <a name="remarks"></a>Poznámky

> [!CAUTION]
>  Počet záznamů je udržován jako "horní mez"; nejpřesnější záznam, který se stále zobrazuje, když uživatel prochází záznamy. Celkový počet záznamů je znám pouze poté, co uživatel přesunul za poslední záznam. Z důvodů výkonu se počet při volání `MoveLast`neaktualizuje. Chcete-li spočítat záznamy sami, zavolejte `MoveNext` opakovaně, dokud `IsEOF` nevrátí nenulovou hodnotu. Přidání záznamu prostřednictvím `CRecordset:AddNew` a `Update` zvyšuje počet; odstranění záznamu pomocí `CRecordset::Delete` sníží počet.

##  <a name="getrowsetsize"></a>CRecordset:: GetRowsetSize

Získá aktuální nastavení počtu řádků, které chcete načíst během daného načtení.

```
DWORD GetRowsetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet řádků, které mají být načteny během daného načtení.

### <a name="remarks"></a>Poznámky

Používáte-li hromadné načítání řádků, je výchozí velikost sady řádků při otevření sady záznamů 25; v opačném případě je to 1.

Chcete-li implementovat hromadné načítání řádků, je nutné zadat možnost `CRecordset::useMultiRowFetch` v parametru *dwOptions* pro [otevřenou](#open) členskou funkci. Chcete-li změnit nastavení pro velikost sady řádků, zavolejte [SetRowsetSize](#setrowsetsize).

Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="getrowsfetched"></a>CRecordset:: GetRowsFetched

Určuje, kolik záznamů bylo skutečně načteno po načtení.

```
DWORD GetRowsFetched() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet řádků načtených ze zdroje dat po daném načtení.

### <a name="remarks"></a>Poznámky

To je užitečné, pokud jste implementovali hromadné načítání řádků. Velikost sady řádků obvykle určuje, kolik řádků bude načteno z načtení; Celkový počet řádků v sadě záznamů ale také ovlivňuje, kolik řádků bude načteno v sadě řádků. Například pokud vaše sada záznamů má 10 záznamů s nastavením velikosti sady řádků 4, pak smyčka prostřednictvím sady záznamů voláním `MoveNext` bude mít za následek konečnou sadu řádků obsahující pouze dva záznamy.

Chcete-li implementovat hromadné načítání řádků, je nutné zadat možnost `CRecordset::useMultiRowFetch` v parametru *dwOptions* pro [otevřenou](#open) členskou funkci. Chcete-li určit velikost sady řádků, zavolejte [SetRowsetSize](#setrowsetsize).

Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#24](../../mfc/codesnippet/cpp/crecordset-class_8.cpp)]

##  <a name="getrowstatus"></a>CRecordset:: GetRowStatus

Získá stav řádku v aktuální sadě řádků.

```
WORD GetRowStatus(WORD wRow) const;
```

### <a name="parameters"></a>Parametry

*wRow*<br/>
Pozice na jednom řádku v aktuální sadě řádků. Tato hodnota může být v rozsahu od 1 do velikosti sady řádků.

### <a name="return-value"></a>Návratová hodnota

Hodnota stavu řádku Podrobnosti najdete v tématu poznámky.

### <a name="remarks"></a>Poznámky

`GetRowStatus` vrátí hodnotu, která indikuje buď změnu stavu na řádek od posledního načtení ze zdroje dat, nebo nenačtený žádný řádek odpovídající *wRow* . V následující tabulce jsou uvedeny možné návratové hodnoty.

|Hodnota stavu|Popis|
|------------------|-----------------|
|SQL_ROW_SUCCESS|Řádek zůstane beze změny.|
|SQL_ROW_UPDATED|Řádek byl aktualizován.|
|SQL_ROW_DELETED|Řádek byl odstraněn.|
|SQL_ROW_ADDED|Řádek byl přidán.|
|SQL_ROW_ERROR|Řádek nejde získat, protože došlo k chybě.|
|SQL_ROW_NOROW|Neexistuje žádný řádek, který by odpovídal *wRow*.|

Další informace najdete v tématu funkce rozhraní ODBC API `SQLExtendedFetch` v Windows SDK.

##  <a name="getstatus"></a>CRecordset:: GetStatus

Určuje index aktuálního záznamu v sadě záznamů a zda byl zobrazen poslední záznam.

```
void GetStatus(CRecordsetStatus& rStatus) const;
```

### <a name="parameters"></a>Parametry

*rStatus*<br/>
Odkaz na objekt `CRecordsetStatus`. Další informace naleznete v části Poznámky.

### <a name="remarks"></a>Poznámky

`CRecordset` se pokusí sledovat index, ale za určitých okolností to nemusí být možné. Vysvětlení najdete v tématu [GetRecordCount](#getrecordcount) .

Struktura `CRecordsetStatus` má následující tvar:

```cpp
struct CRecordsetStatus
{
    long m_lCurrentRecord;
    BOOL m_bRecordCountFinal;
};
```

Dva členové `CRecordsetStatus` mají následující význam:

- `m_lCurrentRecord` obsahuje index aktuálního záznamu v rámci sady záznamů založený na nule, pokud je tento příkaz známý. Pokud index nelze určit, obsahuje tento člen AFX_CURRENT_RECORD_UNDEFINED (-2). Pokud má `IsBOF` hodnotu TRUE (prázdná sada záznamů nebo se pokusy o posunutí před první záznam), `m_lCurrentRecord` je nastaven na AFX_CURRENT_RECORD_BOF (-1). Pokud je v prvním záznamu, pak je nastaven na 0, druhý záznam 1 atd.

- Pokud byl určen celkový počet záznamů v sadě záznamů, `m_bRecordCountFinal` nenulovou hodnotu. Obecně se to musí provést spuštěním na začátku sady záznamů a voláním `MoveNext`, dokud `IsEOF` nevrátí nenulovou hodnotu. Pokud je tento člen nula, počet záznamů vrácený funkcí `GetRecordCount`, pokud ne-1, je pouze "horním" počtem záznamů.

##  <a name="getsql"></a>CRecordset:: GetSQL

Zavolejte tuto členskou funkci, aby se získal příkaz SQL, který se použil k výběru záznamů sady záznamů při jejím otevření.

```
const CString& GetSQL() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz **const** na `CString`, který obsahuje příkaz SQL.

### <a name="remarks"></a>Poznámky

Obvykle se jedná o příkaz SQL **Select** . Řetězec vrácený `GetSQL` je jen pro čtení.

Řetězec vrácený `GetSQL` se obvykle liší od libovolného řetězce, který jste mohli předat sadě záznamů v parametru *lpszSQL* , do členské funkce `Open`. Důvodem je, že sada záznamů vytvoří úplný příkaz SQL na základě toho, co jste předali do `Open`, co jste zadali v ClassWizard, co jste mohli zadat v `m_strFilter` a `m_strSort` datových členů a všechny parametry, které jste mohli zadat. Podrobnosti o tom, jak sada záznamů vytváří tento příkaz SQL, naleznete v článku [Sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).

> [!NOTE]
>  Tuto členskou funkci volejte až po volání funkce [Open](#open).

##  <a name="gettablename"></a>CRecordset:: GetTable.

Získá název tabulky SQL, na které je založen dotaz sady záznamů.

```
const CString& GetTableName() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz **const** na `CString`, který obsahuje název tabulky, pokud je sada záznamů založena na tabulce; v opačném případě prázdný řetězec.

### <a name="remarks"></a>Poznámky

`GetTableName` je platná pouze v případě, že sada záznamů je založena na tabulce, nikoli spojení s více tabulkami nebo předdefinovaným dotazem (uloženou proceduru). Název je určen jen pro čtení.

> [!NOTE]
>  Tuto členskou funkci volejte až po volání funkce [Open](#open).

##  <a name="isbof"></a>CRecordset:: IsBOF

Vrátí nenulovou hodnotu, pokud byla sada záznamů umístěna před první záznam. Neexistuje aktuální záznam.

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud sada záznamů neobsahuje žádné záznamy nebo pokud jste se přesunuli zpět před první záznam; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Než začnete s prvním záznamem sady záznamů, zavoláte tuto členskou funkci před přechodem ze záznamu na záznam a zjistěte, zda jste prošli. Můžete také použít `IsBOF` společně s `IsEOF` k určení, zda sada záznamů obsahuje nějaké záznamy nebo je prázdná. Ihned po volání `Open`, pokud sada záznamů neobsahuje žádné záznamy, `IsBOF` vrátí nenulovou hodnotu. Při otevření sady záznamů, která má alespoň jeden záznam, je první záznam aktuálním záznamem a `IsBOF` vrátí hodnotu 0.

Pokud je první záznam aktuálním záznamem a zavoláte `MovePrev`, `IsBOF` pak vrátí nenulovou hodnotu. Pokud `IsBOF` vrátí nenulovou hodnotu a zavoláte `MovePrev`, dojde k chybě. Pokud `IsBOF` vrátí nenulovou hodnotu, aktuální záznam není definován a všechny akce, které vyžadují aktuální záznam, budou mít za následek chybu.

### <a name="example"></a>Příklad

V tomto příkladu se používá `IsBOF` a `IsEOF` k detekci omezení sady záznamů, když se kód posouvá prostřednictvím sady záznamů v obou směrech.

[!code-cpp[NVC_MFCDatabase#25](../../mfc/codesnippet/cpp/crecordset-class_9.cpp)]

##  <a name="isdeleted"></a>CRecordset:: IsDeleted odstraněno

Určuje, zda byl aktuální záznam odstraněn.

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je sada záznamů umístěna na odstraněný záznam; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Pokud se posunete na záznam a `IsDeleted` vrátí hodnotu TRUE (nenulový), musíte se před provedením jakékoli jiné operace sady záznamů posunout na jiný záznam.

Výsledek `IsDeleted` závisí na mnoha faktorech, jako je například typ sady záznamů, bez ohledu na to, zda je vaše sada záznamů aktualizovatelná, zda jste zadali možnost `CRecordset::skipDeletedRecords` při otevření sady záznamů, zda vaše balíčky ovladačů odstranily záznamy a zda existuje více mohou.

Další informace o `CRecordset::skipDeletedRecords` a balení ovladače naleznete v tématu [otevřená](#open) členská funkce.

> [!NOTE]
>  Pokud jste implementovali hromadné načítání řádků, neměli byste volat `IsDeleted`. Místo toho zavolejte členskou funkci [GetRowStatus](#getrowstatus) . Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="iseof"></a>CRecordset:: IsEOF

Vrátí nenulovou hodnotu, pokud byla sada záznamů umístěna za posledním záznamem. Neexistuje aktuální záznam.

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud sada záznamů neobsahuje žádné záznamy, nebo pokud jste propřesunuli více než poslední záznam; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tuto členskou funkci zavolejte při posouvání záznamu záznamu na záznam, abyste zjistili, jestli jste prošli za posledním záznamem sady záznamů. Můžete také použít `IsEOF` k určení, zda sada záznamů obsahuje nějaké záznamy nebo je prázdná. Ihned po volání `Open`, pokud sada záznamů neobsahuje žádné záznamy, `IsEOF` vrátí nenulovou hodnotu. Při otevření sady záznamů, která má alespoň jeden záznam, je první záznam aktuálním záznamem a `IsEOF` vrátí hodnotu 0.

Pokud je poslední záznam aktuálním záznamem při volání `MoveNext`, `IsEOF` následně vrátí nenulovou hodnotu. Pokud `IsEOF` vrátí nenulovou hodnotu a zavoláte `MoveNext`, dojde k chybě. Pokud `IsEOF` vrátí nenulovou hodnotu, aktuální záznam není definován a všechny akce, které vyžadují aktuální záznam, budou mít za následek chybu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [IsBOF](#isbof).

##  <a name="isfielddirty"></a>CRecordset:: IsFieldDirty

Určuje, zda byl zadaný datový člen pole změněn od volání metody [Edit](#edit) nebo [AddNew](#addnew) .

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>Parametry

*PV*<br/>
Ukazatel na datový člen pole, jehož stav chcete ověřit, nebo hodnotu NULL, chcete-li určit, zda jsou některá pole nečistá.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud se zadaný datový člen pole změnil od chvíle, kdy došlo k volání `AddNew` nebo `Edit`; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Data ve všech datových členech v poli undirty se přenesou do záznamu ve zdroji dat, když je aktuální záznam aktualizován voláním členské funkce [Update](#update) `CRecordset` (po volání `Edit` nebo `AddNew`).

> [!NOTE]
>  Tato členská funkce se nedá použít pro sady záznamů, které používají hromadné načítání řádků. Pokud jste implementovali hromadné načítání řádků, `IsFieldDirty` vždy vrátí hodnotu FALSE a výsledkem bude selhání kontrolního výrazu. Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Volání `IsFieldDirty` obnoví účinek předchozích volání do [SetFieldDirty](#setfielddirty) , protože stav nezadaného pole je znovu vyhodnocován. V případě `AddNew` v případě, že se hodnota aktuálního pole liší od hodnoty pseudo null, je stav pole nastaveno na undirto. V případě `Edit` v případě, že se hodnota pole liší od hodnoty uložené v mezipaměti, je stav pole nastaveno na hodnotu undirto.

`IsFieldDirty` je implementována prostřednictvím [DoFieldExchange](#dofieldexchange).

Další informace o příznaku undirty naleznete v článku [Sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).

##  <a name="isfieldnull"></a>CRecordset:: IsFieldNull

Vrátí nenulovou hodnotu, pokud zadané pole v aktuálním záznamu má hodnotu null (nemá žádnou hodnotu).

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>Parametry

*PV*<br/>
Ukazatel na datový člen pole, jehož stav chcete ověřit, nebo hodnotu NULL, chcete-li určit, zda jsou některá pole null.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je zadaný datový člen pole označen jako null; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Zavolejte tuto členskou funkci, abyste zjistili, jestli je zadaný datový člen v sadě záznamů označený jako null. (V terminologii databáze hodnota null znamená "nemá žádnou hodnotu" a není shodná s hodnotou NULL v C++.) Pokud je datový člen pole označen jako null, je interpretován jako sloupec aktuálního záznamu, pro který neexistuje žádná hodnota.

> [!NOTE]
>  Tato členská funkce se nedá použít pro sady záznamů, které používají hromadné načítání řádků. Pokud jste implementovali hromadné načítání řádků, `IsFieldNull` vždy vrátí hodnotu FALSE a výsledkem bude selhání kontrolního výrazu. Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`IsFieldNull` je implementována prostřednictvím [DoFieldExchange](#dofieldexchange).

##  <a name="isfieldnullable"></a>CRecordset:: IsFieldNullable

Vrátí nenulovou hodnotu, pokud zadané pole v aktuálním záznamu může být nastaveno na hodnotu null (bez hodnoty).

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>Parametry

*PV*<br/>
Ukazatel na datový člen pole, jehož stav chcete ověřit, nebo hodnotu NULL, chcete-li určit, zda lze některá pole nastavit na hodnotu null.

### <a name="remarks"></a>Poznámky

Voláním této členské funkce určíte, zda je zadaný datový člen pole "Nullable" (lze nastavit na hodnotu null). C++ Hodnota null není shodná s hodnotou null, která v terminologii databáze znamená "nemá žádnou hodnotu").

> [!NOTE]
>  Pokud jste implementovali hromadné načítání řádků, nemůžete volat `IsFieldNullable`. Místo toho zavolejte členskou funkci [GetODBCFieldInfo](#getodbcfieldinfo) a určete, zda může být pole nastaveno na hodnotu null. Všimněte si, že můžete vždy volat `GetODBCFieldInfo`, bez ohledu na to, zda jste implementovali hromadné načítání řádků. Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Pole, které nemůže mít hodnotu null, musí mít hodnotu. Pokud se pokusíte nastavit takové pole na hodnotu null při přidávání nebo aktualizaci záznamu, zdroj dat odmítne přidání nebo aktualizaci a [aktualizace](#update) vyvolá výjimku. K výjimce dojde při volání `Update`, ne při volání [SetFieldNull](#setfieldnull).

Použití hodnoty NULL pro první argument funkce bude používat funkci pouze pro `outputColumn` pole, nikoli `param` polí. Například volání

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

nastaví pouze `outputColumn` pole na hodnotu NULL; `param` pole nebudou nijak ovlivněna.

Chcete-li pracovat s `param` poli, je nutné dodat skutečnou adresu jednotlivých `param`, na kterých chcete pracovat, například:

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

To znamená, že nemůžete nastavit všechna `param` pole na hodnotu NULL, stejně jako u polí `outputColumn`.

`IsFieldNullable` je implementována prostřednictvím [DoFieldExchange](#dofieldexchange).

##  <a name="isopen"></a>CRecordset:: Open

Určuje, zda je sada záznamů již otevřena.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla dříve volána členská funkce objektu sady záznamů nebo členská funkce [Requery](#requery) [a sada](#open) záznamů nebyla zavřena. v opačném případě 0.

##  <a name="m_hstmt"></a>CRecordset:: m_hstmt

Obsahuje popisovač do datové struktury příkazu ODBC typu HSTMT přidružené k sadě záznamů.

### <a name="remarks"></a>Poznámky

Každý dotaz na zdroj dat ODBC je přidružen k HSTMT.

> [!CAUTION]
>  Nepoužívejte `m_hstmt` před voláním metody [Open](#open) .

Obvykle není nutné přistupovat k HSTMT přímo, ale možná budete potřebovat pro přímé provádění příkazů SQL. Členská funkce `ExecuteSQL` třídy `CDatabase` poskytuje příklad použití `m_hstmt`.

##  <a name="m_nfields"></a>CRecordset:: m_nFields

Obsahuje počet datových členů pole ve třídě sady záznamů; To znamená, že počet sloupců vybraný sadou záznamů ze zdroje dat.

### <a name="remarks"></a>Poznámky

Konstruktor třídy sady záznamů musí inicializovat `m_nFields` se správným číslem. Pokud jste neimplementovali hromadné načítání řádků, ClassWizard zapíše tuto inicializaci za vás, když ji použijete k deklaraci vaší třídy sady záznamů. Můžete ho také napsat ručně.

Rozhraní používá toto číslo ke správě interakce mezi datovými členy pole a odpovídající sloupce aktuálního záznamu ve zdroji dat.

> [!CAUTION]
>  Toto číslo musí odpovídat počtu výstupních sloupců zaregistrovaných ve `DoFieldExchange` nebo `DoBulkFieldExchange` po volání metody [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) s parametrem `CFieldExchange::outputColumn`.

Sloupce můžete svázat dynamicky, jak je vysvětleno v článku sada záznamů: dynamické vazby datových sloupců. V takovém případě je nutné zvýšit počet v `m_nFields` tak, aby odrážel počet volání funkce RFX nebo hromadně RFX ve vaší `DoFieldExchange` nebo `DoBulkFieldExchange` členské funkci pro dynamicky vázané sloupce.

Další informace naleznete v článcích [Sada záznamů: dynamické vazby datových sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) a [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Příklad

Viz článek [Výměna pole záznamu: Použití RFX](../../data/odbc/record-field-exchange-using-rfx.md).

##  <a name="m_nparams"></a>CRecordset:: m_nParams

Obsahuje počet datových členů parametrů ve třídě sady záznamů. To znamená, že počet parametrů předaných s dotazem sady záznamů.

### <a name="remarks"></a>Poznámky

Pokud vaše třída sady záznamů obsahuje nějaké datové členy parametru, konstruktor třídy musí inicializovat `m_nParams` se správným číslem. Hodnota `m_nParams` výchozí hodnota je 0. Pokud přidáte členy dat parametrů (které je nutné provést ručně), musíte také ručně přidat inicializaci v konstruktoru třídy, aby odrážela počet parametrů (který musí být nejméně tak velký, jako je počet ' ' zástupných symbolů v `m_strFilter` nebo `m_strSort` řetězec).

Rozhraní používá toto číslo při parameterizes dotazu sady záznamů.

> [!CAUTION]
>  Toto číslo musí odpovídat počtu "paraí" zaregistrovaným ve `DoFieldExchange` nebo `DoBulkFieldExchange` po volání metody [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) s hodnotou parametru `CFieldExchange::inputParam`, `CFieldExchange::param`, `CFieldExchange::outputParam`nebo `CFieldExchange::inoutParam`.

### <a name="example"></a>Příklad

  Viz články [Sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) a [Výměna pole záznamu: using RFX](../../data/odbc/record-field-exchange-using-rfx.md).

##  <a name="m_pdatabase"></a>CRecordset:: m_pDatabase

Obsahuje ukazatel na objekt `CDatabase`, pomocí kterého je sada záznamů připojena ke zdroji dat.

### <a name="remarks"></a>Poznámky

Tato proměnná se nastavuje dvěma způsoby. Obvykle při vytváření objektu Recordset předáte ukazatel na již připojený `CDatabase` objekt. Pokud místo toho předáte hodnotu NULL, `CRecordset` pro vás vytvoří objekt `CDatabase` a připojí ho. V obou případech `CRecordset` ukládá ukazatel do této proměnné.

Obvykle nebudete muset přímo používat ukazatel uložený v `m_pDatabase`. Pokud však píšete vlastní rozšíření pro `CRecordset`, může být nutné použít ukazatel. Můžete například potřebovat ukazatel, pokud vyvoláte vlastní `CDBException`s. Případně ho můžete potřebovat, pokud potřebujete něco použít stejným `CDatabase` objekt, jako je například spuštění transakcí, nastavení časových limitů nebo volání `ExecuteSQL` členské funkce třídy `CDatabase` k provedení příkazů SQL přímo.

##  <a name="m_strfilter"></a>CRecordset:: m_strFilter

Po sestavení objektu sady záznamů, ale před voláním jeho členské funkce `Open` použijte tohoto datového člena k uložení `CString` obsahujícího klauzuli **WHERE** jazyka SQL.

### <a name="remarks"></a>Poznámky

Sada záznamů používá tento řetězec k omezení (nebo filtrování) záznamů, které vybral během `Open` nebo `Requery` volání. To je užitečné pro výběr podmnožiny záznamů, například "Všichni prodejci" na bázi Kalifornie "(" State = CA "). Syntaxe rozhraní ODBC SQL pro klauzuli **WHERE** je

`WHERE search-condition`

Všimněte si, že do řetězce nezahrnete klíčové slovo **WHERE** . Rozhraní je dodává.

Můžete také parametrizovat řetězec filtru tím, že v něm umístíte zástupné symboly, deklarujete parametr datového člena ve třídě pro každý zástupný symbol a předáte parametry do sady záznamů za běhu. To vám umožní vytvořit filtr za běhu. Další informace naleznete v článku [Sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

Další informace o klauzulích **WHERE** jazyka SQL najdete v článku [SQL](../../data/odbc/sql.md). Další informace o výběru a filtrování záznamů naleznete v článku [Sada záznamů: filtrování záznamů (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#30](../../mfc/codesnippet/cpp/crecordset-class_12.cpp)]

##  <a name="m_strsort"></a>CRecordset:: m_strSort

Po vytvoření objektu sady záznamů, ale před voláním jeho členské funkce `Open`, použijte tohoto datového člena k uložení `CString` obsahujícího klauzuli **ORDER by** jazyka SQL.

### <a name="remarks"></a>Poznámky

Sada záznamů používá tento řetězec k řazení záznamů, které vybere během `Open` nebo `Requery` volání. Tuto funkci můžete použít k řazení sady záznamů v jednom nebo více sloupcích. Syntaxe rozhraní ODBC SQL pro klauzuli **ORDER by** je

`ORDER BY sort-specification [, sort-specification]...`

kde je specifikace řazení celé číslo nebo název sloupce. Můžete také zadat vzestupné nebo sestupné pořadí (ve výchozím nastavení je pořadí vzestupné) připojením "ASC" nebo "DESC" do seznamu sloupců v řetězci řazení. Vybrané záznamy jsou nejprve seřazené podle prvního sloupce uvedeného v poli, potom podle druhého atd. Například můžete seřadit sadu "Customers" Recordset podle příjmení a pak jméno. Počet sloupců, které můžete zobrazit, závisí na zdroji dat. Další informace najdete v Windows SDK.

Všimněte si, že do řetězce nezahrnete klíčové slovo **ORDER by** . Rozhraní je dodává.

Další informace o klauzulích SQL najdete v článku [SQL](../../data/odbc/sql.md). Další informace o řazení záznamů naleznete v článku [Sada záznamů: řazení záznamů (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#31](../../mfc/codesnippet/cpp/crecordset-class_13.cpp)]

##  <a name="move"></a>CRecordset:: Move

Přesune ukazatel na aktuální záznam v rámci sady záznamů, a to buď dopředu, nebo zpět.

```
virtual void Move(
    long nRows,
    WORD wFetchType = SQL_FETCH_RELATIVE);
```

### <a name="parameters"></a>Parametry

*Hodnota nRows*<br/>
Počet řádků, které se mají přesunout dopředu nebo dozadu Kladné hodnoty posunou vpřed ke konci sady záznamů. Záporné hodnoty se posunou zpět směrem k začátku.

*wFetchType*<br/>
Určuje sadu řádků, kterou bude `Move` načíst. Podrobnosti najdete v tématu poznámky.

### <a name="remarks"></a>Poznámky

Pokud předáte hodnotu 0 pro *hodnota nRows*, `Move` aktualizuje aktuální záznam. `Move` ukončí všechny aktuální `AddNew` nebo `Edit` režim a obnoví hodnotu aktuálního záznamu před zavoláním `AddNew` nebo `Edit`.

> [!NOTE]
>  Při procházení sady záznamů nelze vynechat odstraněné záznamy. Další informace naleznete v tématu [CRecordset:: IsDeleted](#isdeleted) . Když otevřete `CRecordset` se sadou možností `skipDeletedRecords`, `Move` kontrolní výrazy, pokud je parametr *hodnota nRows* 0. Toto chování brání aktualizaci řádků, které jsou odstraněny jinými klientskými aplikacemi pomocí stejných dat. Popis `skipDeletedRecords`naleznete v tématu v [otevřeném](#open) parametru *dwOptions* .

`Move` změnu umístění sady záznamů pomocí sad řádků. Na základě hodnot pro *hodnota nRows* a *wFetchType*`Move` načte příslušnou sadu řádků a následně vytvoří první záznam v dané sadě řádků aktuálního záznamu. Pokud jste neimplementovali hromadné načítání řádků, je velikost sady řádků vždy 1. Při načítání sady řádků `Move` přímo volá členskou funkci [CheckRowsetError](#checkrowseterror) pro zpracování všech chyb, které jsou výsledkem načtení.

V závislosti na hodnotách, které předáte, je `Move` ekvivalentní k ostatním členským funkcím `CRecordset`. Konkrétně hodnota *wFetchType* může označovat členskou funkci, která je intuitivnější a často upřednostňovanou metodou pro přesunutí aktuálního záznamu.

V následující tabulce jsou uvedeny možné hodnoty pro *wFetchType*, sada řádků, kterou `Move` načte na základě *wFetchType* a *hodnota nRows*, a jakékoliv ekvivalentní členské funkce odpovídající *wFetchType*.

|wFetchType|Načtená sada řádků|Ekvivalentní členská funkce|
|----------------|--------------------|--------------------------------|
|SQL_FETCH_RELATIVE (výchozí hodnota)|Sada řádků začínající *hodnota nRows* řádky od prvního řádku v aktuální sadě řádků.||
|SQL_FETCH_NEXT|Následující sada řádků; *hodnota nRows* se ignoruje.|[Metoda](#movenext)|
|SQL_FETCH_PRIOR|Předchozí sada řádků; *hodnota nRows* se ignoruje.|[MovePrev](#moveprev)|
|SQL_FETCH_FIRST|První sada řádků v sadě záznamů; *hodnota nRows* se ignoruje.|[MoveFirst](#movefirst)|
|SQL_FETCH_LAST|Poslední dokončená sada řádků v sadě záznamů; *hodnota nRows* se ignoruje.|[MoveLast](#movelast)|
|SQL_FETCH_ABSOLUTE|Pokud *hodnota nrows* > 0, sada řádků spouští *hodnota nRows* řádky od začátku sady záznamů. Pokud *hodnota nrows* < 0, sada řádků spouští *hodnota nRows* řádky z konce sady záznamů. Pokud *hodnota nRows* = 0, pak se vrátí podmínka Start-of-File (BOF).|[SetAbsolutePosition](#setabsoluteposition)|
|SQL_FETCH_BOOKMARK|Sada řádků začínající na řádku, jehož hodnota záložky odpovídá *hodnota nRows*.|[SetBookmark](#setbookmark)|

> [!NOTE]
>  Pro sady záznamů, které jsou jen pro čtení, je `Move` platný pouze s hodnotou SQL_FETCH_NEXT pro *wFetchType*.

> [!CAUTION]
>  Volání `Move` vyvolá výjimku, pokud sada záznamů neobsahuje žádné záznamy. Chcete-li určit, zda sada záznamů obsahuje nějaké záznamy, zavolejte [IsBOF](#isbof) a [IsEOF](#iseof).

> [!NOTE]
>  Pokud jste se přesunuli za začátek nebo konec sady záznamů (`IsBOF` nebo `IsEOF` vrátí nenulovou hodnotu), volání funkce `Move` pravděpodobně vyvolá `CDBException`. Například pokud `IsEOF` vrátí nenulovou hodnotu a `IsBOF` ne, `MoveNext` vyvolá výjimku, ale `MovePrev` nikoli.

> [!NOTE]
>  Pokud zavoláte `Move`, zatímco se aktualizuje nebo přidává aktuální záznam, aktualizace se ztratí bez upozornění.

Další informace o navigaci v sadě záznamů naleznete v článcích [Sada záznamů: posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) a [Sada záznamů: záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Související informace najdete v tématu funkce rozhraní ODBC API `SQLExtendedFetch` v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#28](../../mfc/codesnippet/cpp/crecordset-class_14.cpp)]

##  <a name="movefirst"></a>CRecordset:: MoveFirst

Vytvoří první záznam v první sadě řádků aktuálního záznamu.

```
void MoveFirst();
```

### <a name="remarks"></a>Poznámky

Bez ohledu na to, zda bylo provedeno hromadné načítání řádků, bude vždy první záznam v sadě záznamů.

Po otevření sady záznamů není nutné volat `MoveFirst` hned. V tuto chvíli je první záznam (pokud existuje) automaticky aktuální záznam.

> [!NOTE]
>  Tato členská funkce není platná pro sady záznamů s dopředné jen pro čtení.

> [!NOTE]
>  Při procházení sady záznamů nelze vynechat odstraněné záznamy. Podrobnosti najdete v části členská funkce [IsDeleted](#isdeleted) .

> [!CAUTION]
>  Volání kterékoli z `Move` Functions vyvolá výjimku, pokud sada záznamů neobsahuje žádné záznamy. Chcete-li určit, zda sada záznamů obsahuje nějaké záznamy, zavolejte `IsBOF` a `IsEOF`.

> [!NOTE]
>  Pokud voláte některou z funkcí `Move`, zatímco se aktualizuje nebo přidává aktuální záznam, aktualizace se ztratí bez upozornění.

Další informace o navigaci v sadě záznamů naleznete v článcích [Sada záznamů: posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) a [Sada záznamů: záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [IsBOF](#isbof).

##  <a name="movelast"></a>CRecordset:: MoveLast

Provede první záznam v poslední dokončené sadě řádků v aktuálním záznamu.

```
void MoveLast();
```

### <a name="remarks"></a>Poznámky

Pokud jste neimplementovali hromadné načítání řádků, vaše sada záznamů má velikost sady řádků 1, takže `MoveLast` jednoduše přesune na poslední záznam v sadě záznamů.

> [!NOTE]
>  Tato členská funkce není platná pro sady záznamů s dopředné jen pro čtení.

> [!NOTE]
>  Při procházení sady záznamů nelze vynechat odstraněné záznamy. Podrobnosti najdete v části členská funkce [IsDeleted](#isdeleted) .

> [!CAUTION]
>  Volání kterékoli z `Move` Functions vyvolá výjimku, pokud sada záznamů neobsahuje žádné záznamy. Chcete-li určit, zda sada záznamů obsahuje nějaké záznamy, zavolejte `IsBOF` a `IsEOF`.

> [!NOTE]
>  Pokud voláte některou z funkcí `Move`, zatímco se aktualizuje nebo přidává aktuální záznam, aktualizace se ztratí bez upozornění.

Další informace o navigaci v sadě záznamů naleznete v článcích [Sada záznamů: posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) a [Sada záznamů: záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [IsBOF](#isbof).

##  <a name="movenext"></a>CRecordset:: MoveNext

Vytvoří první záznam v další sadě řádků s aktuálním záznamem.

```
void MoveNext();
```

### <a name="remarks"></a>Poznámky

Pokud jste neimplementovali hromadné načítání řádků, vaše sada záznamů má velikost sady řádků 1, takže `MoveNext` jednoduše přesune na další záznam.

> [!NOTE]
>  Při procházení sady záznamů nelze vynechat odstraněné záznamy. Podrobnosti najdete v části členská funkce [IsDeleted](#isdeleted) .

> [!CAUTION]
>  Volání kterékoli z `Move` Functions vyvolá výjimku, pokud sada záznamů neobsahuje žádné záznamy. Chcete-li určit, zda sada záznamů obsahuje nějaké záznamy, zavolejte `IsBOF` a `IsEOF`.

> [!NOTE]
>  Doporučuje se také volat `IsEOF` před voláním `MoveNext`. Například pokud jste protáhli za koncem sady záznamů, `IsEOF` vrátí nenulovou hodnotu; následné volání `MoveNext` by vyvolalo výjimku.

> [!NOTE]
>  Pokud voláte některou z funkcí `Move`, zatímco se aktualizuje nebo přidává aktuální záznam, aktualizace se ztratí bez upozornění.

Další informace o navigaci v sadě záznamů naleznete v článcích [Sada záznamů: posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) a [Sada záznamů: záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [IsBOF](#isbof).

##  <a name="moveprev"></a>CRecordset:: MovePrev

Provede první záznam v předchozí sadě řádků aktuálního záznamu.

```
void MovePrev();
```

### <a name="remarks"></a>Poznámky

Pokud jste neimplementovali hromadné načítání řádků, vaše sada záznamů má velikost sady řádků 1, takže `MovePrev` jednoduše přesune na předchozí záznam.

> [!NOTE]
>  Tato členská funkce není platná pro sady záznamů s dopředné jen pro čtení.

> [!NOTE]
>  Při procházení sady záznamů nelze vynechat odstraněné záznamy. Podrobnosti najdete v části členská funkce [IsDeleted](#isdeleted) .

> [!CAUTION]
>  Volání kterékoli z `Move` Functions vyvolá výjimku, pokud sada záznamů neobsahuje žádné záznamy. Chcete-li určit, zda sada záznamů obsahuje nějaké záznamy, zavolejte `IsBOF` a `IsEOF`.

> [!NOTE]
>  Doporučuje se také volat `IsBOF` před voláním `MovePrev`. Například pokud jste se přesunuli před začátek sady záznamů, `IsBOF` vrátí nenulovou hodnotu; následné volání `MovePrev` by vyvolalo výjimku.

> [!NOTE]
>  Pokud voláte některou z funkcí `Move`, zatímco se aktualizuje nebo přidává aktuální záznam, aktualizace se ztratí bez upozornění.

Další informace o navigaci v sadě záznamů naleznete v článcích [Sada záznamů: posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) a [Sada záznamů: záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [IsBOF](#isbof).

##  <a name="onsetoptions"></a>CRecordset:: OnSetOptions

Volá se, aby se nastavily možnosti (používané pro výběr) pro zadaný příkaz ODBC.

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Parametry

*hstmt*<br/>
HSTMT příkazu ODBC, jehož možnosti mají být nastaveny.

### <a name="remarks"></a>Poznámky

Volání `OnSetOptions` k nastavení možností (použitých pro výběr) pro zadaný příkaz ODBC. Rozhraní volá tuto členskou funkci pro nastavení počátečních možností pro sadu záznamů. `OnSetOptions` Určuje podporu zdroje dat pro rolovací kurzory a pro souběžnost kurzoru a nastaví odpovídající možnosti sady záznamů. (Zatímco `OnSetOptions` se používá pro operace výběru, `OnSetUpdateOptions` se používá pro operace aktualizace.)

Přepsat `OnSetOptions` pro nastavení možností specifických pro ovladač nebo zdroj dat. Například pokud váš zdroj dat podporuje otevření pro výhradní přístup, můžete přepsat `OnSetOptions`, abyste mohli využít této možnosti.

Další informace o kurzorech najdete v článku [ODBC](../../data/odbc/odbc-basics.md).

##  <a name="onsetupdateoptions"></a>CRecordset:: OnSetUpdateOptions

Volá se, aby se nastavily možnosti (používané při aktualizaci) pro zadaný příkaz ODBC.

```
virtual void OnSetUpdateOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Parametry

*hstmt*<br/>
HSTMT příkazu ODBC, jehož možnosti mají být nastaveny.

### <a name="remarks"></a>Poznámky

Volání `OnSetUpdateOptions` k nastavení možností (použitých při aktualizaci) pro zadaný příkaz ODBC. Rozhraní volá tuto členskou funkci poté, co vytvoří HSTMT pro aktualizaci záznamů v sadě záznamů. (Zatímco `OnSetOptions` se používá pro operace výběru, `OnSetUpdateOptions` se používá pro operace aktualizace.) `OnSetUpdateOptions` Určuje podporu zdroje dat pro rolovací kurzory a pro souběžnost kurzoru a nastaví odpovídající možnosti sady záznamů.

Před použitím tohoto příkazu pro přístup k databázi přepište `OnSetUpdateOptions` pro nastavení možností příkazu ODBC.

Další informace o kurzorech najdete v článku [ODBC](../../data/odbc/odbc-basics.md).

##  <a name="open"></a>CRecordset:: Open

Otevře sadu záznamů načtením tabulky nebo provedením dotazu, který sada záznamů představuje.

```
virtual BOOL Open(
    UINT nOpenType = AFX_DB_USE_DEFAULT_TYPE,
    LPCTSTR lpszSQL = NULL,
    DWORD dwOptions = none);
```

### <a name="parameters"></a>Parametry

*nOpenType*<br/>
Přijměte výchozí hodnotu, AFX_DB_USE_DEFAULT_TYPE nebo použijte jednu z následujících hodnot z `enum OpenType`:

- `CRecordset::dynaset` sadu záznamů s obousměrným posouváním. Členství a pořadí záznamů je určeno při otevření sady záznamů, ale změny datových hodnot provedené ostatními uživateli jsou viditelné až po operaci načtení. Dynamické sady jsou známy také jako sady záznamů řízené sadou klíčů.

- `CRecordset::snapshot` statické sady záznamů s obousměrným posouváním. Členství a pořadí záznamů je určeno při otevření sady záznamů. Datové hodnoty jsou určeny při načtení záznamů. Změny provedené ostatními uživateli nejsou viditelné, dokud není sada záznamů zavřena a znovu otevřena.

- `CRecordset::dynamic` sadu záznamů s obousměrným posouváním. Změny členství, pořadí a datových hodnot provedené jinými uživateli jsou viditelné po operaci načtení. Povšimněte si, že mnoho ovladačů ODBC nepodporuje tento typ sady záznamů.

- `CRecordset::forwardOnly` sadu záznamů jen pro čtení s dopředné posouvání.

   Pro `CRecordset`je výchozí hodnota `CRecordset::snapshot`. Mechanismus výchozích hodnot umožňuje interakci průvodců aplikace Visual C++ s třídou `CRecordset` pro rozhraní ODBC i třídou `CDaoRecordset` pro rozhraní DAO, které používají různé výchozí hodnoty.

Další informace o těchto typech sady záznamů naleznete v článku [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md). Související informace naleznete v článku "použití bloků a rolovacích kurzorů" v Windows SDK.

> [!CAUTION]
>  Není-li požadovaný typ podporován, rozhraní vyvolá výjimku.

*Ipszsql*<br/>
Ukazatel řetězce obsahující jedno z následujících:

- Ukazatel s hodnotou NULL.

- Název tabulky.

- Příkaz jazyka SQL **Select** (volitelně s klauzulí **WHERE** nebo **ORDER by** klauzule SQL).

- Příkaz **volání** určující název předdefinovaného dotazu (uložená procedura). Buďte opatrní, abyste nevložili prázdné znaky mezi složenou závorku a klíčové slovo **Call** .

Další informace o tomto řetězci naleznete v tabulce a diskuzi o roli ClassWizard v části [poznámky](#remarks) .

> [!NOTE]
>  Pořadí sloupců v sadě výsledků dotazu musí odpovídat pořadí volání funkce RFX nebo hromadného RFX v přepsání funkce [DoFieldExchange](#dofieldexchange) nebo [DoBulkFieldExchange](#dobulkfieldexchange) .

*dwOptions*<br/>
Bitová maska schopná určit kombinaci hodnot uvedených níže. Některé se vzájemně vylučují. Výchozí hodnota je **None (žádné**).

- `CRecordset::none` nejsou nastaveny žádné možnosti. Tato hodnota parametru se vzájemně vylučuje se všemi ostatními hodnotami. Ve výchozím nastavení může být sada záznamů aktualizována pomocí [Edit](#edit) nebo [Delete](#delete) a umožňuje přidávání nových záznamů pomocí metody [AddNew](#addnew). Možnost aktualizace závisí na zdroji dat i na možnosti *nOpenType* , kterou zadáte. Optimalizace pro hromadná přidávání nejsou dostupné. Hromadné načítání řádků nebude implementováno. Odstraněné záznamy nebudou při navigaci v sadě záznamů přeskočeny. Záložky nejsou k dispozici. Automatická kontrola nečistých polí je implementována.

- `CRecordset::appendOnly` nepovoluje `Edit` nebo `Delete` sady záznamů. Povolit pouze funkci `AddNew`. Tato možnost se vzájemně vylučuje s možností `CRecordset::readOnly`.

- `CRecordset::readOnly` otevřít sadu záznamů jako jen pro čtení. Tato možnost se vzájemně vylučuje s možností `CRecordset::appendOnly`.

- `CRecordset::optimizeBulkAdd` použít připravený příkaz SQL k optimalizaci přidávání mnoha záznamů najednou. Platí pouze v případě, že nepoužíváte funkci rozhraní ODBC API `SQLSetPos` k aktualizaci sady záznamů. První aktualizace určuje, která pole jsou označena za nečistá. Tato možnost se vzájemně vylučuje s možností `CRecordset::useMultiRowFetch`.

- `CRecordset::useMultiRowFetch` implementovat hromadné načítání řádků, aby bylo možné načíst více řádků v rámci jedné operace načtení. Jde o pokročilou funkci navrženou pro zvýšení výkonu. Hromadná výměna polí záznamu však není podporována nástrojem ClassWizard. Tato možnost se vzájemně vylučuje s možností `CRecordset::optimizeBulkAdd`. Všimněte si, že pokud zadáte `CRecordset::useMultiRowFetch`, bude možnost `CRecordset::noDirtyFieldCheck` automaticky zapnuta (nebude k dispozici dvojité ukládání do vyrovnávací paměti); u sad záznamů, které jsou jen pro čtení, se možnost automaticky zapne `CRecordset::useExtendedFetch`. Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

- Při procházení sadou záznamů `CRecordset::skipDeletedRecords` přeskočit všechny odstraněné záznamy. V určitých relativních načteních tato možnost sníží výkon. Tato možnost není platná pro sady záznamů s posouváním pouze vpřed. Pokud zavoláte [Move](#move) s parametrem *hodnota nRows* nastaveným na hodnotu 0 a nastaví se sada možností `CRecordset::skipDeletedRecords`, `Move` vyhodnotí. Všimněte si, že `CRecordset::skipDeletedRecords` je podobná *balení ovladače*, což znamená, že odstraněné řádky jsou ze sady záznamů odebrány. Pokud však ovladač záznamy komprimuje, budou přeskočeny pouze vámi odstraněné záznamy. Záznamy odstraněné jinými uživateli v době, kdy byla sada otevřena, nebudou přeskočeny. `CRecordset::skipDeletedRecords` přeskočí řádky odstraněné jinými uživateli.

- `CRecordset::useBookmarks` může používat záložky v sadě záznamů, pokud jsou podporovány. Záložky zpomalují načítání dat, ale zvyšují výkon navigace v nich. Nelze je použít v sadách záznamů s posouváním pouze vpřed. Další informace naleznete v článku [Sada záznamů: záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

- `CRecordset::noDirtyFieldCheck` vypnout automatickou kontrolu nevyřízených polí (dvojité ukládání do vyrovnávací paměti). Tím dojde ke zvýšení výkonu. Pole je však zapotřebí ručně označit jako nečistá zavoláním členských funkcí `SetFieldDirty` a `SetFieldNull`. Povšimněte si, že dvojité ukládání do vyrovnávací paměti ve třídě `CRecordset` je podobné dvojitému ukládání do vyrovnávací paměti ve třídě `CDaoRecordset`. Ve třídě `CRecordset` však nelze zapnout dvojité ukládání do vyrovnávací paměti pro jednotlivá pole. Lze jej zapnout nebo vypnout pouze pro všechna pole najednou. Všimněte si, že pokud zadáte možnost `CRecordset::useMultiRowFetch`, `CRecordset::noDirtyFieldCheck` bude automaticky zapnuta; `SetFieldDirty` a `SetFieldNull` však nelze použít pro sady záznamů, které implementují hromadné načítání řádků.

- `CRecordset::executeDirect` nepoužívejte připravený příkaz SQL. Pro zlepšení výkonu tuto možnost zadejte, pokud nebude nikdy volána členská funkce `Requery`.

- `CRecordset::useExtendedFetch` implementovat `SQLExtendedFetch` namísto `SQLFetch`. Navrženo pro implementaci hromadného načítání řádků pro sady záznamů s posouváním pouze vpřed. Pokud zadáte možnost `CRecordset::useMultiRowFetch` pro sadu záznamů s dopředné jenom dopředné, `CRecordset::useExtendedFetch` se automaticky zapne.

- `CRecordset::userAllocMultiRowBuffers` bude uživatel přidělovat vyrovnávací paměti úložiště pro data. Chcete-li přidělit své vlastní úložiště, použijte tuto možnost spolu s možností `CRecordset::useMultiRowFetch`. V opačném případě bude potřebné úložiště přiděleno rozhraním. Další informace naleznete v článku [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Všimněte si, že zadáním `CRecordset::userAllocMultiRowBuffers` bez určení `CRecordset::useMultiRowFetch` způsobí selhání kontrolního výrazu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se objekt `CRecordset` úspěšně otevřel; jinak 0 v případě, že [CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open) (při volání) vrátí hodnotu 0.

### <a name="remarks"></a>Poznámky

Chcete-li spustit dotaz definovaný sadou záznamů, je zapotřebí zavolat tuto členskou funkci. Před voláním `Open`musíte vytvořit objekt sady záznamů.

Toto připojení sady záznamů ke zdroji dat závisí na způsobu sestavení sady záznamů před voláním `Open`. Pokud předáte objekt [CDatabase](../../mfc/reference/cdatabase-class.md) do konstruktoru sady záznamů, který nebyl připojen ke zdroji dat, tato členská funkce používá [GetDefaultConnect](#getdefaultconnect) k pokusu o otevření objektu databáze. Pokud předáte NULL do konstruktoru sady záznamů, konstruktor vytvoří objekt `CDatabase` za vás a `Open` se pokusí připojit objekt databáze. Podrobnosti o zavírání sady záznamů a připojení za těchto různých okolností naleznete v tématu [Close](#close).

> [!NOTE]
>  Přístup ke zdroji dat pomocí objektu `CRecordset` je vždy sdílen. Na rozdíl od třídy `CDaoRecordset` nelze objekt `CRecordset` použít k otevření zdroje dat s výhradním přístupem.

Při volání `Open`dotaz, obvykle příkaz SQL **Select** , vybere záznamy na základě kritérií uvedených v následující tabulce.

|Hodnota parametru IpszSQL|Zvolené záznamy jsou určeny|Příklad|
|------------------------------------|----------------------------------------|-------------|
|NULL|Řetězec vrácený funkcí `GetDefaultSQL`.||
|Název tabulky SQL|Všechny sloupce tabulkového seznamu ve funkci `DoFieldExchange` nebo `DoBulkFieldExchange`.|`"Customer"`|
|Název předdefinovaného dotazu (uložené procedury)|Sloupce, k jejichž vrácení je dotaz definován.|`"{call OverDueAccts}"`|
|**Vybrat** sloupec-seznam **ze** seznamu tabulek|Zadané sloupce ze zadané tabulky nebo tabulek.|`"SELECT CustId, CustName FROM`<br /><br /> `Customer"`|

> [!CAUTION]
>  Ujistěte se, že do řetězce jazyka SQL nebyly vloženy prázdné znaky. Například pokud vložíte prázdné znaky mezi složenou závorku a klíčové slovo **volání** , knihovna MFC bude interpretovat řetězec SQL jako název tabulky a začlenit ho do příkazu **Select** , což způsobí vyvolání výjimky. Podobně, pokud váš předdefinovaný dotaz používá výstupní parametr, Nevkládat prázdné znaky mezi složenou závorku a symbol. Nakonec není nutné vkládat prázdné znaky před složenou závorku v příkazu **Call** nebo před klíčovým slovem **Select** v příkazu **Select** .

Obvyklým postupem je předání hodnoty NULL `Open`; v tomto případě `Open` volá [GetDefaultSQL](#getdefaultsql). Pokud používáte odvozenou třídu `CRecordset`, `GetDefaultSQL` poskytuje názvy tabulek, které jste zadali v ClassWizard. Místo toho lze zadat jiné informace v parametru `lpszSQL`.

Cokoli, co předáte, `Open` vytvoří konečný řetězec SQL pro dotaz (řetězec může obsahovat klauzule SQL **WHERE** a **ORDER by** připojené k řetězci `lpszSQL`, který jste předali), a pak dotaz spustí. Vytvořenou řetězcovou adresu lze prostudovat voláním [GetSQL](#getsql) po volání metody `Open`. Další podrobnosti o tom, jak sada záznamů vytvoří příkaz SQL a vybere záznamy, naleznete v článku [Sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).

Datové členy polí třídy sady záznamů jsou svázány se sloupci zvolených dat. Jsou-li vráceny jakékoli záznamy, první záznam se stává aktuálním záznamem.

Pokud chcete nastavit možnosti pro sadu záznamů, jako je filtr nebo řazení, určete je po sestavení objektu sady záznamů, ale před voláním `Open`. Chcete-li aktualizovat záznamy v sadě záznamů poté, co je sada záznamů již otevřena, zavolejte příkaz [Requery](#requery).

Další informace, včetně dalších příkladů, naleznete v článcích [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md), [Sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)a [Sada záznamů: vytváření a uzavírání sad záznamů (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).

### <a name="example"></a>Příklad

Následující příklady kódu ukazují různé formy `Open` volání.

[!code-cpp[NVC_MFCDatabase#16](../../mfc/codesnippet/cpp/crecordset-class_15.cpp)]

##  <a name="refreshrowset"></a>CRecordset:: RefreshRowset

Aktualizuje data a stav řádku v aktuální sadě řádků.

```
void RefreshRowset(
    WORD wRow,
    WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>Parametry

*wRow*<br/>
Pozice na jednom řádku v aktuální sadě řádků. Tato hodnota může být v rozsahu od nuly až po velikost sady řádků.

*wLockType*<br/>
Hodnota, která označuje, jak Uzamknout řádek po jeho obnovení. Podrobnosti najdete v tématu poznámky.

### <a name="remarks"></a>Poznámky

Pokud předáte hodnotu nula pro *wRow*, pak se aktualizuje každý řádek v sadě řádků.

Chcete-li použít `RefreshRowset`, je nutné implementovat hromadné načítání řádků zadáním možnosti `CRecordset::useMulitRowFetch` v [otevřené](#open) členské funkci.

`RefreshRowset` volá funkci rozhraní ODBC API `SQLSetPos`. Parametr *wLockType* určuje stav zámku řádku po provedení `SQLSetPos`. Následující tabulka popisuje možné hodnoty pro *wLockType*.

|wLockType|Popis|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE (výchozí hodnota)|Ovladač nebo zdroj dat zajišťuje, že řádek je ve stejném uzamčeném nebo odemčeném stavu, jako by byl zavolán `RefreshRowset`.|
|SQL_LOCK_EXCLUSIVE|Ovladač nebo zdroj dat zamkne řádek výhradně. Ne všechny zdroje dat podporují tento typ zámku.|
|SQL_LOCK_UNLOCK|Ovladač nebo zdroj dat odemkne řádek. Ne všechny zdroje dat podporují tento typ zámku.|

Další informace o `SQLSetPos`najdete v Windows SDK. Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="requery"></a>CRecordset:: Requery

Znovu sestaví (aktualizuje) sadu záznamů.

```
virtual BOOL Requery();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla sada záznamů úspěšně znovu sestavena; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Jsou-li vráceny jakékoli záznamy, první záznam se stává aktuálním záznamem.

Aby sada záznamů odrážela přidávání a odstraňování, které jste vy nebo jiní uživatelé nastavili na zdroj dat, je nutné sadu záznamů znovu sestavit voláním `Requery`. Pokud sada záznamů je dynamická sada, automaticky odrážejí aktualizace, které vy nebo jiní uživatelé provedete, do svých stávajících záznamů (ale ne přidaných). Pokud je sada záznamů snímkem, je nutné volat `Requery`, aby odrážela úpravy provedené jinými uživateli, a také přidání a odstranění.

V případě dynamické sady nebo snímku volejte `Requery` kdykoli chcete sadu záznamů znovu sestavit pomocí nového filtru nebo řazení, nebo hodnot nového parametru. Nastavte novou vlastnost Filter nebo Sort přiřazením nových hodnot `m_strFilter` a `m_strSort` před voláním `Requery`. Před voláním `Requery`nastavte nové parametry přiřazením nových hodnot datovým členům parametru. Pokud se řetězce filtru a řazení nezměnily, můžete použít dotaz, který zvyšuje výkon.

Pokud se pokus o opětovné sestavení sady záznamů nezdaří, sada záznamů je zavřena. Před voláním `Requery`můžete určit, zda lze sadu záznamů znovu dotazovat voláním členské funkce `CanRestart`. `CanRestart` nezaručuje, že `Requery` bude úspěšná.

> [!CAUTION]
>  Volání `Requery` až po volání metody [Open](#open).

### <a name="example"></a>Příklad

V tomto příkladu je znovu sestavena sada záznamů, aby bylo možné použít jiné pořadí řazení.

[!code-cpp[NVC_MFCDatabase#29](../../mfc/codesnippet/cpp/crecordset-class_16.cpp)]

##  <a name="setabsoluteposition"></a>CRecordset:: SetAbsolutePosition

Umístí sadu záznamů na záznamu odpovídající zadanému číslu záznamu.

```
void SetAbsolutePosition(long nRows);
```

### <a name="parameters"></a>Parametry

*Hodnota nRows*<br/>
Pořadové místo na základě jedné položky pro aktuální záznam v sadě záznamů.

### <a name="remarks"></a>Poznámky

`SetAbsolutePosition` přesune aktuální ukazatel záznamu na základě této řadové pozice.

> [!NOTE]
>  Tato členská funkce není platná pro sady záznamů s dopředné jen pro čtení.

Pro sady záznamů rozhraní ODBC, absolutní pozice nastavení 1 odkazuje na první záznam v sadě záznamů; nastavení 0 odkazuje na pozici začátku souboru (BOF).

Můžete také předat záporné hodnoty `SetAbsolutePosition`. V tomto případě je pozice sady záznamů vyhodnocena z konce sady záznamů. Například `SetAbsolutePosition( -1 )` přesune ukazatel na aktuální záznam na poslední záznam v sadě záznamů.

> [!NOTE]
>  Absolutní pozice není určena k použití jako náhradní číslo záznamu. Záložky jsou stále doporučeným způsobem zachování a návratu na danou pozici, protože pozice záznamu se mění při odstranění předcházejících záznamů. Kromě toho nemůžete mít jistotu, že daný záznam bude mít stejné absolutní umístění, pokud je znovu znovu vytvořena sada záznamů, protože pořadí jednotlivých záznamů v rámci sady záznamů není zaručeno, pokud není vytvořeno pomocí příkazu jazyka SQL pomocí klauzule **ORDER by.** klauzule.

Další informace o navigaci a záložkách sady záznamů naleznete v článcích [Sada záznamů: posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) a [Sada záznamů: záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

##  <a name="setbookmark"></a>CRecordset:: SetBookmark

Umístí sadu záznamů na záznam, který obsahuje zadanou záložku.

```
void SetBookmark(const CDBVariant& varBookmark);
```

### <a name="parameters"></a>Parametry

*varBookmark*<br/>
Odkaz na objekt [CDBVariant –](../../mfc/reference/cdbvariant-class.md) obsahující hodnotu záložky pro konkrétní záznam.

### <a name="remarks"></a>Poznámky

Chcete-li zjistit, zda jsou záložky v sadě záznamů podporovány, zavolejte [CanBookmark](#canbookmark). Chcete-li zpřístupnit záložky, pokud jsou podporovány, je nutné nastavit možnost `CRecordset::useBookmarks` v parametru *dwOptions* pro [otevřenou](#open) členskou funkci.

> [!NOTE]
>  Pokud záložky nejsou podporovány nebo nejsou k dispozici, volání `SetBookmark` bude mít za následek vyvolanou výjimku. Záložky nejsou podporovány pro sady záznamů s dopřednou podporou.

Chcete-li nejprve načíst záložku pro aktuální záznam, zavolejte metodu [GetBookmark](#getbookmark), která uloží hodnotu záložky do objektu `CDBVariant`. Později se můžete vrátit k tomuto záznamu voláním `SetBookmark` s použitím uložené hodnoty záložky.

> [!NOTE]
>  Po určitých operacích sady záznamů byste měli před voláním `SetBookmark`ověřit zachování záložky. Například pokud načtete záložku s `GetBookmark` a potom zavoláte `Requery`, záložka již nemusí být platná. Voláním [CDatabase:: GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) zkontrolujete, jestli můžete bezpečně volat `SetBookmark`.

Další informace o záložkách a navigaci v sadě záznamů naleznete v článcích [Sada záznamů: záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) a [Sada záznamů: posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

##  <a name="setfielddirty"></a>CRecordset:: SetFieldDirty

Označí datový člen pole sady záznamů jako změněný nebo beze změny.

```
void SetFieldDirty(void* pv, BOOL bDirty = TRUE);
```

### <a name="parameters"></a>Parametry

*PV*<br/>
Obsahuje adresu datového člena pole v sadě záznamů nebo hodnotu NULL. Pokud je NULL, všechna pole datových členů v sadě záznamů jsou označena příznakem. (C++ Hodnota null není shodná s hodnotou null v terminologii databáze, což znamená "nemá žádnou hodnotu.")

*bDirty*<br/>
TRUE, pokud má datový člen pole označení "dirty" (změněno). Jinak FALSE, pokud datový člen pole musí být označen jako "vyčistit" (beze změny).

### <a name="remarks"></a>Poznámky

Označení polí jako nezměněné zajistí, že se pole neaktualizuje a výsledkem je méně přenosů SQL.

> [!NOTE]
>  Tato členská funkce se nedá použít pro sady záznamů, které používají hromadné načítání řádků. Pokud jste implementovali hromadné načítání řádků, pak `SetFieldDirty` způsobí selhání kontrolního výrazu. Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Rozhraní označuje změněné datové členy pole tak, aby se zajistilo jejich zápis do záznamu ve zdroji dat pomocí mechanismu výměny pole záznamu (RFX). Změna hodnoty pole obvykle automaticky nastaví pole jako neměnné, takže nebudete muset volat `SetFieldDirty` sami, ale někdy budete chtít mít jistotu, že se sloupce explicitně aktualizují nebo vloží bez ohledu na to, jaká hodnota je v datech pole. člen.

> [!CAUTION]
>  Tuto členskou funkci volejte až poté, co jste volali [Edit](#edit) nebo [AddNew](#addnew).

Použití hodnoty NULL pro první argument funkce bude používat funkci pouze pro `outputColumn` pole, nikoli `param` polí. Například volání

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

nastaví pouze `outputColumn` pole na hodnotu NULL; `param` pole nebudou nijak ovlivněna.

Chcete-li pracovat s `param` poli, je nutné dodat skutečnou adresu jednotlivých `param`, na kterých chcete pracovat, například:

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

To znamená, že nemůžete nastavit všechna `param` pole na hodnotu NULL, stejně jako u polí `outputColumn`.

##  <a name="setfieldnull"></a>CRecordset:: SetFieldNull

Označí datový člen pole sady záznamů jako null (konkrétně bez hodnoty) nebo jako jiný než null.

```
void SetFieldNull(void* pv, BOOL bNull = TRUE);
```

### <a name="parameters"></a>Parametry

*PV*<br/>
Obsahuje adresu datového člena pole v sadě záznamů nebo hodnotu NULL. Pokud je NULL, všechna pole datových členů v sadě záznamů jsou označena příznakem. (C++ Hodnota null není shodná s hodnotou null v terminologii databáze, což znamená "nemá žádnou hodnotu.")

*bNull*<br/>
Nenulová, pokud má datový člen pole označení bez hodnoty (null). V opačném případě 0, pokud má datový člen pole označení příznakem jako jiný než null.

### <a name="remarks"></a>Poznámky

Když přidáte nový záznam do sady záznamů, všechna pole datových členů jsou zpočátku nastavena na hodnotu null a označena jako "dirtá" (změna). Když načtete záznam ze zdroje dat, jeho sloupce buď již mají hodnoty, nebo mají hodnotu null.

> [!NOTE]
>  Nevolejte tuto členskou funkci na sady záznamů, které používají hromadné načítání řádků. Pokud jste implementovali hromadné načítání řádků, volání `SetFieldNull` vede v neúspěšném kontrolním výrazu. Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Pokud chcete určit pole aktuálního záznamu, které nemá hodnotu, zavolejte `SetFieldNull` s *bNull* nastavenou na hodnotu true, abyste označili hodnotu null. Pokud pole již bylo označeno jako null a nyní chcete dát hodnotu, stačí nastavit novou hodnotu. Nemusíte odebírat příznak null s `SetFieldNull`. Chcete-li zjistit, zda je pole povoleno mít hodnotu null, zavolejte `IsFieldNullable`.

> [!CAUTION]
>  Tuto členskou funkci volejte až poté, co jste volali [Edit](#edit) nebo [AddNew](#addnew).

Použití hodnoty NULL pro první argument funkce bude používat funkci pouze pro `outputColumn` pole, nikoli `param` polí. Například volání

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

nastaví pouze `outputColumn` pole na hodnotu NULL; `param` pole nebudou nijak ovlivněna.

Chcete-li pracovat s `param` poli, je nutné dodat skutečnou adresu jednotlivých `param`, na kterých chcete pracovat, například:

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

To znamená, že nemůžete nastavit všechna `param` pole na hodnotu NULL, stejně jako u polí `outputColumn`.

> [!NOTE]
>  Při nastavování parametrů na hodnotu null, volání `SetFieldNull` před otevřením sady záznamů je výsledkem kontrolního výrazu. V tomto případě zavolejte [SetParamNull](#setparamnull).

`SetFieldNull` je implementována prostřednictvím [DoFieldExchange](#dofieldexchange).

##  <a name="setlockingmode"></a>CRecordset:: SetLockingMode

Nastaví režim uzamykání na "optimistické" zamykání (výchozí) nebo "pesimistické" zamykání. Určuje způsob uzamčení záznamů pro aktualizace.

```
void SetLockingMode(UINT nMode);
```

### <a name="parameters"></a>Parametry

*nMode*<br/>
Obsahuje jednu z následujících hodnot z `enum LockMode`:

- `optimistic` optimistické zamykání zamkne záznam, který se aktualizuje pouze během volání `Update`.

- `pessimistic` pesimistické zamykání uzamkne záznam hned po volání `Edit` a zůstane uzamčeno, dokud se neukončí volání `Update` nebo dokud nepřejdete na nový záznam.

### <a name="remarks"></a>Poznámky

Tuto členskou funkci volejte, pokud potřebujete určit, které ze dvou strategií zamykání záznamů se sada záznamů používá pro aktualizace. Ve výchozím nastavení je režim uzamykání sady záznamů `optimistic`. Můžete ji změnit na přísnější `pessimistic` strategii zamykání. Po sestavení a otevření objektu sady záznamů zavolejte `SetLockingMode`, ale před voláním `Edit`.

##  <a name="setparamnull"></a>CRecordset:: SetParamNull

Označí parametr jako null (konkrétně bez hodnoty) nebo jako jiný než null.

```
void SetParamNull(
    int nIndex,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index parametru založený na nule.

*bNull*<br/>
Pokud je hodnota TRUE (výchozí hodnota), parametr je označen jako null. V opačném případě je parametr označen jako jiný než null.

### <a name="remarks"></a>Poznámky

Na rozdíl od [SetFieldNull](#setfieldnull)můžete volat `SetParamNull` před otevřením sady záznamů.

`SetParamNull` se obvykle používá s předdefinovanými dotazy (uložené procedury).

##  <a name="setrowsetcursorposition"></a>CRecordset:: SetRowsetCursorPosition

Přesune kurzor na řádek v rámci aktuální sady řádků.

```
void SetRowsetCursorPosition(WORD wRow, WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>Parametry

*wRow*<br/>
Pozice na jednom řádku v aktuální sadě řádků. Tato hodnota může být v rozsahu od 1 do velikosti sady řádků.

*wLockType*<br/>
Hodnota označující, jak se má řádek po obnovení uzamknout Podrobnosti najdete v tématu poznámky.

### <a name="remarks"></a>Poznámky

Při implementaci hromadného načítání řádků jsou záznamy načteny sadou řádků, kde první záznam v načtené sadě řádků je aktuální záznam. Chcete-li vytvořit jiný záznam v rámci sady řádků v aktuálním záznamu, zavolejte `SetRowsetCursorPosition`. Můžete například zkombinovat `SetRowsetCursorPosition` s členskou funkcí [GetFieldValue –](#getfieldvalue) k dynamickému načtení dat z libovolného záznamu vaší sady záznamů.

Chcete-li použít `SetRowsetCursorPosition`, je nutné implementovat hromadné načítání řádků zadáním možnosti `CRecordset::useMultiRowFetch` parametru *dwOptions* v [otevřené](#open) členské funkci.

`SetRowsetCursorPosition` volá funkci rozhraní ODBC API `SQLSetPos`. Parametr *wLockType* určuje stav zámku řádku po provedení `SQLSetPos`. Následující tabulka popisuje možné hodnoty pro *wLockType*.

|wLockType|Popis|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE (výchozí hodnota)|Ovladač nebo zdroj dat zajišťuje, že řádek je ve stejném uzamčeném nebo odemčeném stavu, jako by byl zavolán `SetRowsetCursorPosition`.|
|SQL_LOCK_EXCLUSIVE|Ovladač nebo zdroj dat zamkne řádek výhradně. Ne všechny zdroje dat podporují tento typ zámku.|
|SQL_LOCK_UNLOCK|Ovladač nebo zdroj dat odemkne řádek. Ne všechny zdroje dat podporují tento typ zámku.|

Další informace o `SQLSetPos`najdete v Windows SDK. Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="setrowsetsize"></a>CRecordset:: SetRowsetSize

Určuje počet záznamů, které chcete načíst během načítání.

```
virtual void SetRowsetSize(DWORD dwNewRowsetSize);
```

### <a name="parameters"></a>Parametry

*dwNewRowsetSize*<br/>
Počet řádků, které mají být načteny během daného načtení.

### <a name="remarks"></a>Poznámky

Tato virtuální členská funkce určuje, kolik řádků chcete načíst během jednoho načtení při použití hromadného načítání řádků. Chcete-li implementovat hromadné načítání řádků, je nutné nastavit možnost `CRecordset::useMultiRowFetch` v parametru *dwOptions* pro [otevřenou](#open) členskou funkci.

> [!NOTE]
>  Volání `SetRowsetSize` bez implementace hromadného načtení řádku způsobí selhání kontrolního výrazu.

Před voláním `Open`, aby se původně nastavila velikost sady řádků pro sadu záznamů, volejte `SetRowsetSize`. Výchozí velikost sady řádků při implementaci hromadného načítání řádků je 25.

> [!NOTE]
>  Při volání `SetRowsetSize`buďte opatrní. Pokud ručně přidělíte úložiště pro data (určené možností `CRecordset::userAllocMultiRowBuffers` parametru dwOptions v `Open`), měli byste ověřit, zda je nutné znovu přidělit tyto vyrovnávací paměti úložiště po volání `SetRowsetSize`, ale před provedením všech kurzorů. navigační operace.

Chcete-li získat aktuální nastavení pro velikost sady řádků, zavolejte [GetRowsetSize](#getrowsetsize).

Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="update"></a>CRecordset:: Update

Dokončí operaci `AddNew` nebo `Edit` uložením nových nebo upravených dat ve zdroji dat.

```
virtual BOOL Update();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl jeden záznam úspěšně aktualizován; v opačném případě 0, pokud se žádné sloupce nezměnily. Pokud nebyly aktualizovány žádné záznamy, nebo pokud byl aktualizován více než jeden záznam, je vyvolána výjimka. Výjimka je také vyvolána pro jakékoli jiné selhání ve zdroji dat.

### <a name="remarks"></a>Poznámky

Tuto členskou funkci volejte po volání metody [AddNew](#addnew) nebo [Edit](#edit) členské funkce. Toto volání je vyžadováno k dokončení operace `AddNew` nebo `Edit`.

> [!NOTE]
>  Pokud jste implementovali hromadné načítání řádků, nemůžete volat `Update`. Výsledkem bude selhání kontrolního výrazu. I když `CRecordset` třídy neposkytuje mechanismus pro aktualizaci hromadných řádků dat, můžete napsat vlastní funkce pomocí funkce rozhraní ODBC API `SQLSetPos`. Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`AddNew` i `Edit` připraví upravenou vyrovnávací paměť, ve které jsou přidaná nebo upravená data umístěna k uložení do zdroje dat. `Update` uloží data. Aktualizují se pouze pole označená nebo zjištěná jako změněná.

Pokud zdroj dat podporuje transakce, můžete uskutečnit `Update` volání (a odpovídající `AddNew` nebo volání `Edit`) část transakce. Další informace o transakcích naleznete v článku [transakce (ODBC)](../../data/odbc/transaction-odbc.md).

> [!CAUTION]
>  Pokud zavoláte `Update` bez prvního volání `AddNew` nebo `Edit`, `Update` vyvolá `CDBException`. Pokud voláte `AddNew` nebo `Edit`, je nutné volat `Update` před voláním operace `Move` nebo před zavřením buď sady záznamů nebo připojení ke zdroji dat. V opačném případě se vaše změny ztratí bez oznámení.

Podrobnosti o zpracování selhání `Update` naleznete v článku [Sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

### <a name="example"></a>Příklad

Viz článek [transakce: provádění transakce v sadě záznamů (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="see-also"></a>Viz také:

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDatabase – třída](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordView – třída](../../mfc/reference/crecordview-class.md)
