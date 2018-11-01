---
title: CDocument – třída
ms.date: 11/04/2016
f1_keywords:
- CDocument
- AFXWIN/CDocument
- AFXWIN/CDocument::CDocument
- AFXWIN/CDocument::AddView
- AFXWIN/CDocument::BeginReadChunks
- AFXWIN/CDocument::CanCloseFrame
- AFXWIN/CDocument::ClearChunkList
- AFXWIN/CDocument::ClearPathName
- AFXWIN/CDocument::DeleteContents
- AFXWIN/CDocument::FindChunk
- AFXWIN/CDocument::GetAdapter
- AFXWIN/CDocument::GetDocTemplate
- AFXWIN/CDocument::GetFile
- AFXWIN/CDocument::GetFirstViewPosition
- AFXWIN/CDocument::GetNextView
- AFXWIN/CDocument::GetPathName
- AFXWIN/CDocument::GetThumbnail
- AFXWIN/CDocument::GetTitle
- AFXWIN/CDocument::InitializeSearchContent
- AFXWIN/CDocument::IsModified
- AFXWIN/CDocument::IsSearchAndOrganizeHandler
- AFXWIN/CDocument::LoadDocumentFromStream
- AFXWIN/CDocument::OnBeforeRichPreviewFontChanged
- AFXWIN/CDocument::OnChangedViewList
- AFXWIN/CDocument::OnCloseDocument
- AFXWIN/CDocument::OnCreatePreviewFrame
- AFXWIN/CDocument::OnDocumentEvent
- AFXWIN/CDocument::OnDrawThumbnail
- AFXWIN/CDocument::OnLoadDocumentFromStream
- AFXWIN/CDocument::OnNewDocument
- AFXWIN/CDocument::OnOpenDocument
- AFXWIN/CDocument::OnPreviewHandlerQueryFocus
- AFXWIN/CDocument::OnPreviewHandlerTranslateAccelerator
- AFXWIN/CDocument::OnRichPreviewBackColorChanged
- AFXWIN/CDocument::OnRichPreviewFontChanged
- AFXWIN/CDocument::OnRichPreviewSiteChanged
- AFXWIN/CDocument::OnRichPreviewTextColorChanged
- AFXWIN/CDocument::OnSaveDocument
- AFXWIN/CDocument::OnUnloadHandler
- AFXWIN/CDocument::PreCloseFrame
- AFXWIN/CDocument::ReadNextChunkValue
- AFXWIN/CDocument::ReleaseFile
- AFXWIN/CDocument::RemoveChunk
- AFXWIN/CDocument::RemoveView
- AFXWIN/CDocument::ReportSaveLoadException
- AFXWIN/CDocument::SaveModified
- AFXWIN/CDocument::SetChunkValue
- AFXWIN/CDocument::SetModifiedFlag
- AFXWIN/CDocument::SetPathName
- AFXWIN/CDocument::SetTitle
- AFXWIN/CDocument::UpdateAllViews
- AFXWIN/CDocument::OnFileSendMail
- AFXWIN/CDocument::OnUpdateFileSendMail
- AFXWIN/CDocument::m_bGetThumbnailMode
- AFXWIN/CDocument::m_bPreviewHandlerMode
- AFXWIN/CDocument::m_bSearchMode
- AFXWIN/CDocument::m_clrRichPreviewBackColor
- AFXWIN/CDocument::m_clrRichPreviewTextColor
- AFXWIN/CDocument::m_lfRichPreviewFont
helpviewer_keywords:
- CDocument [MFC], CDocument
- CDocument [MFC], AddView
- CDocument [MFC], BeginReadChunks
- CDocument [MFC], CanCloseFrame
- CDocument [MFC], ClearChunkList
- CDocument [MFC], ClearPathName
- CDocument [MFC], DeleteContents
- CDocument [MFC], FindChunk
- CDocument [MFC], GetAdapter
- CDocument [MFC], GetDocTemplate
- CDocument [MFC], GetFile
- CDocument [MFC], GetFirstViewPosition
- CDocument [MFC], GetNextView
- CDocument [MFC], GetPathName
- CDocument [MFC], GetThumbnail
- CDocument [MFC], GetTitle
- CDocument [MFC], InitializeSearchContent
- CDocument [MFC], IsModified
- CDocument [MFC], IsSearchAndOrganizeHandler
- CDocument [MFC], LoadDocumentFromStream
- CDocument [MFC], OnBeforeRichPreviewFontChanged
- CDocument [MFC], OnChangedViewList
- CDocument [MFC], OnCloseDocument
- CDocument [MFC], OnCreatePreviewFrame
- CDocument [MFC], OnDocumentEvent
- CDocument [MFC], OnDrawThumbnail
- CDocument [MFC], OnLoadDocumentFromStream
- CDocument [MFC], OnNewDocument
- CDocument [MFC], OnOpenDocument
- CDocument [MFC], OnPreviewHandlerQueryFocus
- CDocument [MFC], OnPreviewHandlerTranslateAccelerator
- CDocument [MFC], OnRichPreviewBackColorChanged
- CDocument [MFC], OnRichPreviewFontChanged
- CDocument [MFC], OnRichPreviewSiteChanged
- CDocument [MFC], OnRichPreviewTextColorChanged
- CDocument [MFC], OnSaveDocument
- CDocument [MFC], OnUnloadHandler
- CDocument [MFC], PreCloseFrame
- CDocument [MFC], ReadNextChunkValue
- CDocument [MFC], ReleaseFile
- CDocument [MFC], RemoveChunk
- CDocument [MFC], RemoveView
- CDocument [MFC], ReportSaveLoadException
- CDocument [MFC], SaveModified
- CDocument [MFC], SetChunkValue
- CDocument [MFC], SetModifiedFlag
- CDocument [MFC], SetPathName
- CDocument [MFC], SetTitle
- CDocument [MFC], UpdateAllViews
- CDocument [MFC], OnFileSendMail
- CDocument [MFC], OnUpdateFileSendMail
- CDocument [MFC], m_bGetThumbnailMode
- CDocument [MFC], m_bPreviewHandlerMode
- CDocument [MFC], m_bSearchMode
- CDocument [MFC], m_clrRichPreviewBackColor
- CDocument [MFC], m_clrRichPreviewTextColor
- CDocument [MFC], m_lfRichPreviewFont
ms.assetid: e5a2891d-e1e1-4599-8c7e-afa9b4945446
ms.openlocfilehash: e84ceb11ad789ef3bd6933292030ef2af6f1d817
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50609310"
---
# <a name="cdocument-class"></a>CDocument – třída

Poskytuje základní funkce pro třídy dokumentu definované uživatelem.

## <a name="syntax"></a>Syntaxe

