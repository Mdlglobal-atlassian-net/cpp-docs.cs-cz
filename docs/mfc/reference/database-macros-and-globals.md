---
title: Databázová makra a globální prvky
ms.date: 11/04/2016
f1_keywords:
- AFXDB/AFX_ODBC_CALL
- AFXDB/AFX_SQL_ASYNC
- AFXDB/AFX_SQL_SYNC
- AFXDB/AfxGetHENV
helpviewer_keywords:
- global database functions [MFC]
- database macros [MFC]
- database globals [MFC]
- global functions [MFC], database functions
- macros [MFC], MFC database
ms.assetid: 5b9b9e61-1cf9-4345-9f29-3807dd466488
ms.openlocfilehash: 6d8bd56c0bfe4f9b35e34d067dd1042ed11066d5
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751668"
---
# <a name="database-macros-and-globals"></a>Databázová makra a globální prvky

Níže uvedená makra a globální soubory platí pro databázové aplikace založené na rozhraní ODBC. Nepoužívají se s aplikacemi založenými na DAO.

Před knihovnou MFC 4.2 poskytla makra `AFX_SQL_ASYNC` a `AFX_SQL_SYNC` asynchronní operace příležitost získat čas jiným procesům. Počínaje knihovnou MFC 4.2 se implementace těchto maker změnila, protože třídy Rozhraní MFC ODBC používaly pouze synchronní operace. Makro `AFX_ODBC_CALL` bylo pro knihovnu MFC 4.2 nové.

### <a name="database-macros"></a>Makra databáze

