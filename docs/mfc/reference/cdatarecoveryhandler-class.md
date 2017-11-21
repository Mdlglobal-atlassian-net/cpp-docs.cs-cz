---
title: "Třída CDataRecoveryHandler | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDataRecoveryHandler
- AFXDATARECOVERY/CDataRecoveryHandler
- AFXDATARECOVERY/CDataRecoveryHandler::CDataRecoveryHandler
- AFXDATARECOVERY/CDataRecoveryHandler::AutosaveAllDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::AutosaveDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::CreateDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::DeleteAllAutosavedFiles
- AFXDATARECOVERY/CDataRecoveryHandler::DeleteAutosavedFile
- AFXDATARECOVERY/CDataRecoveryHandler::GenerateAutosaveFileName
- AFXDATARECOVERY/CDataRecoveryHandler::GetAutosaveInterval
- AFXDATARECOVERY/CDataRecoveryHandler::GetAutosavePath
- AFXDATARECOVERY/CDataRecoveryHandler::GetDocumentListName
- AFXDATARECOVERY/CDataRecoveryHandler::GetNormalDocumentTitle
- AFXDATARECOVERY/CDataRecoveryHandler::GetRecoveredDocumentTitle
- AFXDATARECOVERY/CDataRecoveryHandler::GetRestartIdentifier
- AFXDATARECOVERY/CDataRecoveryHandler::GetSaveDocumentInfoOnIdle
- AFXDATARECOVERY/CDataRecoveryHandler::GetShutdownByRestartManager
- AFXDATARECOVERY/CDataRecoveryHandler::Initialize
- AFXDATARECOVERY/CDataRecoveryHandler::QueryRestoreAutosavedDocuments
- AFXDATARECOVERY/CDataRecoveryHandler::ReadOpenDocumentList
- AFXDATARECOVERY/CDataRecoveryHandler::RemoveDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::ReopenPreviousDocuments
- AFXDATARECOVERY/CDataRecoveryHandler::RestoreAutosavedDocuments
- AFXDATARECOVERY/CDataRecoveryHandler::SaveOpenDocumentList
- AFXDATARECOVERY/CDataRecoveryHandler::SetAutosaveInterval
- AFXDATARECOVERY/CDataRecoveryHandler::SetAutosavePath
- AFXDATARECOVERY/CDataRecoveryHandler::SetRestartIdentifier
- AFXDATARECOVERY/CDataRecoveryHandler::SetSaveDocumentInfoOnIdle
- AFXDATARECOVERY/CDataRecoveryHandler::SetShutdownByRestartManager
- AFXDATARECOVERY/CDataRecoveryHandler::UpdateDocumentInfo
dev_langs: C++
helpviewer_keywords:
- CDataRecoveryHandler [MFC], CDataRecoveryHandler
- CDataRecoveryHandler [MFC], AutosaveAllDocumentInfo
- CDataRecoveryHandler [MFC], AutosaveDocumentInfo
- CDataRecoveryHandler [MFC], CreateDocumentInfo
- CDataRecoveryHandler [MFC], DeleteAllAutosavedFiles
- CDataRecoveryHandler [MFC], DeleteAutosavedFile
- CDataRecoveryHandler [MFC], GenerateAutosaveFileName
- CDataRecoveryHandler [MFC], GetAutosaveInterval
- CDataRecoveryHandler [MFC], GetAutosavePath
- CDataRecoveryHandler [MFC], GetDocumentListName
- CDataRecoveryHandler [MFC], GetNormalDocumentTitle
- CDataRecoveryHandler [MFC], GetRecoveredDocumentTitle
- CDataRecoveryHandler [MFC], GetRestartIdentifier
- CDataRecoveryHandler [MFC], GetSaveDocumentInfoOnIdle
- CDataRecoveryHandler [MFC], GetShutdownByRestartManager
- CDataRecoveryHandler [MFC], Initialize
- CDataRecoveryHandler [MFC], QueryRestoreAutosavedDocuments
- CDataRecoveryHandler [MFC], ReadOpenDocumentList
- CDataRecoveryHandler [MFC], RemoveDocumentInfo
- CDataRecoveryHandler [MFC], ReopenPreviousDocuments
- CDataRecoveryHandler [MFC], RestoreAutosavedDocuments
- CDataRecoveryHandler [MFC], SaveOpenDocumentList
- CDataRecoveryHandler [MFC], SetAutosaveInterval
- CDataRecoveryHandler [MFC], SetAutosavePath
- CDataRecoveryHandler [MFC], SetRestartIdentifier
- CDataRecoveryHandler [MFC], SetSaveDocumentInfoOnIdle
- CDataRecoveryHandler [MFC], SetShutdownByRestartManager
- CDataRecoveryHandler [MFC], UpdateDocumentInfo
ms.assetid: 7794802c-e583-4eba-90b9-2fed1a161f9c
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bf80d43179c0b7e5de52aeb2db46ac17b7df2763
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cdatarecoveryhandler-class"></a>CDataRecoveryHandler – třída
`CDataRecoveryHandler` Autosaves dokumenty a obnoví je, pokud neočekávaně ukončí aplikaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDataRecoveryHandler : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[CDataRecoveryHandler::CDataRecoveryHandler](#cdatarecoveryhandler)|Vytvoří `CDataRecoveryHandler` objektu.|  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[CDataRecoveryHandler::AutosaveAllDocumentInfo](#autosavealldocumentinfo)|Autosaves zaregistrována každý soubor `CDataRecoveryHandler` třídy.|  
|[CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo)|Autosaves zadaný dokument.|  
|[CDataRecoveryHandler::CreateDocumentInfo](#createdocumentinfo)|Dokument se přidá do seznamu otevřené dokumenty.|  
|[CDataRecoveryHandler::DeleteAllAutosavedFiles](#deleteallautosavedfiles)|Odstraní všechny aktuální soubory automaticky uloženo.|  
|[CDataRecoveryHandler::DeleteAutosavedFile](#deleteautosavedfile)|Odstraní zadaný automaticky uloženo soubor.|  
|[CDataRecoveryHandler::GenerateAutosaveFileName](#generateautosavefilename)|Generuje název pro soubor automatické ukládání přidružené k názvu souboru dodaný dokument.|  
|[CDataRecoveryHandler::GetAutosaveInterval](#getautosaveinterval)|Vrátí interval mezi automatické ukládání pokusů.|  
|[CDataRecoveryHandler::GetAutosavePath](#getautosavepath)|Vrátí cestu souborů automaticky uloženo.|  
|[CDataRecoveryHandler::GetDocumentListName](#getdocumentlistname)|Načte název dokumentu z `CDocument` objektu.|  
|[CDataRecoveryHandler::GetNormalDocumentTitle](#getnormaldocumenttitle)|Načte normální název zadaný dokument.|  
|[CDataRecoveryHandler::GetRecoveredDocumentTitle](#getrecovereddocumenttitle)|Vytvoří a vrátí název obnovené dokumentu.|  
|[CDataRecoveryHandler::GetRestartIdentifier](#getrestartidentifier)|Načte restartování jedinečný identifikátor pro aplikaci.|  
|[CDataRecoveryHandler::GetSaveDocumentInfoOnIdle](#getsavedocumentinfoonidle)|Určuje, zda `CDataRecoveryHandler` automatické ukládání provádí aktuální nečinné smyčky.|  
|[CDataRecoveryHandler::GetShutdownByRestartManager](#getshutdownbyrestartmanager)|Určuje, zda správce restartování způsobilo, že aplikace ukončíte.|  
|[CDataRecoveryHandler::Initialize](#initialize)|Inicializuje `CDataRecoveryHandler`.|  
|[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments)|Zobrazí dialogové okno pro uživatele, pro každý dokumentu, který `CDataRecoveryHandler` automaticky uloženo. Dialogové okno určuje, jestli uživatel chce obnovení dokumentu automaticky uloženo.|  
|[CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist)|Načte seznam otevřít dokument z registru.|  
|[CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo)|Dodaný dokument odebere ze seznamu otevřít dokument.|  
|[CDataRecoveryHandler::ReopenPreviousDocuments](#reopenpreviousdocuments)|Otevře se dříve otevřené dokumenty.|  
|[CDataRecoveryHandler::RestoreAutosavedDocuments](#restoreautosaveddocuments)|Obnoví dokumenty automaticky uloženo založené na vstup uživatele.|  
|[CDataRecoveryHandler::SaveOpenDocumentList](#saveopendocumentlist)|Uloží aktuální seznam otevřené dokumenty do registru systému Windows.|  
|[CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval)|Nastaví časový interval mezi cykly automatické ukládání v milisekundách.|  
|[CDataRecoveryHandler::SetAutosavePath](#setautosavepath)|Nastaví adresář, kde jsou uloženy soubory automaticky uloženo.|  
|[CDataRecoveryHandler::SetRestartIdentifier](#setrestartidentifier)|Nastaví restartování jedinečný identifikátor pro tuto instanci `CDataRecoveryHandler`.|  
|[CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle)|Nastaví jestli `CDataRecoveryHandler` uloží informace otevřít dokument do registru systému Windows během aktuální nečinnosti cyklu.|  
|[CDataRecoveryHandler::SetShutdownByRestartManager](#setshutdownbyrestartmanager)|Nastaví, zda předchozí ukončení aplikace bylo způsobeno správce restartování.|  
|[CDataRecoveryHandler::UpdateDocumentInfo](#updatedocumentinfo)|Aktualizuje informace pro dokument, protože uživatel jej uložili.|  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|m_bRestoringPreviousOpenDocs|Určuje, zda obslužná rutina obnovení dat neotevře dříve otevřené dokumenty.|  
|m_bSaveDocumentInfoOnIdle|Určuje, zda autosaves obslužná rutina obnovení dat dokumentů na další nečinné smyčky.|  
|m_bShutdownByRestartManager|Určuje, zda správce restartování způsobí, že aplikace ukončete.|  
|m_dwRestartManagerSupportFlags|Příznaky, které označuje, co podpory správce restartování poskytuje pro aplikace.|  
|m_lstAutosavesToDelete|Seznam automaticky uloženo soubory, které nebyly odstraněny, když byly uzavřeny původní dokumenty. Při ukončení aplikace, opakování správce restartování, odstraňování souborů.|  
|m_mapDocNameToAutosaveName|Mapa názvů dokumentu na názvy souborů automaticky uloženo.|  
|m_mapDocNameToDocumentPtr|Mapu dokumentu jména [CDocument](../../mfc/reference/cdocument-class.md) ukazatele.|  
|m_mapDocNameToRestoreBool|Mapa názvů dokumentu na logický parametr, který označuje, zda obnovení dokumentu automaticky uloženo.|  
|m_mapDocumentPtrToDocName|Mapu `CDocument` ukazatele na názvy dokumentu.|  
|m_mapDocumentPtrToDocTitle|Mapu `CDocument` ukazatele na názvy dokumentu. Tyto názvy se používají k ukládání souborů.|  
|m_nAutosaveInterval|Čas v milisekundách mezi autosaves.|  
|m_nTimerID|Identifikátor pro automatické ukládání časovač.|  
|m_strAutosavePath|Umístění, kde jsou uložené dokumenty automaticky uloženo.|  
|m_strRestartIdentifier|Řetězcová reprezentace identifikátoru GUID pro správce restartování.|  
  
## <a name="remarks"></a>Poznámky  
 Správce restartování používá `CDataRecoveryHandler` třída zachovat sledovat všechny otevřené dokumenty a automatické ukládání je podle potřeby. Pokud chcete povolit automatické ukládání, použijte [CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle) metoda. Tato metoda přesměruje `CDataRecoveryHandler` k provedení automatické ukládání na další nečinné smyčky. Volání správce restartování `SetSaveDocumentInfoOnIdle` při `CDataRecoveryHandler` proveďte automatické ukládání.  
  
 Všechny metody `CDataRecoveryHandler` třídy jsou virtuální. Přepsání metody v této třídy lze vytvořit vlastní obslužnou rutinu obnovení vlastní data. Pokud vytvoříte vlastní obslužnou rutinu obnovení dat nebo restartovat správce, nevytvoří instanci CDataRecoveryHandler. [CWinApp – třída](../../mfc/reference/cwinapp-class.md) vytvoří `CDataRecoveryHandler` objektů, jako je povinný.  
  
 Abyste mohli používat `CDataRecoveryHandler` objektu, musí volat [CDataRecoveryHandler::Initialize](#initialize).  
  
 Protože `CDataRecoveryHandler` třída je úzce připojený k správce restartování `CDataRecoveryHandler` závisí na parametru globální `m_dwRestartManagerSupportFlags`. Tento parametr určuje, jaká oprávnění správce restartování má a jak komunikuje s vaší aplikací. Chcete-li správce restartování začlenit do existující aplikace, budete muset přiřadit `m_dwRestartManagerSupportFlags` odpovídající hodnotu v konstruktoru hlavní aplikace. Další informace o tom, jak pomocí Správce restartu najdete v tématu [postupy: Přidání podpory správce restartování](../../mfc/how-to-add-restart-manager-support.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdatarecovery.h  
  
##  <a name="autosavealldocumentinfo"></a>CDataRecoveryHandler::AutosaveAllDocumentInfo  
 Autosaves zaregistrována každý soubor `CDataRecoveryHandler` třídy.  
  
```  
virtual BOOL AutosaveAllDocumentInfo();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud `CDataRecoveryHandler` uložit všechny dokumenty; `FALSE` Pokud dokumentu nebyla uložena.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vrátí hodnotu `TRUE` Pokud neexistují žádné dokumenty, které musí být uložena. Vrátí také `TRUE` bez uložení žádné dokumenty, pokud načítá `CWinApp` nebo `CDocManager` pro aplikace, vygeneruje se chyba.  
  
 Chcete-li použít tuto metodu, buď `AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART` nebo `AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL` musí být nastavena v `m_dwRestartManagerSupportFlags`. V tématu [m_dwRestartManagerSupportFlags](#m_dwrestartmanagersupportflags) Další informace.  
  
##  <a name="autosavedocumentinfo"></a>CDataRecoveryHandler::AutosaveDocumentInfo  
 Autosaves zadaný dokument.  
  
```  
virtual BOOL AutosaveDocumentInfo(
    CDocument* pDocument,  
    BOOL bResetModifiedFlag = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v]`pDocument`|Ukazatel `CDocument` uložit.|  
|[v]`bResetModifiedFlag`|`TRUE`Určuje, že `CDataRecoveryHandler` zvažuje `pDocument` má být změněn; `FALSE` označuje, že rozhraní zvažuje `pDocument` být beze změny. Najdete v části poznámky Další informace o účinek tento příznak.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud jsou nastavená příslušnými příznaky a `pDocument` je platná `CDocument` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Každý `CDocument` objekt má příznak, který určuje, jestli se změnil od posledního uložení. Použití [CDocument::IsModified](../../mfc/reference/cdocument-class.md#ismodified) určit stav pro tento příznak. Pokud `CDocument` nezměnil se od posledního uložení `AutosaveDocumentInfo` odstraní všechny soubory automaticky uloženo pro tento dokument. Pokud dokument došlo ke změně od posledního uložení zavřením vyzývá uživatele k dokument před zavřením uložit.  
  
> [!NOTE]
>  Pomocí `bResetModifiedFlag` na změnu stavu dokumentu na beze změny může způsobit, že uživatel ztratí neuložená data. Pokud rozhraní zvažuje dokumentu ponechat beze změny, zavřením nezobrazí výzvu uživateli uložit.  
  
 Tato metoda vyvolá výjimku s [ASSERT](diagnostic-services.md#assert) makro Pokud `pDocument` není platným `CDocument` objektu.  
  
 Chcete-li použít tuto metodu, buď `AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART` nebo `AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL` musí být nastavena v `m_dwRestartManagerSupportFlags`.   
  
##  <a name="cdatarecoveryhandler"></a>CDataRecoveryHandler::CDataRecoveryHandler  
 Vytvoří `CDataRecoveryHandler` objektu.  
  
```  
CDataRecoveryHandler(
    DWORD dwRestartManagerSupportFlags,  
    int nAutosaveInterval);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v]`dwRestartManagerSupportFlags`|Určuje, které možnosti Správce restartování jsou podporované.|  
|[v]`nAutosaveInterval`|Doba mezi autosaves. Tento parametr je v milisekundách.|  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní MFC framework automaticky vytvoří `CDataRecoveryHandler` objekt pro vaši aplikaci při použití **nový projekt** průvodce. Pokud jsou úpravy, bude se chování obnovení dat nebo správce restartování, byste je neměli vytvářet `CDataRecoveryHandler` objektu.  
  
  
##  <a name="createdocumentinfo"></a>CDataRecoveryHandler::CreateDocumentInfo  
 Dokument se přidá do seznamu otevřené dokumenty.  
  
```  
virtual BOOL CreateDocumentInfo(CDocument* pDocument);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v]`pDocument`|Ukazatel na `CDocument`. Tato metoda vytvoří dokument informace pro tento `CDocument`.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Výchozí implementace vrací `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda ověří, zda `pDocument` je již v seznamu dokumentů před přidáním dokumentu. Pokud `pDocument` je již v seznamu, tato metoda odstraní přidružený soubor automaticky uloženo `pDocument`.  
  
 Chcete-li použít tuto metodu, buď `AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART` nebo `AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL` musí být nastavena v `m_dwRestartManagerSupportFlags`. 
  
##  <a name="deleteallautosavedfiles"></a>CDataRecoveryHandler::DeleteAllAutosavedFiles  
 Odstraní všechny aktuální soubory automaticky uloženo.  
  
```  
virtual BOOL DeleteAllAutosavedFiles();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výchozí implementace vždy vrátí `TRUE`.  
  
##  <a name="deleteautosavedfile"></a>CDataRecoveryHandler::DeleteAutosavedFile  
 Odstraní zadaný automaticky uloženo soubor.  
  
```  
virtual BOOL DeleteAutosavedFile(const CString& strAutosavedFile);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v]`strAutosavedFile`|Řetězec, který obsahuje název souboru automaticky uloženo.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Výchozí implementace vždy návratový `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud tato metoda nemůže odstranit soubor automaticky uložená, uloží název souboru v seznamu. Destruktor pro `CDataRecoveryHandler` pokusí odstranit každý automaticky uloženo soubor zadaný v tomto seznamu.  
  
##  <a name="generateautosavefilename"></a>CDataRecoveryHandler::GenerateAutosaveFileName  
 Generuje název pro soubor automatické ukládání přidružené k názvu souboru dodaný dokument.  
  
```  
virtual CString GenerateAutosaveFileName(const CString& strDocumentName) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`strDocumentName`  
 Řetězec, který obsahuje název dokumentu. `GenerateAutosaveFileName`Tento název dokumentu se používá ke generování odpovídající název souboru automatické ukládání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Název souboru automatické ukládání vygenerovat z `strDocumentName`.  
  
### <a name="remarks"></a>Poznámky  
 Každý název dokumentu má mapování 1: 1 s názvem souboru automatické ukládání.  
  
##  <a name="getautosaveinterval"></a>CDataRecoveryHandler::GetAutosaveInterval  
 Vrátí interval mezi automatické ukládání pokusů.  
  
```  
virtual int GetAutosaveInterval() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet milisekund, po mezi automatické ukládání pokusí.  
  
##  <a name="getautosavepath"></a>CDataRecoveryHandler::GetAutosavePath  
 Vrátí cestu souborů automaticky uloženo.  
  
```  
virtual CString GetAutosavePath() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Umístění, kde jsou uložené dokumenty automaticky uloženo.  
  
##  <a name="getdocumentlistname"></a>CDataRecoveryHandler::GetDocumentListName  
 Načte název dokumentu z `CDocument` objektu.  
  
```  
virtual CString GetDocumentListName(CDocument* pDocument) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v]`pDocument`|Ukazatel na `CDocument`. `GetDocumentListName`načte název dokumentu z tohoto `CDocument`.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Název dokumentu z `pDocument`.  
  
### <a name="remarks"></a>Poznámky  
 `CDataRecoveryHandler` Používá název dokumentu jako klíče v `m_mapDocNameToAutosaveName`, `m_mapDocNameToDocumentPtr`, a `m_mapDocNameToRestoreBool`. Povolit tyto parametr `CDataRecoveryHandler` monitorování `CDocument` objekty, název souboru automatické ukládání a automatické ukládání nastavení.  
  
##  <a name="getnormaldocumenttitle"></a>CDataRecoveryHandler::GetNormalDocumentTitle  
 Načte normální název zadaný dokument.  
  
```  
virtual CString GetNormalDocumentTitle(CDocument* pDocument);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v]`pDocument`|Ukazatel na `CDocument`.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Normální název pro zadaný dokument.  
  
### <a name="remarks"></a>Poznámky  
 Normální název dokumentu je obvykle název souboru dokumentu bez cesty. Toto je název v **název souboru** pole z **uložit jako** dialogové okno.  
  
##  <a name="getrecovereddocumenttitle"></a>CDataRecoveryHandler::GetRecoveredDocumentTitle  
 Vytvoří a vrátí název obnovené dokumentu.  
  
```  
virtual CString GetRecoveredDocumentTitle(const CString& strDocumentTitle) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`strDocumentTitle`  
 Normální název dokumentu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Název obnovené dokumentu.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení, obnovené nadpis dokumentu je normální název s **[obnovit]** přidá se k němu. Obnovená název se zobrazí uživateli při `CDataRecoveryHandler` dotazuje uživateli obnovit dokumenty automaticky uloženo.  
  
##  <a name="getrestartidentifier"></a>CDataRecoveryHandler::GetRestartIdentifier  
 Načte restartování jedinečný identifikátor pro aplikaci.  
  
```  
virtual CString GetRestartIdentifier() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Restartování jedinečný identifikátor.  
  
### <a name="remarks"></a>Poznámky  
 Restartování identifikátor je jedinečný pro každé spuštění aplikace.  
  
 `CDataRecoveryHandler` Ukládá informace v registru o nyní otevřené dokumenty. Po restartování správce ukončí aplikaci a bude ho poskytne identifikátor restartování, který `CDataRecoveryHandler`. `CDataRecoveryHandler` Používá identifikátor restartování načíst seznam dříve otevřené dokumenty. Díky tomu `CDataRecoveryHandler` na pokus o vyhledání a obnovení souborů automaticky uloženo.  
  
##  <a name="getsavedocumentinfoonidle"></a>CDataRecoveryHandler::GetSaveDocumentInfoOnIdle  
 Určuje, zda `CDataRecoveryHandler` automatické ukládání provádí aktuální nečinné smyčky.  
  
```  
virtual BOOL GetSaveDocumentInfoOnIdle() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Určuje, `CDataRecoveryHandler` autosaves na aktuální nečinné smyčky; `FALSE` označuje je nepoužívá.  
  
##  <a name="getshutdownbyrestartmanager"></a>CDataRecoveryHandler::GetShutdownByRestartManager  
 Určuje, zda správce restartování způsobilo, že aplikace ukončíte.  
  
```  
virtual BOOL GetShutdownByRestartManager() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Označuje, že správce restartování způsobilo, že aplikace ukončíte; `FALSE` označuje tomu tak není.  
  
##  <a name="initialize"></a>CDataRecoveryHandler::Initialize  
 Inicializuje `CDataRecoveryHandler`.  
  
```  
virtual BOOL Initialize();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud se inicializace úspěšné; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Proces inicializace načte cestu pro ukládání automatické ukládání souborů z registru. Pokud `Initialize` metoda nemůže najít tohoto adresáře nebo pokud cesta je `NULL`, `Initialize` selže a vrátí `FALSE`.  
  
 Použití [CDataRecoveryHandler::SetAutosavePath](#setautosavepath) k automatické ukládání cestu změnit po inicializuje vaší aplikace `CDataRecoveryHandler`.  
  
 `Initialize` Metoda také spustí časovač monitorování, když dojde k další automatické ukládání. Použití [CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval) změnit interval automatického ukládání po inicializuje vaší aplikace `CDataRecoveryHandler`.  
  
##  <a name="queryrestoreautosaveddocuments"></a>CDataRecoveryHandler::QueryRestoreAutosavedDocuments  
 Zobrazí dialogové okno pro uživatele, pro každý dokumentu, který `CDataRecoveryHandler` automaticky uloženo. Dialogové okno určuje, jestli uživatel chce obnovení dokumentu automaticky uloženo.  
  
```  
virtual void QueryRestoreAutosavedDocuments();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud je aplikace kódování Unicode, zobrazí tato metoda [objektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md) uživateli. Jinak, používá rozhraní [AfxMessageBox –](../../mfc/reference/cstring-formatting-and-message-box-display.md#afxmessagebox) dotazovat uživatele.  
  
 Po `QueryRestoreAutosavedDocuments` shromažďuje všechny odpovědi od uživatele, ukládá informace v členské proměnné `m_mapDocNameToRestoreBool`. Tato metoda neobnoví dokumenty automaticky uloženo.  
  
##  <a name="readopendocumentlist"></a>CDataRecoveryHandler::ReadOpenDocumentList  
 Načte seznam otevřít dokument z registru.  
  
```  
virtual BOOL ReadOpenDocumentList();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Určuje, že `ReadOpenDocumentList` načíst informace pro minimálně jeden dokument z registru; `FALSE` označuje byl načteny žádné informace o dokumentu.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce načte informace otevřít dokument z registru a ukládá je v členské proměnné `m_mapDocNameToAutosaveName`.  
  
 Po `ReadOpenDocumentList` načte všechna data, odstraní informace o dokumentu z registru.  
  
##  <a name="removedocumentinfo"></a>CDataRecoveryHandler::RemoveDocumentInfo  
 Dodaný dokument odebere ze seznamu otevřít dokument.  
  
```  
virtual BOOL RemoveDocumentInfo(CDocument* pDocument);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v]`pDocument`|Ukazatel na dokument, který chcete odebrat.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud `pDocument` byla odebrána ze seznamu; `FALSE` Pokud došlo k chybě.  
  
### <a name="remarks"></a>Poznámky  
 Když uživatel nezavře dokumentu, rozhraní používá tato metoda ho odebrat ze seznamu otevřené dokumenty.  
  
 Pokud `RemoveDocumentInfo` nelze najít `pDocument` v seznamu otevřené dokumenty, neprovede žádnou akci a vrátí `TRUE`.  
  
 Při použití této metody `AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES` musí být nastavena v `m_dwRestartManagerSupportFlags`.   
  
##  <a name="reopenpreviousdocuments"></a>CDataRecoveryHandler::ReopenPreviousDocuments  
 Otevře se dříve otevřené dokumenty.  
  
```  
virtual BOOL ReopenPreviousDocuments();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud byl otevřen alespoň jeden dokument; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda otevře nejnovější uložení o dříve otevřené dokumenty. Pokud nebyla uložena dokumentu nebo automaticky uložená, `ReopenPreviousDocuments` otevře prázdný dokument založený na šabloně pro daný typ souboru.  
  
 Při použití této metody `AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES` musí být nastavena v `m_dwRestartManagerSupportFlags`. Pokud tento parametr není nastaven, `ReopenPreviousDocuments` neprovede žádnou akci a vrátí `FALSE`.  
  
 Pokud neexistují žádné dokumenty uložené v seznamu dříve otevřené dokumenty `ReopenPreviousDocuments` neprovede žádnou akci a vrátí `FALSE`.  
  
##  <a name="restoreautosaveddocuments"></a>CDataRecoveryHandler::RestoreAutosavedDocuments  
 Obnoví dokumenty automaticky uloženo založené na vstup uživatele.  
  
```  
virtual BOOL RestoreAutosavedDocuments();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud tato metoda obnoví úspěšně dokumenty.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá [CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments) k určení, které dokumenty uživatel chce obnovit. Pokud se uživatel rozhodne nechcete obnovit dokument automaticky uloženo `RestoreAutosavedDocuments` odstraní tento soubor. V opačném `RestoreAutosavedDocuments` nahradí otevřít dokument automaticky uložená verze.  
  
 Chcete-li použít tuto metodu, buď `AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES` nebo `AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES` musí být nastavena v `m_dwRestartManagerSupportFlags`.   
  
##  <a name="saveopendocumentlist"></a>CDataRecoveryHandler::SaveOpenDocumentList  
 Uloží aktuální seznam otevřené dokumenty do registru systému Windows.  
  
```  
virtual BOOL SaveOpenDocumentList();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud neexistují žádné otevřené dokumenty uložit, nebo pokud se úspěšně uložily. `FALSE`Pokud jsou dokumenty uložit do registru, ale nejsou uloženy, protože došlo k chybě.  
  
### <a name="remarks"></a>Poznámky  
 Volání správce restartování `SaveOpenDocumentList` při ukončení aplikace neočekávaně nebo když opustí pro upgrade. Po restartování aplikace používá [CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist) načíst seznam otevřené dokumenty.  
  
 Tato metoda šetří pouze seznam otevřené dokumenty. Metoda [CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo) zodpovídá za ukládání dokumentů, sami.  
  
##  <a name="setautosaveinterval"></a>CDataRecoveryHandler::SetAutosaveInterval  
 Nastaví časový interval mezi cykly automatické ukládání v milisekundách.  
  
```  
Virtual void SetAutosaveInterval(int nAutosaveInterval);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nAutosaveInterval`  
 Nové automatické ukládání interval v milisekundách.  
  
##  <a name="setautosavepath"></a>CDataRecoveryHandler::SetAutosavePath  
 Nastaví adresář, kde jsou uloženy soubory automaticky uloženo.  
  
```  
virtual void SetAutosavePath(const CString& strAutosavePath);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v]`strAutosavePath`|Cesta, kam se ukládají automaticky ukládat soubory.|  
  
### <a name="remarks"></a>Poznámky  
 Změna adresáře automatické ukládání nepřesouvá aktuálně soubory automaticky uloženo.  
  
##  <a name="setrestartidentifier"></a>CDataRecoveryHandler::SetRestartIdentifier  
 Nastaví restartování jedinečný identifikátor pro tuto instanci `CDataRecoveryHandler`.  
  
```  
virtual void SetRestartIdentifier(const CString& strRestartIdentifier);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v]`strRestartIdentifier`|Jedinečný identifikátor pro správce restartování.|  
  
### <a name="remarks"></a>Poznámky  
 Správce restartování zaznamenává informace o otevřené dokumenty v registru. Tyto informace se uloží spolu restartování jedinečný identifikátor jako klíč. Restartování identifikátor je jedinečný pro každou instanci aplikace více instancí aplikace může neočekávaně ukončit a správce restartování můžete obnovit každý z nich.  
  
##  <a name="setsavedocumentinfoonidle"></a>CDataRecoveryHandler::SetSaveDocumentInfoOnIdle  
 Nastaví jestli `CDataRecoveryHandler` uloží informace otevřít dokument do registru systému Windows během aktuální nečinnosti cyklu.  
  
```  
virtual void SetSaveDocumentInfoOnIdle(BOOL bSaveOnIdle);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v]`bSaveOnIdle`|`TRUE`Uložte dokument informace během aktuální nečinnosti cyklu; `FALSE to not perform a save`.|  
  
##  <a name="setshutdownbyrestartmanager"></a>CDataRecoveryHandler::SetShutdownByRestartManager  
 Nastaví, zda předchozí ukončení aplikace bylo způsobeno správce restartování.  
  
```  
virtual void SetShutdownByRestartManager(BOOL bShutdownByRestartManager);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v]`bShutdownByRestartManager`|`TRUE`k označení, že správce restartování způsobilo, že aplikace ukončíte; `FALSE` k označení, že aplikace byl ukončen z jiného důvodu.|  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní se chová různě v závislosti na tom, jestli se předchozí ukončovací nebo zda byl inicializován nástrojem Správce restartování.  
  
##  <a name="updatedocumentinfo"></a>CDataRecoveryHandler::UpdateDocumentInfo  
 Aktualizuje informace pro dokument, protože uživatel jej uložili.  
  
```  
virtual BOOL UpdateDocumentInfo(CDocument* pDocument);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v]`pDocument`|Ukazatel na uložený dokument.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud tato metoda dokumentu automaticky uložená a aktualizovat informace o dokumentu; `FALSE` Pokud došlo k chybě.  
  
### <a name="remarks"></a>Poznámky  
 Když uživatel uloží dokument, odebere aplikace automaticky uloženo soubor, protože už je potřeba. `UpdateDocumentInfo`Odstraní soubor automaticky uloženo voláním [CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo). `UpdateDocumentInfo`potom přidá informace z `pDocument` do seznamu aktuálně otevřené dokumenty protože `RemoveDocumentInfo` odstraní informace, ale uložené dokument je stále otevřen.  
  
 Při použití této metody `AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES` musí být nastavena v `m_dwRestartManagerSupportFlags`.   
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Postupy: Přidání podpory správce restartování](../../mfc/how-to-add-restart-manager-support.md)