```
class CDocument : public CCmdTarget
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDocument::CDocument](#cdocument)|Vytvoří `CDocument` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDocument::AddView](#addview)|Zobrazení se připojí k tomuto dokumentu.|
|[CDocument::BeginReadChunks](#beginreadchunks)|Inicializuje bloku dat čtení.|
|[CDocument::CanCloseFrame](#cancloseframe)|Pokročilé overridable; volá se před zavřením okna rámce zobrazení tohoto dokumentu.|
|[CDocument::ClearChunkList](#clearchunklist)|Vymaže seznamu bloků.|
|[CDocument::ClearPathName](#clearpathname)|Vymaže cestu objektu dokumentu.|
|[CDocument::DeleteContents](#deletecontents)|Volá se, aby, vyčistěte dokumentu.|
|[CDocument::FindChunk](#findchunk)|Vyhledá bloků dat se zadaným identifikátorem GUID.|
|[CDocument::GetAdapter](#getadapter)|Vrací ukazatel na objekt implementace `IDocument` rozhraní.|
|[CDocument::GetDocTemplate](#getdoctemplate)|Vrací ukazatel na šablonu dokumentu, který popisuje typ dokumentu.|
|[CDocument::GetFile](#getfile)|Vrací ukazatel na požadovaný `CFile` objektu.|
|[CDocument::GetFirstViewPosition](#getfirstviewposition)|Vrátí pozici první v seznamu zobrazení; používá k zahájení iterace.|
|[CDocument::GetNextView](#getnextview)|Iteruje přes seznam zobrazení, které jsou spojené s dokumentem.|
|[CDocument::GetPathName](#getpathname)|Vrátí cestu k souboru dat dokumentu.|
|[CDocument::GetThumbnail](#getthumbnail)|Volá se, aby vytvořit rastrový obrázek miniatury poskytovatele používané k zobrazení miniatury.|
|[CDocument::GetTitle](#gettitle)|Vrátí název dokumentu.|
|[CDocument::InitializeSearchContent](#initializesearchcontent)|Volá se, aby inicializovat obsah vyhledávání pro obslužnou rutinu hledání.|
|[CDocument::IsModified](#ismodified)|Určuje, zda dokumentu se změnila od posledního uložení.|
|[CDocument::IsSearchAndOrganizeHandler](#issearchandorganizehandler)|Určuje, jestli této instance `CDocument` objekt byl vytvořen pro obslužnou rutinu hledání & Uspořádat.|
|[CDocument::LoadDocumentFromStream](#loaddocumentfromstream)|Volá se, aby načíst data dokumentu z datového proudu.|
|[CDocument::OnBeforeRichPreviewFontChanged](#onbeforerichpreviewfontchanged)|Voláno před provedením změnit písmo pro náhled ve formátu RTF.|
|[CDocument::OnChangedViewList](#onchangedviewlist)|Volá se po zobrazení je přidán či odebrán z dokumentu.|
|[CDocument::OnCloseDocument](#onclosedocument)|Volá se, aby zavřít dokument.|
|[CDocument::OnCreatePreviewFrame](#oncreatepreviewframe)|Volá se rozhraním, když je nutné vytvořit objekt frame, ve verzi preview pro náhled ve formátu RTF.|
|[CDocument::OnDocumentEvent](#ondocumentevent)|Volá se rozhraním v reakci na událost dokumentu.|
|[CDocument::OnDrawThumbnail](#ondrawthumbnail)|Potlačí tuto metodu v odvozené třídě k vykreslení obsahu miniatury.|
|[CDocument::OnLoadDocumentFromStream](#onloaddocumentfromstream)|Volá se rozhraním, když je nutné načíst data dokumentu z datového proudu.|
|[CDocument::OnNewDocument](#onnewdocument)|Volá se, aby vytvoříte nový textový dokument.|
|[CDocument::OnOpenDocument](#onopendocument)|Volá se, aby existující dokument otevřít.|
|[CDocument::OnPreviewHandlerQueryFocus](#onpreviewhandlerqueryfocus)|Obslužné rutiny náhledu se vraťte HWND z volání funkce hodnotu GetFocus přesměruje.|
|[CDocument::OnPreviewHandlerTranslateAccelerator](#onpreviewhandlertranslateaccelerator)|Určí, že obslužné rutiny náhledu pro zpracování jedním stisknutím tlačítka předány z pumpu zpráv procesu, ve kterém je spuštěna obslužná rutina ve verzi preview.|
|[CDocument::OnRichPreviewBackColorChanged](#onrichpreviewbackcolorchanged)|Volá se, když se změní barva pozadí náhledu.|
|[CDocument::OnRichPreviewFontChanged](#onrichpreviewfontchanged)|Volá se při změně písmo pro náhled ve formátu RTF.|
|[CDocument::OnRichPreviewSiteChanged](#onrichpreviewsitechanged)|Volá se při změně webu náhled ve formátu RTF.|
|[CDocument::OnRichPreviewTextColorChanged](#onrichpreviewtextcolorchanged)|Volá se, když se změní barva textu náhled ve formátu RTF.|
|[CDocument::OnSaveDocument](#onsavedocument)|Volá se, aby dokument uložit na disk.|
|[CDocument::OnUnloadHandler](#onunloadhandler)|Volá se rozhraním, když byla uvolněna obslužné rutiny náhledu.|
|[CDocument::PreCloseFrame](#precloseframe)|Volá se před zavřením okna rámce.|
|[CDocument::ReadNextChunkValue](#readnextchunkvalue)|Přečte další blok hodnotu.|
|[CDocument::ReleaseFile](#releasefile)|Uvolní soubor, aby byl k dispozici pro použití jiné aplikace.|
|[CDocument::RemoveChunk](#removechunk)|Odebere bloků dat se zadaným identifikátorem GUID.|
|[CDocument::RemoveView](#removeview)|Odpojí zobrazení z dokumentu.|
|[CDocument::ReportSaveLoadException](#reportsaveloadexception)|Pokročilé overridable; volá se při otevření nebo uložení operaci nejde dokončit z důvodu výjimky.|
|[CDocument::SaveModified](#savemodified)|Pokročilé overridable; volá se, aby požádat uživatele, zda má být uložen dokument.|
|[CDocument::SetChunkValue](#setchunkvalue)|Nastaví hodnotu bloku.|
|[CDocument::SetModifiedFlag](#setmodifiedflag)|Nastaví příznak označující, že upravíte dokument od posledního uložení.|
|[CDocument::SetPathName](#setpathname)|Nastaví cestu k souboru dat dokument používá.|
|[CDocument::SetTitle](#settitle)|Nastaví název dokumentu.|
|[CDocument::UpdateAllViews](#updateallviews)|Upozorní, všechna zobrazení, které dokumentu se změnila.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CDocument::OnFileSendMail](#onfilesendmail)|Odešle e-mailovou zprávu se na dokument připojený.|
|[CDocument::OnUpdateFileSendMail](#onupdatefilesendmail)|Povolit příkaz Odeslat e-mailu, pokud je k dispozici podpora e-mailu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CDocument::m_bGetThumbnailMode](#m_bgetthumbnailmode)|Určuje, že `CDocument` objekt byl vytvořen dllhost pro miniatury. By měl být vráceny se změnami `CView::OnDraw`.|
|[CDocument::m_bPreviewHandlerMode](#m_bpreviewhandlermode)|Určuje, že `CDocument` objekt byl vytvořen prevhost pro `Rich Preview`. By měl být vráceny se změnami `CView::OnDraw`.|
|[CDocument::m_bSearchMode](#m_bsearchmode)|Určuje, že `CDocument` objekt byl vytvořen pomocí indexeru nebo další vyhledávací aplikaci.|
|[CDocument::m_clrRichPreviewBackColor](#m_clrrichpreviewbackcolor)|Určuje barvu pozadí okna Náhled ve formátu RTF. Tato barva je nastavena podle hostitele.|
|[CDocument::m_clrRichPreviewTextColor](#m_clrrichpreviewtextcolor)|Určuje barvu popředí náhledu okna. Tato barva je nastavena podle hostitele.|
|[CDocument::m_lfRichPreviewFont](#m_lfrichpreviewfont)|Určuje písmo pro text pro okno náhledu. V těchto písmo je nastavená hostitelem.|

## <a name="remarks"></a>Poznámky

Dokument představuje jednotku dat uživatel obvykle otevře pomocí příkazu Otevřít soubor a uloží pomocí příkazu Uložit.

`CDocument` standardní operace, jako je vytvoření dokumentu, načtením a uložíte ho podporuje. Rozhraní framework zpracovává dokumentů pomocí rozhraní definované `CDocument`.

Aplikace může podporovat více než jeden typ dokumentu. aplikace může například podporovat, tabulky a textové dokumenty. Každý typ dokument má šablonu přidružený dokument; Dokument šablony určuje, jaké prostředky (například nabídky, ikona nebo akcelerátoru tabulka) se používají pro daný typ dokumentu. Každý dokument obsahuje ukazatel na jeho přidruženého `CDocTemplate` objektu.

Uživatelé komunikují s dokumentem prostřednictvím [CView](../../mfc/reference/cview-class.md) objekty s ním spojená. Zobrazení vykreslí obrázek v okně s rámečkem dokumentu a uživatelský vstup interpretuje jako operace v dokumentu. Dokument může mít více zobrazení s ním spojená. Když uživatel otevře okno dokumentu, vytvoří zobrazení rozhraní a připojí ho k tomuto dokumentu. Dokument šablony určuje, jaký typ zobrazení a rámečku okna se používají k zobrazení všech typů dokumentů.

Dokumenty jsou součástí standardní rozhraní framework příkaz, směrování a v důsledku přijímá příkazy z komponenty standardní uživatelské rozhraní (například uložit soubor položky nabídky). Dokument přijímá příkazy předané aktivní zobrazení. Pokud dokument nebude zpracování daného příkazu, předá příkazu se šablonou dokumentu, která ho spravuje.

Když se změní data dokumentu každá z jeho zobrazení musí odpovídat tyto úpravy. `CDocument` poskytuje [UpdateAllViews](#updateallviews) členské funkce pro vás upozornit zobrazení tyto změny, tak zobrazení můžete repaint sami podle potřeby. Rozhraní také vyzve uživatele před zavřením uložit upravený soubor.

K implementaci dokumenty v typické aplikaci, postupujte takto:

- Odvodit třídu z `CDocument` pro každý typ dokumentu.

- Přidání členské proměnné k ukládání dat každého dokumentu.

- Implementace členské funkce pro čtení a úpravy dat dokumentu. Zobrazení dokumentu jsou nejdůležitější uživatelé tyto členské funkce.

- Přepsat [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) členské funkce ve třídě dokumentů pro zápis a čtení dokumentu dat do a z disku.

`CDocument` zajišťuje podporu pro odesílání dokumentu e-mailem. Pokud je k dispozici podpora e-mailu (MAPI). Přečtěte si články [MAPI](../../mfc/mapi.md) a [Podpora MAPI v MFC](../../mfc/mapi-support-in-mfc.md).

Další informace o `CDocument`, naleznete v tématu [serializace](../../mfc/serialization-in-mfc.md), [Document/View – architektura témata](../../mfc/document-view-architecture.md), a [vytváření dokumentů/zobrazení](../../mfc/document-view-creation.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocument`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