|||
|-|-|
|[AFX_ODBC_CALL](#afx_odbc_call)|Volá funkci rozhraní API `SQL_STILL_EXECUTING`ROZHRANÍ ODBC, která vrací . `AFX_ODBC_CALL`opakovaně volá funkci, dokud se `SQL_STILL_EXECUTING`již nevrátí .|
|[AFX_SQL_ASYNC](#afx_sql_async)|Volání `AFX_ODBC_CALL`.|
|[AFX_SQL_SYNC](#afx_sql_sync)|Volá funkci rozhraní API ROZHRANÍ `SQL_STILL_EXECUTING`ODBC, která se nevrátí .|

### <a name="database-globals"></a>Globální databáze

|||
|-|-|
|[Modul AfxDbInit](#afxdbinitmodule)|Přidá podporu databáze pro běžnou knihovnu DLL knihovny MFC, která je dynamicky propojena s knihovnou MFC.|
|[AfxGetHENV](#afxgethenv)|Načte popisovač do prostředí ROZHRANÍ ODBC aktuálně používá knihovna MFC. Tento popisovač můžete použít v přímých voláních ROZHRANÍ ODBC.|

## <a name="afxdbinitmodule"></a><a name="afxdbinitmodule"></a>Modul AfxDbInit

Pro podporu databáze Knihovny MFC (nebo DAO) z běžné knihovny DLL knihovny MFC, která je dynamicky propojena s knihovnou MFC, přidejte volání této funkce v běžné funkci knihovny `CWinApp::InitInstance` MFC DLL pro inicializaci knihovny DLL databáze knihovny MFC.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI AfxDbInitModule( );
```

### <a name="remarks"></a>Poznámky

Ujistěte se, že k tomuto volání dojde před voláním základní třídy nebo libovolným přidaným kódem, který přistupuje k knihovně DLL databáze knihovny MFC. Knihovna DLL databáze knihovny MFC je knihovna DLL rozšíření knihovny MFC. V pořadí pro rozšíření knihovny MFC `CDynLinkLibrary` DLL získat kabelové `CDynLinkLibrary` do řetězce, musí vytvořit objekt v kontextu každého modulu, který bude používat. `AfxDbInitModule`vytvoří `CDynLinkLibrary` objekt v kontextu běžné knihovny MFC DLL tak, aby se dostal do řetězce `CDynLinkLibrary` objektů běžné knihovny MFC DLL.

### <a name="requirements"></a>Požadavky

**Záhlaví:** \<afxdll_.h>

## <a name="afx_odbc_call"></a><a name="afx_odbc_call"></a>AFX_ODBC_CALL

Toto makro slouží k volání libovolné `SQL_STILL_EXECUTING`funkce rozhraní API ROZHRANÍ ODBC, která může vrátit .

```
AFX_ODBC_CALL(SQLFunc)
```

### <a name="parameters"></a>Parametry

*SQLFunc*<br/>
Funkce ROZHRANÍ API ROZHRANÍ ODBC. Další informace o funkcích rozhraní API rozhraní ODBC naleznete v části Sada Windows SDK.

### <a name="remarks"></a>Poznámky

`AFX_ODBC_CALL`opakovaně volá funkci, dokud se `SQL_STILL_EXECUTING`již nevrátí .

Před vyvoláním `AFX_ODBC_CALL`je nutné deklarovat proměnnou `nRetCode`typu RETCODE.

Všimněte si, že třídy Rozhraní MFC ODBC nyní používají pouze synchronní zpracování. Chcete-li provést asynchronní operaci, musíte volat funkci `SQLSetConnectOption`ROZHRANÍ API ROZHRANÍ ODBC . Další informace naleznete v tématu "Provádění funkcí asynchronně" v sadě Windows SDK.

### <a name="example"></a>Příklad

Tento příklad `AFX_ODBC_CALL` používá `SQLColumns` k volání funkce ROZHRANÍ API ROZHRANÍ ODBC, která `strTableName`vrací seznam sloupců v tabulce s názvem . Všimněte si `nRetCode` deklarace a použití datových členů sady záznamů k předání parametrů funkci. Příklad také znázorňuje kontrolu výsledků volání `Check`s , členské `CRecordset`funkce třídy . Proměnná `prs` je ukazatel `CRecordset` na objekt, deklarovaný jinde.

[!code-cpp[NVC_MFCDatabase#39](../../mfc/codesnippet/cpp/database-macros-and-globals_1.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="afx_sql_async"></a><a name="afx_sql_async"></a>AFX_SQL_ASYNC

Implementace tohoto makra se změnila v knihovně MFC 4.2.

```
AFX_SQL_ASYNC(prs, SQLFunc)
```

### <a name="parameters"></a>Parametry

*prs*<br/>
Ukazatel na `CRecordset` objekt nebo `CDatabase` objekt. Počínaje mfc 4.2, tato hodnota parametru je ignorována.

*SQLFunc*<br/>
Funkce ROZHRANÍ API ROZHRANÍ ODBC. Další informace o funkcích rozhraní API rozhraní ODBC naleznete v části Sada Windows SDK.

### <a name="remarks"></a>Poznámky

`AFX_SQL_ASYNC`jednoduše zavolá makro [AFX_ODBC_CALL](#afx_odbc_call) a ignoruje parametr *prs.* Ve verzích knihovny MFC před `AFX_SQL_ASYNC` verzí 4.2 byl použit `SQL_STILL_EXECUTING`k volání funkcí rozhraní API ROZHRANÍ ODBC, které se mohou vrátit . Pokud se funkce rozhraní `SQL_STILL_EXECUTING`API `AFX_SQL_ASYNC` ROZHRANÍ `prs->OnWaitForDataSource`ODBC vrátila , pak by volala .

> [!NOTE]
> Třídy Rozhraní MFC ODBC nyní používají pouze synchronní zpracování. Chcete-li provést asynchronní operaci, musíte volat funkci `SQLSetConnectOption`ROZHRANÍ API ROZHRANÍ ODBC . Další informace naleznete v tématu "Provádění funkcí asynchronně" v sadě Windows SDK.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdb.h

## <a name="afx_sql_sync"></a><a name="afx_sql_sync"></a>AFX_SQL_SYNC

Makro `AFX_SQL_SYNC` jednoduše volá `SQLFunc`funkci .

```
AFX_SQL_SYNC(SQLFunc)
```

### <a name="parameters"></a>Parametry

*SQLFunc*<br/>
Funkce ROZHRANÍ API ROZHRANÍ ODBC. Další informace o těchto funkcích naleznete v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Toto makro slouží k volání funkcí `SQL_STILL_EXECUTING`rozhraní API ROZHRANÍ ODBC, které se nevrátí .

Před `AFX_SQL_SYNC`voláním je nutné `nRetCode`deklarovat proměnnou typu RETCODE. Můžete zkontrolovat hodnotu `nRetCode` po volání makra.

Všimněte si, `AFX_SQL_SYNC` že implementace změněna v knihovně MFC 4.2. Vzhledem k tomu, že kontrola `AFX_SQL_SYNC` stavu serveru již `nRetCode`nebyla vyžadována, jednoduše přiřadí hodnotu společnosti . Například místo volání

[!code-cpp[NVC_MFCDatabase#40](../../mfc/codesnippet/cpp/database-macros-and-globals_2.cpp)]

můžete jednoduše provést zadání

[!code-cpp[NVC_MFCDatabase#41](../../mfc/codesnippet/cpp/database-macros-and-globals_3.cpp)]

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdb.h

## <a name="afxgethenv"></a><a name="afxgethenv"></a>AfxGetHENV

Vrácený popisovač můžete použít v přímé masce ODBC, ale nesmíte zavřít popisovač `CDatabase`nebo `CRecordset`předpokládat, že popisovač je stále platný a dostupný po zničení všech existujících nebo odvozených objektů.

```
HENV AFXAPI AfxGetHENV();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač prostředí ROZHRANÍ ODBC aktuálně používán knihovnou MFC. Může `SQL_HENV_NULL` být, pokud neexistují žádné [cdatabase](../../mfc/reference/cdatabase-class.md) objekty a žádné [CRecordset](../../mfc/reference/crecordset-class.md) objekty v použití.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdb.h

## <a name="see-also"></a>Viz také

[Makra a globální](../../mfc/reference/mfc-macros-and-globals.md)
