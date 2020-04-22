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
ms.openlocfilehash: ab6cde9f478dc6f2e3cb0ba5bb338a3852f083fd
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750502"
---
# <a name="crecordset-class"></a>CRecordset – třída

Představuje sadu záznamů vybraných ze zdroje dat.

## <a name="syntax"></a>Syntaxe

```
class CRecordset : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CRecordset::CRecordset](#crecordset)|Vytvoří `CRecordset` objekt. Odvozené třídy musí poskytnout konstruktor, který volá tento jeden.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CRecordset::Přidatnový](#addnew)|Připravuje se na přidání nového záznamu. Volání `Update` k dokončení přidání.|
|[CRecordset::CanAppend](#canappend)|Vrátí nenulovou hodnotu, pokud lze nové `AddNew` záznamy přidat do sady záznamů pomocí členské funkce.|
|[CRecordset::CanBookmark](#canbookmark)|Vrátí nenulovou hodnotu, pokud sada záznamů podporuje záložky.|
|[CRecordset::Zrušit](#cancel)|Zruší asynchronní operaci nebo proces z druhého vlákna.|
|[CRecordset::Zrušitaktualizaci](#cancelupdate)|Zruší všechny čekající aktualizace `AddNew` z `Edit` důvodu nebo operace.|
|[CRecordset::CanRestart](#canrestart)|Vrátí nenulovou, pokud `Requery` může být volána pro opětovné spuštění dotazu sady záznamů.|
|[CRecordset::CanScroll](#canscroll)|Vrátí nenulovou hodnotu, pokud můžete procházet záznamy.|
|[CRecordset::CanTransact](#cantransact)|Vrátí nenulovou, pokud zdroj dat podporuje transakce.|
|[CRecordset::CanUpdate](#canupdate)|Vrátí nenulovou hodnotu, pokud lze sadu záznamů aktualizovat (můžete přidávat, aktualizovat nebo odstraňovat záznamy).|
|[CRecordset::CheckRowsetError](#checkrowseterror)|Volána ke zpracování chyb generovaných během načítání záznamu.|
|[CRecordset::Zavřít](#close)|Zavře sadu záznamů a odbc HSTMT s ním spojené.|
|[CRecordset::Delete](#delete)|Odstraní aktuální záznam ze sady záznamů. Po odstranění je nutné explicitně přejít na jiný záznam.|
|[CRecordset::DoBulkFieldExchange](#dobulkfieldexchange)|Nazývá se výměna hromadných řádků dat ze zdroje dat do sady záznamů. Implementuje výměnu polí hromadného záznamu (Bulk RFX).|
|[CRecordset::DoFieldExchange](#dofieldexchange)|Nazývá se výměna dat (v obou směrech) mezi datovými členy pole sady záznamů a odpovídajícím záznamem ve zdroji dat. Implementuje výměnu pole záznamu (RFX).|
|[CRecordset::Upravit](#edit)|Připraví změny aktuálního záznamu. Volání `Update` k dokončení úpravy.|
|[CRecordset::FlushResultSet](#flushresultset)|Vrátí nenulovou, pokud je při použití předdefinovaného dotazu načtení jiná sada výsledků.|
|[CRecordset::GetBookmark](#getbookmark)|Přiřadí hodnotu záložky záznamu objektu parametru.|
|[CRecordset::GetDefaultConnect](#getdefaultconnect)|Volána získat výchozí připojovací řetězec.|
|[CRecordset::GetDefaultSQL](#getdefaultsql)|Volána k získání výchozího řetězce SQL ke spuštění.|
|[CRecordset::GetFieldValue](#getfieldvalue)|Vrátí hodnotu pole v sadě záznamů.|
|[CRecordset::GetODBCFieldCount](#getodbcfieldcount)|Vrátí počet polí v sadě záznamů.|
|[CRecordset::GetODBCFieldInfo](#getodbcfieldinfo)|Vrátí určité druhy informací o polích v sadě záznamů.|
|[CRecordset::GetRecordCount](#getrecordcount)|Vrátí počet záznamů v sadě záznamů.|
|[CRecordset::GetRowsetSize](#getrowsetsize)|Vrátí počet záznamů, které chcete načíst během jednoho načtení.|
|[CRecordset::GetRowsFetched](#getrowsfetched)|Vrátí skutečný počet řádků načtených během načtení.|
|[CRecordset::GetRowStatus](#getrowstatus)|Vrátí stav řádku po načtení.|
|[CRecordset::GetSQL](#getsql)|Získá řetězec SQL slouží k výběru záznamů pro sadu záznamů.|
|[CRecordset::GetStatus](#getstatus)|Získá stav sady záznamů: index aktuálního záznamu a zda byl získán konečný počet záznamů.|
|[CRecordset::GetTableName](#gettablename)|Získá název tabulky, na kterém je založena sada záznamů.|
|[CRecordset::IsBOF](#isbof)|Vrátí nenulovou hodnotu, pokud byla sada záznamů umístěna před prvním záznamem. Neexistuje žádný aktuální záznam.|
|[CRecordset::IsDeleted](#isdeleted)|Vrátí nenulovou hodnotu, pokud je sada záznamů umístěna na odstraněný záznam.|
|[CRecordset::IsEOF](#iseof)|Vrátí nenulovou hodnotu, pokud byla sada záznamů umístěna za posledním záznamem. Neexistuje žádný aktuální záznam.|
|[CRecordset::IsFieldDirty](#isfielddirty)|Vrátí nenulovou hodnotu, pokud bylo změněno zadané pole v aktuálním záznamu.|
|[Sada záznamů C::Hodnota IsFieldNull](#isfieldnull)|Vrátí nenulovou hodnotu, pokud je zadané pole v aktuálním záznamu null (nemá žádnou hodnotu).|
|[CRecordset::IsFieldNullable](#isfieldnullable)|Vrátí nenulovou hodnotu, pokud lze zadané pole v aktuálním záznamu nastavit na hodnotu null (bez hodnoty).|
|[CRecordset::IsOpen](#isopen)|Vrátí nenulovou hodnotu, pokud `Open` byla volána dříve.|
|[CRecordset::Přesunout](#move)|Umístí sadu záznamů na zadaný počet záznamů z aktuálního záznamu v obou směrech.|
|[CRecordset::PřesunoutPrvní](#movefirst)|Umístí aktuální záznam na první záznam v sadě záznamů. Test `IsBOF` pro první.|
|[CRecordset::MoveLast](#movelast)|Umístí aktuální záznam na poslední záznam nebo na poslední sadu řádků. Test `IsEOF` pro první.|
|[CRecordset::MoveNext](#movenext)|Umístí aktuální záznam na další záznam nebo na další sadu řádků. Test `IsEOF` pro první.|
|[CRecordset::MovePrev](#moveprev)|Umístí aktuální záznam na předchozí záznam nebo na předchozí sadu řádků. Test `IsBOF` pro první.|
|[CRecordset::OnSetOptions](#onsetoptions)|Nazývá se nastavení možností (používá se při výběru) pro zadaný příkaz ODBC.|
|[CRecordset::OnSetUpdateOptions](#onsetupdateoptions)|Nazývá se nastavení možností (používá se při aktualizaci) pro zadaný příkaz ODBC.|
|[Crecordset::open](#open)|Otevře sadu záznamů načtením tabulky nebo provedením dotazu, který sada záznamů představuje.|
|[CRecordset::RefreshRowset](#refreshrowset)|Aktualizuje data a stav zadaného řádku(ů).|
|[CRecordset::Requery](#requery)|Znovu spustí dotaz sady záznamů a aktualizuje vybrané záznamy.|
|[CRecordset::Nastavitabsoluteposition](#setabsoluteposition)|Umístí sadu záznamů na záznam odpovídající zadanému číslu záznamu.|
|[CRecordset::SetBookmark](#setbookmark)|Umístí sadu záznamů na záznam určený záložkou.|
|[CRecordset::SetFieldDirty](#setfielddirty)|Označí zadané pole v aktuálním záznamu jako změněné.|
|[CRecordset::SetFieldNull](#setfieldnull)|Nastaví hodnotu zadaného pole v aktuálním záznamu na hodnotu null (bez hodnoty).|
|[CRecordset::SetLockingMode](#setlockingmode)|Nastaví režim zamykání na "optimistické" zamykání (výchozí) nebo "pesimistické" zamykání. Určuje, jak jsou záznamy uzamčeny pro aktualizace.|
|[CRecordset::SetParamNull](#setparamnull)|Nastaví zadaný parametr na hodnotu null (bez hodnoty).|
|[CRecordset::SetRowsetCursorPosition](#setrowsetcursorposition)|Umístí kurzor na zadaný řádek v rámci sady řádků.|
|[CRecordset::SetRowsetSize](#setrowsetsize)|Určuje počet záznamů, které chcete načíst během načítání.|
|[CRecordset::Aktualizovat](#update)|Dokončí operaci `AddNew` `Edit` nebo operaci uložením nových nebo upravených dat do zdroje dat.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CSada záznamů::m_hstmt](#m_hstmt)|Obsahuje popisovač příkazu ODBC pro sadu záznamů. Zadejte `HSTMT`.|
|[CRecordset::m_nFields](#m_nfields)|Obsahuje počet datových členů pole v sadě záznamů. Zadejte `UINT`.|
|[CSada záznamů::m_nParams](#m_nparams)|Obsahuje počet datových členů parametrů v sadě záznamů. Zadejte `UINT`.|
|[CRecordset::m_pDatabase](#m_pdatabase)|Obsahuje ukazatel na `CDatabase` objekt, jehož prostřednictvím je sada záznamů připojena ke zdroji dat.|
|[CSada záznamů::m_strFilter](#m_strfilter)|Obsahuje `CString` klauzuli, která určuje klauzuli `WHERE` strukturovaného dotazovacího jazyka (SQL). Používá se jako filtr k výběru pouze těch záznamů, které splňují určitá kritéria.|
|[CRecordset::m_strSort](#m_strsort)|`CString` Obsahuje, který určuje `ORDER BY` klauzuli SQL. Slouží k řízení způsobu řazení záznamů.|

## <a name="remarks"></a><a name="remarks"></a>Poznámky

Objekty označované `CRecordset` jako "sady záznamů" se obvykle používají ve dvou formách: dynaseje a snímky. Sada dynasad zůstane synchronizována s aktualizacemi dat provedenými jinými uživateli. Snímek je statické zobrazení dat. Každý formulář představuje sadu záznamů opravených v době otevření sady záznamů, ale při přechodu na záznam v dynasetě odráží změny následně provedené v záznamu, a to buď jinými uživateli, nebo jinými sadami záznamů v aplikaci.

> [!NOTE]
> Pokud pracujete s třídami DAO (Data Access Objects) místo s třídami Open Database Connectivity (ODBC), použijte místo toho třídu [CDaoRecordset.](../../mfc/reference/cdaorecordset-class.md) Další informace naleznete v článku [Přehled: Programování databáze](../../data/data-access-programming-mfc-atl.md).

Chcete-li pracovat s oběma typy sad záznamů, obvykle odvodit třídu sady záznamů specifické pro aplikaci z `CRecordset`. Sady záznamů vybírají záznamy ze zdroje dat a pak můžete:

- Procházejte záznamy.

- Aktualizujte záznamy a zadejte režim uzamčení.

- Filtrujte sadu záznamů, abyste omezili, které záznamy vybere z těch, které jsou k dispozici ve zdroji dat.

- Seřaďte sadu záznamů.

- Parametrizujte sadu záznamů pro přizpůsobení jejího výběru informacemi, které nejsou známy až do spuštění.

Chcete-li použít třídu, otevřete databázi a vytvořte objekt `CDatabase` sady záznamů a předejte konstruktoru ukazatel objektu. Potom volání `Open` sady záznamů členské funkce, kde můžete určit, zda je objekt dynaset nebo snímek. Volání `Open` vybere data ze zdroje dat. Po otevření objektu sady záznamů použijte jeho členské funkce a datové členy k procházení záznamů a pracujte s nimi. Dostupné operace závisí na tom, zda je objekt dynaset nebo snímek, zda je aktualizovatelný nebo jen pro čtení (to závisí na schopnosti zdroje dat připojení otevřené databáze (ODBC) a zda jste implementovali hromadné načítání řádků. Chcete-li aktualizovat záznamy, které mohly být od `Open` volání `Requery` změněny nebo přidány, zavolejte člennou funkci objektu. Volání `Close` členské funkce objektu a zničit objekt po dokončení s ním.

V odvozené `CRecordset` třídě se výměna pole záznamu (RFX) nebo hromadná výměna pole záznamu (Bulk RFX) používá k podpoře čtení a aktualizace polí záznamů.

Další informace o sadách záznamů a výměně polí záznamů naleznete v článcích [Přehled: Programování databáze](../../data/data-access-programming-mfc-atl.md), [Sada záznamů (ODBC),](../../data/odbc/recordset-odbc.md) [Sada záznamů: Načítání záznamů hromadně (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)a [Výměna pole záznamů (RFX).](../../data/odbc/record-field-exchange-rfx.md) Zaměření na dynasady a snímky naleznete v článcích [Dynaset](../../data/odbc/dynaset.md) a [Snímek](../../data/odbc/snapshot.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CRecordset`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="crecordsetaddnew"></a><a name="addnew"></a>CRecordset::Přidatnový

Připraví se na přidání nového záznamu do tabulky.

```
virtual void AddNew();
```

### <a name="remarks"></a>Poznámky

