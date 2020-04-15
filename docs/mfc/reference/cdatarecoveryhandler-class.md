---
title: CDataRecoveryHandler – třída
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
ms.openlocfilehash: bdfcbea6c345235358384691388afcdbbd2d0a42
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321935"
---
# <a name="cdatarecoveryhandler-class"></a>CDataRecoveryHandler – třída

Automaticky `CDataRecoveryHandler` uloží dokumenty a obnoví je, pokud aplikace neočekávaně ukončí.

## <a name="syntax"></a>Syntaxe

```
class CDataRecoveryHandler : public CObject
```

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[CDataRecoveryHandler::CDataRecoveryHandler CDataRecoveryHandler CDataRecoveryHandler CDataRecoveryHandler CDataRecoveryHandler CDataRecoveryHandler::](#cdatarecoveryhandler)|Vytvoří `CDataRecoveryHandler` objekt.|

### <a name="methods"></a>Metody

|||
|-|-|
|[CDataRecoveryHandler::Automatické uloženíAllDocumentInfo](#autosavealldocumentinfo)|Automaticky uloží každý soubor `CDataRecoveryHandler` registrovaný ve třídě.|
|[CDataRecoveryHandler::Automatické uloženídokumentuInfo](#autosavedocumentinfo)|Automaticky uloží zadaný dokument.|
|[CDataRecoveryHandler::CreateDocumentInfo](#createdocumentinfo)|Přidá dokument do seznamu otevřených dokumentů.|
|[CDataRecoveryHandler::DeleteAllAutosavedFiles](#deleteallautosavedfiles)|Odstraní všechny aktuální automaticky uložené soubory.|
|[CDataRecoveryHandler::DeleteAutosavedFile](#deleteautosavedfile)|Odstraní zadaný automaticky uložený soubor.|
|[CDataRecoveryHandler::GenerateAutosaveFileName](#generateautosavefilename)|Generuje název souboru automatického ukládání přidruženého k zadanému názvu souboru dokumentu.|
|[CDataRecoveryHandler::GetAutosaveInterval](#getautosaveinterval)|Vrátí interval mezi pokusy o automatické ukládání.|
|[CDataRecoveryHandler::GetAutosavePath](#getautosavepath)|Vrátí cestu k automaticky uloženým souborům.|
|[CDataRecoveryHandler::GetDocumentListName](#getdocumentlistname)|Načte název dokumentu `CDocument` z objektu.|
|[CDataRecoveryHandler::GetNormalDocumentTitle](#getnormaldocumenttitle)|Načte normální název pro zadaný dokument.|
|[CDataRecoveryHandler::GetRecoveredDocumentTitle](#getrecovereddocumenttitle)|Vytvoří a vrátí název obnoveného dokumentu.|
|[CDataRecoveryHandler::GetRestartIdentifier](#getrestartidentifier)|Načte jedinečný identifikátor restartování aplikace.|
|[CDataRecoveryHandler::getSaveDocumentInfoOnIdle](#getsavedocumentinfoonidle)|Označuje, `CDataRecoveryHandler` zda provádí automatické ukládání na aktuální nečinnosti smyčky.|
|[CDataRecoveryHandler::GetShutdownByRestartManager](#getshutdownbyrestartmanager)|Označuje, zda správce restartování způsobil ukončení aplikace.|
|[CDataRecoveryHandler::Inicializovat](#initialize)|Inicializuje `CDataRecoveryHandler`.|
|[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments)|Zobrazí uživateli dialogové okno pro každý `CDataRecoveryHandler` dokument, který byl automaticky uložen. Dialogové okno určuje, zda chce uživatel obnovit automaticky uložený dokument.|
|[CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist)|Načte otevřený seznam dokumentů z registru.|
|[CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo)|Odebere dodaný dokument ze seznamu otevřených dokumentů.|
|[CDataRecoveryHandler::Znovu otevřítpředchozí dokumenty](#reopenpreviousdocuments)|Otevře dříve otevřené dokumenty.|
|[CDataRecoveryHandler::Obnovitautomaticky uložené dokumenty](#restoreautosaveddocuments)|Obnoví automaticky uložené dokumenty na základě vstupu uživatele.|
|[CDataRecoveryHandler::UložitOpenDocumentList](#saveopendocumentlist)|Uloží aktuální seznam otevřených dokumentů do registru systému Windows.|
|[CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval)|Nastaví čas mezi cykly automatického ukládání v milisekundách.|
|[CDataRecoveryHandler::SetAutosavePath](#setautosavepath)|Nastaví adresář, ve kterém jsou uloženy automaticky uložené soubory.|
|[CDataRecoveryHandler::SetRestartIdentifier](#setrestartidentifier)|Nastaví jedinečný identifikátor restartování pro `CDataRecoveryHandler`tuto instanci .|
|[cDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle)|Nastaví, `CDataRecoveryHandler` zda uloží informace o otevřeném dokumentu do registru systému Windows během aktuálního cyklu nečinnosti.|
|[CDataRecoveryHandler::SetShutdownByRestartManager](#setshutdownbyrestartmanager)|Nastaví, zda předchozí ukončení aplikace bylo způsobeno správcem restartování.|
|[CDataRecoveryHandler::UpdateDocumentInfo](#updatedocumentinfo)|Aktualizuje informace o dokumentu, protože jej uživatel uložil.|

### <a name="data-members"></a>Členové dat

|||
|-|-|
|m_bRestoringPreviousOpenDocs|Označuje, zda obslužná rutina obnovení dat znovu otevře dříve otevřené dokumenty.|
|m_bSaveDocumentInfoOnIdle|Označuje, zda obslužná rutina obnovení dat automaticky ukládá dokumenty na další nečinné smyčky.|
|m_bShutdownByRestartManager|Označuje, zda správce restartování způsobí ukončení aplikace.|
|m_dwRestartManagerSupportFlags|Příznaky, které označují, jakou podporu poskytuje správce restartování pro aplikaci.|
|m_lstAutosavesToDelete|Seznam automaticky uložených souborů, které nebyly odstraněny při zavření původních dokumentů. Po ukončení aplikace se pokusí správce restartování soubory znovu odstranit.|
|m_mapDocNameToAutosaveName|Mapa názvů dokumentů k automaticky uloženým názvům souborů.|
|m_mapDocNameToDocumentPtr|Mapa názvů dokumentů na ukazatele [CDocument.](../../mfc/reference/cdocument-class.md)|
|m_mapDocNameToRestoreBool|Mapa názvů dokumentů na logický parametr, která označuje, zda má být automaticky uložený dokument obnoven.|
|m_mapDocumentPtrToDocName|Mapa ukazatelů `CDocument` na názvy dokumentů.|
|m_mapDocumentPtrToDocTitle|Mapa ukazatelů `CDocument` na názvy dokumentů. Tyto názvy se používají pro ukládání souborů.|
|m_nAutosaveInterval|Čas v milisekundách mezi automatickým ukládáním.|
|m_nTimerID|Identifikátor časovače automatického ukládání.|
|m_strAutosavePath|Umístění, kde jsou uloženy automaticky uložené dokumenty.|
|m_strRestartIdentifier|Řetězcová reprezentace identifikátoru GUID pro správce restartování.|

## <a name="remarks"></a>Poznámky

Správce restartování používá `CDataRecoveryHandler` třídu ke sledování všech otevřených dokumentů a k jejich automatickému uložení podle potřeby. Chcete-li povolit automatické ukládání, použijte metodu [CDataRecoveryHandler::SetSaveDocumentInfoOnIdle.](#setsavedocumentinfoonidle) Tato metoda nasměruje `CDataRecoveryHandler` provést automatické uložení na další nečinnosti smyčky. Správce restartování `SetSaveDocumentInfoOnIdle` volá, `CDataRecoveryHandler` když by měl provést automatické ukládání.

Všechny metody třídy `CDataRecoveryHandler` jsou virtuální. Přepsat metody v této třídě vytvořit vlastní obslužnou rutinu obnovení dat. Pokud nevytvoříte vlastní obslužnou rutinu pro obnovení dat nebo správce restartování, nevytvářejte instance CDataRecoveryHandler. [Třída CWinApp](../../mfc/reference/cwinapp-class.md) vytvoří `CDataRecoveryHandler` objekt podle potřeby.

Před použitím objektu `CDataRecoveryHandler` je nutné zavolat [CDataRecoveryHandler::Initialize](#initialize).

Vzhledem `CDataRecoveryHandler` k tomu, že třída `CDataRecoveryHandler` je úzce `m_dwRestartManagerSupportFlags`spojena s správce mj. Tento parametr určuje, jaká oprávnění má správce restartování a jak bude pracovat s vaší aplikací. Chcete-li začlenit správce restartování do existující `m_dwRestartManagerSupportFlags` aplikace, musíte přiřadit příslušnou hodnotu v konstruktoru hlavní aplikace. Další informace o použití správce restartování naleznete v [tématu Postup: Přidání podpory správce restartování](../../mfc/how-to-add-restart-manager-support.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdatarecovery.h

## <a name="cdatarecoveryhandlerautosavealldocumentinfo"></a><a name="autosavealldocumentinfo"></a>CDataRecoveryHandler::Automatické uloženíAllDocumentInfo

Automaticky uloží každý soubor `CDataRecoveryHandler` registrovaný ve třídě.

```
virtual BOOL AutosaveAllDocumentInfo();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, `CDataRecoveryHandler` pokud jsou uloženy všechny dokumenty; Nepravda, pokud nebyl některý dokument uložen.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí hodnotu PRAVDA, pokud neexistují žádné dokumenty, které musí být uloženy. Vrátí také hodnotu TRUE bez uložení `CWinApp` `CDocManager` dokumentů, pokud načítání nebo pro aplikaci generuje chybu.

Chcete-li použít tuto metodu, AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL `m_dwRestartManagerSupportFlags`AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART musí být v . Další informace naleznete v [tématu How to: Add Restart Manager Support](../../mfc/how-to-add-restart-manager-support.md).

## <a name="cdatarecoveryhandlerautosavedocumentinfo"></a><a name="autosavedocumentinfo"></a>CDataRecoveryHandler::Automatické uloženídokumentuInfo

Automaticky uloží zadaný dokument.

```
virtual BOOL AutosaveDocumentInfo(
    CDocument* pDocument,
    BOOL bResetModifiedFlag = TRUE);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*pDokument*|[v] Ukazatel na `CDocument` uložit.|
|*bResetModifiedFlag*|[v] TRUE označuje, `CDataRecoveryHandler` že považuje *pDocument* změnit; FALSE označuje, že rozhraní považuje *pDocument* za nezměněné. Další informace o účinku tohoto příznaku naleznete v části Poznámky.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud jsou nastaveny příslušné příznaky `CDocument` a *pDocument* je platný objekt.

### <a name="remarks"></a>Poznámky

Každý `CDocument` objekt má příznak, který označuje, zda se změnil od posledního uložení. Použijte [CDocument::IsModified](../../mfc/reference/cdocument-class.md#ismodified) k určení stavu tohoto příznaku. Pokud `CDocument` se a od posledního `AutosaveDocumentInfo` uložení nezměnila, odstraní všechny automaticky uložené soubory pro tento dokument. Pokud se dokument od posledního uložení změnil, jeho zavření vyzve uživatele k uložení dokumentu před zavřením.

> [!NOTE]
> Použití *bResetModifiedFlag* změnit stav dokumentu na nezměněné může způsobit, že uživatel ztratí neuložená data. Pokud rozhraní považuje dokument za nezměněný, jeho zavření nevyzve uživatele k uložení.

Tato metoda vyvolá výjimku s makro [ASSERT,](diagnostic-services.md#assert) pokud `CDocument` *pDocument* není platný objekt.

Chcete-li použít tuto metodu, musí být AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART nebo AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL nastaveny v *m_dwRestartManagerSupportFlags*.

## <a name="cdatarecoveryhandlercdatarecoveryhandler"></a><a name="cdatarecoveryhandler"></a>CDataRecoveryHandler::CDataRecoveryHandler CDataRecoveryHandler CDataRecoveryHandler CDataRecoveryHandler CDataRecoveryHandler CDataRecoveryHandler::

Vytvoří `CDataRecoveryHandler` objekt.

```
CDataRecoveryHandler(
    DWORD dwRestartManagerSupportFlags,
    int nAutosaveInterval);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*dwRestartManagerSupportFlags*|[v] Označuje, které možnosti správce restartování jsou podporovány.|
|*nInterval automatického ukládání*|[v] Doba mezi automatickým ukládáním. Tento parametr je v milisekundách.|

### <a name="remarks"></a>Poznámky

Rozhraní knihovny MFC `CDataRecoveryHandler` automaticky vytvoří objekt pro vaši aplikaci při použití průvodce **nový projekt.** Pokud nepřizpůsobíte chování pro obnovení dat nebo správce `CDataRecoveryHandler` restartování, neměli byste vytvářet objekt.

## <a name="cdatarecoveryhandlercreatedocumentinfo"></a><a name="createdocumentinfo"></a>CDataRecoveryHandler::CreateDocumentInfo

Přidá dokument do seznamu otevřených dokumentů.

```
virtual BOOL CreateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*pDokument*|[v] Ukazatel na `CDocument`. Tato metoda vytvoří informace `CDocument`o dokumentu pro tento .|

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí hodnotu PRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda zkontroluje, zda *pDocument* je již v seznamu dokumentů před přidáním dokumentu. Pokud *je pDocument* již v seznamu, tato metoda odstraní automaticky uložený soubor přidružený k *pDocument*.

Chcete-li použít tuto metodu, musí být AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART nebo AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL nastaveny v *m_dwRestartManagerSupportFlags*.

## <a name="cdatarecoveryhandlerdeleteallautosavedfiles"></a><a name="deleteallautosavedfiles"></a>CDataRecoveryHandler::DeleteAllAutosavedFiles

Odstraní všechny aktuální automaticky uložené soubory.

```
virtual BOOL DeleteAllAutosavedFiles();
```

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vždy vrátí hodnotu PRAVDA.

## <a name="cdatarecoveryhandlerdeleteautosavedfile"></a><a name="deleteautosavedfile"></a>CDataRecoveryHandler::DeleteAutosavedFile

Odstraní zadaný automaticky uložený soubor.

```
virtual BOOL DeleteAutosavedFile(const CString& strAutosavedFile);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*StrAutosavedFile*|[v] Řetězec obsahující název automaticky uloženého souboru.|

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vždy vrátí hodnotu PRAVDA.

### <a name="remarks"></a>Poznámky

Pokud tato metoda nemůže odstranit automaticky uložený soubor, uloží název souboru do seznamu. Destruktor pro `CDataRecoveryHandler` pokusy o odstranění každého automaticky uloženého souboru zadaného v tomto seznamu.

## <a name="cdatarecoveryhandlergenerateautosavefilename"></a><a name="generateautosavefilename"></a>CDataRecoveryHandler::GenerateAutosaveFileName

Generuje název souboru automatického ukládání přidruženého k zadanému názvu souboru dokumentu.

```
virtual CString GenerateAutosaveFileName(const CString& strDocumentName) const;
```

### <a name="parameters"></a>Parametry

*strDocumentName*<br/>
[v] Řetězec, který obsahuje název dokumentu. `GenerateAutosaveFileName`Tento název dokumentu použije ke generování odpovídajícího názvu souboru automatického ukládání.

### <a name="return-value"></a>Návratová hodnota

Název souboru automatického ukládání generovaný z *funkce strDocumentName*.

### <a name="remarks"></a>Poznámky

Každý název dokumentu má mapování 1:1 s názvem souboru automatického ukládání.

## <a name="cdatarecoveryhandlergetautosaveinterval"></a><a name="getautosaveinterval"></a>CDataRecoveryHandler::GetAutosaveInterval

Vrátí interval mezi pokusy o automatické ukládání.

```
virtual int GetAutosaveInterval() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet milisekund mezi pokusy o automatické ukládání.

## <a name="cdatarecoveryhandlergetautosavepath"></a><a name="getautosavepath"></a>CDataRecoveryHandler::GetAutosavePath

Vrátí cestu k automaticky uloženým souborům.

```
virtual CString GetAutosavePath() const;
```

### <a name="return-value"></a>Návratová hodnota

Umístění, kde jsou uloženy automaticky uložené dokumenty.

## <a name="cdatarecoveryhandlergetdocumentlistname"></a><a name="getdocumentlistname"></a>CDataRecoveryHandler::GetDocumentListName

Načte název dokumentu `CDocument` z objektu.

```
virtual CString GetDocumentListName(CDocument* pDocument) const;
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*pDokument*|[v] Ukazatel na `CDocument`. `GetDocumentListName`načte název dokumentu `CDocument`z tohoto .|

### <a name="return-value"></a>Návratová hodnota

Název dokumentu z *pDocument*.

### <a name="remarks"></a>Poznámky

Název `CDataRecoveryHandler` dokumentu používá jako klíč v *m_mapDocNameToAutosaveName*, *m_mapDocNameToDocumentPtr*a *m_mapDocNameToRestoreBool*. Tyto parametry `CDataRecoveryHandler` umožňují `CDocument` sledovat objekty, název souboru automatického ukládání a nastavení automatického ukládání.

## <a name="cdatarecoveryhandlergetnormaldocumenttitle"></a><a name="getnormaldocumenttitle"></a>CDataRecoveryHandler::GetNormalDocumentTitle

Načte normální název pro zadaný dokument.

```
virtual CString GetNormalDocumentTitle(CDocument* pDocument);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*pDokument*|[v] Ukazatel na `CDocument`.|

### <a name="return-value"></a>Návratová hodnota

Normální název pro zadaný dokument.

### <a name="remarks"></a>Poznámky

Normální název dokumentu je obvykle název souboru dokumentu bez cesty. Toto je název v poli **Název souboru** dialogového okna **Uložit jako.**

## <a name="cdatarecoveryhandlergetrecovereddocumenttitle"></a><a name="getrecovereddocumenttitle"></a>CDataRecoveryHandler::GetRecoveredDocumentTitle

Vytvoří a vrátí název obnoveného dokumentu.

```
virtual CString GetRecoveredDocumentTitle(const CString& strDocumentTitle) const;
```

### <a name="parameters"></a>Parametry

*strDocumentTitle*<br/>
[v] Normální název dokumentu.

### <a name="return-value"></a>Návratová hodnota

Obnovený název dokumentu.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení je obnovený název dokumentu normálním názvem s **připojeným [obnoveným]** k němu. Obnovený název se zobrazí uživateli, `CDataRecoveryHandler` když se uživatel i na dotaz uchýlil k obnovení automaticky uložených dokumentů.

## <a name="cdatarecoveryhandlergetrestartidentifier"></a><a name="getrestartidentifier"></a>CDataRecoveryHandler::GetRestartIdentifier

Načte jedinečný identifikátor restartování aplikace.

```
virtual CString GetRestartIdentifier() const;
```

### <a name="return-value"></a>Návratová hodnota

Jedinečný identifikátor restartování.

### <a name="remarks"></a>Poznámky

Identifikátor restartování je jedinečný pro každé spuštění aplikace.

Ukládá `CDataRecoveryHandler` informace v registru o aktuálně otevřených dokumentech. Když správce restartování ukončí aplikaci a restartuje ji, dodá identifikátor restartu do . `CDataRecoveryHandler` Identifikátor `CDataRecoveryHandler` restartování používá k načtení seznamu dříve otevřených dokumentů. To umožňuje `CDataRecoveryHandler` pokusit se najít a obnovit automaticky uložené soubory.

## <a name="cdatarecoveryhandlergetsavedocumentinfoonidle"></a><a name="getsavedocumentinfoonidle"></a>CDataRecoveryHandler::getSaveDocumentInfoOnIdle

Označuje, `CDataRecoveryHandler` zda provádí automatické ukládání na aktuální nečinnosti smyčky.

```
virtual BOOL GetSaveDocumentInfoOnIdle() const;
```

### <a name="return-value"></a>Návratová hodnota

True označuje `CDataRecoveryHandler` automatické ukládání na aktuální nečinnosti smyčky; FALSE označuje, že tomu tak není.

## <a name="cdatarecoveryhandlergetshutdownbyrestartmanager"></a><a name="getshutdownbyrestartmanager"></a>CDataRecoveryHandler::GetShutdownByRestartManager

Označuje, zda správce restartování způsobil ukončení aplikace.

```
virtual BOOL GetShutdownByRestartManager() const;
```

### <a name="return-value"></a>Návratová hodnota

True označuje, že správce restartování způsobil ukončení aplikace. FALSE označuje, že tomu tak nebylo.

## <a name="cdatarecoveryhandlerinitialize"></a><a name="initialize"></a>CDataRecoveryHandler::Inicializovat

Inicializuje `CDataRecoveryHandler`.

```
virtual BOOL Initialize();
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je inicializace úspěšná; jinak FALSE.

### <a name="remarks"></a>Poznámky

Proces inicializace načte cestu pro ukládání automaticky uložených souborů z registru. Pokud `Initialize` metoda nemůže najít tento adresář nebo `Initialize` pokud je `FALSE`cesta null, selže a vrátí .

Pomocí [cdatarecoveryhandleru::SetAutosavePath](#setautosavepath) změňte cestu automatického ukládání po `CDataRecoveryHandler`inicializaci aplikace .

Metoda `Initialize` také spustí časovač pro sledování při dalším automatickém ukládání. Pomocí [cdatarecoveryhandleru::SetAutosaveInterval](#setautosaveinterval) změňte interval automatického ukládání po `CDataRecoveryHandler`inicializaci aplikace .

## <a name="cdatarecoveryhandlerqueryrestoreautosaveddocuments"></a><a name="queryrestoreautosaveddocuments"></a>CDataRecoveryHandler::QueryRestoreAutosavedDocuments

Zobrazí uživateli dialogové okno pro každý `CDataRecoveryHandler` dokument, který byl automaticky uložen. Dialogové okno určuje, zda chce uživatel obnovit automaticky uložený dokument.

```
virtual void QueryRestoreAutosavedDocuments();
```

### <a name="remarks"></a>Poznámky

Pokud je vaše aplikace Unicode, tato metoda zobrazí [CTaskDialog](../../mfc/reference/ctaskdialog-class.md) uživateli. V opačném případě rozhraní používá [AfxMessageBox](../../mfc/reference/cstring-formatting-and-message-box-display.md#afxmessagebox) k dotazování uživatele.

Po `QueryRestoreAutosavedDocuments` shromáždění všech odpovědí od uživatele uloží informace v proměnné člena *m_mapDocNameToRestoreBool*. Tato metoda neobnoví automaticky uložené dokumenty.

## <a name="cdatarecoveryhandlerreadopendocumentlist"></a><a name="readopendocumentlist"></a>CDataRecoveryHandler::ReadOpenDocumentList

Načte otevřený seznam dokumentů z registru.

```
virtual BOOL ReadOpenDocumentList();
```

### <a name="return-value"></a>Návratová hodnota

True označuje, že `ReadOpenDocumentList` načtené informace pro alespoň jeden dokument z registru; NEPRAVDA označuje, že nebyly načteny žádné informace o dokumentu.

### <a name="remarks"></a>Poznámky

Tato funkce načte informace o otevřeném dokumentu z registru a uloží je do členské proměnné *m_mapDocNameToAutosaveName*.

Po `ReadOpenDocumentList` načtení všech dat odstraní informace o dokumentu z registru.

## <a name="cdatarecoveryhandlerremovedocumentinfo"></a><a name="removedocumentinfo"></a>CDataRecoveryHandler::RemoveDocumentInfo

Odebere dodaný dokument ze seznamu otevřených dokumentů.

```
virtual BOOL RemoveDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*pDokument*|[v] Ukazatel na dokument odebrat.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud *pDocument* byl odebrán ze seznamu; Nepravda, pokud došlo k chybě.

### <a name="remarks"></a>Poznámky

Když uživatel zavře dokument, rozhraní framework používá tuto metodu k jeho odebrání ze seznamu otevřených dokumentů.

Pokud `RemoveDocumentInfo` nelze najít *pDocument* v seznamu otevřených dokumentů, neprovede nic a vrátí hodnotu TRUE.

Chcete-li použít tuto metodu, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES musí být nastavena v *m_dwRestartManagerSupportFlags*.

## <a name="cdatarecoveryhandlerreopenpreviousdocuments"></a><a name="reopenpreviousdocuments"></a>CDataRecoveryHandler::Znovu otevřítpředchozí dokumenty

Otevře dříve otevřené dokumenty.

```
virtual BOOL ReopenPreviousDocuments();
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byl otevřen alespoň jeden dokument; jinak FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda otevře poslední uložení dříve otevřených dokumentů. Pokud dokument nebyl uložen nebo `ReopenPreviousDocuments` automaticky uložen, otevře se prázdný dokument založený na šabloně pro daný typ souboru.

Chcete-li použít tuto metodu, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES musí být nastavena v *m_dwRestartManagerSupportFlags*. Pokud tento parametr není `ReopenPreviousDocuments` nastaven, neprovede nic a vrátí hodnotu NEPRAVDA.

Pokud nejsou v seznamu dříve otevřených dokumentů `ReopenPreviousDocuments` uloženy žádné dokumenty, neprovede žádnou akci a vrátí hodnotu FALSE.

## <a name="cdatarecoveryhandlerrestoreautosaveddocuments"></a><a name="restoreautosaveddocuments"></a>CDataRecoveryHandler::Obnovitautomaticky uložené dokumenty

Obnoví automaticky uložené dokumenty na základě vstupu uživatele.

```
virtual BOOL RestoreAutosavedDocuments();
```

### <a name="return-value"></a>Návratová hodnota

TRUE Pokud tato metoda úspěšně obnoví dokumenty.

### <a name="remarks"></a>Poznámky

Tato metoda volá [CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments) k určení, které dokumenty chce uživatel obnovit. Pokud se uživatel rozhodne neobnovit automaticky `RestoreAutosavedDocuments` uložený dokument, odstraní soubor automatického ukládání. V `RestoreAutosavedDocuments` opačném případě nahradí otevřený dokument automaticky uloženou verzí.

Chcete-li použít tuto metodu, AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES `m_dwRestartManagerSupportFlags`AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES musí být v písmenu .

## <a name="cdatarecoveryhandlersaveopendocumentlist"></a><a name="saveopendocumentlist"></a>CDataRecoveryHandler::UložitOpenDocumentList

Uloží aktuální seznam otevřených dokumentů do registru systému Windows.

```
virtual BOOL SaveOpenDocumentList();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud neexistují žádné otevřené dokumenty, které by bylo možné uložit, nebo pokud byly úspěšně uloženy. False, pokud existují dokumenty uložit do registru, ale nebyly uloženy, protože došlo k chybě.

### <a name="remarks"></a>Poznámky

Správce restartování `SaveOpenDocumentList` volá, když se aplikace neočekávaně ukončí nebo když se ukončí pro upgrade. Když se aplikace restartuje, používá [CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist) k načtení seznamu otevřených dokumentů.

Tato metoda uloží pouze seznam otevřených dokumentů. Metoda [CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo) je zodpovědná za uložení samotných dokumentů.

## <a name="cdatarecoveryhandlersetautosaveinterval"></a><a name="setautosaveinterval"></a>CDataRecoveryHandler::SetAutosaveInterval

Nastaví čas mezi cykly automatického ukládání v milisekundách.

```
Virtual void SetAutosaveInterval(int nAutosaveInterval);
```

### <a name="parameters"></a>Parametry

*nInterval automatického ukládání*<br/>
[v] Nový interval automatického ukládání v milisekundách.

## <a name="cdatarecoveryhandlersetautosavepath"></a><a name="setautosavepath"></a>CDataRecoveryHandler::SetAutosavePath

Nastaví adresář, ve kterém jsou uloženy automaticky uložené soubory.

```
virtual void SetAutosavePath(const CString& strAutosavePath);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*Trasa automatického ukládání*|[v] Cesta, kde jsou uloženy soubory automatického ukládání.|

### <a name="remarks"></a>Poznámky

Změna adresáře automatického ukládání se aktuálně automaticky uloženými soubory nepřesune.

## <a name="cdatarecoveryhandlersetrestartidentifier"></a><a name="setrestartidentifier"></a>CDataRecoveryHandler::SetRestartIdentifier

Nastaví jedinečný identifikátor restartování pro `CDataRecoveryHandler`tuto instanci .

```
virtual void SetRestartIdentifier(const CString& strRestartIdentifier);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*strRestartIdentifier*|[v] Jedinečný identifikátor správce restartování.|

### <a name="remarks"></a>Poznámky

Správce restartování zaznamenává informace o otevřených dokumentech v registru. Tyto informace jsou uloženy s jedinečným identifikátorem restartování jako klíč. Vzhledem k tomu, že identifikátor restartování je jedinečný pro každou instanci aplikace, může dojít k neočekávaně ukončení více instancí aplikace a správce restartování může každou z nich obnovit.

## <a name="cdatarecoveryhandlersetsavedocumentinfoonidle"></a><a name="setsavedocumentinfoonidle"></a>cDataRecoveryHandler::SetSaveDocumentInfoOnIdle

Nastaví, `CDataRecoveryHandler` zda uloží informace o otevřeném dokumentu do registru systému Windows během aktuálního cyklu nečinnosti.

```
virtual void SetSaveDocumentInfoOnIdle(BOOL bSaveOnIdle);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*bSaveOnIdle*|[v] TRUE pro uložení informací o dokumentu během aktuálního cyklu nečinnosti; FALSE neprovede uložení.|

## <a name="cdatarecoveryhandlersetshutdownbyrestartmanager"></a><a name="setshutdownbyrestartmanager"></a>CDataRecoveryHandler::SetShutdownByRestartManager

Nastaví, zda předchozí ukončení aplikace bylo způsobeno správcem restartování.

```
virtual void SetShutdownByRestartManager(BOOL bShutdownByRestartManager);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*bShutdownByRestartManager*|[v] TRUE označuje, že správce restartování způsobil ukončení aplikace; FALSE označuje, že aplikace byla ukončena z jiného důvodu.|

### <a name="remarks"></a>Poznámky

Rozhraní framework se chová odlišně v závislosti na tom, zda předchozí ukončení bylo neočekávané nebo zda byla inicionována správcem restartování.

## <a name="cdatarecoveryhandlerupdatedocumentinfo"></a><a name="updatedocumentinfo"></a>CDataRecoveryHandler::UpdateDocumentInfo

Aktualizuje informace o dokumentu, protože jej uživatel uložil.

```
virtual BOOL UpdateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*pDokument*|[v] Ukazatel na uložený dokument.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud tato metoda odstranila automaticky uložený dokument a aktualizovala informace o dokumentu; Nepravda, pokud došlo k chybě.

### <a name="remarks"></a>Poznámky

Když uživatel uloží dokument, aplikace automaticky uložený soubor odebere, protože již není potřeba. `UpdateDocumentInfo`odstraní automaticky uložený soubor voláním [CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo). `UpdateDocumentInfo`pak přidá informace z *pDocument* do seznamu aktuálně `RemoveDocumentInfo` otevřených dokumentů, protože odstraní tyto informace, ale uložený dokument je stále otevřený.

Chcete-li použít tuto metodu, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES musí být nastavena v *m_dwRestartManagerSupportFlags*.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Postupy: Přidání podpory správce restartování](../../mfc/how-to-add-restart-manager-support.md)
