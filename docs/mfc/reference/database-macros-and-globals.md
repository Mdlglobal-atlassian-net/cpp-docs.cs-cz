---
title: Databázová makra a globální prvky | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- AFXDB/AFX_ODBC_CALL
- AFXDB/AFX_SQL_ASYNC
- AFXDB/AFX_SQL_SYNC
- AFXDB/AfxGetHENV
dev_langs:
- C++
helpviewer_keywords:
- global database functions [MFC]
- database macros [MFC]
- database globals [MFC]
- global functions [MFC], database functions
- macros [MFC], MFC database
ms.assetid: 5b9b9e61-1cf9-4345-9f29-3807dd466488
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb4dbb75dba33fe616fbce95cdec74bd81cc3fe9
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121913"
---
# <a name="database-macros-and-globals"></a>Databázová makra a globální prvky
Makra a globální prvky, které jsou níže uvedené platí pro aplikace založené na rozhraní ODBC databáze. Používají nejsou s aplikace založené na rozhraní DAO.  
  
 Před MFC 4.2, makra `AFX_SQL_ASYNC` a `AFX_SQL_SYNC` Dal asynchronních operací příležitost yield čas jiným procesům. Od verze knihovny MFC 4.2, provádění těchto makra změnit, protože třídy knihovny MFC rozhraní ODBC použit pouze synchronní operace. Makro `AFX_ODBC_CALL` byl nový MFC 4.2.  
  
### <a name="database-macros"></a>Databázová makra  
  
