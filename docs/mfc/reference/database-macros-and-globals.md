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
ms.openlocfilehash: 47a1bb434801c24ab8eee048d9ef8f93793101cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323187"
---
# <a name="database-macros-and-globals"></a>Databázová makra a globální prvky

Makra a globální prvky tady platí pro databázi založenou na ODBC aplikací. Používají se s aplikací založených na DAO.

Před 4.2 knihovny MFC, makra `AFX_SQL_ASYNC` a `AFX_SQL_SYNC` přiřadil asynchronních operací příležitost výnosu čas na jiné procesy. Od verze 4.2 knihovny MFC, provádění těchto maker, změnit, protože třídy knihovny MFC rozhraní ODBC používat pouze synchronní operace. Makro `AFX_ODBC_CALL` nové 4.2 knihovny MFC.

### <a name="database-macros"></a>Databázová makra

|||
|-|-|
|[AFX_ODBC_CALL](#afx_odbc_call)|Volání rozhraní API ODBC funkce, která vrací `SQL_STILL_EXECUTING`. `AFX_ODBC_CALL` bude opakovaně volat funkci dokud již vrátí `SQL_STILL_EXECUTING`.|
|[AFX_SQL_ASYNC](#afx_sql_async)|Volání `AFX_ODBC_CALL`.|
|[AFX_SQL_SYNC](#afx_sql_sync)|Volání rozhraní API ODBC funkce, která nevrací `SQL_STILL_EXECUTING`.|

### <a name="database-globals"></a>Databázové Globály

|||
|-|-|
|[AfxDbInitModule](#afxdbinitmodule)|Přidá podporu databáze pro běžné knihovny MFC DLL staticky propojené do MFC.|
|[AfxGetHENV](#afxgethenv)|Načte popisovače prostředí ODBC aktuálně používána knihovnou MFC. Můžete použít tento ovladač v přímého volání rozhraní ODBC.|

## <a name="afxdbinitmodule"></a> AfxDbInitModule

Z běžné knihovny MFC DLL staticky propojené do MFC podpory databáze knihovny MFC (nebo rozhraní DAO), přidejte volání pro tuto funkci ve vaší běžné knihovny MFC DLL `CWinApp::InitInstance` databáze funkci za účelem inicializace knihovny MFC DLL.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI AfxDbInitModule( );
```

### <a name="remarks"></a>Poznámky

Ujistěte se, že k tomuto volání před voláním třídy base ani v žádném přidaném kód, který přistupuje k databázi knihovny MFC DLL. Databáze knihovny MFC DLL je rozšiřující knihovny DLL; MFC aby rozšiřující knihovny DLL MFC do `CDynLinkLibrary` řetěz, musíte vytvořit `CDynLinkLibrary` objektu v kontextu každého modulu, který budete používat ho. `AfxDbInitModule` vytvoří `CDynLinkLibrary` objektu v kontextu vašeho běžné knihovny MFC DLL tak, aby získá zapojenými do `CDynLinkLibrary` objektu řetězce běžné knihovny MFC DLL.

### <a name="requirements"></a>Požadavky

**Header:** \<afxdll_.h>

##  <a name="afx_odbc_call"></a>  AFX_ODBC_CALL

Použijte toto makro volat jakékoli funkce ODBC API, která může vracet `SQL_STILL_EXECUTING`.

```
AFX_ODBC_CALL(SQLFunc)
```

### <a name="parameters"></a>Parametry

*SQLFunc*<br/>
Funkce rozhraní ODBC API. Další informace o funkcích rozhraní API ODBC najdete v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

`AFX_ODBC_CALL` opakovaně volání funkce do ho už vrátí `SQL_STILL_EXECUTING`.

Před vyvoláním `AFX_ODBC_CALL`, je třeba deklarovat proměnnou, `nRetCode`, typu RETCODE.

Všimněte si, že třídy knihovny MFC rozhraní ODBC teď použijte pouze synchronní zpracování. Aby bylo možné provést asynchronní operaci, musí volat funkce ODBC API `SQLSetConnectOption`. Další informace naleznete v tématu "Provádění funkce asynchronně" v sadě Windows SDK.

### <a name="example"></a>Příklad

Tento příklad používá `AFX_ODBC_CALL` volat `SQLColumns` funkce ODBC API, která vrátí seznam hodnot sloupce v tabulce s názvem podle `strTableName`. Poznámka: deklarace `nRetCode` a využívání záznamů datových členů pro předání parametrů funkci. Tento příklad také znázorňuje, Kontrola výsledků volání s `Check`, členské funkce třídy `CRecordset`. Proměnná `prs` je ukazatel `CRecordset` objektu někde jinde deklarovaný.

[!code-cpp[NVC_MFCDatabase#39](../../mfc/codesnippet/cpp/database-macros-and-globals_1.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

##  <a name="afx_sql_async"></a>  AFX_SQL_ASYNC

Implementace tohoto makra v MFC 4.2 změnit.

```
AFX_SQL_ASYNC(prs, SQLFunc)
```

### <a name="parameters"></a>Parametry

*žádosti o přijetí změn*<br/>
Ukazatel `CRecordset` objektu nebo `CDatabase` objektu. Od verze 4.2 knihovny MFC, je tato hodnota parametru ignorována.

*SQLFunc*<br/>
Funkce rozhraní ODBC API. Další informace o funkcích rozhraní API ODBC najdete v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

`AFX_SQL_ASYNC` jednoduše volá makro [AFX_ODBC_CALL](#afx_odbc_call) a ignoruje *žádosti o přijetí změn* parametru. Ve verzích MFC před 4.2 `AFX_SQL_ASYNC` byla použita k volání funkcí rozhraní API ODBC, které můžou vrátit `SQL_STILL_EXECUTING`. Pokud funkci rozhraní ODBC API vrátilo hodnotu `SQL_STILL_EXECUTING`, pak `AFX_SQL_ASYNC` zavolal `prs->OnWaitForDataSource`.

> [!NOTE]
>  Třídy knihovny MFC rozhraní ODBC nyní používají pouze synchronní zpracování. Aby bylo možné provést asynchronní operaci, musí volat funkce ODBC API `SQLSetConnectOption`. Další informace naleznete v tématu "Provádění funkce asynchronně" v sadě Windows SDK.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdb.h

##  <a name="afx_sql_sync"></a>  AFX_SQL_SYNC

`AFX_SQL_SYNC` – Makro jednoduše volá funkci `SQLFunc`.

```
AFX_SQL_SYNC(SQLFunc)
```

### <a name="parameters"></a>Parametry

*SQLFunc*<br/>
Funkce rozhraní ODBC API. Další informace o těchto funkcích najdete v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Použijte toto makro volání funkcí rozhraní API ODBC, které nebudou nalezeny `SQL_STILL_EXECUTING`.

Před voláním `AFX_SQL_SYNC`, je třeba deklarovat proměnnou, `nRetCode`, typu RETCODE. Můžete zkontrolovat hodnotu `nRetCode` po volání makra.

Všimněte si, že implementace `AFX_SQL_SYNC` změnil 4.2 knihovny MFC. Vzhledem k tomu, že kontroluje se stav serveru již není požadován, `AFX_SQL_SYNC` jednoduše přiřadí hodnotu k `nRetCode`. Například místo provedení volání

[!code-cpp[NVC_MFCDatabase#40](../../mfc/codesnippet/cpp/database-macros-and-globals_2.cpp)]

můžete jednoduše provést přiřazení

[!code-cpp[NVC_MFCDatabase#41](../../mfc/codesnippet/cpp/database-macros-and-globals_3.cpp)]

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdb.h

##  <a name="afxgethenv"></a>  AfxGetHENV

Lze Vrácený popisovač přímého volání rozhraní ODBC, ale nemůže zavřít popisovač nebo předpokládá, že popisovač je pořád platné a k dispozici po všechny existující `CDatabase`– nebo `CRecordset`-odvozené objekty nejsou zničeny.

```
HENV AFXAPI AfxGetHENV();
```

### <a name="return-value"></a>Návratová hodnota

Popisovače prostředí ODBC aktuálně používána knihovnou MFC. Může být `SQL_HENV_NULL` Pokud neexistují žádné [CDatabase](../../mfc/reference/cdatabase-class.md) objekty a ne [CRecordset](../../mfc/reference/crecordset-class.md) objekty používané.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdb.h

## <a name="see-also"></a>Viz také:

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
