---
title: Třída CDBException
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
ms.openlocfilehash: 1ab7daeb3af55c92985c951c632b1d4050681474
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321895"
---
# <a name="cdbexception-class"></a>Třída CDBException

Představuje podmínku výjimky vyplývající z tříd y databáze.

## <a name="syntax"></a>Syntaxe

```
class CDBException : public CException
```

## <a name="members"></a>Členové

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[VÝJIMKA CDB::m_nRetCode](#m_nretcode)|Obsahuje návratový kód připojení otevřené databáze (ODBC) typu RETCODE.|
|[VÝJIMKA CDB::m_strError](#m_strerror)|Obsahuje řetězec, který popisuje chybu v alfanumerických termínech.|
|[VÝJIMKA CDB::m_strStateNativeOrigin](#m_strstatenativeorigin)|Obsahuje řetězec popisující chybu z hlediska kódů chyb vrácených rozhraním ODBC.|

## <a name="remarks"></a>Poznámky

Třída obsahuje dva členy veřejných dat, které můžete použít k určení příčiny výjimky nebo k zobrazení textové zprávy popisující výjimku. `CDBException`objekty jsou konstruovány a vyvolány členské funkce tříd y databáze.

> [!NOTE]
> Tato třída je jednou z tříd připojení otevřené databáze knihovny MFC (ODBC). Pokud místo toho používáte novější třídy objektů přístupu k datům (DAO), použijte místo toho [výjimku CDaoException.](../../mfc/reference/cdaoexception-class.md) Všechny názvy tříd DAO mají jako předponu "CDao". Další informace naleznete v článku [Přehled: Programování databáze](../../data/data-access-programming-mfc-atl.md).

Výjimkou jsou případy abnormálního spuštění zahrnujícípodmínky mimo ovládací prvek programu, jako jsou například chyby zdroje dat nebo vstupně-videa sítě. Chyby, které můžete očekávat, že se zobrazí v normálním průběhu provádění programu, se obvykle nepovažují za výjimky.

K těmto objektům můžete přistupovat v rámci výrazu **CATCH.** Můžete také `CDBException` vyvolat objekty z `AfxThrowDBException` vlastního kódu s globální funkcí.

Další informace o zpracování výjimek `CDBException` obecně nebo o objektech naleznete v článcích [Zpracování výjimek (MFC)](../../mfc/exception-handling-in-mfc.md) a [Výjimky: Výjimky databáze](../../mfc/exceptions-database-exceptions.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CDBException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="cdbexceptionm_nretcode"></a><a name="m_nretcode"></a>VÝJIMKA CDB::m_nRetCode

Obsahuje kód chyby ODBC typu RETCODE vrácený funkcí API (Application Programming Interface) rozhraní ODBC.

### <a name="remarks"></a>Poznámky

Tento typ obsahuje kódy s předponou SQL definované kódy ODBC a AFX_SQL kódy s předponou definované třídami databáze. Pro `CDBException`, tento člen bude obsahovat jednu z následujících hodnot:

- AFX_SQL_ERROR_API_CONFORMANCE Ovladač `CDatabase::OpenEx` nebo `CDatabase::Open` volání neodpovídá požadované úrovni shody rozhraní ODBC API 1 (SQL_OAC_LEVEL1).

- AFX_SQL_ERROR_CONNECT_FAIL Připojení ke zdroji dat se nezdařilo. Předali jste`CDatabase` konstruktoru sady záznamů null a následný pokus `GetDefaultConnect` o vytvoření připojení na základě selhání.

- AFX_SQL_ERROR_DATA_TRUNCATED Požadujete více dat, než jste poskytli úložiště. Informace o zvýšení poskytovaného úložiště `CString` `CByteArray` dat nebo datových typů naleznete v argumentu `nMaxLength` pro [RFX_Text](record-field-exchange-functions.md#rfx_text) a [RFX_Binary](record-field-exchange-functions.md#rfx_binary) v části Makra a globální data.

- AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED Volání `CRecordset::Open` žádosti o dynaset se nezdařilo. Dynasady nejsou podporovány ovladačem.

- AFX_SQL_ERROR_EMPTY_COLUMN_LIST Pokusili jste se otevřít tabulku (nebo co jste dal nelze identifikovat jako volání procedury nebo **SELECT** prohlášení), ale nejsou `DoFieldExchange` k dispozici žádné sloupce identifikované v záznamu pole exchange (RFX) volání funkce v přepsání.

- AFX_SQL_ERROR_FIELD_SCHEMA_MISMATCH Typ funkce RFX v `DoFieldExchange` přepsání není kompatibilní s datovým typem sloupce v sadě záznamů.

- AFX_SQL_ERROR_ILLEGAL_MODE Volali `CRecordset::Update` jste `CRecordset::AddNew` `CRecordset::Edit`bez předchozího volání nebo .

- AFX_SQL_ERROR_LOCK_MODE_NOT_SUPPORTED Požadavek na uzamčení záznamů pro aktualizaci nemohl být splněn, protože ovladač ROZHRANÍ ODBC nepodporuje uzamčení.

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED `CRecordset::Update` Volali `Delete` jste nebo pro tabulku bez jedinečného klíče a změnili více záznamů.

- AFX_SQL_ERROR_NO_CURRENT_RECORD Pokusili jste se upravit nebo odstranit dříve odstraněný záznam. Po odstranění je nutné přejít na nový aktuální záznam.

- AFX_SQL_ERROR_NO_POSITIONED_UPDATES Požadavek na sadu dynase nelze splnit, protože ovladač ROZHRANÍ ODBC nepodporuje aktualizace umístění.

- AFX_SQL_ERROR_NO_ROWS_AFFECTED Jste `CRecordset::Update` `Delete`zavolali nebo , ale při zahájení operace již nebyl záznam nalezen.

- AFX_SQL_ERROR_ODBC_LOAD_FAILED Pokus o načtení rozhraní ODBC. DLL se nezdařilo. Systém Windows nemohl najít nebo nemohl načíst tuto dll. Tato chyba je závažná.

- AFX_SQL_ERROR_ODBC_V2_REQUIRED Požadavek na sadu dynase nelze splnit, protože je vyžadován ovladač ROZHRANÍ ODBC kompatibilní s úrovní 2.

- AFX_SQL_ERROR_RECORDSET_FORWARD_ONLY Pokus o posouvání nebyl úspěšný, protože zdroj dat nepodporuje zpětné posouvání.

- AFX_SQL_ERROR_SNAPSHOT_NOT_SUPPORTED Volání `CRecordset::Open` požadující snímek se nezdařilo. Snímky nejsou podporovány ovladačem. (K tomu by mělo dojít pouze v případě, že knihovna kurzorů ODBC ODBCCURS. DLL není k dispozici.)

- AFX_SQL_ERROR_SQL_CONFORMANCE Ovladač `CDatabase::OpenEx` nebo `CDatabase::Open` volání neodpovídá požadované úrovni shody ODBC SQL "Minimum" (SQL_OSC_MINIMUM).

- AFX_SQL_ERROR_SQL_NO_TOTAL Ovladač ODBC nemohl určit celkovou `CLongBinary` velikost datové hodnoty. Operace pravděpodobně selhala, protože globální blok paměti nelze předanou.

- AFX_SQL_ERROR_RECORDSET_READONLY Pokusili jste se aktualizovat sadu záznamů jen pro čtení nebo je zdroj dat jen pro čtení. Se sadou záznamů nebo objektem, `CDatabase` ke kterým je přidružena, nelze provádět žádné operace aktualizace.

- funkce SQL_ERROR se nezdařila. Chybová zpráva vrácená funkcí `SQLError` ODBC `m_strError` je uložena v datovém členu.

- SQL_INVALID_HANDLE funkce se nezdařila z důvodu neplatného popisovače prostředí, popisovače připojení nebo popisovače příkazu. To znamená chybu programování. Funkce ODBC není k dispozici `SQLError`žádné další informace .

Kódy s předponou SQL jsou definovány rozhraním ODBC. Kódy s předponou AFX jsou definovány v AFXDB. H, nalezen v knihovně MFC\INCLUDE.

## <a name="cdbexceptionm_strerror"></a><a name="m_strerror"></a>VÝJIMKA CDB::m_strError

Obsahuje řetězec popisující chybu, která způsobila výjimku.

### <a name="remarks"></a>Poznámky

Řetězec popisuje chybu v alfanumerických termínech. Podrobnější informace a příklad naleznete `m_strStateNativeOrigin`v tématu .

## <a name="cdbexceptionm_strstatenativeorigin"></a><a name="m_strstatenativeorigin"></a>VÝJIMKA CDB::m_strStateNativeOrigin

Obsahuje řetězec popisující chybu, která způsobila výjimku.

### <a name="remarks"></a>Poznámky

Řetězec je ve tvaru "State:%s,Native:%ld,Origin:%s", kde jsou formátové kódy v pořadí nahrazeny hodnotami, které popisují:

- SQLSTATE, řetězec ukončený nulou obsahující pětimístný kód chyby vrácený v parametru `SQLError` *szSqlState* funkce ODBC . Hodnoty SQLSTATE jsou uvedeny v dodatku A, [ODBC Chybové kódy](/sql/odbc/reference/appendixes/appendix-a-odbc-error-codes), v *odkazu programátora ODBC*. Příklad: "S0022".

- Nativní kód chyby, specifický pro zdroj dat, vrácený `SQLError` v parametru *pfNativeError* funkce. Příklad: 207.

- Text chybové zprávy vrácený v parametru *szErrorMsg* `SQLError` funkce. Tato zpráva se skládá z několika názvů v závorkách. Jako chyba je předána z jeho zdroje uživateli, každá komponenta ODBC (zdroj dat, ovladač, Správce ovladačů) připojí svůj vlastní název. Tyto informace pomáhají určit původ chyby. Příklad: [Microsoft][ODBC SQL Server Driver][SQL Server]

Rozhraní framework interpretuje chybový řetězec `m_strStateNativeOrigin`a vloží jeho součásti do ; pokud `m_strStateNativeOrigin` obsahuje informace pro více než jednu chybu, jsou chyby odděleny novými řádky. Rozhraní framework umístí text alfanumerické chyby do `m_strError`aplikace .

Další informace o kódech použitých k seřizování tohoto řetězce naleznete ve funkci [SQLError](/sql/odbc/reference/syntax/sqlerror-function) v *odkazu programátora ODBC*.

### <a name="example"></a>Příklad

Z rozhraní ODBC: "State:S0022,Native:207,Origin:\[Microsoft]\[\[ODBC SQL Server Driver] SQL Server] SQL Server] Neplatný název sloupce "ColName".

V `m_strStateNativeOrigin`:\["State:S0022,Native:207,Origin:\[Microsoft] ODBC\[SQL Server Driver] SQL Server]"

V `m_strError`: "Neplatný název sloupce 'ColName'"

## <a name="see-also"></a>Viz také

[CException – třída](../../mfc/reference/cexception-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDatabase – třída](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange – třída](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset::Aktualizovat](../../mfc/reference/crecordset-class.md#update)<br/>
[CRecordset::Delete](../../mfc/reference/crecordset-class.md#delete)<br/>
[CException – třída](../../mfc/reference/cexception-class.md)
