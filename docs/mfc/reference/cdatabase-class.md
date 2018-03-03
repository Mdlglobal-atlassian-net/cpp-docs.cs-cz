---
title: "CDatabase – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c6aeaa64b0b665449ee9216070cdebbc2632948b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cdatabase-class"></a>CDatabase – třída
Reprezentuje připojení ke zdroji dat, pomocí kterého lze provozovat na datovém zdroji.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDatabase : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CDatabase::CDatabase](#cdatabase)|Vytvoří `CDatabase` objektu. Je třeba inicializovat objekt voláním `OpenEx` nebo **otevřete**.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDatabase::BeginTrans](#begintrans)|Spustí "transakcí" – řadu reverzibilního volání `AddNew`, **upravit**, **odstranit**, a **aktualizace** členské funkce třídy `CRecordset` – na zdroj dat připojené. Zdroj dat musí podporovat transakce **metody BeginTrans** nemá žádný vliv.|  
|[CDatabase::BindParameters](#bindparameters)|Umožňuje svázání parametrů před voláním `CDatabase::ExecuteSQL`.|  
|[CDatabase::Cancel](#cancel)|Zruší asynchronní operaci nebo proces z druhé vlákna.|  
|[CDatabase::CanTransact](#cantransact)|Vrátí nenulové hodnoty, pokud je zdroj dat podporuje transakce.|  
|[CDatabase::CanUpdate](#canupdate)|Vrátí nenulové hodnoty, pokud `CDatabase` objekt je v aktualizovatelné (ne jen pro čtení).|  
|[CDatabase::Close](#close)|Zavře připojení ke zdroji dat.|  
|[CDatabase::CommitTrans](#committrans)|Dokončení transakce začne po **metody BeginTrans**. Příkazy v rámci transakce, které alter zdroji dat jsou prováděny postupně.|  
|[CDatabase::ExecuteSQL](#executesql)|Provede dotaz SQL. Jsou vráceny žádné záznamy data.|  
|[CDatabase::GetBookmarkPersistence](#getbookmarkpersistence)|Identifikuje operací, pomocí kterých záložky na objekty sady záznamů zachovají.|  
|[CDatabase::GetConnect](#getconnect)|Vrátí připojovací řetězec ODBC používaná k připojení `CDatabase` objekt ke zdroji dat.|  
|[CDatabase::GetCursorCommitBehavior](#getcursorcommitbehavior)|Identifikuje účinek potvrzování transakce na objekt otevřete sady záznamů.|  
|[CDatabase::GetCursorRollbackBehavior](#getcursorrollbackbehavior)|Identifikuje účinek vrácení transakce zpět na objekt otevřete sady záznamů.|  
|[CDatabase::GetDatabaseName](#getdatabasename)|Vrací název databáze aktuálně používá.|  
|[CDatabase::IsOpen](#isopen)|Vrátí nenulové hodnoty, pokud `CDatabase` objekt je aktuálně připojený ke zdroji dat.|  
|[CDatabase::OnSetOptions](#onsetoptions)|Voláno rámcem pro nastavení možností standardní připojení. Výchozí implementace nastaví hodnotu časového limitu dotazu. Tyto možnosti předem, můžete vytvořit voláním `SetQueryTimeout`.|  
|[CDatabase::Open](#open)|Vytvoří připojení ke zdroji dat (prostřednictvím ovladače ODBC).|  
|[CDatabase::OpenEx](#openex)|Vytvoří připojení ke zdroji dat (prostřednictvím ovladače ODBC).|  
|[CDatabase::Rollback](#rollback)|Vrátí zpět změny provedené v průběhu aktuální transakci. Zdroj dat vrátí do původního stavu, jak jsou definovány v **metody BeginTrans** volání, která je v nezměněném stavu.|  
|[CDatabase::SetLoginTimeout](#setlogintimeout)|Nastaví počet sekund, po které dojde k pokusu o připojení zdroje dat vypršení časového limitu.|  
|[CDatabase::SetQueryTimeout](#setquerytimeout)|Nastaví počet sekund, po které databázové dotaz operace bude časový limit. Ovlivňuje všechny následné záznamů **otevřete**, `AddNew`, **upravit**, a **odstranit** volání.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CDatabase::m_hdbc](#m_hdbc)|Otevřete popisovač připojení databáze rozhraní ODBC ke zdroji dat. Typ **HDBC**.|  
  
## <a name="remarks"></a>Poznámky  
 Zdroj dat je konkrétní instanci data hostovány systémem správy některé databáze (databázového systému). Mezi příklady patří Microsoft SQL Server, Microsoft Access, aktualizované dBASE a xBASE. Může mít jeden nebo více `CDatabase` objektů active současně ve vaší aplikaci.  
  
> [!NOTE]
>  Pokud pracujete s třídy objektů DAO (Data Access), nikoli třídy připojení ODBC (Open Database), použijte třídu [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) místo. Další informace najdete v článku [přehled: programování databáze](../../data/data-access-programming-mfc-atl.md).  
  
 Chcete-li použít `CDatabase`, vytvořit `CDatabase` objekt a volání jeho `OpenEx` – členská funkce. Otevře připojení. Když potom vytvoříte `CRecordset` objekty pro provoz na připojeného zdroje dat, předat konstruktoru záznamů ukazatel na vaše `CDatabase` objektu. Po dokončení práce připojení, volejte **Zavřít** členské funkce a zrušení `CDatabase` objektu. **Zavřít** zavře všechny sady záznamů knihovnou dříve.  
  
 Další informace o `CDatabase`, najdete v článcích [datové zdroje (ODBC)](../../data/odbc/data-source-odbc.md) a [přehled: programování databáze](../../data/data-access-programming-mfc-atl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDatabase`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdb.h  
  
##  <a name="begintrans"></a>CDatabase::BeginTrans  
 Volání této funkce člen k zahájení transakce s připojeného zdroje dat.  
  
```  
BOOL BeginTrans();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud bylo volání úspěšné a jsou změny potvrzeny pouze ručně. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Transakce se skládá z jedné nebo více volání `AddNew`, **upravit**, **odstranit**, a **aktualizace** členské funkce `CRecordset` objektu. Před zahájením transakce, `CDatabase` objekt musí již byla připojena k zdroj dat voláním jeho `OpenEx` nebo **otevřete** – členská funkce. K ukončení transakce, volání [CommitTrans](#committrans) přijmout všechny změny do zdroje dat (a je provádět) nebo volání [vrácení zpět](#rollback) k přerušení celá transakce. Volání **metody BeginTrans** po otevření účastní operace všechny sady záznamů a jako blízko skutečnou aktualizace operations nejdříve.  
  
> [!CAUTION]
>  V závislosti na vaší ovladač ODBC otevírat záznamů před voláním **metody BeginTrans** může způsobit problémy při volání metody **vrácení zpět**. Byste měli zkontrolovat konkrétní ovladač, který používáte. Například při použití ovladače Microsoft Access součástí Microsoft ODBC Desktop ovladač Pack 3.0, musíte vzít v úvahu pro databázový stroj Jet požadavek, že by neměl začínat transakce na všechny databáze, který má otevřít kurzor. V databázové třídy MFC otevřít kurzor znamená otevřenou `CRecordset` objektu. Další informace najdete v tématu [Technická poznámka 68](../../mfc/tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver.md).  
  
 **Metody BeginTrans** může také uzamčení záznamů dat na serveru, v závislosti na požadované souběžnost a možností zdroj dat. Informace o uzamčení data, najdete v článku [sada záznamů: zamykání záznamů (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).  
  
 Uživatelská transakce je podrobně popsaný v článku [transakce (ODBC)](../../data/odbc/transaction-odbc.md).  
  
 **Metody BeginTrans** vytváří stavu, do které pořadí transakcí možné vrátit zpět (vrátit). Vytvořit nový stav pro vrácení zpět, potvrďte aktuální transakce, pak zavolají **metody BeginTrans** znovu.  
  
> [!CAUTION]
>  Volání metody **metody BeginTrans** znovu bez volání **CommitTrans** nebo **vrácení zpět** chybu.  
  
 Volání [CanTransact](#cantransact) – členská funkce k určení, zda ovladač podporuje transakce pro danou databázi. Měli byste také zavolat [GetCursorCommitBehavior](#getcursorcommitbehavior) a [GetCursorRollbackBehavior](#getcursorrollbackbehavior) k určení podporu písmen a zachovávání kurzoru.  
  
 Další informace o transakcích, najdete v článku [transakce (ODBC)](../../data/odbc/transaction-odbc.md).  
  
### <a name="example"></a>Příklad  
  Najdete v článku [transakce: provádění transakcí v sadě záznamů (rozhraní ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).  
  
##  <a name="bindparameters"></a>CDatabase::BindParameters  
 Přepsání `BindParameters` když potřebujete pro svázání parametrů před voláním [CDatabase::ExecuteSQL](#executesql).  
  
```  
virtual void BindParameters(HSTMT hstmt);
```  
  
### <a name="parameters"></a>Parametry  
 `hstmt`  
 Popisovač příkazu ODBC, pro které chcete pro svázání parametrů.  
  
### <a name="remarks"></a>Poznámky  
 Tento přístup je užitečné, když není nutné výsledek nastavit z uložené procedury.  
  
 V přepsání, volat **SQLBindParameters** a souvisejících funkcí rozhraní ODBC pro vazbu parametrů. MFC volá přepsání před volání `ExecuteSQL`. Není potřeba volat **SQLPrepare**; `ExecuteSQL` volání **SQLExecDirect** a zničí **hstmt**, který je použit pouze jednou.  
  
##  <a name="cancel"></a>CDatabase::Cancel  
 Volání této funkce člen k vyžádání, že zdroj dat zrušit asynchronní operace probíhá nebo proces z druhé vlákna.  
  
```  
void Cancel();
```  
  
### <a name="remarks"></a>Poznámky  
 Upozorňujeme, že třídy knihovny MFC rozhraní ODBC už použít asynchronní zpracování; k provedení určité operace asychronous, musí přímo volat rozhraní API ODBC funkce [SQLSetConnectOption](https://msdn.microsoft.com/library/ms713564.aspx). Další informace najdete v tématu [asynchronního spuštění](https://msdn.microsoft.com/library/ms713563.aspx) ve Windows SDK.  
  
##  <a name="cantransact"></a>CDatabase::CanTransact  
 Volání této funkce člen k určení, zda databáze umožňuje transakce.  
  
```  
BOOL CanTransact() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud nenulové hodnoty pomocí této sady záznamů `CDatabase` objektu povolit transakce; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Informace o transakcích, najdete v článku [transakce (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="canupdate"></a>CDatabase::CanUpdate  
 Volání této funkce člen můžete určit, zda `CDatabase` objekt umožňuje aktualizace.  
  
```  
BOOL CanUpdate() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě `CDatabase` aktualizace umožňuje objektu; jinak 0, která buď, které určuje předán **TRUE** v `bReadOnly` při otevření `CDatabase` objekt nebo že zdroj dat samotné je jen pro čtení. Zdroj dat je určeno jen pro čtení, pokud se volání funkce rozhraní API ODBC **SQLGetInfo** pro **SQL_DATASOURCE_READ_ONLY** vrátí "y".  
  
### <a name="remarks"></a>Poznámky  
 Ne všechny ovladače podporovat aktualizace.  
  
##  <a name="cdatabase"></a>CDatabase::CDatabase  
 Vytvoří `CDatabase` objektu.  
  
```  
CDatabase();
```  
  
### <a name="remarks"></a>Poznámky  
 Po vytváření objektu, musí volat jeho `OpenEx` nebo **otevřete** – členská funkce navázat připojení ke zdroji zadaná data.  
  
 Možná bude vhodné pro vložení `CDatabase` objekt ve třídě dokumentů.  
  
### <a name="example"></a>Příklad  
 Tento příklad ukazuje použití `CDatabase` v `CDocument`-odvozené třídy.  
  
 [!code-cpp[NVC_MFCDatabase#9](../../mfc/codesnippet/cpp/cdatabase-class_1.h)]  
  
 [!code-cpp[NVC_MFCDatabase#10](../../mfc/codesnippet/cpp/cdatabase-class_2.cpp)]  
  
##  <a name="close"></a>CDatabase::Close  
 Pokud chcete odpojit ze zdroje dat, volání této funkce člen.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Poznámky  
 Je nutné zavřít všechny sady záznamů přidružené `CDatabase` objekt před voláním této funkce člen. Protože **Zavřít** nezničí `CDatabase` objekt, můžete opakovaně použít objekt otevřením nové připojení ke stejnému zdroji dat nebo jinému zdroji dat.  
  
 Všechna nevyřízená `AddNew` nebo **upravit** došlo ke zrušení příkazů sad záznamů pomocí databáze a všechny čekající transakce jsou vráceny zpět. Všechny závislé na sady záznamů `CDatabase` objekt jsou ponechána v nedefinované stavu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDatabase#12](../../mfc/codesnippet/cpp/cdatabase-class_3.cpp)]  
  
##  <a name="committrans"></a>CDatabase::CommitTrans  
 Volání této funkce člen po dokončení transakce.  
  
```  
BOOL CommitTrans();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud aktualizace byly úspěšně potvrzeny; jinak 0. Pokud **CommitTrans** selže, stav zdroje dat není definován. Je nutné zkontrolovat data určit jeho stav.  
  
### <a name="remarks"></a>Poznámky  
 Transakce se skládá z řady volání `AddNew`, **upravit**, **odstranit**, a **aktualizace** členské funkce `CRecordset` objekt, který začal s volání na [metody BeginTrans](#begintrans) – členská funkce. **CommitTrans –** potvrdí transakce. Ve výchozím nastavení se aktualizace potvrdí okamžitě; volání metody **metody BeginTrans** způsobí, že závazek aktualizací se proto objevit až **CommitTrans** je volána.  
  
 Dokud zavoláte **CommitTrans** k ukončení transakce, můžete volat [vrácení zpět](#rollback) – členská funkce přerušení transakce a nechte zdroj dat v jejím původním stavu. Chcete-li zahájit novou transakci, volejte **metody BeginTrans** znovu.  
  
 Další informace o transakcích, najdete v článku [transakce (ODBC)](../../data/odbc/transaction-odbc.md).  
  
### <a name="example"></a>Příklad  
  Najdete v článku [transakce: provádění transakcí v sadě záznamů (rozhraní ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).  
  
##  <a name="executesql"></a>CDatabase::ExecuteSQL  
 Volání této funkce člen, pokud budete potřebovat k provedení příkazu SQL přímo.  
  
```  
void ExecuteSQL(LPCTSTR lpszSQL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszSQL`  
 Ukazatel na ukončené hodnotou null řetězec obsahující platný příkaz SQL k provedení. Můžete předat [CString](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="remarks"></a>Poznámky  
 Příkaz vytvořte jako řetězce ukončené hodnotou null. `ExecuteSQL`nevrací datových záznamů. Pokud chcete pracovat záznamů, použijte místo toho objekt sady záznamů.  
  
 Většina příkazů pro zdroj dat jsou vydávány prostřednictvím sady záznamů objekty, které podporují příkazy pro výběr dat, vkládání nových záznamů, odstraňování záznamů a úpravy záznamů. Ale ne všechny funkce ODBC je přímo podporované databázové třídy, takže může v některých případech třeba, aby přímá volání SQL s `ExecuteSQL`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDatabase#13](../../mfc/codesnippet/cpp/cdatabase-class_4.cpp)]  
  
##  <a name="getbookmarkpersistence"></a>CDatabase::GetBookmarkPersistence  
 Volání této funkce člen k určení zachování záložek na objekt sady záznamů po určité operace.  
  
```  
DWORD GetBookmarkPersistence() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Bitová maska, která identifikuje operací, pomocí kterých záložky na objekt sady záznamů zachovají. Podrobnosti najdete v tématu poznámky.  
  
### <a name="remarks"></a>Poznámky  
 Například, pokud zavoláte `CRecordset::GetBookmark` a pak zavolají `CRecordset::Requery`, záložku získaný `GetBookmark` zřejmě není platná. By měly volat `GetBookmarkPersistence` před voláním `CRecordset::SetBookmark`.  
  
 Následující tabulka uvádí bitová maska hodnoty, které mohou být kombinovány pro vrácenou hodnotu `GetBookmarkPersistence`.  
  
|Hodnota maskování bitů|Trvalost záložek|  
|-------------------|--------------------------|  
|`SQL_BP_CLOSE`|Záložky jsou platné po **Requery** operaci.|  
|`SQL_BP_DELETE`|Záložku pro řádek, je platný po **odstranit** operaci na daném řádku.|  
|`SQL_BP_DROP`|Záložky jsou platné po **Zavřít** operaci.|  
|`SQL_BP_SCROLL`|Záložky jsou platné po všech **přesunout** operaci. To jednoduše označuje, jestli záložky jsou podporovány v sadě záznamů, jak ho vrátila `CRecordset::CanBookmark`.|  
|`SQL_BP_TRANSACTION`|Záložky jsou platné po je transakce potvrzena nebo vrácena zpět.|  
|`SQL_BP_UPDATE`|Záložku pro řádek, je platný po **aktualizace** operaci na daném řádku.|  
|`SQL_BP_OTHER_HSTMT`|Záložky přidružený jeden objekt sady záznamů jsou platné ve druhé sady záznamů.|  
  
 Další informace o této návratovou hodnotu, najdete v části funkce rozhraní API ODBC **SQLGetInfo** ve Windows SDK. Další informace o záložky, najdete v článku [sada záznamů: záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).  
  
##  <a name="getconnect"></a>CDatabase::GetConnect  
 Volání této funkce člen načíst připojovací řetězec použitý při volání `OpenEx` nebo `Open` který připojený `CDatabase` objekt ke zdroji dat.  
  
```  
const CString GetConnect() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `const` [CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahující připojovací řetězec, pokud `OpenEx` nebo `Open` , jinak hodnota, musí být prázdný řetězec.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [CDatabase::Open](#open) popis vytvoření připojovacího řetězce.  
  
##  <a name="getcursorcommitbehavior"></a>CDatabase::GetCursorCommitBehavior  
 Volání této funkce člen k určení jak [CommitTrans](#committrans) operaci ovlivňuje kurzory na objekty otevřete sady záznamů.  
  
```  
int GetCursorCommitBehavior() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota označující vliv transakcí na objekty otevřete sady záznamů. Podrobnosti najdete v tématu poznámky.  
  
### <a name="remarks"></a>Poznámky  
 Následující tabulka uvádí možné návratové hodnoty pro `GetCursorCommitBehavior` a odpovídající vliv na otevřete sadu záznamů.  
  
|Návratová hodnota|Vliv na CRecordset – objekty|  
|------------------|----------------------------------|  
|`SQL_CB_CLOSE`|Volání `CRecordset::Requery` hned za potvrzení transakce.|  
|`SQL_CB_DELETE`|Volání `CRecordset::Close` hned za potvrzení transakce.|  
|`SQL_CB_PRESERVE`|Normálně pokračovat `CRecordset` operace.|  
  
 Další informace o této návratovou hodnotu, najdete v části funkce rozhraní API ODBC **SQLGetInfo** ve Windows SDK. Další informace o transakcích, najdete v článku [transakce (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="getcursorrollbackbehavior"></a>CDatabase::GetCursorRollbackBehavior  
 Volání této funkce člen k určení jak [vrácení zpět](#rollback) operaci ovlivňuje kurzory na objekty otevřete sady záznamů.  
  
```  
int GetCursorRollbackBehavior() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota označující vliv transakcí na objekty otevřete sady záznamů. Podrobnosti najdete v tématu poznámky.  
  
### <a name="remarks"></a>Poznámky  
 Následující tabulka uvádí možné návratové hodnoty pro `GetCursorRollbackBehavior` a odpovídající vliv na otevřete sadu záznamů.  
  
|Návratová hodnota|Vliv na CRecordset – objekty|  
|------------------|----------------------------------|  
|`SQL_CB_CLOSE`|Volání `CRecordset::Requery` hned za vrácení transakce.|  
|`SQL_CB_DELETE`|Volání `CRecordset::Close` hned za vrácení transakce.|  
|`SQL_CB_PRESERVE`|Normálně pokračovat `CRecordset` operace.|  
  
 Další informace o této návratovou hodnotu, najdete v části funkce rozhraní API ODBC **SQLGetInfo** ve Windows SDK. Další informace o transakcích, najdete v článku [transakce (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="getdatabasename"></a>CDatabase::GetDatabaseName  
 Volání této funkce člen získávání názvu aktuálně připojené databáze (za předpokladu, že zdroje dat definuje s názvem objektu s názvem "databáze").  
  
```  
CString GetDatabaseName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahující název databáze, pokud úspěšná, jinak, prázdnou `CString`.  
  
### <a name="remarks"></a>Poznámky  
 Toto není stejný jako název zdroje dat (DSN) zadaný v `OpenEx` nebo **otevřete** volání. Co `GetDatabaseName` vrátí závisí na ODBC. Obecně platí databázi je kolekce tabulek. Pokud tato entita má název, `GetDatabaseName` vrátí ji.  
  
 Můžete například zobrazit tento název v nadpisu. Pokud dojde k chybě při načítání názvu z rozhraní ODBC, `GetDatabaseName` vrátí prázdnou **Cstring**.  
  
##  <a name="isopen"></a>CDatabase::IsOpen  
 Volání této funkce člen můžete určit, zda `CDatabase` objekt je aktuálně připojený ke zdroji dat.  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud nenulové hodnoty `CDatabase` objektu je aktuálně připojen; jinak hodnota 0.  
  
##  <a name="m_hdbc"></a>CDatabase::m_hdbc  
 Obsahuje veřejné popisovač pro připojení zdroje dat ODBC – "popisovač připojení".  
  
### <a name="remarks"></a>Poznámky  
 Za normálních okolností bude mít potřeba získat přímo přístup k této proměnné členů. Místo toho rozhraní přiděluje popisovač při volání `OpenEx` nebo **otevřete**. Rozhraní framework zruší přidělení popisovač při volání **odstranit** operátor na `CDatabase` objektu. Všimněte si, že **Zavřít** – členská funkce není zrušit přidělení popisovač.  
  
 Za určitých okolností ale musíte používat popisovač přímo. Například, pokud je třeba volat funkce rozhraní API ODBC přímo a nikoli v rámci třídy `CDatabase`, může být nutné popisovač připojení pro předat jako parametr. Viz následující příklad kódu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDatabase#15](../../mfc/codesnippet/cpp/cdatabase-class_5.cpp)]  
  
##  <a name="onsetoptions"></a>CDatabase::OnSetOptions  
 Při provádění přímo příkazu jazyka SQL s volá rámec této – členská funkce `ExecuteSQL` – členská funkce.  
  
```  
virtual void OnSetOptions(HSTMT hstmt);
```  
  
### <a name="parameters"></a>Parametry  
 `hstmt`  
 Popisovač příkazu ODBC, pro které jsou nastavené možnosti.  
  
### <a name="remarks"></a>Poznámky  
 `CRecordset::OnSetOptions`také volá tuto funkci člen.  
  
 `OnSetOptions`Nastaví hodnotu časového limitu přihlášení. Pokud zde nejsou předchozích volání `SetQueryTimeout` a členské funkce `OnSetOptions` odráží aktuální hodnoty, jinak, nastaví výchozí hodnoty.  
  
> [!NOTE]
>  Před MFC 4.2 `OnSetOptions` buď snychronous nebo asynchronní také nastavit režim zpracovávání. Počínaje MFC 4.2, všechny operace jsou synchronní. Chcete-li provést asynchronní operaci, musíte provést přímé volání rozhraní API ODBC funkce **SQLSetPos**.  
  
 Není potřeba přepsat `OnSetOptions` Chcete-li změnit hodnotu časového limitu. Místo toho pokud chcete přizpůsobit časový limit dotazu, volání `SetQueryTimeout` před vytvořením sady záznamů; `OnSetOptions` budou používat novou hodnotu. Sada hodnoty se vztahují na dalších operacích na všechny sady záznamů nebo přímá volání SQL.  
  
 Přepsání `OnSetOptions` Pokud chcete nastavit další možnosti. Přepsání by měly volat základní třídy `OnSetOptions` před nebo po volání funkce rozhraní API ODBC **SQLSetStmtOption**. Postupujte podle metoda v rozhraní framework výchozí implementaci `OnSetOptions`.  
  
##  <a name="open"></a>CDatabase::Open  
 Volání této funkce člen k chybě při inicializaci nově vytvořený `CDatabase` objektu.  
  
```  
virtual BOOL Open(
    LPCTSTR lpszDSN,  
    BOOL bExclusive = FALSE,  
    BOOL bReadOnly = FALSE,  
    LPCTSTR lpszConnect = _T("ODBC;"),  
    BOOL bUseCursorLib = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszDSN`  
 Určuje název zdroje dat – název registrovaný s rozhraním ODBC prostřednictvím programu Správce rozhraní ODBC. Pokud je zadaná hodnota názvu DSN v `lpszConnect` (ve tvaru "DSN =\<zdroj dat >"), nesmí být zadaný znovu v `lpszDSN`. V takovém případě `lpszDSN` by měla být **NULL**. Jinak můžete předat **NULL** Pokud chcete uživateli zprostředkovali lze zobrazit dialogové okno zdroje dat, ve kterém může uživatel vybrat zdroj dat. Další informace najdete v části poznámky.  
  
 `bExclusive`  
 Není podporováno v této verzi knihovny tříd. V současné době kontrolní výrazy selže, pokud tento parametr je **TRUE**. Zdroj dat je vždy otevřít, protože sdílené (není výhradní).  
  
 `bReadOnly`  
 **Hodnota TRUE,** Pokud máte v úmyslu připojení jako jen pro čtení a aktualizace zdroje dat můžete zakázat. Všechny závislé sady záznamů zdědí tento atribut. Výchozí hodnota je **FALSE**.  
  
 `lpszConnect`  
 Určuje připojovací řetězec. Připojovací řetězec zřetězí informace, které by mohly mít včetně název zdroje dat, ID uživatele platný na zdroji dat, řetězec uživatele ověřování (heslo, pokud zdroj dat vyžaduje jednu) a další informace. Celý připojovací řetězec musí obsahovat předponu řetězec "ODBC;" (velká nebo malá písmena). "ODBC;" řetězec se používá k označení, že se připojení zdroje dat ODBC; Toto je pro vzestupnou kompatibility při budoucích verzích knihovny tříd může podporovat zdroje dat jiný ODBC.  
  
 `bUseCursorLib`  
 **Hodnota TRUE,** Pokud chcete, aby knihovna DLL kurzorů ODBC má být načten. Knihovna kurzorů zakrývá některé funkce základní ovladač ODBC, efektivně brání použití dynamické sady (Pokud je ovladač podporuje). Pouze kurzory podporována, pokud je načtena knihovna kurzorů jsou statické snímky a dopředné kurzory. Výchozí hodnota je **TRUE**. Pokud chcete vytvořit objekt sady záznamů přímo z `CRecordset` bez odvozování z něj, nesmí načítat knihovna kurzorů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud se připojení úspěšně; jinak 0, pokud uživatel vybere zrušit, když se zobrazí dialogové okno se žádostí o další informace o připojení. Ve všech ostatních případech rozhraní vyvolá výjimku.  
  
### <a name="remarks"></a>Poznámky  
 Databázový objekt musí inicializovat před použitím vytvořit objekt sady záznamů.  
  
> [!NOTE]
>  Volání [OpenEx](#openex) – členská funkce je upřednostňovaný způsob, jak připojit ke zdroji dat a inicializace objektu databáze.  
  
 Pokud parametry ve vaší **otevřete** volání neobsahují dostatek informací pro připojení, ovladač ODBC otevře dialogové okno se získat potřebné informace od uživatele. Při volání **otevřete**, připojovací řetězec, `lpszConnect`, je uložené v soukromě `CDatabase` objektu a je k dispozici při volání [GetConnect](#getconnect) – členská funkce.  
  
 Pokud chcete, můžete otevřít dialogové okno Vlastní před voláním **otevřete** získat informace o od uživatele, jako například heslo, pak přidejte tyto informace do připojovacího řetězce je předat do **otevřete**. Nebo můžete chtít uložit připojovací řetězec, předáte tak můžete znovu použít, je další čas voláními aplikace **otevřete** na `CDatabase` objektu.  
  
 Můžete také použít připojovací řetězec pro více úrovní ověřování přihlášení (jednotlivých jiné `CDatabase` objektu) nebo vyjádřit jiné informace specifické pro zdroj dat. Další informace o připojovacích řetězcích naleznete v kapitole 5 v sadě Windows SDK.  
  
 Je možné pro pokus o připojení k vypršení časového limitu, pokud například hostitel databázového systému nedostupný. Pokud se nezdaří pokus o připojení, **otevřete** vyvolá `CDBException`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDatabase#14](../../mfc/codesnippet/cpp/cdatabase-class_6.cpp)]  
  
##  <a name="openex"></a>CDatabase::OpenEx  
 Volání této funkce člen k chybě při inicializaci nově vytvořený `CDatabase` objektu.  
  
```  
virtual BOOL OpenEx(
    LPCTSTR lpszConnectString,  
    DWORD dwOptions = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszConnectString`  
 Určuje připojovací řetězec ODBC. To zahrnuje název zdroje dat a také další volitelné informace, jako je například ID uživatele a heslo. Například "DSN = SQLServer_Source; UID = SA; PWD = abc123 "je možné připojovací řetězec. Všimněte si, že pokud předáte **NULL** pro `lpszConnectString`, dialogové okno zdroje dat se zobrazí výzva k výběru zdroje dat.  
  
 `dwOptions`  
 Bitová maska, která určuje kombinaci následující hodnoty. Výchozí hodnota je 0, což znamená, že databáze otevřou jako sdílený přístup pro zápis, nebude možné načíst knihovnu DLL knihovny kurzorů ODBC a dialogové okno připojení rozhraní ODBC se zobrazí jenom v případě, že není k dispozici dostatek informací pro připojení.  
  
- **CDatabase::openExclusive** není podporováno v této verzi knihovny tříd. Zdroj dat je vždy otevřít, protože sdílené (není výhradní). Kontrolní výrazy v současné době selže, pokud zadáte tuto možnost.  
  
- **CDatabase::openReadOnly** otevřít zdroj dat jen pro čtení.  
  
- **CDatabase::useCursorLib** načíst knihovny kurzorů ODBC knihovny DLL. Knihovna kurzorů zakrývá některé funkce základní ovladač ODBC, efektivně brání použití dynamické sady (Pokud je ovladač podporuje). Pouze kurzory podporována, pokud je načtena knihovna kurzorů jsou statické snímky a dopředné kurzory. Pokud chcete vytvořit objekt sady záznamů přímo z `CRecordset` bez odvozování z něj, nesmí načítat knihovna kurzorů.  
  
- **CDatabase::noOdbcDialog** nezobrazovat ODBC připojení dialogových oken, bez ohledu na to, jestli je zadaný dostatek informací o připojení.  
  
- **CDatabase::forceOdbcDialog** vždycky zobrazí dialogové okno připojení ODBC.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud se připojení úspěšně; jinak 0, pokud uživatel vybere zrušit, když se zobrazí dialogové okno se žádostí o další informace o připojení. Ve všech ostatních případech rozhraní vyvolá výjimku.  
  
### <a name="remarks"></a>Poznámky  
 Databázový objekt musí inicializovat před použitím vytvořit objekt sady záznamů.  
  
 Pokud `lpszConnectString` parametr ve vaší `OpenEx` volání neobsahuje dostatek informací pro připojení, ovladač ODBC otevře dialogové okno se získat potřebné informace od uživatele, pokud jste nenastavili **CDatabase:: noOdbcDialog** nebo **CDatabase::forceOdbcDialog** v `dwOptions` parametr. Při volání `OpenEx`, připojovací řetězec, `lpszConnectString`, je uložen v soukromě `CDatabase` objektu a je k dispozici při volání [GetConnect](#getconnect) – členská funkce.  
  
 Pokud chcete, můžete otevřít dialogové okno Vlastní před voláním `OpenEx` k získání informací od uživatele, jako například heslo a poté přidejte tyto informace do připojovacího řetězce je předat do `OpenEx`. Nebo můžete chtít uložit připojovací řetězec, předáte tak můžete znovu použít, je další čas voláními aplikace `OpenEx` na `CDatabase` objektu.  
  
 Můžete také použít připojovací řetězec pro více úrovní ověřování přihlášení (jednotlivých jiné `CDatabase` objektu) nebo vyjádřit jiné informace specifické pro zdroj dat. Další informace o připojovacích řetězcích, naleznete v kapitole 6 v *referenční informace pro programátory ODBC*.  
  
 Je možné pro pokus o připojení k vypršení časového limitu, pokud například hostitel databázového systému nedostupný. Pokud se nezdaří pokus o připojení, `OpenEx` vyvolá `CDBException`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDatabase#11](../../mfc/codesnippet/cpp/cdatabase-class_7.cpp)]  
  
##  <a name="rollback"></a>CDatabase::Rollback  
 Volání této funkce člen změny provedené během transakce.  
  
```  
BOOL Rollback();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud transakce byla úspěšně obrácený; jinak 0. Pokud **vrácení zpět** volání selže, zdroj dat a transakce nejsou definovány stavy. Pokud **vrácení zpět** vrátí hodnotu 0, je nutné zkontrolovat, zdroj dat k určení stavu.  
  
### <a name="remarks"></a>Poznámky  
 Všechny `CRecordset` `AddNew`, **upravit**, **odstranit**, a **aktualizace** volání provést, protože poslední [metody BeginTrans](#begintrans) jsou vráceny zpátky do stavu, které existovalo v čase volání.  
  
 Po volání **vrácení zpět**transakce je nad a musí volat **metody BeginTrans** znovu pro jiné transakci. Záznam, který byl předtím, než jste volali metodu aktuální **metody BeginTrans** stane aktuálním záznamem znovu po **vrácení zpět**.  
  
 Po vrácení zpět zůstane aktuální záznam, který byl aktuální před vrácení zpět. Podrobnosti o stavu sady záznamů a zdroji dat po vrácení zpět, najdete v článku [transakce (ODBC)](../../data/odbc/transaction-odbc.md).  
  
### <a name="example"></a>Příklad  
  Najdete v článku [transakce: provádění transakcí v sadě záznamů (rozhraní ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).  
  
##  <a name="setlogintimeout"></a>CDatabase::SetLoginTimeout  
 Volání této funkce člen – před voláním `OpenEx` nebo **otevřete** – přepsat výchozí počet sekund, než pokus o data připojení ke zdroji časového limitu.  
  
```  
void SetLoginTimeout(DWORD dwSeconds);
```  
  
### <a name="parameters"></a>Parametry  
 `dwSeconds`  
 Počet sekund před pokus o připojení vyprší časový limit.  
  
### <a name="remarks"></a>Poznámky  
 Pokud například databázového systému není k dispozici, může pokus o připojení k vypršení časového limitu. Volání **SetLoginTimeout** po sestavení Neinicializovaný `CDatabase` objektu, ale před voláním `OpenEx` nebo **otevřete**.  
  
 Výchozí hodnota pro vypršení časových limitů přihlášení je 15 sekund. Ne všechny zdroje dat podporují možnost zadat hodnotu časového limitu přihlášení. Pokud zdroj dat nepodporuje časový limit, získáte výstup trasování, ale ne k výjimce. Hodnota 0 znamená "nekonečné."  
  
##  <a name="setquerytimeout"></a>CDatabase::SetQueryTimeout  
 Volání této funkce člena přepsat výchozí počet sekund před dalších operacích na připojené datový zdroj časový limit.  
  
```  
void SetQueryTimeout(DWORD dwSeconds);
```  
  
### <a name="parameters"></a>Parametry  
 `dwSeconds`  
 Počet sekund před pokusu o dotaz vyprší časový limit.  
  
### <a name="remarks"></a>Poznámky  
 Operace může vypršení časového limitu z důvodu problémy se síťovým přístupem, doba zpracování nadměrné dotazu a tak dále. Volání `SetQueryTimeout` před otevřením sady záznamů nebo před voláním sady záznamů `AddNew`, **aktualizace** nebo **odstranit** členské funkce, pokud chcete změnit hodnotu časového limitu dotazu. Toto nastavení ovlivňuje všechny následné **otevřete**, `AddNew`, **aktualizace**, a **odstranit** volání všechny sady záznamů přidružený k tomuto `CDatabase` objektu. Změna časový limit dotazu pro sadu záznamů po počáteční hodnotu pro sadu záznamů nezmění. Například následující **přesunout** operations nepoužívejte novou hodnotu.  
  
 Výchozí hodnota pro vypršení časových limitů dotazu je 15 sekund. Ne všechny zdroje dat podporují možnost nastavit hodnotu časového limitu dotazu. Pokud nastavíte hodnotu časového limitu dotazu 0, dojde k bez časového limitu; komunikace se zdroji dat, může přestat reagovat. Toto chování může být užitečné při vývoji. Pokud zdroj dat nepodporuje časový limit, získáte výstup trasování, ale ne k výjimce.  
  
## <a name="see-also"></a>Viz také  
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CRecordset – třída](../../mfc/reference/crecordset-class.md)
