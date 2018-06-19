---
title: Třída CDBException | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDBException
- AFXDB/CDBException
- AFXDB/CDBException::m_nRetCode
- AFXDB/CDBException::m_strError
- AFXDB/CDBException::m_strStateNativeOrigin
dev_langs:
- C++
helpviewer_keywords:
- CDBException [MFC], m_nRetCode
- CDBException [MFC], m_strError
- CDBException [MFC], m_strStateNativeOrigin
ms.assetid: eb9e1119-89f5-49a7-b9d4-b91cee1ccc82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 824ac88326042eb55ecb9667c39331d1ab5464e7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33368332"
---
# <a name="cdbexception-class"></a>CDBException – třída
Představuje podmínku vzniklých databázové třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDBException : public CException  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CDBException::m_nRetCode](#m_nretcode)|Obsahuje návratový kód připojení ODBC (Open Database), typu **RETCODE**.|  
|[CDBException::m_strError](#m_strerror)|Obsahuje řetězec, který popisuje danou chybu v alfanumerické podmínky.|  
|[CDBException::m_strStateNativeOrigin](#m_strstatenativeorigin)|Obsahuje řetězec popisující chyby z hlediska kódů chyb vrácených nástrojem ODBC.|  
  
## <a name="remarks"></a>Poznámky  
 Třída obsahuje dva členy veřejná data, které můžete použít a zjistěte příčinu výjimky nebo zobrazíte textovou zprávu s popisem výjimky. `CDBException` objekty jsou vytvořená a vyvolané členské funkce tříd databáze.  
  
> [!NOTE]
>  Tato třída je jedním z třídy knihovny MFC připojení ODBC (Open Database). Pokud místo toho používáte novější třídy objektů DAO (Data Access), použijte [CDaoException](../../mfc/reference/cdaoexception-class.md) místo. Všechny názvy tříd DAO mít jako předponu "CDao". Další informace najdete v článku [přehled: programování databáze](../../data/data-access-programming-mfc-atl.md).  
  
 Výjimky jsou případech abnormální provádění zahrnující podmínky mimo řízení programu, jako je například zdroj dat nebo vstupně-výstupní chyby sítě. Chyby, které by se dalo očekávat zobrazíte v běžném průběhu provádění vašeho programu nejsou obvykle považovány za výjimky.  
  
 Dostanete tyto objekty v rámci oboru **CATCH** výraz. Můžete také vyvolat `CDBException` objekty z vlastního kódu pomocí `AfxThrowDBException` globální funkce.  
  
 Další informace o zpracování výjimek v obecné nebo o `CDBException` objekty, najdete v článcích [zpracování výjimek (MFC)](../../mfc/exception-handling-in-mfc.md) a [výjimky: výjimky databáze](../../mfc/exceptions-database-exceptions.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CDBException`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdb.h  
  
##  <a name="m_nretcode"></a>  CDBException::m_nRetCode  
 Obsahuje kód chyby rozhraní ODBC typu **RETCODE** vrácený aplikace rozhraní ODBC programovací rozhraní (API), funkce.  
  
### <a name="remarks"></a>Poznámky  
 Tento typ obsahuje předponu SQL kódy definované rozhraní ODBC a předponu AFX_SQL kódy definované databázové třídy. Pro `CDBException`, tento člen bude obsahovat jeden z následujících hodnot:  
  
- **AFX_SQL_ERROR_API_CONFORMANCE** ovladač `CDatabase::OpenEx` nebo `CDatabase::Open` volání neodpovídá požadované úrovni shoda rozhraní API ODBC 1 ( **SQL_OAC_LEVEL1**).  
  
- **AFX_SQL_ERROR_CONNECT_FAIL** připojení ke zdroji dat se nezdařilo. Je předán **NULL** `CDatabase` ukazatel na vaše konstruktor sady záznamů a další pokus o vytvoření připojení na základě `GetDefaultConnect` se nezdařilo.  
  
- **AFX_SQL_ERROR_DATA_TRUNCATED** požadujete víc dat, než jste zadali pro úložiště. Informace o zvýšení úložiště zadaná data pro `CString` nebo `CByteArray` datové typy, najdete v článku `nMaxLength` argument pro [RFX_Text](record-field-exchange-functions.md#rfx_text) a [RFX_Binary –](record-field-exchange-functions.md#rfx_binary) v části "makra a Globals."  
  
- **AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED** volání `CRecordset::Open` požaduje dynamická sada se nezdařilo. Ovladač nepodporuje dynamické sady.  
  
- **AFX_SQL_ERROR_EMPTY_COLUMN_LIST** jste se pokusili otevřít tabulku (nebo jste zadali, nebylo možné identifikovat jako volání procedury nebo **vyberte** příkaz), ale neexistují žádné sloupce určené v výměna pole záznamu (RFX) volání funkce do vaší `DoFieldExchange` přepsat.  
  
- **AFX_SQL_ERROR_FIELD_SCHEMA_MISMATCH** typ funkce RFX ve vaší `DoFieldExchange` přepsání není kompatibilní s datový typ sloupce v sadě záznamů.  
  
- **AFX_SQL_ERROR_ILLEGAL_MODE** můžete volat `CRecordset::Update` bez dříve volání `CRecordset::AddNew` nebo `CRecordset::Edit`.  
  
- **AFX_SQL_ERROR_LOCK_MODE_NOT_SUPPORTED** váš požadavek na uzamčení záznamů pro aktualizaci nelze splnit, protože ovladač ODBC nepodporuje uzamčení.  
  
- **AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED, která** můžete volat `CRecordset::Update` nebo **odstranit** pro tabulku bez jedinečné klíče a změnit více záznamů.  
  
- **AFX_SQL_ERROR_NO_CURRENT_RECORD** jste se pokusili získat upravit nebo odstranit záznam dříve odstraněné. Po odstranění se musí přejděte na nový aktuální záznam.  
  
- **AFX_SQL_ERROR_NO_POSITIONED_UPDATES** vaši žádost pro dynamická sada nelze splnit, protože vaše ovladač ODBC nepodporuje umístěné aktualizace.  
  
- **AFX_SQL_ERROR_NO_ROWS_AFFECTED** můžete volat `CRecordset::Update` nebo **odstranit**, ale když operaci zahájil záznamu může již nelze nalézt.  
  
- **AFX_SQL_ERROR_ODBC_LOAD_FAILED** pokus o načtení ODBC. Knihovny DLL se nezdařilo; Windows nelze najít, nebo nelze načíst tuto knihovnu DLL. Tato chyba je závažná.  
  
- **AFX_SQL_ERROR_ODBC_V2_REQUIRED** vaši žádost o dynamická sada nelze splnit, protože je vyžadován úrovně 2kompatibilní ovladač ODBC.  
  
- **AFX_SQL_ERROR_RECORDSET_FORWARD_ONLY** pokus o přechod nebyla úspěšná, protože zdroj dat nepodporuje zpětné posouvání.  
  
- **AFX_SQL_ERROR_SNAPSHOT_NOT_SUPPORTED** volání `CRecordset::Open` požaduje snímku se nezdařilo. Snímky nepodporuje ovladač. (To by měl použít pouze v případě knihovny kurzorů ODBC ODBCCURS. Knihovny DLL se nenachází.)  
  
- **AFX_SQL_ERROR_SQL_CONFORMANCE** ovladač `CDatabase::OpenEx` nebo `CDatabase::Open` volání neodpovídá požadované úrovni ODBC SQL shoda "Minimální" ( **SQL_OSC_MINIMUM**).  
  
- **AFX_SQL_ERROR_SQL_NO_TOTAL** ovladač ODBC se nepodařilo určit celková velikost `CLongBinary` hodnotu data. Operace se pravděpodobně selhala, protože nelze souhrnů ještě neumístěných blok globální paměť.  
  
- **AFX_SQL_ERROR_RECORDSET_READONLY** jste se pokusili aktualizovat sadu záznamů jen pro čtení, nebo zdroj dat je jen pro čtení. Sady záznamů lze provést žádné operace aktualizace nebo `CDatabase` objekt je přidružený.  
  
- **SQL_ERROR** funkce se nezdařilo. Chybová zpráva vrácená funkcí rozhraní ODBC **funkce SQLError** je uložen v **m_strError** – datový člen.  
  
- **SQL_INVALID_HANDLE** funkce došlo prostředí neplatný popisovač, popisovač připojení nebo popisovač příkazu. To znamená chybě programování. Žádné další informace jsou k dispozici z funkce ODBC **funkce SQLError**.  
  
 Kódy předponu SQL jsou definovány ODBC. Afx – předponu kódy jsou definovány v AFXDB. H v MFC\INCLUDE nalezen.  
  
##  <a name="m_strerror"></a>  CDBException::m_strError  
 Obsahuje řetězec popisující chybu, která způsobila výjimku.  
  
### <a name="remarks"></a>Poznámky  
 Řetězec popisuje chybu v alfanumerické podmínky. Podrobnější informace a příklad najdete v článku **m_strStateNativeOrigin**.  
  
##  <a name="m_strstatenativeorigin"></a>  CDBException::m_strStateNativeOrigin  
 Obsahuje řetězec popisující chybu, která způsobila výjimku.  
  
### <a name="remarks"></a>Poznámky  
 Řetězec je je formulář "stav: % s, nativní: % ld původu: % s", kde jsou kódy formát, v pořadí, nahrazují hodnoty, které popisují:  
  
-   **SQLSTATE**, s kódem chyby pěti znacích, vrátí se v řetězce ukončené hodnotou null *szSqlState* parametr funkce ODBC **funkce SQLError**. **SQLSTATE** hodnoty jsou uvedené v dodatku A, [kódy chyb ODBC](https://msdn.microsoft.com/library/ms714687.aspx)v *referenční informace pro programátory ODBC*. Příklad: "S0022".  
  
-   Vrácený kód chyby nativní, specifické pro zdroj dat v *pfNativeError* parametr **funkce SQLError** funkce. Příklad: 207.  
  
-   Vrátí text chybové zprávy *szErrorMsg* parametr **funkce SQLError** funkce. Tato zpráva se skládá z několika názvů v závorkách. Jako chybu je předaný z její zdroj pro uživatele, jednotlivých součástí rozhraní ODBC (zdroj dat, ovladače, správce ovladačů) připojí svůj vlastní název. Tyto informace pomáhají ke kotvícímu bodu počátek chyby. Příklad: [Microsoft] [ovladač ODBC SQL Server] [SQL Server]  
  
 Rozhraní framework interpretuje řetězec chyby a vloží jeho součástí do **m_strStateNativeOrigin**; Pokud **m_strStateNativeOrigin** obsahuje informace pro více než jednu chybu, jsou odděleny chyby Vložení znaků newline. Rozhraní framework vloží text alfanumerické chyby do **m_strError**.  
  
 Další informace o kódech použité k vytvoření tohoto řetězce najdete v tématu [funkce SQLError](https://msdn.microsoft.com/library/ms716312.aspx) v fungovat *referenční informace pro programátory ODBC*.  
  
### <a name="example"></a>Příklad  
  Z rozhraní ODBC: "Stavu: S0022, nativní: 207, původu: [Microsoft] [ovladač ODBC SQL Server] [SQL Server] neplatný název sloupce"ColName. "  
  
 V **m_strStateNativeOrigin**: "stavu: S0022, nativní: 207, původu: [Microsoft] [ovladač ODBC SQL Server] [SQL Server]"  
  
 V **m_strError**: "Neplatný název sloupce"ColName."  
  
## <a name="see-also"></a>Viz také  
 [CException – třída](../../mfc/reference/cexception-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CDatabase – třída](../../mfc/reference/cdatabase-class.md)   
 [CRecordset – třída](../../mfc/reference/crecordset-class.md)   
 [CFieldExchange – třída](../../mfc/reference/cfieldexchange-class.md)   
 [CRecordset::Update](../../mfc/reference/crecordset-class.md#update)   
 [CRecordset::Delete](../../mfc/reference/crecordset-class.md#delete)   
 [CException – třída](../../mfc/reference/cexception-class.md)
