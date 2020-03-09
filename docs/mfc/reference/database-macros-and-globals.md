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
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866646"
---
# <a name="database-macros-and-globals"></a>Databázová makra a globální prvky

Níže uvedená makra a globální parametry se vztahují na databázové aplikace založené na rozhraní ODBC. Nepoužívají se pro aplikace založené na rozhraní DAO.

Před knihovnou MFC 4,2 makra `AFX_SQL_ASYNC` a `AFX_SQL_SYNC` předávaly asynchronní operace k získání času pro jiné procesy. Počínaje verzí MFC 4,2 se implementace těchto maker změnila, protože třídy knihovny MFC rozhraní ODBC používaly pouze synchronní operace. Makro `AFX_ODBC_CALL` bylo v knihovně MFC 4,2 nové.

### <a name="database-macros"></a>Databázová makra

|||
|-|-|
|[AFX_ODBC_CALL](#afx_odbc_call)|Volá funkci rozhraní ODBC API, která vrací `SQL_STILL_EXECUTING`. `AFX_ODBC_CALL` bude funkci volat opakovaně, dokud již nevrátí `SQL_STILL_EXECUTING`.|
|[AFX_SQL_ASYNC](#afx_sql_async)|Volá `AFX_ODBC_CALL`.|
|[AFX_SQL_SYNC](#afx_sql_sync)|Volá funkci rozhraní ODBC API, která nevrací `SQL_STILL_EXECUTING`.|

### <a name="database-globals"></a>Databáze Globals

|||
|-|-|
|[AfxDbInitModule](#afxdbinitmodule)|Přidá podporu databáze pro regulární knihovnu MFC DLL, která je dynamicky propojena s knihovnou MFC.|
|[AfxGetHENV](#afxgethenv)|Načte popisovač do prostředí ODBC, které aktuálně používá knihovna MFC. Tento popisovač můžete použít v přímém volání ODBC.|

## <a name="afxdbinitmodule"></a>AfxDbInitModule

Pro podporu databáze knihovny MFC (nebo rozhraní DAO) z běžné knihovny MFC DLL, která je dynamicky propojena s knihovnou MFC, přidejte volání této funkce ve vaší běžné funkci `CWinApp::InitInstance` knihovny MFC DLL pro inicializaci knihovny MFC databáze knihovny MFC.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI AfxDbInitModule( );
```

### <a name="remarks"></a>Poznámky

Ujistěte se, že k tomuto volání dojde před jakýmkoli voláním základní třídy nebo jakýmkoli přidaným kódem, který přistupuje k databázové knihovně MFC DLL. Knihovna DLL databáze knihovny MFC je rozšiřující knihovna DLL knihovny MFC; aby knihovna DLL rozšíření knihovny MFC mohla být zapojená do `CDynLinkLibrary`ho řetězce, musí vytvořit objekt `CDynLinkLibrary` v kontextu každého modulu, který ho bude používat. `AfxDbInitModule` vytvoří objekt `CDynLinkLibrary` v regulárním kontextu knihovny MFC DLL tak, aby byl připojen do `CDynLinkLibrary`ho řetězu objektů běžné knihovny MFC DLL.

### <a name="requirements"></a>Požadavky

**Header:** \<AFXDLL_. h >

##  <a name="afx_odbc_call"></a>AFX_ODBC_CALL

Toto makro použijte k volání libovolné funkce rozhraní ODBC API, která může vracet `SQL_STILL_EXECUTING`.

```
AFX_ODBC_CALL(SQLFunc)
```

### <a name="parameters"></a>Parametry

*SQLFunc*<br/>
Funkce rozhraní API ODBC. Další informace o funkcích rozhraní API ODBC najdete v Windows SDK.

### <a name="remarks"></a>Poznámky

`AFX_ODBC_CALL` opakovaně volá funkci, dokud již nevrátí `SQL_STILL_EXECUTING`.

Před vyvoláním `AFX_ODBC_CALL`musíte deklarovat proměnnou `nRetCode`typu RETCODE.

Všimněte si, že třídy knihovny MFC rozhraní ODBC nyní používají pouze synchronní zpracování. Aby bylo možné provést asynchronní operaci, je nutné zavolat funkci rozhraní ODBC API `SQLSetConnectOption`. Další informace naleznete v tématu "asynchronní spouštění funkcí" v Windows SDK.

### <a name="example"></a>Příklad

V tomto příkladu se používá `AFX_ODBC_CALL` k volání funkce rozhraní ODBC API `SQLColumns`, která vrátí seznam sloupců v tabulce s názvem `strTableName`. Všimněte si deklarace `nRetCode` a použití datových členů sady záznamů k předání parametrů do funkce. Příklad také znázorňuje kontrolu výsledků volání s `Check`, členskou funkcí třídy `CRecordset`. Proměnná `prs` je ukazatel na objekt `CRecordset` deklarovaný jinde.

[!code-cpp[NVC_MFCDatabase#39](../../mfc/codesnippet/cpp/database-macros-and-globals_1.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXDB. h

##  <a name="afx_sql_async"></a>AFX_SQL_ASYNC

Implementace tohoto makra se změnila v knihovně MFC 4,2.

```
AFX_SQL_ASYNC(prs, SQLFunc)
```

### <a name="parameters"></a>Parametry

*PR*<br/>
Ukazatel na objekt `CRecordset` nebo objekt `CDatabase`. Počínaje verzí MFC 4,2 je tato hodnota parametru ignorována.

*SQLFunc*<br/>
Funkce rozhraní API ODBC. Další informace o funkcích rozhraní API ODBC najdete v Windows SDK.

### <a name="remarks"></a>Poznámky

`AFX_SQL_ASYNC` jednoduše volá makro [AFX_ODBC_CALL](#afx_odbc_call) a ignoruje parametr *PR* . Ve verzích knihovny MFC starších než 4,2 byla `AFX_SQL_ASYNC` použita k volání funkcí rozhraní ODBC API, které mohou vracet `SQL_STILL_EXECUTING`. Pokud funkce rozhraní ODBC API vrátila hodnotu `SQL_STILL_EXECUTING`, `AFX_SQL_ASYNC` by zavolala `prs->OnWaitForDataSource`.

> [!NOTE]
>  Třídy knihovny MFC rozhraní ODBC nyní používají pouze synchronní zpracování. Aby bylo možné provést asynchronní operaci, je nutné zavolat funkci rozhraní ODBC API `SQLSetConnectOption`. Další informace naleznete v tématu "asynchronní spouštění funkcí" v Windows SDK.

### <a name="requirements"></a>Požadavky

  **Header** AFXDB. h

##  <a name="afx_sql_sync"></a>AFX_SQL_SYNC

Makro `AFX_SQL_SYNC` jednoduše volá `SQLFunc`funkce.

```
AFX_SQL_SYNC(SQLFunc)
```

### <a name="parameters"></a>Parametry

*SQLFunc*<br/>
Funkce rozhraní API ODBC. Další informace o těchto funkcích naleznete v Windows SDK.

### <a name="remarks"></a>Poznámky

Pomocí tohoto makra můžete volat funkce rozhraní ODBC API, které nebudou vracet `SQL_STILL_EXECUTING`.

Před voláním `AFX_SQL_SYNC`musíte deklarovat proměnnou `nRetCode`typu RETCODE. Můžete kontrolovat hodnotu `nRetCode` po volání makra.

Všimněte si, že implementace `AFX_SQL_SYNC` změněna v knihovně MFC 4,2. Vzhledem k tomu, že kontrola stavu serveru už není nutná, `AFX_SQL_SYNC` jednoduše přiřadí hodnotu `nRetCode`. Například místo provedení volání

[!code-cpp[NVC_MFCDatabase#40](../../mfc/codesnippet/cpp/database-macros-and-globals_2.cpp)]

můžete jednoduše provést přiřazení.

[!code-cpp[NVC_MFCDatabase#41](../../mfc/codesnippet/cpp/database-macros-and-globals_3.cpp)]

### <a name="requirements"></a>Požadavky

  **Header** AFXDB. h

##  <a name="afxgethenv"></a>AfxGetHENV

Vrácený popisovač můžete použít v přímém volání rozhraní ODBC, ale nesmíte zavřít popisovač nebo předpokládat, že popisovač je stále platný a dostupný po zničení všech existujících objektů odvozených `CDatabase`nebo `CRecordset`.

```
HENV AFXAPI AfxGetHENV();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač prostředí ODBC aktuálně používaného knihovnou MFC. Může být `SQL_HENV_NULL`, pokud neexistují žádné objekty [CDatabase](../../mfc/reference/cdatabase-class.md) a nejsou používány žádné objekty [CRecordset](../../mfc/reference/crecordset-class.md) .

### <a name="requirements"></a>Požadavky

  **Header** AFXDB. h

## <a name="see-also"></a>Viz také

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
