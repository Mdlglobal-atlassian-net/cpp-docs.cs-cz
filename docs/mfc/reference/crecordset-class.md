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
ms.openlocfilehash: efb833a8d4cc0b801f75951bc648d6b83df5bae8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57305182"
---
# <a name="crecordset-class"></a>CRecordset – třída

Představuje sadu záznamů ze zdroje dat vybrané.

## <a name="syntax"></a>Syntaxe

```
class CRecordset : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CRecordset::CRecordset](#crecordset)|Vytvoří `CRecordset` objektu. Odvozené třídy musí poskytovat konstruktor, který volá tento.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CRecordset::AddNew](#addnew)|Připraví pro přidání nového záznamu. Volání `Update` k dokončení přidání.|
|[CRecordset::CanAppend](#canappend)|Vrátí nenulovou hodnotu, pokud nové záznamy může být přidána do sady záznamů prostřednictvím `AddNew` členskou funkci.|
|[CRecordset::CanBookmark](#canbookmark)|Vrátí nenulovou hodnotu, pokud sada záznamů podporuje záložky.|
|[CRecordset::Cancel](#cancel)|Zruší asynchronní operace nebo proces z druhého vlákna.|
|[CRecordset::CancelUpdate](#cancelupdate)|Zruší všechny čekající aktualizace z důvodu `AddNew` nebo `Edit` operace.|
|[CRecordset::CanRestart](#canrestart)|Vrátí nenulovou hodnotu, pokud `Requery` může být volána znovu spustit dotaz sadu záznamů.|
|[CRecordset::CanScroll](#canscroll)|Vrátí nenulovou hodnotu, pokud při procházení záznamů.|
|[CRecordset::CanTransact](#cantransact)|Vrátí nenulovou hodnotu, pokud zdroj dat podporuje transakce.|
|[CRecordset::CanUpdate](#canupdate)|Vrátí nenulovou hodnotu, pokud je možné aktualizovat sadu záznamů (můžete přidat, aktualizaci nebo odstranění záznamů).|
|[CRecordset::CheckRowsetError](#checkrowseterror)|Volá se, aby zpracovávat chyby vytvořené během načítání záznam.|
|[CRecordset::Close](#close)|Zavře sady záznamů a s ním spojená HSTMT rozhraní ODBC.|
|[CRecordset::Delete](#delete)|Odstraní aktuální záznam ze sady záznamů. Po odstranění se musí explicitně přechod na jiný záznam.|
|[CRecordset::DoBulkFieldExchange](#dobulkfieldexchange)|Volá se, aby exchange hromadné řádky dat ze zdroje dat na sadu záznamů. Implementuje Hromadná výměna polí záznamu (Bulk RFX).|
|[CRecordset::DoFieldExchange](#dofieldexchange)|Volá se pro výměnu dat (v obou směrech) mezi datové členy polí sady záznamů a odpovídající záznam ve zdroji dat. Implementuje zaznamenat exchange poli (RFX).|
|[CRecordset::Edit](#edit)|Připraví změn aktuálního záznamu. Volání `Update` dokončete úpravu.|
|[CRecordset::FlushResultSet](#flushresultset)|Vrátí nenulovou hodnotu, pokud existuje jiný výsledek nastavte se má načíst, při použití předdefinovaného dotazu.|
|[CRecordset::GetBookmark](#getbookmark)|Přiřadí hodnotu záložku záznamu parametrem objektu.|
|[CRecordset::GetDefaultConnect](#getdefaultconnect)|Volá za účelem získání výchozí připojovací řetězec.|
|[CRecordset::GetDefaultSQL](#getdefaultsql)|Volá za účelem získání výchozí řetězec SQL k provedení.|
|[CRecordset::GetFieldValue](#getfieldvalue)|Vrátí hodnotu pole v sadě záznamů.|
|[CRecordset::GetODBCFieldCount](#getodbcfieldcount)|Vrátí počet polí v sadě záznamů.|
|[CRecordset::GetODBCFieldInfo](#getodbcfieldinfo)|Vrátí určité druhy informací o polích v sadě záznamů.|
|[CRecordset::GetRecordCount](#getrecordcount)|Vrátí počet záznamů v sadě záznamů.|
|[CRecordset::GetRowsetSize](#getrowsetsize)|Vrátí počet záznamů, které chcete načíst během jednoho načtení.|
|[CRecordset::GetRowsFetched](#getrowsfetched)|Vrátí skutečný počet řádků, které jsou načteny.|
|[CRecordset::GetRowStatus](#getrowstatus)|Vrátí stavový řádek po fetch.|
|[CRecordset::GetSQL](#getsql)|Získá řetězec SQL použít pro výběr záznamů pro sady záznamů.|
|[CRecordset::GetStatus](#getstatus)|Získá stav sada záznamů: index aktuální záznam a určuje, zda byl získán konečný počet záznamů.|
|[CRecordset::GetTableName](#gettablename)|Získá název tabulky, na kterých je založena sadu záznamů.|
|[CRecordset::IsBOF](#isbof)|Vrátí nenulovou hodnotu, pokud sada záznamů obsahuje byl umístěn před první záznam. Neexistuje aktuální záznam.|
|[CRecordset::IsDeleted](#isdeleted)|Vrátí nenulovou hodnotu, pokud sada záznamů je umístěn na odstraněný záznam.|
|[CRecordset::IsEOF](#iseof)|Vrátí nenulovou hodnotu, pokud sada záznamů zařadila po posledním záznamu. Neexistuje aktuální záznam.|
|[CRecordset::IsFieldDirty](#isfielddirty)|Vrátí nenulovou hodnotu, pokud byl změněn v zadaném poli aktuální záznam.|
|[CRecordset::IsFieldNull](#isfieldnull)|Vrátí nenulovou hodnotu, pokud aktuální záznam v zadaném poli má hodnotu null (neobsahuje hodnotu).|
|[CRecordset::IsFieldNullable](#isfieldnullable)|Vrátí nenulovou hodnotu, pokud zadané pole v aktuální záznam můžete nastavit na hodnotu null (s žádná hodnota).|
|[CRecordset::IsOpen](#isopen)|Vrátí nenulovou hodnotu, pokud `Open` se zavolala dříve.|
|[CRecordset::Move](#move)|Nastaví pozici sady záznamů na zadaný počet záznamů z aktuální záznam v obou směrech.|
|[CRecordset::MoveFirst](#movefirst)|Aktuální záznam se umístí na první záznam v sadě záznamů. Test pro `IsBOF` první.|
|[CRecordset::MoveLast](#movelast)|Aktuální záznam se umístí na poslední záznam nebo poslední sadu řádků. Test pro `IsEOF` první.|
|[CRecordset::MoveNext](#movenext)|Aktuální záznam se umístí na další záznam nebo na další sadu řádků. Test pro `IsEOF` první.|
|[CRecordset::MovePrev](#moveprev)|Aktuální záznam se umístí na předchozí záznam nebo na předchozí sadu řádků. Test pro `IsBOF` první.|
|[CRecordset::OnSetOptions](#onsetoptions)|Volá se, aby nastavení možností (používá se na výběr) pro zadaný příkaz ODBC.|
|[CRecordset::OnSetUpdateOptions](#onsetupdateoptions)|Volá se, aby nastavení možností (používá se při aktualizaci) pro zadaný příkaz ODBC.|
|[CRecordset::Open](#open)|Otevře sadu záznamů načtením tabulky nebo provedením dotazu, který sada záznamů představuje.|
|[CRecordset::RefreshRowset](#refreshrowset)|Aktualizuje data a stav zadaný počet řádků.|
|[CRecordset::Requery](#requery)|Spustí dotaz sady záznamů znovu a aktualizujte vybrané záznamy.|
|[CRecordset::SetAbsolutePosition](#setabsoluteposition)|Nastaví pozici sady záznamů v záznamu odpovídá zadané číslo záznamu.|
|[CRecordset::SetBookmark](#setbookmark)|Nastaví pozici sady záznamů na zadaný záznam záložkou.|
|[CRecordset::SetFieldDirty](#setfielddirty)|V zadaném poli aktuální záznam označuje, jak změnit.|
|[CRecordset::SetFieldNull](#setfieldnull)|Nastaví hodnotu zadaného pole v aktuální záznam na hodnotu null (s žádná hodnota).|
|[CRecordset::SetLockingMode](#setlockingmode)|Nastaví režim uzamčení "optimistické" uzamčení (výchozí) nebo "pesimistické" zamykání. Určuje, jak jsou záznamy zamknuté aktualizací.|
|[CRecordset::SetParamNull](#setparamnull)|Zadaný parametr nastaví na hodnotu null (s žádná hodnota).|
|[CRecordset::SetRowsetCursorPosition](#setrowsetcursorposition)|Umístí kurzor na zadaný řádek v rámci dané sadě řádků.|
|[CRecordset::SetRowsetSize](#setrowsetsize)|Určuje počet záznamů, které chcete načíst během fetch.|
|[CRecordset::Update](#update)|Dokončení `AddNew` nebo `Edit` operace uložením nových nebo upravených dat ve zdroji dat.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CRecordset::m_hstmt](#m_hstmt)|Obsahuje popisovač příkazu ODBC pro sady záznamů. Typ `HSTMT`.|
|[CRecordset::m_nFields](#m_nfields)|Obsahuje číslo pole datových členů v sadě záznamů. Typ `UINT`.|
|[CRecordset::m_nParams](#m_nparams)|Obsahuje počet parametry datových členů v sadě záznamů. Typ `UINT`.|
|[CRecordset::m_pDatabase](#m_pdatabase)|Obsahuje ukazatel `CDatabase` objekt, jehož prostřednictvím sady záznamů je připojený ke zdroji dat.|
|[CRecordset::m_strFilter](#m_strfilter)|Obsahuje `CString` jazyk SQL (Structured Query), který určuje `WHERE` klauzuli. Použít jako filtr k výběru jen takové záznamy, které splňují určitá kritéria.|
|[CRecordset::m_strSort](#m_strsort)|Obsahuje `CString` SQL, který určuje `ORDER BY` klauzuli. Používat k ovládání řazení záznamů.|

## <a name="remarks"></a>Poznámky

Označuje jako "sady záznamů" `CRecordset` objekty se obvykle používají ve dvou formách: dynamické a snímků. Dynamická sada zůstane synchronizovaná se aktualizace dat provedené jinými uživateli. Snímek je statické zobrazení dat. Každý formulář představuje sadu záznamů stanoveno v době otevření sady záznamů, ale při posouvání se záznamem v dynamická sada odráží změny následně záznam, jiným uživatelům nebo jiné sady záznamů ve vaší aplikaci.

> [!NOTE]
>  Pokud pracujete s třídami objektů DAO (Data Access), a ne třídy připojení ODBC (Open Database), použijte třídu [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) místo. Další informace najdete v článku [přehled: Databáze programování](../../data/data-access-programming-mfc-atl.md).

Pro práci s buď typ sady záznamů, obvykle odvodit třídu specifické pro aplikaci záznamů z `CRecordset`. Sady záznamů vybírají záznamy ze zdroje dat, a pak můžete:

- Projděte si záznamy.

- Aktualizovat záznamy a zadat režim uzamčení.

- Filtrování záznamů záznamy, které vybere z dostupných ve zdroji dat omezit.

- Řazení záznamů.

- Parametrizace sady záznamů s informacemi, které nejsou známé až do běhu přizpůsobit jeho výběr.

Použití vaší třídy, otevření databáze a vytvořit objekt sady záznamů, předá konstruktoru ukazatel na váš `CDatabase` objektu. Poté zavolejte sady záznamů `Open` členská funkce, kde můžete určit, zda je objekt dynamická sada nebo snímku. Volání `Open` vybere data z datového zdroje. Po je otevřen objekt sady záznamů, projděte si záznamy a pracovat s nimi pomocí jeho členské funkce a datovým členům. Operace jsou dostupné závisí na tom, zda je objekt dynamická sada nebo snímku, ať už jde o aktualizovat nebo jen pro čtení (závisí na možnosti připojení ODBC (Open Database) zdroj dat), a určuje, zda jste implementovali hromadné načítání řádků. Chcete-li aktualizovat záznamy, které mohou mít se změnily nebo přibyly od `Open` volání, volání objektu `Requery` členskou funkci. Volání objektu `Close` členské funkce a zničte objekt, když dokončíte s ním.

V odvozené `CRecordset` třídy, záznamu exchange poli (RFX) nebo hromadná výměna pole záznamu (Bulk RFX) slouží k podpoře pro čtení a aktualizaci polí záznamů.

Další informace o výměna polí záznamu a sady záznamů, najdete v článcích [přehled: Databáze programování](../../data/data-access-programming-mfc-atl.md), [záznamů (ODBC)](../../data/odbc/recordset-odbc.md), [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md), a [zaznamenat Exchange poli (RFX)](../../data/odbc/record-field-exchange-rfx.md). Zaměřením na dynamické a snímků, najdete v článcích [dynamická sada](../../data/odbc/dynaset.md) a [snímku](../../data/odbc/snapshot.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CRecordset`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

##  <a name="addnew"></a>  CRecordset::AddNew

Připraví pro přidání nového záznamu do tabulky.

```
virtual void AddNew();
```

### <a name="remarks"></a>Poznámky