##  <a name="addview"></a>  CDocument::AddView

Voláním této funkce připojení zobrazení k dokumentu.

```
void AddView(CView* pView);
```

### <a name="parameters"></a>Parametry

*pView*<br/>
Odkazuje na zobrazení přidán.

### <a name="remarks"></a>Poznámky

Tato funkce přidá zadané zobrazení Seznam zobrazení, které jsou přidružené k dokumentu. funkce také nastaví zobrazení dokumentu ukazatel na tento dokument. Rozhraní volá tuto funkci při zobrazení nově vytvořený objekt se připojuje k dokumentu. k tomu dochází v reakci na nový soubor, otevřít soubor nebo nové okno příkaz nebo rozdělit okno s rozdělovačem.

Voláním této funkce jenom v případě, že jsou ruční vytvoření a připojení zobrazení. Obvykle vám umožní framework připojení dokumentů a zobrazení tak, že definujete [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objektu, který chcete přidružit třídy dokumentu, zobrazení třídy a třídy oken s rámečkem.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocViewSDI#12](../../mfc/codesnippet/cpp/cdocument-class_1.cpp)]

##  <a name="beginreadchunks"></a>  CDocument::BeginReadChunks

Inicializuje bloku dat čtení.

```
virtual void BeginReadChunks ();
```

### <a name="remarks"></a>Poznámky

##  <a name="cancloseframe"></a>  CDocument::CanCloseFrame

Volá se rozhraním před zavřením okna rámce zobrazení dokumentu.

```
virtual BOOL CanCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>Parametry

*pFrame*<br/>
Odkazuje na okno rámce zobrazení připojené k dokumentu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je bezpečné zavřete okno rámce. jinak 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace zkontroluje, pokud existují další oken s rámečkem v dokumentu zobrazení. Pokud je okno zadaného rámce poslední z nich, který zobrazí dokument, funkce zobrazí výzvu k uložení dokumentu, pokud byl změněn. Tato funkce přepište, pokud chcete provést zvláštní zpracování při zavření okna rámce. To je moderní overridable.

##  <a name="cdocument"></a>  CDocument::CDocument

Vytvoří `CDocument` objektu.

```
CDocument();
```

### <a name="remarks"></a>Poznámky

Rozhraní framework zpracovává vytvoření dokumentu pro vás. Přepsat [OnNewDocument](#onnewdocument) členská funkce k provedení inicializace v jednotlivých dokumentů; to je obzvláště důležité v jednom dokumentu rozhraní (SDI) aplikace.

##  <a name="clearchunklist"></a>  CDocument::ClearChunkList

Vymaže seznamu bloků.

```
virtual void ClearChunkList ();
```

### <a name="remarks"></a>Poznámky

##  <a name="clearpathname"></a>  CDocument::ClearPathName

Vymaže cestu objektu dokumentu.

```
virtual void ClearPathName();
```

### <a name="remarks"></a>Poznámky

Vymazání cestu z `CDocument` objekt způsobí, že aplikace vyzve uživatele, když je dokument uložen dále. Díky tomu **Uložit** příkazu se chovat jako **uložit jako** příkazu.

##  <a name="deletecontents"></a>  CDocument::DeleteContents

Volá se rozhraním, aniž by zlikvidoval odstranit data dokumentu `CDocument` samotného objektu.

```
virtual void DeleteContents();
```

### <a name="remarks"></a>Poznámky

Je volána těsně před plánovaným je dokument ke zničení. Nazývá se také zajistit, že dokument je prázdný, předtím, než se znovu použije. To je zvlášť důležité pro aplikace SDI, která používá pouze jeden dokument; dokument je znovu pokaždé, když uživatel vytvoří nebo otevře jiný dokument. Voláním této funkce pro implementaci "Upravit Vymazat vše" nebo podobné příkaz, který odstraní všechna data dokumentu. Výchozí implementace této funkce nemá žádný účinek. Potlačí tuto funkci můžete odstranit data v dokumentu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#57](../../mfc/codesnippet/cpp/cdocument-class_2.cpp)]

##  <a name="findchunk"></a>  CDocument::FindChunk

Vyhledá bloků dat se zadaným identifikátorem GUID.

```
virtual POSITION FindChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>Parametry

*identifikátor GUID*<br/>
Určuje identifikátor GUID blok, který se má najít.

*Identifikátor PID*<br/>
Určuje identifikátor PID blok k vyhledání.

### <a name="return-value"></a>Návratová hodnota

Pozice v seznamu interní bloků dat v případě úspěšného ověření. V opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

##  <a name="getadapter"></a>  CDocument::GetAdapter

Vrací ukazatel implementaci objektu `IDocument` rozhraní.

```
virtual ATL::IDocument* GetAdapter();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel implementaci objektu `IDocument` rozhraní.

### <a name="remarks"></a>Poznámky

##  <a name="getdoctemplate"></a>  CDocument::GetDocTemplate

Voláním této funkce získání ukazatele na šablonu dokumentu pro tento typ dokumentu.

```
CDocTemplate* GetDocTemplate() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na šablonu dokumentu pro tento typ dokumentu nebo hodnota NULL, pokud dokument nespravuje šablonu dokumentu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#58](../../mfc/codesnippet/cpp/cdocument-class_3.cpp)]

##  <a name="getfile"></a>  CDocument::GetFile

Voláním této členské funkce, chcete-li získat ukazatel `CFile` objektu.

```
virtual CFile* GetFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CFileException* pError);
```

### <a name="parameters"></a>Parametry

*lpszFileName*<br/>
Řetězec, který určuje cestu k souboru požadovaného. Cesta může být relativní nebo absolutní.

*pError*<br/>
Ukazatel na existující objekt výjimky souborů, která označuje stav dokončení operace.

*nOpenFlags*<br/>
Režim sdílení a přístup. Určuje akci, která má provést při otevírání souboru. Zkombinováním možností uvedených v konstruktoru cfile – [CFile::CFile](../../mfc/reference/cfile-class.md#cfile) pomocí bitový operátor OR (&#124;) – operátor. Jsou vyžadovány; jeden přístupová oprávnění a možnost jedna sdílená složka `modeCreate` a `modeNoInherit` režimy jsou volitelné.

### <a name="return-value"></a>Návratová hodnota

Ukazatel `CFile` objektu.

##  <a name="getfirstviewposition"></a>  CDocument::GetFirstViewPosition

Voláním této funkce získá pozici první zobrazení v seznamu zobrazení spojené s dokumentem.

```
virtual POSITION GetFirstViewPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

POZICE hodnotu, která lze použít pro iterace pomocí produktu [GetNextView](#getnextview) členskou funkci.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

##  <a name="getnextview"></a>  CDocument::GetNextView

Voláním této funkce k iteraci v rámci všechna zobrazení dokumentu.

```
virtual CView* GetNextView(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*rposition.*<br/>
Odkaz na hodnotu pozice vrácené předchozím volání `GetNextView` nebo [GetFirstViewPosition](#getfirstviewposition) členské funkce. Tato hodnota nesmí být NULL.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na zobrazení identifikovaný *rposition*.

### <a name="remarks"></a>Poznámky

Funkce vrátí zobrazení identifikovaný *rposition* a pak nastaví *rposition* hodnotu pozice další zobrazení v seznamu. Pokud zobrazení načtených je poslední v seznamu, pak *rposition* nastaven na hodnotu NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

##  <a name="getpathname"></a>  CDocument::GetPathName

Voláním této funkce získáte plně kvalifikovanou cestu souboru dokumentu na disku.

```
const CString& GetPathName() const;
```

### <a name="return-value"></a>Návratová hodnota

Plně kvalifikovaná cesta dokumentu. Tento řetězec je prázdný, pokud dokument nebyl uložen, nebo nemá přidružený soubor na disku.

##  <a name="getthumbnail"></a>  CDocument::GetThumbnail

Vytvoří rastrový obrázek použitého zprostředkovatelem miniatur zobrazíte na miniaturu.

```
virtual BOOL GetThumbnail(
    UINT cx,
    HBITMAP* phbmp,
    DWORD* pdwAlpha);
```

### <a name="parameters"></a>Parametry

*CX*<br/>
Určuje šířku a výšku rastrového obrázku.

*phbmp*<br/>
Obsahuje popisovač rastrový obrázek, když funkce skončí úspěšně.

*pdwAlpha*<br/>
Obsahuje hodnotu DWORD určující hodnotu alfa kanál, když funkce skončí úspěšně.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud rastrový obrázek pro miniaturu vytvořil úspěšně; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="gettitle"></a>  CDocument::GetTitle

Voláním této funkce získáte název dokumentu, který je obvykle odvozen z dokumentu název souboru.

```
const CString& GetTitle() const;
```

### <a name="return-value"></a>Návratová hodnota

Název dokumentu.

##  <a name="initializesearchcontent"></a>  CDocument::InitializeSearchContent

Volá se, aby se inicializovat obsah vyhledávání pro obslužnou rutinu hledání.

```
virtual void InitializeSearchContent ();
```

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu v odvozené třídě inicializovat obsah vyhledávání. Obsah by měl být řetězec s části oddělené ";". Například "bod; obdélník; položky OLE.".

##  <a name="ismodified"></a>  CDocument::IsModified

Voláním této funkce určete, jestli dokument se změnila od posledního uložení.

```
virtual BOOL IsModified();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud dokument se změnila od posledního uložení; jinak 0.

##  <a name="issearchandorganizehandler"></a>  CDocument::IsSearchAndOrganizeHandler

Určuje, zda tuto instanci `CDocument` byla vytvořena pro obslužnou rutinu hledání & Uspořádat.

```
BOOL IsSearchAndOrganizeHandler() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud tato instance `CDocument` byla vytvořena pro obslužnou rutinu hledání & Uspořádat.

### <a name="remarks"></a>Poznámky

Aktuálně tato funkce vrací hodnotu TRUE jenom pro obslužné rutiny náhledu implementované v out of procesový server. Na úrovni vaší aplikace, aby tato funkce vrací TRUE, můžete nastavit příslušnými příznaky (m_bPreviewHandlerMode, m_bSearchMode, m_bGetThumbnailMode).

##  <a name="loaddocumentfromstream"></a>  CDocument::LoadDocumentFromStream

Volá se, aby načíst data dokumentu z datového proudu.

```
virtual HRESULT LoadDocumentFromStream(
    IStream* pStream,
    DWORD dwGrfMode);
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
Ukazatel na datový proud. Tento datový proud je poskytnut pomocí prostředí.

*dwGrfMode*<br/>
Režim přístupu do datového proudu.

### <a name="return-value"></a>Návratová hodnota

S_OK, pokud je operace načtení úspěšné, jinak HRESULT s kódem chyby.

### <a name="remarks"></a>Poznámky

Mohou přepsat tuto metodu v odvozené třídě přizpůsobení jak načíst data z datového proudu.

##  <a name="m_bgetthumbnailmode"></a>  CDocument::m_bGetThumbnailMode

Určuje, že `CDocument` objekt byl vytvořen dllhost pro miniatury. By měl být vráceny se změnami `CView::OnDraw`.

```
BOOL m_bGetThumbnailMode;
```

### <a name="remarks"></a>Poznámky

`TRUE` Označuje, že dokument vytvořil dllhost pro miniatury.

##  <a name="m_bpreviewhandlermode"></a>  CDocument::m_bPreviewHandlerMode

Určuje, že `CDocument` objekt prevhost vytvořil pro náhled ve formátu RTF. By měl být vráceny se změnami `CView::OnDraw`.

```
BOOL m_bPreviewHandlerMode;
```

### <a name="remarks"></a>Poznámky

Hodnota TRUE označuje, že dokument vytvořil prevhost pro náhled ve formátu RTF.

##  <a name="m_bsearchmode"></a>  CDocument::m_bSearchMode

Určuje, že `CDocument` objekt byl vytvořen, indexer nebo jiné hledání aplikací.

```
BOOL m_bSearchMode;
```

### <a name="remarks"></a>Poznámky

`TRUE` Označuje, že dokument byl vytvořen, indexer nebo jiné hledání aplikací.

##  <a name="m_clrrichpreviewbackcolor"></a>  CDocument::m_clrRichPreviewBackColor

Určuje barvu pozadí okna Náhled ve formátu RTF. Tato barva je nastavena podle hostitele.

```
COLORREF m_clrRichPreviewBackColor;
```

### <a name="remarks"></a>Poznámky

##  <a name="m_clrrichpreviewtextcolor"></a>  CDocument::m_clrRichPreviewTextColor

Určuje barvu popředí v okně Náhled ve formátu RTF. Tato barva je nastavena podle hostitele.

```
COLORREF m_clrRichPreviewTextColor;
```

### <a name="remarks"></a>Poznámky

##  <a name="m_lfrichpreviewfont"></a>  CDocument::m_lfRichPreviewFont

Určuje písmo pro text pro okno náhledu. V těchto písmo je nastavená hostitelem.

```
CFont m_lfRichPreviewFont;
```

### <a name="remarks"></a>Poznámky

##  <a name="onbeforerichpreviewfontchanged"></a>  CDocument::OnBeforeRichPreviewFontChanged

Voláno před provedením změnit písmo pro náhled ve formátu RTF.

```
virtual void OnBeforeRichPreviewFontChanged();
```

### <a name="remarks"></a>Poznámky

##  <a name="onchangedviewlist"></a>  CDocument::OnChangedViewList

Volá se rozhraním po zobrazení je přidán či odebrán z dokumentu.

```
virtual void OnChangedViewList();
```

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce ověří, zda poslední zobrazení se odebírá a pokud ano, odstraní dokument. Tato funkce přepište, pokud chcete provést zvláštní zpracování v rámci přidá nebo odebere zobrazení. Například pokud chcete dokument zůstat otevřené i v případě, že nejsou k dispozici žádná zobrazení k němu připojená, přepište tuto funkci.

##  <a name="onclosedocument"></a>  CDocument::OnCloseDocument

Volá se rozhraním při zavření dokumentu, obvykle jako součást příkazu soubor zavřít.

```
virtual void OnCloseDocument();
```

### <a name="remarks"></a>Poznámky

Výchozí implementaci této funkce odstraní všechny rámce pro zobrazení dokumentu, zobrazení se zavře, vyčistí obsah dokumentu a pak zavolá [DeleteContents](#deletecontents) členskou funkci odstranění dokumentu. data.

Tato funkce přepište, pokud chcete provést zpracování zvláštního vyčištění po rozhraní zavření dokumentu. Například pokud dokument představuje záznam v databázi, můžete přepsat této funkce se zavřít databázi. Verze základní třídy tuto funkci byste měli volat z přepsání.

##  <a name="oncreatepreviewframe"></a>  CDocument::OnCreatePreviewFrame

Volá se rozhraním, když je nutné vytvořit objekt frame, ve verzi preview pro náhled ve formátu RTF.

```
virtual BOOL OnCreatePreviewFrame();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud rámec proběhne úspěšně; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="ondocumentevent"></a>  CDocument::OnDocumentEvent

Volá se rozhraním v reakci na událost dokumentu.

```
virtual void OnDocumentEvent(DocumentEvent deEvent);
```

### <a name="parameters"></a>Parametry

*deEvent*<br/>
[in] Výčtový datový typ, který popisuje typ události.

### <a name="remarks"></a>Poznámky

Události dokumentu může ovlivnit více tříd. Tato metoda je zodpovědná za zpracování událostí dokumentů, které ovlivňují tříd jiných než [CDocument – třída](../../mfc/reference/cdocument-class.md). V současné době je jedinou třídu, která musí reagovat na události dokumentu [cdatarecoveryhandler – třída](../../mfc/reference/cdatarecoveryhandler-class.md). `CDocument` Třída má jiné přepisovatelný metody zodpovědného za obsluhu vliv na `CDocument`.

V následující tabulce jsou uvedeny možné hodnoty pro *deEvent* a události, které odpovídají.

|Hodnota|Odpovídající události|
|-----------|-------------------------|
|`onAfterNewDocument`|Vytvořil se nový dokument.|
|`onAfterOpenDocument`|Byl otevřen nový dokument.|
|`onAfterSaveDocument`|Dokument byl uložen.|
|`onAfterCloseDocument`|Dokument byl ukončen.|

##  <a name="ondrawthumbnail"></a>  CDocument::OnDrawThumbnail

Potlačí tuto metodu v odvozené třídě pro kreslení na miniaturu.

```
virtual void OnDrawThumbnail(
    CDC& dc,
    LPRECT lprcBounds);
```

### <a name="parameters"></a>Parametry

*řadič domény*<br/>
Odkaz na kontext zařízení.

*lprcBounds*<br/>
Určuje ohraničující obdélník oblasti, ve kterém má být vykreslena miniaturu.

### <a name="remarks"></a>Poznámky

##  <a name="onfilesendmail"></a>  CDocument::OnFileSendMail

Odešle zprávu přes hostitele rezidenční e-mailu (pokud existuje) s dokumentem jako přílohu.

```
void OnFileSendMail();
```

### <a name="remarks"></a>Poznámky

`OnFileSendMail` volání [OnSaveDocument](#onsavedocument) k serializaci (bez názvu a upravené dokumenty do dočasného souboru, kterou pak odesílají prostřednictvím elektronické pošty Uložit). Pokud dokument nebyl změněn, není potřeba dočasný soubor; Původní se odesílají. `OnFileSendMail` načte MAPI32. Knihovny DLL, pokud ho ještě nenačetl.

Speciální implementaci `OnFileSendMail` pro [coledocument –](../../mfc/reference/coledocument-class.md) popisovače složené soubory správně.

`CDocument` zajišťuje podporu pro odesílání dokumentu e-mailem. Pokud je k dispozici podpora e-mailu (MAPI). Přečtěte si články [MAPI témata](../../mfc/mapi.md) a [Podpora MAPI v MFC](../../mfc/mapi-support-in-mfc.md).

##  <a name="onloaddocumentfromstream"></a>  CDocument::OnLoadDocumentFromStream

Volá se rozhraním, když je nutné načíst data dokumentu z datového proudu.

```
virtual HRESULT OnLoadDocumentFromStream(
    IStream* pStream,
    DWORD grfMode);
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
Ukazatel na příchozím datovém proudu.

*grfMode*<br/>
Režim přístupu do datového proudu.

### <a name="return-value"></a>Návratová hodnota

S_OK při úspěchu; zatížení jinak kód chyby.

### <a name="remarks"></a>Poznámky

##  <a name="onnewdocument"></a>  CDocument::OnNewDocument

Volá se rozhraním, jako součást příkazu soubor nový.

```
virtual BOOL OnNewDocument();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud dokument byl úspěšně inicializován; jinak 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce se volá [DeleteContents](#deletecontents) členská funkce zajistit, že dokument je prázdný a pak označí nový dokument jako čistý. Přepsání této funkce lze inicializovat strukturu dat pro nový dokument. Verze základní třídy tuto funkci byste měli volat z přepsání.

Pokud uživatel vybere příkaz Nový soubor v aplikaci SDI, rozhraní používá tuto funkci znovu inicializovat k existujícímu dokumentu a nevytvářejte nové. Pokud uživatel zvolí nový soubor v aplikaci (MDI interface) více dokumentů, rozhraní pokaždé, když vytvoří nový dokument a pak zavolá této funkce lze inicializovat ji. Je nutné umístit inicializační kód této funkce místo v konstruktoru pro příkaz Nový soubor bude platit v aplikace SDI.

Všimněte si, že existují případech, kdy `OnNewDocument` je volána dvakrát. K tomu dojde, když je dokument vložený jako Server dokument ActiveX. Funkce je nejprve volán `CreateInstance` – metoda (vystavené `COleObjectFactory`-odvozené třídy) a podruhé podle `InitNew` – metoda (vystavené `COleServerDoc`-odvozené třídy).

### <a name="example"></a>Příklad

Následující příklady znázorňují alternativní metody inicializace objektu dokumentu.

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

##  <a name="onopendocument"></a>  CDocument::OnOpenDocument

Volá se rozhraním, jako součást příkazu soubor otevřít.

```
virtual BOOL OnOpenDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
Odkazuje na cestu dokument otevřít.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud dokument byl úspěšně načten. jinak 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce se otevře zadaný soubor, volání [DeleteContents](#deletecontents) členské funkce zajistit, že dokument je prázdný, volá [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) do čtení tohoto souboru obsah a pak označí jako vyčistit dokument. Tato funkce přepište, pokud chcete použít něco než mechanismus archivu nebo mechanismus souborů. Například můžete například napsat aplikaci, ve kterém dokumentů představují záznamy v databázi spíš než samostatné soubory.

Pokud uživatel zvolí příkazu soubor otevřít v aplikaci SDI, systém použije tuto funkci opětovnou inicializaci existující `CDocument` objektu a nevytvářejte nové. Pokud uživatel vybere možnost otevřít soubor v aplikaci MDI, rozhraní sestaví nový `CDocument` pokaždé, když objekt a potom volání této funkce lze inicializovat ji. Je nutné umístit inicializační kód této funkce místo v konstruktoru pro příkaz Otevřít soubor se započítá aplikace SDI.

### <a name="example"></a>Příklad

Následující příklady znázorňují alternativní metody inicializace objektu dokumentu.

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

[!code-cpp[NVC_MFCDocView#63](../../mfc/codesnippet/cpp/cdocument-class_8.cpp)]

##  <a name="onpreviewhandlerqueryfocus"></a>  CDocument::OnPreviewHandlerQueryFocus

Obslužné rutiny náhledu se vraťte HWND získaných volání přesměruje `GetFocus` funkce.

```
virtual HRESULT OnPreviewHandlerQueryFocus(HWND* phwnd);
```

### <a name="parameters"></a>Parametry

*phwnd*<br/>
[out] Po návratu metody obsahuje ukazatel na HWND vrácená z volání `GetFocus` funkce z obslužné rutiny náhledu vlákno na popředí.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK v případě úspěchu; nebo jinak chybovou hodnotu.

### <a name="remarks"></a>Poznámky

##  <a name="onpreviewhandlertranslateaccelerator"></a>  CDocument::OnPreviewHandlerTranslateAccelerator

Určí, že obslužné rutiny náhledu pro zpracování jedním stisknutím tlačítka předány z pumpu zpráv procesu, ve kterém je spuštěna obslužná rutina ve verzi preview.

```
virtual HRESULT OnPreviewHandlerTranslateAccelerator(MSG* pmsg);
```

### <a name="parameters"></a>Parametry

*pmsg*<br/>
[in] Ukazatel na zprávy okna.

### <a name="return-value"></a>Návratová hodnota

Pokud stisknutí klávesy zprávy mohou být zpracovány obslužnou rutinu ve verzi preview, obslužná rutina zpracovává je a vrátí hodnotu S_OK. Pokud obslužné rutiny náhledu nelze zpracovat zprávu stisk klávesy, nabízí ji k hostiteli prostřednictvím `IPreviewHandlerFrame::TranslateAccelerator`. Pokud zprávu zpracuje hostitele, tato metoda vrátí hodnotu S_OK. Pokud hostitel nezpracovává zprávy, tato metoda vrátí S_FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="onrichpreviewbackcolorchanged"></a>  CDocument::OnRichPreviewBackColorChanged

Volá se, když se změní barva pozadí náhledu.

```
virtual void OnRichPreviewBackColorChanged();
```

### <a name="remarks"></a>Poznámky

##  <a name="onrichpreviewfontchanged"></a>  CDocument::OnRichPreviewFontChanged

Volá se při změně písmo pro náhled ve formátu RTF.

```
virtual void OnRichPreviewFontChanged();
```

### <a name="remarks"></a>Poznámky

##  <a name="onrichpreviewsitechanged"></a>  CDocument::OnRichPreviewSiteChanged

Volá se při změně webu náhled ve formátu RTF.

```
virtual void OnRichPreviewSiteChanged();
```

### <a name="remarks"></a>Poznámky

##  <a name="onrichpreviewtextcolorchanged"></a>  CDocument::OnRichPreviewTextColorChanged

Volá se, když se změní barva textu náhled ve formátu RTF.

```
virtual void OnRichPreviewTextColorChanged();
```

### <a name="remarks"></a>Poznámky

##  <a name="onsavedocument"></a>  CDocument::OnSaveDocument

Volá se rozhraním, jako součást příkazu soubor uložit nebo uložit jako.

```
virtual BOOL OnSaveDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
Odkazuje na plně kvalifikovanou cestu, do kterého byste soubor uložit.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud dokument se úspěšně uložila; jinak 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce se otevře zadaný soubor volání [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) zapsat data dokumentu do souboru a pak značky vyčistit dokument jako. Tato funkce přepište, pokud chcete provést zvláštní zpracování, když rozhraní framework uloží dokument. Například můžete například napsat aplikaci, ve kterém dokumentů představují záznamy v databázi spíš než samostatné soubory.

##  <a name="onunloadhandler"></a>  CDocument::OnUnloadHandler

Volá se rozhraním, když obslužnou rutinu ve verzi preview bude uvolněna.

```
virtual void OnUnloadHandler();
```

### <a name="remarks"></a>Poznámky

##  <a name="onupdatefilesendmail"></a>  CDocument::OnUpdateFileSendMail

Povolit příkaz ID_FILE_SEND_MAIL, pokud je k dispozici podpora e-mailu (MAPI).

```
void OnUpdateFileSendMail(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Ukazatel [ccmdui –](../../mfc/reference/ccmdui-class.md) objekt přidružený k příkazu ID_FILE_SEND_MAIL.

### <a name="remarks"></a>Poznámky

V opačném případě funkce odebere ID_FILE_SEND_MAIL příkaz z nabídky, včetně oddělovače nad nebo pod položku nabídky podle potřeby. Rozhraní MAPI je povolená, pokud MAPI32. Knihovna DLL je k dispozici v cestě a v části [e-mailu] VÍTĚZSTVÍ. Soubor INI, MAPI = 1. Většina aplikací umístit tento příkaz v nabídce Soubor.

`CDocument` zajišťuje podporu pro odesílání dokumentu e-mailem. Pokud je k dispozici podpora e-mailu (MAPI). Přečtěte si články [MAPI témata](../../mfc/mapi.md) a [Podpora MAPI v MFC](../../mfc/mapi-support-in-mfc.md).

##  <a name="precloseframe"></a>  CDocument::PreCloseFrame

Tato členská funkce je voláno rozhraním zničen okno rámce.

```
virtual void PreCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>Parametry

*pFrame*<br/>
Ukazatel [CFrameWnd](../../mfc/reference/cframewnd-class.md) obsahující přidružené `CDocument` objektu.

### <a name="remarks"></a>Poznámky

To může být potlačena za účelem poskytnout vlastní vyčištění, ale nezapomeňte volat základní třídy.

Výchozí `PreCloseFrame` nemá žádný účinek, `CDocument`. `CDocument`-Odvozené třídy [coledocument –](../../mfc/reference/coledocument-class.md) a [cricheditdoc –](../../mfc/reference/cricheditdoc-class.md) použít tuto členskou funkci.

##  <a name="readnextchunkvalue"></a>  CDocument::ReadNextChunkValue

Přečte další hodnotu bloku.

```
virtual BOOL ReadNextChunkValue(IFilterChunkValue** ppValue);
```

### <a name="parameters"></a>Parametry

*ppValue*<br/>
[out] Po návratu funkce *ppValue* obsahuje hodnotu, která byla načtena.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

##  <a name="releasefile"></a>  CDocument::ReleaseFile

Tato členská funkce se volá se rozhraním pro verzi souboru, takže k dispozici pro použití jiné aplikace.

```
virtual void ReleaseFile(
    CFile* pFile,
    BOOL bAbort);
```

### <a name="parameters"></a>Parametry

*pFile*<br/>
Ukazatel na objekt cfile – uvolnit.

*bAbort*<br/>
Určuje, zda je soubor uvolnit pomocí `CFile::Close` nebo `CFile::Abort`. FALSE, pokud má být uvolněna pomocí souboru [CFile::Close](../../mfc/reference/cfile-class.md#close); Hodnota TRUE, pokud má být uvolněna pomocí souboru [CFile::Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="remarks"></a>Poznámky

Pokud *bAbort* má hodnotu TRUE, `ReleaseFile` volání `CFile::Abort`, a soubor se uvolní. `CFile::Abort` nebude vyvolat výjimku.

Pokud *bAbort* má hodnotu FALSE, `ReleaseFile` volání `CFile::Close` a soubor se uvolní.

Tato členská funkce tak, aby vyžadovala akci uživatele, před vydáním soubor přepište.

##  <a name="removechunk"></a>  CDocument::RemoveChunk

Odebere bloků dat s identifikátorem GUID.

```
virtual void RemoveChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>Parametry

*identifikátor GUID*<br/>
Určuje identifikátor GUID blok, který se má odebrat.

*Identifikátor PID*<br/>
Určuje identifikátor PID blok má být odebrán.

### <a name="remarks"></a>Poznámky

##  <a name="removeview"></a>  CDocument::RemoveView

Voláním této funkce se odpojit zobrazení z dokumentu.

```
void RemoveView(CView* pView);
```

### <a name="parameters"></a>Parametry

*pView*<br/>
Odkazuje na zobrazení odebírá.

### <a name="remarks"></a>Poznámky

Tato funkce zruší zadané zobrazení Seznam zobrazení, které jsou přidružené k dokumentu. také nastaví zobrazení dokumentu ukazatel na hodnotu NULL. Tato funkce je volána rozhraním, když zavření okna rámce nebo je uzavřen do podokna okno s rozdělovačem.

Voláním této funkce jenom v případě, že jsou ručně odpojení zobrazení. Obvykle vám umožní rozhraní odpojit dokumentů a zobrazení tak, že definujete [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objektu, který chcete přidružit třídy dokumentu, zobrazení třídy a třídy oken s rámečkem.

Podívejte se na příklad na [AddView](#addview) ukázku implementace.

##  <a name="reportsaveloadexception"></a>  CDocument::ReportSaveLoadException

Volá se, pokud je vyvolána výjimka (obvykle [cfileexception –](../../mfc/reference/cfileexception-class.md) nebo [carchiveexception –](../../mfc/reference/carchiveexception-class.md)) při ukládání nebo načítání dokumentu.

```
virtual void ReportSaveLoadException(
    LPCTSTR lpszPathName,
    CException* e,
    BOOL bSaving,
    UINT nIDPDefault);
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
Odkazuje na název dokumentu, který byl právě uložit nebo načíst.

*e*<br/>
Odkazuje na výjimku, která byla vyvolána. Může mít hodnotu NULL.

*bSaving*<br/>
Příznak označující, jaké operace probíhala; nenulové, pokud se dokument uloží, 0 když načtení dokumentu.

*nIDPDefault*<br/>
Identifikátor chybové zprávy, který se má zobrazit, pokud funkce není uveden více konkrétní skupinu.

### <a name="remarks"></a>Poznámky

Výchozí implementace zkontroluje objektu výjimky a hledá chybovou zprávu, která speciálně popisuje příčinu. Pokud konkrétní zprávu nebyl nalezen nebo pokud *e* má hodnotu NULL, obecné zprávu určenou podle *nIDPDefault* parametr se používá. Funkce pak zobrazí okno se zprávou obsahující chybovou zprávu. Tato funkce přepište, pokud byste chtěli poskytnout další, vlastní chyby zprávy. To je moderní overridable.

##  <a name="savemodified"></a>  CDocument::SaveModified

Volá se rozhraním, než je upravený dokument bude uzavřen.

```
virtual BOOL SaveModified();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je bez obav pokračovat a uzavřít dokumentu. 0, pokud by neměla zavřít dokument.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce se zobrazí okno se zprávou s žádostí o, jestli se má uložit změny v dokumentu, pokud byly provedeny některé. Tato funkce přepište, pokud aplikace vyžaduje jinou proceduru vyzývá k tomu. To je moderní overridable.

##  <a name="setchunkvalue"></a>  CDocument::SetChunkValue

Nastaví hodnotu bloku.

```
virtual BOOL SetChunkValue (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>Parametry

*pValue*<br/>
Určuje hodnotu bloků dat pro nastavení.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

##  <a name="setmodifiedflag"></a>  CDocument::SetModifiedFlag

Voláním této funkce po provedení změny v dokumentu.

```
virtual void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Parametry

*bModified*<br/>
Příznak označující, zda byl změněn dokument.

### <a name="remarks"></a>Poznámky

Při volání této funkce konzistentně, zajistíte tím, že rozhraní vyzve uživatele k uložit změny před zavřením dokumentu. Obvykle byste měli použít výchozí hodnotu TRUE pro *bModified* parametru. Označit jako vyčistit dokument (bez úprav), voláním této funkce s hodnotou FALSE.

##  <a name="setpathname"></a>  CDocument::SetPathName

Voláním této funkce zadejte plně kvalifikovanou cestu souboru dokumentu na disku.

```
virtual void SetPathName(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
Odkazuje na řetězec, který se použije jako cestu pro dokument.

*bAddToMRU*<br/>
Určuje, zda název souboru se přidá do seznamu naposledy použitých seznam souborů (MRU). Při hodnotě TRUE se přidá název souboru; Pokud má hodnotu FALSE, tam není přidaný.

### <a name="remarks"></a>Poznámky

V závislosti na hodnotě z *bAddToMRU* cestu přidat, nebo nebyla přidána do seznamu naposledy použitých položek seznamu aplikací. Všimněte si, že některé dokumenty nejsou přiřazeny k souboru na disku. Voláním této funkce jenom v případě, že přepíšete výchozí implementace pro otevírání a ukládání souborů, používané rozhraním.

##  <a name="settitle"></a>  CDocument::SetTitle

Voláním této funkce k určení názvu dokumentu (je řetězec zobrazený v záhlaví okna rámce).

```
virtual void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>Parametry

*lpszTitle*<br/>
Odkazuje na řetězec, který se použije jako název dokumentu.

### <a name="remarks"></a>Poznámky

Volání této funkce aktualizace názvů všech oken s rámečkem, která zobrazují dokument.

##  <a name="updateallviews"></a>  CDocument::UpdateAllViews

Voláním této funkce po dokumentu se změnila.

```
void UpdateAllViews(
    CView* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL);
```

### <a name="parameters"></a>Parametry

*pSender*<br/>
Odkazuje na zobrazení, úpravy dokumentů, nebo hodnota NULL, pokud jsou všechna zobrazení aktualizovat.

*lHint*<br/>
Obsahuje informace o změnu.

*pHint*<br/>
Odkazuje na objekt ukládání informací o změnu.

### <a name="remarks"></a>Poznámky

Tuto funkci byste měli volat po volání [SetModifiedFlag](#setmodifiedflag) členskou funkci. Tuto funkci informuje každé zobrazení připojené k dokumentu, s výjimkou zobrazení určené *pSender*, který dokument se změnila. Obvykle volání této funkce z vaší třídy zobrazení po změně dokumentu prostřednictvím zobrazení uživatele.

Tato funkce volá [CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate) členskou funkci pro každý z dokumentu zobrazení s výjimkou odesílání zobrazit předáním hodnoty *pHint* a *lHint*. Pomocí těchto parametrů k předávání informací do zobrazení o změny provedené v dokumentu. Můžete kódovat informací pomocí *lHint* nebo můžete definovat [CObject](../../mfc/reference/cobject-class.md)-odvozené třídy k ukládání informací o změny a předejte objekt této třídy pomocí *pHint*. Přepsat `CView::OnUpdate` členské funkce ve vaší [CView](../../mfc/reference/cview-class.md)-odvozené třídy k optimalizaci aktualizuje zobrazení zobrazení na základě informací, které jsou předány.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#64](../../mfc/codesnippet/cpp/cdocument-class_9.cpp)]

## <a name="see-also"></a>Viz také

[Ukázky knihovny MFC MDIDOCVW](../../visual-cpp-samples.md)<br/>
[Ukázky knihovny MFC SNAPVW](../../visual-cpp-samples.md)<br/>
[Ukázky knihovny MFC agent NPP](../../visual-cpp-samples.md)<br/>
[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[CView – třída](../../mfc/reference/cview-class.md)<br/>
[CDocTemplate – třída](../../mfc/reference/cdoctemplate-class.md)