|||  
|-|-|  
|[AFX_ODBC_CALL –](#afx_odbc_call)|Volání rozhraní API ODBC funkce vracející `SQL_STILL_EXECUTING`. `AFX_ODBC_CALL` opakovaně zavolá funkci dokud už vrátí `SQL_STILL_EXECUTING`.|  
|[AFX_SQL_ASYNC –](#afx_sql_async)|Volání `AFX_ODBC_CALL`.|  
|[AFX_SQL_SYNC –](#afx_sql_sync)|Volání rozhraní API ODBC funkce, která nevrátí `SQL_STILL_EXECUTING`.|  
  
### <a name="database-globals"></a>Globální funkce databáze  
  
|||  
|-|-| 
|[AfxDbInitModule –](#afxdbinitmodule)|Přidá podporu běžné MFC knihovny DLL dynamicky propojené s knihovnou MFC databáze.| 
|[AFXGetHENV –](#afxgethenv)|Načte popisovač pro prostředí aktuálně používán MFC ODBC. Tento popisovač můžete použít v přímé volání rozhraní ODBC.|  


## <a name="afxdbinitmodule"></a> AfxDbInitModule –
Pro databázi knihovny MFC (nebo DAO) podporují z regulární knihovny MFC DLL dynamicky propojené s knihovnou MFC, přidejte volání této funkce ve vašem regulární MFC DLL `CWinApp::InitInstance` databáze funkce k chybě při inicializaci knihovny MFC DLL.  
   
### <a name="syntax"></a>Syntaxe    
```
void AFXAPI AfxDbInitModule( );    
```  
   
### <a name="remarks"></a>Poznámky  
 Zajistěte, aby toto volání dojde před voláním jakékoli základní třídy nebo přidané kód, který přistupuje k databázi MFC DLL. Databáze MFC DLL je knihovnu DLL; v pořadí pro knihovnu DLL do `CDynLinkLibrary` řetězci, musíte vytvořit `CDynLinkLibrary` objektu v kontextu každý modul, který bude používat ho. `AfxDbInitModule` vytvoří `CDynLinkLibrary` objektu v kontextu vaší regulární MFC DLL tak, aby získá přes drátové sítě do `CDynLinkLibrary` objektu řetězu běžné knihovny MFC DLL.  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** < afxdll_.h >  
   
### <a name="see-also"></a>Viz také  
 [Makra a globální prvky](mfc-macros-and-globals.md)
 
  

##  <a name="afx_odbc_call"></a>  AFX_ODBC_CALL –  
 Použití tohoto makra volat jakékoli funkce rozhraní API ODBC, která může vrátit `SQL_STILL_EXECUTING`.  
  
```  
AFX_ODBC_CALL(SQLFunc)  
```  
  
### <a name="parameters"></a>Parametry  
 *SQLFunc*  
 Funkce rozhraní API ODBC. Další informace o funkcích rozhraní API ODBC najdete v části Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 `AFX_ODBC_CALL` opakovaně volá funkci dokud už vrátí `SQL_STILL_EXECUTING`.  
  
 Před vyvoláním `AFX_ODBC_CALL`, je třeba deklarovat proměnnou, `nRetCode`, typu RETCODE.  
  
 Všimněte si, že třídy knihovny MFC rozhraní ODBC nyní použití pouze synchronní zpracování. Chcete-li provést asynchronní operaci, musí volat rozhraní API ODBC funkce `SQLSetConnectOption`. Další informace naleznete v tématu "Provádění funkce asynchronně" v sadě Windows SDK.  

  
### <a name="example"></a>Příklad  
 Tento příklad používá `AFX_ODBC_CALL` k volání `SQLColumns` funkce rozhraní API ODBC, který vrátí seznam hodnot sloupců v tabulce s názvem podle `strTableName`. Všimněte si prohlášení o `nRetCode` a využívat data členů sady záznamů předat parametry funkce. Tento příklad také ukazuje Kontrola výsledků volání s `Check`, členské funkce třídy `CRecordset`. Proměnná `prs` je ukazatel na `CRecordset` objekt, deklarovaný jinde.  
  
 [!code-cpp[NVC_MFCDatabase#39](../../mfc/codesnippet/cpp/database-macros-and-globals_1.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdb.h  

##  <a name="afx_sql_async"></a>  AFX_SQL_ASYNC –  
 Implementace tohoto makra v MFC 4.2 změnit.  
  
```   
AFX_SQL_ASYNC(prs, SQLFunc)   
```  
  
### <a name="parameters"></a>Parametry  
 *prs*  
 Ukazatel `CRecordset` objekt nebo `CDatabase` objektu. Počínaje MFC 4.2, tato hodnota parametru je ignorována.  
  
 *SQLFunc*  
 Funkce rozhraní API ODBC. Další informace o funkcích rozhraní API ODBC najdete v části Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 `AFX_SQL_ASYNC` jednoduše volá makro [afx_odbc_call –](#afx_odbc_call) a ignoruje *prs* parametr. Ve verzích MFC před 4.2 `AFX_SQL_ASYNC` se používá k volání rozhraní API ODBC funkce, které může vrátit `SQL_STILL_EXECUTING`. Pokud funkce rozhraní API ODBC nevrátila `SQL_STILL_EXECUTING`, pak `AFX_SQL_ASYNC` by volání `prs->OnWaitForDataSource`.  
  
> [!NOTE]
>  Třídy MFC rozhraní ODBC teď použít pouze synchronní zpracování. Chcete-li provést asynchronní operaci, musí volat rozhraní API ODBC funkce `SQLSetConnectOption`. Další informace naleznete v tématu "Provádění funkce asynchronně" v sadě Windows SDK.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdb.h  
  
##  <a name="afx_sql_sync"></a>  AFX_SQL_SYNC –  
 `AFX_SQL_SYNC` Makro jednoduše volá funkci `SQLFunc`.  
  
```   
AFX_SQL_SYNC(SQLFunc)   
```  
  
### <a name="parameters"></a>Parametry  
 *SQLFunc*  
 Funkce rozhraní API ODBC. Další informace o těchto funkcích najdete v části Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra k volání rozhraní API ODBC funkce, které nevrátí `SQL_STILL_EXECUTING`.  
  
 Před voláním `AFX_SQL_SYNC`, je třeba deklarovat proměnnou, `nRetCode`, typu RETCODE. Můžete zkontrolovat hodnotu `nRetCode` po volání makro.  
  
 Všimněte si, že implementace `AFX_SQL_SYNC` v MFC 4.2 změnit. Vzhledem k tomu, že kontrola stavu serveru nebyla nutná, už `AFX_SQL_SYNC` jednoduše přiřadí hodnota `nRetCode`. Například místo uskutečněním hovoru  
  
 [!code-cpp[NVC_MFCDatabase#40](../../mfc/codesnippet/cpp/database-macros-and-globals_2.cpp)]  
  
 můžete jednoduše provést přiřazení  
  
 [!code-cpp[NVC_MFCDatabase#41](../../mfc/codesnippet/cpp/database-macros-and-globals_3.cpp)]  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdb.h  
  
##  <a name="afxgethenv"></a>  AFXGetHENV –  
 Vrácený popisovač můžete použít v přímé volání rozhraní ODBC, ale nesmí zavřít popisovač nebo Předpokládejme, že popisovač je stále platný a dostupný po všechny existující `CDatabase`- nebo `CRecordset`-odvozené objekty zničena.  
  
```   
HENV AFXAPI AfxGetHENV(); 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač prostředí aktuálně používán MFC ODBC. Může být `SQL_HENV_NULL` Pokud neexistují žádné [CDatabase](../../mfc/reference/cdatabase-class.md) objekty a ne [CRecordset –](../../mfc/reference/crecordset-class.md) objekty používá.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdb.h  
    
## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
