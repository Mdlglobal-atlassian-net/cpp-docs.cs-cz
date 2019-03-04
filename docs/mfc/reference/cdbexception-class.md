---
title: CDBException – třída
ms.date: 11/04/2016
f1_keywords:
- CDBException
- AFXDB/CDBException
- AFXDB/CDBException::m_nRetCode
- AFXDB/CDBException::m_strError
- AFXDB/CDBException::m_strStateNativeOrigin
helpviewer_keywords:
- CDBException [MFC], m_nRetCode
- CDBException [MFC], m_strError
- CDBException [MFC], m_strStateNativeOrigin
ms.assetid: eb9e1119-89f5-49a7-b9d4-b91cee1ccc82
ms.openlocfilehash: e8a5195d4d2a3662d79d515c28dc66d1b0a27b24
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57295016"
---
# <a name="cdbexception-class"></a>CDBException – třída

Představuje podmínku výjimky vyplývající z databázových tříd.

## <a name="syntax"></a>Syntaxe

```
class CDBException : public CException
```

## <a name="members"></a>Členové

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CDBException::m_nRetCode](#m_nretcode)|Obsahuje návratový kód připojení ODBC (Open Database), typu RETCODE.|
|[CDBException::m_strError](#m_strerror)|Obsahuje řetězec popisující chybu v podmínkách alfanumerické znaky.|
|[CDBException::m_strStateNativeOrigin](#m_strstatenativeorigin)|Obsahuje řetězec popisující chybu, kterou z hlediska kódů chyb vrácených nástrojem ODBC.|

## <a name="remarks"></a>Poznámky

Třída zahrnuje dvě veřejné datové členy, která vám pomůže určit příčinu výjimky nebo zobrazení textová zpráva popisující výjimku. `CDBException` objekty jsou vytvořena a vyvolané členské funkce tříd databáze.

> [!NOTE]
>  Tato třída je jedním z třídy knihovny MFC připojení ODBC (Open Database). Pokud raději používáte novější třídy objektů DAO (Data Access), použijte [cdaoexception –](../../mfc/reference/cdaoexception-class.md) místo. Všechny názvy tříd DAO mají "CDao" jako předponu. Další informace najdete v článku [přehled: Databáze programování](../../data/data-access-programming-mfc-atl.md).

Výjimky jsou případy abnormální provádění zahrnující podmínek mimo řízení programu, jako je zdroj dat nebo vstupně-výstupní chyby sítě. Chyby, které by se dalo očekávat v běžném průběhu provádění programu nejsou obvykle považovány za výjimky.

Můžete přístup k těmto objektům v rámci oboru **CATCH** výrazu. Můžete také vyvolat `CDBException` objekty z vlastního kódu s využitím `AfxThrowDBException` globální funkce.

Další informace o zpracování výjimek v obecné, nebo o `CDBException` objekty, najdete v článcích [zpracování výjimek (MFC)](../../mfc/exception-handling-in-mfc.md) a [výjimky: Výjimky databáze](../../mfc/exceptions-database-exceptions.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cexception –](../../mfc/reference/cexception-class.md)

`CDBException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

##  <a name="m_nretcode"></a>  CDBException::m_nRetCode

Obsahuje kód chyby rozhraní ODBC typu RETCODE vrácená funkcí ODBC aplikace programovací rozhraní (API).

### <a name="remarks"></a>Poznámky

Tento typ obsahuje předponu SQL kódy definované rozhraní ODBC a předponou AFX_SQL kódy definované v rámci tříd databáze. Pro `CDBException`, tento člen bude obsahovat jeden z následujících hodnot:

- AFX_SQL_ERROR_API_CONFORMANCE ovladače pro `CDatabase::OpenEx` nebo `CDatabase::Open` volání není v souladu s vyžaduje úroveň dodržování standardu ODBC API 1 (SQL_OAC_LEVEL1).

- AFX_SQL_ERROR_CONNECT_FAIL připojení ke zdroji dat se nezdařilo. Předán s hodnotou NULL`CDatabase` ukazatel na váš konstruktoru sady záznamů a další pokus o vytvoření připojení na základě `GetDefaultConnect` se nezdařilo.

- AFX_SQL_ERROR_DATA_TRUNCATED požadovaná více dat, než jste zadali pro úložiště. Informace o zvýšení úložiště poskytnutá data pro `CString` nebo `CByteArray` datové typy najdete v článku `nMaxLength` argument pro [RFX_Text](record-field-exchange-functions.md#rfx_text) a [RFX_Binary –](record-field-exchange-functions.md#rfx_binary) v části "makra a Globals."

- Volání AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED A `CRecordset::Open` požaduje dynamická sada se nezdařilo. Dynamické sady nepodporuje ovladače.

- AFX_SQL_ERROR_EMPTY_COLUMN_LIST jste se pokusili otevřít tabulku (nebo jste zadali, nelze identifikovat jako volání procedury nebo **vyberte** příkaz), ale nejsou žádné sloupce označené ve volání funkce pole záznamu (RFX) systému exchange v vaše `DoFieldExchange` přepsat.

- AFX_SQL_ERROR_FIELD_SCHEMA_MISMATCH typu RFX fungovat ve vaší `DoFieldExchange` přepsání není kompatibilní s datovým typem sloupce v sadě záznamů.

- AFX_SQL_ERROR_ILLEGAL_MODE jste volali `CRecordset::Update` bez dříve volání `CRecordset::AddNew` nebo `CRecordset::Edit`.

- AFX_SQL_ERROR_LOCK_MODE_NOT_SUPPORTED vaši žádost o zámek záznamů pro aktualizaci nelze splnit, protože ovladač rozhraní ODBC není podporováno uzamčení.

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED, která jste volali `CRecordset::Update` nebo `Delete` pro tabulku s žádný jedinečný klíč a změnit více záznamů.

- AFX_SQL_ERROR_NO_CURRENT_RECORD jste se pokusili upravit nebo odstranit dřív odstraněný záznam. Po odstranění musí přejděte do nové aktuální záznam.

- AFX_SQL_ERROR_NO_POSITIONED_UPDATES, které vaši žádost o dynamická sada nelze splnit, protože ovladač rozhraní ODBC nepodporuje umístěné aktualizace.

- AFX_SQL_ERROR_NO_ROWS_AFFECTED jste volali `CRecordset::Update` nebo `Delete`, ale při zahájení operace již nelze najít záznam.

- AFX_SQL_ERROR_ODBC_LOAD_FAILED pokus o načtení rozhraní ODBC. Knihovna DLL se nezdařil. Windows nelze nalézt nebo nelze načíst tuto knihovnu DLL. Tato chyba je závažná.

- AFX_SQL_ERROR_ODBC_V2_REQUIRED, které vaši žádost o dynamická sada nelze splnit, protože se vyžaduje úrovně 2 kompatibilní ovladač ODBC.

- AFX_SQL_ERROR_RECORDSET_FORWARD_ONLY pokus posunout, aby nebyla úspěšná, protože zdroj dat nepodporuje zpětně posouvání.

- Volání AFX_SQL_ERROR_SNAPSHOT_NOT_SUPPORTED A `CRecordset::Open` požaduje snímku se nezdařilo. Snímky nepodporuje ovladače. (To by mělo nastat pouze při knihovna kurzorů rozhraní ODBC ODBCCURS. Knihovna DLL není k dispozici.)

- AFX_SQL_ERROR_SQL_CONFORMANCE ovladače pro `CDatabase::OpenEx` nebo `CDatabase::Open` volání není v souladu s požadovanou úroveň shody SQL ODBC "Minimální" (SQL_OSC_MINIMUM).

- Ovladač ODBC AFX_SQL_ERROR_SQL_NO_TOTAL nebyl schopen určit celkovou velikost `CLongBinary` datovou hodnotu. Operace se nezdařila, pravděpodobně protože nebylo možné předpřidělené blok globální paměti.

- AFX_SQL_ERROR_RECORDSET_READONLY jste se pokusili aktualizovat sadu záznamů jen pro čtení, nebo zdroj dat je jen pro čtení. Žádné operace aktualizace, můžete to provést pomocí sady záznamů nebo `CDatabase` objekt je přidružený.

- SQL_ERROR Function se nezdařil. Chybová zpráva vrácená funkcí ODBC `SQLError` je uložen v `m_strError` datový člen.

- Funkce SQL_INVALID_HANDLE se nezdařila kvůli neplatné prostředí popisovač, popisovače připojení nebo popisovač příkazu. To znamená o programovou chybu. Žádné další informace jsou k dispozici z funkce ODBC `SQLError`.

Kódy s předponou SQL jsou definovány ODBC. Afx – předponou kódy jsou definovány v AFXDB. H, součástí MFC\INCLUDE.

##  <a name="m_strerror"></a>  CDBException::m_strError

Obsahuje řetězec popisující chybu, která způsobila výjimku.

### <a name="remarks"></a>Poznámky

Řetězec popisuje chybu v podmínkách alfanumerické znaky. Podrobnější informace a příklad najdete v článku `m_strStateNativeOrigin`.

##  <a name="m_strstatenativeorigin"></a>  CDBException::m_strStateNativeOrigin

Obsahuje řetězec popisující chybu, která způsobila výjimku.

### <a name="remarks"></a>Poznámky

Řetězec je formuláře "stav: % s, nativní: % ld původu: % s", kde jsou kódy v pořadí, nahrazena hodnot, které popisují:

- SQLSTATE, řetězec zakončený hodnotou null obsahující kód pěti chyby vrácené v *szSqlState* parametr funkce ODBC `SQLError`. SQLSTATE hodnoty jsou uvedené v dodatku A [kódy chyb rozhraní ODBC](/previous-versions/windows/desktop/ms714687)v *ODBC programátora*. Příklad: "S0022".

- Kód nativní chyby specifické pro zdroj dat se vrátil v *pfNativeError* parametr `SQLError` funkce. Příklad: 207.

- Text chybové zprávy vrácené v *szErrorMsg* parametr `SQLError` funkce. Tato zpráva se skládá z několika názvy v závorkách. Jako chybu je úspěšný z jeho zdroje pro uživatele, jednotlivé komponenty rozhraní ODBC (zdroj dat, ovladače, správce ovladačů) přidá svůj vlastní název. Tyto informace pomáhají určit původ chyby. Příklad: [Microsoft] [ovladač ODBC SQL Server] [SQL Server]

Rozhraní framework interpretuje řetězec chyby a vloží do jeho komponenty `m_strStateNativeOrigin`; Pokud `m_strStateNativeOrigin` obsahuje informace o více než jednu chybu, chyby jsou odděleny tabulátorů. Vloží text alfanumerické chyby do rozhraní framework `m_strError`.

Další informace o kódech použité k vytvoření tohoto řetězce najdete v tématu [SQLError](/previous-versions/windows/desktop/ms716312) fungovat v *ODBC programátora*.

### <a name="example"></a>Příklad

  Z rozhraní ODBC: "Stav: S0022, nativní: 207, původu: [Microsoft] [SQL Server ovladače ODBC] [SQL Server] neplatný název sloupce '%{colname/."

V `m_strStateNativeOrigin`: "Stav: S0022, nativní: 207, původu: [Microsoft] [ovladač ODBC SQL Server] [SQL Server]"

V `m_strError`: "Neplatný název sloupce '%{colname/."

## <a name="see-also"></a>Viz také:

[CException – třída](../../mfc/reference/cexception-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDatabase – třída](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange – třída](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset::Update](../../mfc/reference/crecordset-class.md#update)<br/>
[CRecordset::Delete](../../mfc/reference/crecordset-class.md#delete)<br/>
[CException – třída](../../mfc/reference/cexception-class.md)
