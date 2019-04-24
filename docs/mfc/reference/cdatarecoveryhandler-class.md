---
title: CDataRecoveryHandler Class
ms.date: 03/27/2019
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
ms.openlocfilehash: 5c5836a11dbf9e05db5b56e0bc5c062dd1617b2f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62253579"
---
# <a name="cdatarecoveryhandler-class"></a>CDataRecoveryHandler Class

`CDataRecoveryHandler` Automaticky ukládá dokumenty a obnoví je, pokud se aplikace neočekávaně ukončí.

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
|[CDataRecoveryHandler::AutosaveAllDocumentInfo](#autosavealldocumentinfo)|Automaticky ukládá zaregistrovat každý soubor `CDataRecoveryHandler` třídy.|
|[CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo)|Automaticky ukládá zadaný dokument.|
|[CDataRecoveryHandler::CreateDocumentInfo](#createdocumentinfo)|Přidání dokumentu do seznamu otevřených dokumentů.|
|[CDataRecoveryHandler::DeleteAllAutosavedFiles](#deleteallautosavedfiles)|Odstraní všechny aktuální automaticky uložené soubory.|
|[CDataRecoveryHandler::DeleteAutosavedFile](#deleteautosavedfile)|Odstraní soubor zadaný automaticky uložené.|
|[CDataRecoveryHandler::GenerateAutosaveFileName](#generateautosavefilename)|Vygeneruje název pro soubor automatického ukládání přidružený název souboru zadaný dokument.|
|[CDataRecoveryHandler::GetAutosaveInterval](#getautosaveinterval)|Vrátí interval mezi pokusy automatického ukládání.|
|[CDataRecoveryHandler::GetAutosavePath](#getautosavepath)|Vrátí cestu z automaticky uložené soubory.|
|[CDataRecoveryHandler::GetDocumentListName](#getdocumentlistname)|Načte název dokumentu z `CDocument` objektu.|
|[CDataRecoveryHandler::GetNormalDocumentTitle](#getnormaldocumenttitle)|Obnoví normální záhlaví pro zadaný dokument.|
|[CDataRecoveryHandler::GetRecoveredDocumentTitle](#getrecovereddocumenttitle)|Vytvoří a vrátí název obnovené dokumentu.|
|[CDataRecoveryHandler::GetRestartIdentifier](#getrestartidentifier)|Načte restartování jedinečný identifikátor pro aplikaci.|
|[CDataRecoveryHandler::GetSaveDocumentInfoOnIdle](#getsavedocumentinfoonidle)|Určuje, zda `CDataRecoveryHandler` provádí automatické ukládání na aktuální nečinné smyčky.|
|[CDataRecoveryHandler::GetShutdownByRestartManager](#getshutdownbyrestartmanager)|Určuje, zda správce restartování způsobila ukončení aplikace.|
|[CDataRecoveryHandler::Initialize](#initialize)|Inicializuje `CDataRecoveryHandler`.|
|[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments)|Uživateli se zobrazí dialogové okno pro každý odeslaný dokument `CDataRecoveryHandler` automaticky uložené. Dialogové okno určuje, jestli uživatel chce obnovit automaticky uložené dokumentu.|
|[CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist)|Načte seznam otevřít dokument z registru.|
|[CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo)|Odebere zadaný dokument ze seznamu otevřených dokumentů.|
|[CDataRecoveryHandler::ReopenPreviousDocuments](#reopenpreviousdocuments)|Otevře se dřív otevřených dokumentů.|
|[CDataRecoveryHandler::RestoreAutosavedDocuments](#restoreautosaveddocuments)|Obnoví automaticky uložené dokumenty na základě uživatelského zadání.|
|[CDataRecoveryHandler::SaveOpenDocumentList](#saveopendocumentlist)|Uloží aktuální seznam otevřených dokumentů do registru Windows.|
|[CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval)|Nastaví časový interval mezi cykly automatického ukládání v milisekundách.|
|[CDataRecoveryHandler::SetAutosavePath](#setautosavepath)|Nastaví adresář, kde jsou uloženy soubory automaticky uložené.|
|[CDataRecoveryHandler::SetRestartIdentifier](#setrestartidentifier)|Nastaví restartování jedinečný identifikátor pro tuto instanci `CDataRecoveryHandler`.|
|[CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle)|Nastaví, zda `CDataRecoveryHandler` uloží informace o otevřený dokument do registru Windows během aktuální nečinnosti cyklu.|
|[CDataRecoveryHandler::SetShutdownByRestartManager](#setshutdownbyrestartmanager)|Nastaví, zda správce restartování způsobila předchozí ukončení aplikace.|
|[CDataRecoveryHandler::UpdateDocumentInfo](#updatedocumentinfo)|Aktualizuje informace pro dokument, protože uživatel ho uložili.|

### <a name="data-members"></a>Datové členy

|||
|-|-|
|m_bRestoringPreviousOpenDocs|Určuje, zda obslužná rutina pro obnovení dat neotevře dřív otevřených dokumentů.|
|m_bSaveDocumentInfoOnIdle|Určuje, zda automaticky ukládá data recovery obslužná rutina dokumenty na další nečinné smyčky.|
|m_bShutdownByRestartManager|Určuje, zda správce restartování způsobí ukončení aplikace.|
|m_dwRestartManagerSupportFlags|Příznaky, které označují, co podpora restart Manageru poskytuje pro aplikace.|
|m_lstAutosavesToDelete|Seznam automaticky uložené soubory, které nebyly odstraněny při původní dokumenty nebyly uzavřeny. Při ukončení aplikace, opakované pokusy správce restartování, odstraňování souborů.|
|m_mapDocNameToAutosaveName|Mapování názvů dokumentů k názvům souborů automaticky uložené.|
|m_mapDocNameToDocumentPtr|Mapování názvů dokumentů pro [CDocument](../../mfc/reference/cdocument-class.md) ukazatele.|
|m_mapDocNameToRestoreBool|Mapování názvů dokumentů pro parametr logické hodnoty označující, jestli se má obnovit automaticky uložené dokumentu.|
|m_mapDocumentPtrToDocName|Mapa `CDocument` ukazatele na název dokumentu.|
|m_mapDocumentPtrToDocTitle|Mapa `CDocument` ukazatele na názvy dokumentů. Tyto názvy se používají pro ukládání souborů.|
|m_nAutosaveInterval|Doba v milisekundách mezi automaticky ukládá.|
|m_nTimerID|Identifikátor časovače automatického ukládání.|
|m_strAutosavePath|Umístění, kde jsou uložené dokumenty automaticky uložené.|
|m_strRestartIdentifier|Řetězcové vyjádření identifikátoru GUID pro správce restartování.|

## <a name="remarks"></a>Poznámky

Používá správce restartování `CDataRecoveryHandler` třídy zachovat všechny otevřené dokumenty a automatické ukládání je sledují podle potřeby. Pokud chcete povolit automatické ukládání, použijte [CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle) metody. Tato metoda přesměruje `CDataRecoveryHandler` provádět automatické ukládání na další nečinné smyčky. Volá správce restartování `SetSaveDocumentInfoOnIdle` při `CDataRecoveryHandler` měli provést automatické ukládání.

Všechny metody `CDataRecoveryHandler` třídy jsou virtuální. Přepište metody této třídy pro vytvoření vlastní obslužné rutiny vlastních dat obnovení. Pokud vytvoříte vlastní rutinu obnovení dat nebo restartovat správce, nevytvářejte instanci cdatarecoveryhandler –. [CWinApp – třída](../../mfc/reference/cwinapp-class.md) vytvoří `CDataRecoveryHandler` objektů, jako je povinný.

Než budete moct použít `CDataRecoveryHandler` objektu, je nutné volat [CDataRecoveryHandler::Initialize](#initialize).

Protože `CDataRecoveryHandler` třídy úzce připojen správce restartování `CDataRecoveryHandler` závisí na parametru globální `m_dwRestartManagerSupportFlags`. Tento parametr určuje, jaká oprávnění, která má správce restartování a interakci s vaší aplikací. Správce restartování začlenit do existující aplikace, je potřeba přiřadit `m_dwRestartManagerSupportFlags` odpovídající hodnotu v konstruktoru hlavní aplikace. Další informace o tom, jak použít správce restartování najdete v tématu [jak: Přidání podpory správce restartování](../../mfc/how-to-add-restart-manager-support.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdatarecovery.h

##  <a name="autosavealldocumentinfo"></a>  CDataRecoveryHandler::AutosaveAllDocumentInfo

Automaticky ukládá zaregistrovat každý soubor `CDataRecoveryHandler` třídy.

```
virtual BOOL AutosaveAllDocumentInfo();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud `CDataRecoveryHandler` uložit všechny dokumenty; FALSE, pokud dokument nebyl uložen.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí hodnotu PRAVDA, pokud neexistují žádné dokumenty, které musí být uložen. Také vrátí hodnotu TRUE bez uložení všech dokumentů, pokud načítá `CWinApp` nebo `CDocManager` pro aplikace dojde k chybě.

Pokud chcete použít tuto metodu, musí být nastavena AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART nebo AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL v `m_dwRestartManagerSupportFlags`. Další informace najdete v tématu [jak: Přidání podpory správce restartování](../../mfc/how-to-add-restart-manager-support.md).

##  <a name="autosavedocumentinfo"></a>  CDataRecoveryHandler::AutosaveDocumentInfo

Automaticky ukládá zadaný dokument.

```
virtual BOOL AutosaveDocumentInfo(
    CDocument* pDocument,
    BOOL bResetModifiedFlag = TRUE);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*pDocument*|[in] Ukazatel `CDocument` uložte.|
|*bResetModifiedFlag*|[in] Hodnota TRUE znamená, že `CDataRecoveryHandler` bere v úvahu *pDocument* má být upraven; Hodnota FALSE označuje, že bude považovat za rozhraní *pDocument* bude bez úprav. Další informace o účinek tohoto příznaku v části poznámky.|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud jsou nastavené příslušnými příznaky a *pDocument* v platném `CDocument` objektu.

### <a name="remarks"></a>Poznámky

Každý `CDocument` objekt má příznak označující, pokud se změnil od posledního uložení. Použití [CDocument::IsModified](../../mfc/reference/cdocument-class.md#ismodified) k určení stavu tento příznak. Pokud `CDocument` nebyl změněn od posledního uložení `AutosaveDocumentInfo` odstraní všechny soubory automaticky uložené pro tento dokument. Pokud dokument změnila od posledního uložení, jeho uzavřením vyzve uživatele k dokument před zavřením uložit.

> [!NOTE]
>  Pomocí *bResetModifiedFlag* změny stavu dokumentu k verzí bez úprav mohou způsobit, že uživatel ke ztrátě neuložených dat. Pokud rozhraní bere v úvahu dokumentu bez jakýchkoli úprav, jeho uzavřením výzvu uživateli umožňují uložit.

Tato metoda vyvolá výjimku [ASSERT](diagnostic-services.md#assert) – makro Pokud *pDocument* není platným `CDocument` objektu.

Pokud chcete použít tuto metodu, musí být nastavena AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART nebo AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL v *m_dwRestartManagerSupportFlags*.

##  <a name="cdatarecoveryhandler"></a>  CDataRecoveryHandler::CDataRecoveryHandler

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
|*dwRestartManagerSupportFlags*|[in] Určuje, jaké možnosti Správce restartování jsou podporovány.|
|*nAutosaveInterval*|[in] Doba mezi automaticky ukládá. Tento parametr je v milisekundách.|

### <a name="remarks"></a>Poznámky

Rozhraní MFC framework automaticky vytvoří `CDataRecoveryHandler` objekt pro vaši aplikaci při použití **nový projekt** průvodce. Pokud se přizpůsobení chování obnovení dat nebo správce restartování, nevytvářejte `CDataRecoveryHandler` objektu.

##  <a name="createdocumentinfo"></a>  CDataRecoveryHandler::CreateDocumentInfo

Přidání dokumentu do seznamu otevřených dokumentů.

```
virtual BOOL CreateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*pDocument*|[in] Ukazatel `CDocument`. Tato metoda vytvoří dokument informace pro tento `CDocument`.|

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrací hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Tato metoda ověří, zda *pDocument* je již v seznamu dokumentů před přidáním dokumentu. Pokud *pDocument* je již v seznamu, tato metoda odstraní přidružené k souboru automaticky uložené *pDocument*.

Pokud chcete použít tuto metodu, musí být nastavena AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART nebo AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL v *m_dwRestartManagerSupportFlags*.

##  <a name="deleteallautosavedfiles"></a>  CDataRecoveryHandler::DeleteAllAutosavedFiles

Odstraní všechny aktuální automaticky uložené soubory.

```
virtual BOOL DeleteAllAutosavedFiles();
```

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vždy vrátí hodnotu TRUE.

##  <a name="deleteautosavedfile"></a>  CDataRecoveryHandler::DeleteAutosavedFile

Odstraní soubor zadaný automaticky uložené.

```
virtual BOOL DeleteAutosavedFile(const CString& strAutosavedFile);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*strAutosavedFile*|[in] Řetězec, který obsahuje název souboru automaticky uložené.|

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vždy vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Pokud tuto metodu nelze odstranit soubor automaticky uložené, uloží název souboru v seznamu. Destruktor `CDataRecoveryHandler` pokusí odstranit každý soubor automaticky uložené v tomto seznamu uvedené.

##  <a name="generateautosavefilename"></a>  CDataRecoveryHandler::GenerateAutosaveFileName

Vygeneruje název pro soubor automatického ukládání přidružený název souboru zadaný dokument.

```
virtual CString GenerateAutosaveFileName(const CString& strDocumentName) const;
```

### <a name="parameters"></a>Parametry

*strDocumentName*<br/>
[in] Řetězec, který obsahuje název dokumentu. `GenerateAutosaveFileName` název tohoto dokumentu se používá ke generování odpovídající název souboru automatického ukládání.

### <a name="return-value"></a>Návratová hodnota

Název souboru automatického ukládání generovaných *strDocumentName*.

### <a name="remarks"></a>Poznámky

Každý název dokumentu obsahuje mapování 1: 1 s názvem souboru automatického ukládání.

##  <a name="getautosaveinterval"></a>  CDataRecoveryHandler::GetAutosaveInterval

Vrátí interval mezi pokusy automatického ukládání.

```
virtual int GetAutosaveInterval() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet milisekund mezi automatického ukládání pokusí.

##  <a name="getautosavepath"></a>  CDataRecoveryHandler::GetAutosavePath

Vrátí cestu z automaticky uložené soubory.

```
virtual CString GetAutosavePath() const;
```

### <a name="return-value"></a>Návratová hodnota

Umístění, kde jsou uložené dokumenty automaticky uložené.

##  <a name="getdocumentlistname"></a>  CDataRecoveryHandler::GetDocumentListName

Načte název dokumentu z `CDocument` objektu.

```
virtual CString GetDocumentListName(CDocument* pDocument) const;
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*pDocument*|[in] Ukazatel `CDocument`. `GetDocumentListName` načte název dokumentu z tohoto `CDocument`.|

### <a name="return-value"></a>Návratová hodnota

Název dokumentu z *pDocument*.

### <a name="remarks"></a>Poznámky

`CDataRecoveryHandler` Použije název dokumentu jako klíč v *m_mapDocNameToAutosaveName*, *m_mapDocNameToDocumentPtr*, a *m_mapDocNameToRestoreBool*. Povolení těchto parametrů `CDataRecoveryHandler` monitorování `CDocument` objekty, název souboru automatického ukládání a automatického ukládání nastavení.

##  <a name="getnormaldocumenttitle"></a>  CDataRecoveryHandler::GetNormalDocumentTitle

Obnoví normální záhlaví pro zadaný dokument.

```
virtual CString GetNormalDocumentTitle(CDocument* pDocument);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*pDocument*|[in] Ukazatel `CDocument`.|

### <a name="return-value"></a>Návratová hodnota

Normální záhlaví pro zadaný dokument.

### <a name="remarks"></a>Poznámky

Normální záhlaví dokumentu je obvykle název souboru dokumentu bez cesty. Toto je název v **název_souboru** pole **uložit jako** dialogové okno.

##  <a name="getrecovereddocumenttitle"></a>  CDataRecoveryHandler::GetRecoveredDocumentTitle

Vytvoří a vrátí název obnovené dokumentu.

```
virtual CString GetRecoveredDocumentTitle(const CString& strDocumentTitle) const;
```

### <a name="parameters"></a>Parametry

*strDocumentTitle*<br/>
[in] Normální záhlaví pro dokument.

### <a name="return-value"></a>Návratová hodnota

Název obnovené dokumentu.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení, obnovené název dokumentu je normální záhlaví s **[Obnoveno]** připojí k němu. Název obnovené se zobrazí uživateli při `CDataRecoveryHandler` dotazuje uživateli obnovit automaticky uložené dokumenty.

##  <a name="getrestartidentifier"></a>  CDataRecoveryHandler::GetRestartIdentifier

Načte restartování jedinečný identifikátor pro aplikaci.

```
virtual CString GetRestartIdentifier() const;
```

### <a name="return-value"></a>Návratová hodnota

Restartování jedinečný identifikátor.

### <a name="remarks"></a>Poznámky

Identifikátor restartování je jedinečný pro každé spuštění aplikace.

`CDataRecoveryHandler` Ukládá informace v registru o aktuálně otevřených dokumentů. Když správce restartování aplikace se ukončí a restartuje ho, poskytne restartování identifikátor, který `CDataRecoveryHandler`. `CDataRecoveryHandler` Používá identifikátor restartování k načtení seznamu dřív otevřených dokumentů. Díky tomu `CDataRecoveryHandler` pokusí najít a automaticky uložené soubory obnovit.

##  <a name="getsavedocumentinfoonidle"></a>  CDataRecoveryHandler::GetSaveDocumentInfoOnIdle

Určuje, zda `CDataRecoveryHandler` provádí automatické ukládání na aktuální nečinné smyčky.

```
virtual BOOL GetSaveDocumentInfoOnIdle() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE označuje, `CDataRecoveryHandler` automaticky ukládá na aktuální nečinné smyčky Hodnota FALSE označuje, že tomu tak není.

##  <a name="getshutdownbyrestartmanager"></a>  CDataRecoveryHandler::GetShutdownByRestartManager

Určuje, zda správce restartování způsobila ukončení aplikace.

```
virtual BOOL GetShutdownByRestartManager() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE označuje, že správce restartování způsob ukončení; aplikace Hodnota FALSE označuje, že tomu tak není.

##  <a name="initialize"></a>  CDataRecoveryHandler::Initialize

Inicializuje `CDataRecoveryHandler`.

```
virtual BOOL Initialize();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud se inicializace je úspěšná. v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Proces inicializace načte cestu pro ukládání automatického ukládání souborů z registru. Pokud `Initialize` metoda nemůže najít tento adresář nebo pokud se cesta je NULL, `Initialize` selže a vrátí `FALSE`.

Použití [CDataRecoveryHandler::SetAutosavePath](#setautosavepath) změňte cestu k automatické ukládání po vaše aplikace inicializuje `CDataRecoveryHandler`.

`Initialize` Metoda také spustí časovač monitorování, když dojde k dalším automatického ukládání. Použití [CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval) interval automatického ukládání změnit poté, co vaše aplikace inicializuje `CDataRecoveryHandler`.

##  <a name="queryrestoreautosaveddocuments"></a>  CDataRecoveryHandler::QueryRestoreAutosavedDocuments

Uživateli se zobrazí dialogové okno pro každý odeslaný dokument `CDataRecoveryHandler` automaticky uložené. Dialogové okno určuje, jestli uživatel chce obnovit automaticky uložené dokumentu.

```
virtual void QueryRestoreAutosavedDocuments();
```

### <a name="remarks"></a>Poznámky

Pokud je vaše aplikace kódování Unicode, tato metoda zobrazí [CTaskDialog](../../mfc/reference/ctaskdialog-class.md) uživateli. V opačném případě rozhraní používá [AfxMessageBox](../../mfc/reference/cstring-formatting-and-message-box-display.md#afxmessagebox) k dotazování uživatele.

Po `QueryRestoreAutosavedDocuments` shromáždí všechny odpovědi od uživatele, uloží informace do členské proměnné *m_mapDocNameToRestoreBool*. Tato metoda neobnovuje automaticky uložené dokumenty.

##  <a name="readopendocumentlist"></a>  CDataRecoveryHandler::ReadOpenDocumentList

Načte seznam otevřít dokument z registru.

```
virtual BOOL ReadOpenDocumentList();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE znamená, že `ReadOpenDocumentList` načíst informace pro minimálně jeden dokument z registru. Hodnota FALSE označuje, že byl načten žádné informace o dokumentu.

### <a name="remarks"></a>Poznámky

Tato funkce načítá informace otevřít dokument z registru a uloží jej v členské proměnné *m_mapDocNameToAutosaveName*.

Po `ReadOpenDocumentList` načte všechna data, odstraní informace o dokumentu z registru.

##  <a name="removedocumentinfo"></a>  CDataRecoveryHandler::RemoveDocumentInfo

Odebere zadaný dokument ze seznamu otevřených dokumentů.

```
virtual BOOL RemoveDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*pDocument*|[in] Ukazatel na dokument, který chcete odebrat.|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE v případě *pDocument* byl odebrán ze seznamu. FALSE, pokud došlo k chybě.

### <a name="remarks"></a>Poznámky

Při zavření dokumentu, rozhraní používá tato metoda se odebrat ze seznamu otevřených dokumentů.

Pokud `RemoveDocumentInfo` nejde najít *pDocument* v seznamu otevřených dokumentů nemá žádný účinek a vrátí hodnotu TRUE.

Pokud chcete použít tuto metodu, musí být nastavena v AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES *m_dwRestartManagerSupportFlags*.

##  <a name="reopenpreviousdocuments"></a>  CDataRecoveryHandler::ReopenPreviousDocuments

Otevře se dřív otevřených dokumentů.

```
virtual BOOL ReopenPreviousDocuments();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud byl jeden dokument otevřen; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda se otevře poslední uložit dřív otevřených dokumentů. Pokud dokument nebyl uložen nebo automaticky uložené, `ReopenPreviousDocuments` otevře prázdný dokument založený na šabloně pro daný typ souboru.

Pokud chcete použít tuto metodu, musí být nastavena v AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES *m_dwRestartManagerSupportFlags*. Pokud tento parametr není nastaven, `ReopenPreviousDocuments` neprovede žádnou akci a vrátí hodnotu FALSE.

Pokud neexistují žádné dokumenty uložené v seznamu dřív otevřených dokumentů `ReopenPreviousDocuments` neprovede žádnou akci a vrátí hodnotu FALSE.

##  <a name="restoreautosaveddocuments"></a>  CDataRecoveryHandler::RestoreAutosavedDocuments

Obnoví automaticky uložené dokumenty na základě uživatelského zadání.

```
virtual BOOL RestoreAutosavedDocuments();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud metoda úspěšně obnoví dokumenty.

### <a name="remarks"></a>Poznámky

Tato metoda volá [CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments) k určení, které dokumenty uživatel chce obnovit. Pokud se uživatel rozhodne obnovení dokumentu automaticky uložené `RestoreAutosavedDocuments` odstraní soubor automatického ukládání. V opačném případě `RestoreAutosavedDocuments` nahradí dokument otevřít automaticky uložené verze.

Pokud chcete použít tuto metodu, musí být nastavena AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES nebo AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES v `m_dwRestartManagerSupportFlags`.

##  <a name="saveopendocumentlist"></a>  CDataRecoveryHandler::SaveOpenDocumentList

Uloží aktuální seznam otevřených dokumentů do registru Windows.

```
virtual BOOL SaveOpenDocumentList();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud neexistují žádné otevřené dokumenty, chcete-li uložit nebo pokud se úspěšně uložily. FALSE, pokud jsou dokumenty, chcete-li uložit do registru, ale nebyly uloženy, protože došlo k chybě.

### <a name="remarks"></a>Poznámky

Volá správce restartování `SaveOpenDocumentList` když se aplikace neočekávaně ukončí, nebo když opustí pro upgrade. Když se aplikace restartuje, používá [CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist) načíst seznam otevřených dokumentů.

Tato metoda šetří seznam otevřených dokumentů. Metoda [CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo) zodpovídá za uložení samotných dokumentech.

##  <a name="setautosaveinterval"></a>  CDataRecoveryHandler::SetAutosaveInterval

Nastaví časový interval mezi cykly automatického ukládání v milisekundách.

```
Virtual void SetAutosaveInterval(int nAutosaveInterval);
```

### <a name="parameters"></a>Parametry

*nAutosaveInterval*<br/>
[in] Nové automatické ukládání interval v milisekundách.

##  <a name="setautosavepath"></a>  CDataRecoveryHandler::SetAutosavePath

Nastaví adresář, kde jsou uloženy soubory automaticky uložené.

```
virtual void SetAutosavePath(const CString& strAutosavePath);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*strAutosavePath*|[in] Cesta kde jsou uloženy soubory automatického ukládání.|

### <a name="remarks"></a>Poznámky

Změna adresáře automatického ukládání nepřesouvá aktuálně automaticky uložené soubory.

##  <a name="setrestartidentifier"></a>  CDataRecoveryHandler::SetRestartIdentifier

Nastaví restartování jedinečný identifikátor pro tuto instanci `CDataRecoveryHandler`.

```
virtual void SetRestartIdentifier(const CString& strRestartIdentifier);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*strRestartIdentifier*|[in] Jedinečný identifikátor pro správce restartování.|

### <a name="remarks"></a>Poznámky

Správce restartování zaznamenává informace o otevřených dokumentů v registru. Tyto informace se ukládají s restartování jedinečný identifikátor jako klíč. Protože identifikátor restartování je jedinečný pro každou instanci aplikace, více instancí aplikace může neočekávaně ukončena a správce restartování můžete obnovit každý z nich.

##  <a name="setsavedocumentinfoonidle"></a>  CDataRecoveryHandler::SetSaveDocumentInfoOnIdle

Nastaví, zda `CDataRecoveryHandler` uloží informace o otevřený dokument do registru Windows během aktuální nečinnosti cyklu.

```
virtual void SetSaveDocumentInfoOnIdle(BOOL bSaveOnIdle);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*bSaveOnIdle*|[in] TRUE, pokud chcete uložit informace o dokumentu během aktuální nečinnosti cyklu; FALSE, nebude se provádět uložení.|

##  <a name="setshutdownbyrestartmanager"></a>  CDataRecoveryHandler::SetShutdownByRestartManager

Nastaví, zda správce restartování způsobila předchozí ukončení aplikace.

```
virtual void SetShutdownByRestartManager(BOOL bShutdownByRestartManager);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*bShutdownByRestartManager*|[in] Hodnota TRUE označuje, že správce restartování způsobila ukončení; aplikace FALSE označuje, že aplikace byla ukončena z nějakého jiného důvodu.|

### <a name="remarks"></a>Poznámky

Rozhraní se chová různě v závislosti na Určuje, zda nebyl očekáván předchozí ukončení nebo zda byl inicializován nástrojem Správce restartování.

##  <a name="updatedocumentinfo"></a>  CDataRecoveryHandler::UpdateDocumentInfo

Aktualizuje informace pro dokument, protože uživatel ho uložili.

```
virtual BOOL UpdateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*pDocument*|[in] Ukazatel na uložený dokument.|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda odstraní automaticky uložené dokumentu a aktualizované informace o dokumentu; FALSE, pokud došlo k chybě.

### <a name="remarks"></a>Poznámky

Když uživatel uloží dokument, aplikace odebere soubor automaticky uložené, protože už je nepotřebujete. `UpdateDocumentInfo` Odstraní soubor automaticky uložené voláním [CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo). `UpdateDocumentInfo` Přidá informace z *pDocument* do seznamu aktuálně otevřené dokumenty protože `RemoveDocumentInfo` odstraní informace, ale uložené dokument je stále otevřen.

Pokud chcete použít tuto metodu, musí být nastavena v AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES *m_dwRestartManagerSupportFlags*.

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Postupy: Přidání podpory správce restartování](../../mfc/how-to-add-restart-manager-support.md)