Je třeba zavolat [Requery](#requery) členskou funkci zobrazíte nově přidaný záznam. Pole záznamu jsou zpočátku hodnotu Null. (V terminologii databáze s hodnotou Null znamená "mít žádná hodnota" a není stejná jako hodnota NULL v jazyce C++.) K dokončení operace, musí volat [aktualizace](#update) členskou funkci. `Update` Uloží změny do zdroje dat.

> [!NOTE]
>  Pokud jste implementovali hromadné načítání řádků, nelze volat `AddNew`. To způsobí neplatnost kontrolního výrazu. Přestože třída `CRecordset` neposkytuje mechanismus pro hromadnou aktualizaci řádků dat, můžete napsat vlastní funkce pomocí funkce ODBC API `SQLSetPos`. Další informace o hromadném načítání řádků naleznete v článku [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`AddNew` připraví nový, prázdný záznam pomocí sady záznamů pole datových členů. Po zavolání `AddNew`, nastavte hodnoty, které chcete do sady záznamů pole datových členů. (Není potřeba volat [upravit](#edit) členské funkce pro tento účel; použijte `Edit` pouze pro existující záznamy.) Pokud následně voláte `Update`, změněné na zdroj dat se uloží hodnoty v poli datové členy.

> [!CAUTION]
>  Pokud posunete na nový záznam, dříve než zavoláte `Update`, dojde ke ztrátě nový záznam a žádná varování je přiřazena.

Pokud zdroj dat podporuje transakce, můžete vytvořit vaše `AddNew` volání součástí transakce. Další informace o transakcích, naleznete v tématu třídy [CDatabase](../../mfc/reference/cdatabase-class.md). Všimněte si, že byste měli volat [CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) před voláním `AddNew`.

> [!NOTE]
>  Pro dynamické sady nové záznamy se přidají do sady záznamů jako poslední záznam. Přidání záznamů nejsou přidány do snímků je nutné volat `Requery` aktualizace sady záznamů.

Je neplatné volat `AddNew` pro sadu záznamů jehož `Open` nebyla volána členská funkce. A `CDBException` je vyvolána, pokud zavoláte `AddNew` pro sadu záznamů, které se nejde připojit k. Můžete určit, jestli je sada záznamů aktualizovat pomocí volání [CanAppend](#canappend).

Další informace najdete v následujících článcích: [Recordset: Jak sady záznamů aktualizují záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md), [sada záznamů: Přidání, aktualizace nebo odstranění záznamů (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), a [transakce (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="example"></a>Příklad

Přečtěte si článek [transakce: Provádění transakcí v sadě záznamů (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

##  <a name="canappend"></a>  CRecordset::CanAppend

Určuje, zda dřív otevřených záznamů slouží k přidání nových záznamů.

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud sada záznamů umožňuje přidávání nových záznamů; jinak 0. `CanAppend` Vrátí hodnotu 0-li otevřít sadu záznamů jen pro čtení.

##  <a name="canbookmark"></a>  CRecordset::CanBookmark

Určuje, zda sada záznamů umožňuje označit záznamů pomocí záložky.

```
BOOL CanBookmark() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud sada záznamů podporuje záložky; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce je nezávislá `CRecordset::useBookmarks` možnost *dwOptions* parametr [otevřít](#open) členskou funkci. `CanBookmark` Určuje, zda daný ovladač ODBC a kurzor typ podpory záložek. `CRecordset::useBookmarks` Určuje, zda záložky k dispozici, pokud jsou podporovány.

> [!NOTE]
>  Záložky nejsou podporované sady záznamů s posouváním pouze vpřed.

Další informace o záložek a navigaci v sadě záznamů najdete v článcích [sada záznamů: Záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) a [sada záznamů: Posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

##  <a name="cancel"></a>  CRecordset::Cancel

Požadavky, že zdroj dat zrušit probíhá asynchronní operace nebo proces z druhého vlákna.

```
void Cancel();
```

### <a name="remarks"></a>Poznámky

Mějte na paměti, že třídy knihovny MFC rozhraní ODBC již nebudete používat asynchronní zpracování. k provádění asynchronní operace, musíte přímo zavolat funkci rozhraní API ODBC `SQLSetConnectOption`. Další informace naleznete v tématu "Provádění funkce asynchronně" v *Příručka programátora SDK ODBC*.

##  <a name="cancelupdate"></a>  CRecordset::CancelUpdate

Zruší všechny čekající aktualizace, způsobené [upravit](#edit) nebo [AddNew](#addnew) operace, před [aktualizace](#update) je volána.

```
void CancelUpdate();
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Tato členská funkce se nedá použít pro sady záznamů, které jsou pomocí hromadné načítání řádků, protože takové sady záznamů nejde volat metodu `Edit`, `AddNew`, nebo `Update`. Další informace o hromadném načítání řádků naleznete v článku [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Pokud je povolena automatická kontrola nečistých polí, `CancelUpdate` obnoví členské proměnné na hodnoty měli před `Edit` nebo `AddNew` byl volaný; jinak vrátí hodnotu, zůstane žádné změny hodnot. Ve výchozím nastavení je kontrola automatické pole povolena při otevření sady záznamů. Ho zakážete, je nutné zadat `CRecordset::noDirtyFieldCheck` v *dwOptions* parametr [otevřít](#open) členskou funkci.

Další informace o aktualizaci dat, najdete v článku [sada záznamů: Přidání, aktualizace nebo odstranění záznamů (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md).

##  <a name="canrestart"></a>  CRecordset::CanRestart

Určuje, zda sada záznamů umožňuje restartovat dotaz (Chcete-li aktualizovat své záznamy) voláním `Requery` členskou funkci.

```
BOOL CanRestart() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je povoleno znova poslal dotaz; jinak 0.

##  <a name="canscroll"></a>  CRecordset::CanScroll

Určuje, zda sada záznamů umožňuje posouvání.

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud sada záznamů, umožňuje posouvání; jinak 0.

### <a name="remarks"></a>Poznámky

Další informace o procházení, najdete v článku [sada záznamů: Posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

##  <a name="cantransact"></a>  CRecordset::CanTransact

Určuje, zda sada záznamů umožňuje transakce.

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud sada záznamů umožňuje operací. jinak 0.

### <a name="remarks"></a>Poznámky

Další informace najdete v článku [transakce (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="canupdate"></a>  CRecordset::CanUpdate

Určuje, zda je možné aktualizovat sady záznamů.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud sada záznamů je možné aktualizovat; jinak 0.

### <a name="remarks"></a>Poznámky

Sada záznamů může být jen pro čtení, pokud podkladový zdroj dat je jen pro čtení, nebo pokud jste zadali `CRecordset::readOnly` v *dwOptions* parametr při otevření sady záznamů.

##  <a name="checkrowseterror"></a>  CRecordset::CheckRowsetError

Volá se, aby zpracovávat chyby vytvořené během načítání záznam.

```
virtual void CheckRowsetError(RETCODE nRetCode);
```

### <a name="parameters"></a>Parametry

*nRetCode*<br/>
Funkce rozhraní ODBC API návratový kód. Podrobnosti najdete v tématu poznámky.

### <a name="remarks"></a>Poznámky

Tato virtuální členská funkce zpracovává chyby, ke kterým dochází při načtení záznamů, a je užitečný při hromadné načítání řádků. Možná budete chtít zvážit přepsání `CheckRowsetError` implementovat vlastní zpracování chyb.

`CheckRowsetError` je volána automaticky v navigační operace kurzoru, jako například `Open`, `Requery`, ani na žádného `Move` operace. Je jí předán na návratový typ funkce ODBC API `SQLExtendedFetch`. V následující tabulce jsou uvedeny možné hodnoty pro *nRetCode* parametru.

|nRetCode|Popis|
|--------------|-----------------|
|SQL_SUCCESS|Funkce úspěšně; nejsou dostupné žádné další informace.|
|SQL_SUCCESS_WITH_INFO|Funkce byla úspěšně dokončena, případně s méně závažná chyba. Další informace lze získat voláním `SQLError`.|
|SQL_NO_DATA_FOUND|Všechny řádky ze sady výsledků mají načíst.|
|SQL_ERROR|Funkce se nezdařila. Další informace lze získat voláním `SQLError`.|
|SQL_INVALID_HANDLE|Funkce se nezdařila kvůli neplatné prostředí popisovač, popisovače připojení nebo popisovač příkazu. To znamená o programovou chybu. Je k dispozici žádné další informace o `SQLError`.|
|SQL_STILL_EXECUTING|Funkce, která byla spuštěna asynchronně stále probíhá. Všimněte si, že ve výchozím nastavení, MFC nikdy předá tuto hodnotu a `CheckRowsetError`; Knihovny MFC bude dál volání `SQLExtendedFetch` dokud by již nevracelo SQL_STILL_EXECUTING.|

Další informace o `SQLError`, naleznete v sadě Windows SDK. Další informace o hromadném načítání řádků naleznete v článku [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="close"></a>  CRecordset::Close

Zavře sadu záznamů.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

HSTMT rozhraní ODBC a veškerou paměť framework přidělené pro sady záznamů jsou navrácena. Obvykle po volání `Close`, odstraňte objekt sady záznamů jazyka C++, pokud byla přidělena pomocí **nové**.

Můžete volat `Open` znovu po volání `Close`. Díky tomu můžete znovu použít objekt sady záznamů. Alternativou je volání `Requery`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#17](../../mfc/codesnippet/cpp/crecordset-class_1.cpp)]

##  <a name="crecordset"></a>  CRecordset::CRecordset

Vytvoří `CRecordset` objektu.

```
CRecordset(CDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>Parametry

*pDatabase*<br/>
Obsahuje ukazatel `CDatabase` objekt nebo hodnotu NULL. Pokud není NULL a `CDatabase` objektu `Open` členská funkce se nevolala pro připojení ke zdroji dat, sada záznamů se pokusí otevřít ho za vás během své vlastní `Open` volání. Pokud předáte hodnotu NULL, `CDatabase` objekt je vytvořen a připojené pomocí informace o zdroji dat jste zadali při odvozenou třídu sady záznamů s ClassWizard.

### <a name="remarks"></a>Poznámky

Můžete buď používat `CRecordset` přímo nebo odvozovat třídu specifické pro aplikaci z `CRecordset`. ClassWizard můžete použít k odvození třídy sady záznamů.

> [!NOTE]
>  Odvozená třída *musí* zadat vlastní konstruktor. V konstruktoru odvozené třídy volání konstruktoru `CRecordset::CRecordset`, předáním příslušné parametry společně.

Předat hodnotu NULL do konstruktoru sady záznamů mít `CDatabase` objekt vytvořen a připojení automaticky za vás. To je užitečné sdruženou hodnotu, která není nutné vytvořit a připojit `CDatabase` objektu před sestavením sady záznamů.

### <a name="example"></a>Příklad

Další informace najdete v článku [sada záznamů: Deklarování třídy pro tabulku (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).

##  <a name="delete"></a>  CRecordset::Delete

Odstraní aktuální záznam.

```
virtual void Delete();
```

### <a name="remarks"></a>Poznámky

Po úspěšném odstranění sady záznamů pole datových členů jsou nastaveny na hodnotu Null a musí explicitně voláním `Move` funkce, aby bylo možné přesunout mimo odstraněný záznam. Jakmile přesunete mimo odstraněným záznamem, není možné vrátit. Pokud je zdroj dat podporuje transakce, lze provádět `Delete` volání součástí transakce. Další informace najdete v článku [transakce (ODBC)](../../data/odbc/transaction-odbc.md).

> [!NOTE]
>  Pokud jste implementovali hromadné načítání řádků, nelze volat `Delete`. To způsobí neplatnost kontrolního výrazu. Přestože třída `CRecordset` neposkytuje mechanismus pro hromadnou aktualizaci řádků dat, můžete napsat vlastní funkce pomocí funkce ODBC API `SQLSetPos`. Další informace o hromadném načítání řádků naleznete v článku [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!CAUTION]
>  Sada záznamů třeba umožnit aktualizaci modelové a musí být platný záznam v sadě záznamů při volání `Delete`; v opačném případě dojde k chybě. Například pokud odstranit záznam, ale ne přejděte na nový záznam, před voláním `Delete` znovu `Delete` vyvolá [CDBException](../../mfc/reference/cdbexception-class.md).

Na rozdíl od [AddNew](#addnew) a [upravit](#edit), volání `Delete` nenásleduje volání [aktualizace](#update). Pokud `Delete` volání selže, pole data členů jsou ponechány beze změny.

### <a name="example"></a>Příklad

Tento příklad ukazuje na sadu záznamů vytvořené v rámci funkce. Příklad předpokládá existenci `m_dbCust`, členské proměnné typu `CDatabase` již připojen ke zdroji dat.

[!code-cpp[NVC_MFCDatabase#18](../../mfc/codesnippet/cpp/crecordset-class_2.cpp)]

##  <a name="dobulkfieldexchange"></a>  CRecordset::DoBulkFieldExchange

Volá se, aby exchange hromadné řádky dat ze zdroje dat na sadu záznamů. Implementuje Hromadná výměna polí záznamu (Bulk RFX).

```
virtual void DoBulkFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) objektu. Rozhraní se už nastavili tento objekt k určení kontextu pro operaci exchange pole.

### <a name="remarks"></a>Poznámky

Po implementaci hromadné načítání řádků volá framework tato členská funkce automaticky posílat data ze zdroje dat do objektu sady záznamů. `DoBulkFieldExchange` sváže parametr datové členy, pokud chcete parametr zástupné texty v řetězci příkaz SQL pro výběr sady záznamů.

Pokud není implementována hromadné načítání řádků, volá framework [DoFieldExchange](#dofieldexchange). Implementovat hromadné načítání řádků, je nutné zadat `CRecordset::useMultiRowFetch` možnost *dwOptions* parametr [otevřít](#open) členskou funkci.

> [!NOTE]
> `DoBulkFieldExchange` je dostupná jenom v případě, že používáte třídu odvozenou z `CRecordset`. Pokud jste vytvořili objekt sady záznamů přímo z `CRecordset`, je třeba zavolat [getfieldvalue –](#getfieldvalue) členské funkce lze získat data.

Hromadná výměna pole záznamu (Bulk RFX) je podobný výměna pole záznamu (RFX). Je automaticky přenesená data ze zdroje dat do objektu sady záznamů. Však nelze volat `AddNew`, `Edit`, `Delete`, nebo `Update` chcete přenést změny zpět do zdroje dat. Třída `CRecordset` aktuálně neposkytuje mechanismus pro hromadnou aktualizaci řádků dat; však můžete napsat vlastní funkce pomocí funkce ODBC API `SQLSetPos`.

Všimněte si, že ClassWizard nepodporuje Hromadná výměna polí záznamu; Proto je nutné přepsat `DoBulkFieldExchange` ručně pomocí volání funkcí RFX hromadného zápisu. Další informace o těchto funkcích naleznete v tématu [funkce výměny polí v záznamu](../../mfc/reference/record-field-exchange-functions.md).

Další informace o hromadném načítání řádků naleznete v článku [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Související informace najdete v článku [výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md).

##  <a name="dofieldexchange"></a>  CRecordset::DoFieldExchange

Volá se pro výměnu dat (v obou směrech) mezi datové členy polí sady záznamů a odpovídající záznam ve zdroji dat. Implementuje zaznamenat exchange poli (RFX).

```
virtual void DoFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) objektu. Rozhraní se už nastavili tento objekt k určení kontextu pro operaci exchange pole.

### <a name="remarks"></a>Poznámky

Při hromadné načítání řádků není implementována, volá framework umožňuje automaticky výměnu dat mezi datové členy polí objektu sady záznamů a odpovídající sloupce aktuální záznam ve zdroji dat. Tato členská funkce. `DoFieldExchange` sváže parametr datové členy, pokud chcete parametr zástupné texty v řetězci příkaz SQL pro výběr sady záznamů.

Pokud je implementovaná hromadné načítání řádků, volá framework [DoBulkFieldExchange](#dobulkfieldexchange). Implementovat hromadné načítání řádků, je nutné zadat `CRecordset::useMultiRowFetch` možnost *dwOptions* parametr [otevřít](#open) členskou funkci.

> [!NOTE]
> `DoFieldExchange` je dostupná jenom v případě, že používáte třídu odvozenou z `CRecordset`. Pokud jste vytvořili objekt sady záznamů přímo z `CRecordset`, je třeba zavolat [getfieldvalue –](#getfieldvalue) členské funkce lze získat data.

Výměna dat pole, kterým se říká výměna pole záznamu (RFX), funguje v obou směrech: z objektu sady záznamů datoví členové pole na pole záznamu ve zdroji dat a z tohoto záznamu ve zdroji dat do objektu sady záznamů.

Pouze akce je obvykle třeba provést při implementaci `DoFieldExchange` pro sady záznamů odvozené třídy je vytvořte třídu s ClassWizard a zadejte názvy a datové typy pole datových členů. Je také přidat kód do co ClassWizard zapisuje zadat parametry datových členů nebo řešit všechny sloupce, které dynamickou vazbu. Další informace najdete v článku [sada záznamů: Dynamické vazby datových sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Při deklaraci vaší třídy odvozené sady záznamů s ClassWizard Průvodce provádí zápis přepsání `DoFieldExchange` , který vypadá podobně jako v následujícím příkladu:

[!code-cpp[NVC_MFCDatabase#19](../../mfc/codesnippet/cpp/crecordset-class_3.cpp)]

Další informace o funkcí RFX, naleznete v tématu [funkce výměny polí v záznamu](../../mfc/reference/record-field-exchange-functions.md).

Pro další příklady a podrobnými informacemi o `DoFieldExchange`, najdete v článku [výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md). Obecné informace o RFX, najdete v článku [výměna pole záznamu](../../data/odbc/record-field-exchange-rfx.md).

##  <a name="edit"></a>  CRecordset::Edit

Umožňuje změnit aktuální záznam.

```
virtual void Edit();
```

### <a name="remarks"></a>Poznámky

Po zavolání `Edit`, datové členy polí můžete změnit přímo resetováním jejich hodnoty. Na dokončení operace, pokud následně volat [aktualizace](#update) uložte provedené změny ve zdroji dat členské funkce.

> [!NOTE]
>  Pokud jste implementovali hromadné načítání řádků, nelze volat `Edit`. To způsobí neplatnost kontrolního výrazu. Přestože třída `CRecordset` neposkytuje mechanismus pro hromadnou aktualizaci řádků dat, můžete napsat vlastní funkce pomocí funkce ODBC API `SQLSetPos`. Další informace o hromadném načítání řádků naleznete v článku [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`Edit` uloží hodnoty datových členů sady záznamů. Při volání `Edit`, provést změny, potom zavolejte `Edit` znovu, budou obnoveny hodnoty záznamu tak byly před první `Edit` volání.

V některých případech můžete aktualizovat sloupec tak, že ji s hodnotou Null (obsahující žádná data). Chcete-li tak učinit, zavolejte [SetFieldNull](#setfieldnull) s parametrem hodnoty true označíte pole hodnotu Null; to taky způsobí, že sloupec, který se aktualizovat. Pokud chcete pole, které chcete zapsat do zdroje dat i v případě, že nedošlo ke změně jeho hodnoty, volejte [SetFieldDirty](#setfielddirty) s parametrem hodnotu TRUE. Tento postup funguje i v případě, že pole má hodnotu Null.

Pokud je zdroj dat podporuje transakce, lze provádět `Edit` volání součástí transakce. Všimněte si, že byste měli volat [CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) před voláním `Edit` a po otevření sady záznamů. Všimněte si také, že volání [CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) není náhradou za volání `Update` Dokončit `Edit` operace. Další informace o transakcích, naleznete v tématu třídy [CDatabase](../../mfc/reference/cdatabase-class.md).

V závislosti na aktuální režim uzamčení, může být uzamčena záznam aktualizuje `Edit` až do okamžiku volání `Update` nebo přejít na jiný záznam, nebo může být uzamčen pouze během `Edit` volání. Můžete změnit režim uzamčení s [SetLockingMode](#setlockingmode).

Obnovení předchozí hodnotu aktuální záznam, když se posunete na nový záznam před voláním `Update`. A `CDBException` je vyvolána, pokud zavoláte `Edit` pro sady záznamů, která se nedá aktualizovat nebo pokud neexistuje aktuální záznam.

Další informace najdete v článcích [transakce (ODBC)](../../data/odbc/transaction-odbc.md) a [sada záznamů: Zamykání záznamů (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#20](../../mfc/codesnippet/cpp/crecordset-class_4.cpp)]

##  <a name="flushresultset"></a>  CRecordset::FlushResultSet

Načte další sadu výsledků předdefinovaného dotazu (uložené procedury), pokud existuje více sad výsledků dotazu.

```
BOOL FlushResultSet();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud existuje více sad výsledků dotazu, který se má načíst; jinak 0.

### <a name="remarks"></a>Poznámky

Měli byste zavolat `FlushResultSet` pouze až budete hotoví zcela umístěte kurzor na aktuální sadu výsledků. Všimněte si, že po načtení Další výsledek, nastavte při volání `FlushResultSet`, kurzor není platný pro tuto sadu výsledků, měli byste zavolat [MoveNext](#movenext) členskou funkci po volání `FlushResultSet`.

Používá-li předdefinovaný dotaz výstupní parametr nebo vstupně výstupní parametry, musí volat `FlushResultSet` dokud vrátí `FALSE` (hodnota 0), aby bylo možné získat hodnoty těchto parametrů.

`FlushResultSet` volá funkci rozhraní API ODBC `SQLMoreResults`. Pokud `SQLMoreResults` vrátí SQL_ERROR nebo SQL_INVALID_HANDLE, pak `FlushResultSet` vyvolá výjimku. Další informace o `SQLMoreResults`, naleznete v sadě Windows SDK.

Uložená procedura musí mít pole vázaný, pokud chcete volat `FlushResultSet`.

### <a name="example"></a>Příklad

Následující kód předpokládá, že `COutParamRecordset` je `CRecordset`-odvozeného objektu na základě předdefinovaného dotazu s parametrem vstupní a výstupní parametr a s více sad výsledků dotazu. Poznámka: struktura [DoFieldExchange](#dofieldexchange) přepsat.

[!code-cpp[NVC_MFCDatabase#21](../../mfc/codesnippet/cpp/crecordset-class_5.cpp)]

[!code-cpp[NVC_MFCDatabase#22](../../mfc/codesnippet/cpp/crecordset-class_6.cpp)]

##  <a name="getbookmark"></a>  CRecordset::GetBookmark

Získá hodnotu záložky pro požadovaný aktuální záznam.

```
void GetBookmark(CDBVariant& varBookmark);
```

### <a name="parameters"></a>Parametry

*varBookmark*<br/>
Odkaz na [CDBVariant](../../mfc/reference/cdbvariant-class.md) objekt představující záložku na aktuální záznam.

### <a name="remarks"></a>Poznámky

Chcete-li zjistit, jestli jsou v sadě záznamů podporuje záložky, zavolejte [CanBookmark](#canbookmark). Pokud chcete zpřístupnit záložky Pokud jsou podporovány, je nutné nastavit `CRecordset::useBookmarks` možnost *dwOptions* parametr [otevřít](#open) členskou funkci.

> [!NOTE]
>  Pokud jsou záložky nepodporovaný nebo nedostupný, volání `GetBookmark` povede k vyvolání výjimky. Záložky nejsou podporované sady záznamů s posouváním pouze vpřed.

`GetBookmark` přiřadí hodnotu záložky aktuální záznam `CDBVariant` objektu. Chcete-li vrátit se k tomuto záznamu kdykoli po přechod na jiný záznam, zavolejte [SetBookmark](#setbookmark) s odpovídajícím `CDBVariant` objektu.

> [!NOTE]
>  Po určitých operacích sady záznamů záložky může už nebude platná. Například, pokud zavoláte `GetBookmark` následovaný `Requery`, nebudete moci vrátit k záznamu s `SetBookmark`. Volání [CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) ke kontrole, jestli může bezpečně volat `SetBookmark`.

Další informace o záložek a navigaci v sadě záznamů najdete v článcích [sada záznamů: Záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) a [sada záznamů: Posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

##  <a name="getdefaultconnect"></a>  CRecordset::GetDefaultConnect

Volá za účelem získání výchozí připojovací řetězec.

```
virtual CString GetDefaultConnect();
```

### <a name="return-value"></a>Návratová hodnota

A `CString` , která obsahuje výchozí připojovací řetězec.

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto funkci člena se získat výchozí připojovací řetězec pro zdroj dat, na kterých je založena sadu záznamů. ClassWizard implementuje tato funkce vám určením stejného zdroje dat, které používáte v nástroji ClassWizard k získání informací o tabulky a sloupce. Můžete se pravděpodobně bude výhodné přináší setrvávání u tohoto připojení výchozí při vývoji vaší aplikace. Ale výchozí připojení nemusí být vhodný pro uživatele vaší aplikace. Pokud je to tento případ, byste měli znovu implementovat tuto funkci, ClassWizard verze se zahodí. Další informace o připojovacích řetězcích najdete v článku [datové zdroje (ODBC)](../../data/odbc/data-source-odbc.md).

##  <a name="getdefaultsql"></a>  CRecordset::GetDefaultSQL

Volá za účelem získání výchozí řetězec SQL k provedení.

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>Návratová hodnota

A `CString` , která obsahuje výchozí příkaz SQL.

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto funkci člena se získat výchozí příkaz SQL, na kterých je založena sadu záznamů. Může to být název tabulky nebo SQL **vyberte** příkazu.

Nepřímo definovat výchozí příkaz SQL. tím, že deklarujete třídu sady záznamů s ClassWizard a ClassWizard tento úkol provede za vás.

Pokud potřebujete řetězec příkazu SQL pro vlastní použití, zavolejte `GetSQL`, který vrátí příkaz jazyka SQL, které jsou použity k výběru sady záznamů zaznamenává, když se otevřel. Můžete upravit výchozí řetězec SQL ve vaší třídě přepsání `GetDefaultSQL`. Například můžete zadat předdefinovaný dotaz pomocí volání **volání** příkazu. (Všimněte si, ale, že pokud upravíte `GetDefaultSQL`, budete také muset upravit `m_nFields` tak, aby odpovídaly počet sloupců ve zdroji dat.)

Další informace najdete v článku [sada záznamů: Deklarování třídy pro tabulku (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).

> [!CAUTION]
>  Název tabulky bude prázdný, pokud rozhraní neidentifikoval název tabulky, pokud byly zadány více názvy tabulek, nebo pokud **volání** příkaz se nepovedlo interpretovat. Všimněte si, že při použití **volání** příkazu nesmí vložen prázdný znak mezi složenou závorku a **volání** – klíčové slovo, ani vhodné vložit mezery před složenou závorku nebo před  **Vyberte** – klíčové slovo v **vyberte** příkazu.

##  <a name="getfieldvalue"></a>  CRecordset::GetFieldValue

Načte data tabulky v aktuální záznam.

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

*varValu*e A odkaz na [CDBVariant](../../mfc/reference/cdbvariant-class.md) objekt, který uloží hodnotu pole.

*nFieldType*<br/>
ODBC C datový typ pole. Použití výchozí hodnoty, DEFAULT_FIELD_TYPE, vynutí `GetFieldValue` určit typ C dat z datového typu SQL, na základě následující tabulky. V opačném případě můžete zadat data přímo zadejte nebo vyberte kompatibilní datový typ; Například můžete ukládat do SQL_C_CHAR libovolného datového typu.

|Datový typ jazyka C|Datový typ SQL.|
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

Další informace o typech dat rozhraní ODBC najdete v tématech "Datových typů SQL" a "C datové typy" v dodatku D sady Windows SDK.

*nIndex*<br/>
Index založený na nule v poli.

*strValue*<br/>
Odkaz na [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt, který uloží hodnotu pole převedeno na text, bez ohledu na datový typ pole.

### <a name="remarks"></a>Poznámky

Pole můžete vyhledávat podle názvu nebo podle indexu. Můžete uložit hodnotu pole buď `CDBVariant` objektu nebo `CString` objektu.

Pokud jste implementovali hromadné načítání řádků, je vždy aktuální záznam umístěn na první záznam v sadě řádků. Použití `GetFieldValue` záznamu v rámci dané sady řádků, je třeba nejprve zavolat [SetRowsetCursorPosition](#setrowsetcursorposition) členskou funkci, přesuňte kurzor na požadovaný řádek v rámci této sady řádků. Poté zavolejte `GetFieldValue` pro tento řádek. Implementovat hromadné načítání řádků, je nutné zadat `CRecordset::useMultiRowFetch` možnost *dwOptions* parametr [otevřít](#open) členskou funkci.

Můžete použít `GetFieldValue` se dynamicky načíst pole v době běhu místo staticky jejich vazbu v době návrhu. Například, pokud deklarujete objekt sady záznamů přímo z `CRecordset`, je nutné použít `GetFieldValue` k načtení pole dat; výměna pole záznamu (RFX) nebo hromadná výměna pole záznamu (Bulk RFX), není implementována.

> [!NOTE]
>  Pokud deklarujete objekt sady záznamů bez odvozený od `CRecordset`, není nutné načíst knihovna kurzorů rozhraní ODBC. Knihovna kurzorů rozhraní vyžaduje, aby sada záznamů měly alespoň jeden sloupec vázané; ale při použití `CRecordset` přímo, žádný sloupec je vázána. Členské funkce [CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) a [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) řídit, jestli se načtou knihovna kurzorů rozhraní.

`GetFieldValue` volá funkci rozhraní API ODBC `SQLGetData`. Pokud ovladač vypíše hodnotu SQL_NO_TOTAL skutečná délka hodnoty pole `GetFieldValue` vyvolá výjimku. Další informace o `SQLGetData`, naleznete v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující ukázkový kód ukazuje volání `GetFieldValue` pro objekt sady záznamů deklarované přímo z `CRecordset`.

[!code-cpp[NVC_MFCDatabase#23](../../mfc/codesnippet/cpp/crecordset-class_7.cpp)]

> [!NOTE]
>  Na rozdíl od třídy DAO `CDaoRecordset`, `CRecordset` nemá `SetFieldValue` členskou funkci. Pokud vytvoříte objekt přímo z `CRecordset`, je účinné jen pro čtení.

Další informace o hromadném načítání řádků naleznete v článku [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="getodbcfieldcount"></a>  CRecordset::GetODBCFieldCount

Načte celkový počet polí v objektu sady záznamů.

```
short GetODBCFieldCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet polí v sadě záznamů.

### <a name="remarks"></a>Poznámky

Další informace o vytváření sad záznamů naleznete v článku [sada záznamů: Vytváření a uzavírání sad záznamů (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).

##  <a name="getodbcfieldinfo"></a>  CRecordset::GetODBCFieldInfo

Získá informace o polích v sadě záznamů.

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

*fieldinfo*<br/>
Odkaz na `CODBCFieldInfo` struktury.

*nIndex*<br/>
Index založený na nule v poli.

### <a name="remarks"></a>Poznámky

Jednu verzi funkce umožňuje vyhledávání podle názvu pole. Jiné verze umožňuje vyhledat pole podle indexu.

Popis vrácené informace najdete v článku [codbcfieldinfo –](../../mfc/reference/codbcfieldinfo-structure.md) struktury.

Další informace o vytváření sad záznamů naleznete v článku [sada záznamů: Vytváření a uzavírání sad záznamů (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).

##  <a name="getrecordcount"></a>  CRecordset::GetRecordCount

Určuje velikost sady záznamů.

```
long GetRecordCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet záznamů v sadě záznamů; 0, pokud sada záznamů neobsahuje žádné záznamy; nebo -1, pokud nelze určit počet záznamů.

### <a name="remarks"></a>Poznámky

> [!CAUTION]
>  Počet záznamů je nakládat jako s "vysoké vody značku," nejvyšší číslované záznam zatím viděli, jak uživatel přesouvá mezi záznamy. Celkový počet záznamů je známé jenom po uživatele překročil poslední záznam. Z důvodů výkonu není aktualizován počet při volání `MoveLast`. Počet záznamů, volání `MoveNext` opakovaně, dokud není `IsEOF` vrátí nenulovou hodnotu. Přidání záznamu prostřednictvím `CRecordset:AddNew` a `Update` zvyšuje počet; odstranění záznamu prostřednictvím `CRecordset::Delete` snižuje počet.

##  <a name="getrowsetsize"></a>  CRecordset::GetRowsetSize

Získá aktuální nastavení pro počet řádků, které chcete načíst během daného načítání.

```
DWORD GetRowsetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet řádků pro načtení během daného načítání.

### <a name="remarks"></a>Poznámky

Pokud používáte hromadné načítání řádků, výchozí velikost řádků při otevření sady záznamů je 25; v opačném případě je 1.

Implementovat hromadné načítání řádků, je nutné zadat `CRecordset::useMultiRowFetch` možnost *dwOptions* parametr [otevřít](#open) členskou funkci. Chcete-li změnit nastavení pro velikost řádků, zavolejte [SetRowsetSize](#setrowsetsize).

Další informace o hromadném načítání řádků naleznete v článku [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="getrowsfetched"></a>  CRecordset::GetRowsFetched

Určuje, kolik záznamů se načetlo skutečně po fetch.

```
DWORD GetRowsFetched() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet řádků získané ze zdroje dat po daném načtení.

### <a name="remarks"></a>Poznámky

To je užitečné, pokud jste implementovali hromadné načítání řádků. Velikost řádků obvykle označuje, kolik řádků se načte z fetch; Celkový počet řádků v sadě záznamů však také ovlivní kolik řádků se načte v sadě řádků. Například pokud sady záznamů s nastavením velikost řádků 4 10 záznamů, potom opakování v sadě záznamů voláním `MoveNext` způsobí finální sada řádků s pouze 2 záznamy.

Implementovat hromadné načítání řádků, je nutné zadat `CRecordset::useMultiRowFetch` možnost *dwOptions* parametr [otevřít](#open) členskou funkci. Chcete-li určit velikost řádků, zavolejte [SetRowsetSize](#setrowsetsize).

Další informace o hromadném načítání řádků naleznete v článku [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#24](../../mfc/codesnippet/cpp/crecordset-class_8.cpp)]

##  <a name="getrowstatus"></a>  CRecordset::GetRowStatus

Získá stav pro řádek v aktuální sadě řádků.

```
WORD GetRowStatus(WORD wRow) const;
```

### <a name="parameters"></a>Parametry

*wRow*<br/>
Jedna pozice řádku v aktuální sadě řádků. Tato hodnota musí být v rozsahu 1 na velikost v sadě řádků.

### <a name="return-value"></a>Návratová hodnota

Hodnota stavu řádku. Podrobnosti najdete v tématu poznámky.

### <a name="remarks"></a>Poznámky

`GetRowStatus` Vrátí hodnotu, která označuje buď všechny změny ve stavu k řádku od posledního načíst ze zdroje dat, nebo že žádný řádek odpovídající *wRow* se načetla. Následující tabulka obsahuje seznam možných vrácených hodnot.

|Hodnota stavu|Popis|
|------------------|-----------------|
|SQL_ROW_SUCCESS|Řádek je beze změny.|
|SQL_ROW_UPDATED|Řádek byl aktualizován.|
|SQL_ROW_DELETED|Řádek byl odstraněn.|
|SQL_ROW_ADDED|Řádek byl přidán.|
|SQL_ROW_ERROR|Řádek je nelze získat z důvodu chyby.|
|SQL_ROW_NOROW|Neexistuje žádný řádek, který odpovídá *wRow*.|

Další informace najdete v tématu funkce ODBC API `SQLExtendedFetch` v sadě Windows SDK.

##  <a name="getstatus"></a>  CRecordset::GetStatus

Určuje index aktuálního záznamu v sadě záznamů a určuje, zda poslední záznam ukázala.

```
void GetStatus(CRecordsetStatus& rStatus) const;
```

### <a name="parameters"></a>Parametry

*rStatus*<br/>
Odkaz na `CRecordsetStatus` objektu. Další informace naleznete v části Poznámky.

### <a name="remarks"></a>Poznámky

`CRecordset` pokusí se sledovat indexu, ale za určitých okolností to nemusí být možné. Zobrazit [getrecordcount –](#getrecordcount) vysvětlení.

`CRecordsetStatus` Struktura má následující formát:

```cpp
struct CRecordsetStatus
{
    long m_lCurrentRecord;
    BOOL m_bRecordCountFinal;
};
```

Dva členové `CRecordsetStatus` mají následující význam:

- `m_lCurrentRecord` Pokud jsou známé, obsahuje index založený na nule aktuální záznam v sadě záznamů. Pokud nelze určit index, obsahuje tento člen AFX_CURRENT_RECORD_UNDEFINED-(2). Pokud `IsBOF` je TRUE (prázdná sada záznamů nebo pokus posunout před první záznam), pak `m_lCurrentRecord` je nastavena na AFX_CURRENT_RECORD_BOF (-1). Pokud na první záznam, pak je nastavena na hodnotu 0, druhý záznam 1 a tak dále.

- `m_bRecordCountFinal` Nenulové, pokud celkový počet záznamů v sadě záznamů bylo zjištěno. Obecně to musíte udělat cena začíná na začátku sady záznamů a volání `MoveNext` dokud `IsEOF` vrátí nenulovou hodnotu. Pokud tento člen je nula, záznam se počítají jako vrácené `GetRecordCount`, pokud není hodnota -1, je pouze "vysoká označuje jako horní mez" počet záznamů.

##  <a name="getsql"></a>  CRecordset::GetSQL

Voláním této členské funkce, chcete-li získat příkazu SQL, která byla použita k výběru záznamů sady záznamů, když se otevřel.

```
const CString& GetSQL() const;
```

### <a name="return-value"></a>Návratová hodnota

A **const** odkaz `CString` , která obsahuje příkaz jazyka SQL.

### <a name="remarks"></a>Poznámky

Obecně to bude SQL **vyberte** příkazu. Řetězec vrácený funkcí `GetSQL` je jen pro čtení.

Řetězec vrácený funkcí `GetSQL` se obvykle liší od libovolný řetězec, kterou jste předali do sady záznamů v *Ipszsql* parametr `Open` členskou funkci. Důvodem je, že sada záznamů sestavuje úplný příkaz SQL na předané na základě `Open`, zadaným ClassWizard, co jste zadali v `m_strFilter` a `m_strSort` datové členy a parametry můžou mít zadat. Podrobnosti o tom, jak sada záznamů sestavuje tento příkaz jazyka SQL, najdete v článku [sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).

> [!NOTE]
>  Voláním této členské funkce pouze po volání [otevřít](#open).

##  <a name="gettablename"></a>  CRecordset::GetTableName

Získá název tabulky SQL, na kterých je založena dotaz sady záznamů.

```
const CString& GetTableName() const;
```

### <a name="return-value"></a>Návratová hodnota

A **const** odkaz `CString` , který obsahuje tabulku, název, pokud je sada záznamů v tabulce na základě; v opačném případě prázdný řetězec.

### <a name="remarks"></a>Poznámky

`GetTableName` platí pouze pokud sada záznamů je na základě tabulky, nikoli připojení více tabulek nebo předdefinovaného dotazu (uložené procedury). Název je jen pro čtení.

> [!NOTE]
>  Voláním této členské funkce pouze po volání [otevřít](#open).

##  <a name="isbof"></a>  CRecordset::IsBOF

Vrátí nenulovou hodnotu, pokud sada záznamů obsahuje byl umístěn před první záznam. Neexistuje aktuální záznam.

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud sada záznamů obsahuje žádné záznamy nebo pokud jste přesunuli zpět před první záznam; jinak 0.

### <a name="remarks"></a>Poznámky

Voláním této členské funkce před přejít z záznam do záznamu zjistěte, zda jste došli před první záznam sady záznamů. Můžete také použít `IsBOF` spolu s `IsEOF` k určení, zda sada záznamů obsahuje záznamy, nebo je prázdný. Ihned poté, co zavoláte `Open`, pokud sada záznamů neobsahuje žádné záznamy `IsBOF` vrátí nenulovou hodnotu. Při otevření sady záznamů, který má alespoň jeden záznam, první záznam je aktuální záznam a `IsBOF` vrátí hodnotu 0.

Pokud je první záznam aktuální záznam a zavoláte `MovePrev`, `IsBOF` následně vrátí nenulovou hodnotu. Pokud `IsBOF` vrátí nenulovou hodnotu a můžete volat `MovePrev`, dojde k chybě. Pokud `IsBOF` vrátí nenulovou hodnotu, je definován aktuální záznam a žádné akce, které aktuální záznam způsobí chybu.

### <a name="example"></a>Příklad

Tento příklad používá `IsBOF` a `IsEOF` ke zjištění omezení sady záznamů, jak kód procházení záznamů v obou směrech.

[!code-cpp[NVC_MFCDatabase#25](../../mfc/codesnippet/cpp/crecordset-class_9.cpp)]

##  <a name="isdeleted"></a>  CRecordset::IsDeleted

Určuje, zda aktuální záznam byl odstraněn.

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud sada záznamů je umístěn na odstraněný záznam; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud se posunete na záznam a `IsDeleted` vrátí hodnotu TRUE (nenulový), pak musí přejít k jinému záznamu před provedením jakékoli další operace, sada záznamů.

Výsledek `IsDeleted` závislá na mnoha faktorech, jako je například váš typ sady záznamů, zda sady záznamů je aktualizovat, zda jste zadali `CRecordset::skipDeletedRecords` možnost při otevření sady záznamů, zda vaše balíčky ovladačů, odstranit záznamy a, zda existují více uživatelů.

Další informace o `CRecordset::skipDeletedRecords` a ovladač balení, najdete v článku [otevřít](#open) členskou funkci.

> [!NOTE]
>  Pokud jste implementovali hromadné načítání řádků, neměli by jste volat `IsDeleted`. Namísto toho zavolejte metodu [GetRowStatus](#getrowstatus) členskou funkci. Další informace o hromadném načítání řádků naleznete v článku [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="iseof"></a>  CRecordset::IsEOF

Vrátí nenulovou hodnotu, pokud sada záznamů zařadila po posledním záznamu. Neexistuje aktuální záznam.

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud sada záznamů obsahuje žádné záznamy nebo pokud jste přešli za poslední záznam; jinak 0.

### <a name="remarks"></a>Poznámky

Voláním této členské funkce při posunutí ze záznamu záznamu Další informace, jestli jste došli za poslední záznam sady záznamů. Můžete také použít `IsEOF` k určení, zda sada záznamů obsahuje záznamy, nebo je prázdný. Ihned poté, co zavoláte `Open`, pokud sada záznamů neobsahuje žádné záznamy `IsEOF` vrátí nenulovou hodnotu. Při otevření sady záznamů, který má alespoň jeden záznam, první záznam je aktuální záznam a `IsEOF` vrátí hodnotu 0.

Pokud je poslední záznam aktuální záznam při volání `MoveNext`, `IsEOF` následně vrátí nenulovou hodnotu. Pokud `IsEOF` vrátí nenulovou hodnotu a můžete volat `MoveNext`, dojde k chybě. Pokud `IsEOF` vrátí nenulovou hodnotu, je definován aktuální záznam a žádné akce, které aktuální záznam způsobí chybu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [IsBOF](#isbof).

##  <a name="isfielddirty"></a>  CRecordset::IsFieldDirty

Určuje, zda zadaná pole datového člena se změnil od [upravit](#edit) nebo [AddNew](#addnew) byla volána.

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>Parametry

*pv*<br/>
Ukazatel na pole datového člena, jehož stav chcete zkontrolovat nebo NULL, pokud chcete zjistit, zda jsou změny libovolné pole.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud zadané pole datového člena se změnil od volání `AddNew` nebo `Edit`; jinak 0.

### <a name="remarks"></a>Poznámky

Data ve všech datových členů nečistých polí se přesunou do záznamu ve zdroji dat. Pokud aktuální záznam se aktualizuje pomocí volání [aktualizace](#update) členskou funkci `CRecordset` (po volání `Edit` nebo `AddNew`).

> [!NOTE]
>  Tato členská funkce se nevztahuje na sady záznamů, které jsou pomocí hromadné načítání řádků. Pokud jste implementovali hromadné načítání řádků, pak `IsFieldDirty` vždy vrátí hodnotu FALSE a způsobí neplatnost kontrolního výrazu. Další informace o hromadném načítání řádků naleznete v článku [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Volání `IsFieldDirty` resetuje účinky předchozích volání [SetFieldDirty](#setfielddirty) vzhledem k tomu, že se znovu zhodnotí změny stavu pole. V `AddNew` případu, pokud aktuální hodnota pole se liší od hodnoty null pseudo pole je nastaven stav dirty. V `Edit` malá a velká, pokud hodnota pole se liší od hodnotu uloženou v mezipaměti, pak je pole Stav dirty.

`IsFieldDirty` se implementuje pomocí [DoFieldExchange](#dofieldexchange).

Další informace o příznak změny, najdete v článku [sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).

##  <a name="isfieldnull"></a>  CRecordset::IsFieldNull

Vrátí nenulovou hodnotu, pokud zadané pole v záznamu o aktuální hodnotu Null (neobsahuje hodnotu).

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>Parametry

*pv*<br/>
Ukazatel na pole datového člena, jehož stav chcete zkontrolovat nebo NULL, pokud chcete zjistit, zda libovolné pole jsou Null.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud zadané pole datového člena je označený jako hodnota Null. jinak 0.

### <a name="remarks"></a>Poznámky

Voláním této členské funkce k určení, zda zadaná pole datového člena sady záznamů byl označen jako hodnota Null. (V terminologii databáze s hodnotou Null znamená "mít žádná hodnota" a není stejná jako hodnota NULL v jazyce C++.) Pokud pole datového člena je označený jako hodnota Null, je interpretován jako sloupec aktuální záznam, pro kterou neexistuje žádná hodnota.

> [!NOTE]
>  Tato členská funkce se nevztahuje na sady záznamů, které jsou pomocí hromadné načítání řádků. Pokud jste implementovali hromadné načítání řádků, pak `IsFieldNull` vždy vrátí hodnotu FALSE a způsobí neplatnost kontrolního výrazu. Další informace o hromadném načítání řádků naleznete v článku [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

`IsFieldNull` se implementuje pomocí [DoFieldExchange](#dofieldexchange).

##  <a name="isfieldnullable"></a>  CRecordset::IsFieldNullable

Vrátí nenulovou hodnotu, pokud zadané pole v aktuální záznam lze nastavit na hodnotu Null (s žádná hodnota).

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>Parametry

*pv*<br/>
Ukazatel na pole datového člena, jehož stav chcete zkontrolovat nebo NULL, pokud chcete určit, pokud libovolné pole lze nastavit na hodnotu Null.

### <a name="remarks"></a>Poznámky

Voláním této členské funkce určuje, jestli je zadané pole datového člena "null" (může být nastavena na hodnotu Null; C++ NULL není stejná jako hodnota Null, tzn., v, řečeno terminologií databáze, "s žádnou hodnotu").

> [!NOTE]
>  Pokud jste implementovali hromadné načítání řádků, nelze volat `IsFieldNullable`. Namísto toho zavolejte metodu [GetODBCFieldInfo](#getodbcfieldinfo) členskou funkci k určení, zda pole lze nastavit na hodnotu Null. Všimněte si, že vždy můžete volat `GetODBCFieldInfo`, bez ohledu na to, zda jste implementovali hromadné načítání řádků. Další informace o hromadném načítání řádků naleznete v článku [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Pole, které nemůže mít hodnotu Null musí mít hodnotu. Pokud se pokusíte nastavit toto pole na hodnotu Null při přidávání nebo aktualizaci záznamu, odmítne zdroj dat je přidání nebo aktualizace, a [aktualizovat](#update) vyvolá výjimku. Vyvolá se výjimka při volání `Update`, ne v případě, že zavoláte [SetFieldNull](#setfieldnull).

Použití NULL pro první argument funkce se vztahují pouze k funkci `outputColumn` pole, nikoli `param` pole. Například volání

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

Nastaví pouze `outputColumn` pole na hodnotu NULL; `param` pole zůstanou beze změn.

Pro práci na `param` pole, je nutné zadat skutečnou adresu jednotlivých `param` chcete pracovat, jako například:

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

To znamená, že nemůžete nastavit všechny `param` pole na hodnotu NULL, jako u `outputColumn` pole.

`IsFieldNullable` se implementuje pomocí [DoFieldExchange](#dofieldexchange).

##  <a name="isopen"></a>  CRecordset::IsOpen

Určuje, zda sada záznamů je už otevřené.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulovou hodnotu, pokud objekt sady záznamů [otevřít](#open) nebo [Requery](#requery) dříve byla volána členská funkce a sady záznamů nebyla uzavřena; jinak 0.

##  <a name="m_hstmt"></a>  CRecordset::m_hstmt

Obsahuje popisovač ODBC příkaz datová struktura typu HSTMT, přidružené k sadě záznamů.

### <a name="remarks"></a>Poznámky

Každý dotaz do zdroje dat ODBC je přidružený HSTMT.

> [!CAUTION]
>  Nepoužívejte `m_hstmt` před [otevřít](#open) byla volána.

Obvykle není potřeba přímý přístup HSTMT, ale můžete potřebovat pro přímé spouštění příkazů jazyka SQL. `ExecuteSQL` Členské funkce třídy `CDatabase` poskytuje příklad použití `m_hstmt`.

##  <a name="m_nfields"></a>  CRecordset::m_nFields

Obsahuje číslo pole datových členů ve třídě sady záznamů; To znamená, počet vybraných sadou záznamů ze zdroje dat sloupců.

### <a name="remarks"></a>Poznámky

Konstruktor pro třídu sady záznamů musí inicializovat `m_nFields` správné číslo. Pokud jste neimplementovali hromadné načítání řádků, ClassWizard zapíše tuto inicializaci za vás, když ji použijete k deklaraci vaší třídy sady záznamů. Můžete je zapsat také ručně.

Rozhraní používá ke správě interakcí mezi datové členy polí a odpovídající sloupce aktuální záznam ve zdroji dat. Toto číslo.

> [!CAUTION]
>  Toto číslo musí odpovídat počtu "výstupní sloupce" zaregistrovaný v `DoFieldExchange` nebo `DoBulkFieldExchange` po volání [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) s parametrem `CFieldExchange::outputColumn`.

Sloupce můžete svázat dynamicky, jak je popsáno v článku "Sada záznamů: Dynamické vazby datových sloupců." Pokud tak učiníte, musíte zvýšit počet v `m_nFields` tak, aby odrážely počet funkcí RFX nebo Bulk RFX volání vaší `DoFieldExchange` nebo `DoBulkFieldExchange` členskou funkci pro dynamické vazby sloupců.

Další informace najdete v článcích [sada záznamů: Dynamické vazby datových sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) a [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Příklad

Přečtěte si článek [výměna polí záznamu: Použití funkce RFX](../../data/odbc/record-field-exchange-using-rfx.md).

##  <a name="m_nparams"></a>  CRecordset::m_nParams

Obsahuje číslo parametru datové členy třídy sady záznamů; To znamená předaný počet parametrů pomocí dotazu sadu záznamů.

### <a name="remarks"></a>Poznámky

Pokud vaše sada záznamů třída nemá žádné parametry datových členů, konstruktor pro třídu musí inicializovat `m_nParams` správné číslo. Hodnota `m_nParams` výchozí hodnota je 0. Pokud chcete přidat parametry datových členů (které musíte udělat ručně) je třeba také ručně přidat inicializace v konstruktoru třídy tak, aby odrážely počet parametrů (který musí být přinejmenším stejně velká jako počet "zástupné symboly ve vaší `m_strFilter` nebo `m_strSort`řetězec).

Rozhraní používá toto číslo při parametrizuje dotaz sady záznamů.

> [!CAUTION]
>  Tato hodnota musí odpovídat jako počet "parametrů" zaregistrované v `DoFieldExchange` nebo `DoBulkFieldExchange` po volání [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) s hodnotou parametru `CFieldExchange::inputParam`, `CFieldExchange::param`, `CFieldExchange::outputParam`, nebo `CFieldExchange::inoutParam`.

### <a name="example"></a>Příklad

  Přečtěte si články [sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) a [výměna polí záznamu: Použití funkce RFX](../../data/odbc/record-field-exchange-using-rfx.md).

##  <a name="m_pdatabase"></a>  CRecordset::m_pDatabase

Obsahuje ukazatel `CDatabase` objekt, jehož prostřednictvím sady záznamů je připojený ke zdroji dat.

### <a name="remarks"></a>Poznámky

Tato proměnná je nastavená dvěma způsoby. Obvykle předat ukazatel k již připojené `CDatabase` objektu při vytvoření objektu sady záznamů. Pokud místo toho předáte NULL `CRecordset` vytvoří `CDatabase` objekt za vás a připojí ji. V obou případech `CRecordset` ukládá ukazatel v této proměnné.

Obvykle nebudete muset přímo pomocí ukazatele uložené v `m_pDatabase`. Pokud Tvorba vlastních rozšíření pro `CRecordset`, ale budete muset použít ukazatele. Například můžete potřebovat ukazatel pokud vyvoláte vlastní `CDBException`s. Nebo může být nutné, pokud je potřeba udělat něco pomocí stejných `CDatabase` objektu, například spuštění transakce, vypršení časového limitu pro nastavení, nebo volání `ExecuteSQL` členské funkce třídy `CDatabase` k provedení příkazů SQL přímo.

##  <a name="m_strfilter"></a>  CRecordset::m_strFilter

Po vytvoření objektu sady záznamů, ale před voláním jeho `Open` členské funkce, použijte tento datový člen k ukládání `CString` obsahující SQL **kde** klauzuli.

### <a name="remarks"></a>Poznámky

Sada záznamů tento řetězec používá k omezení (nebo filtr) vybere během záznamy `Open` nebo `Requery` volání. To je užitečné pro výběr dílčí sady záznamů, například "všechny prodejců v Kalifornii" ("stav = CA"). Syntaxe ODBC SQL **kde** je klauzule

`WHERE search-condition`

Všimněte si, že nejsou zahrnuté **kde** – klíčové slovo do řetězce. Architektura dodává ho.

Můžete také parametrizovat řetězec vašeho filtru tak, že "zástupné symboly v něm deklarace parametru datový člen ve své třídě pro každý zástupný znak a předání parametrů do sady záznamů v době spuštění. Tímto způsobem můžete vytvořit filtr v době běhu. Další informace najdete v článku [sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

Další informace o SQL **kde** klauzule, najdete v článku [SQL](../../data/odbc/sql.md). Další informace o výběr a filtrování záznamů najdete v článku [sada záznamů: Filtrování záznamů (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#30](../../mfc/codesnippet/cpp/crecordset-class_12.cpp)]

##  <a name="m_strsort"></a>  CRecordset::m_strSort

Po vytvoření objektu sady záznamů, ale před voláním jeho `Open` členské funkce, použijte tento datový člen k ukládání `CString` obsahující SQL **klauzule ORDER BY** klauzuli.

### <a name="remarks"></a>Poznámky

Sada záznamů tento řetězec používá k řazení záznamů vybere během `Open` nebo `Requery` volání. Tato funkce slouží k řazení sady záznamů na jeden nebo více sloupců. Syntaxe ODBC SQL **klauzule ORDER BY** je klauzule

`ORDER BY sort-specification [, sort-specification]...`

Pokud specifikace řazení je celé číslo nebo název sloupce. Vzestupné nebo sestupné pořadí (ve výchozím nastavení je vzestupném pořadí) můžete také zadat připojením "ASC" nebo "DESC" do seznamu sloupců v řetězci řazení. Vybrané položky jsou seřazeny nejprve podle prvního sloupce uvedené, potom podle druhého a tak dále. Například můžete objednat sady záznamů "Zákazníci" podle příjmení, pak křestní jméno. Počet sloupců, které můžete vytvořit seznam závisí na zdroji dat. Další informace najdete v tématu Windows SDK.

Všimněte si, že nejsou zahrnuté **klauzule ORDER BY** – klíčové slovo do řetězce. Architektura dodává ho.

Další informace o klauzulích SQL, najdete v článku [SQL](../../data/odbc/sql.md). Další informace o řazení záznamů, najdete v článku [sada záznamů: Řazení záznamů (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#31](../../mfc/codesnippet/cpp/crecordset-class_13.cpp)]

##  <a name="move"></a>  CRecordset::Move

Přesune ukazatel aktuální záznam v rámci sady záznamů, dopředu nebo dozadu.

```
virtual void Move(
    long nRows,
    WORD wFetchType = SQL_FETCH_RELATIVE);
```

### <a name="parameters"></a>Parametry

*nRows*<br/>
Počet řádků pro přesun vpřed nebo vzad. Kladné hodnoty pokračovat dál a na konci sady záznamů. Záporné hodnoty zpět, přesuňte směrem k začátku.

*wFetchType*<br/>
Určuje sadu řádků, které `Move` načte. Podrobnosti najdete v tématu poznámky.

### <a name="remarks"></a>Poznámky

Pokud předáte hodnotu 0 pro *nRows*, `Move` aktualizuje aktuální záznam; `Move` se ukončí všechny aktuální `AddNew` nebo `Edit` režimu a obnoví aktuální záznam hodnotu před `AddNew` nebo `Edit` byla volána.

> [!NOTE]
>  Když přesunete prostřednictvím sady záznamů, nelze přeskočit odstraněné záznamy. Zobrazit [CRecordset::IsDeleted](#isdeleted) Další informace. Při otevření `CRecordset` s `skipDeletedRecords` sada, možností `Move` vyhodnotí, pokud *nRows* parametru je 0. Toto chování zabrání aktualizaci řádků, které se odstraní v jiné klientské aplikace používají stejná data. Najdete v článku *dwOption* parametr [otevřít](#open) popis `skipDeletedRecords`.

`Move` přemístí sadu záznamů pomocí sad řádků. Na základě hodnot pro *nRows* a *wFetchType*, `Move` načte odpovídající sadu řádků a potom provede první záznam v této sadě řádků %{Rowset/ aktuální záznam. Pokud jste neimplementovali hromadné načítání řádků, velikost řádků je vždy 1. Při načítání sady řádků `Move` přímo volá [CheckRowsetError](#checkrowseterror) členskou funkci pro zpracování chyb, které jsou výsledkem načítání.

V závislosti na hodnoty předané `Move` je ekvivalentní k navzájem `CRecordset` členské funkce. Konkrétně hodnota *wFetchType* může znamenat členská funkce, která je mnohem intuitivnější a často upřednostňovanou metodou pro přesun aktuální záznam.

V následující tabulce jsou uvedeny možné hodnoty pro *wFetchType*, v sadě řádků, které `Move` načte podle *wFetchType* a *nRows*a jakýkoli ekvivalent Členské funkce odpovídající *wFetchType*.

|wFetchType|Počet získaných řádků|Ekvivalentní členská funkce|
|----------------|--------------------|--------------------------------|
|SQL_FETCH_RELATIVE (výchozí hodnota)|Sada řádků počáteční *nRows* řádky z prvního řádku v aktuální sadě řádků.||
|SQL_FETCH_NEXT|Další sady řádků; *nRows* se ignoruje.|[MoveNext](#movenext)|
|SQL_FETCH_PRIOR|V předchozí sadě řádků; *nRows* se ignoruje.|[MovePrev](#moveprev)|
|SQL_FETCH_FIRST|První sadu řádků v sadě záznamů; *nRows* se ignoruje.|[MoveFirst](#movefirst)|
|SQL_FETCH_LAST|Poslední úplné sady řádků v sadě záznamů; *nRows* se ignoruje.|[MoveLast](#movelast)|
|SQL_FETCH_ABSOLUTE|Pokud *nRows* > 0, v sadě řádků od *nRows* řádky od začátku sady záznamů. Pokud *nRows* < 0, v sadě řádků od *nRows* řádky z konce sady záznamů. Pokud *nRows* = 0, je vrácena podmínku začátku souboru (BOF).|[SetAbsolutePosition](#setabsoluteposition)|
|SQL_FETCH_BOOKMARK|V sadě řádků počínaje řádkem, jehož hodnota Záložka odpovídá *nRows*.|[SetBookmark](#setbookmark)|

> [!NOTE]
>  Pro posouváním pouze vpřed `Move` je platný pouze s hodnotou SQL_FETCH_NEXT pro *wFetchType*.

> [!CAUTION]
>  Volání `Move` vyvolá výjimku, pokud sada záznamů neobsahuje žádné záznamy. Chcete-li zjistit, zda sada záznamů obsahuje záznamy, které, zavolejte [IsBOF](#isbof) a [IsEOF](#iseof).

> [!NOTE]
>  Pokud jste přešli po začátku nebo konci sady záznamů (`IsBOF` nebo `IsEOF` vrátí nenulovou hodnotu), volání `Move` pravděpodobně vyvolá funkce `CDBException`. Například pokud `IsEOF` vrátí nenulovou hodnotu a `IsBOF` nemá, pak `MoveNext` vyvolá výjimku, ale `MovePrev` se tak nestane.

> [!NOTE]
>  Při volání `Move` při aktuální záznam aktualizovány nebo přidány, aktualizace bude ztracen bez předchozího upozornění.

Další informace o navigaci v sadě záznamů najdete v článcích [sada záznamů: Posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) a [sada záznamů: Záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Další informace o hromadném načítání řádků naleznete v článku [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Související informace najdete v části funkce ODBC API `SQLExtendedFetch` v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#28](../../mfc/codesnippet/cpp/crecordset-class_14.cpp)]

##  <a name="movefirst"></a>  CRecordset::MoveFirst

Díky první záznam v první sadě řádků %{Rowset/ aktuální záznam.

```
void MoveFirst();
```

### <a name="remarks"></a>Poznámky

Bez ohledu na to, zda hromadné načítání řádků implementován bude vždy první záznam v sadě záznamů.

Není nutné volat `MoveFirst` ihned po otevření sady záznamů. V tu chvíli první záznam (pokud existuje) je automaticky aktuální záznam.

> [!NOTE]
>  Tato členská funkce není platná pro dopředné sady záznamů.

> [!NOTE]
>  Když přesunete prostřednictvím sady záznamů, nelze přeskočit odstraněné záznamy. Zobrazit [IsDeleted](#isdeleted) členskou funkci podrobnosti.

> [!CAUTION]
>  Některé z volání `Move` funkce vyvolá výjimku, pokud sada záznamů neobsahuje žádné záznamy. Chcete-li zjistit, zda sada záznamů obsahuje záznamy, které, zavolejte `IsBOF` a `IsEOF`.

> [!NOTE]
>  Pokud některý z volání `Move` funkce při aktuální záznam aktualizovány nebo přidány, aktualizace bude ztracen bez předchozího upozornění.

Další informace o navigaci v sadě záznamů najdete v článcích [sada záznamů: Posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) a [sada záznamů: Záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Další informace o hromadném načítání řádků naleznete v článku [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [IsBOF](#isbof).

##  <a name="movelast"></a>  CRecordset::MoveLast

Díky první záznam v poslední úplné sadě řádků %{Rowset/ aktuální záznam.

```
void MoveLast();
```

### <a name="remarks"></a>Poznámky

Pokud jste neimplementovali hromadné načítání řádků, sady záznamů řádků velikost je 1, takže `MoveLast` jednoduše přejde na poslední záznam v sadě záznamů.

> [!NOTE]
>  Tato členská funkce není platná pro dopředné sady záznamů.

> [!NOTE]
>  Když přesunete prostřednictvím sady záznamů, nelze přeskočit odstraněné záznamy. Zobrazit [IsDeleted](#isdeleted) členskou funkci podrobnosti.

> [!CAUTION]
>  Některé z volání `Move` funkce vyvolá výjimku, pokud sada záznamů neobsahuje žádné záznamy. Chcete-li zjistit, zda sada záznamů obsahuje záznamy, které, zavolejte `IsBOF` a `IsEOF`.

> [!NOTE]
>  Pokud některý z volání `Move` funkce při aktuální záznam aktualizovány nebo přidány, aktualizace bude ztracen bez předchozího upozornění.

Další informace o navigaci v sadě záznamů najdete v článcích [sada záznamů: Posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) a [sada záznamů: Záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Další informace o hromadném načítání řádků naleznete v článku [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [IsBOF](#isbof).

##  <a name="movenext"></a>  CRecordset::MoveNext

Díky první záznam v dalším řádků aktuální záznam.

```
void MoveNext();
```

### <a name="remarks"></a>Poznámky

Pokud jste neimplementovali hromadné načítání řádků, sady záznamů řádků velikost je 1, takže `MoveNext` jednoduše přejde na další záznam.

> [!NOTE]
>  Když přesunete prostřednictvím sady záznamů, nelze přeskočit odstraněné záznamy. Zobrazit [IsDeleted](#isdeleted) členskou funkci podrobnosti.

> [!CAUTION]
>  Některé z volání `Move` funkce vyvolá výjimku, pokud sada záznamů neobsahuje žádné záznamy. Chcete-li zjistit, zda sada záznamů obsahuje záznamy, které, zavolejte `IsBOF` a `IsEOF`.

> [!NOTE]
>  Doporučuje se také, že zavoláte `IsEOF` před voláním `MoveNext`. Pokud jste přešli za koncem záznamů, například `IsEOF` vrátí nenulovou hodnotu; následných volání `MoveNext` by vyvolat výjimku.

> [!NOTE]
>  Pokud některý z volání `Move` funkce při aktuální záznam aktualizovány nebo přidány, aktualizace bude ztracen bez předchozího upozornění.

Další informace o navigaci v sadě záznamů najdete v článcích [sada záznamů: Posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) a [sada záznamů: Záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Další informace o hromadném načítání řádků naleznete v článku [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [IsBOF](#isbof).

##  <a name="moveprev"></a>  CRecordset::MovePrev

Díky první záznam v předchozí sadě řádků %{Rowset/ aktuální záznam.

```
void MovePrev();
```

### <a name="remarks"></a>Poznámky

Pokud jste neimplementovali hromadné načítání řádků, sady záznamů řádků velikost je 1, takže `MovePrev` jednoduše přejde na předchozí záznam.

> [!NOTE]
>  Tato členská funkce není platná pro dopředné sady záznamů.

> [!NOTE]
>  Když přesunete prostřednictvím sady záznamů, nelze přeskočit odstraněné záznamy. Zobrazit [IsDeleted](#isdeleted) členskou funkci podrobnosti.

> [!CAUTION]
>  Některé z volání `Move` funkce vyvolá výjimku, pokud sada záznamů neobsahuje žádné záznamy. Chcete-li zjistit, zda sada záznamů obsahuje záznamy, které, zavolejte `IsBOF` a `IsEOF`.

> [!NOTE]
>  Doporučuje se také, že zavoláte `IsBOF` před voláním `MovePrev`. Pokud jste přešli náskok před začátkem záznamů, například `IsBOF` vrátí nenulovou hodnotu; následných volání `MovePrev` by vyvolat výjimku.

> [!NOTE]
>  Pokud některý z volání `Move` funkce při aktuální záznam aktualizovány nebo přidány, aktualizace bude ztracen bez předchozího upozornění.

Další informace o navigaci v sadě záznamů najdete v článcích [sada záznamů: Posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) a [sada záznamů: Záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Další informace o hromadném načítání řádků naleznete v článku [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [IsBOF](#isbof).

##  <a name="onsetoptions"></a>  CRecordset::OnSetOptions

Volá se, aby nastavení možností (používá se na výběr) pro zadaný příkaz ODBC.

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Parametry

*hstmt*<br/>
HSTMT ODBC příkaz, jehož možnosti mají být nastaveny.

### <a name="remarks"></a>Poznámky

Volání `OnSetOptions` nastavení možností (používá se na výběr) pro zadaný příkaz ODBC. Rozhraní volá tuto funkci člena nastavit výchozí možnosti pro sady záznamů. `OnSetOptions` Určuje zdroj dat podporu pro posuvný kurzory a souběžnosti kurzoru a příslušným způsobem nastaví možnosti sady záznamů. (Zatímco `OnSetOptions` se používá pro výběr operace, `OnSetUpdateOptions` se používá pro operace update.)

Přepsat `OnSetOptions` nastavení možností konkrétní ke zdroji dat nebo ovladač. Například pokud zdroj dat podporuje otevírání pro výhradní přístup, může být přepíšete `OnSetOptions` využít tuto možnost.

Další informace o kurzory, najdete v článku [ODBC](../../data/odbc/odbc-basics.md).

##  <a name="onsetupdateoptions"></a>  CRecordset::OnSetUpdateOptions

Volá se, aby nastavení možností (používá se při aktualizaci) pro zadaný příkaz ODBC.

```
virtual void OnSetUpdateOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Parametry

*hstmt*<br/>
HSTMT ODBC příkaz, jehož možnosti mají být nastaveny.

### <a name="remarks"></a>Poznámky

Volání `OnSetUpdateOptions` nastavení možností (používá se při aktualizaci) pro zadaný příkaz ODBC. Rozhraní volá tuto funkci člena po vytvoření HSTMT k aktualizaci záznamů v sadě záznamů. (Zatímco `OnSetOptions` se používá pro výběr operace, `OnSetUpdateOptions` se používá pro operace update.) `OnSetUpdateOptions` Určuje zdroj dat podporu pro posuvný kurzory a souběžnosti kurzoru a příslušným způsobem nastaví možnosti sady záznamů.

Přepsat `OnSetUpdateOptions` nastavení možností příkazu ODBC před, který tento příkaz slouží k přístupu k databázi.

Další informace o kurzory, najdete v článku [ODBC](../../data/odbc/odbc-basics.md).

##  <a name="open"></a>  CRecordset::Open

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

- `CRecordset::dynaset` Sada záznamů s obousměrným posouváním. Členství a pořadí záznamů je určeno při otevření sady záznamů, ale změny datových hodnot provedené ostatními uživateli jsou viditelné až po operaci načtení. Dynamické sady jsou známy také jako sady záznamů řízené sadou klíčů.

- `CRecordset::snapshot` Statická sada záznamů s obousměrným posouváním. Členství a pořadí záznamů je určeno při otevření sady záznamů. Datové hodnoty jsou určeny při načtení záznamů. Změny provedené ostatními uživateli nejsou viditelné, dokud není sada záznamů zavřena a znovu otevřena.

- `CRecordset::dynamic` Sada záznamů s obousměrným posouváním. Změny členství, pořadí a datových hodnot provedené jinými uživateli jsou viditelné po operaci načtení. Povšimněte si, že mnoho ovladačů ODBC nepodporuje tento typ sady záznamů.

- `CRecordset::forwardOnly` Jen pro čtení záznamů s posouváním pouze vpřed.

   Pro `CRecordset`, výchozí hodnota je `CRecordset::snapshot`. Mechanismus výchozích hodnot umožňuje interakci průvodců aplikace Visual C++ s třídou `CRecordset` pro rozhraní ODBC i třídou `CDaoRecordset` pro rozhraní DAO, které používají různé výchozí hodnoty.

Další informace o těchto typech sad záznamů naleznete v článku [sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md). Související informace najdete v článku "Použití bloku a posuvný kurzorů" v sadě Windows SDK.

> [!CAUTION]
>  Není-li požadovaný typ podporován, rozhraní vyvolá výjimku.

*lpszSQL*<br/>
Ukazatel řetězce obsahující jedno z následujících:

- Ukazatel s hodnotou NULL.

- Název tabulky.

- SQL **vyberte** – příkaz (volitelně spolu s SQL **kde** nebo **klauzule ORDER BY** klauzule).

- A **volání** příkaz a zadejte název předdefinovaného dotazu (uložené procedury). Buďte opatrní, nevkládejte prázdný znak mezi složenou závorku a **volání** – klíčové slovo.

Další informace o tomto řetězci naleznete v tabulce a v diskuzi o účelu nástroje ClassWizard v části Poznámky.

> [!NOTE]
>  Pořadí sloupců v sadě výsledků musí odpovídat pořadí funkcí RFX nebo Bulk RFX funkce volá ve vaší [DoFieldExchange](#dofieldexchange) nebo [DoBulkFieldExchange](#dobulkfieldexchange) přepisu funkce.

*dwOptions*<br/>
Bitová maska schopná určit kombinaci hodnot uvedených níže. Některé se vzájemně vylučují. Výchozí hodnota je **žádný**.

- `CRecordset::none` Nezvolit žádné možnosti. Tato hodnota parametru se vzájemně vylučuje se všemi ostatními hodnotami. Ve výchozím nastavení, je možné aktualizovat sady záznamů s [upravit](#edit) nebo [odstranit](#delete) umožňuje přidávání nových záznamů pomocí [AddNew](#addnew). Možnosti aktualizace závisí na zdroji dat stejně jako na *nOpenType* zadané možnosti. Optimalizace pro hromadná přidávání nejsou dostupné. Hromadné načítání řádků nebude implementováno. Odstraněné záznamy nebudou při navigaci v sadě záznamů přeskočeny. Záložky nejsou k dispozici. Automatická kontrola nečistých polí je implementována.

- `CRecordset::appendOnly` Nepovolit `Edit` nebo `Delete` v sadě záznamů. Povolit pouze funkci `AddNew`. Tato možnost se vzájemně vylučuje s možností `CRecordset::readOnly`.

- `CRecordset::readOnly` Otevřete sadu záznamů jen pro čtení. Tato možnost se vzájemně vylučuje s možností `CRecordset::appendOnly`.

- `CRecordset::optimizeBulkAdd` Optimalizovat přidání mnoha záznamů najednou pomocí připraveného příkazu jazyka SQL. Platí jenom v případě, že nepoužíváte funkci rozhraní API ODBC `SQLSetPos` sada záznamů. První aktualizace určuje, která pole jsou označena za nečistá. Tato možnost se vzájemně vylučuje s možností `CRecordset::useMultiRowFetch`.

- `CRecordset::useMultiRowFetch` Implementujte hromadné načítání řádků a umožnit více řádků, které se mají načíst v jediné operace načtení. Jde o pokročilou funkci navrženou pro zvýšení výkonu. Hromadná výměna polí záznamu však není podporována nástrojem ClassWizard. Tato možnost se vzájemně vylučuje s možností `CRecordset::optimizeBulkAdd`. Všimněte si, že pokud zadáte `CRecordset::useMultiRowFetch`, možnost `CRecordset::noDirtyFieldCheck` bude automaticky zapnuta (dvojité ukládání do vyrovnávací paměti nebude k dispozici), na dopředné sady záznamů, možnost `CRecordset::useExtendedFetch` bude automaticky zapnuta. Další informace o hromadném načítání řádků naleznete v článku [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

- `CRecordset::skipDeletedRecords` Všechny odstraněné záznamy přeskočte při navigaci v sadě záznamů. V určitých relativních načteních tato možnost sníží výkon. Tato možnost není platná pro sady záznamů s posouváním pouze vpřed. Při volání [přesunout](#move) s *nRows* parametrem nastaveným na hodnotu 0 a `CRecordset::skipDeletedRecords` sada, možností `Move` vyhodnocena. Všimněte si, že `CRecordset::skipDeletedRecords` je podobný *ovladač balení*, což znamená odstranění řádků se odeberou ze sady záznamů. Pokud však ovladač záznamy komprimuje, budou přeskočeny pouze vámi odstraněné záznamy. Záznamy odstraněné jinými uživateli v době, kdy byla sada otevřena, nebudou přeskočeny. `CRecordset::skipDeletedRecords` Přeskočí řádky odstraněné jinými uživateli.

- `CRecordset::useBookmarks` V sadě záznamů, lze použít záložky, pokud se podporuje. Záložky zpomalují načítání dat, ale zvyšují výkon navigace v nich. Nelze je použít v sadách záznamů s posouváním pouze vpřed. Další informace najdete v článku [sada záznamů: Záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

- `CRecordset::noDirtyFieldCheck` Vypněte automatické nečistých polí (dvojité ukládání do vyrovnávací paměti) kontrola. Tím dojde ke zvýšení výkonu. Pole je však zapotřebí ručně označit jako nečistá zavoláním členských funkcí `SetFieldDirty` a `SetFieldNull`. Povšimněte si, že dvojité ukládání do vyrovnávací paměti ve třídě `CRecordset` je podobné dvojitému ukládání do vyrovnávací paměti ve třídě `CDaoRecordset`. Ve třídě `CRecordset` však nelze zapnout dvojité ukládání do vyrovnávací paměti pro jednotlivá pole. Lze jej zapnout nebo vypnout pouze pro všechna pole najednou. Všimněte si, že pokud zadáte možnost `CRecordset::useMultiRowFetch`, pak `CRecordset::noDirtyFieldCheck` zapne automaticky, nicméně `SetFieldDirty` a `SetFieldNull` nelze použít v sadách záznamů implementujících hromadné načítání řádků.

- `CRecordset::executeDirect` Nepoužívat připravený příkaz jazyka SQL. Za účelem vylepšení výkonu, zadejte tuto možnost, pokud `Requery` nebude nikdy volána členská funkce.

- `CRecordset::useExtendedFetch` Implementace `SQLExtendedFetch` místo `SQLFetch`. Navrženo pro implementaci hromadného načítání řádků pro sady záznamů s posouváním pouze vpřed. Pokud zadáte možnost `CRecordset::useMultiRowFetch` na dopředné sady záznamů, potom `CRecordset::useExtendedFetch` bude automaticky zapnuta.

- `CRecordset::userAllocMultiRowBuffers` Uživatel přidělí vyrovnávací paměti úložišť pro data. Chcete-li přidělit své vlastní úložiště, použijte tuto možnost spolu s možností `CRecordset::useMultiRowFetch`. V opačném případě bude potřebné úložiště přiděleno rozhraním. Další informace najdete v článku [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Zadání `CRecordset::userAllocMultiRowBuffers` bez zadání `CRecordset::useMultiRowFetch` způsobí neplatnost kontrolního výrazu.

### <a name="return-value"></a>Návratová hodnota

Nenulovou hodnotu, pokud `CRecordset` objekt byl úspěšně otevřen; jinak vrátí hodnotu 0, pokud [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) (je-li zavolána) vrátí hodnotu 0.

### <a name="remarks"></a>Poznámky

Chcete-li spustit dotaz definovaný sadou záznamů, je zapotřebí zavolat tuto členskou funkci. Před voláním `Open`, musíte vytvořit objekt sady záznamů.

Tato sada záznamů připojení ke zdroji dat závisí na způsobu vytvoření sady záznamů před zavoláním funkce `Open`. Pokud předáte [CDatabase](../../mfc/reference/cdatabase-class.md) objektu do konstruktoru sady záznamů, který nebyl připojen ke zdroji dat, tato členská funkce používá [GetDefaultConnect](#getdefaultconnect) pokusí otevřít databázový objekt. Pokud předáte NULL do konstruktoru sady záznamů, vytvoří konstruktor `CDatabase` objekt a `Open` pokusí připojit k databázovému objektu. Podrobnosti o uzavírání sady záznamů a připojení za těchto různých podmínek naleznete v tématu [Zavřít](#close).

> [!NOTE]
>  Přístup ke zdroji dat pomocí objektu `CRecordset` je vždy sdílen. Na rozdíl od třídy `CDaoRecordset` nelze objekt `CRecordset` použít k otevření zdroje dat s výhradním přístupem.

Při volání `Open`, dotaz, obvykle SQL **vyberte** příkaz, vybere záznamy na základě kritérií uvedených v následující tabulce.

|Hodnota parametru IpszSQL|Zvolené záznamy jsou určeny|Příklad|
|------------------------------------|----------------------------------------|-------------|
|NULL|Řetězec vrácený funkcí `GetDefaultSQL`.||
|Název tabulky SQL|Všechny sloupce tabulkového seznamu ve funkci `DoFieldExchange` nebo `DoBulkFieldExchange`.|`"Customer"`|
|Název předdefinovaného dotazu (uložené procedury)|Sloupce, k jejichž vrácení je dotaz definován.|`"{call OverDueAccts}"`|
|**Vyberte** seznam sloupců **FROM** seznam tabulek|Zadané sloupce ze zadané tabulky nebo tabulek.|`"SELECT CustId, CustName FROM`<br /><br /> `Customer"`|

> [!CAUTION]
>  Ujistěte se, že do řetězce jazyka SQL nebyly vloženy prázdné znaky. Například, pokud vložen prázdný znak mezi složenou závorku a **volání** se interpretuje řetězec SQL jako název tabulky a začlení jej do – klíčové slovo, MFC **vyberte** příkaz, který bude mít za následek vyvolání výjimky. Obdobně, používá-li předdefinovaný dotaz výstupní parametr, nevkládejte prázdný znak mezi složenou závorku a "symbol. Nakonec nesmí vložen prázdný znak před složenou závorku v **volání** příkazu nebo před **vyberte** – klíčové slovo v **vyberte** příkazu.

Obvyklým postupem je předat hodnotu NULL na `Open`; v takovém případě `Open` volání [GetDefaultSQL](#getdefaultsql). Pokud používáte odvozený `CRecordset` třídy, `GetDefaultSQL` názvy tabulek zadaných v nástroji ClassWizard. Místo toho lze zadat jiné informace v parametru `lpszSQL`.

Bez ohledu na předané, `Open` vytvoří konečný řetězec SQL pro dotaz (řetězec může obsahovat SQL **kde** a **klauzule ORDER BY** klauzule připojenou k `lpszSQL` jste předali řetězec) a pak spustí dotaz. Můžete prozkoumat sestavený řetězec voláním [GetSQL](#getsql) po volání `Open`. Další podrobnosti o tom, jak sada záznamů sestavuje příkaz SQL a vybírá záznamy, najdete v článku [sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).

Datové členy polí třídy sady záznamů jsou svázány se sloupci zvolených dat. Jsou-li vráceny jakékoli záznamy, první záznam se stává aktuálním záznamem.

Pokud chcete nastavit možnosti sady záznamů, například filtr nebo řazení, zadat po vytvoření objektu sady záznamů, ale před voláním `Open`. Pokud chcete aktualizovat záznamy v sadě záznamů po sady záznamů je již otevřen, zavolejte [Requery](#requery).

Další informace, včetně dalších příkladů, najdete v článcích [sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md), [sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md), a [sada záznamů: Vytváření a uzavírání sad záznamů (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).

### <a name="example"></a>Příklad

Následující ukázky kódu demonstrují různé způsoby `Open` volání.

[!code-cpp[NVC_MFCDatabase#16](../../mfc/codesnippet/cpp/crecordset-class_15.cpp)]

##  <a name="refreshrowset"></a>  CRecordset::RefreshRowset

Aktualizuje data a stav pro řádek v aktuální sadě řádků.

```
void RefreshRowset(
    WORD wRow,
    WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>Parametry

*wRow*<br/>
Jedna pozice řádku v aktuální sadě řádků. Tato hodnota rozsahu od nuly do velikosti v sadě řádků.

*wLockType*<br/>
Hodnota určující, jak uzamknout řádek po byly aktualizovány. Podrobnosti najdete v tématu poznámky.

### <a name="remarks"></a>Poznámky

Pokud předáte nulové hodnoty *wRow*, pak se aktualizují každý řádek v dané sadě řádků.

Použití `RefreshRowset`, musí jste implementovali hromadné načítání řádků zadáním `CRecordset::useMulitRowFetch` možnost [otevřít](#open) členskou funkci.

`RefreshRowset` volá funkci rozhraní API ODBC `SQLSetPos`. *WLockType* parametr určuje stav zámku řádku po `SQLSetPos` provedl. Následující tabulka popisuje možné hodnoty pro *wLockType*.

|wLockType|Popis|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE (výchozí hodnota)|Zdroj ovladače nebo data zajišťuje, že řádek ve stejném státě uzamčen nebo odemknout před `RefreshRowset` byla volána.|
|SQL_LOCK_EXCLUSIVE|Zdroj ovladače nebo data výhradně zamkne řádku. Ne všechny zdroje dat podporují tento typ zámku.|
|SQL_LOCK_UNLOCK|Zdroj ovladače nebo data odemkne řádku. Ne všechny zdroje dat podporují tento typ zámku.|

Další informace o `SQLSetPos`, naleznete v sadě Windows SDK. Další informace o hromadném načítání řádků naleznete v článku [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="requery"></a>  CRecordset::Requery

Znovu sestaví (aktualizace) na sadu záznamů.

```
virtual BOOL Requery();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud sada záznamů bylo byl úspěšně sestaven; jinak 0.

### <a name="remarks"></a>Poznámky

Jsou-li vráceny jakékoli záznamy, první záznam se stává aktuálním záznamem.

V pořadí záznamů reflektování přidání a odstranění, které vám a dalším uživatelům, aby ke zdroji dat, je nutné znovu vytvořit sadu záznamů voláním `Requery`. Pokud je dynamická sada záznamů, automaticky zobrazuje aktualizace, které vy nebo ostatní uživatelé provést existujících záznamů (ale ne doplňky). Pokud je sada záznamů snímku, musíte zavolat `Requery` tak, aby odrážely změny podle jiných uživatelů a přidání a odstranění.

Pro dynamická sada nebo snímku volání `Requery` kdykoli chcete znovu vytvořit sadu záznamů pomocí nový filtr nebo řazení nebo nové hodnoty parametrů. Nastavit vlastnost nový filtr nebo řazení přiřazením nových hodnot `m_strFilter` a `m_strSort` před voláním `Requery`. Nastavit nové parametry přiřazením nových hodnot pro parametry datových členů před voláním `Requery`. Pokud filtrování a řazení řetězců jsou beze změny, můžete znovu použít dotaz, což zvyšuje výkon.

Pokud se nezdaří pokus o opětovné vytvoření sady záznamů, sady záznamů je zavřený. Před voláním `Requery`, můžete určit, jestli sadu záznamů můžete fokusu voláním `CanRestart` členskou funkci. `CanRestart` není zaručeno, že `Requery` proběhne úspěšně.

> [!CAUTION]
>  Volání `Requery` pouze poté, co jste volali [otevřít](#open).

### <a name="example"></a>Příklad

V tomto příkladu znovu sestaví sada záznamů použít jiné pořadí řazení.

[!code-cpp[NVC_MFCDatabase#29](../../mfc/codesnippet/cpp/crecordset-class_16.cpp)]

##  <a name="setabsoluteposition"></a>  CRecordset::SetAbsolutePosition

Nastaví pozici sady záznamů v záznamu odpovídá zadané číslo záznamu.

```
void SetAbsolutePosition(long nRows);
```

### <a name="parameters"></a>Parametry

*nRows*<br/>
Založen na jedničce pořadové číslo pozice pro aktuální záznam v sadě záznamů.

### <a name="remarks"></a>Poznámky

`SetAbsolutePosition` přesune ukazatel aktuální záznam založené na tomto pořadí.

> [!NOTE]
>  Tato členská funkce není platné sady záznamů s posouváním pouze vpřed.

Pro sady záznamů rozhraní ODBC o nastavení absolutní pozici 1 odkazuje na první záznam v sadě záznamů; nastavení 0 znamená pozice (BOF) začátku souboru.

Můžete také předat záporné hodnoty `SetAbsolutePosition`. V tomto případě pozici sady záznamů je vyhodnocen od konce sady záznamů. Například `SetAbsolutePosition( -1 )` přesune ukazatel na aktuální záznam na poslední záznam v sadě záznamů.

> [!NOTE]
>  Absolutní pozici není určena pro použití jako číslo náhradní záznam. Doporučený způsob uchování a vrácení k dané pozici od pozice změny záznamu při odstranění předchozí záznamy jsou stále záložky. Kromě toho můžete nemůže být jistí, že daný záznam budou mít stejné absolutní pozici, pokud sada záznamů se znovu vytvoří znovu vzhledem k tomu, že pokud není vytvořené příkazem SQL pomocí nenízaručeno,žepořadíjednotlivýchzáznamůvrámcisadyzáznamů**Klauzule ORDER BY** klauzuli.

Další informace o navigaci v sadě záznamů a záložky, najdete v článcích [sada záznamů: Posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) a [sada záznamů: Záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

##  <a name="setbookmark"></a>  CRecordset::SetBookmark

Nastaví pozici sady záznamů na záznam obsahující zadanou záložkou.

```
void SetBookmark(const CDBVariant& varBookmark);
```

### <a name="parameters"></a>Parametry

*varBookmark*<br/>
Odkaz na [CDBVariant](../../mfc/reference/cdbvariant-class.md) objekt, který obsahuje hodnotu záložku pro konkrétní záznam.

### <a name="remarks"></a>Poznámky

Chcete-li zjistit, jestli jsou v sadě záznamů podporuje záložky, zavolejte [CanBookmark](#canbookmark). Pokud chcete zpřístupnit záložky Pokud jsou podporovány, je nutné nastavit `CRecordset::useBookmarks` možnost *dwOptions* parametr [otevřít](#open) členskou funkci.

> [!NOTE]
>  Pokud jsou záložky nepodporovaný nebo nedostupný, volání `SetBookmark` povede k vyvolání výjimky. Záložky nejsou podporované sady záznamů s posouváním pouze vpřed.

Nejdřív načtěte záložku pro požadovaný aktuální záznam, zavolejte [GetBookmark](#getbookmark), který uloží hodnotu záložku `CDBVariant` objektu. Později, můžete se vrátit k tomuto záznamu voláním `SetBookmark` pomocí hodnoty uloženou záložku.

> [!NOTE]
>  Po určitých operacích sady záznamů, měli byste zkontrolovat trvalost záložku před voláním `SetBookmark`. Například, pokud načtete Záložka s `GetBookmark` a následně zavolat `Requery`, Záložka už nebude platná. Volání [CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) ke kontrole, jestli může bezpečně volat `SetBookmark`.

Další informace o záložek a navigaci v sadě záznamů najdete v článcích [sada záznamů: Záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) a [sada záznamů: Posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

##  <a name="setfielddirty"></a>  CRecordset::SetFieldDirty

Označí pole datového člena sady záznamů, jak změnit nebo jako beze změny.

```
void SetFieldDirty(void* pv, BOOL bDirty = TRUE);
```

### <a name="parameters"></a>Parametry

*pv*<br/>
Obsahuje adresu pole datového člena v sadě záznamů nebo hodnota NULL. Pokud má hodnotu NULL, se označí všechny datové členy v sadě záznamů. (C++ NULL není stejná jako hodnota Null v, řečeno terminologií databáze, což znamená, že "s žádnou hodnotu.")

*bDirty*<br/>
TRUE, pokud je datový člen pole bude označen jako "nesprávné" (změněné). V opačném případě hodnotu FALSE, pokud je datový člen pole bude označen jako "clean" (beze změny).

### <a name="remarks"></a>Poznámky

Označení polí jako beze změny zajistí pole neaktualizuje a má za následek menší provoz SQL.

> [!NOTE]
>  Tato členská funkce se nevztahuje na sady záznamů, které jsou pomocí hromadné načítání řádků. Pokud jste implementovali hromadné načítání řádků, pak `SetFieldDirty` způsobí neplatnost kontrolního výrazu. Další informace o hromadném načítání řádků naleznete v článku [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Značky framework změnit pole datové členy zajistit, že se budou zapisovat do záznamu ve zdroji dat pomocí mechanismu pole záznamu (RFX) systému exchange. Změna hodnoty pole obecně nastaví pole změny automaticky, tedy zřídka bude nutné zavolat `SetFieldDirty` sami, ale můžete někdy chtít zajistit, že sloupce budou explicitně aktualizovat nebo vložit bez ohledu na to, jaká hodnota je v datech pole člen.

> [!CAUTION]
>  Voláním této členské funkce, až po jste volali [upravit](#edit) nebo [AddNew](#addnew).

Použití NULL pro první argument funkce se vztahují pouze k funkci `outputColumn` pole, nikoli `param` pole. Například volání

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

Nastaví pouze `outputColumn` pole na hodnotu NULL; `param` pole zůstanou beze změn.

Pro práci na `param` pole, je nutné zadat skutečnou adresu jednotlivých `param` chcete pracovat, jako například:

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

To znamená, že nemůžete nastavit všechny `param` pole na hodnotu NULL, jako u `outputColumn` pole.

##  <a name="setfieldnull"></a>  CRecordset::SetFieldNull

Označí pole datového člena sady záznamů jako Null (konkrétně s žádná hodnota) nebo jinou hodnotu než Null.

```
void SetFieldNull(void* pv, BOOL bNull = TRUE);
```

### <a name="parameters"></a>Parametry

*pv*<br/>
Obsahuje adresu pole datového člena v sadě záznamů nebo hodnota NULL. Pokud má hodnotu NULL, se označí všechny datové členy v sadě záznamů. (C++ NULL není stejná jako hodnota Null v, řečeno terminologií databáze, což znamená, že "s žádnou hodnotu.")

*bNull*<br/>
Nenulové, pokud je datový člen pole bude označen jako s žádné hodnoty (Null). Jinak 0, pokud je datový člen pole bude označen jako jinou hodnotu než Null.

### <a name="remarks"></a>Poznámky

Při přidání nového záznamu do sady záznamů, všechny datové členy jsou zpočátku nastaven na hodnotu Null a označen jako "nesprávné" (změněné). Při načítání záznam ze zdroje dat, její sloupce již mají hodnoty nebo hodnotu Null.

> [!NOTE]
>  Nevolejte tuto členskou funkci na sady záznamů, které jsou pomocí hromadné načítání řádků. Pokud jste implementovali hromadné načítání řádků, volání `SetFieldNull` výsledkem neplatnost kontrolního výrazu. Další informace o hromadném načítání řádků naleznete v článku [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Pokud chcete konkrétně určit pole z aktuální záznam tak, že hodnoty, volejte nemusí `SetFieldNull` s *bNull* nastavena na hodnotu TRUE, označit ji jako hodnotu Null. Pokud byla dříve označená pole hodnotu Null a teď chcete jí hodnotu, jednoduše nastavte jej na novou hodnotu. Nemáte, můžete odebrat příznak Null s `SetFieldNull`. Chcete-li zjistit, jestli pole může mít hodnotu Null, zavolejte `IsFieldNullable`.

> [!CAUTION]
>  Voláním této členské funkce, až po jste volali [upravit](#edit) nebo [AddNew](#addnew).

Použití NULL pro první argument funkce se vztahují pouze k funkci `outputColumn` pole, nikoli `param` pole. Například volání

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

Nastaví pouze `outputColumn` pole na hodnotu NULL; `param` pole zůstanou beze změn.

Pro práci na `param` pole, je nutné zadat skutečnou adresu jednotlivých `param` chcete pracovat, jako například:

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

To znamená, že nemůžete nastavit všechny `param` pole na hodnotu NULL, jako u `outputColumn` pole.

> [!NOTE]
>  Při nastavování parametrů na hodnotu Null, volání `SetFieldNull` před sady záznamů je otevřené za následek kontrolní výraz. V takovém případě volat [SetParamNull](#setparamnull).

`SetFieldNull` se implementuje pomocí [DoFieldExchange](#dofieldexchange).

##  <a name="setlockingmode"></a>  CRecordset::SetLockingMode

Nastaví režim uzamčení "optimistické" uzamčení (výchozí) nebo "pesimistické" zamykání. Určuje, jak jsou záznamy zamknuté aktualizací.

```
void SetLockingMode(UINT nMode);
```

### <a name="parameters"></a>Parametry

*nMode*<br/>
Obsahuje nejméně jednu z následujících hodnot z `enum LockMode`:

- `optimistic` Optimistické uzamykání, uzamkne záznam aktualizuje pouze během volání `Update`.

- `pessimistic` Pesimistické zamykání uzamkne záznam co nejdříve `Edit` nazývá a udržuje ho zamykat, dokud `Update` volání dokončí nebo přesunout do nového záznamu.

### <a name="remarks"></a>Poznámky

Voláním této členské funkce, pokud je potřeba určit, které používá pro aktualizace sady záznamů dvou strategií zamykání záznamů. Ve výchozím režimu uzamčení sady záznamů je `optimistic`. Můžete výběr změnit na víc opatrní `pessimistic` strategie uzamčení. Volání `SetLockingMode` po vytvoření a otevření objektu sady záznamů, ale před voláním `Edit`.

##  <a name="setparamnull"></a>  CRecordset::SetParamNull

Označí parametr jako hodnotu Null (konkrétně s žádná hodnota) nebo jinou hodnotu než Null.

```
void SetParamNull(
    int nIndex,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Z nuly vycházející index parametru.

*bNull*<br/>
Pokud hodnotu TRUE (výchozí hodnota), parametr je označený jako hodnota Null. V opačném případě je parametr označený jako jinou hodnotu než Null.

### <a name="remarks"></a>Poznámky

Na rozdíl od [SetFieldNull](#setfieldnull), můžete volat `SetParamNull` před otevřením sady záznamů.

`SetParamNull` Obvykle se používá s předdefinované dotazy (uložené procedury).

##  <a name="setrowsetcursorposition"></a>  CRecordset::SetRowsetCursorPosition

Přesune kurzor na řádek v rámci aktuální sady řádků.

```
void SetRowsetCursorPosition(WORD wRow, WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>Parametry

*wRow*<br/>
Jedna pozice řádku v aktuální sadě řádků. Tato hodnota musí být v rozsahu 1 na velikost v sadě řádků.

*wLockType*<br/>
Hodnota označující, jak uzamknout řádek po byly aktualizovány. Podrobnosti najdete v tématu poznámky.

### <a name="remarks"></a>Poznámky

Při implementaci hromadné načítání řádků, záznamy se načítají pomocí sad řádků, pokud je první záznam v počet získaných řádků aktuální záznam. Aby bylo možné nastavit jiný záznam v dané sadě řádků na aktuální záznam, zavolejte `SetRowsetCursorPosition`. Například můžete kombinovat `SetRowsetCursorPosition` s [getfieldvalue –](#getfieldvalue) členská funkce se dynamicky načíst data ze všech záznamů sady záznamů.

Použití `SetRowsetCursorPosition`, musí jste implementovali hromadné načítání řádků zadáním `CRecordset::useMultiRowFetch` možnost *dwOptions* parametr [otevřít](#open) členská funkce.

`SetRowsetCursorPosition` volá funkci rozhraní API ODBC `SQLSetPos`. *WLockType* parametr určuje stav zámku řádku po `SQLSetPos` provedl. Následující tabulka popisuje možné hodnoty pro *wLockType*.

|wLockType|Popis|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE (výchozí hodnota)|Zdroj ovladače nebo data zajišťuje, že řádek ve stejném státě uzamčen nebo odemknout před `SetRowsetCursorPosition` byla volána.|
|SQL_LOCK_EXCLUSIVE|Zdroj ovladače nebo data výhradně zamkne řádku. Ne všechny zdroje dat podporují tento typ zámku.|
|SQL_LOCK_UNLOCK|Zdroj ovladače nebo data odemkne řádku. Ne všechny zdroje dat podporují tento typ zámku.|

Další informace o `SQLSetPos`, naleznete v sadě Windows SDK. Další informace o hromadném načítání řádků naleznete v článku [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="setrowsetsize"></a>  CRecordset::SetRowsetSize

Určuje počet záznamů, které chcete načíst během fetch.

```
virtual void SetRowsetSize(DWORD dwNewRowsetSize);
```

### <a name="parameters"></a>Parametry

*dwNewRowsetSize*<br/>
Počet řádků pro načtení během daného načítání.

### <a name="remarks"></a>Poznámky

Tato virtuální členská funkce určuje, kolik řádků chcete načíst během jednoho načtení při použití hromadné načítání řádků. Implementovat hromadné načítání řádků, je nutné nastavit `CRecordset::useMultiRowFetch` možnost *dwOptions* parametr [otevřít](#open) členskou funkci.

> [!NOTE]
>  Volání `SetRowsetSize` bez implementace hromadné načítání řádků způsobí neplatnost kontrolního výrazu.

Volání `SetRowsetSize` před voláním `Open` začátku nastavit velikost řádků pro sady záznamů. Výchozí velikost řádků při implementaci hromadného načítání řádků je 25.

> [!NOTE]
>  Buďte opatrní při volání metody `SetRowsetSize`. Pokud jsou ručně přidělení úložiště dat (podle `CRecordset::userAllocMultiRowBuffers` dwOptions parametru v `Open`), měli byste zkontrolovat, jestli je potřeba přidělit jinému uživateli vyrovnávací paměti úložiště po zavolání `SetRowsetSize`, ale před Proveďte všechny operace kurzoru navigace.

Chcete-li získat aktuální nastavení pro velikost řádků, zavolejte [GetRowsetSize](#getrowsetsize).

Další informace o hromadném načítání řádků naleznete v článku [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="update"></a>  CRecordset::Update

Dokončení `AddNew` nebo `Edit` operace uložením nových nebo upravených dat ve zdroji dat.

```
virtual BOOL Update();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud jeden záznam byl úspěšně aktualizován; jinak 0, pokud jste změnili žádné sloupce. Pokud nebyly aktualizovány žádné záznamy, nebo pokud více než jeden záznam byl aktualizován, je vyvolána výjimka. Dojde k výjimce také další chyby ve zdroji dat.

### <a name="remarks"></a>Poznámky

Voláním této členské funkce po volání [AddNew](#addnew) nebo [upravit](#edit) členskou funkci. Toto volání je vyžadované k dokončení `AddNew` nebo `Edit` operace.

> [!NOTE]
>  Pokud jste implementovali hromadné načítání řádků, nelze volat `Update`. To způsobí neplatnost kontrolního výrazu. Přestože třída `CRecordset` neposkytuje mechanismus pro hromadnou aktualizaci řádků dat, můžete napsat vlastní funkce pomocí funkce ODBC API `SQLSetPos`. Další informace o hromadném načítání řádků naleznete v článku [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Obě `AddNew` a `Edit` připravit vyrovnávací paměť úprav ve kterém je umístí údaje přidané nebo upravené pro ukládání do zdroje dat. `Update` uloží data. Jsou aktualizovány pouze pole označeno nebo zjistil jako změnit.

Pokud je zdroj dat podporuje transakce, lze provádět `Update` volání (a odpovídající `AddNew` nebo `Edit` volání) součástí transakce. Další informace o transakcích, najdete v článku [transakce (ODBC)](../../data/odbc/transaction-odbc.md).

> [!CAUTION]
>  Při volání `Update` bez předchozího volání `AddNew` nebo `Edit`, `Update` vyvolá `CDBException`. Při volání `AddNew` nebo `Edit`, je nutné volat `Update` před voláním `Move` operace nebo před zavřením připojení ke zdroji dat nebo sady záznamů. Jinak vaše změny se ztratí bez oznámení.

Podrobnosti o zpracování `Update` selhání, najdete v článku [sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

### <a name="example"></a>Příklad

Přečtěte si článek [transakce: Provádění transakcí v sadě záznamů (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).

## <a name="see-also"></a>Viz také:

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDatabase – třída](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordView – třída](../../mfc/reference/crecordview-class.md)