Chcete-li zobrazit nově přidaný záznam, musíte zavolat členskou funkci [Requery.](#requery) Pole záznamu jsou zpočátku Null. (V terminologii databáze null znamená "bez hodnoty" a není stejný jako NULL v jazyce C++.) Chcete-li operaci dokončit, musíte zavolat člennou funkci [Aktualizace.](#update) `Update`uloží změny do zdroje dat.

> [!NOTE]
> Pokud jste implementovali hromadné načítání řádků, nelze volat `AddNew`. Výsledkem bude neúspěšný kontrolní výraz. Přestože `CRecordset` třída neposkytuje mechanismus pro aktualizaci hromadných řádků dat, můžete zapisovat vlastní funkce pomocí funkce `SQLSetPos`ROZHRANÍ API ROZHRANÍ ODBC . Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

`AddNew`připraví nový prázdný záznam pomocí datových členů sady záznamů. Po volání `AddNew`nastavte požadované hodnoty v datových členech pole sady záznamů. (Není pro tento účel třeba volat členská `Edit` funkci [Edit;](#edit) používejte pouze pro existující záznamy.) Při následném `Update`volání jsou změněné hodnoty v datových členech pole uloženy ve zdroji dat.

> [!CAUTION]
> Pokud před voláním `Update`přejdete na nový záznam , nový záznam bude ztracen a nebude vydáno žádné upozornění.

Pokud zdroj dat podporuje transakce, můžete `AddNew` volání součástí transakce. Další informace o transakcích naleznete v tématu [cdatabase](../../mfc/reference/cdatabase-class.md)třídy . Všimněte si, že byste měli zavolat [CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) před voláním `AddNew`.

> [!NOTE]
> U dynaseje jsou nové záznamy přidány do sady záznamů jako poslední záznam. Přidané záznamy nejsou přidány do snímků; chcete-li `Requery` aktualizovat sadu záznamů, musíte zavolat.

Je nezákonné volat `AddNew` sadu záznamů, `Open` jehož členská funkce nebyla volána. A `CDBException` je vyvolána, `AddNew` pokud voláte sadu záznamů, které nelze připojit. Můžete určit, zda je sada záznamů aktualizovatelná voláním [CanAppend](#canappend).

Další informace naleznete v následujících článcích: [Sada záznamů: Jak sady záznamů aktualizovat záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md), [Sada záznamů: Přidání, Aktualizace a odstranění záznamů (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)a [Transakce (ODBC).](../../data/odbc/transaction-odbc.md)

### <a name="example"></a>Příklad

Viz článek [Transakce: Provedení transakce v sadě záznamů (ODBC).](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)

## <a name="crecordsetcanappend"></a><a name="canappend"></a>CRecordset::CanAppend

Určuje, zda dříve otevřená sada záznamů umožňuje přidávat nové záznamy.

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud sada záznamů umožňuje přidávání nových záznamů; jinak 0. `CanAppend`vrátí hodnotu 0, pokud jste sadu záznamů otevřeli jen pro čtení.

## <a name="crecordsetcanbookmark"></a><a name="canbookmark"></a>CRecordset::CanBookmark

Určuje, zda sada záznamů umožňuje označit záznamy pomocí záložek.

```
BOOL CanBookmark() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud sada záznamů podporuje záložky; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce je `CRecordset::useBookmarks` nezávislá na možnosti v parametru *dwOptions* členské funkce [Otevřít.](#open) `CanBookmark`označuje, zda dané záložky podpory ovladače ODBC a typu kurzoru podporují. `CRecordset::useBookmarks`označuje, zda budou záložky k dispozici, pokud jsou podporovány.

> [!NOTE]
> Záložky nejsou podporovány v sadách záznamů pouze pro předávání.

Další informace o záložkách a navigaci v sadě záznamů naleznete v článcích [Sada záznamů: Záložky a absolutní pozice (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) a [Sada záznamů: Posouvání (ODBC).](../../data/odbc/recordset-scrolling-odbc.md)

## <a name="crecordsetcancel"></a><a name="cancel"></a>CRecordset::Zrušit

Požaduje, aby zdroj dat zrušil probíhající asynchronní operaci nebo proces z druhého vlákna.

```cpp
void Cancel();
```

### <a name="remarks"></a>Poznámky

Všimněte si, že třídy Knihovny MFC ODBC již nepoužívají asynchronní zpracování. Chcete-li provést asychronní operaci, musíte přímo `SQLSetConnectOption`volat funkci ROZHRANÍ API ROZHRANÍ ODBC . Další informace naleznete v tématu "Provádění funkcí asynchronně" v *průvodci programátorem sady ODBC SDK*.

## <a name="crecordsetcancelupdate"></a><a name="cancelupdate"></a>CRecordset::Zrušitaktualizaci

Zruší všechny čekající aktualizace způsobené operací [Upravit](#edit) nebo [PřidatNový](#addnew) [před](#update) update je volána.

```cpp
void CancelUpdate();
```

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Tato členská funkce není použitelná u sad záznamů, které používají `Edit`hromadné `AddNew`načítání `Update`řádků, protože tyto sady záznamů nemohou volat , , nebo . Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

Pokud je povolena automatická `CancelUpdate` kontrola znečištěného pole, obnoví `Edit` `AddNew` členské proměnné na hodnoty, které měly před nebo byly volány; v opačném případě zůstanou změny hodnoty zachovány. Ve výchozím nastavení je při otevření sady záznamů povoleno automatické kontrolu polí. Chcete-li jej zakázat, musíte zadat `CRecordset::noDirtyFieldCheck` parametr *dwOptions* členské funkce [Otevřít.](#open)

Další informace o aktualizaci dat naleznete v článku [Sada záznamů: Přidání, aktualizace a odstranění záznamů (ODBC).](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)

## <a name="crecordsetcanrestart"></a><a name="canrestart"></a>CRecordset::CanRestart

Určuje, zda sada záznamů umožňuje restartování dotazu (aktualizovat jeho `Requery` záznamy) voláním členské funkce.

```
BOOL CanRestart() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je povolen requery; jinak 0.

## <a name="crecordsetcanscroll"></a><a name="canscroll"></a>CRecordset::CanScroll

Určuje, zda sada záznamů umožňuje posouvání.

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud sada záznamů umožňuje posouvání; jinak 0.

### <a name="remarks"></a>Poznámky

Další informace o posouvání naleznete v článku [Sada záznamů: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="crecordsetcantransact"></a><a name="cantransact"></a>CRecordset::CanTransact

Určuje, zda sada záznamů umožňuje transakce.

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud sada záznamů povoluje transakce; jinak 0.

### <a name="remarks"></a>Poznámky

Další informace naleznete v článku [Transakce (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="crecordsetcanupdate"></a><a name="canupdate"></a>CRecordset::CanUpdate

Určuje, zda lze sadu záznamů aktualizovat.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud lze aktualizovat sadu záznamů; jinak 0.

### <a name="remarks"></a>Poznámky

Sada záznamů může být jen pro čtení, pokud je základní `CRecordset::readOnly` zdroj dat jen pro čtení nebo pokud jste při otevření sady záznamů zadali parametr *dwOptions.*

## <a name="crecordsetcheckrowseterror"></a><a name="checkrowseterror"></a>CRecordset::CheckRowsetError

Volána ke zpracování chyb generovaných během načítání záznamu.

```
virtual void CheckRowsetError(RETCODE nRetCode);
```

### <a name="parameters"></a>Parametry

*nRetCode*<br/>
Návratový kód funkce ROZHRANÍ API ROZHRANÍ ODBC. Podrobnosti naleznete v tématu Poznámky.

### <a name="remarks"></a>Poznámky

Tato virtuální členská funkce zpracovává chyby, ke kterým dochází při načítání záznamů a je užitečná při hromadném načítání řádků. Možná budete chtít zvážit `CheckRowsetError` přepsání implementovat vlastní zpracování chyb.

`CheckRowsetError`je volána automaticky v operaci `Open`navigace `Requery`kurzorem, například , nebo jakékoli `Move` operaci. Je předána vrácená hodnota funkce `SQLExtendedFetch`ROZHRANÍ API ROZHRANÍ ODBC . V následující tabulce jsou uvedeny možné hodnoty parametru *nRetCode.*

|nRetCode|Popis|
|--------------|-----------------|
|SQL_SUCCESS|Funkce byla úspěšně dokončena. nejsou k dispozici žádné další informace.|
|Sql_success_with_info|Funkce byla úspěšně dokončena, pravděpodobně s nezávažnou chybou. Další informace lze získat `SQLError`na telefonním čísle .|
|SQL_NO_DATA_FOUND|Všechny řádky ze sady výsledků byly načteny.|
|Sql_error|Funkce se nezdařila. Další informace lze získat `SQLError`na telefonním čísle .|
|SQL_INVALID_HANDLE|Funkce se nezdařila z důvodu neplatného popisovače prostředí, popisovače připojení nebo popisovače příkazu. To znamená chybu programování. Od společnosti nejsou `SQLError`k dispozici žádné další informace.|
|SQL_STILL_EXECUTING|Funkce, která byla spuštěna asynchronně je stále spuštěna. Všimněte si, že ve výchozím nastavení `CheckRowsetError`knihovna MFC nikdy nepředá tuto hodnotu ; Knihovna MFC `SQLExtendedFetch` bude pokračovat v volání, dokud již nevrátí SQL_STILL_EXECUTING.|

Další informace `SQLError`o aplikaci naleznete v souboru Windows SDK. Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

## <a name="crecordsetclose"></a><a name="close"></a>CRecordset::Zavřít

Zavře sadu záznamů.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

ODBC HSTMT a všechny paměti rámce přidělené pro sadu záznamů jsou přiděleny. Obvykle po `Close`volání odstraníte objekt sady záznamů jazyka C++, pokud byl přidělen s **novým**.

Po volání `Open` `Close`můžete volat znovu . To umožňuje znovu použít objekt sady záznamů. Alternativou je `Requery`volání .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#17](../../mfc/codesnippet/cpp/crecordset-class_1.cpp)]

## <a name="crecordsetcrecordset"></a><a name="crecordset"></a>CRecordset::CRecordset

Vytvoří `CRecordset` objekt.

```
CRecordset(CDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>Parametry

*pDatabáze*<br/>
Obsahuje ukazatel na `CDatabase` objekt nebo hodnotu NULL. Pokud není null `CDatabase` a `Open` členská funkce objektu nebyla volána pro připojení ke zdroji dat, sada `Open` záznamů se pokusí otevřít za vás během vlastního volání. Pokud předáte hodnotu `CDatabase` NULL, objekt je vytvořen a připojen za vás pomocí informací o zdroji dat, které jste zadali při odvození třídy sady záznamů pomocí ClassWizard.

### <a name="remarks"></a>Poznámky

Můžete použít `CRecordset` přímo nebo odvodit `CRecordset`třídu specifickou pro aplikaci z aplikace . Pomocí Průvodce classwizard můžete odvodit třídy sady záznamů.

> [!NOTE]
> Odvozená třída *musí* dodávat vlastní konstruktor. V konstruktoru odvozené třídy, volání `CRecordset::CRecordset`konstruktoru , předávání příslušné parametry spolu s ním.

Předejte null konstruktoru sady `CDatabase` záznamů, aby byl objekt automaticky vytvořen a připojen. Toto je užitečný těsnopis, který `CDatabase` nevyžaduje vytvoření a připojení objektu před sestavením sady záznamů.

### <a name="example"></a>Příklad

Další informace naleznete v článku [Sada záznamů: Deklarování třídy pro tabulku (ODBC).](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)

## <a name="crecordsetdelete"></a><a name="delete"></a>CRecordset::Delete

Odstraní aktuální záznam.

```
virtual void Delete();
```

### <a name="remarks"></a>Poznámky

Po úspěšném odstranění jsou datové členy sady záznamů nastaveny na hodnotu Null a `Move` je nutné explicitně zavolat jednu z funkcí, aby bylo možné přesunout odstraněný záznam. Jakmile se přesunete mimo odstraněný záznam, není možné se k němu vrátit. Pokud zdroj dat podporuje transakce, můžete `Delete` volat část transakce. Další informace naleznete v článku [Transakce (ODBC)](../../data/odbc/transaction-odbc.md).

> [!NOTE]
> Pokud jste implementovali hromadné načítání řádků, nelze volat `Delete`. Výsledkem bude neúspěšný kontrolní výraz. Přestože `CRecordset` třída neposkytuje mechanismus pro aktualizaci hromadných řádků dat, můžete zapisovat vlastní funkce pomocí funkce `SQLSetPos`ROZHRANÍ API ROZHRANÍ ODBC . Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

> [!CAUTION]
> Sada záznamů musí být aktualizovatelná a při volání `Delete`musí být v sadě záznamů platný aktuální záznam ; v opačném případě dojde k chybě. Pokud například odstraníte záznam, ale před dalším voláním `Delete` se `Delete` neposunete na nový záznam, vyvolá výjimku [CDBException](../../mfc/reference/cdbexception-class.md).

Na rozdíl od [AddNew](#addnew) `Delete` a [Upravit](#edit), volání není následuje volání [Update](#update). Pokud `Delete` volání selže, datové členy pole zůstanou beze změny.

### <a name="example"></a>Příklad

Tento příklad ukazuje sadu záznamů vytvořenou v rámci funkce. Příklad předpokládá existenci `m_dbCust`, členské proměnné typu, `CDatabase` který je již připojen ke zdroji dat.

[!code-cpp[NVC_MFCDatabase#18](../../mfc/codesnippet/cpp/crecordset-class_2.cpp)]

## <a name="crecordsetdobulkfieldexchange"></a><a name="dobulkfieldexchange"></a>CRecordset::DoBulkFieldExchange

Nazývá se výměna hromadných řádků dat ze zdroje dat do sady záznamů. Implementuje výměnu polí hromadného záznamu (Bulk RFX).

```
virtual void DoBulkFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Ukazatel na objekt [CFieldExchange.](../../mfc/reference/cfieldexchange-class.md) Rámec již nastavil tento objekt k určení kontextu pro operaci výměny v terénu.

### <a name="remarks"></a>Poznámky

Při hromadné načítání řádků je implementováno, rozhraní framework volá tuto členská funkci k automatickému přenosu dat ze zdroje dat do objektu sady záznamů. `DoBulkFieldExchange`také váže členy dat parametru, pokud existuje, na zástupné symboly parametrů v řetězci příkazu SQL pro výběr sady záznamů.

Pokud hromadné načítání řádků není implementováno, rozhraní framework volání [DoFieldExchange](#dofieldexchange). Chcete-li implementovat hromadné načítání `CRecordset::useMultiRowFetch` řádků, musíte zadat možnost parametru *dwOptions* v členské funkci [Otevřít.](#open)

> [!NOTE]
> `DoBulkFieldExchange`je k dispozici pouze v případě, `CRecordset`že používáte třídu odvozenou z aplikace . Pokud jste vytvořili objekt sady `CRecordset`záznamů přímo z aplikace , musíte volat člennou funkci [GetFieldValue,](#getfieldvalue) abyste načetli data.

Výměna pole hromadného záznamu (Bulk RFX) je podobná výměně pole záznamu (RFX). Data jsou automaticky přenesena ze zdroje dat do objektu sady záznamů. Nelze však `AddNew`volat `Edit` `Delete`, `Update` , , nebo přenést změny zpět do zdroje dat. Třída `CRecordset` v současné době neposkytuje mechanismus pro aktualizaci hromadných řádků dat; můžete však napsat vlastní funkce pomocí funkce `SQLSetPos`ROZHRANÍ API ROZHRANÍ ODBC .

Všimněte si, že ClassWizard nepodporuje hromadné výměny pole záznamu; proto je nutné `DoBulkFieldExchange` přepsat ručně zápisem volání funkce hromadné RFX. Další informace o těchto funkcích naleznete v tématu [Funkce výměny polí záznamu](../../mfc/reference/record-field-exchange-functions.md).

Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) Související informace naleznete v článku [Výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md).

## <a name="crecordsetdofieldexchange"></a><a name="dofieldexchange"></a>CRecordset::DoFieldExchange

Nazývá se výměna dat (v obou směrech) mezi datovými členy pole sady záznamů a odpovídajícím záznamem ve zdroji dat. Implementuje výměnu pole záznamu (RFX).

```
virtual void DoFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Ukazatel na objekt [CFieldExchange.](../../mfc/reference/cfieldexchange-class.md) Rámec již nastavil tento objekt k určení kontextu pro operaci výměny v terénu.

### <a name="remarks"></a>Poznámky

Pokud není implementováno hromadné načítání řádků, rozhraní framework volá tuto členská funkci k automatické výměně dat mezi datovými členy pole objektu sady záznamů a odpovídajícími sloupci aktuálního záznamu ve zdroji dat. `DoFieldExchange`také váže členy dat parametru, pokud existuje, na zástupné symboly parametrů v řetězci příkazu SQL pro výběr sady záznamů.

Pokud je implementováno hromadné načítání řádků, framework volá [DoBulkFieldExchange](#dobulkfieldexchange). Chcete-li implementovat hromadné načítání `CRecordset::useMultiRowFetch` řádků, musíte zadat možnost parametru *dwOptions* v členské funkci [Otevřít.](#open)

> [!NOTE]
> `DoFieldExchange`je k dispozici pouze v případě, `CRecordset`že používáte třídu odvozenou z aplikace . Pokud jste vytvořili objekt sady `CRecordset`záznamů přímo z aplikace , musíte volat člennou funkci [GetFieldValue,](#getfieldvalue) abyste načetli data.

Výměna dat pole, nazývaná výměna pole záznamu (RFX), funguje v obou směrech: od datových členů pole objektu sady záznamů až po pole záznamu ve zdroji dat a ze záznamu ve zdroji dat k objektu sady záznamů.

Jedinou akcí, kterou je `DoFieldExchange` třeba normálně provést k implementaci pro odvozenou třídu sady záznamů, je vytvoření třídy pomocí Průvodce třídou a určení názvů a datových typů datových členů pole. Můžete také přidat kód, co ClassWizard zapíše určit členy dat parametru nebo řešit všechny sloupce, které svázat dynamicky. Další informace naleznete v článku [Sada záznamů: Dynamicky vazebné datové sloupce (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Když deklarujete třídu odvozené sady záznamů pomocí `DoFieldExchange` Průvodce třídou, průvodce za píše přepsání za vás, které se podobá následujícímu příkladu:

[!code-cpp[NVC_MFCDatabase#19](../../mfc/codesnippet/cpp/crecordset-class_3.cpp)]

Další informace o funkcích RFX naleznete v tématu [Funkce výměny polí záznamu](../../mfc/reference/record-field-exchange-functions.md).

Další příklady a `DoFieldExchange`podrobnosti o najdete v článku [Záznam pole Exchange: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Obecné informace o RFX naleznete v článku [Výměna pole záznamu](../../data/odbc/record-field-exchange-rfx.md).

## <a name="crecordsetedit"></a><a name="edit"></a>CRecordset::Upravit

Umožňuje změny aktuálního záznamu.

```
virtual void Edit();
```

### <a name="remarks"></a>Poznámky

Po volání `Edit`můžete změnit datové členy pole přímým resetováním jejich hodnot. Operace je dokončena, když následně zavoláte [členská](#update) funkci Update a uložíte změny do zdroje dat.

> [!NOTE]
> Pokud jste implementovali hromadné načítání řádků, nelze volat `Edit`. Výsledkem bude neúspěšný kontrolní výraz. Přestože `CRecordset` třída neposkytuje mechanismus pro aktualizaci hromadných řádků dat, můžete zapisovat vlastní funkce pomocí funkce `SQLSetPos`ROZHRANÍ API ROZHRANÍ ODBC . Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

`Edit`uloží hodnoty datových členů sady záznamů. Pokud zavoláte `Edit`, provedete `Edit` změny a pak zavoláte znovu, hodnoty záznamu `Edit` se obnoví na hodnoty, které byly před prvním voláním.

V některých případech můžete chtít aktualizovat sloupec tím, že je Null (obsahující žádná data). Chcete-li tak učinit, volání [SetFieldNull](#setfieldnull) s parametrem TRUE označit pole Null; To také způsobí, že sloupec aktualizovat. Pokud chcete, aby pole bylo zapsáno do zdroje dat, i když se jeho hodnota nezměnila, zavolejte [SetFieldDirty](#setfielddirty) s parametrem TRUE. To funguje i v případě, že pole mělo hodnotu Null.

Pokud zdroj dat podporuje transakce, můžete `Edit` volat část transakce. Všimněte si, že byste měli volat `Edit` [CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) před voláním a po otevření sady záznamů. Všimněte si také, že volání [CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) není náhradou za volání `Update` k dokončení `Edit` operace. Další informace o transakcích naleznete v tématu [cdatabase](../../mfc/reference/cdatabase-class.md)třídy .

V závislosti na aktuálním režimu uzamčení `Edit` může být `Update` aktualizovaný záznam uzamčen, dokud nezavoláte `Edit` nebo nepřejdete na jiný záznam, nebo může být uzamčen pouze během hovoru. Režim zamykání můžete změnit pomocí [režimu SetLockingMode](#setlockingmode).

Předchozí hodnota aktuálního záznamu bude obnovena, pokud před `Update`voláním přejdete na nový záznam . A `CDBException` je vyvolána, `Edit` pokud voláte sadu záznamů, které nelze aktualizovat, nebo pokud neexistuje žádný aktuální záznam.

Další informace naleznete v článcích [Transakce (ODBC)](../../data/odbc/transaction-odbc.md) a [Recordset: Uzamčení záznamů (ODBC).](../../data/odbc/recordset-locking-records-odbc.md)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#20](../../mfc/codesnippet/cpp/crecordset-class_4.cpp)]

## <a name="crecordsetflushresultset"></a><a name="flushresultset"></a>CRecordset::FlushResultSet

Načte další sadu výsledků předdefinovaného dotazu (uložená procedura), pokud existuje více sad výsledků.

```
BOOL FlushResultSet();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je třeba načíst více sad výsledků; jinak 0.

### <a name="remarks"></a>Poznámky

Měli byste `FlushResultSet` volat pouze v případě, že jste zcela dokončeni s kurzorem na aktuální sadu výsledků. Všimněte si, že při načtení další sadu výsledků voláním `FlushResultSet`, kurzor není platný pro tuto sadu výsledků; po volání `FlushResultSet`byste měli zavolat člennou funkci [MoveNext](#movenext) .

Pokud předdefinovaný dotaz používá výstupní parametr nebo parametry input/output, musíte volat, `FlushResultSet` dokud nevrátí `FALSE` (hodnota 0), abyste získali tyto hodnoty parametrů.

`FlushResultSet`volá funkci `SQLMoreResults`ROZHRANÍ API ROZHRANÍ ODBC . Pokud `SQLMoreResults` vrátí SQL_ERROR nebo `FlushResultSet` SQL_INVALID_HANDLE, pak vyvolá výjimku. Další informace `SQLMoreResults`o aplikaci naleznete v souboru Windows SDK.

Uložená procedura musí mít vázaná `FlushResultSet`pole, pokud chcete volat .

### <a name="example"></a>Příklad

Následující kód předpokládá, `COutParamRecordset` že `CRecordset`je odvozený objekt založený na předdefinovaný dotaz s vstupní parametr a výstupní parametr a mají více sad výsledků. Všimněte si struktury [přepsání DoFieldExchange.](#dofieldexchange)

[!code-cpp[NVC_MFCDatabase#21](../../mfc/codesnippet/cpp/crecordset-class_5.cpp)]

[!code-cpp[NVC_MFCDatabase#22](../../mfc/codesnippet/cpp/crecordset-class_6.cpp)]

## <a name="crecordsetgetbookmark"></a><a name="getbookmark"></a>CRecordset::GetBookmark

Získá hodnotu záložky pro aktuální záznam.

```cpp
void GetBookmark(CDBVariant& varBookmark);
```

### <a name="parameters"></a>Parametry

*varBookmark*<br/>
Odkaz na objekt [CDBVariant](../../mfc/reference/cdbvariant-class.md) představující záložku na aktuálním záznamu.

### <a name="remarks"></a>Poznámky

Chcete-li zjistit, zda jsou záložky v sadě záznamů podporovány, zavolejte [CanBookmark](#canbookmark). Chcete-li záložky zpřístupnit, pokud jsou `CRecordset::useBookmarks` podporovány, musíte nastavit možnost v parametru *dwOptions* členské funkce [Otevřít.](#open)

> [!NOTE]
> Pokud záložky nejsou podporovány `GetBookmark` nebo nejsou k dispozici, volání bude mít za následek vyvolání výjimky. Záložky nejsou podporovány v sadách záznamů pouze pro předávání.

`GetBookmark`přiřadí `CDBVariant` objektu hodnotu záložky pro aktuální záznam. Chcete-li se k tomuto záznamu kdykoli vrátit po přesunutí na `CDBVariant` jiný záznam, zavolejte [SetBookmark](#setbookmark) s odpovídajícím objektem.

> [!NOTE]
> Po určité operace sady záznamů již nemusí být záložky platné. Pokud například zavoláte `GetBookmark` `Requery`následovaný písmenem , nebude pravděpodobně možné `SetBookmark`vrátit se k záznamu pomocí . Volání [CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) zkontrolovat, zda `SetBookmark`můžete bezpečně volat .

Další informace o záložkách a navigaci v sadě záznamů naleznete v článcích [Sada záznamů: Záložky a absolutní pozice (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) a [Sada záznamů: Posouvání (ODBC).](../../data/odbc/recordset-scrolling-odbc.md)

## <a name="crecordsetgetdefaultconnect"></a><a name="getdefaultconnect"></a>CRecordset::GetDefaultConnect

Volána získat výchozí připojovací řetězec.

```
virtual CString GetDefaultConnect();
```

### <a name="return-value"></a>Návratová hodnota

A, `CString` který obsahuje výchozí připojovací řetězec.

### <a name="remarks"></a>Poznámky

Rozhraní Framework volá tuto členskou funkci, aby získalo výchozí připojovací řetězec pro zdroj dat, na kterém je založena sada záznamů. ClassWizard implementuje tuto funkci za vás identifikací stejného zdroje dat, který používáte v ClassWizard získat informace o tabulkách a sloupcích. Pravděpodobně zjistíte, že je vhodné spoléhat se na toto výchozí připojení při vývoji aplikace. Výchozí připojení však nemusí být vhodné pro uživatele aplikace. Pokud tomu tak je, měli byste tuto funkci znovu implementovat a zahodit verzi ClassWizard. Další informace o připojovacích řetězcích naleznete v článku [Zdroj dat (ODBC).](../../data/odbc/data-source-odbc.md)

## <a name="crecordsetgetdefaultsql"></a><a name="getdefaultsql"></a>CRecordset::GetDefaultSQL

Volána k získání výchozího řetězce SQL ke spuštění.

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>Návratová hodnota

A, `CString` který obsahuje výchozí příkaz SQL.

### <a name="remarks"></a>Poznámky

Rozhraní Framework volá tuto členskou funkci, aby získalo výchozí příkaz SQL, na kterém je založena sada záznamů. Může se jedná o název tabulky nebo příkaz SQL **SELECT.**

Nepřímo definujete výchozí příkaz SQL deklarováním třídy sady záznamů pomocí Průvodce řazením záznamů a ClassWizard provede tento úkol za vás.

Pokud potřebujete řetězec příkazu SQL pro `GetSQL`vlastní použití, call , který vrátí příkaz SQL použitý k výběru záznamů sady záznamů při jeho otevření. Výchozí řetězec SQL můžete upravit v přepsání `GetDefaultSQL`třídy aplikace . Můžete například zadat volání předdefinovaného dotazu pomocí příkazu **CALL.** (Všimněte si však, `GetDefaultSQL`že pokud upravujete , je také nutné upravit tak, `m_nFields` aby odpovídaly počtu sloupců ve zdroji dat.)

Další informace naleznete v článku [Sada záznamů: Deklarování třídy pro tabulku (ODBC).](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)

> [!CAUTION]
> Název tabulky bude prázdný, pokud rozhraní framework nemohlo identifikovat název tabulky, pokud bylo zadáno více názvů tabulek nebo pokud příkaz **CALL** nelze interpretovat. Všimněte si, že při použití **příkazu CALL** nesmíte vložit mezery mezi složené závorky a **call** klíčové slovo, ani byste neměli vkládat mezery před složené složenou závorku nebo před klíčové slovo **SELECT** v příkazu **SELECT.**

## <a name="crecordsetgetfieldvalue"></a><a name="getfieldvalue"></a>CRecordset::GetFieldValue

Načte data polí v aktuálním záznamu.

```cpp
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

*název lpsz*<br/>
Název pole.

*varValu*e Odkaz na objekt [CDBVariant,](../../mfc/reference/cdbvariant-class.md) který uloží hodnotu pole.

*nTyp pole*<br/>
Datový typ odbc C pole. Použití výchozí hodnoty DEFAULT_FIELD_TYPE `GetFieldValue` vynutí určení datového typu C z datového typu SQL na základě následující tabulky. V opačném případě můžete zadat datový typ přímo nebo zvolit kompatibilní datový typ; můžete například uložit libovolný datový typ do SQL_C_CHAR.

|Datový typ C|Datový typ SQL|
|-----------------|-------------------|
|SQL_C_BIT|SQL_BIT|
|SQL_C_UTINYINT|SQL_TINYINT|
|SQL_C_SSHORT|SQL_SMALLINT|
|SQL_C_SLONG|SQL_INTEGER|
|SQL_C_FLOAT|SQL_REAL|
|SQL_C_DOUBLE|SQL_FLOATSQL_DOUBLE|
|SQL_C_TIMESTAMP|SQL_DATESQL_TIMESQL_TIMESTAMP|
|Sql_c_char|SQL_NUMERICSQL_DECIMALSQL_BIGINTSQL_CHARSQL_VARCHARSQL_LONGVARCHAR|
|Sql_c_binary|SQL_BINARYSQL_VARBINARYSQL_LONGVARBINARY|

Další informace o datových typech ROZHRANÍ ODBC naleznete v tématech Datové typy SQL a "Datové typy Jazyka C" v dodatku D sady Windows SDK.

*nIndex*<br/>
Nulový index pole.

*strValue*<br/>
Odkaz na [cstring](../../atl-mfc-shared/reference/cstringt-class.md) objekt, který bude ukládat hodnotu pole převedenou na text, bez ohledu na datový typ pole.

### <a name="remarks"></a>Poznámky

Pole můžete vyhledat podle názvu nebo indexu. Hodnotu pole můžete uložit `CDBVariant` do objektu nebo objektu. `CString`

Pokud jste implementovali hromadné načítání řádků, aktuální záznam je vždy umístěn na první záznam v sadě řádků. Chcete-li použít `GetFieldValue` na záznam v rámci dané sady řádků, musíte nejprve volat [SetRowsetCursorPosition](#setrowsetcursorposition) člennou funkci přesunout kurzor na požadovaný řádek v rámci této sady řádků. Tak `GetFieldValue` zavolejte pro ten řádek. Chcete-li implementovat hromadné načítání `CRecordset::useMultiRowFetch` řádků, musíte zadat možnost parametru *dwOptions* v členské funkci [Otevřít.](#open)

Můžete použít `GetFieldValue` k dynamicky načítat pole za běhu, nikoli staticky vazby je v době návrhu. Pokud jste například deklarovali objekt `CRecordset`sady záznamů `GetFieldValue` přímo z aplikace , musíte použít k načtení dat pole. záznam pole exchange (RFX), nebo hromadné záznam pole exchange (Bulk RFX), není implementována.

> [!NOTE]
> Pokud deklarujete objekt sady `CRecordset`záznamů bez odvození z aplikace , nemáte načtenou knihovnu kurzorů ROZHRANÍ ODBC. Knihovna kurzorů vyžaduje, aby sada záznamů měla alespoň jeden vázaný sloupec; však při `CRecordset` použití přímo, žádný ze sloupců jsou vázány. Členské funkce [CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) a [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) ovládací prvek, zda bude načtena knihovna kurzoru.

`GetFieldValue`volá funkci `SQLGetData`ROZHRANÍ API ROZHRANÍ ODBC . Pokud ovladač výstupy hodnota SQL_NO_TOTAL pro skutečnou délku hodnoty pole, `GetFieldValue` vyvolá výjimku. Další informace `SQLGetData`o aplikaci naleznete v souboru Windows SDK.

### <a name="example"></a>Příklad

Následující ukázkový kód ilustruje `GetFieldValue` volání objektu sady `CRecordset`záznamů deklarovaného přímo z .

[!code-cpp[NVC_MFCDatabase#23](../../mfc/codesnippet/cpp/crecordset-class_7.cpp)]

> [!NOTE]
> Na rozdíl od `CDaoRecordset`třídy DAO `CRecordset` nemá členská `SetFieldValue` funkce. Pokud vytvoříte objekt `CRecordset`přímo z aplikace , je efektivně jen pro čtení.

Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

## <a name="crecordsetgetodbcfieldcount"></a><a name="getodbcfieldcount"></a>CRecordset::GetODBCFieldCount

Načte celkový počet polí v objektu sady záznamů.

```
short GetODBCFieldCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet polí v sadě záznamů.

### <a name="remarks"></a>Poznámky

Další informace o vytváření sad záznamů naleznete v článku [Sada záznamů: Vytváření a zavírání sad záznamů (ODBC).](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)

## <a name="crecordsetgetodbcfieldinfo"></a><a name="getodbcfieldinfo"></a>CRecordset::GetODBCFieldInfo

Získá informace o polích v sadě záznamů.

```cpp
void GetODBCFieldInfo(
    LPCTSTR lpszName,
    CODBCFieldInfo& fieldinfo);

void GetODBCFieldInfo(
    short nIndex,
    CODBCFieldInfo& fieldinfo);
```

### <a name="parameters"></a>Parametry

*název lpsz*<br/>
Název pole.

*Fieldinfo*<br/>
Odkaz na `CODBCFieldInfo` strukturu.

*nIndex*<br/>
Nulový index pole.

### <a name="remarks"></a>Poznámky

Jedna verze funkce umožňuje vyhledat pole podle názvu. Druhá verze umožňuje vyhledat pole podle indexu.

Popis vrácených informací naleznete ve struktuře [CODBCFieldInfo.](../../mfc/reference/codbcfieldinfo-structure.md)

Další informace o vytváření sad záznamů naleznete v článku [Sada záznamů: Vytváření a zavírání sad záznamů (ODBC).](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)

## <a name="crecordsetgetrecordcount"></a><a name="getrecordcount"></a>CRecordset::GetRecordCount

Určuje velikost sady záznamů.

```
long GetRecordCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet záznamů v sadě záznamů; 0, pokud sada záznamů neobsahuje žádné záznamy; nebo -1, pokud nelze určit počet záznamů.

### <a name="remarks"></a>Poznámky

> [!CAUTION]
> Počet záznamů je udržován jako "značka vysoké hladiny vody", což je nejvyšší číslovaný záznam, který je dosud považován za uživatele, který prochází záznamy. Celkový počet záznamů je znám až poté, co uživatel přešel za poslední záznam. Z důvodů výkonu počet není aktualizován `MoveLast`při volání . Chcete-li záznamy spočítat sami, opakovaně volejte, `MoveNext` dokud `IsEOF` nevrátí nenulovou hodnotu. Přidání záznamu `CRecordset:AddNew` přes `Update` a zvyšuje počet; odstranění záznamu pomocí `CRecordset::Delete` sníží počet.

## <a name="crecordsetgetrowsetsize"></a><a name="getrowsetsize"></a>CRecordset::GetRowsetSize

Získá aktuální nastavení pro počet řádků, které chcete načíst během daného načtení.

```
DWORD GetRowsetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet řádků načíst během dané načtení.

### <a name="remarks"></a>Poznámky

Pokud používáte hromadné načítání řádků, je výchozí velikost sady řádků při otevření sady záznamů 25; jinak je 1.

Chcete-li implementovat hromadné načítání `CRecordset::useMultiRowFetch` řádků, musíte zadat možnost v parametru *dwOptions* členské funkce [Otevřít.](#open) Chcete-li změnit nastavení velikosti sady řádků, zavolejte [SetRowsetSize](#setrowsetsize).

Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

## <a name="crecordsetgetrowsfetched"></a><a name="getrowsfetched"></a>CRecordset::GetRowsFetched

Určuje, kolik záznamů bylo skutečně načteno po načtení.

```
DWORD GetRowsFetched() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet řádků načtených ze zdroje dat po daném načtení.

### <a name="remarks"></a>Poznámky

To je užitečné, když jste implementovali hromadné načítání řádků. Velikost sady řádků obvykle označuje, kolik řádků bude načteno z načtení; celkový počet řádků v sadě záznamů však také ovlivňuje, kolik řádků bude načteno v sadě řádků. Pokud má například sada záznamů 10 záznamů s nastavením velikosti sady řádků 4, bude opakování sady záznamů voláním `MoveNext` mít za následek, že poslední sada řádků bude mít pouze 2 záznamy.

Chcete-li implementovat hromadné načítání `CRecordset::useMultiRowFetch` řádků, musíte zadat možnost v parametru *dwOptions* členské funkce [Otevřít.](#open) Chcete-li určit velikost sady řádků, zavolejte [SetRowsetSize](#setrowsetsize).

Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#24](../../mfc/codesnippet/cpp/crecordset-class_8.cpp)]

## <a name="crecordsetgetrowstatus"></a><a name="getrowstatus"></a>CRecordset::GetRowStatus

Získá stav pro řádek v aktuální sadě řádků.

```
WORD GetRowStatus(WORD wRow) const;
```

### <a name="parameters"></a>Parametry

*wŘádek*<br/>
Jednomístná pozice řádku v aktuální sadě řádků. Tato hodnota může být v rozsahu od 1 do velikosti sady řádků.

### <a name="return-value"></a>Návratová hodnota

Hodnota stavu řádku. Podrobnosti naleznete v tématu Poznámky.

### <a name="remarks"></a>Poznámky

`GetRowStatus`vrátí hodnotu, která označuje buď všechny změny stavu řádku od posledního načtení ze zdroje dat, nebo že nebyl načten žádný řádek odpovídající *wRow.* V následující tabulce jsou uvedeny možné vrácené hodnoty.

|Hodnota stavu|Popis|
|------------------|-----------------|
|SQL_ROW_SUCCESS|Řádek se nezmění.|
|SQL_ROW_UPDATED|Řádek byl aktualizován.|
|SQL_ROW_DELETED|Řádek byl odstraněn.|
|SQL_ROW_ADDED|Řádek byl přidán.|
|SQL_ROW_ERROR|Řádek je nenahraditelný z důvodu chyby.|
|SQL_ROW_NOROW|Neexistuje žádný řádek, který odpovídá *wRow*.|

Další informace naleznete v části `SQLExtendedFetch` Funkce rozhraní API ROZHRANÍ ODBC v sadě Windows SDK.

## <a name="crecordsetgetstatus"></a><a name="getstatus"></a>CRecordset::GetStatus

Určuje index aktuálního záznamu v sadě záznamů a zda byl zaznamenán poslední záznam.

```cpp
void GetStatus(CRecordsetStatus& rStatus) const;
```

### <a name="parameters"></a>Parametry

*rStav*<br/>
Odkaz na `CRecordsetStatus` objekt. Další informace naleznete v části Poznámky.

### <a name="remarks"></a>Poznámky

`CRecordset`pokusí sledovat index, ale za určitých okolností to nemusí být možné. Viz [GetRecordCount](#getrecordcount) pro vysvětlení.

Struktura `CRecordsetStatus` má následující tvar:

```cpp
struct CRecordsetStatus
{
    long m_lCurrentRecord;
    BOOL m_bRecordCountFinal;
};
```

Dva členové `CRecordsetStatus` mají následující významy:

- `m_lCurrentRecord`Obsahuje nulový index aktuálního záznamu v sadě záznamů, pokud je znám. Pokud index nelze určit, tento člen obsahuje AFX_CURRENT_RECORD_UNDEFINED (-2). Pokud `IsBOF` je TRUE (prázdná sada záznamů nebo `m_lCurrentRecord` pokus o posun před prvním záznamem), je nastavena na AFX_CURRENT_RECORD_BOF (-1). Pokud na první záznam, pak je nastavena na 0, druhý záznam 1, a tak dále.

- `m_bRecordCountFinal`Nenulová, pokud byl určen celkový počet záznamů v sadě záznamů. Obecně to musí být provedeno spuštěním na začátku `MoveNext` `IsEOF` sady záznamů a voláním, dokud nevrátí nenulovou hodnotu. Pokud je tento člen nula, `GetRecordCount`počet záznamů jako vrácený do , pokud ne -1, je pouze "horní mez" počet záznamů.

## <a name="crecordsetgetsql"></a><a name="getsql"></a>CRecordset::GetSQL

Volání této členské funkce získat příkaz SQL, který byl použit k výběru záznamů sady záznamů při jeho otevření.

```
const CString& GetSQL() const;
```

### <a name="return-value"></a>Návratová hodnota

**Const** odkaz na `CString` který obsahuje příkaz SQL.

### <a name="remarks"></a>Poznámky

To bude obecně sql **select** příkaz. Řetězec vrácený `GetSQL` je jen pro čtení.

Řetězec vrácený `GetSQL` podle se obvykle liší od libovolného řetězce, který jste předali `Open` sadě záznamů v parametru *lpszSQL* do členské funkce. Důvodem je, že sada záznamů vytvoří úplný příkaz `Open`SQL na základě toho, co jste předali `m_strFilter` `m_strSort` , co jste zadali pomocí ClassWizard, co jste zadali v a datových členech a všechny parametry, které jste zadali. Podrobnosti o tom, jak sada záznamů vytváří tento příkaz SQL, naleznete v článku [Sada záznamů: Jak sady záznamů vyberte záznamy (ODBC).](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)

> [!NOTE]
> Volání této členské funkce pouze po volání [Open](#open).

## <a name="crecordsetgettablename"></a><a name="gettablename"></a>CRecordset::GetTableName

Získá název tabulky SQL, na kterém je založen dotaz sady záznamů.

```
const CString& GetTableName() const;
```

### <a name="return-value"></a>Návratová hodnota

**Const** odkaz `CString` na, který obsahuje název tabulky, pokud je sada záznamů založena na tabulce; v opačném případě prázdný řetězec.

### <a name="remarks"></a>Poznámky

`GetTableName`je platný pouze v případě, že sada záznamů je založena na tabulce, nikoli spojení více tabulek nebo předdefinovaný dotaz (uložená procedura). Název je jen pro čtení.

> [!NOTE]
> Volání této členské funkce pouze po volání [Open](#open).

## <a name="crecordsetisbof"></a><a name="isbof"></a>CRecordset::IsBOF

Vrátí nenulovou hodnotu, pokud byla sada záznamů umístěna před prvním záznamem. Neexistuje žádný aktuální záznam.

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud sada záznamů neobsahuje žádné záznamy nebo pokud jste před prvním záznamem posunuli zpět; jinak 0.

### <a name="remarks"></a>Poznámky

Před přechodem ze záznamu na záznam zavolejte tuto členovou funkci a zjistěte, zda jste před prvním záznamem sady záznamů odešli. Můžete také `IsBOF` použít `IsEOF` spolu s určit, zda sada záznamů obsahuje nějaké záznamy nebo je prázdný. Ihned po `Open`volání vrátí sada záznamů `IsBOF` hodnotu nenulová. Když otevřete sadu záznamů, která má alespoň jeden záznam, `IsBOF` první záznam je aktuální záznam a vrátí hodnotu 0.

Pokud je první záznam aktuální mše a voláte `MovePrev`, `IsBOF` vrátí se následně nenulová. Pokud `IsBOF` vrátí nenulovou `MovePrev`a zavoláte , dojde k chybě. Pokud `IsBOF` vrátí nenulovou hodnotu, aktuální záznam není definován a každá akce, která vyžaduje aktuální záznam, bude mít za následek chybu.

### <a name="example"></a>Příklad

Tento příklad `IsBOF` `IsEOF` používá a zjistit limity sady záznamů jako kód posouvá sadu záznamů v obou směrech.

[!code-cpp[NVC_MFCDatabase#25](../../mfc/codesnippet/cpp/crecordset-class_9.cpp)]

## <a name="crecordsetisdeleted"></a><a name="isdeleted"></a>CRecordset::IsDeleted

Určuje, zda byl aktuální záznam odstraněn.

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je sada záznamů umístěna na odstraněný záznam; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud přejdete na `IsDeleted` záznam a vrátíte hodnotu TRUE (nenulová), musíte se před provedením jiných operací sady záznamů posunout na jiný záznam.

Výsledek `IsDeleted` závisí na mnoha faktorech, jako je typ sady záznamů, zda je sada `CRecordset::skipDeletedRecords` záznamů aktualizovatelná, zda jste při otevření sady záznamů zadali tuto možnost, zda ovladač zabalí odstraněné záznamy a zda je více uživatelů.

Další informace `CRecordset::skipDeletedRecords` o a balení ovladače naleznete v části [Otevřená](#open) členská funkce.

> [!NOTE]
> Pokud jste implementovali hromadné načítání řádků, `IsDeleted`neměli byste volat . Místo toho volejte člennou funkci [GetRowStatus.](#getrowstatus) Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

## <a name="crecordsetiseof"></a><a name="iseof"></a>CRecordset::IsEOF

Vrátí nenulovou hodnotu, pokud byla sada záznamů umístěna za posledním záznamem. Neexistuje žádný aktuální záznam.

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud sada záznamů neobsahuje žádné záznamy nebo pokud jste se posunuli za poslední záznam; jinak 0.

### <a name="remarks"></a>Poznámky

Volání této členské funkce při posouvání ze záznamu do záznamu zjistit, zda jste překročili poslední záznam sady záznamů. Můžete také `IsEOF` určit, zda sada záznamů obsahuje nějaké záznamy nebo je prázdná. Ihned po `Open`volání vrátí sada záznamů `IsEOF` hodnotu nenulová. Když otevřete sadu záznamů, která má alespoň jeden záznam, `IsEOF` první záznam je aktuální záznam a vrátí hodnotu 0.

Pokud je poslední záznam aktuálním `MoveNext`záznamem při volání , `IsEOF` vrátí se následně nenulová. Pokud `IsEOF` vrátí nenulovou `MoveNext`a zavoláte , dojde k chybě. Pokud `IsEOF` vrátí nenulovou hodnotu, aktuální záznam není definován a každá akce, která vyžaduje aktuální záznam, bude mít za následek chybu.

### <a name="example"></a>Příklad

Viz příklad pro [IsBOF](#isbof).

## <a name="crecordsetisfielddirty"></a><a name="isfielddirty"></a>CRecordset::IsFieldDirty

Určuje, zda byl zadaný datový člen pole změněn od [doby, kdy](#edit) byl volán příkaz Upravit nebo [Přidat nový.](#addnew)

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>Parametry

*Pv*<br/>
Ukazatel na člena dat pole, jehož stav chcete zkontrolovat, nebo NULL k určení, zda některé z polí jsou nečisté.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud se zadaný `AddNew` datový `Edit`člen pole změnil od volání nebo ; jinak 0.

### <a name="remarks"></a>Poznámky

Data ve všech datových členech `CRecordset` nefunkčních polí budou přenesena do záznamu ve zdroji dat při aktualizaci aktuálního `AddNew`záznamu voláním členské funkce [Update](#update) (po volání `Edit` nebo ).

> [!NOTE]
> Tato členská funkce není použitelná u sad záznamů, které používají hromadné načítání řádků. Pokud jste implementovali hromadné načítání `IsFieldDirty` řádků, vrátí vždy FALSE a bude mít za následek kontrolní výraz se nezdařilo. Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

Volání `IsFieldDirty` obnoví účinky předchozích volání [SetFieldDirty,](#setfielddirty) protože dirty stav pole je přehodnocena. V `AddNew` případě, že se aktuální hodnota pole liší od pseudo nulové hodnoty, je stav pole nastaven nečistý. V `Edit` případě, že hodnota pole se liší od hodnoty uložené v mezipaměti, pak stav pole je nastaven dirty.

`IsFieldDirty`je implementována prostřednictvím [DoFieldExchange](#dofieldexchange).

Další informace o příznaku dirty naleznete v článku [Sada záznamů: Jak sady záznamů vyberte záznamy (ODBC).](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)

## <a name="crecordsetisfieldnull"></a><a name="isfieldnull"></a>Sada záznamů C::Hodnota IsFieldNull

Vrátí nenulovou hodnotu, pokud je zadané pole v aktuálním záznamu Null (nemá žádnou hodnotu).

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>Parametry

*Pv*<br/>
Ukazatel na datového člena pole, jehož stav chcete zkontrolovat, nebo NULL k určení, zda některé z polí jsou Null.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je zadaný datový člen pole označen jako Null; jinak 0.

### <a name="remarks"></a>Poznámky

Volání této členské funkce k určení, zda byl zadaný datový člen pole sady záznamů označen jako null. (V terminologii databáze null znamená "bez hodnoty" a není stejný jako NULL v jazyce C++.) Pokud je datový člen pole označen jako Null, je interpretován jako sloupec aktuálního záznamu, pro který neexistuje žádná hodnota.

> [!NOTE]
> Tato členská funkce není použitelná u sad záznamů, které používají hromadné načítání řádků. Pokud jste implementovali hromadné načítání `IsFieldNull` řádků, vrátí vždy FALSE a bude mít za následek kontrolní výraz se nezdařilo. Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

`IsFieldNull`je implementována prostřednictvím [DoFieldExchange](#dofieldexchange).

## <a name="crecordsetisfieldnullable"></a><a name="isfieldnullable"></a>CRecordset::IsFieldNullable

Vrátí nenulovou hodnotu, pokud lze zadané pole v aktuálním záznamu nastavit na hodnotu Null (bez hodnoty).

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>Parametry

*Pv*<br/>
Ukazatel na datového člena pole, jehož stav chcete zkontrolovat, nebo NULL k určení, zda lze některé z polí nastavit na hodnotu Null.

### <a name="remarks"></a>Poznámky

Volání této členské funkce k určení, zda je zadaný člen dat pole "nullable" (lze nastavit na hodnotu Null; C++ NULL není stejný jako Null, což v terminologii databáze znamená "bez hodnoty").

> [!NOTE]
> Pokud jste implementovali hromadné načítání řádků, nelze volat `IsFieldNullable`. Místo toho zavolejte člennou funkci [GetODBCFieldInfo](#getodbcfieldinfo) a zjistěte, zda lze pole nastavit na hodnotu Null. Všimněte si, `GetODBCFieldInfo`že můžete vždy volat , bez ohledu na to, zda jste implementovali hromadné načítání řádků. Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

Pole, které nemůže být Null, musí mít hodnotu. Pokud se pokusíte nastavit takové pole na Hodnotu Null při přidávání nebo aktualizaci záznamu, zdroj dat odmítne přidání nebo aktualizaci a [Update](#update) vyvolá výjimku. K výjimce dochází `Update`při volání , nikoli při volání [SetFieldNull](#setfieldnull).

Použití null pro první argument funkce bude používat `outputColumn` funkci `param` pouze pro pole, nikoli pole. Například volání

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

nastaví `outputColumn` pouze pole na hodnotu NULL; `param` pole nebudou ovlivněna.

Chcete-li `param` pracovat na polích, musíte `param` zadat skutečnou adresu osoby, na které chcete pracovat, například:

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

To znamená, že `param` nelze nastavit všechna pole `outputColumn` na hodnotu NULL, stejně jako u polí.

`IsFieldNullable`je implementována prostřednictvím [DoFieldExchange](#dofieldexchange).

## <a name="crecordsetisopen"></a><a name="isopen"></a>CRecordset::IsOpen

Určuje, zda je sada záznamů již otevřena.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla dříve volána členská funkce objektu [Open](#open) nebo [Requery objektu](#requery) sady záznamů a sada záznamů nebyla uzavřena; jinak 0.

## <a name="crecordsetm_hstmt"></a><a name="m_hstmt"></a>CSada záznamů::m_hstmt

Obsahuje popisovač datové struktury příkazu ODBC typu HSTMT přidružené k sadě záznamů.

### <a name="remarks"></a>Poznámky

Každý dotaz ke zdroji dat ODBC je přidružen k HSTMT.

> [!CAUTION]
> Nepoužívejte `m_hstmt` před [otevřením](#open) byl volán.

Za normálních okolností není nutné přistupovat k HSTMT přímo, ale budete potřebovat pro přímé provádění příkazů SQL. Členská `ExecuteSQL` funkce `CDatabase` třídy poskytuje `m_hstmt`příklad použití .

## <a name="crecordsetm_nfields"></a><a name="m_nfields"></a>CRecordset::m_nFields

Obsahuje počet datových členů pole ve třídě sady záznamů; počet sloupců vybraných sadou záznamů ze zdroje dat.

### <a name="remarks"></a>Poznámky

Konstruktor pro třídu sady záznamů `m_nFields` musí inicializovat se správným číslem. Pokud jste neimplementovali hromadné načítání řádků, ClassWizard zapíše tuto inicializaci za vás, když ji použijete k deklarování třídy sady záznamů. Můžete také napsat ručně.

Rozhraní Framework používá toto číslo ke správě interakce mezi datovými členy pole a odpovídajícími sloupci aktuálního záznamu ve zdroji dat.

> [!CAUTION]
> Toto číslo musí odpovídat počtu "výstupních sloupců" registrovaných v `DoFieldExchange` nebo `DoBulkFieldExchange` po volání [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) s parametrem `CFieldExchange::outputColumn`.

Sloupce můžete svázat dynamicky, jak je vysvětleno v článku "Sada záznamů: Dynamicky vazebné datové sloupce". Pokud tak učiníte, je nutné `m_nFields` zvýšit počet v odrážet počet RFX `DoFieldExchange` nebo `DoBulkFieldExchange` hromadné RFX volání funkce ve vaší nebo členské funkce pro dynamicky vázané sloupce.

Další informace naleznete v článcích [Sada záznamů: Dynamicky vazebné datové sloupce (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) a [Recordset: Načítání záznamů hromadně (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

### <a name="example"></a>Příklad

Viz článek [Výměna pole záznamu: Pomocí RFX](../../data/odbc/record-field-exchange-using-rfx.md).

## <a name="crecordsetm_nparams"></a><a name="m_nparams"></a>CSada záznamů::m_nParams

Obsahuje počet datových členů parametru ve třídě sady záznamů; to znamená počet parametrů předaných s dotazem sady záznamů.

### <a name="remarks"></a>Poznámky

Pokud vaše třída sady záznamů má všechny datové členy parametru, `m_nParams` konstruktor pro třídu musí inicializovat se správným číslem. Hodnota výchozí `m_nParams` hodnoty 0. Pokud přidáte datové členy parametrů (což je nutné provést ručně), musíte také ručně přidat inicializaci v konstruktoru třídy tak, aby odrážela počet `m_strFilter` `m_strSort` parametrů (které musí být alespoň stejně velké jako počet zástupných symbolů ve vašem nebo řetězci).

Rozhraní framework používá toto číslo při parametrizaci dotazu sady záznamů.

> [!CAUTION]
> Toto číslo musí odpovídat počtu "params" registrovaných `DoFieldExchange` v nebo `DoBulkFieldExchange` po volání `CFieldExchange::param` [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) s hodnotou parametru `CFieldExchange::inputParam`, , `CFieldExchange::outputParam`, nebo `CFieldExchange::inoutParam`.

### <a name="example"></a>Příklad

  Podívejte se na články [Recordset: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) a [Výměna pole záznamu: Pomocí RFX](../../data/odbc/record-field-exchange-using-rfx.md).

## <a name="crecordsetm_pdatabase"></a><a name="m_pdatabase"></a>CRecordset::m_pDatabase

Obsahuje ukazatel na `CDatabase` objekt, jehož prostřednictvím je sada záznamů připojena ke zdroji dat.

### <a name="remarks"></a>Poznámky

Tato proměnná je nastavena dvěma způsoby. Obvykle předáte ukazatel již připojenému `CDatabase` objektu při vytváření objektu sady záznamů. Pokud místo toho `CRecordset` předáte hodnotu NULL, vytvoří `CDatabase` za vás objekt a připojí jej. V obou `CRecordset` případech uloží ukazatel v této proměnné.

Za normálních okolností nebudete muset `m_pDatabase`přímo používat ukazatel uložený v aplikaci . Pokud však napíšete `CRecordset`vlastní rozšíření do aplikace , bude pravděpodobně nutné použít ukazatel. Například můžete potřebovat ukazatel, pokud hodíte vlastní `CDBException`s. Nebo budete potřebovat, pokud potřebujete něco provést `CDatabase` pomocí stejného objektu, jako je například `ExecuteSQL` spuštění transakcí, nastavení časového nastavení nebo volání členské funkce třídy `CDatabase` k přímému spuštění příkazů SQL.

## <a name="crecordsetm_strfilter"></a><a name="m_strfilter"></a>CSada záznamů::m_strFilter

Po vytvoření objektu sady záznamů, ale `Open` před voláním jeho členské `CString` funkce použijte tento datový člen k uložení obsahující klauzuli SQL **WHERE.**

### <a name="remarks"></a>Poznámky

Sada záznamů používá tento řetězec k omezení (nebo filtrování) `Open` záznamů, které vybere během volání nebo `Requery` volání. To je užitečné pro výběr podmnožinu záznamů, například "všichni prodejci se sídlem v Kalifornii" ("stav = certifikační autorita"). Syntaxe ODBC SQL pro klauzuli **WHERE** je

`WHERE search-condition`

Všimněte si, že do řetězce nezahrnete klíčové slovo **WHERE.** Rámec ji dodává.

Řetězec filtru můžete také parametrizovat umístěním zástupných symbolů '' do něj, deklarováním datového člena parametru ve vaší třídě pro každý zástupný symbol a předáním parametrů sadě záznamů za běhu. To umožňuje vytvořit filtr za běhu. Další informace naleznete v článku [Sada záznamů: Parametrizace sady záznamů (ODBC).](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

Další informace o klauzulích SQL **WHERE** naleznete v článku [SQL](../../data/odbc/sql.md). Další informace o výběru a filtrování záznamů naleznete v článku [Sada záznamů: Filtrování záznamů (ODBC).](../../data/odbc/recordset-filtering-records-odbc.md)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#30](../../mfc/codesnippet/cpp/crecordset-class_12.cpp)]

## <a name="crecordsetm_strsort"></a><a name="m_strsort"></a>CRecordset::m_strSort

Po vytvoření objektu sady záznamů, ale `Open` před voláním jeho členské `CString` funkce použijte tento datový člen k uložení obsahující klauzule SQL **ORDER BY.**

### <a name="remarks"></a>Poznámky

Sada záznamů používá tento řetězec k seřazení `Open` záznamů, které vybere během volání nebo `Requery` volání. Pomocí této funkce můžete seřadit sadu záznamů v jednom nebo více sloupcích. Syntaxe ODBC SQL pro klauzuli **ORDER BY** je

`ORDER BY sort-specification [, sort-specification]...`

kde specifikace řazení je celé číslo nebo název sloupce. Můžete také určit vzestupné nebo sestupné pořadí (pořadí je vzestupně ve výchozím nastavení) připojením "ASC" nebo "DESC" do seznamu sloupců v řetězci řazení. Vybrané záznamy jsou seřazeny nejprve podle prvního uvedeného sloupce, potom podle druhého a tak dále. Můžete například objednat sadu záznamů "Zákazníci" podle příjmení a poté křestního jména. Počet sloupců, které můžete uvést, závisí na zdroji dat. Další informace naleznete v souboru Windows SDK.

Všimněte si, že do řetězce nezahrnete klíčové slovo **ORDER BY.** Rámec ji dodává.

Další informace o klauzulích SQL naleznete v článku [SQL](../../data/odbc/sql.md). Další informace o řazení záznamů naleznete v článku [Sada záznamů: Řazení záznamů (ODBC).](../../data/odbc/recordset-sorting-records-odbc.md)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#31](../../mfc/codesnippet/cpp/crecordset-class_13.cpp)]

## <a name="crecordsetmove"></a><a name="move"></a>CRecordset::Přesunout

Přesune ukazatel aktuálního záznamu v sadě záznamů dopředu nebo dozadu.

```
virtual void Move(
    long nRows,
    WORD wFetchType = SQL_FETCH_RELATIVE);
```

### <a name="parameters"></a>Parametry

*nŘádky*<br/>
Počet řádků, které se mají pohybovat dopředu nebo dozadu. Kladné hodnoty se posouvají vpřed ke konci sady záznamů. Záporné hodnoty se pohybují dozadu směrem k začátku.

*wFetchType*<br/>
Určuje sadu řádků, `Move` která se načte. Podrobnosti naleznete v tématu Poznámky.

### <a name="remarks"></a>Poznámky

Pokud předáte hodnotu 0 pro `Move` *nRows*, aktualizuje aktuální záznam; `Move` ukončí libovolný `AddNew` proud `Edit` nebo režim a obnoví hodnotu `AddNew` aktuálního záznamu před nebo `Edit` byl volán.

> [!NOTE]
> Při procházení sady záznamů nelze odstraněné záznamy přeskočit. Další informace naleznete [v tématu CRecordset::IsDeleted.](#isdeleted) Při otevření `CRecordset` s `skipDeletedRecords` nastavenou `Move` možností, uplatní, pokud *nRows* parametr je 0. Toto chování zabraňuje aktualizaci řádků, které jsou odstraněny jinými klientskými aplikacemi pomocí stejných dat. Popis souboru naleznete v parametru `skipDeletedRecords` *dwOption* v části [Otevřít.](#open)

`Move`přemístí sadu záznamů podle sad řádků. Na základě hodnot pro *nRows* a `Move` *wFetchType*načte příslušnou sadu řádků a potom vytvoří první záznam v této sadě řádků aktuální záznam. Pokud jste neimplementovali hromadné načítání řádků, velikost sady řádků je vždy 1. Při načítání sady řádků `Move` přímo volá členská funkce [CheckRowsetError,](#checkrowseterror) aby zpracovat všechny chyby vyplývající z načtení.

V závislosti na předávaném hodnotách `Move` je ekvivalentní ostatním `CRecordset` členským funkcím. Zejména hodnota *wFetchType* může znamenat členská funkce, která je intuitivnější a často upřednostňovanou metodou pro přesunutí aktuálního záznamu.

V následující tabulce jsou uvedeny možné hodnoty pro `Move` *wFetchType*, sadu řádků, která bude načítat na základě *wFetchType* a *nRows*, a všechny ekvivalentní členské funkce odpovídající *wFetchType*.

|wFetchType|Načtená sada řádků|Ekvivalentní členská funkce|
|----------------|--------------------|--------------------------------|
|SQL_FETCH_RELATIVE (výchozí hodnota)|Sada řádků začínající *nRows* řádky z prvního řádku v aktuální sadě řádků.||
|SQL_FETCH_NEXT|Další sada řádků; *nRows* je ignorována.|[Movenext](#movenext)|
|SQL_FETCH_PRIOR|Předchozí sada řádků; *nRows* je ignorována.|[Moveprev](#moveprev)|
|SQL_FETCH_FIRST|První sada řádků v sadě záznamů; *nRows* je ignorována.|[Movefirst](#movefirst)|
|SQL_FETCH_LAST|Poslední úplná sada řádků v sadě záznamů; *nRows* je ignorována.|[Movelast](#movelast)|
|SQL_FETCH_ABSOLUTE|Pokud *nRows* > 0, sada řádků začínající *nRows* řádky od začátku sady záznamů. Pokud *nRows* < 0, sada řádků začínající *nRows* řádky od konce sady záznamů. Pokud *nRows* = 0, pak je vrácena podmínka začátku souboru (BOF).|[NastavitabsolutePosition](#setabsoluteposition)|
|SQL_FETCH_BOOKMARK|Sada řádků začínající na řádku, jehož hodnota záložky odpovídá *nRows*.|[Značka SetBookmark](#setbookmark)|

> [!NOTE]
> Pro sady záznamů pouze `Move` pro předávání je platný pouze s hodnotou SQL_FETCH_NEXT pro *wFetchType*.

> [!CAUTION]
> Volání `Move` vyvolá výjimku, pokud sada záznamů nemá žádné záznamy. Chcete-li zjistit, zda sada záznamů má nějaké záznamy, volání [IsBOF](#isbof) a [IsEOF](#iseof).

> [!NOTE]
> Pokud jste se posunuli za začátek nebo`IsBOF` `IsEOF` konec sady záznamů `Move` (nebo vrátí `CDBException`nenulovou hodnotu), volání funkce bude pravděpodobně hodit . Například pokud `IsEOF` vrátí nenulovou `IsBOF` a `MoveNext` není, pak `MovePrev` vyvolá výjimku, ale nebude.

> [!NOTE]
> Pokud zavoláte `Move` v době, kdy je aktuální záznam aktualizován nebo přidáván, aktualizace budou ztraceny bez upozornění.

Další informace o navigaci v sadě záznamů naleznete v článcích [Sada záznamů: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) a [Recordset: Záložky a Absolutní pozice (ODBC).](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) Související informace naleznete v části `SQLExtendedFetch` Funkce rozhraní API ROZHRANÍ ODBC v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#28](../../mfc/codesnippet/cpp/crecordset-class_14.cpp)]

## <a name="crecordsetmovefirst"></a><a name="movefirst"></a>CRecordset::PřesunoutPrvní

Vytvoří první záznam v první sadě řádků aktuální záznam.

```cpp
void MoveFirst();
```

### <a name="remarks"></a>Poznámky

Bez ohledu na to, zda bylo implementováno hromadné načítání řádků, bude to vždy první záznam v sadě záznamů.

Není třeba volat `MoveFirst` ihned po otevření sady záznamů. V té době je první záznam (pokud existuje) automaticky aktuální záznam.

> [!NOTE]
> Tato členská funkce není platná pro sady záznamů pouze pro předávání.

> [!NOTE]
> Při procházení sady záznamů nelze odstraněné záznamy přeskočit. Podrobnosti naleznete v členské funkci [IsDeleted.](#isdeleted)

> [!CAUTION]
> Volání některé `Move` z funkcí vyvolá výjimku, pokud sada záznamů nemá žádné záznamy. Chcete-li zjistit, zda sada `IsBOF` záznamů `IsEOF`má nějaké záznamy, volání a .

> [!NOTE]
> Pokud zavoláte některou z funkcí během `Move` aktualizace nebo přidání aktuálního záznamu, aktualizace budou bez upozornění ztraceny.

Další informace o navigaci v sadě záznamů naleznete v článcích [Sada záznamů: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) a [Recordset: Záložky a Absolutní pozice (ODBC).](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

### <a name="example"></a>Příklad

  Viz příklad pro [IsBOF](#isbof).

## <a name="crecordsetmovelast"></a><a name="movelast"></a>CRecordset::MoveLast

Vytvoří první záznam v poslední kompletní sadě řádků aktuální záznam.

```cpp
void MoveLast();
```

### <a name="remarks"></a>Poznámky

Pokud jste neimplementovali hromadné načítání řádků, má sada záznamů velikost `MoveLast` sady řádků 1, takže se jednoduše přesune na poslední záznam v sadě záznamů.

> [!NOTE]
> Tato členská funkce není platná pro sady záznamů pouze pro předávání.

> [!NOTE]
> Při procházení sady záznamů nelze odstraněné záznamy přeskočit. Podrobnosti naleznete v členské funkci [IsDeleted.](#isdeleted)

> [!CAUTION]
> Volání některé `Move` z funkcí vyvolá výjimku, pokud sada záznamů nemá žádné záznamy. Chcete-li zjistit, zda sada `IsBOF` záznamů `IsEOF`má nějaké záznamy, volání a .

> [!NOTE]
> Pokud zavoláte některou z funkcí během `Move` aktualizace nebo přidání aktuálního záznamu, aktualizace budou bez upozornění ztraceny.

Další informace o navigaci v sadě záznamů naleznete v článcích [Sada záznamů: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) a [Recordset: Záložky a Absolutní pozice (ODBC).](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

### <a name="example"></a>Příklad

  Viz příklad pro [IsBOF](#isbof).

## <a name="crecordsetmovenext"></a><a name="movenext"></a>CRecordset::MoveNext

Vytvoří první záznam v další sadě řádků jako aktuální záznam.

```cpp
void MoveNext();
```

### <a name="remarks"></a>Poznámky

Pokud jste neimplementovali hromadné načítání řádků, má sada záznamů velikost `MoveNext` sady řádků 1, takže se jednoduše přesune na další záznam.

> [!NOTE]
> Při procházení sady záznamů nelze odstraněné záznamy přeskočit. Podrobnosti naleznete v členské funkci [IsDeleted.](#isdeleted)

> [!CAUTION]
> Volání některé `Move` z funkcí vyvolá výjimku, pokud sada záznamů nemá žádné záznamy. Chcete-li zjistit, zda sada `IsBOF` záznamů `IsEOF`má nějaké záznamy, volání a .

> [!NOTE]
> Před voláním `MoveNext`je `IsEOF` také doporučeno zavolat . Pokud jste například posunuli za konec sady `IsEOF` záznamů, vrátí se nenulová; následné volání `MoveNext` by vyvolat výjimku.

> [!NOTE]
> Pokud zavoláte některou z funkcí během `Move` aktualizace nebo přidání aktuálního záznamu, aktualizace budou bez upozornění ztraceny.

Další informace o navigaci v sadě záznamů naleznete v článcích [Sada záznamů: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) a [Recordset: Záložky a Absolutní pozice (ODBC).](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

### <a name="example"></a>Příklad

  Viz příklad pro [IsBOF](#isbof).

## <a name="crecordsetmoveprev"></a><a name="moveprev"></a>CRecordset::MovePrev

Vytvoří první záznam v předchozí sadě řádků jako aktuální záznam.

```cpp
void MovePrev();
```

### <a name="remarks"></a>Poznámky

Pokud jste neimplementovali hromadné načítání řádků, má sada záznamů velikost `MovePrev` sady řádků 1, takže se jednoduše přesune na předchozí záznam.

> [!NOTE]
> Tato členská funkce není platná pro sady záznamů pouze pro předávání.

> [!NOTE]
> Při procházení sady záznamů nelze odstraněné záznamy přeskočit. Podrobnosti naleznete v členské funkci [IsDeleted.](#isdeleted)

> [!CAUTION]
> Volání některé `Move` z funkcí vyvolá výjimku, pokud sada záznamů nemá žádné záznamy. Chcete-li zjistit, zda sada `IsBOF` záznamů `IsEOF`má nějaké záznamy, volání a .

> [!NOTE]
> Před voláním `MovePrev`je `IsBOF` také doporučeno zavolat . Pokud jste například posunuli před začátek sady `IsBOF` záznamů, vrátí se nenulová; následné volání `MovePrev` by vyvolat výjimku.

> [!NOTE]
> Pokud zavoláte některou z funkcí během `Move` aktualizace nebo přidání aktuálního záznamu, aktualizace budou bez upozornění ztraceny.

Další informace o navigaci v sadě záznamů naleznete v článcích [Sada záznamů: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) a [Recordset: Záložky a Absolutní pozice (ODBC).](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

### <a name="example"></a>Příklad

  Viz příklad pro [IsBOF](#isbof).

## <a name="crecordsetonsetoptions"></a><a name="onsetoptions"></a>CRecordset::OnSetOptions

Nazývá se nastavení možností (používá se při výběru) pro zadaný příkaz ODBC.

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Parametry

*hstmt*<br/>
HSTMT příkazu ODBC, jehož možnosti mají být nastaveny.

### <a name="remarks"></a>Poznámky

Volání `OnSetOptions` k nastavení možností (použitých při výběru) pro zadaný příkaz ODBC. Rozhraní Framework volá tuto členská funkci k nastavení počátečních možností sady záznamů. `OnSetOptions`určuje podporu zdroje dat pro posuvné kurzory a souběžnost kurzoru a podle toho nastaví možnosti sady záznamů. (Vzhledem `OnSetOptions` k tomu, `OnSetUpdateOptions` že se používá pro operace výběru, se používá pro operace aktualizace.)

Přepsáním `OnSetOptions` nastavte možnosti specifické pro ovladač nebo zdroj dat. Například pokud váš zdroj dat podporuje otevření pro `OnSetOptions` výhradní přístup, můžete přepsat využít této schopnosti.

Další informace o kurzorech naleznete v článku [ODBC](../../data/odbc/odbc-basics.md).

## <a name="crecordsetonsetupdateoptions"></a><a name="onsetupdateoptions"></a>CRecordset::OnSetUpdateOptions

Nazývá se nastavení možností (používá se při aktualizaci) pro zadaný příkaz ODBC.

```
virtual void OnSetUpdateOptions(HSTMT hstmt);
```

### <a name="parameters"></a>Parametry

*hstmt*<br/>
HSTMT příkazu ODBC, jehož možnosti mají být nastaveny.

### <a name="remarks"></a>Poznámky

Volání `OnSetUpdateOptions` k nastavení možností (používá se při aktualizaci) pro zadaný příkaz ODBC. Rozhraní Framework volá tuto členská funkci poté, co vytvoří HSTMT aktualizovat záznamy v sadě záznamů. (Vzhledem `OnSetOptions` k tomu, `OnSetUpdateOptions` že se používá pro operace výběru, se používá pro operace aktualizace.) `OnSetUpdateOptions` určuje podporu zdroje dat pro posuvné kurzory a souběžnost kurzoru a podle toho nastaví možnosti sady záznamů.

Přepsání `OnSetUpdateOptions` maže tenastavit možnosti příkazu ODBC před tímto příkazem se používá pro přístup k databázi.

Další informace o kurzorech naleznete v článku [ODBC](../../data/odbc/odbc-basics.md).

## <a name="crecordsetopen"></a><a name="open"></a>Crecordset::open

Otevře sadu záznamů načtením tabulky nebo provedením dotazu, který sada záznamů představuje.

```
virtual BOOL Open(
    UINT nOpenType = AFX_DB_USE_DEFAULT_TYPE,
    LPCTSTR lpszSQL = NULL,
    DWORD dwOptions = none);
```

### <a name="parameters"></a>Parametry

*nOpenType*<br/>
Přijměte výchozí hodnotu, AFX_DB_USE_DEFAULT_TYPE nebo použijte `enum OpenType`jednu z následujících hodnot z :

- `CRecordset::dynaset`Sada záznamů s obousměrným posouváním. Členství a pořadí záznamů je určeno při otevření sady záznamů, ale změny datových hodnot provedené ostatními uživateli jsou viditelné až po operaci načtení. Dynamické sady jsou známy také jako sady záznamů řízené sadou klíčů.

- `CRecordset::snapshot`Statická sada záznamů s obousměrným posouváním. Členství a pořadí záznamů je určeno při otevření sady záznamů. Datové hodnoty jsou určeny při načtení záznamů. Změny provedené ostatními uživateli nejsou viditelné, dokud není sada záznamů zavřena a znovu otevřena.

- `CRecordset::dynamic`Sada záznamů s obousměrným posouváním. Změny členství, pořadí a datových hodnot provedené jinými uživateli jsou viditelné po operaci načtení. Povšimněte si, že mnoho ovladačů ODBC nepodporuje tento typ sady záznamů.

- `CRecordset::forwardOnly`Sada záznamů jen pro čtení s pouze posunutím vpřed.

   Pro `CRecordset`výchozí hodnotu `CRecordset::snapshot`je . Mechanismus výchozích hodnot umožňuje interakci průvodců aplikace Visual C++ s třídou `CRecordset` pro rozhraní ODBC i třídou `CDaoRecordset` pro rozhraní DAO, které používají různé výchozí hodnoty.

Další informace o těchto typech sad záznamů naleznete v článku [Sada záznamů (ODBC).](../../data/odbc/recordset-odbc.md) Související informace naleznete v článku "Použití blokování a rolovací kurzory" v sadě Windows SDK.

> [!CAUTION]
> Není-li požadovaný typ podporován, rozhraní vyvolá výjimku.

*Lpszsql*<br/>
Ukazatel řetězce obsahující jedno z následujících:

- Ukazatel NULL.

- Název tabulky.

- Příkaz SQL **SELECT** (volitelně s klauzulí SQL **WHERE** nebo **ORDER BY).**

- Příkaz **CALL** určující název předdefinovaného dotazu (uložená procedura). Dávejte pozor, abyste nevkládali mezery mezi složené závorky a klíčové slovo **CALL.**

Další informace o tomto řetězci naleznete v tabulce a diskusi o roli ClassWizard v části [Poznámky.](#remarks)

> [!NOTE]
> Pořadí sloupců v sadě výsledků se musí shodovat s pořadím volání funkce RFX nebo Bulk RFX v přepsání funkce [DoFieldExchange](#dofieldexchange) nebo [DoBulkFieldExchange.](#dobulkfieldexchange)

*Dwoptions*<br/>
Bitová maska schopná určit kombinaci hodnot uvedených níže. Některé se vzájemně vylučují. Výchozí hodnota je **žádná**.

- `CRecordset::none`Nejsou nastaveny žádné možnosti. Tato hodnota parametru se vzájemně vylučuje se všemi ostatními hodnotami. Ve výchozím nastavení lze sadu záznamů aktualizovat pomocí [funkce Upravit](#edit) nebo [Odstranit](#delete) a umožňuje připojit nové záznamy pomocí [funkce AddNew](#addnew). Aktualizovatelnost závisí na zdroji dat a také na zadané možnosti *nOpenType.* Optimalizace pro hromadná přidávání nejsou dostupné. Hromadné načítání řádků nebude implementováno. Odstraněné záznamy nebudou při navigaci v sadě záznamů přeskočeny. Záložky nejsou k dispozici. Automatická kontrola nečistých polí je implementována.

- `CRecordset::appendOnly`Nepovoluj `Edit` sadu záznamů ani `Delete` na ní. Povolit pouze funkci `AddNew`. Tato možnost se vzájemně vylučuje s možností `CRecordset::readOnly`.

- `CRecordset::readOnly`Otevřete sadu záznamů jen pro čtení. Tato možnost se vzájemně vylučuje s možností `CRecordset::appendOnly`.

- `CRecordset::optimizeBulkAdd`Pomocí připraveného příkazu SQL optimalizujte přidání mnoha záznamů najednou. Platí pouze v případě, že k `SQLSetPos` aktualizaci sady záznamů nepoužíváte funkci ROZHRANÍ API ROZHRANÍ ODBC. První aktualizace určuje, která pole jsou označena za nečistá. Tato možnost se vzájemně vylučuje s možností `CRecordset::useMultiRowFetch`.

- `CRecordset::useMultiRowFetch`Implementovat hromadné načítání řádků povolit více řádků, které mají být načteny v rámci operace načtení. Jde o pokročilou funkci navrženou pro zvýšení výkonu. Hromadná výměna polí záznamu však není podporována nástrojem ClassWizard. Tato možnost se vzájemně vylučuje s možností `CRecordset::optimizeBulkAdd`. Všimněte si, `CRecordset::useMultiRowFetch`že pokud `CRecordset::noDirtyFieldCheck` zadáte , pak možnost bude zapnuta automaticky (dvojité ukládání do vyrovnávací paměti nebude k dispozici); na sadách záznamů pouze `CRecordset::useExtendedFetch` pro předávání, bude tato možnost automaticky zapnuta. Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

- `CRecordset::skipDeletedRecords`Při procházení sadou záznamů přeskočte všechny odstraněné záznamy. V určitých relativních načteních tato možnost sníží výkon. Tato možnost není platná pro sady záznamů s posouváním pouze vpřed. Pokud zavoláte [Move](#move) s parametrem *nRows* `CRecordset::skipDeletedRecords` nastaveným `Move` na 0 a nastavenou možností, bude uplatněna. Všimněte `CRecordset::skipDeletedRecords` si, že je podobný *balení ovladače*, což znamená, že odstraněné řádky jsou odebrány ze sady záznamů. Pokud však ovladač záznamy komprimuje, budou přeskočeny pouze vámi odstraněné záznamy. Záznamy odstraněné jinými uživateli v době, kdy byla sada otevřena, nebudou přeskočeny. `CRecordset::skipDeletedRecords`přeskakuje řádky odstraněné jinými uživateli.

- `CRecordset::useBookmarks`Může používat záložky v sadě záznamů, pokud je podporován. Záložky zpomalují načítání dat, ale zvyšují výkon navigace v nich. Nelze je použít v sadách záznamů s posouváním pouze vpřed. Další informace naleznete v článku [Sada záznamů: Záložky a absolutní pozice (ODBC).](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)

- `CRecordset::noDirtyFieldCheck`Vypněte automatickou kontrolu znečištěného pole (dvojité ukládání do vyrovnávací paměti). Tím dojde ke zvýšení výkonu. Pole je však zapotřebí ručně označit jako nečistá zavoláním členských funkcí `SetFieldDirty` a `SetFieldNull`. Povšimněte si, že dvojité ukládání do vyrovnávací paměti ve třídě `CRecordset` je podobné dvojitému ukládání do vyrovnávací paměti ve třídě `CDaoRecordset`. Ve třídě `CRecordset` však nelze zapnout dvojité ukládání do vyrovnávací paměti pro jednotlivá pole. Lze jej zapnout nebo vypnout pouze pro všechna pole najednou. Všimněte si, že `CRecordset::useMultiRowFetch`pokud `CRecordset::noDirtyFieldCheck` zadáte možnost , pak se zapne automaticky; však `SetFieldDirty` `SetFieldNull` a nelze použít na sady záznamů, které implementují hromadné načítání řádků.

- `CRecordset::executeDirect`Nepoužívejte připravený příkaz SQL. Chcete-li zvýšit výkon, `Requery` zadejte tuto možnost, pokud členské funkce nikdy nebude volána.

- `CRecordset::useExtendedFetch`Implementovat `SQLExtendedFetch` `SQLFetch`namísto . Navrženo pro implementaci hromadného načítání řádků pro sady záznamů s posouváním pouze vpřed. Pokud zadáte možnost `CRecordset::useMultiRowFetch` v sadě záznamů pouze `CRecordset::useExtendedFetch` pro předávání, bude automaticky zapnuta.

- `CRecordset::userAllocMultiRowBuffers`Uživatel přidělí vyrovnávací paměti úložiště pro data. Chcete-li přidělit své vlastní úložiště, použijte tuto možnost spolu s možností `CRecordset::useMultiRowFetch`. V opačném případě bude potřebné úložiště přiděleno rozhraním. Další informace naleznete v článku [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) Všimněte si, že zadání `CRecordset::userAllocMultiRowBuffers` bez zadání `CRecordset::useMultiRowFetch` bude mít za následek kontrolní výraz se nezdařilo.

### <a name="return-value"></a>Návratová hodnota

Nenulová, `CRecordset` pokud byl objekt úspěšně otevřen; jinak 0, pokud [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) (pokud je volána) vrátí 0.

### <a name="remarks"></a>Poznámky

Chcete-li spustit dotaz definovaný sadou záznamů, je zapotřebí zavolat tuto členskou funkci. Před `Open`voláním je nutné vytvořit objekt sady záznamů.

Připojení této sady záznamů ke zdroji dat závisí na tom, `Open`jak vytvoříte sadu záznamů před voláním . Pokud předáte objekt [CDatabase](../../mfc/reference/cdatabase-class.md) konstruktoru sady záznamů, který nebyl připojen ke zdroji dat, tato členská funkce použije k pokusu o otevření databázového objektu [funkci GetDefaultConnect.](#getdefaultconnect) Pokud předáte null konstruktoru sady záznamů, konstruktor vytvoří `CDatabase` objekt `Open` za vás a pokusí se připojit databázový objekt. Podrobnosti o zavření sady záznamů a připojení za těchto různých okolností naleznete v [tématu Zavřít](#close).

> [!NOTE]
> Přístup ke zdroji dat pomocí objektu `CRecordset` je vždy sdílen. Na rozdíl od třídy `CDaoRecordset` nelze objekt `CRecordset` použít k otevření zdroje dat s výhradním přístupem.

Při volání `Open`vybere dotaz, obvykle příkaz SQL **SELECT,** záznamy na základě kritérií zobrazených v následující tabulce.

|Hodnota parametru IpszSQL|Zvolené záznamy jsou určeny|Příklad|
|------------------------------------|----------------------------------------|-------------|
|NULL|Řetězec vrácený funkcí `GetDefaultSQL`.||
|Název tabulky SQL|Všechny sloupce tabulkového seznamu ve funkci `DoFieldExchange` nebo `DoBulkFieldExchange`.|`"Customer"`|
|Název předdefinovaného dotazu (uložené procedury)|Sloupce, k jejichž vrácení je dotaz definován.|`"{call OverDueAccts}"`|
|**VYBRAT** seznam sloupců **z** tabulky|Zadané sloupce ze zadané tabulky nebo tabulek.|`"SELECT CustId, CustName FROM`<br /><br /> `Customer"`|

> [!CAUTION]
> Ujistěte se, že do řetězce jazyka SQL nebyly vloženy prázdné znaky. Pokud například vložíte prázdné znaky mezi složené závorky a klíčové slovo **CALL,** knihovna MFC nesprávně interpretuje řetězec SQL jako název tabulky a začlení jej do příkazu **SELECT,** což bude mít za následek vyvolání výjimky. Podobně pokud předdefinovaný dotaz používá výstupní parametr, nevkládejte mezery mezi složené závorky a symbol '. Nakonec nesmíte vložit mezery před složené složenou závorku v příkazu **CALL** nebo před klíčové slovo **SELECT** v příkazu **SELECT.**

Obvyklý postup je předat `Open`NULL do ; v tomto `Open` případě volá [GetDefaultSQL](#getdefaultsql). Pokud používáte odvozenou `CRecordset` třídu, `GetDefaultSQL` přidá název tabulky, které jste zadali v ClassWizard. Místo toho lze zadat jiné informace v parametru `lpszSQL`.

Bez ohledu `Open` na to, co předáte, vytvoří konečný řetězec SQL pro dotaz (řetězec `lpszSQL` může mít klauzule SQL **WHERE** a ORDER **BY** připojené k řetězci, který jste předali) a poté spustí dotaz. Můžete prozkoumat vytvořený řetězec voláním [GetSQL](#getsql) po volání `Open`. Další podrobnosti o tom, jak sada záznamů vytváří příkaz SQL a vybírá záznamy, naleznete v článku [Sada záznamů: Jak sady záznamů vyberte záznamy (ODBC).](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)

Datové členy polí třídy sady záznamů jsou svázány se sloupci zvolených dat. Jsou-li vráceny jakékoli záznamy, první záznam se stává aktuálním záznamem.

Chcete-li nastavit volby pro sadu záznamů, například filtr nebo řazení, zadejte je `Open`po vytvoření objektu sady záznamů, ale před voláním . Chcete-li aktualizovat záznamy v sadě záznamů po otevření sady záznamů, zavolejte [dotaz Requery](#requery).

Další informace, včetně dalších příkladů, naleznete v článcích [Sada záznamů (ODBC),](../../data/odbc/recordset-odbc.md) [Sada záznamů: Jak sady záznamů vyberte záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)a [Recordset: Vytváření a zavírání sad záznamů (ODBC).](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)

### <a name="example"></a>Příklad

Následující příklady kódu zobrazit různé `Open` formy volání.

[!code-cpp[NVC_MFCDatabase#16](../../mfc/codesnippet/cpp/crecordset-class_15.cpp)]

## <a name="crecordsetrefreshrowset"></a><a name="refreshrowset"></a>CRecordset::RefreshRowset

Aktualizuje data a stav řádku v aktuální sadě řádků.

```cpp
void RefreshRowset(
    WORD wRow,
    WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>Parametry

*wŘádek*<br/>
Jednomístná pozice řádku v aktuální sadě řádků. Tato hodnota může být v rozsahu od nuly do velikosti sady řádků.

*wLockType*<br/>
Hodnota označující, jak zamknout řádek po jeho aktualizaci. Podrobnosti naleznete v tématu Poznámky.

### <a name="remarks"></a>Poznámky

Pokud předáte hodnotu nula pro *wRow*, pak každý řádek v sadě řádků bude aktualizován.

Chcete-li použít `RefreshRowset`, musíte mít implementovat `CRecordset::useMulitRowFetch` hromadné načítání řádků zadáním možnosti v [otevřené](#open) členské funkce.

`RefreshRowset`volá funkci `SQLSetPos`ROZHRANÍ API ROZHRANÍ ODBC . Parametr *wLockType* určuje stav zámku řádku `SQLSetPos` po provedení. Následující tabulka popisuje možné hodnoty pro *wLockType*.

|wLockType|Popis|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE (výchozí hodnota)|Ovladač nebo zdroj dat zajišťuje, že řádek je ve stejném uzamčeném nebo odemčeném stavu, jako tomu bylo předtím. `RefreshRowset`|
|SQL_LOCK_EXCLUSIVE|Ovladač nebo zdroj dat uzamkne řádek výhradně. Ne všechny zdroje dat podporují tento typ zámku.|
|SQL_LOCK_UNLOCK|Ovladač nebo zdroj dat odemkne řádek. Ne všechny zdroje dat podporují tento typ zámku.|

Další informace `SQLSetPos`o aplikaci naleznete v souboru Windows SDK. Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

## <a name="crecordsetrequery"></a><a name="requery"></a>CRecordset::Requery

Znovu vytvoří (aktualizuje) sadu záznamů.

```
virtual BOOL Requery();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla sada záznamů úspěšně znovu sestavena; jinak 0.

### <a name="remarks"></a>Poznámky

Jsou-li vráceny jakékoli záznamy, první záznam se stává aktuálním záznamem.

Aby sada záznamů odrážela dodatky a odstranění, které vy nebo jiní uživatelé provádíte do `Requery`zdroje dat, je nutné znovu vytvořit sadu záznamů voláním . Pokud je sada záznamů dynaset, automaticky odráží aktualizace, které vy nebo jiní uživatelé provedete s existujícími záznamy (ale ne s dodatky). Pokud je sada záznamů snímek, `Requery` musíte volat tak, aby odrážely úpravy ostatních uživatelů a také doplňky a odstranění.

Pro dynaset nebo snímek `Requery` volejte kdykoli, kdy chcete znovu sestavit sadu záznamů pomocí nového filtru nebo řazení nebo nových hodnot parametrů. Nastavte novou vlastnost filtru nebo řazení přiřazením `m_strSort` nových `Requery`hodnot `m_strFilter` a před voláním . Před voláním `Requery`nastavte nové parametry přiřazením nových hodnot datovým členům parametrů . Pokud jsou řetězce filtru a řazení nezměněny, můžete dotaz znovu použít, což zvyšuje výkon.

Pokud se pokus o znovusestavení sady záznamů nezdaří, sada záznamů je uzavřena. Před voláním `Requery`můžete určit, zda lze sadu záznamů znovu `CanRestart` dotazovat voláním členské funkce. `CanRestart`nezaručuje, `Requery` že bude úspěšná.

> [!CAUTION]
> Volat `Requery` až po volání [Otevřít](#open).

### <a name="example"></a>Příklad

Tento příklad znovu vytvoří sadu záznamů a použije jiné pořadí řazení.

[!code-cpp[NVC_MFCDatabase#29](../../mfc/codesnippet/cpp/crecordset-class_16.cpp)]

## <a name="crecordsetsetabsoluteposition"></a><a name="setabsoluteposition"></a>CRecordset::Nastavitabsoluteposition

Umístí sadu záznamů na záznam odpovídající zadanému číslu záznamu.

```cpp
void SetAbsolutePosition(long nRows);
```

### <a name="parameters"></a>Parametry

*nŘádky*<br/>
Jednomístná ordinální pozice pro aktuální záznam v sadě záznamů.

### <a name="remarks"></a>Poznámky

`SetAbsolutePosition`přesune ukazatel aktuálního záznamu na základě této ordinální polohy.

> [!NOTE]
> Tato členská funkce není platná pro sady záznamů pouze pro předávání.

U sad záznamů ROZHRANÍ ODBC odkazuje nastavení absolutní polohy 1 na první záznam v sadě záznamů; nastavení 0 odkazuje na pozici začátku souboru (BOF).

Záporné hodnoty můžete `SetAbsolutePosition`také předat . V tomto případě je pozice sady záznamů vyhodnocena od konce sady záznamů. Například `SetAbsolutePosition( -1 )` přesune ukazatel aktuálního záznamu na poslední záznam v sadě záznamů.

> [!NOTE]
> Absolutní pozice není určena k použití jako náhradní číslo záznamu. Záložky jsou stále doporučeným způsobem, jak zachovat a vrátit se na danou pozici, protože pozice záznamu se změní při odstranění předchozích záznamů. Kromě toho si nemůžete být jisti, že daný záznam bude mít stejnou absolutní pozici, pokud je sada záznamů znovu vytvořena, protože pořadí jednotlivých záznamů v rámci sady záznamů není zaručeno, pokud není vytvořeno pomocí příkazu SQL pomocí klauzule **ORDER BY.**

Další informace o navigaci a záložkách sady záznamů naleznete v článcích [Sada záznamů: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) a [Recordset: Záložky a Absolutní pozice (ODBC).](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)

## <a name="crecordsetsetbookmark"></a><a name="setbookmark"></a>CRecordset::SetBookmark

Umístí sadu záznamů na záznam obsahující zadanou záložku.

```cpp
void SetBookmark(const CDBVariant& varBookmark);
```

### <a name="parameters"></a>Parametry

*varBookmark*<br/>
Odkaz na objekt [CDBVariant](../../mfc/reference/cdbvariant-class.md) obsahující hodnotu záložky pro určitý záznam.

### <a name="remarks"></a>Poznámky

Chcete-li zjistit, zda jsou záložky v sadě záznamů podporovány, zavolejte [CanBookmark](#canbookmark). Chcete-li záložky zpřístupnit, pokud jsou `CRecordset::useBookmarks` podporovány, musíte nastavit možnost v parametru *dwOptions* členské funkce [Otevřít.](#open)

> [!NOTE]
> Pokud záložky nejsou podporovány `SetBookmark` nebo nejsou k dispozici, volání bude mít za následek vyvolání výjimky. Záložky nejsou podporovány v sadách záznamů pouze pro předávání.

Chcete-li nejprve načíst záložku pro aktuální záznam, zavolejte [GetBookmark](#getbookmark), který uloží hodnotu záložky do objektu. `CDBVariant` Později se můžete k tomuto záznamu vrátit voláním `SetBookmark` pomocí uložené hodnoty záložky.

> [!NOTE]
> Po určitých operacích sady záznamů byste měli `SetBookmark`před voláním zkontrolovat trvalost záložky . Pokud například načtete záložku `GetBookmark` s `Requery`a pak zavoláte , nemusí být již platná. Volání [CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) zkontrolovat, zda `SetBookmark`můžete bezpečně volat .

Další informace o záložkách a navigaci v sadě záznamů naleznete v článcích [Sada záznamů: Záložky a absolutní pozice (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) a [Sada záznamů: Posouvání (ODBC).](../../data/odbc/recordset-scrolling-odbc.md)

## <a name="crecordsetsetfielddirty"></a><a name="setfielddirty"></a>CRecordset::SetFieldDirty

Označí datového člena pole sady záznamů jako změněného nebo nezměněného.

```cpp
void SetFieldDirty(void* pv, BOOL bDirty = TRUE);
```

### <a name="parameters"></a>Parametry

*Pv*<br/>
Obsahuje adresu datového člena pole v sadě záznamů nebo null. Pokud null, jsou označeny všechny členy dat pole v sadě záznamů. (C++ NULL není stejný jako Null v databázi terminologie, což znamená "bez hodnoty.")

*bDirty*<br/>
PRAVDA, pokud má být datový člen pole označen jako "dirty" (změněn). Jinak FALSE, pokud člen dat pole má být označen jako "čistý" (beze změny).

### <a name="remarks"></a>Poznámky

Označení polí jako nezměněných zajišťuje, že pole nebude aktualizováno a výsledkem bude méně provozu SQL.

> [!NOTE]
> Tato členská funkce není použitelná u sad záznamů, které používají hromadné načítání řádků. Pokud jste implementovali hromadné načítání `SetFieldDirty` řádků, bude výsledkem neúspěšná kontrolní skupina. Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

Rámcové značky změnily datové členy pole, aby bylo zajištěno, že budou zapsány do záznamu ve zdroji dat mechanismem výměny pole záznamu (RFX). Změna hodnoty pole obvykle nastaví pole dirty automaticky, takže `SetFieldDirty` budete zřídka muset volat sami sebe, ale někdy můžete chtít zajistit, že sloupce budou explicitně aktualizovány nebo vloženy bez ohledu na to, jaká hodnota je v datovém členu pole.

> [!CAUTION]
> Volání této členské funkce až po volání [Upravit](#edit) nebo [Přidatnový](#addnew).

Použití null pro první argument funkce bude používat `outputColumn` funkci `param` pouze pro pole, nikoli pole. Například volání

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

nastaví `outputColumn` pouze pole na hodnotu NULL; `param` pole nebudou ovlivněna.

Chcete-li `param` pracovat na polích, musíte `param` zadat skutečnou adresu osoby, na které chcete pracovat, například:

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

To znamená, že `param` nelze nastavit všechna pole `outputColumn` na hodnotu NULL, stejně jako u polí.

## <a name="crecordsetsetfieldnull"></a><a name="setfieldnull"></a>CRecordset::SetFieldNull

Označí datového člena pole sady záznamů jako null (konkrétně bez hodnoty) nebo jako nenulový.

```cpp
void SetFieldNull(void* pv, BOOL bNull = TRUE);
```

### <a name="parameters"></a>Parametry

*Pv*<br/>
Obsahuje adresu datového člena pole v sadě záznamů nebo null. Pokud null, jsou označeny všechny členy dat pole v sadě záznamů. (C++ NULL není stejný jako Null v databázi terminologie, což znamená "bez hodnoty.")

*bNull*<br/>
Nenulová, pokud má být datový člen pole označen jako neoznačený jako bez hodnoty (Null). V opačném případě 0, pokud má být datový člen pole označen jako nenulový.

### <a name="remarks"></a>Poznámky

Když přidáte nový záznam do sady záznamů, všechny datové členy pole jsou zpočátku nastaveny na hodnotu Null a označeny jako "dirty" (změněno). Při načtení záznamu ze zdroje dat jeho sloupce již mají hodnoty nebo jsou null.

> [!NOTE]
> Nevolejte tuto člennou funkci na sadách záznamů, které používají hromadné načítání řádků. Pokud jste implementovali hromadné načítání `SetFieldNull` řádků, volání výsledků v kontrolním výrazu se nezdařilo. Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

Pokud konkrétně chcete určit pole aktuálního záznamu jako pole, `SetFieldNull` které nemá hodnotu, volání s *hodnotou bNull* nastavenou na HODNOTU TRUE, která jej označí jako null. Pokud bylo pole dříve označeno jako null a nyní chcete mu přidělit hodnotu, jednoduše nastavte jeho novou hodnotu. Není třeba odebrat příznak Null `SetFieldNull`s . Chcete-li zjistit, zda je povoleno `IsFieldNullable`mít pole hodnotu Null, volejte .

> [!CAUTION]
> Volání této členské funkce až po volání [Upravit](#edit) nebo [Přidatnový](#addnew).

Použití null pro první argument funkce bude používat `outputColumn` funkci `param` pouze pro pole, nikoli pole. Například volání

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

nastaví `outputColumn` pouze pole na hodnotu NULL; `param` pole nebudou ovlivněna.

Chcete-li `param` pracovat na polích, musíte `param` zadat skutečnou adresu osoby, na které chcete pracovat, například:

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

To znamená, že `param` nelze nastavit všechna pole `outputColumn` na hodnotu NULL, stejně jako u polí.

> [!NOTE]
> Při nastavování parametrů na `SetFieldNull` hodnotu Null má volání před otevřením sady záznamů za následek kontrolní výraz. V tomto případě volejte [SetParamNull](#setparamnull).

`SetFieldNull`je implementována prostřednictvím [DoFieldExchange](#dofieldexchange).

## <a name="crecordsetsetlockingmode"></a><a name="setlockingmode"></a>CRecordset::SetLockingMode

Nastaví režim zamykání na "optimistické" zamykání (výchozí) nebo "pesimistické" zamykání. Určuje, jak jsou záznamy uzamčeny pro aktualizace.

```cpp
void SetLockingMode(UINT nMode);
```

### <a name="parameters"></a>Parametry

*nRežim*<br/>
Obsahuje jednu z následujících hodnot z `enum LockMode`:

- `optimistic`Optimistické zamykání uzamkne `Update`záznam aktualizovaný pouze během volání do .

- `pessimistic`Pesimistické zamykání `Edit` uzamkne záznam, `Update` jakmile je voláno, a zachová jej uzamčený, dokud se hovor nedokončí nebo nepřesunete na nový záznam.

### <a name="remarks"></a>Poznámky

Volání této členské funkce, pokud potřebujete určit, které ze dvou strategií zamykání záznamů sada záznamů používá pro aktualizace. Ve výchozím nastavení je `optimistic`režim uzamčení sady záznamů . Můžete to změnit na `pessimistic` opatrnější strategii zamykání. Volání `SetLockingMode` po vytvoření a otevření objektu sady `Edit`záznamů, ale před voláním .

## <a name="crecordsetsetparamnull"></a><a name="setparamnull"></a>CRecordset::SetParamNull

Označí parametr jako Null (konkrétně bez hodnoty) nebo jako non-Null.

```cpp
void SetParamNull(
    int nIndex,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Nula na základě indexu parametru.

*bNull*<br/>
Pokud true (výchozí hodnota), parametr je označen jako Null. V opačném případě je parametr označen jako non-Null.

### <a name="remarks"></a>Poznámky

Na rozdíl od [SetFieldNull](#setfieldnull), můžete volat `SetParamNull` před otevřením sady záznamů.

`SetParamNull`se obvykle používá s předdefinovanými dotazy (uložené procedury).

## <a name="crecordsetsetrowsetcursorposition"></a><a name="setrowsetcursorposition"></a>CRecordset::SetRowsetCursorPosition

Přesune kurzor na řádek v rámci aktuální sady řádků.

```cpp
void SetRowsetCursorPosition(WORD wRow, WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>Parametry

*wŘádek*<br/>
Jednomístná pozice řádku v aktuální sadě řádků. Tato hodnota může být v rozsahu od 1 do velikosti sady řádků.

*wLockType*<br/>
Hodnota označující, jak zamknout řádek po jeho aktualizaci. Podrobnosti naleznete v tématu Poznámky.

### <a name="remarks"></a>Poznámky

Při implementaci hromadného načítání řádků jsou záznamy načteny sadami řádků, kde první záznam v načtené sadě řádků je aktuální záznam. Chcete-li vytvořit další záznam v rámci sady `SetRowsetCursorPosition`řádků aktuální záznam, volejte . Můžete například kombinovat `SetRowsetCursorPosition` s člennou funkcí [GetFieldValue](#getfieldvalue) a dynamicky načíst data z libovolného záznamu vaší sady záznamů.

`SetRowsetCursorPosition`Chcete-li použít , musíte mít implementovány `CRecordset::useMultiRowFetch` hromadné načítání řádků zadáním *možnosti dwOptions* parametr v [Open](#open) členské funkce.

`SetRowsetCursorPosition`volá funkci `SQLSetPos`ROZHRANÍ API ROZHRANÍ ODBC . Parametr *wLockType* určuje stav zámku řádku `SQLSetPos` po provedení. Následující tabulka popisuje možné hodnoty pro *wLockType*.

|wLockType|Popis|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE (výchozí hodnota)|Ovladač nebo zdroj dat zajišťuje, že řádek je ve stejném uzamčeném nebo odemčeném stavu, jako tomu bylo předtím. `SetRowsetCursorPosition`|
|SQL_LOCK_EXCLUSIVE|Ovladač nebo zdroj dat uzamkne řádek výhradně. Ne všechny zdroje dat podporují tento typ zámku.|
|SQL_LOCK_UNLOCK|Ovladač nebo zdroj dat odemkne řádek. Ne všechny zdroje dat podporují tento typ zámku.|

Další informace `SQLSetPos`o aplikaci naleznete v souboru Windows SDK. Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

## <a name="crecordsetsetrowsetsize"></a><a name="setrowsetsize"></a>CRecordset::SetRowsetSize

Určuje počet záznamů, které chcete načíst během načítání.

```
virtual void SetRowsetSize(DWORD dwNewRowsetSize);
```

### <a name="parameters"></a>Parametry

*dwNewRowsetVelikost*<br/>
Počet řádků načíst během dané načtení.

### <a name="remarks"></a>Poznámky

Tato virtuální členská funkce určuje, kolik řádků chcete načíst během jednoho načtení při použití hromadného načítání řádků. Chcete-li implementovat hromadné načítání `CRecordset::useMultiRowFetch` řádků, musíte nastavit možnost v parametru *dwOptions* členské funkce [Otevřít.](#open)

> [!NOTE]
> Volání `SetRowsetSize` bez implementace hromadného načítání řádků bude mít za následek kontrolní výraz, který se nezdařil.

Volání `SetRowsetSize` před `Open` voláním nejprve nastavit velikost sady řádků pro sadu záznamů. Výchozí velikost sady řádků při implementaci hromadného načítání řádků je 25.

> [!NOTE]
> Při volání `SetRowsetSize`buďte opatrní . Pokud ručně přidělujete úložiště pro data (jak `CRecordset::userAllocMultiRowBuffers` je určeno možností parametru dwOptions v aplikaci `Open`), měli byste `SetRowsetSize`zkontrolovat, zda je třeba tyto vyrovnávací paměti úložiště po volání přerozdělit , ale před provedením jakékoli operace navigace kurzorem.

Chcete-li získat aktuální nastavení pro velikost sady řádků, volejte [GetRowsetSize](#getrowsetsize).

Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

## <a name="crecordsetupdate"></a><a name="update"></a>CRecordset::Aktualizovat

Dokončí operaci `AddNew` `Edit` nebo operaci uložením nových nebo upravených dat do zdroje dat.

```
virtual BOOL Update();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl jeden záznam úspěšně aktualizován; jinak 0, pokud se nezměnily žádné sloupce. Pokud nebyly aktualizovány žádné záznamy nebo pokud byl aktualizován více než jeden záznam, je vyvolána výjimka. Výjimka je také vyvolána pro jakékoli jiné selhání ve zdroji dat.

### <a name="remarks"></a>Poznámky

Volání této členské funkce po volání [přidatnové](#addnew) nebo [upravit](#edit) členské funkce. Toto volání je `AddNew` nutné `Edit` k dokončení operace nebo.

> [!NOTE]
> Pokud jste implementovali hromadné načítání řádků, nelze volat `Update`. Výsledkem bude neúspěšný kontrolní výraz. Přestože `CRecordset` třída neposkytuje mechanismus pro aktualizaci hromadných řádků dat, můžete zapisovat vlastní funkce pomocí funkce `SQLSetPos`ROZHRANÍ API ROZHRANÍ ODBC . Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

Obě `AddNew` `Edit` a připravit upravit vyrovnávací paměti, ve kterém jsou umístěny přidané nebo upravené data pro uložení do zdroje dat. `Update`uloží data. Aktualizována jsou pouze pole označená nebo zjištěná jako změněná.

Pokud zdroj dat podporuje transakce, můžete `Update` volání (a `AddNew` `Edit` jeho odpovídající nebo volání) součástí transakce. Další informace o transakcích naleznete v článku [Transakce (ODBC).](../../data/odbc/transaction-odbc.md)

> [!CAUTION]
> Pokud `Update` zavoláte bez `AddNew` předchozího volání buď nebo `Edit`, `Update` vyvolá . `CDBException` Pokud `AddNew` zavoláte `Edit`nebo , `Update` musíte zavolat před voláním `Move` operace nebo před zavření sady záznamů nebo připojení zdroje dat. V opačném případě budou změny ztraceny bez oznámení.

Podrobnosti o `Update` zpracování chyb naleznete v článku [Sada záznamů: Jak sady záznamů aktualizovat záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

### <a name="example"></a>Příklad

Viz článek [Transakce: Provedení transakce v sadě záznamů (ODBC).](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDatabase – třída](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordView – třída](../../mfc/reference/crecordview-class.md)
