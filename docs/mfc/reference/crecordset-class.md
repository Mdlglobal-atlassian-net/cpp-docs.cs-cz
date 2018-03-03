---
title: "CRecordset – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c2375739fe4d8442d4ecb7a1514641d45de4a8be
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="crecordset-class"></a>CRecordset – třída
Představuje sadu záznamy ze zdroje dat vybraná.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CRecordset : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CRecordset::CRecordset](#crecordset)|Vytvoří `CRecordset` objektu. Odvozené třídy musí poskytovat konstruktor, který volá tento jeden.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CRecordset::AddNew](#addnew)|Připraví pro přidávání nového záznamu. Volání `Update` dokončit přidání.|  
|[CRecordset::CanAppend](#canappend)|Vrátí nenulové hodnoty, pokud nové záznamy lze přidat do sady záznamů prostřednictvím `AddNew` – členská funkce.|  
|[CRecordset::CanBookmark](#canbookmark)|Vrátí nenulové hodnoty, pokud sada záznamu podporuje záložky.|  
|[CRecordset::Cancel](#cancel)|Zruší asynchronní operaci nebo proces z druhé vlákna.|  
|[CRecordset::CancelUpdate](#cancelupdate)|Zruší všechny čekající aktualizace z důvodu `AddNew` nebo `Edit` operaci.|  
|[CRecordset::CanRestart](#canrestart)|Vrátí nenulovou Pokud `Requery` lze volat pro spusťte znovu dotaz sady záznamů.|  
|[CRecordset::CanScroll](#canscroll)|Vrátí nenulové hodnoty, pokud lze procházet záznamů.|  
|[CRecordset::CanTransact](#cantransact)|Vrátí nenulové hodnoty, pokud je zdroj dat podporuje transakce.|  
|[CRecordset::CanUpdate](#canupdate)|Vrátí nenulové hodnoty, pokud lze aktualizovat sadu záznamů (můžete přidat, aktualizaci nebo odstranění záznamů).|  
|[CRecordset::CheckRowsetError](#checkrowseterror)|Volá se budou zpracovávat chyby vygenerovaných během načítání záznamu.|  
|[CRecordset::Requery](#close)|Zavře sady záznamů a ODBC **HSTMT** s ním spojená.|  
|[CRecordset::Delete](#delete)|Odstraní záznam na aktuální záznam ze sady záznamů. Po odstranění se musí explicitně přejít k jinému záznamu.|  
|[CRecordset::DoBulkFieldExchange](#dobulkfieldexchange)|Voláno k výměně hromadné řádky dat ze zdroje dat na sadu záznamů. Implementuje hromadně výměna pole záznamu (Bulk RFX).|  
|[CRecordset::DoFieldExchange](#dofieldexchange)|Volá se pro výměnu dat (v obou směrech) mezi pole datových členů sady záznamů a odpovídající záznam na datovém zdroji. Implementuje záznam pole (exchange – RFX).|  
|[CRecordset::Edit](#edit)|Připraví změny záznam na aktuální záznam. Volání `Update` dokončete úpravu.|  
|[CRecordset::FlushResultSet](#flushresultset)|Vrátí nenulové hodnoty, pokud existuje jiný výsledek nastavit mají být načteny, při použití předdefinovaný dotaz.|  
|[CRecordset::GetBookmark](#getbookmark)|Hodnota záložky záznamu přiřadí objekt parametr.|  
|[CRecordset::GetDefaultConnect](#getdefaultconnect)|Volá se získat výchozí připojovací řetězec.|  
|[CRecordset::GetDefaultSQL](#getdefaultsql)|Volá se získat výchozí řetězec SQL k provedení.|  
|[CRecordset::GetFieldValue](#getfieldvalue)|Vrátí hodnotu pole v sadě záznamů.|  
|[CRecordset::GetODBCFieldCount](#getodbcfieldcount)|Vrátí počet polí v sadě záznamů.|  
|[CRecordset::GetODBCFieldInfo](#getodbcfieldinfo)|Vrátí určité informace o pole v sadě záznamů.|  
|[CRecordset::GetRecordCount](#getrecordcount)|Vrátí počet záznamů v sadě záznamů.|  
|[CRecordset::GetRowsetSize](#getrowsetsize)|Vrátí počet záznamů, který chcete načíst během jednoho načtení.|  
|[CRecordset::GetRowsFetched](#getrowsfetched)|Vrátí skutečný počet řádků, které jsou načteny.|  
|[CRecordset::GetRowStatus](#getrowstatus)|Vrátí stav řádek po fetch.|  
|[CRecordset::GetSQL](#getsql)|Získá řetězec SQL, které jsou použity k výběru záznamy pro sady záznamů.|  
|[CRecordset::GetStatus](#getstatus)|Získá stav sada záznamů: index na aktuální záznam a jestli byl získán konečný počet záznamů.|  
|[CRecordset::GetTableName](#gettablename)|Získá název tabulky, na kterých je založena sady záznamů.|  
|[CRecordset::IsBOF](#isbof)|Vrátí nenulové hodnoty, pokud sada záznamů obsahuje byl umístěn před první záznam. Neexistuje aktuální záznam.|  
|[CRecordset::IsDeleted](#isdeleted)|Vrátí nenulové hodnoty, pokud sada záznamů umístěna na odstraněného záznamu.|  
|[CRecordset::IsEOF](#iseof)|Vrátí nenulové hodnoty, pokud sada záznamů obsahuje byl umístěn za poslední záznam. Neexistuje aktuální záznam.|  
|[CRecordset::IsFieldDirty](#isfielddirty)|Vrátí nenulovou došlo ke změně v zadaném poli záznam na aktuální záznam.|  
|[CRecordset::IsFieldNull](#isfieldnull)|Vrátí nenulové hodnoty, pokud v zadaném poli záznam na aktuální záznam má hodnotu null (nemá žádnou hodnotu).|  
|[CRecordset::IsFieldNullable](#isfieldnullable)|Vrátí nenulové hodnoty, pokud v zadaném poli záznam na aktuální záznam můžete nastavit na hodnotu null (nutnosti žádná hodnota).|  
|[CRecordset::IsOpen](#isopen)|Vrátí nenulovou Pokud `Open` byla volána dříve.|  
|[CRecordset::Move](#move)|Umisťuje sadu záznamů na zadaný počet záznamů z aktuální záznam v obou směrech.|  
|[CRecordset::MoveFirst](#movefirst)|Umisťuje záznam na aktuální záznam na první záznam v sadě záznamů. Testování pro `IsBOF` první.|  
|[CRecordset::MoveLast](#movelast)|Umisťuje záznam na aktuální záznam na poslední záznam nebo na poslední sadu řádků. Testování pro `IsEOF` první.|  
|[CRecordset::MoveNext](#movenext)|Umisťuje záznam na aktuální záznam na další záznam nebo na další sadu řádků. Testování pro `IsEOF` první.|  
|[CRecordset::MovePrev](#moveprev)|Umisťuje záznam na aktuální záznam na předchozího záznamu nebo na předchozí řádků. Testování pro `IsBOF` první.|  
|[CRecordset::OnSetOptions](#onsetoptions)|Voláno k nastavení možností (používá se na výběr) pro zadaný příkaz ODBC.|  
|[CRecordset::OnSetUpdateOptions](#onsetupdateoptions)|Volá se pro nastavení možností (používá se při aktualizaci) pro zadaný příkaz ODBC.|  
|[CRecordset::Open](#open)|Otevře sadu záznamů načtením tabulky nebo provedením dotazu, který sada záznamů představuje.|  
|[CRecordset::RefreshRowset](#refreshrowset)|Aktualizuje data a stav zadané řádky.|  
|[CRecordset::Requery](#requery)|Spustí dotaz sady záznamů znovu a aktualizujte vybrané záznamy.|  
|[CRecordset::SetAbsolutePosition](#setabsoluteposition)|Umisťuje sadu záznamů na záznam odpovídající číslo zadaný záznam.|  
|[CRecordset::SetBookmark](#setbookmark)|Umisťuje sadu záznamů na zadaný záložkou záznam.|  
|[CRecordset::SetFieldDirty](#setfielddirty)|Označí aktuální záznam v zadaném poli jako změnit.|  
|[CRecordset::SetFieldNull](#setfieldnull)|Nastaví hodnotu zadaného pole v aktuálním záznamu na hodnotu null (nutnosti žádná hodnota).|  
|[CRecordset::SetLockingMode](#setlockingmode)|Nastaví režim uzamčení "optimistické" uzamčení (výchozí) nebo "pesimistické" uzamčení. Určuje, jak jsou záznamy uzamčeny aktualizací.|  
|[CRecordset::SetParamNull](#setparamnull)|Zadaný parametr nastaví na hodnotu null (nutnosti žádná hodnota).|  
|[CRecordset::SetRowsetCursorPosition](#setrowsetcursorposition)|Umisťuje kurzor na zadaný řádku v sadě řádků.|  
|[CRecordset::SetRowsetSize](#setrowsetsize)|Určuje počet záznamů, které chcete načíst během fetch.|  
|[CRecordset::Update](#update)|Dokončení `AddNew` nebo `Edit` operace uložením nových nebo upravených dat na datovém zdroji.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CRecordset::m_hstmt](#m_hstmt)|Obsahuje popisovače sady záznamů rozhraní ODBC příkaz. Typ `HSTMT`.|  
|[CRecordset::m_nFields](#m_nfields)|Obsahuje počet pole datových členů v sadě záznamů. Typ `UINT`.|  
|[CRecordset::m_nParams](#m_nparams)|Obsahuje počet parametry datových členů v sadě záznamů. Typ `UINT`.|  
|[CRecordset::m_pDatabase](#m_pdatabase)|Obsahuje odkazy `CDatabase` objekt, pomocí kterého je sada záznamů připojený ke zdroji dat.|  
|[CRecordset::m_strFilter](#m_strfilter)|Obsahuje `CString` jazyka SQL (Structured Query), který určuje `WHERE` klauzule. Použít jako filtr, chcete-li vybrat pouze ty záznamy, které splňují určitá kritéria.|  
|[CRecordset::m_strSort](#m_strsort)|Obsahuje `CString` SQL, který určuje `ORDER BY` klauzule. Použít k řízení řazení záznamů.|  
  
## <a name="remarks"></a>Poznámky  
 Označuje jako "sady záznamů," `CRecordset` objekty jsou obvykle používány ve dvou formách: dynamické sady a snímky. Dynamická sada zůstane synchronizovaná s aktualizace dat od jiných uživatelů. Snímek je statické zobrazení dat. Každý formulář představuje sadu záznamů pevné v době, kdy je otevření sady záznamů, ale při posouvání na záznam v dynamická sada odráží změny následně provedené na záznam, pomocí jiných uživatelů nebo pomocí jiné sady záznamů ve vaší aplikaci.  
  
> [!NOTE]
>  Pokud pracujete s třídy objektů DAO (Data Access), nikoli třídy připojení ODBC (Open Database), použijte třídu [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) místo. Další informace najdete v článku [přehled: programování databáze](../../data/data-access-programming-mfc-atl.md).  
  
 Pro práci s buď druh sady záznamů, obvykle odvodíte třídu specifické pro aplikaci záznamů z `CRecordset`. Sady záznamů vybírají záznamy ze zdroje dat a pak můžete:  
  
-   Procházet záznamy.  
  
-   Aktualizovat záznamy a určete režim uzamčení.  
  
-   Sada záznamů omezit záznamy, které vybere z dostupných ve zdroji dat filtrujte.  
  
-   Seřadí sadu záznamů.  
  
-   Parametrizace sady záznamů, chcete-li přizpůsobit svůj výběr s informacemi o není známý až při spuštění.  
  
 Pokud chcete používat vlastní třídy, otevřete databázi a vytvořte objekt sady záznamů, předávání konstruktoru ukazatel na vaše `CDatabase` objektu. Potom zavolejte sady záznamů **otevřete** – členská funkce, kde můžete určit, zda je objekt dynamická sada nebo snímek. Volání metody **otevřete** vybere data ze zdroje dat. Po otevření objekt sady záznamů použijte její funkce a data členy člen projděte záznamy a pracovat s nimi. Operace, které jsou k dispozici závisí na tom, zda objekt dynamická sada nebo snímek, jestli je aktualizovat nebo jen pro čtení (závisí na možnosti připojení ODBC (Open Database) zdroj dat), a jestli jste implementovali hromadné načítání řádků. K aktualizaci záznamů, které může mít změnily nebo přibyly od **otevřete** volání, volání objektu **Requery –** – členská funkce. Volání objektu **Zavřít** členské funkce a odstraňte objekt po dokončení s ním.  
  
 V odvozené `CRecordset` třídy, zaznamenejte pole (exchange – RFX) nebo hromadná výměna pole záznamu (Bulk RFX) se používá k čtení a aktualizaci polí záznamů.  
  
 Další informace o výměně pole sady záznamů a záznamů, najdete v článcích [přehled: databáze programování](../../data/data-access-programming-mfc-atl.md), [záznamů (ODBC)](../../data/odbc/recordset-odbc.md), [sada záznamů: načítání záznamů v hromadné (ODBC) ](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md), a [záznam pole (Exchange – RFX)](../../data/odbc/record-field-exchange-rfx.md). Zaměřená na dynamické sady a snímky, najdete v článcích [dynamická sada](../../data/odbc/dynaset.md) a [snímku](../../data/odbc/snapshot.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CRecordset`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdb.h  
  
##  <a name="addnew"></a>CRecordset::AddNew  
 Připraví pro přidávání nového záznamu do tabulky.  
  
```  
virtual void AddNew();
```  
  
### <a name="remarks"></a>Poznámky  
 Je třeba zavolat [Requery –](#requery) – členská funkce zobrazíte nově přidaného záznamu. Pole záznamu jsou původně hodnotu Null. (V terminologii databáze Null znamená "nutnosti žádná hodnota" a není stejný jako **NULL** v jazyce C++.) Pokud chcete provést operaci, musí volat [aktualizace](#update) – členská funkce. **Aktualizace** uloží změny do zdroje dat.  
  
> [!NOTE]
>  Pokud jste implementovali hromadné načítání řádků, nelze volat `AddNew`. Tato akce způsobí selhání kontrolního výrazu. Přestože třída `CRecordset` neposkytuje mechanismus pro hromadnou aktualizaci řádků dat, můžete napsat vlastní funkce pomocí funkce rozhraní API ODBC **SQLSetPos**. Další informace o hromadné načítání řádků, najdete v článku [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 `AddNew`připraví nový, prázdný záznam pomocí sady záznamů pole datových členů. Po zavolání metody `AddNew`, nastavte hodnoty, které chcete v sadě záznamů pole datových členů. (Není nutné volat [upravit](#edit) – členská funkce pro tento účel; použijte **upravit** pouze pro existující záznamy.) Při následně volání **aktualizace**, změněné hodnoty pole datových členů jsou uloženy na datovém zdroji.  
  
> [!CAUTION]
>  Pokud se posunete na nový záznam před voláním **aktualizace**, nový záznam dojde ke ztrátě, a je zadána žádná upozornění.  
  
 Pokud zdroj dat podporuje transakce, můžete provést vaší `AddNew` volání součástí transakce. Další informace o transakcích, najdete v části třídy [CDatabase](../../mfc/reference/cdatabase-class.md). Všimněte si, že by měly volat [CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) před voláním `AddNew`.  
  
> [!NOTE]
>  Pro dynamické sady jsou přidány nové záznamy sadě záznamů jako poslední záznam. Přidání záznamů nejsou přidány do snímky; je třeba volat **Requery** aktualizuje sadu záznamů.  
  
 Není povolen pro volání `AddNew` pro sadu záznamů jejichž **otevřete** – členská funkce nebyla volána. A `CDBException` je vyvolána při volání `AddNew` pro sady záznamů, který nelze připojit. Můžete určit, zda je záznamů aktualizovat voláním [CanAppend](#canappend).  
  
 Další informace naleznete v následujících článcích: [sada záznamů: Jak sady záznamů aktualizace záznamů (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md), [sada záznamů: přidávání, aktualizace a odstranění záznamů (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), a [(transakce Rozhraní ODBC)](../../data/odbc/transaction-odbc.md).  
  
### <a name="example"></a>Příklad  
 Najdete v článku [transakce: provádění transakcí v sadě záznamů (rozhraní ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).  
  
##  <a name="canappend"></a>CRecordset::CanAppend  
 Určuje, zda dříve otevřen sada záznamů umožňuje přidat nové záznamy.  
  
```  
BOOL CanAppend() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě, že sada záznamů umožňuje přidání nové záznamy; jinak 0. `CanAppend`Vrátí 0, pokud jste otevřeli sada záznamů jen pro čtení.  
  
##  <a name="canbookmark"></a>CRecordset::CanBookmark  
 Určuje, zda sada záznamů umožňuje označit záznamů pomocí záložky.  
  
```  
BOOL CanBookmark() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud sada záznamu podporuje záložky; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je nezávislá **CRecordset::useBookmarks** možnost `dwOptions` parametr [otevřete](#open) – členská funkce. `CanBookmark`Určuje, zda daný ovladač ODBC a kurzor typ podporu záložky. **CRecordset::useBookmarks** označuje, zda záložky bude k dispozici, pokud jsou podporované.  
  
> [!NOTE]
>  Záložky nejsou podporovány na dopředné sady záznamů.  
  
 Další informace o záložky a navigaci v sadě záznamů, najdete v článcích [sada záznamů: záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) a [sada záznamů: posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).  
  
##  <a name="cancel"></a>CRecordset::Cancel  
 Požadavky, že zdroj dat zrušit asynchronní operace probíhá nebo proces z druhé vlákna.  
  
```  
void Cancel();
```  
  
### <a name="remarks"></a>Poznámky  
 Upozorňujeme, že třídy knihovny MFC rozhraní ODBC už použít asynchronní zpracování; k provedení určité operace asychronous, musí přímo volat rozhraní API ODBC funkce **SQLSetConnectOption**. Další informace naleznete v tématu "Provádění funkce asynchronně" v *ODBC SDK – Příručka pro vývojáře*.  
  
##  <a name="cancelupdate"></a>CRecordset::CancelUpdate  
 Zruší všechny čekající aktualizace, způsobené [upravit](#edit) nebo [AddNew](#addnew) operace, před [aktualizace](#update) je volána.  
  
```  
void CancelUpdate();
```  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Tento člen funkce se nedá použít na sady záznamů, které používají hromadné načítání řádků, protože takové sady záznamů nelze volat **upravit**, `AddNew`, nebo **aktualizace**. Další informace o hromadné načítání řádků, najdete v článku [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Pokud kontrola automatické změny pole povolena, `CancelUpdate` obnoví členské proměnné na hodnoty měly před **upravit** nebo `AddNew` jinak, zůstane žádné změny hodnot. Ve výchozím nastavení je kontrola automatické pole povolena při otevření sady záznamů. Pokud chcete zakázat, je nutné zadat **CRecordset::noDirtyFieldCheck** v `dwOptions` parametr [otevřete](#open) – členská funkce.  
  
 Další informace o aktualizaci dat, najdete v článku [sada záznamů: přidávání, aktualizace a odstranění záznamů (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md).  
  
##  <a name="canrestart"></a>CRecordset::CanRestart  
 Určuje, zda sada záznamů umožňuje restartování jeho dotaz (Chcete-li obnovit svoje záznamy o) voláním **Requery –** – členská funkce.  
  
```  
BOOL CanRestart() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je povoleno requery; jinak 0.  
  
##  <a name="canscroll"></a>CRecordset::CanScroll  
 Určuje, zda sada záznamů umožňuje posouvání.  
  
```  
BOOL CanScroll() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě, že sada záznamů umožňuje posouvání; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o posouvání, najdete v článku [sada záznamů: posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).  
  
##  <a name="cantransact"></a>CRecordset::CanTransact  
 Určuje, zda sada záznamů umožňuje transakce.  
  
```  
BOOL CanTransact() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě, že sada záznamů umožňuje transakce; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v článku [transakce (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="canupdate"></a>CRecordset::CanUpdate  
 Určuje, zda lze aktualizovat sadu záznamů.  
  
```  
BOOL CanUpdate() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud lze aktualizovat sadu záznamů; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Sady záznamů může být jen pro čtení, pokud příslušný zdroj dat je jen pro čtení, nebo pokud jste zadali **CRecordset::readOnly** v `dwOptions` parametr při otevření sady záznamů.  
  
##  <a name="checkrowseterror"></a>CRecordset::CheckRowsetError  
 Volá se budou zpracovávat chyby vygenerovaných během načítání záznamu.  
  
```  
virtual void CheckRowsetError(RETCODE nRetCode);
```  
  
### <a name="parameters"></a>Parametry  
 `nRetCode`  
 Funkce rozhraní API ODBC návratový kód. Podrobnosti najdete v tématu poznámky.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člena virtuální zpracovává chyby, ke kterým dochází, když jsou načteno záznamů, a jsou užitečné při hromadné načítání řádků. Možná budete chtít zvážit přepsání `CheckRowsetError` implementovat vlastní zpracování chyb.  
  
 `CheckRowsetError`je volána automaticky v navigačním operaci kurzoru, jako například **otevřete**, **Requery –**, nebo jakoukoli **přesunout** operaci. Návratová hodnota funkce rozhraní API ODBC je předán **SQLExtendedFetch**. V následující tabulce jsou uvedeny možné hodnoty `nRetCode` parametr.  
  
|nRetCode|Popis|  
|--------------|-----------------|  
|**SQL_SUCCESS**|Funkce byla dokončena úspěšně; nejsou dostupné žádné další informace.|  
|**SQL_SUCCESS_WITH_INFO**|Funkce byla úspěšně dokončena, případně s méně závažná chyba. Další informace získáte pomocí volání **funkce SQLError**.|  
|**SQL_NO_DATA_FOUND**|Mít byl načteny všechny řádky ze sady výsledků.|  
|**SQL_ERROR.**|Funkce se nezdařila. Další informace získáte pomocí volání **funkce SQLError**.|  
|**SQL_INVALID_HANDLE**|Funkce se nezdařila z důvodu prostředí neplatný popisovač, popisovač připojení nebo popisovač příkazu. To znamená chybě programování. Žádné další informace najdete na webu **funkce SQLError**.|  
|`SQL_STILL_EXECUTING`|Funkci, která byla spuštěna asynchronně stále probíhá. Všimněte si, že ve výchozím nastavení, MFC se nikdy předat tuto hodnotu na `CheckRowsetError`; MFC bude pokračovat volání **SQLExtendedFetch** dokud už vrátí `SQL_STILL_EXECUTING`.|  
  
 Další informace o **funkce SQLError**, najdete v části Windows SDK. Další informace o hromadné načítání řádků, najdete v článku [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="close"></a>CRecordset::Requery  
 Zavře sady záznamů.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Poznámky  
 ODBC **HSTMT** a všechny paměti rozhraní přidělené sady záznamů jsou navrácena. Obvykle po volání **Zavřít**, pokud byl přidělen s se odstranit objekt sady záznamů C++ **nové**.  
  
 Můžete volat **otevřete** znovu po volání **Zavřít**. Díky tomu můžete znovu použít objekt sady záznamů. Alternativou je volat **Requery –**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDatabase#17](../../mfc/codesnippet/cpp/crecordset-class_1.cpp)]  
  
##  <a name="crecordset"></a>CRecordset::CRecordset  
 Vytvoří `CRecordset` objektu.  
  
```  
CRecordset(CDatabase* pDatabase = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pDatabase`  
 Obsahuje odkazy `CDatabase` objekt nebo hodnota **NULL**. Není-li **NULL** a `CDatabase` objektu **otevřete** – členská funkce nebyla zavolána pro připojení ke zdroji dat, sada záznamů pokusí otevřít pro vás během vlastní **otevřete**  volání. Pokud předáte **NULL**, `CDatabase` objekt je vytvořená a používáte informace o zdroji dat jste zadali při odvozené třídě sada záznamů s ClassWizard připojením.  
  
### <a name="remarks"></a>Poznámky  
 Můžete buď používat `CRecordset` přímo nebo odvodit třídu specifické pro aplikaci z `CRecordset`. ClassWizard můžete použít k odvození třídy sady záznamů.  
  
> [!NOTE]
>  Odvozené třídy *musí* zadat vlastní konstruktor. V konstruktoru odvozené třídy, volat konstruktor `CRecordset::CRecordset`, předáním příslušné parametry společně.  
  
 Předat **NULL** do sady záznamů konstruktoru tak, aby měl `CDatabase` objekt vytvořený a připojení pro vás automaticky. To je užitečné zkratkou, která není nutné vytvořit a připojit se `CDatabase` objekt před vytvořením sady záznamů.  
  
### <a name="example"></a>Příklad  
 Další informace najdete v článku [sada záznamů: deklarování třídy pro tabulku (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).  
  
##  <a name="delete"></a>CRecordset::Delete  
 Odstraní záznam na aktuální záznam.  
  
```  
virtual void Delete();
```  
  
### <a name="remarks"></a>Poznámky  
 Po úspěšné odstranění sady záznamů pole datových členů nastaveny na hodnotu Null a musí explicitně volání jednoho z **přesunout** funkce opustit odstraněného záznamu. Po přesunutí mimo odstraněné záznam není možné vrátit se k němu. Pokud zdroj dat podporuje transakce, můžete provést **odstranit** volání součástí transakce. Další informace najdete v článku [transakce (ODBC)](../../data/odbc/transaction-odbc.md).  
  
> [!NOTE]
>  Pokud jste implementovali hromadné načítání řádků, nelze volat **odstranit**. Tato akce způsobí selhání kontrolního výrazu. Přestože třída `CRecordset` neposkytuje mechanismus pro hromadnou aktualizaci řádků dat, můžete napsat vlastní funkce pomocí funkce rozhraní API ODBC **SQLSetPos**. Další informace o hromadné načítání řádků, najdete v článku [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
> [!CAUTION]
>  Musí být aktualizovat sadu záznamů a musí být platný záznam v sadě záznamů při volání **odstranit**, jinak dojde k chybě. Například, pokud jste odstranit záznam, ale není přejděte na nový záznam před voláním **odstranit** znovu **odstranit** vyvolá [CDBException](../../mfc/reference/cdbexception-class.md).  
  
 Na rozdíl od [AddNew](#addnew) a [upravit](#edit), volání **odstranit** nenásleduje volání [aktualizace](#update). Pokud **odstranit** volání selže, pole data členové jsou ponechána beze změny.  
  
### <a name="example"></a>Příklad  
 Tento příklad ukazuje na sadu záznamů na rámečku funkce vytvořit. Příklad předpokládá existenci `m_dbCust`, členské proměnné typu `CDatabase` už připojeno ke zdroji dat.  
  
 [!code-cpp[NVC_MFCDatabase#18](../../mfc/codesnippet/cpp/crecordset-class_2.cpp)]  
  
##  <a name="dobulkfieldexchange"></a>CRecordset::DoBulkFieldExchange  
 Voláno k výměně hromadné řádky dat ze zdroje dat na sadu záznamů. Implementuje hromadně výměna pole záznamu (Bulk RFX).  
  
```  
virtual void DoBulkFieldExchange(CFieldExchange* pFX);
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Ukazatel [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) objektu. Rozhraní bude již nastavili tento objekt určit kontext pro operaci exchange pole.  
  
### <a name="remarks"></a>Poznámky  
 Pokud se implementuje hromadné načítání řádků, volá rámec této – členská funkce automaticky posílat data ze zdroje dat do objektu sady záznamů. `DoBulkFieldExchange`také vytvoří vazbu parametry datových členů, pokud existuje, zástupných symbolů parametrů v příkaz SQL pro výběr sady záznamů.  
  
 Pokud není implementována hromadné načítání řádků, volá framework [DoFieldExchange](#dofieldexchange). Chcete-li implementovat hromadné načítání řádků, je nutné zadat `CRecordset::useMultiRowFetch` možnost `dwOptions` parametr v [otevřete](#open) – členská funkce.  
  
> [!NOTE]
> `DoBulkFieldExchange`je k dispozici pouze v případě, že používáte třídy odvozené od `CRecordset`. Pokud jste vytvořili objekt sady záznamů přímo z `CRecordset`, musí volat [GetFieldValue](#getfieldvalue) – členská funkce načíst data.  
  
 Hromadná výměna pole záznamu (Bulk RFX) je podobná výměna pole záznamu (RFX). Data se automaticky přenáší ze zdroje dat do objektu sady záznamů. Však nelze volat `AddNew`, **upravit**, **odstranit**, nebo **aktualizace** chcete přenést změny zpět do zdroje dat. Třída `CRecordset` aktuálně neposkytuje mechanismus pro hromadnou aktualizaci řádků dat; však můžete napsat vlastní funkce pomocí funkce rozhraní API ODBC **SQLSetPos**.  
  
 Všimněte si, že ClassWizard nepodporuje Hromadná výměna pole záznamu; Proto je nutné přepsat `DoBulkFieldExchange` ručně pomocí volání funkce RFX hromadného zápisu. Další informace o těchto funkcích naleznete v tématu [funkce výměny polí v záznamu](../../mfc/reference/record-field-exchange-functions.md).  
  
 Další informace o hromadné načítání řádků, najdete v článku [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Související informace najdete v článku [výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
##  <a name="dofieldexchange"></a>CRecordset::DoFieldExchange  
 Volá se pro výměnu dat (v obou směrech) mezi pole datových členů sady záznamů a odpovídající záznam na datovém zdroji. Implementuje záznam pole (exchange – RFX).  
  
```  
virtual void DoFieldExchange(CFieldExchange* pFX);
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Ukazatel [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) objektu. Rozhraní bude již nastavili tento objekt určit kontext pro operaci exchange pole.  
  
### <a name="remarks"></a>Poznámky  
 Při hromadné načítání řádků není implementována, volá rámec této – členská funkce pro automaticky výměnu dat mezi pole datových členů z objektu sady záznamů a na odpovídající sloupce ve zdroji dat na aktuální záznam. `DoFieldExchange`také vytvoří vazbu parametry datových členů, pokud existuje, zástupných symbolů parametrů v příkaz SQL pro výběr sady záznamů.  
  
 Pokud se implementuje hromadné načítání řádků, zavolá rozhraní [DoBulkFieldExchange](#dobulkfieldexchange). Chcete-li implementovat hromadné načítání řádků, je nutné zadat `CRecordset::useMultiRowFetch` možnost `dwOptions` parametr v [otevřete](#open) – členská funkce.  
  
> [!NOTE]
> `DoFieldExchange`je k dispozici pouze v případě, že používáte třídy odvozené od `CRecordset`. Pokud jste vytvořili objekt sady záznamů přímo z `CRecordset`, musí volat [GetFieldValue](#getfieldvalue) – členská funkce načíst data.  
  
 Výměna pole dat, nazývá výměna pole záznamu (RFX), funguje v obou směrech: objekt sady záznamů pole datových členů na pole záznamu ve zdroji dat a ze záznamu ve zdroji dat do objektu sady záznamů.  
  
 Jedinou akcí, je obvykle nutné provést při implementaci `DoFieldExchange` pro odvozené sady záznamů třídy je vytvoření třídy s ClassWizard a zadejte názvy a datové typy pole datových členů. Může také přidat kód do co ClassWizard zapisuje zadat parametry datových členů nebo řešit všechny sloupce, které můžete vytvořit vazbu dynamicky. Další informace najdete v článku [sada záznamů: dynamické vazby datových sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
 Po deklarování vaší třídy odvozené sady záznamů s ClassWizard zapisuje Průvodce přepsání `DoFieldExchange` , která se podobá následujícímu příkladu:  
  
 [!code-cpp[NVC_MFCDatabase#19](../../mfc/codesnippet/cpp/crecordset-class_3.cpp)]  
  
 Další informace o funkce RFX, naleznete v tématu [funkce výměny polí v záznamu](../../mfc/reference/record-field-exchange-functions.md).  
  
 Další příklady a podrobnosti o `DoFieldExchange`, najdete v článku [výměna polí záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Obecné informace o RFX, najdete v článku [výměna pole záznamu](../../data/odbc/record-field-exchange-rfx.md).  
  
##  <a name="edit"></a>CRecordset::Edit  
 Umožňuje změny záznam na aktuální záznam.  
  
```  
virtual void Edit();
```  
  
### <a name="remarks"></a>Poznámky  
 Po zavolání metody **upravit**, můžete změnit pole datových členů přímo resetováním jejich hodnot. Tato operace nebude dokončena při následně volání [aktualizace](#update) – členská funkce a uložit provedené změny na datovém zdroji.  
  
> [!NOTE]
>  Pokud jste implementovali hromadné načítání řádků, nelze volat **upravit**. Tato akce způsobí selhání kontrolního výrazu. Přestože třída `CRecordset` neposkytuje mechanismus pro hromadnou aktualizaci řádků dat, můžete napsat vlastní funkce pomocí funkce rozhraní API ODBC **SQLSetPos**. Další informace o hromadné načítání řádků, najdete v článku [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 **Upravit** uloží hodnoty datových členů sady záznamů. Když zavoláte **upravit**, provést změny, potom volat **upravit** znovu, obnoví hodnoty záznamu se nacházely před první **upravit** volání.  
  
 V některých případech můžete chtít aktualizovat sloupec tím, že s hodnotou Null (obsahující žádná data). Chcete-li to provést, volejte [SetFieldNull](#setfieldnull) s parametrem **TRUE** označit pole hodnotu Null; to také způsobí, že sloupec aktualizovat. Pokud chcete, aby pole, které chcete být napsané ke zdroji dat i v případě, že její hodnota nezměnilo, volejte [SetFieldDirty](#setfielddirty) s parametrem **TRUE**. Tento postup funguje i v případě, že pole měl hodnotu Null.  
  
 Pokud zdroj dat podporuje transakce, můžete provést **upravit** volání součástí transakce. Všimněte si, že by měly volat [CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) před voláním **upravit** a po otevření sady záznamů. Všimněte si, že volání [CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) nenahrazuje pro volání **aktualizace** k dokončení **upravit** operaci. Další informace o transakcích, najdete v části třídy [CDatabase](../../mfc/reference/cdatabase-class.md).  
  
 V závislosti na aktuální režim uzamčení, může být uzamčen záznam aktualizované **upravit** dokud zavoláte **aktualizace** nebo se posouvají na jiný záznam, nebo může být uzamčena pouze během **upravit** volání. Můžete změnit režim uzamčení s [SetLockingMode](#setlockingmode).  
  
 Pokud se posunete na nový záznam před voláním obnoví předchozí hodnotu na aktuální záznam **aktualizace**. A `CDBException` je vyvolána při volání **upravit** pro sady záznamů, která nelze aktualizovat nebo pokud neexistuje aktuální záznam.  
  
 Další informace najdete v článcích [transakce (ODBC)](../../data/odbc/transaction-odbc.md) a [sada záznamů: zamykání záznamů (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDatabase#20](../../mfc/codesnippet/cpp/crecordset-class_4.cpp)]  
  
##  <a name="flushresultset"></a>CRecordset::FlushResultSet  
 Načte další sadu výsledků předdefinovaný dotaz (uloženou proceduru), pokud existuje více sad výsledků dotazu.  
  
```  
BOOL FlushResultSet();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud existuje více sad výsledků dotazu, které mají být načteny; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 By měly volat `FlushResultSet` pouze po zcela dokončení umístěte kurzor na aktuální sadu výsledků dotazu. Všimněte si, že pokud načítáte Další výsledek nastavit, že zavoláte `FlushResultSet`, ukazatelem není platný v dané sadě výsledků; by měly volat [MoveNext](#movenext) – členská funkce po volání `FlushResultSet`.  
  
 Pokud předdefinovaný dotaz používá výstupní parametr nebo vstupní a výstupní parametry, musí volat `FlushResultSet` dokud vrátí `FALSE` (hodnota 0), aby bylo možné získat hodnoty těchto parametrů.  
  
 `FlushResultSet`volání funkce rozhraní API ODBC `SQLMoreResults`. Pokud `SQLMoreResults` vrátí `SQL_ERROR` nebo `SQL_INVALID_HANDLE`, pak `FlushResultSet` vyvolá výjimku. Další informace o `SQLMoreResults`, najdete v části Windows SDK.  
  
 Uložená procedura musí mít vázané pole, pokud chcete volat `FlushResultSet`.  
  
### <a name="example"></a>Příklad  
 Následující kód předpokládá, že `COutParamRecordset` je `CRecordset`-odvozené objekt založený na předdefinovaný dotaz s parametrem vstupní a výstupní parametr a s více sad výsledků dotazu. Všimněte si strukturu [DoFieldExchange](#dofieldexchange) přepsat.  
  
 [!code-cpp[NVC_MFCDatabase#21](../../mfc/codesnippet/cpp/crecordset-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDatabase#22](../../mfc/codesnippet/cpp/crecordset-class_6.cpp)]  
  
##  <a name="getbookmark"></a>CRecordset::GetBookmark  
 Získá hodnotu záložku na aktuální záznam.  
  
```  
void GetBookmark(CDBVariant& varBookmark);
```  
  
### <a name="parameters"></a>Parametry  
 `varBookmark`  
 Odkaz na [CDBVariant](../../mfc/reference/cdbvariant-class.md) objekt reprezentující záložek na aktuální záznam.  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li zjistit, jestli jsou na sadu záznamů podporuje záložky, volejte [CanBookmark](#canbookmark). Pro záložky byly k dispozici, pokud jsou podporovány, je třeba nastavit **CRecordset::useBookmarks** možnost `dwOptions` parametr [otevřete](#open) – členská funkce.  
  
> [!NOTE]
>  Pokud záložky nepodporovaný nebo nedostupný, volání `GetBookmark` bude mít za následek výjimku hlášeny. Záložky nejsou podporovány na dopředné sady záznamů.  
  
 `GetBookmark`přiřadí hodnotě záložky aktuální záznam, který `CDBVariant` objektu. Chcete-li vrátit k kdykoli po přesunutí na jiný záznam, volejte [SetBookmark](#setbookmark) s odpovídajícím `CDBVariant` objektu.  
  
> [!NOTE]
>  Po určité operace sady záznamů záložky může již nebude platný. Například, pokud zavoláte `GetBookmark` následuje **Requery –**, nebude možné se vraťte do záznamu s `SetBookmark`. Volání [CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) zkontrolujte, zda můžete bezpečně volat `SetBookmark`.  
  
 Další informace o záložky a navigaci v sadě záznamů, najdete v článcích [sada záznamů: záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) a [sada záznamů: posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).  
  
##  <a name="getdefaultconnect"></a>CRecordset::GetDefaultConnect  
 Volá se získat výchozí připojovací řetězec.  
  
```  
virtual CString GetDefaultConnect();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CString` obsahující výchozí připojovací řetězec.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen získat výchozí připojovací řetězec pro zdroj dat, na kterých je založena na sadu záznamů volá framework. ClassWizard implementuje tuto funkci pro vás tím, že určíte stejný zdroj dat, který používáte v ClassWizard a získat informace o tabulek a sloupců. Pravděpodobně zjistíte, je vhodnější spoléhají na tuto výchozí připojení při vývoji vaší aplikace. Ale výchozí připojení nemusí být vhodný pro uživatele vaší aplikace. Pokud je to tento případ, by měl přeimplementovat tuto funkci zahození ClassWizard na verzi. Další informace o připojovacích řetězcích najdete v článku [datové zdroje (ODBC)](../../data/odbc/data-source-odbc.md).  
  
##  <a name="getdefaultsql"></a>CRecordset::GetDefaultSQL  
 Volá se získat výchozí řetězec SQL k provedení.  
  
```  
virtual CString GetDefaultSQL();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CString` obsahující výchozí příkaz jazyka SQL.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen získat příkaz výchozí SQL, na kterých je založena na sadu záznamů volá framework. To může být název tabulky nebo SQL **vyberte** příkaz.  
  
 Nepřímo zadejte příkaz jazyka SQL výchozí deklarováním třídu sady záznamů s ClassWizard a ClassWizard tato úloha provede za vás.  
  
 Pokud potřebujete příkaz SQL pro vlastní použití, volání `GetSQL`, který vrátí příkaz jazyka SQL, které jsou použity k výběru záznamy sady záznamů, pokud byl otevřen. Můžete upravit výchozí řetězec SQL v přepsání vaší třídy `GetDefaultSQL`. Můžete například zadat předdefinovaný dotaz pomocí volání **volání** příkaz. (Všimněte si, ale, že pokud upravíte `GetDefaultSQL`, budete také muset upravit `m_nFields` odpovídat počtu sloupců ve zdroji dat.)  
  
 Další informace najdete v článku [sada záznamů: deklarování třídy pro tabulku (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md).  
  
> [!CAUTION]
>  Název tabulky bude prázdný, pokud rozhraní nelze určit název tabulky, pokud bylo zadáno více názvů tabulek, nebo pokud **volání** příkaz nelze interpretovat. Všimněte si, že při použití **volání** příkazu nesmí vložení mezery mezi složené závorky a **volání** – klíčové slovo, ani vhodné vložit prázdné před složené závorky nebo před ním  **Vyberte** – klíčové slovo v **vyberte** příkaz.  
  
##  <a name="getfieldvalue"></a>CRecordset::GetFieldValue  
 Načte data v poli v aktuální záznam.  
  
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
 `lpszName`  
 Název pole.  
  
 *varValu*e  
 Odkaz na [CDBVariant](../../mfc/reference/cdbvariant-class.md) objekt, který se uloží hodnotu pole.  
  
 `nFieldType`  
 Datový typ rozhraní ODBC C pole. Pomocí výchozí hodnoty, **DEFAULT_FIELD_TYPE**, vynutí `GetFieldValue` určit typ C dat z datového typu SQL, na základě následující tabulky. Jinak můžete zadat data přímo zadejte nebo vyberte kompatibilní datový typ; Například můžete ukládat jakýkoli typ dat do **SQL_C_CHAR**.  
  
|C – datový typ|Datový typ SQL.|  
|-----------------|-------------------|  
|**SQL_C_BIT**|**SQL_BIT**|  
|**SQL_C_UTINYINT**|**SQL_TINYINT**|  
|**SQL_C_SSHORT**|**SQL_SMALLINT**|  
|**SQL_C_SLONG**|**SQL_INTEGER**|  
|**SQL_C_FLOAT**|**SQL_REAL**|  
|**SQL_C_DOUBLE**|**SQL_FLOATSQL_DOUBLE**|  
|**SQL_C_TIMESTAMP**|**SQL_DATESQL_TIMESQL_TIMESTAMP**|  
|**SQL_C_CHAR**|**SQL_NUMERICSQL_DECIMALSQL_BIGINTSQL_CHARSQL_VARCHARSQL_LONGVARCHAR**|  
|**SQL_C_BINARY**|**SQL_BINARYSQL_VARBINARYSQL_LONGVARBINARY**|  
  
 Další informace o typech dat rozhraní ODBC najdete v tématech "Datové typy SQL" a "C datové typy" v dodatku D sady Windows SDK.  
  
 `nIndex`  
 Index založený na nule pole.  
  
 `strValue`  
 Odkaz na [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt, který se uloží hodnotu pole převést na text, bez ohledu na datový typ tohoto pole.  
  
### <a name="remarks"></a>Poznámky  
 Pole můžete vyhledávat podle názvu nebo podle indexu. Hodnota pole můžete ukládat buď `CDBVariant` objekt nebo `CString` objektu.  
  
 Pokud jste implementovali hromadné načítání řádků, je vždycky nastavený na aktuální záznam na první záznam v sadě řádků. Použít `GetFieldValue` na záznam v rámci dané sady řádků, je třeba nejprve zavolat [SetRowsetCursorPosition](#setrowsetcursorposition) – členská funkce přesuňte kurzor na požadovaný řádek v této sadě řádků. Potom zavolejte `GetFieldValue` na příslušném řádku. Chcete-li implementovat hromadné načítání řádků, je nutné zadat `CRecordset::useMultiRowFetch` možnost `dwOptions` parametr v [otevřete](#open) – členská funkce.  
  
 Můžete použít `GetFieldValue` se dynamicky načíst pole v době běhu spíše než staticky je vazba v době návrhu. Například, pokud je nutné, aby deklarované objekt sady záznamů přímo z `CRecordset`, je nutné použít `GetFieldValue` načíst data v poli; pole záznamu (exchange – RFX) nebo hromadná výměna pole záznamu (Bulk RFX), není implementována.  
  
> [!NOTE]
>  Pokud je objekt sady záznamů deklarovat bez odvozování z `CRecordset`, není nutné načíst knihovny kurzorů ODBC. Knihovna kurzorů vyžaduje, aby obsahovaly sadu záznamů alespoň jeden sloupec vázané; ale při použití `CRecordset` přímo, žádné sloupce je vázána. Členské funkce [CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) a [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) řídit, jestli bude načten knihovna kurzorů.  
  
 `GetFieldValue`volání funkce rozhraní API ODBC **SQLGetData**. Pokud ovladač výstupy hodnota **SQL_NO_TOTAL** pro skutečné délce hodnota pole `GetFieldValue` vyvolá výjimku. Další informace o **SQLGetData**, najdete v části Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující vzorový kód ukazuje volání `GetFieldValue` pro objekt sady záznamů deklarovaný přímo z `CRecordset`.  
  
 [!code-cpp[NVC_MFCDatabase#23](../../mfc/codesnippet/cpp/crecordset-class_7.cpp)]  
  
> [!NOTE]
>  Na rozdíl od třídy DAO `CDaoRecordset`, `CRecordset` nemá `SetFieldValue` – členská funkce. Pokud vytvoříte objekt přímo z `CRecordset`, je efektivně jen pro čtení.  
  
 Další informace o hromadné načítání řádků, najdete v článku [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="getodbcfieldcount"></a>CRecordset::GetODBCFieldCount  
 Načte celkový počet polí v objektu sady záznamů.  
  
```  
short GetODBCFieldCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet polí v sadě záznamů.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o vytvoření sady záznamů, najdete v článku [sada záznamů: vytváření a uzavírání sad záznamů (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).  
  
##  <a name="getodbcfieldinfo"></a>CRecordset::GetODBCFieldInfo  
 Získá informace o pole v sadě záznamů.  
  
```  
void GetODBCFieldInfo(
    LPCTSTR lpszName,  
    CODBCFieldInfo& fieldinfo);

 
void GetODBCFieldInfo(
    short nIndex,  
    CODBCFieldInfo& fieldinfo);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Název pole.  
  
 `fieldinfo`  
 Odkaz na `CODBCFieldInfo` struktury.  
  
 `nIndex`  
 Index založený na nule pole.  
  
### <a name="remarks"></a>Poznámky  
 Jedna verze funkce umožňuje vyhledat pole podle názvu. Na další verzi umožňuje vyhledat pole podle indexu.  
  
 Popis o vrácené informace naleznete v tématu [codbcfieldinfo –](../../mfc/reference/codbcfieldinfo-structure.md) struktura.  
  
 Další informace o vytvoření sady záznamů, najdete v článku [sada záznamů: vytváření a uzavírání sad záznamů (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).  
  
##  <a name="getrecordcount"></a>CRecordset::GetRecordCount  
 Určuje velikost sady záznamů.  
  
```  
long GetRecordCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet záznamů v sadě záznamů; 0, pokud sada záznamů obsahuje žádné záznamy; nebo -1, pokud nelze určit počet záznamů.  
  
### <a name="remarks"></a>Poznámky  
  
> [!CAUTION]
>  Počet záznamů je udržovat jako "horní mez," záznam nejvyšší číslované zatím vidět jako uživatel prochází přes záznamy. Celkový počet záznamů je známé pouze po uživatele překročil poslední záznam. Z důvodů výkonu, není aktualizován počet při volání `MoveLast`. Chcete-li počet záznamů, volejte `MoveNext` opakovaně až `IsEOF` vrátí nenulovou hodnotu. Přidání záznamu prostřednictvím **CRecordset:AddNew** a **aktualizace** zvyšuje počet; odstranění záznamu prostřednictvím `CRecordset::Delete` snižuje počet.  
  
##  <a name="getrowsetsize"></a>CRecordset::GetRowsetSize  
 Získá aktuální nastavení pro počet řádků, který chcete načíst při daném načtení.  
  
```  
DWORD GetRowsetSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet řádků, které mají načíst při daném načtení.  
  
### <a name="remarks"></a>Poznámky  
 Pokud používáte hromadné načítání řádků, je výchozí velikost řádků při otevření sady záznamů 25; v opačném případě je 1.  
  
 Chcete-li implementovat hromadné načítání řádků, je nutné zadat `CRecordset::useMultiRowFetch` možnost v `dwOptions` parametr [otevřete](#open) – členská funkce. Chcete-li změnit nastavení velikosti sady řádků, volejte [SetRowsetSize](#setrowsetsize).  
  
 Další informace o hromadné načítání řádků, najdete v článku [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="getrowsfetched"></a>CRecordset::GetRowsFetched  
 Určuje, kolik záznamy byly načteny ve skutečnosti po fetch.  
  
```  
DWORD GetRowsFetched() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet řádků načíst ze zdroje dat po daném načtení.  
  
### <a name="remarks"></a>Poznámky  
 To je užitečné, když jste implementovali hromadné načítání řádků. Velikost sady řádků obvykle znamená, kolik řádků bude načten z: fetch; Celkový počet řádků v sadě záznamů, ale taky ovlivňuje kolik řádků bude načten v sadě řádků. Například pokud vaše sada záznamů obsahuje 10 záznamy s nastavením velikosti řádků 4, pak ve smyčce přes sadu záznamů voláním `MoveNext` bude mít za následek konečné řádků s pouze 2 záznamy.  
  
 Chcete-li implementovat hromadné načítání řádků, je nutné zadat `CRecordset::useMultiRowFetch` možnost v `dwOptions` parametr [otevřete](#open) – členská funkce. Chcete-li určit velikost sady řádků, volejte [SetRowsetSize](#setrowsetsize).  
  
 Další informace o hromadné načítání řádků, najdete v článku [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDatabase#24](../../mfc/codesnippet/cpp/crecordset-class_8.cpp)]  
  
##  <a name="getrowstatus"></a>CRecordset::GetRowStatus  
 Získá stav pro řádek v aktuální sadě řádků.  
  
```  
WORD GetRowStatus(WORD wRow) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `wRow`  
 Na základě jedné pozice řádku v aktuální sadě řádků. Tato hodnota musí být v rozsahu 1 až velikost sady řádků.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota stavu pro řádek. Podrobnosti najdete v tématu poznámky.  
  
### <a name="remarks"></a>Poznámky  
 `GetRowStatus`Vrátí hodnotu, která určuje buď všechny změny ve stavu na řádek od posledního načíst ze zdroje dat, nebo že žádný řádek odpovídající `wRow` nebyla načtena. Následující tabulka uvádí možné vrácené hodnoty.  
  
|Hodnota stavu|Popis|  
|------------------|-----------------|  
|`SQL_ROW_SUCCESS`|Řádek je beze změny.|  
|`SQL_ROW_UPDATED`|Řádek byl aktualizován.|  
|`SQL_ROW_DELETED`|Řádek byl odstraněn.|  
|`SQL_ROW_ADDED`|Řádek byl přidán.|  
|`SQL_ROW_ERROR`|Řádek je nelze získat z důvodu chyby.|  
|`SQL_ROW_NOROW`|Neexistuje odpovídající řádek `wRow`.|  
  
 Další informace najdete v tématu funkce rozhraní API ODBC **SQLExtendedFetch** ve Windows SDK.  
  
##  <a name="getstatus"></a>CRecordset::GetStatus  
 Určuje index v sadě záznamů a zda poslední záznam ukázala záznam na aktuální záznam.  
  
```  
void GetStatus(CRecordsetStatus& rStatus) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `rStatus`  
 Odkaz na **CRecordsetStatus** objektu. Další informace naleznete v části Poznámky.  
  
### <a name="remarks"></a>Poznámky  
 `CRecordset`pokusí se sledovat index, ale za určitých okolností nemusí být možné. V tématu [getrecordcount –](#getrecordcount) vysvětlení.  
  
 **CRecordsetStatus** struktura má následující formát:  
  
 `struct CRecordsetStatus`  
  
 `{`  
  
 `long m_lCurrentRecord;`  
  
 `BOOL m_bRecordCountFinal;`  
  
 `};`  
  
 Dva členové **CRecordsetStatus** mají následující významy:  
  
- **m_lCurrentRecord** obsahuje index založený na nule aktuální záznamu v sadě záznamů, pokud je znám. Pokud index nelze určit, tento člen obsahuje **AFX_CURRENT_RECORD_UNDEFINED** -(2). Pokud `IsBOF` je **TRUE** (prázdná sada záznamů nebo pokus o přechod před první záznam), pak **m_lCurrentRecord** je nastaven na **AFX_CURRENT_RECORD_BOF** (-1). Pokud na první záznam, pak je nastaveno na hodnotu 0, druhý záznam 1 a tak dále.  
  
- **m_bRecordCountFinal** Nonzero, pokud byla zjištěna celkový počet záznamů v sadě záznamů. Obecně to musíte udělat začínající na začátku sady záznamů a volání `MoveNext` dokud `IsEOF` vrátí nenulovou hodnotu. Pokud tento člen je nulová, záznamu, se počítají jako vrácený `GetRecordCount`, pokud není hodnotu -1, pouze "horní meze" počet záznamů.  
  
##  <a name="getsql"></a>CRecordset::GetSQL  
 Volání této funkce člen získat příkaz jazyka SQL, která byla použita k výběru sady záznamů záznamů, pokud byl otevřen.  
  
```  
const CString& GetSQL() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A **const** odkaz na `CString` obsahující příkaz jazyka SQL.  
  
### <a name="remarks"></a>Poznámky  
 Obvykle to bude SQL **vyberte** příkaz. Řetězec vrácený `GetSQL` je jen pro čtení.  
  
 Řetězec vrácený `GetSQL` se obvykle liší od libovolný řetězec, bylo předáno do sady záznamů v `lpszSQL` parametru **otevřete** – členská funkce. Důvodem je, že vytváří sadu záznamů úplný příkaz SQL na předán na základě **otevřete**, zadaným ClassWizard, co možná jste zadali v **m_strFilter** a `m_strSort` datové členy a parametry, které jste zadali. Podrobné informace o tom, jak sady záznamů vytvoří tento příkaz SQL najdete v článku [sada záznamů: Jak sady záznamů vyberte záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).  
  
> [!NOTE]
>  Volání této funkce člen pouze po volání [otevřete](#open).  
  
##  <a name="gettablename"></a>CRecordset::GetTableName  
 Získá název tabulky SQL, na kterých je založena dotaz sady záznamů.  
  
```  
const CString& GetTableName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A **const** odkaz na `CString` obsahující v tabulce název, pokud je sada záznamů podle tabulky; jinak hodnota prázdný řetězec.  
  
### <a name="remarks"></a>Poznámky  
 `GetTableName`je platné, pokud sada záznamů je založená na tabulku, není připojení k několika tabulkám nebo předdefinovaný dotaz (uloženou proceduru). Název je jen pro čtení.  
  
> [!NOTE]
>  Volání této funkce člen pouze po volání [otevřete](#open).  
  
##  <a name="isbof"></a>CRecordset::IsBOF  
 Vrátí nenulové hodnoty, pokud sada záznamů obsahuje byl umístěn před první záznam. Neexistuje aktuální záznam.  
  
```  
BOOL IsBOF() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud sada záznamů obsahuje žádné záznamy nebo pokud jste přešli zpátky před první záznam; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce člen před posunutí ze záznamu záznam se dozvíte, zda jste došli před na první záznam sady záznamů. Můžete také použít `IsBOF` spolu s `IsEOF` k určení, zda sada záznamů obsahuje záznamy nebo je prázdný. Okamžitě po zavolání metody **otevřete**, pokud sada záznamů obsahuje žádné záznamy `IsBOF` vrátí nenulovou hodnotu. Když otevřete záznamů, která obsahuje alespoň jeden záznam, je na první záznam na aktuální záznam a `IsBOF` vrátí hodnotu 0.  
  
 Pokud na první záznam na aktuální záznam a volání `MovePrev`, `IsBOF` následně vrátí nenulové hodnoty. Pokud `IsBOF` vrátí nenulovou a volání `MovePrev`, dojde k chybě. Pokud `IsBOF` vrátí nenulové hodnoty, není definován na aktuální záznam a jakoukoliv akci, která vyžaduje aktuální záznam bude výsledkem chyba.  
  
### <a name="example"></a>Příklad  
 Tento příklad používá `IsBOF` a `IsEOF` ke zjištění mezí sady záznamů jako kód posune prostřednictvím sady záznamů v obou směrech.  
  
 [!code-cpp[NVC_MFCDatabase#25](../../mfc/codesnippet/cpp/crecordset-class_9.cpp)]  
  
##  <a name="isdeleted"></a>CRecordset::IsDeleted  
 Určuje, zda byl odstraněn záznam na aktuální záznam.  
  
```  
BOOL IsDeleted() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud sada záznamů umístěna na záznam odstraněného; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud se posunete na záznam a `IsDeleted` vrátí **TRUE** (nenulové hodnoty), pak musí posunutí jiný záznam před provedením další operace sady záznamů.  
  
 Výsledek `IsDeleted` závisí na mnoha faktorech, například vaše sada záznamů typu, zda je sady záznamů aktualizovat, zda jste zadali **CRecordset::skipDeletedRecords** možnost při otevření sady záznamů, jestli vaše balíčky ovladačů odstranit záznamy, a zda více uživatelů.  
  
 Další informace o **CRecordset::skipDeletedRecords** a ovladačů balení, najdete v článku [otevřete](#open) – členská funkce.  
  
> [!NOTE]
>  Pokud jste implementovali hromadné načítání řádků, nesmí se volat `IsDeleted`. Místo toho zavolejte [GetRowStatus –](#getrowstatus) – členská funkce. Další informace o hromadné načítání řádků, najdete v článku [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="iseof"></a>CRecordset::IsEOF  
 Vrátí nenulové hodnoty, pokud sada záznamů obsahuje byl umístěn za poslední záznam. Neexistuje aktuální záznam.  
  
```  
BOOL IsEOF() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud sada záznamů obsahuje žádné záznamy nebo pokud jste přešli nad rámec poslední záznam; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce člen při posunutí ze záznamu záznamu zjistěte, zda jste došli nad rámec poslední záznam sady záznamů. Můžete také použít `IsEOF` k určení, zda sada záznamů obsahuje záznamy nebo je prázdný. Okamžitě po zavolání metody **otevřete**, pokud sada záznamů obsahuje žádné záznamy `IsEOF` vrátí nenulovou hodnotu. Když otevřete záznamů, která obsahuje alespoň jeden záznam, je na první záznam na aktuální záznam a `IsEOF` vrátí hodnotu 0.  
  
 Pokud je poslední záznam na aktuální záznam při volání `MoveNext`, `IsEOF` následně vrátí nenulové hodnoty. Pokud `IsEOF` vrátí nenulovou a volání `MoveNext`, dojde k chybě. Pokud `IsEOF` vrátí nenulové hodnoty, není definován na aktuální záznam a jakoukoliv akci, která vyžaduje aktuální záznam bude výsledkem chyba.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [IsBOF](#isbof).  
  
##  <a name="isfielddirty"></a>CRecordset::IsFieldDirty  
 Určuje, zda zadaná pole datového člena se změnil od [upravit](#edit) nebo [AddNew](#addnew) byla volána.  
  
```  
BOOL IsFieldDirty(void* pv);
```  
  
### <a name="parameters"></a>Parametry  
 `pv`  
 Ukazatel na pole datového člena, jejichž stav chcete zkontrolovat, nebo **NULL** k určení, pokud žádná pole jsou chybná.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud zadané pole datových členů došlo ke změně od volání `AddNew` nebo **upravit**; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Data v všechny změny pole datových členů budou přeneseny na záznam ve zdroji dat při aktualizaci na aktuální záznam voláním [aktualizace](#update) členské funkce `CRecordset` (následující volání **upravit**nebo `AddNew`).  
  
> [!NOTE]
>  Tento člen funkce se nedá použít na sady záznamů, které používají hromadné načítání řádků. Pokud jste implementovali hromadné načítání řádků, pak `IsFieldDirty` vždy vrátí **FALSE** a způsobí selhání kontrolního výrazu. Další informace o hromadné načítání řádků, najdete v článku [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Volání metody `IsFieldDirty` obnoví důsledky předchozích volání [SetFieldDirty](#setfielddirty) vzhledem k tomu, že se znovu zhodnotí nevyřízený stav pole. V `AddNew` případ, pokud aktuální hodnota pole se liší od hodnotu null pseudo pole je nastaven stav dirty. V **upravit** případ, pokud hodnota pole se liší od hodnota uložená v mezipaměti, pak je pole Stav dirty.  
  
 `IsFieldDirty`se implementuje pomocí [DoFieldExchange](#dofieldexchange).  
  
 Další informace o příznak změny, najdete v článku [sada záznamů: Jak sady záznamů vyberte záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).  
  
##  <a name="isfieldnull"></a>CRecordset::IsFieldNull  
 Vrátí nenulové hodnoty, pokud v zadaném poli záznam na aktuální záznam má hodnotu Null (nemá žádnou hodnotu).  
  
```  
BOOL IsFieldNull(void* pv);
```  
  
### <a name="parameters"></a>Parametry  
 `pv`  
 Ukazatel na pole datového člena, jejichž stav chcete zkontrolovat, nebo **NULL** k určení, pokud je některý z pole hodnotu Null.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud zadané pole datového člena označen příznakem jako hodnota Null. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce člen k určení, zda zadaná pole datových členů sady záznamů byl označen příznakem jako hodnotu Null. (V terminologii databáze Null znamená "nutnosti žádná hodnota" a není stejný jako **NULL** v jazyce C++.) Pokud pole datových členů je označena jako hodnota Null, je interpretován jako sloupec na aktuální záznam, pro kterou neexistuje žádná hodnota.  
  
> [!NOTE]
>  Tento člen funkce se nedá použít na sady záznamů, které používají hromadné načítání řádků. Pokud jste implementovali hromadné načítání řádků, pak `IsFieldNull` vždy vrátí **FALSE** a způsobí selhání kontrolního výrazu. Další informace o hromadné načítání řádků, najdete v článku [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 `IsFieldNull`se implementuje pomocí [DoFieldExchange](#dofieldexchange).  
  
##  <a name="isfieldnullable"></a>CRecordset::IsFieldNullable  
 Vrátí nenulové hodnoty, pokud v zadaném poli záznam na aktuální záznam lze nastavit na hodnotu Null (nutnosti žádná hodnota).  
  
```  
BOOL IsFieldNullable(void* pv);
```  
  
### <a name="parameters"></a>Parametry  
 `pv`  
 Ukazatel na pole datového člena, jejichž stav chcete zkontrolovat, nebo **NULL** k určení, pokud žádná pole lze nastavit na hodnotu Null.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce člen k určení, zda je zadaná pole datového člena "null" (může být nastavena na hodnotu Null; C++ **NULL** není stejná jako hodnota Null, což v terminologii databáze znamená "s žádnou hodnotu").  
  
> [!NOTE]
>  Pokud jste implementovali hromadné načítání řádků, nelze volat `IsFieldNullable`. Místo toho zavolejte [GetODBCFieldInfo](#getodbcfieldinfo) – členská funkce k určení, zda pole lze nastavit na hodnotu Null. Všimněte si, že můžete vždy volat `GetODBCFieldInfo`, bez ohledu na to, jestli jste implementovali hromadné načítání řádků. Další informace o hromadné načítání řádků, najdete v článku [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Pole, která nemůže mít hodnotu Null, musí mít hodnotu. Pokud se pokusíte toto pole nastavíte na hodnotu Null při přidávání nebo aktualizaci záznamu, zdroj dat odmítne přidání nebo aktualizace, a [aktualizace](#update) vyvolá výjimku. Výjimka nastává při volání **aktualizace**, není při volání [SetFieldNull](#setfieldnull).  
  
 Pomocí **NULL** pro první argument funkce se vztahují pouze k funkci **outputColumn** polí není **param** pole. Například volání  
  
 [!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]  
  
 Nastaví pouze **outputColumn** polí k **NULL**; **param** pole, zůstanou beze změn.  
  
 Pro práci na **param** pole, je třeba zadat adresu skutečného jednotlivých **param** chcete pracovat, jako například:  
  
 [!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]  
  
 To znamená, že nelze nastavit všechny **param** polí k **NULL**, stejně jako **outputColumn** pole.  
  
 `IsFieldNullable`se implementuje pomocí [DoFieldExchange](#dofieldexchange).  
  
##  <a name="isopen"></a>CRecordset::IsOpen  
 Určuje, pokud sada záznamů je již otevřeno.  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě objekt sady záznamů [otevřete](#open) nebo [Requery –](#requery) – členská funkce dříve byla volána a sady záznamů nebyla uzavřena; jinak hodnota 0.  
  
##  <a name="m_hstmt"></a>CRecordset::m_hstmt  
 Obsahuje popisovač pro strukturu dat rozhraní ODBC příkaz typu **HSTMT**, přidružené sady záznamů.  
  
### <a name="remarks"></a>Poznámky  
 Každý dotaz na zdroji dat rozhraní ODBC je přidružen **HSTMT**.  
  
> [!CAUTION]
>  Nepoužívejte **m_hstmt** před [otevřete](#open) byla volána.  
  
 Normálně není potřeba přístup **HSTMT** přímo, ale můžete ho potřebovat pro přímé spouštění příkazů jazyka SQL. `ExecuteSQL` Funkce člena třídy `CDatabase` poskytuje příklad použití **m_hstmt**.  
  
##  <a name="m_nfields"></a>CRecordset::m_nFields  
 Obsahuje počet pole datových členů ve třídě sady záznamů; To znamená, počet sloupců vybraných funkcí sady záznamů z datového zdroje.  
  
### <a name="remarks"></a>Poznámky  
 V konstruktoru pro třídy sady záznamů musí inicializovat `m_nFields` s správné číslo. Nemáte-li hromadné načítání řádků, ClassWizard zapíše tento inicializace pro vás, pokud ji používáte deklarovat třídu sady záznamů. Je také možné zapsat ji ručně.  
  
 Rozhraní používá toto číslo ke správě interakce mezi pole datových členů a na odpovídající sloupce ve zdroji dat na aktuální záznam.  
  
> [!CAUTION]
>  Toto číslo musí odpovídat počtu "výstupních sloupcích" zaregistrovaný v `DoFieldExchange` nebo `DoBulkFieldExchange` po volání [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) s parametrem **CFieldExchange::outputColumn**.  
  
 Sloupce lze vázat dynamicky, jak je popsáno v článku "Sada záznamů: dynamické vazby datových sloupců." Pokud tak učiníte, musíte zvýšit počet v `m_nFields` tak, aby odrážela počet funkcí RFX nebo Bulk RFX volání vaše `DoFieldExchange` nebo `DoBulkFieldExchange` – členská funkce pro dynamicky vázané sloupce.  
  
 Další informace najdete v článcích [sada záznamů: dynamické vazby datových sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) a [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Příklad  
 Najdete v článku [výměna polí záznamu: Použití RFX](../../data/odbc/record-field-exchange-using-rfx.md).  
  
##  <a name="m_nparams"></a>CRecordset::m_nParams  
 Obsahuje počet parametry datových členů v třídě sady záznamů; To znamená počet parametrů předaných s dotaz sady záznamů.  
  
### <a name="remarks"></a>Poznámky  
 Pokud vaše sada záznamů třída má všechny parametry datových členů, musí inicializovat v konstruktoru pro třídu `m_nParams` s správné číslo. Hodnota `m_nParams` výchozí hodnota je 0. Pokud přidáte parametry datových členů (které je potřeba udělat ručně) musíte taky ručně přidat inicializaci v konstruktoru třídy tak, aby odrážela počet parametrů (která musí být alespoň tak velké, jaká počet '' zástupné symboly v vaší **m_strFilter**  nebo `m_strSort` řetězec).  
  
 Rozhraní používá toto číslo, když ho parameterizes dotaz sady záznamů.  
  
> [!CAUTION]
>  Toto číslo musí odpovídat počtu "parametry" zaregistrovaný v `DoFieldExchange` nebo `DoBulkFieldExchange` po volání [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) s hodnotou parametru **CFieldExchange::inputParam**,  **CFieldExchange::param**, **CFieldExchange::outputParam**, nebo **CFieldExchange::inoutParam**.  
  
### <a name="example"></a>Příklad  
  Najdete v článcích [sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) a [výměna polí záznamu: Použití RFX](../../data/odbc/record-field-exchange-using-rfx.md).  
  
##  <a name="m_pdatabase"></a>CRecordset::m_pDatabase  
 Obsahuje odkazy `CDatabase` objekt, pomocí kterého je sada záznamů připojený ke zdroji dat.  
  
### <a name="remarks"></a>Poznámky  
 Tato proměnná je nastavená dvěma způsoby. Obvykle můžete předat ukazatel již připojené `CDatabase` objektu při sestavení objektu záznamů. Pokud předáte **NULL** místo toho `CRecordset` vytvoří `CDatabase` objektu pro vás a připojí ho. V obou případech `CRecordset` ukládá ukazatele v této proměnné.  
  
 Obvykle nebudete muset přímo pomocí ukazatele uložené v **m_pDatabase**. Pokud píšete vlastní rozšíření `CRecordset`, ale budete muset použít ukazatele. Například může být nutné ukazatele Pokud jste throw vlastní `CDBException`s. Nebo může být nutné, pokud je potřeba udělat něco používající stejný `CDatabase` objektu, například spuštění transakce, nastavení časových limitů, nebo volání `ExecuteSQL` funkce člena třídy `CDatabase` pro spuštění příkazů SQL přímo.  
  
##  <a name="m_strfilter"></a>CRecordset::m_strFilter  
 Po sestavení objektu záznamů, ale před voláním jeho **otevřete** členské funkce, použijte tento člen data k uložení `CString` obsahující SQL **kde** klauzule.  
  
### <a name="remarks"></a>Poznámky  
 Sady záznamů tento řetězec používá k omezení (nebo filtrovat) záznamy vybere během **otevřete** nebo **Requery** volání. To je užitečné pro výběr podmnožinu záznamů, jako je například "všichni prodejci založené na kalifornské" ("Stav = certifikační Autority"). Syntaxe ODBC SQL **kde** je klauzule  
  
 `WHERE search-condition`  
  
 Všimněte si, že neuvedete **kde** – klíčové slovo ve vašem řetězci. Rozhraní framework poskytuje ho.  
  
 Můžete také parametrizovat vaší řetězec filtru tak, že s zástupné symboly v něm deklarace parametr datového člena ve třídě pro každý zástupný symbol a předávání parametrů do sady záznamů na dobu běhu. Díky tomu můžete vytvořit filtr za běhu. Další informace najdete v článku [sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
 Další informace o SQL **kde** klauzule, najdete v článku [SQL](../../data/odbc/sql.md). Další informace o výběru a filtrování záznamů, najdete v článku [sada záznamů: filtrování záznamů (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDatabase#30](../../mfc/codesnippet/cpp/crecordset-class_12.cpp)]  
  
##  <a name="m_strsort"></a>CRecordset::m_strSort  
 Po sestavení objektu záznamů, ale před voláním jeho **otevřete** člen fungovat, použijte tento člen data k uložení `CString` obsahující SQL **Order** klauzule.  
  
### <a name="remarks"></a>Poznámky  
 Sady záznamů tento řetězec používá k řazení záznamů vybere během **otevřete** nebo **Requery** volání. Tato funkce slouží k seřazení sady záznamů na jeden nebo více sloupců. Syntaxe ODBC SQL **Order** je klauzule  
  
 `ORDER BY sort-specification [, sort-specification]...`  
  
 kde specifikaci řazení je celé číslo nebo název sloupce. Můžete také zadat vzestupném nebo sestupném pořadí (ve výchozím nastavení je vzestupném pořadí) "ASC" nebo "DESC" připojení k seznamu sloupců v řetězci řazení. Vybrané záznamy jsou seřazeny nejprve podle prvního sloupce uvedené a pak podle druhého a tak dále. Například můžete objednat sady záznamů "Zákazníci" příjmení a poté křestní jméno. Počet sloupců, které můžete vytvořit seznam závisí na datovém zdroji. Další informace najdete v tématu Windows SDK.  
  
 Všimněte si, že neuvedete **Order** – klíčové slovo ve vašem řetězci. Rozhraní framework poskytuje ho.  
  
 Další informace o klauzule SQL, najdete v článku [SQL](../../data/odbc/sql.md). Další informace o řazení záznamů, najdete v článku [sada záznamů: řazení záznamů (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDatabase#31](../../mfc/codesnippet/cpp/crecordset-class_13.cpp)]  
  
##  <a name="move"></a>CRecordset::Move  
 Přesune aktuální záznam ukazatele v rámci sady záznamů, vpřed nebo zpět.  
  
```  
virtual void Move(
    long nRows,  
    WORD wFetchType = SQL_FETCH_RELATIVE);
```  
  
### <a name="parameters"></a>Parametry  
 `nRows`  
 Počet řádků, které mají přesunutí nebo předchozí. Kladné hodnoty. přesuňte směrem vpřed, na konci sady záznamů. Záporné hodnoty přesunout zpátky, zpět na začátek.  
  
 `wFetchType`  
 Určuje sadu řádků, **přesunout** bude načíst. Podrobnosti najdete v tématu poznámky.  
  
### <a name="remarks"></a>Poznámky  
 Pokud předáte hodnotu 0 pro `nRows`, **přesunout** aktualizuje na aktuální záznam; **Přesunout** se ukončí všechny aktuální `AddNew` nebo **upravit** režimu a obnoví hodnotu na aktuální záznam před `AddNew` nebo **upravit** byla volána.  
  
> [!NOTE]
>  Když přesouváte prostřednictvím sady záznamů, nelze přeskočit odstraněné záznamy. V tématu [CRecordset::IsDeleted](#isdeleted) Další informace. Při otevření `CRecordset` s **skipDeletedRecords** možnost sady **přesunout** vyhodnotí, pokud `nRows` parametru je 0. Toto chování zabraňuje aktualizace řádků, které jsou odstranil jiné klientské aplikace používají stejná data. Najdete v článku `dwOption` parametr v [otevřete](#open) popis **skipDeletedRecords**.  
  
 **Přesunout** přemístí sadu záznamů pomocí sady řádků. Na základě hodnot pro `nRows` a `wFetchType`, **přesunout** načte odpovídající sadu řádků a potom provede na první záznam v této sadě řádků na aktuální záznam. Nemáte-li hromadné načítání řádků, pak velikost sady řádků je vždy 1. Při načítání sady řádků **přesunout** přímo volá [CheckRowsetError](#checkrowseterror) – členská funkce pro zpracování chyby způsobené načtení.  
  
 V závislosti na hodnoty předáte **přesunout** je ekvivalentní druhý `CRecordset` členské funkce. Konkrétně hodnota `wFetchType` může znamenat členské funkce, který je intuitivnější a často upřednostňovanou metodou pro přesun na aktuální záznam.  
  
 Následující tabulka uvádí možné hodnoty pro `wFetchType`, sadu řádků, **přesunout** bude načíst na základě `wFetchType` a `nRows`a všechny funkce ekvivalentní člen odpovídající `wFetchType`.  
  
|wFetchType|Načtených řádků|Ekvivalentní – členská funkce|  
|----------------|--------------------|--------------------------------|  
|`SQL_FETCH_RELATIVE`(výchozí hodnota)|Sada řádků počáteční `nRows` řádky z prvního řádku v aktuální sadě řádků.||  
|`SQL_FETCH_NEXT`|Další sadu řádků; `nRows` je ignorována.|[MoveNext –](#movenext)|  
|`SQL_FETCH_PRIOR`|Předchozí řádků; `nRows` je ignorována.|[MovePrev –](#moveprev)|  
|`SQL_FETCH_FIRST`|První sadu řádků v sadě záznamů; `nRows` je ignorována.|[MoveFirst –](#movefirst)|  
|`SQL_FETCH_LAST`|Poslední kompletní sady řádků v sadě záznamů; `nRows` je ignorována.|[MoveLast –](#movelast)|  
|`SQL_FETCH_ABSOLUTE`|Pokud `nRows` > 0, řádků od `nRows` řádky od začátku sady záznamů. Pokud `nRows` < 0, řádků od `nRows` řádky od konce sady záznamů. Pokud `nRows` = 0, je vrácena podmínku začátku souboru (BOF).|[SetAbsolutePosition –](#setabsoluteposition)|  
|`SQL_FETCH_BOOKMARK`|Sada řádků od řádku, jehož hodnota záložku odpovídá `nRows`.|[SetBookmark –](#setbookmark)|  
  
> [!NOTE]
>  Pro dopředné sady záznamů **přesunout** je platný pouze s hodnotou `SQL_FETCH_NEXT` pro `wFetchType`.  
  
> [!CAUTION]
>  Volání metody **přesunout** vyvolá výjimku, pokud má sada záznamů žádné záznamy. Chcete-li určit, zda sada záznamů obsahuje všechny záznamy, volejte [IsBOF](#isbof) a [IsEOF](#iseof).  
  
> [!NOTE]
>  Pokud jste přešli po začátku nebo konci sadu záznamů ( `IsBOF` nebo `IsEOF` vrátí nenulovou hodnotu), volání **přesunout** funkce vyvolá výjimku pravděpodobně `CDBException`. Například pokud `IsEOF` vrátí nenulovou hodnotu a `IsBOF` neexistuje, pak `MoveNext` vyvolá výjimku, ale `MovePrev` nikoli.  
  
> [!NOTE]
>  Když zavoláte **přesunout** při záznam na aktuální záznam se aktualizovat nebo přidání, aktualizace se ztratí bez upozornění.  
  
 Další informace o navigaci v sadě záznamů, najdete v článcích [sada záznamů: posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) a [sada záznamů: záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Další informace o hromadné načítání řádků, najdete v článku [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Související informace najdete v tématu funkce rozhraní API ODBC **SQLExtendedFetch** ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDatabase#28](../../mfc/codesnippet/cpp/crecordset-class_14.cpp)]  
  
##  <a name="movefirst"></a>CRecordset::MoveFirst  
 Vytváří na první záznam v první sadu řádků na aktuální záznam.  
  
```  
void MoveFirst();
```  
  
### <a name="remarks"></a>Poznámky  
 Bez ohledu na to, jestli hromadné načítání řádků byl implementován bude vždy na první záznam v sadě záznamů.  
  
 Není nutné volat **MoveFirst** okamžitě po otevření sady záznamů. V ten moment se první záznam (pokud existuje) je automaticky záznam na aktuální záznam.  
  
> [!NOTE]
>  Tento člen funkce není platná pro dopředné sady záznamů.  
  
> [!NOTE]
>  Když přesouváte prostřednictvím sady záznamů, nelze přeskočit odstraněné záznamy. Najdete v článku [IsDeleted](#isdeleted) – členská funkce podrobnosti.  
  
> [!CAUTION]
>  Žádné z volání **přesunout** funkce vyvolá výjimku, pokud má sada záznamů žádné záznamy. Chcete-li určit, zda sada záznamů obsahuje všechny záznamy, volejte `IsBOF` a `IsEOF`.  
  
> [!NOTE]
>  Pokud žádné z volání **přesunout** funkce při záznam na aktuální záznam se aktualizovat nebo přidání, aktualizace se ztratí bez upozornění.  
  
 Další informace o navigaci v sadě záznamů, najdete v článcích [sada záznamů: posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) a [sada záznamů: záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Další informace o hromadné načítání řádků, najdete v článku [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [IsBOF](#isbof).  
  
##  <a name="movelast"></a>CRecordset::MoveLast  
 Umožňuje na první záznam v sadě řádků poslední úplný záznam na aktuální záznam.  
  
```  
void MoveLast();
```  
  
### <a name="remarks"></a>Poznámky  
 Nemáte-li hromadné načítání řádků, sady záznamů má velikost řádků 1, takže `MoveLast` jednoduše přejde na poslední záznam v sadě záznamů.  
  
> [!NOTE]
>  Tento člen funkce není platná pro dopředné sady záznamů.  
  
> [!NOTE]
>  Když přesouváte prostřednictvím sady záznamů, nelze přeskočit odstraněné záznamy. Najdete v článku [IsDeleted](#isdeleted) – členská funkce podrobnosti.  
  
> [!CAUTION]
>  Žádné z volání **přesunout** funkce vyvolá výjimku, pokud má sada záznamů žádné záznamy. Chcete-li určit, zda sada záznamů obsahuje všechny záznamy, volejte `IsBOF` a `IsEOF`.  
  
> [!NOTE]
>  Pokud žádné z volání **přesunout** funkce při záznam na aktuální záznam se aktualizovat nebo přidání, aktualizace se ztratí bez upozornění.  
  
 Další informace o navigaci v sadě záznamů, najdete v článcích [sada záznamů: posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) a [sada záznamů: záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Další informace o hromadné načítání řádků, najdete v článku [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [IsBOF](#isbof).  
  
##  <a name="movenext"></a>CRecordset::MoveNext  
 Vytváří na první záznam v další sadu řádků na aktuální záznam.  
  
```  
void MoveNext();
```  
  
### <a name="remarks"></a>Poznámky  
 Nemáte-li hromadné načítání řádků, sady záznamů má velikost řádků 1, takže `MoveNext` jednoduše přejde na další záznam.  
  
> [!NOTE]
>  Když přesouváte prostřednictvím sady záznamů, nelze přeskočit odstraněné záznamy. Najdete v článku [IsDeleted](#isdeleted) – členská funkce podrobnosti.  
  
> [!CAUTION]
>  Žádné z volání **přesunout** funkce vyvolá výjimku, pokud má sada záznamů žádné záznamy. Chcete-li určit, zda sada záznamů obsahuje všechny záznamy, volejte `IsBOF` a `IsEOF`.  
  
> [!NOTE]
>  Je také vhodné volat `IsEOF` před voláním `MoveNext`. Pokud jste přešli za koncem sady záznamů, například `IsEOF` vrátí nenulovou; následné volání `MoveNext` by vyvolat výjimku.  
  
> [!NOTE]
>  Pokud žádné z volání **přesunout** funkce při záznam na aktuální záznam se aktualizovat nebo přidání, aktualizace se ztratí bez upozornění.  
  
 Další informace o navigaci v sadě záznamů, najdete v článcích [sada záznamů: posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) a [sada záznamů: záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Další informace o hromadné načítání řádků, najdete v článku [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [IsBOF](#isbof).  
  
##  <a name="moveprev"></a>CRecordset::MovePrev  
 Umožňuje na první záznam v předchozí sadě řádků na aktuální záznam.  
  
```  
void MovePrev();
```  
  
### <a name="remarks"></a>Poznámky  
 Nemáte-li hromadné načítání řádků, sady záznamů má velikost řádků 1, takže `MovePrev` jednoduše přesune do předchozího záznamu.  
  
> [!NOTE]
>  Tento člen funkce není platná pro dopředné sady záznamů.  
  
> [!NOTE]
>  Když přesouváte prostřednictvím sady záznamů, nelze přeskočit odstraněné záznamy. Najdete v článku [IsDeleted](#isdeleted) – členská funkce podrobnosti.  
  
> [!CAUTION]
>  Žádné z volání **přesunout** funkce vyvolá výjimku, pokud má sada záznamů žádné záznamy. Chcete-li určit, zda sada záznamů obsahuje všechny záznamy, volejte `IsBOF` a `IsEOF`.  
  
> [!NOTE]
>  Je také vhodné volat `IsBOF` před voláním `MovePrev`. Pokud jste přešli před začátek sady záznamů, například `IsBOF` vrátí nenulovou; následné volání `MovePrev` by vyvolat výjimku.  
  
> [!NOTE]
>  Pokud žádné z volání **přesunout** funkce při záznam na aktuální záznam se aktualizovat nebo přidání, aktualizace se ztratí bez upozornění.  
  
 Další informace o navigaci v sadě záznamů, najdete v článcích [sada záznamů: posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) a [sada záznamů: záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md). Další informace o hromadné načítání řádků, najdete v článku [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [IsBOF](#isbof).  
  
##  <a name="onsetoptions"></a>CRecordset::OnSetOptions  
 Voláno k nastavení možností (používá se na výběr) pro zadaný příkaz ODBC.  
  
```  
virtual void OnSetOptions(HSTMT hstmt);
```  
  
### <a name="parameters"></a>Parametry  
 `hstmt`  
 **HSTMT** ODBC příkazu, jehož možnosti jsou nastavení.  
  
### <a name="remarks"></a>Poznámky  
 Volání `OnSetOptions` nastavení možností (používá se na výběr) pro zadaný příkaz ODBC. Tato funkce člen nastavit výchozí možnosti pro sadu záznamů volá framework. `OnSetOptions`Určuje zdroj dat podporu pro posouvatelného kurzory a kurzor souběžnosti a odpovídajícím způsobem nastaví možnosti sady záznamů. (Zatímco `OnSetOptions` se používá pro výběr operace `OnSetUpdateOptions` se používá pro operace aktualizace.)  
  
 Přepsání `OnSetOptions` nastavení možností konkrétní ke zdroji dat nebo ovladač. Například pokud zdroj dat podporuje otevírání pro výhradní přístup, může přepíšete `OnSetOptions` využít tuto možnost.  
  
 Další informace o kurzory, najdete v článku [ODBC](../../data/odbc/odbc-basics.md).  
  
##  <a name="onsetupdateoptions"></a>CRecordset::OnSetUpdateOptions  
 Volá se pro nastavení možností (používá se při aktualizaci) pro zadaný příkaz ODBC.  
  
```  
virtual void OnSetUpdateOptions(HSTMT hstmt);
```  
  
### <a name="parameters"></a>Parametry  
 `hstmt`  
 **HSTMT** ODBC příkazu, jehož možnosti jsou nastavení.  
  
### <a name="remarks"></a>Poznámky  
 Volání `OnSetUpdateOptions` nastavení možností (používá se při aktualizaci) pro zadaný příkaz ODBC. Tento člen funkce volá framework po vytvoření HSTMT k aktualizaci záznamů v sadě záznamů. (Zatímco `OnSetOptions` se používá pro výběr operace `OnSetUpdateOptions` se používá pro operace aktualizace.) `OnSetUpdateOptions` Určuje podporu zdroj dat pro posouvatelného kurzory a kurzor souběžnosti a odpovídajícím způsobem nastaví možnosti sady záznamů.  
  
 Přepsání `OnSetUpdateOptions` nastavení možností příkazu ODBC před tento příkaz slouží pro přístup k databázi.  
  
 Další informace o kurzory, najdete v článku [ODBC](../../data/odbc/odbc-basics.md).  
  
##  <a name="open"></a>CRecordset::Open  
 Otevře sadu záznamů načtením tabulky nebo provedením dotazu, který sada záznamů představuje.  
  
```  
virtual BOOL Open(
    UINT nOpenType = AFX_DB_USE_DEFAULT_TYPE,  
    LPCTSTR lpszSQL = NULL,  
    DWORD dwOptions = none);
```  
  
### <a name="parameters"></a>Parametry  
 `nOpenType`  
 Přijměte výchozí hodnotu **AFX_DB_USE_DEFAULT_TYPE**, nebo použijte jednu z následujících hodnot z **výčtu OpenType**:  
  
- **CRecordset::dynaset** sady záznamů s obousměrný posouvání. Členství a pořadí záznamů je určeno při otevření sady záznamů, ale změny datových hodnot provedené ostatními uživateli jsou viditelné až po operaci načtení. Dynamické sady jsou známy také jako sady záznamů řízené sadou klíčů.  
  
- **CRecordset::snapshot** statické sada záznamů s obousměrný posouvání. Členství a pořadí záznamů je určeno při otevření sady záznamů. Datové hodnoty jsou určeny při načtení záznamů. Změny provedené ostatními uživateli nejsou viditelné, dokud není sada záznamů zavřena a znovu otevřena.  
  
- **CRecordset::dynamic** sady záznamů s obousměrný posouvání. Změny členství, pořadí a datových hodnot provedené jinými uživateli jsou viditelné po operaci načtení. Povšimněte si, že mnoho ovladačů ODBC nepodporuje tento typ sady záznamů.  
  
- **CRecordset::forwardOnly** jen pro čtení sady záznamů s pouze dál posouvání.  
  
     Pro `CRecordset`, výchozí hodnota je **CRecordset::snapshot**. Mechanismus výchozích hodnot umožňuje interakci průvodců aplikace Visual C++ s třídou `CRecordset` pro rozhraní ODBC i třídou `CDaoRecordset` pro rozhraní DAO, které používají různé výchozí hodnoty.  
  
 Další informace o těchto typech sady záznamů, najdete v článku [záznamů (ODBC)](../../data/odbc/recordset-odbc.md). Související informace najdete v článku "Pomocí bloku a posouvatelného kurzory" v sadě Windows SDK.  
  
> [!CAUTION]
>  Není-li požadovaný typ podporován, rozhraní vyvolá výjimku.  
  
 `lpszSQL`  
 Ukazatel řetězce obsahující jedno z následujících:  
  
-   A **NULL** ukazatel.  
  
-   Název tabulky.  
  
-   SQL **vyberte** – příkaz (volitelně i s SQL **kde** nebo **Order** klauzule).  
  
-   A **volání** příkaz a zadejte název předdefinovaný dotaz (uloženou proceduru). Buďte opatrní nevkládejte mezery mezi složené závorky a **volání** – klíčové slovo.  
  
 Další informace o tomto řetězci naleznete v tabulce a v diskuzi o účelu nástroje ClassWizard v části Poznámky.  
  
> [!NOTE]
>  Pořadí sloupců ve vaší sadě výsledků dotazu musí odpovídat pořadí RFX nebo Bulk RFX funkce volá vaší [DoFieldExchange](#dofieldexchange) nebo [DoBulkFieldExchange](#dobulkfieldexchange) funkce přepsání.  
  
 `dwOptions`  
 Bitová maska schopná určit kombinaci hodnot uvedených níže. Některé se vzájemně vylučují. Výchozí hodnota je **žádné**.  
  
- **CRecordset::none** není nastavený žádný možnosti. Tato hodnota parametru se vzájemně vylučuje se všemi ostatními hodnotami. Ve výchozím nastavení, můžete aktualizovat sadu záznamů [upravit](#edit) nebo [odstranit](#delete) a umožňuje připojení nové záznamy s [AddNew](#addnew). Možnosti aktualizace závisí na zdroji dat stejně jako na zadané možnosti `nOpenType`. Optimalizace pro hromadná přidávání nejsou dostupné. Hromadné načítání řádků nebude implementováno. Odstraněné záznamy nebudou při navigaci v sadě záznamů přeskočeny. Záložky nejsou k dispozici. Automatická kontrola nečistých polí je implementována.  
  
- **CRecordset::appendOnly** neumožňují **upravit** nebo **odstranit** v sadě záznamů. Povolit pouze funkci `AddNew`. Tato možnost je vzájemně se vylučuje s **CRecordset::readOnly**.  
  
- **CRecordset::readOnly** otevření záznamů jen pro čtení. Tato možnost je vzájemně se vylučuje s **CRecordset::appendOnly**.  
  
- **CRecordset::optimizeBulkAdd** použít připravený příkaz SQL za účelem optimalizace přidání mnoho záznamů najednou. Platí jenom v případě, že nepoužíváte funkce rozhraní API ODBC **SQLSetPos** aktualizovat sadu záznamů. První aktualizace určuje, která pole jsou označena za nečistá. Tato možnost se vzájemně vylučuje s možností `CRecordset::useMultiRowFetch`.  
  
- `CRecordset::useMultiRowFetch`Hromadné načítání řádků umožňuje více řádků má být načtena v rámci jednoho načtení operace implementujte. Jde o pokročilou funkci navrženou pro zvýšení výkonu. Hromadná výměna polí záznamu však není podporována nástrojem ClassWizard. Tato možnost je vzájemně se vylučuje s **CRecordset::optimizeBulkAdd**. Všimněte si, že pokud zadáte `CRecordset::useMultiRowFetch`, pak možnost **CRecordset::noDirtyFieldCheck** bude automaticky zapnuto (dvojité ukládání do vyrovnávací paměti nebude k dispozici); na dopředné sady záznamů, možnost  **CRecordset::useExtendedFetch** bude automaticky zapnuta. Další informace o hromadné načítání řádků, najdete v článku [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
- **CRecordset::skipDeletedRecords** při procházení sady záznamů přeskočit všechny odstraněné záznamy. V určitých relativních načteních tato možnost sníží výkon. Tato možnost není platná pro sady záznamů s posouváním pouze vpřed. Když zavoláte [přesunout](#move) s `nRows` parametr nastaven na hodnotu 0 a **CRecordset::skipDeletedRecords** možnost sady **přesunout** bude assert. Všimněte si, že **CRecordset::skipDeletedRecords** je podobná *ovladač okolních*, což znamená, že odstranit řádky se odeberou ze sady záznamů. Pokud však ovladač záznamy komprimuje, budou přeskočeny pouze vámi odstraněné záznamy. Záznamy odstraněné jinými uživateli v době, kdy byla sada otevřena, nebudou přeskočeny. **CRecordset::skipDeletedRecords** přeskočí řádek Odstraněný jinými uživateli.  
  
- **CRecordset::useBookmarks** mohou používat záložky v sadě záznamů, pokud podporován. Záložky zpomalují načítání dat, ale zvyšují výkon navigace v nich. Nelze je použít v sadách záznamů s posouváním pouze vpřed. Další informace najdete v článku [sada záznamů: záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).  
  
- **CRecordset::noDirtyFieldCheck** vypnout automatické změny pole Kontrola (dvojité ukládání do vyrovnávací paměti). Tím dojde ke zvýšení výkonu. Pole je však zapotřebí ručně označit jako nečistá zavoláním členských funkcí `SetFieldDirty` a `SetFieldNull`. Povšimněte si, že dvojité ukládání do vyrovnávací paměti ve třídě `CRecordset` je podobné dvojitému ukládání do vyrovnávací paměti ve třídě `CDaoRecordset`. Ve třídě `CRecordset` však nelze zapnout dvojité ukládání do vyrovnávací paměti pro jednotlivá pole. Lze jej zapnout nebo vypnout pouze pro všechna pole najednou. Všimněte si, že pokud zadáte možnost `CRecordset::useMultiRowFetch`, pak **CRecordset::noDirtyFieldCheck** bude zapnuta automaticky, ale `SetFieldDirty` a `SetFieldNull` nelze použít na sady záznamů, který implementuje hromadné načítání řádků.  
  
- **CRecordset::executeDirect** nepoužívejte připravený příkaz SQL. Pro lepší výkon, zadejte tuto možnost, pokud **Requery –** – členská funkce nebude nikdy volat.  
  
- **CRecordset::useExtendedFetch** implementace **SQLExtendedFetch** místo **SQLFetch**. Navrženo pro implementaci hromadného načítání řádků pro sady záznamů s posouváním pouze vpřed. Pokud zadáte možnost `CRecordset::useMultiRowFetch` na dopředné sady záznamů, pak **CRecordset::useExtendedFetch** bude automaticky zapnuta.  
  
- **CRecordset::userAllocMultiRowBuffers** uživatele bude přidělení vyrovnávací paměti úložiště pro data. Chcete-li přidělit své vlastní úložiště, použijte tuto možnost spolu s možností `CRecordset::useMultiRowFetch`. V opačném případě bude potřebné úložiště přiděleno rozhraním. Další informace najdete v článku [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Všimněte si, že zadání **CRecordset::userAllocMultiRowBuffers** bez zadání `CRecordset::useMultiRowFetch` způsobí selhání kontrolního výrazu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud nenulové hodnoty `CRecordset` objekt byl úspěšně otevřen; jinak hodnota 0, pokud [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) (Pokud je volána), vrátí hodnotu 0.  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li spustit dotaz definovaný sadou záznamů, je zapotřebí zavolat tuto členskou funkci. Před voláním **otevřete**, je nutné vytvořit objekt sady záznamů.  
  
 Tato sada záznamů připojení ke zdroji dat závisí na tom, jak vytvořit sadu záznamů před voláním **otevřete**. Pokud předáte [CDatabase](../../mfc/reference/cdatabase-class.md) objektu do konstruktoru záznamů, který nebyl připojen ke zdroji dat používá tuto funkci člen [GetDefaultConnect](#getdefaultconnect) pokusu o otevření objektu databáze. Pokud předáte **NULL** do konstruktoru záznamů konstruktoru vytvoří `CDatabase` objektu, a **otevřete** pokusí připojit k databázovému objektu. Podrobnosti o zavření sady záznamů a připojení těchto různých okolností, najdete v části [Zavřít](#close).  
  
> [!NOTE]
>  Přístup ke zdroji dat pomocí objektu `CRecordset` je vždy sdílen. Na rozdíl od třídy `CDaoRecordset` nelze objekt `CRecordset` použít k otevření zdroje dat s výhradním přístupem.  
  
 Při volání **otevřete**, dotaz, obvykle SQL **vyberte** prohlášení, vybere záznamů na základě kritérií, které jsou uvedené v následující tabulce.  
  
|Hodnota parametru IpszSQL|Zvolené záznamy jsou určeny|Příklad|  
|------------------------------------|----------------------------------------|-------------|  
|**HODNOTU NULL**|Řetězec vrácený funkcí `GetDefaultSQL`.||  
|Název tabulky SQL|Všechny sloupce tabulkového seznamu ve funkci `DoFieldExchange` nebo `DoBulkFieldExchange`.|`"Customer"`|  
|Název předdefinovaného dotazu (uložené procedury)|Sloupce, k jejichž vrácení je dotaz definován.|`"{call OverDueAccts}"`|  
|**Vyberte** seznamu sloupců **FROM** seznam tabulek|Zadané sloupce ze zadané tabulky nebo tabulek.|`"SELECT CustId, CustName FROM`<br /><br /> `Customer"`|  
  
> [!CAUTION]
>  Ujistěte se, že do řetězce jazyka SQL nebyly vloženy prázdné znaky. Například, pokud vložení mezery mezi složené závorky a **volání** bude špatně interpretovat řetězec SQL jako název tabulky a začleňte je do – klíčové slovo, MFC **vyberte** příkaz, který bude mít za následek Probíhá došlo k výjimce. Podobně pokud předdefinovaný dotaz používá výstupní parametr, nevkládejte mezery mezi složené závorky a '' symbol. Nakonec nesmí Vložit prázdné před složených závorek v **volání** příkaz nebo před ním **vyberte** – klíčové slovo v **vyberte** příkaz.  
  
 Součástí postupu je předat **NULL** k **otevřete**; v takovém případě **otevřete** volání [GetDefaultSQL](#getdefaultsql). Pokud používáte odvozeným `CRecordset` třídy, **GetDefaultSQL** poskytuje názvy tabulky jste zadali v ClassWizard. Místo toho lze zadat jiné informace v parametru `lpszSQL`.  
  
 Ať předáte **otevřete** vytvoří konečnou řetězec SQL pro dotaz (řetězec může mít SQL **kde** a **ORDER BY** klauzule připojenou k `lpszSQL` je řetězec Předaný) a potom provede daný dotaz. Můžete zkontrolovat vytvořený řetězec voláním [GetSQL](#getsql) po volání **otevřete**. Další podrobnosti o tom, jak sady záznamů vytvoří příkazu jazyka SQL a vybere záznamy, najdete v článku [sada záznamů: Jak sady záznamů vyberte záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md).  
  
 Datové členy polí třídy sady záznamů jsou svázány se sloupci zvolených dat. Jsou-li vráceny jakékoli záznamy, první záznam se stává aktuálním záznamem.  
  
 Pokud chcete nastavit možnosti sady záznamů, jako je například filtrování nebo řazení, specifikovat, co vytvoříte objekt sady záznamů, ale před voláním **otevřete**. Pokud chcete aktualizovat záznamy v sadě záznamů po sada záznamů je už otevřený, volejte [Requery –](#requery).  
  
 Další informace, včetně další příklady najdete v článcích [záznamů (ODBC)](../../data/odbc/recordset-odbc.md), [sada záznamů: Jak sady záznamů vyberte záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md), a [sada záznamů: vytváření a uzavírání Sady záznamů (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md).  
  
### <a name="example"></a>Příklad  
 Následující příklady kódu ukazují různé formy **otevřete** volání.  
  
 [!code-cpp[NVC_MFCDatabase#16](../../mfc/codesnippet/cpp/crecordset-class_15.cpp)]  
  
##  <a name="refreshrowset"></a>CRecordset::RefreshRowset  
 Aktualizuje data a stav pro řádek v aktuální sadě řádků.  
  
```  
void RefreshRowset(
    WORD wRow,  
    WORD wLockType = SQL_LOCK_NO_CHANGE);
```  
  
### <a name="parameters"></a>Parametry  
 `wRow`  
 Na základě jedné pozice řádku v aktuální sadě řádků. Tato hodnota v rozsahu nula velikost sady řádků.  
  
 `wLockType`  
 Hodnota, která určuje, jak uzamknout řádek po jeho aktualizaci. Podrobnosti najdete v tématu poznámky.  
  
### <a name="remarks"></a>Poznámky  
 Pokud předáte hodnotu nula pro `wRow`, pak se aktualizují každý řádek v dané sadě řádků.  
  
 Použít `RefreshRowset`, musí jste implementovali hromadné načítání řádků zadáním **CRecordset::useMulitRowFetch** možnost [otevřete](#open) – členská funkce.  
  
 `RefreshRowset`volání funkce rozhraní API ODBC **SQLSetPos**. `wLockType` Parametr určuje stav zámku řádek po **SQLSetPos** má provést. Následující tabulka popisuje možné hodnoty pro `wLockType`.  
  
|wLockType|Popis|  
|---------------|-----------------|  
|`SQL_LOCK_NO_CHANGE`(výchozí hodnota)|Zdroj ovladače nebo data zajišťuje, že řádek v takovém stavu uzamčení nebo odemknout před `RefreshRowset` byla volána.|  
|`SQL_LOCK_EXCLUSIVE`|Ovladače nebo datový zdroj výhradně zamkne řádek. Ne všechny zdroje dat podporují tento typ zámku.|  
|`SQL_LOCK_UNLOCK`|Ovladače nebo datový zdroj odemkne řádek. Ne všechny zdroje dat podporují tento typ zámku.|  
  
 Další informace o **SQLSetPos**, najdete v části Windows SDK. Další informace o hromadné načítání řádků, najdete v článku [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="requery"></a>CRecordset::Requery  
 Znovu sestaví (obnovení) sady záznamů.  
  
```  
virtual BOOL Requery();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud sada záznamů byl úspěšně znovu sestaven; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Jsou-li vráceny jakékoli záznamy, první záznam se stává aktuálním záznamem.  
  
 V pořadí sady záznamů tak, aby odrážela přidání a odstranění, které vy nebo jiní uživatelé využívají ke zdroji dat, musíte znovu vytvořit sadu záznamů voláním **Requery –**. Pokud je dynamická sada záznamů, automaticky zobrazuje aktualizace, které vy nebo jiní uživatelé provést na existující záznamy (ale ne dodatky). Pokud je sada záznamů snímku, musí volat **Requery** tak, aby odrážela úpravy ostatní uživatelé a také přidání a odstranění.  
  
 Dynamická sada nebo snímek, volání **Requery** kdykoli chcete znovu vytvořit sadu záznamů pomocí nový filtr nebo řazení nebo nové hodnoty parametrů. Nastavte novou vlastnost filtru nebo řazení přiřazením nové hodnoty pro **m_strFilter** a `m_strSort` před voláním **Requery –**. Nastavit nové parametry přiřazením nové hodnoty pro parametry datových členů před voláním **Requery –**. Pokud filtrování a řazení řetězců beze změny, můžete opakovaně použít dotaz, což zvyšuje výkon.  
  
 Pokud se nezdaří pokus o znovu vytvoření sady záznamů, sada záznamů je zavřený. Před voláním **Requery –**, můžete určit, zda může být sada záznamů fokusu voláním `CanRestart` – členská funkce. `CanRestart`není zaručeno, který **Requery** bude úspěšné.  
  
> [!CAUTION]
>  Volání **Requery –** až poté, co můžete volat [otevřete](#open).  
  
### <a name="example"></a>Příklad  
 Tento příklad znovu sestaví sady záznamů použít jiné pořadí řazení.  
  
 [!code-cpp[NVC_MFCDatabase#29](../../mfc/codesnippet/cpp/crecordset-class_16.cpp)]  
  
##  <a name="setabsoluteposition"></a>CRecordset::SetAbsolutePosition  
 Umisťuje sadu záznamů na záznam odpovídající číslo zadaný záznam.  
  
```  
void SetAbsolutePosition(long nRows);
```  
  
### <a name="parameters"></a>Parametry  
 `nRows`  
 Na základě jedné pořadové číslo pozice pro aktuální záznam v sadě záznamů.  
  
### <a name="remarks"></a>Poznámky  
 `SetAbsolutePosition`přesune ukazatel aktuální záznam na základě této pozice řadových číslovek.  
  
> [!NOTE]
>  Tento člen funkce není platná na dopředné sady záznamů.  
  
 Pro sady záznamů rozhraní ODBC odkazuje na nastavení absolutní umístění 1 na první záznam v sadě záznamů; Hodnota 0 odkazuje na začátku souboru pozici (BOF).  
  
 Můžete také předat záporné hodnoty k `SetAbsolutePosition`. V takovém případě pozice sady záznamů se vyhodnotí z konce sady záznamů. Například `SetAbsolutePosition( -1 )` Přesune aktuální záznamů ukazatele na poslední záznam v sadě záznamů.  
  
> [!NOTE]
>  Absolutní umístění není určena pro použití jako náhradní číslo záznamu. Záložky jsou stále doporučeným způsobem zachování a vrátilo se do dané pozici od pozice změny záznamu při odstranění předchozí záznamů. Kromě toho můžete nelze si být jistí, že daný záznam budou mít stejné absolutní pozici Pokud sady záznamů se znovu vytvoří znovu vzhledem k tomu, že není zaručena pořadí jednotlivých záznamů v rámci sady záznamů, pokud není vytvořená s příkazem SQL pomocí **Order** klauzule.  
  
 Další informace o navigaci v sadě záznamů a záložky, najdete v článcích [sada záznamů: posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) a [sada záznamů: záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).  
  
##  <a name="setbookmark"></a>CRecordset::SetBookmark  
 Umisťuje sadu záznamů na záznam obsahující zadanou záložkou.  
  
```  
void SetBookmark(const CDBVariant& varBookmark);
```  
  
### <a name="parameters"></a>Parametry  
 `varBookmark`  
 Odkaz na [CDBVariant](../../mfc/reference/cdbvariant-class.md) objekt obsahující hodnotu záložku pro konkrétní záznam.  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li zjistit, jestli jsou na sadu záznamů podporuje záložky, volejte [CanBookmark](#canbookmark). Pro záložky byly k dispozici, pokud jsou podporovány, je třeba nastavit **CRecordset::useBookmarks** možnost `dwOptions` parametr [otevřete](#open) – členská funkce.  
  
> [!NOTE]
>  Pokud záložky nepodporovaný nebo nedostupný, volání `SetBookmark` bude mít za následek výjimku hlášeny. Záložky nejsou podporovány na dopředné sady záznamů.  
  
 Nejdřív načíst záložku na aktuální záznam, volání [GetBookmark](#getbookmark), což šetří záložku hodnota, která má `CDBVariant` objektu. Později, můžete se vrátit záznamů voláním `SetBookmark` pomocí hodnoty uložené záložky.  
  
> [!NOTE]
>  Po určité operace sady záznamů, byste měli zkontrolovat trvalost záložku před voláním `SetBookmark`. Například, pokud je načíst Záložka s `GetBookmark` a pak zavolají **Requery –**, Záložka již nebude platný. Volání [CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) zkontrolujte, zda můžete bezpečně volat `SetBookmark`.  
  
 Další informace o záložky a navigaci v sadě záznamů, najdete v článcích [sada záznamů: záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) a [sada záznamů: posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).  
  
##  <a name="setfielddirty"></a>CRecordset::SetFieldDirty  
 Flags – datový člen pole sady záznamů, jak změnit nebo jako beze změny.  
  
```  
void SetFieldDirty(void* pv, BOOL bDirty = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pv`  
 Obsahuje pole datového člena v sadě záznamů adresu nebo **NULL**. Pokud **NULL**, jsou označeny všechna pole datových členů v sadě záznamů. (C++ **NULL** není stejná jako hodnota Null v terminologii databáze, což znamená "žádná hodnota s".)  
  
 `bDirty`  
 **Hodnota TRUE,** Pokud pole datového člena je označen jako "nesprávné" (změněné). V opačném případě **FALSE** Pokud pole datového člena je označen jako "čisté" (beze změny).  
  
### <a name="remarks"></a>Poznámky  
 Označení pole jako beze změny zajišťuje pole není aktualizován a má za následek menší provoz SQL.  
  
> [!NOTE]
>  Tento člen funkce se nedá použít na sady záznamů, které používají hromadné načítání řádků. Pokud jste implementovali hromadné načítání řádků, pak `SetFieldDirty` způsobí selhání kontrolního výrazu. Další informace o hromadné načítání řádků, najdete v článku [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Značky framework změnit pole datových členů zajistit, že se budou zapisovat do záznamu ve zdroji dat pomocí mechanismus pole záznamu (exchange – RFX). Změna hodnoty pole obecně nastaví pole změny automaticky, takže bude málokdy potřeba volat `SetFieldDirty` sami, ale můžete někdy chtít zajistit, že sloupce budou explicitně aktualizovat nebo vložit bez ohledu na to, jaké hodnota je v datech pole člen.  
  
> [!CAUTION]
>  Volání této funkce člen až poté, co můžete volat [upravit](#edit) nebo [AddNew](#addnew).  
  
 Pomocí **NULL** pro první argument funkce se vztahují pouze k funkci **outputColumn** polí není **param** pole. Například volání  
  
 [!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]  
  
 Nastaví pouze **outputColumn** polí k **NULL**; **param** pole, zůstanou beze změn.  
  
 Pro práci na **param** pole, je třeba zadat adresu skutečného jednotlivých **param** chcete pracovat, jako například:  
  
 [!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]  
  
 To znamená, že nelze nastavit všechny **param** polí k **NULL**, stejně jako **outputColumn** pole.  
  
##  <a name="setfieldnull"></a>CRecordset::SetFieldNull  
 Pole datových členů sady záznamů příznaky jako hodnotu Null (konkrétně nutnosti žádná hodnota) nebo jinou hodnotu než Null.  
  
```  
void SetFieldNull(void* pv, BOOL bNull = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pv`  
 Obsahuje pole datového člena v sadě záznamů adresu nebo **NULL**. Pokud **NULL**, jsou označeny všechna pole datových členů v sadě záznamů. (C++ **NULL** není stejná jako hodnota Null v terminologii databáze, což znamená "žádná hodnota s".)  
  
 `bNull`  
 Nenulové hodnoty, pokud je pole data člen bude označen jako s žádnou hodnotu (Null). Jinak hodnota 0, pokud datový člen pole bude označen jako nesmí být nulová.  
  
### <a name="remarks"></a>Poznámky  
 Když přidáte nový záznam do sady záznamů, jsou všechny datové členy původně nastavená na hodnotu Null a označené jako "nesprávné" (změněné). Pokud načítáte záznam ze zdroje dat, její sloupce buď již mít hodnoty, nebo hodnotu Null.  
  
> [!NOTE]
>  Nevolejte tuto funkci člena na sady záznamů, které používají hromadné načítání řádků. Pokud jste implementovali hromadné načítání řádků, volání `SetFieldNull` výsledkem selhání kontrolního výrazu. Další informace o hromadné načítání řádků, najdete v článku [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Pokud chcete konkrétně určíte pole na aktuální záznam, který nemá hodnotu volání `SetFieldNull` s `bNull` nastavena na **TRUE** na příznak jako hodnotu Null. Pokud byl dříve označená pole hodnotu Null a teď chcete u ní hodnotu, jednoduše nastavte ho na novou hodnotu. Nemáte odeberte příznak Null s `SetFieldNull`. Pokud chcete zjistit, zda pole může mít hodnotu Null, volání `IsFieldNullable`.  
  
> [!CAUTION]
>  Volání této funkce člen až poté, co můžete volat [upravit](#edit) nebo [AddNew](#addnew).  
  
 Pomocí **NULL** pro první argument funkce se vztahují pouze k funkci **outputColumn** polí není **param** pole. Například volání  
  
 [!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]  
  
 Nastaví pouze **outputColumn** polí k **NULL**; **param** pole, zůstanou beze změn.  
  
 Pro práci na **param** pole, je třeba zadat adresu skutečného jednotlivých **param** chcete pracovat, jako například:  
  
 [!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]  
  
 To znamená, že nelze nastavit všechny **param** polí k **NULL**, stejně jako **outputColumn** pole.  
  
> [!NOTE]
>  Při nastavování parametrů na hodnotu Null, volání `SetFieldNull` předtím, než je otevřen má za následek kontrolní výrazy záznamů. V takovém případě volání [SetParamNull](#setparamnull).  
  
 `SetFieldNull`se implementuje pomocí [DoFieldExchange](#dofieldexchange).  
  
##  <a name="setlockingmode"></a>CRecordset::SetLockingMode  
 Nastaví režim uzamčení "optimistické" uzamčení (výchozí) nebo "pesimistické" uzamčení. Určuje, jak jsou záznamy uzamčeny aktualizací.  
  
```  
void SetLockingMode(UINT nMode);
```  
  
### <a name="parameters"></a>Parametry  
 `nMode`  
 Obsahuje jeden z následujících hodnot z **výčtu LockMode**:  
  
- **Optimistické** optimistické zamykání uzamkne záznam aktualizované pouze během volání **aktualizace**.  
  
- **Pesimistické** pesimistické zamykání uzamkne záznam co nejrychleji **upravit** se nazývá a udržuje ho uzamčení až **aktualizace** dokončení volání nebo přesunout do nového záznamu.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce člen, pokud je potřeba určit, které používá pro aktualizace sady záznamů dva strategie zamykání záznamů. Ve výchozím nastavení, je režim uzamčení sady záznamů **optimistickou metodu**. Který, můžete změnit na více zvýšení opatrnosti **pesimistické** strategie uzamčení. Volání `SetLockingMode` po vytvoření a otevřete objekt sady záznamů, ale před voláním **upravit**.  
  
##  <a name="setparamnull"></a>CRecordset::SetParamNull  
 Příznaky parametr hodnotu Null (konkrétně nutnosti žádná hodnota) nebo jako nesmí být nulová.  
  
```  
void SetParamNull(
    int nIndex,  
    BOOL bNull = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index založený na nule parametru.  
  
 `bNull`  
 Pokud **TRUE** (výchozí hodnota), parametr označen příznakem jako hodnotu Null. Jinak hodnota parametru označení nesmí být nulová.  
  
### <a name="remarks"></a>Poznámky  
 Na rozdíl od [SetFieldNull](#setfieldnull), můžete volat `SetParamNull` před otevřením sady záznamů.  
  
 `SetParamNull`Obvykle se používá s předdefinované dotazy (uložené procedury).  
  
##  <a name="setrowsetcursorposition"></a>CRecordset::SetRowsetCursorPosition  
 Posune kurzor na řádek v aktuální sadě řádků.  
  
```  
void SetRowsetCursorPosition(WORD wRow, WORD wLockType = SQL_LOCK_NO_CHANGE);
```  
  
### <a name="parameters"></a>Parametry  
 `wRow`  
 Na základě jedné pozice řádku v aktuální sadě řádků. Tato hodnota musí být v rozsahu 1 až velikost sady řádků.  
  
 `wLockType`  
 Hodnota označující, jak uzamknout řádek po jeho aktualizaci. Podrobnosti najdete v tématu poznámky.  
  
### <a name="remarks"></a>Poznámky  
 Při implementaci hromadné načítání řádků, zaznamenává se načítají pomocí sad řádků, pokud je první záznam v načtených řádků na aktuální záznam. Chcete-li nastavit jiný záznam v dané sadě řádků na aktuální záznam, volání `SetRowsetCursorPosition`. Například můžete kombinovat `SetRowsetCursorPosition` s [GetFieldValue](#getfieldvalue) – členská funkce se dynamicky načíst data ze všech záznamů sady záznamů.  
  
 Použít `SetRowsetCursorPosition`, musí jste implementovali hromadné načítání řádků zadáním `CRecordset::useMultiRowFetch` možnost `dwOptions` parametr ve [otevřete](#open) – členská funkce.  
  
 `SetRowsetCursorPosition`volání funkce rozhraní API ODBC **SQLSetPos**. `wLockType` Parametr určuje stav zámku řádek po **SQLSetPos** má provést. Následující tabulka popisuje možné hodnoty pro `wLockType`.  
  
|wLockType|Popis|  
|---------------|-----------------|  
|`SQL_LOCK_NO_CHANGE`(výchozí hodnota)|Zdroj ovladače nebo data zajišťuje, že řádek v takovém stavu uzamčení nebo odemknout před `SetRowsetCursorPosition` byla volána.|  
|`SQL_LOCK_EXCLUSIVE`|Ovladače nebo datový zdroj výhradně zamkne řádek. Ne všechny zdroje dat podporují tento typ zámku.|  
|`SQL_LOCK_UNLOCK`|Ovladače nebo datový zdroj odemkne řádek. Ne všechny zdroje dat podporují tento typ zámku.|  
  
 Další informace o **SQLSetPos**, najdete v části Windows SDK. Další informace o hromadné načítání řádků, najdete v článku [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="setrowsetsize"></a>CRecordset::SetRowsetSize  
 Určuje počet záznamů, které chcete načíst během fetch.  
  
```  
virtual void SetRowsetSize(DWORD dwNewRowsetSize);
```  
  
### <a name="parameters"></a>Parametry  
 *dwNewRowsetSize*  
 Počet řádků, které mají načíst při daném načtení.  
  
### <a name="remarks"></a>Poznámky  
 Tento člen virtuální funkce určuje, kolik řádků chcete načíst během jednoho načtení při použití hromadné načítání řádků. K implementaci hromadné načítání řádků, je nutné nastavit `CRecordset::useMultiRowFetch` možnost `dwOptions` parametr [otevřete](#open) – členská funkce.  
  
> [!NOTE]
>  Volání metody `SetRowsetSize` bez implementace hromadné načítání řádků bude mít za následek selhání kontrolního výrazu.  
  
 Volání `SetRowsetSize` před voláním **otevřete** původně nastavení velikosti řádků sady záznamů. Výchozí velikost řádků při implementaci hromadné načítání řádků je 25.  
  
> [!NOTE]
>  Buďte opatrní při volání metody `SetRowsetSize`. Pokud jsou ručně přidělování paměti pro data (jak je stanoveno **CRecordset::userAllocMultiRowBuffers** možnost parametru dwOptions v **otevřete**), byste měli zkontrolovat, jestli je potřeba Po zavolání metody znovu přidělte vyrovnávací paměti úložiště `SetRowsetSize`, ale před provedením jakékoli operace kurzoru navigace.  
  
 Chcete-li získat aktuální nastavení velikosti sady řádků, volejte [GetRowsetSize](#getrowsetsize).  
  
 Další informace o hromadné načítání řádků, najdete v článku [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="update"></a>CRecordset::Update  
 Dokončení `AddNew` nebo **upravit** operaci uložením nových nebo upravených dat na datovém zdroji.  
  
```  
virtual BOOL Update();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud jeden záznam byla úspěšně aktualizována; jinak hodnota 0, pokud nejsou uvedeny žádné sloupce změnily. Pokud žádné záznamy se aktualizovaly, nebo pokud se více než jeden záznam byl aktualizován, je vyvolána výjimka. Je také vyvolána výjimka pro další selhání na datovém zdroji.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce člen po volání [AddNew](#addnew) nebo [upravit](#edit) – členská funkce. Toto volání je nutné pro dokončení `AddNew` nebo **upravit** operaci.  
  
> [!NOTE]
>  Pokud jste implementovali hromadné načítání řádků, nelze volat **aktualizace**. Tato akce způsobí selhání kontrolního výrazu. Přestože třída `CRecordset` neposkytuje mechanismus pro hromadnou aktualizaci řádků dat, můžete napsat vlastní funkce pomocí funkce rozhraní API ODBC **SQLSetPos**. Další informace o hromadné načítání řádků, najdete v článku [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Obě `AddNew` a **upravit** příprava ve kterém je umístěn přidané nebo upravených dat vyrovnávací paměti pro ukládání ke zdroji dat. **Aktualizace** uloží data. Jsou aktualizovány pouze pole označené nebo detekované jako změnit.  
  
 Pokud zdroj dat podporuje transakce, můžete provést **aktualizace** volání (a odpovídající `AddNew` nebo **upravit** volání) součástí transakce. Další informace o transakcích, najdete v článku [transakce (ODBC)](../../data/odbc/transaction-odbc.md).  
  
> [!CAUTION]
>  Když zavoláte **aktualizace** bez předchozího volání `AddNew` nebo **upravit**, **aktualizace** vyvolá `CDBException`. Když zavoláte `AddNew` nebo **upravit**, musí volat **aktualizace** před voláním **přesunout** operaci nebo před zavřením připojení ke zdroji dat nebo sady záznamů. Jinak vaše změny budou ztraceny bez oznámení.  
  
 Podrobnosti o zpracování **aktualizace** selhání, najdete v článku [sada záznamů: Jak sady záznamů aktualizace záznamů (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
### <a name="example"></a>Příklad  
 Najdete v článku [transakce: provádění transakcí v sadě záznamů (rozhraní ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).  
  
## <a name="see-also"></a>Viz také  
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CDatabase – třída](../../mfc/reference/cdatabase-class.md)   
 [CRecordView – třída](../../mfc/reference/crecordview-class.md)
