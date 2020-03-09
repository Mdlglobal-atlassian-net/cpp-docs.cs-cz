---
title: Objektu CDocument – třída
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
ms.openlocfilehash: 2d87ff67000fb5b70c0a5c965638875e6f50b22c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856758"
---
# <a name="cdocument-class"></a>Objektu CDocument – třída

Poskytuje základní funkce pro uživatelsky definované třídy dokumentů.

## <a name="syntax"></a>Syntaxe

```
class CDocument : public CCmdTarget
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Objektu CDocument:: objektu CDocument](#cdocument)|Vytvoří objekt `CDocument`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Objektu CDocument:: AddView](#addview)|Připojí zobrazení k dokumentu.|
|[Objektu CDocument:: BeginReadChunks](#beginreadchunks)|Inicializuje čtení bloků dat.|
|[Objektu CDocument:: CanCloseFrame](#cancloseframe)|Rozšířené přepsatelné; volá se před zavřením okna rámce, které zobrazuje tento dokument.|
|[Objektu CDocument:: ClearChunkList](#clearchunklist)|Vymaže seznam bloků dat.|
|[Objektu CDocument:: ClearPathName](#clearpathname)|Vymaže cestu k objektu dokumentu.|
|[Objektu CDocument::D eleteContents](#deletecontents)|Volá se, aby se provedlo vyčištění dokumentu.|
|[Objektu CDocument:: FindChunk](#findchunk)|Vyhledá blok dat se zadaným identifikátorem GUID.|
|[Objektu CDocument:: getadapter](#getadapter)|Vrací ukazatel na objekt implementující `IDocument` rozhraní.|
|[Objektu CDocument:: GetDocTemplate](#getdoctemplate)|Vrátí ukazatel na šablonu dokumentu, která popisuje typ dokumentu.|
|[Objektu CDocument:: GetFile](#getfile)|Vrátí ukazatel na požadovaný objekt `CFile`.|
|[Objektu CDocument:: GetFirstViewPosition](#getfirstviewposition)|Vrátí pozici prvního v seznamu zobrazení; používá se k zahájení iterace.|
|[Objektu CDocument:: GetNextView](#getnextview)|Projde seznamem zobrazení přidružených k dokumentu.|
|[Objektu CDocument:: getcesta](#getpathname)|Vrátí cestu k datovému souboru dokumentu.|
|[Objektu CDocument:: GetThumbnail](#getthumbnail)|Volá se, aby se vytvořil rastrový obrázek, který se použije u poskytovatele miniatur k zobrazení miniatury.|
|[Objektu CDocument:: getTitle](#gettitle)|Vrátí název dokumentu.|
|[Objektu CDocument:: InitializeSearchContent](#initializesearchcontent)|Volá se, aby se inicializoval obsah hledání pro obslužnou rutinu hledání.|
|[Objektu CDocument::-Modified](#ismodified)|Uvádí, zda byl dokument od posledního uložení změněn.|
|[Objektu CDocument:: IsSearchAndOrganizeHandler](#issearchandorganizehandler)|Určuje, zda byla vytvořena tato instance `CDocument`ho objektu pro hledání & uspořádání obslužné rutiny.|
|[Objektu CDocument:: LoadDocumentFromStream](#loaddocumentfromstream)|Volá se, aby se načetla data dokumentu ze streamu.|
|[Objektu CDocument:: OnBeforeRichPreviewFontChanged](#onbeforerichpreviewfontchanged)|Volá se před změnou písma ve verzi Preview.|
|[Objektu CDocument:: OnChangedViewList](#onchangedviewlist)|Volá se po přidání nebo odebrání zobrazení z dokumentu.|
|[Objektu CDocument:: OnCloseDocument](#onclosedocument)|Volá se, aby se dokument zavřel.|
|[Objektu CDocument:: OnCreatePreviewFrame](#oncreatepreviewframe)|Volá se rozhraním, když je potřeba vytvořit rámec verze Preview pro bohatou verzi Preview.|
|[Objektu CDocument:: OnDocumentEvent](#ondocumentevent)|Volá se rozhraním v reakci na událost dokumentu.|
|[Objektu CDocument:: metodu ondrawthumbnail](#ondrawthumbnail)|Přepište tuto metodu v odvozené třídě pro vykreslení obsahu miniatury.|
|[Objektu CDocument:: OnLoadDocumentFromStream](#onloaddocumentfromstream)|Volá se rozhraním, když potřebuje načíst data dokumentu ze streamu.|
|[Objektu CDocument:: OnNewDocument](#onnewdocument)|Volá se, aby se vytvořil nový dokument.|
|[Objektu CDocument:: OnOpenDocument](#onopendocument)|Volá se, aby se otevřel existující dokument.|
|[Objektu CDocument:: OnPreviewHandlerQueryFocus](#onpreviewhandlerqueryfocus)|Nasměruje obslužnou rutinu Preview tak, aby vrátila HWND z volání funkce GetFocus.|
|[Objektu CDocument:: OnPreviewHandlerTranslateAccelerator](#onpreviewhandlertranslateaccelerator)|Nasměruje obslužnou rutinu Preview tak, aby zpracovala klávesovou zkratku, která je předána od čerpadla zpráv procesu, ve kterém je spuštěná obslužná rutina náhledu.|
|[Objektu CDocument:: OnRichPreviewBackColorChanged](#onrichpreviewbackcolorchanged)|Volá se, když se změní barva pozadí ve verzi Preview.|
|[Objektu CDocument:: OnRichPreviewFontChanged](#onrichpreviewfontchanged)|Volá se, když se změní písmo s bohatou náhledem.|
|[Objektu CDocument:: OnRichPreviewSiteChanged](#onrichpreviewsitechanged)|Volá se, když se změní web s bohatou verzí Preview.|
|[Objektu CDocument:: OnRichPreviewTextColorChanged](#onrichpreviewtextcolorchanged)|Volá se, když se změní barva textu s bohatou funkcí Preview.|
|[Objektu CDocument:: OnSaveDocument](#onsavedocument)|Volá se, aby se dokument uložil na disk.|
|[Objektu CDocument:: OnUnloadHandler](#onunloadhandler)|Volá se rozhraním, když se načítá obslužná rutina náhledu.|
|[Objektu CDocument::P reCloseFrame](#precloseframe)|Volá se před zavřením okna rámce.|
|[Objektu CDocument:: ReadNextChunkValue](#readnextchunkvalue)|Přečte další hodnotu bloku.|
|[Objektu CDocument:: ReleaseFile](#releasefile)|Uvolní soubor, který ho zpřístupní pro použití v jiných aplikacích.|
|[Objektu CDocument:: RemoveChunk](#removechunk)|Odebere blok dat se zadaným identifikátorem GUID.|
|[Objektu CDocument:: RemoveView](#removeview)|Odpojí zobrazení od dokumentu.|
|[Objektu CDocument:: ReportSaveLoadException](#reportsaveloadexception)|Rozšířené přepsatelné; volá se, když se operace otevření nebo uložení nedá dokončit z důvodu výjimky.|
|[Objektu CDocument:: SaveModified](#savemodified)|Rozšířené přepsatelné; volá se, aby se uživatel požádá o to, jestli se má dokument uložit.|
|[Objektu CDocument:: SetChunkValue](#setchunkvalue)|Nastaví hodnotu bloku.|
|[Objektu CDocument:: SetModifiedFlag](#setmodifiedflag)|Nastaví příznak označující, že jste dokument změnili od chvíle, kdy byl naposledy uložen.|
|[Objektu CDocument:: SetPathName](#setpathname)|Nastaví cestu k datovému souboru používanému dokumentem.|
|[Objektu CDocument:: SetTitle](#settitle)|Nastaví název dokumentu.|
|[Objektu CDocument:: UpdateAllViews](#updateallviews)|Upozorní všechna zobrazení, že dokument byl upraven.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[Objektu CDocument:: OnFileSendMail](#onfilesendmail)|Odešle e-mailovou zprávu s připojeným dokumentem.|
|[Objektu CDocument:: OnUpdateFileSendMail](#onupdatefilesendmail)|Povolí příkaz Odeslat poštu, pokud je k dispozici podpora pošty.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[Objektu CDocument:: m_bGetThumbnailMode](#m_bgetthumbnailmode)|Určuje, že objekt Dllhost pro miniatury vytvořil objekt `CDocument`. By mělo být vráceno se změnami `CView::OnDraw`.|
|[Objektu CDocument:: m_bPreviewHandlerMode](#m_bpreviewhandlermode)|Určuje, že `CDocument` objekt byl vytvořen pomocí prevhost pro `Rich Preview`. By mělo být vráceno se změnami `CView::OnDraw`.|
|[Objektu CDocument:: m_bSearchMode](#m_bsearchmode)|Určuje, že `CDocument` objekt byl vytvořen pomocí indexeru nebo jiné vyhledávací aplikace.|
|[Objektu CDocument:: m_clrRichPreviewBackColor](#m_clrrichpreviewbackcolor)|Určuje barvu pozadí okna ve verzi Preview. Tato barva je nastavena hostitelem.|
|[Objektu CDocument:: m_clrRichPreviewTextColor](#m_clrrichpreviewtextcolor)|Určuje barvu popředí okna s bohatou náhledem. Tato barva je nastavena hostitelem.|
|[Objektu CDocument:: m_lfRichPreviewFont](#m_lfrichpreviewfont)|Určuje písmo textu pro okno s bohatou náhledem. Informace o tomto písmu nastavuje hostitel.|

## <a name="remarks"></a>Poznámky

Dokument představuje jednotku dat, kterou uživatel obvykle otevírá, pomocí příkazu otevřít soubor a uloží soubor s příkazem Uložit.

`CDocument` podporuje standardní operace, jako je vytváření dokumentů, jejich načítání a ukládání. Rozhraní pracuje s dokumenty pomocí rozhraní definovaného `CDocument`.

Aplikace může podporovat více než jeden typ dokumentu; aplikace může například podporovat tabulky i textové dokumenty. Každý typ dokumentu má přidruženou šablonu dokumentu. Šablona dokumentu určuje, které prostředky (například nabídka, ikona nebo tabulka akcelerátorů) se použijí pro tento typ dokumentu. Každý dokument obsahuje ukazatel na jeho přidružený `CDocTemplate` objekt.

Uživatelé komunikují s dokumentem prostřednictvím přidružených objektů programu [CView](../../mfc/reference/cview-class.md) . Zobrazení Vykreslí obrázek dokumentu v okně rámce a interpretuje vstup uživatele jako operace v dokumentu. K dokumentu může být přidruženo více zobrazení. Když uživatel otevře okno v dokumentu, rozhraní vytvoří zobrazení a připojí ho k dokumentu. Šablona dokumentu určuje, jaký typ zobrazení a okno rámce se používá k zobrazení každého typu dokumentu.

Dokumenty jsou součástí standardního směrování příkazů rozhraní a následně přijímají příkazy ze standardních komponent uživatelského rozhraní (například položka nabídky Uložit soubor). Dokument přijímá příkazy předané aktivním zobrazením. Pokud dokument nezpracovává daný příkaz, předává příkaz do šablony dokumentu, která ho spravuje.

Při změně dat dokumentu musí každé z jeho zobrazení odrážet tyto změny. `CDocument` poskytuje členskou funkci [UpdateAllViews](#updateallviews) pro upozorňování zobrazení těchto změn, takže zobrazení mohou v případě potřeby překreslit sami. Rámec také vyzve uživatele k uložení upraveného souboru před jeho zavřením.

K implementaci dokumentů v typické aplikaci je nutné provést následující akce:

- Odvodit třídu z `CDocument` pro každý typ dokumentu.

- Přidejte členské proměnné pro uložení dat každého dokumentu.

- Implementujte členské funkce pro čtení a úpravy dat dokumentu. Zobrazení dokumentu jsou nejdůležitějšími uživateli těchto členských funkcí.

- Přepsat členskou funkci [CObject:: serializovat](../../mfc/reference/cobject-class.md#serialize) ve třídě dokumentu pro zápis a čtení dat dokumentu na disk a z disku.

`CDocument` podporuje odesílání dokumentů prostřednictvím pošty, pokud je k dispozici podpora pošty (MAPI). Přečtěte si článek podpora [rozhraní MAPI](../../mfc/mapi.md) a [MAPI v knihovně MFC](../../mfc/mapi-support-in-mfc.md).

Další informace o `CDocument`najdete v tématech [serializace](../../mfc/serialization-in-mfc.md), [dokument/zobrazení architektury](../../mfc/document-view-architecture.md)a [vytváření dokumentů a zobrazení](../../mfc/document-view-creation.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocument`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="addview"></a>Objektu CDocument:: AddView

Voláním této funkce připojte zobrazení k dokumentu.

```
void AddView(CView* pView);
```

### <a name="parameters"></a>Parametry

*pView*<br/>
Odkazuje na zobrazení, které chcete přidat.

### <a name="remarks"></a>Poznámky

Tato funkce přidá zadané zobrazení do seznamu zobrazení přidružených k dokumentu. funkce také nastaví ukazatel dokumentu zobrazení na tento dokument. Rozhraní volá tuto funkci při připojení nově vytvořeného objektu zobrazení k dokumentu. k tomu dochází v reakci na příkaz soubor nový, otevřít soubor nebo nové okno nebo v případě, že je rozdělené okno s rozdělovačem.

Tuto funkci volejte pouze v případě, že vytváříte a připojujete zobrazení ručně. Obvykle umožníte rozhraní připojit dokumenty a zobrazení definováním objektu [CDocTemplate –](../../mfc/reference/cdoctemplate-class.md) k přidružení třídy dokumentu třída, třídy zobrazení a třídy okna s rámečkem.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocViewSDI#12](../../mfc/codesnippet/cpp/cdocument-class_1.cpp)]

##  <a name="beginreadchunks"></a>Objektu CDocument:: BeginReadChunks

Inicializuje čtení bloků dat.

```
virtual void BeginReadChunks ();
```

### <a name="remarks"></a>Poznámky

##  <a name="cancloseframe"></a>Objektu CDocument:: CanCloseFrame

Volá se rozhraním, než se zavře okno rámce, ve kterém se dokument zobrazuje.

```
virtual BOOL CanCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>Parametry

*pFrame*<br/>
Odkazuje na okno rámce zobrazení připojeného k dokumentu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je bezpečné zavřít okno rámce; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace kontroluje, zda je dokument zobrazen v jiných oknech s rámečkem. Pokud je zadané okno rámce poslední, který dokument zobrazuje, funkce vyzve uživatele k uložení dokumentu, pokud byl upraven. Tuto funkci potlačíte, pokud chcete provádět zvláštní zpracování při zavření okna rámce. Toto je pokročilá přepsatelné.

##  <a name="cdocument"></a>Objektu CDocument:: objektu CDocument

Vytvoří objekt `CDocument`.

```
CDocument();
```

### <a name="remarks"></a>Poznámky

Rozhraní zpracovává vytváření dokumentů za vás. Přepsat členskou funkci [OnNewDocument](#onnewdocument) pro provedení inicializace na základě dokumentu; To je obzvláště důležité v aplikacích rozhraní SDI (Single Document Interface).

##  <a name="clearchunklist"></a>Objektu CDocument:: ClearChunkList

Vymaže seznam bloků dat.

```
virtual void ClearChunkList ();
```

### <a name="remarks"></a>Poznámky

##  <a name="clearpathname"></a>Objektu CDocument:: ClearPathName

Vymaže cestu k objektu dokumentu.

```
virtual void ClearPathName();
```

### <a name="remarks"></a>Poznámky

Vymazání cesty z objektu `CDocument` způsobí, že aplikace vyzve uživatele při příštím uložení dokumentu. Příkaz **Uložit** jako se bude chovat jako příkaz **Uložit jako** .

##  <a name="deletecontents"></a>Objektu CDocument::D eleteContents

Volá se rozhraním, aby se odstranila data dokumentu, aniž by se zničil samotný objekt `CDocument`.

```
virtual void DeleteContents();
```

### <a name="remarks"></a>Poznámky

Je volána těsně před tím, než bude dokument zničen. Je také volána, aby bylo zajištěno, že před jeho použitím bude dokument prázdný. To je důležité zejména pro aplikaci SDI, která používá pouze jeden dokument. Když uživatel vytvoří nebo otevře jiný dokument, dokument se znovu použije. Voláním této funkce Naimplementujte příkaz "upravit Clear All" nebo podobný příkaz, který odstraní všechna data dokumentu. Výchozí implementace této funkce neprovede žádnou akci. Přepsáním této funkce odstraníte data v dokumentu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#57](../../mfc/codesnippet/cpp/cdocument-class_2.cpp)]

##  <a name="findchunk"></a>Objektu CDocument:: FindChunk

Vyhledá blok dat se zadaným identifikátorem GUID.

```
virtual POSITION FindChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>Parametry

*hlavních*<br/>
Určuje identifikátor GUID bloku, který se má najít.

*PID*<br/>
Určuje PID bloku, který se má najít.

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu umístěte do interního seznamu bloků. Jinak NULL.

### <a name="remarks"></a>Poznámky

##  <a name="getadapter"></a>Objektu CDocument:: getadapter

Vrací ukazatel na objekt implementující rozhraní `IDocument`.

```
virtual ATL::IDocument* GetAdapter();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt implementující rozhraní `IDocument`.

### <a name="remarks"></a>Poznámky

##  <a name="getdoctemplate"></a>Objektu CDocument:: GetDocTemplate

Voláním této funkce získáte ukazatel na šablonu dokumentu pro tento typ dokumentu.

```
CDocTemplate* GetDocTemplate() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na šablonu dokumentu pro tento typ dokumentu nebo hodnotu NULL, pokud dokument není spravován šablonou dokumentu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#58](../../mfc/codesnippet/cpp/cdocument-class_3.cpp)]

##  <a name="getfile"></a>Objektu CDocument:: GetFile

Chcete-li získat ukazatel na objekt `CFile`, zavolejte tuto členskou funkci.

```
virtual CFile* GetFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CFileException* pError);
```

### <a name="parameters"></a>Parametry

*lpszFileName*<br/>
Řetězec, který představuje cestu k požadovanému souboru. Cesta může být relativní nebo absolutní.

*pError*<br/>
Ukazatel na existující objekt výjimky souboru, který určuje stav dokončení operace.

*nOpenFlags*<br/>
Režim sdílení a přístupu. Určuje akci, která se má provést při otevírání souboru. Můžete kombinovat možnosti uvedené v konstruktoru CFile – [CFile –:: CFile –](../../mfc/reference/cfile-class.md#cfile) pomocí operátoru OR (&#124;). Vyžaduje se jedno oprávnění k přístupu a jedna možnost sdílení. režimy `modeCreate` a `modeNoInherit` jsou volitelné.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt `CFile`.

##  <a name="getfirstviewposition"></a>Objektu CDocument:: GetFirstViewPosition

Voláním této funkce získáte pozici prvního zobrazení v seznamu zobrazení přidružených k dokumentu.

```
virtual POSITION GetFirstViewPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota pozice, kterou lze použít pro iteraci s členskou funkcí [GetNextView](#getnextview) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

##  <a name="getnextview"></a>Objektu CDocument:: GetNextView

Voláním této funkce můžete iterovat všemi zobrazeními dokumentu.

```
virtual CView* GetNextView(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*rPosition.*<br/>
Odkaz na hodnotu pozice vrácený předchozím voláním členských funkcí `GetNextView` nebo [GetFirstViewPosition](#getfirstviewposition) . Tato hodnota nesmí být NULL.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na zobrazení identifikovaný *rPosition.* .

### <a name="remarks"></a>Poznámky

Funkce vrátí zobrazení identifikované *rPosition.* a pak nastaví *RPOSITION.* na hodnotu pozice dalšího zobrazení v seznamu. Pokud je načtené zobrazení poslední v seznamu, pak je *rPosition.* nastaven na hodnotu null.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

##  <a name="getpathname"></a>Objektu CDocument:: getcesta

Voláním této funkce získáte plně kvalifikovanou cestu k souboru na disku dokumentu.

```
const CString& GetPathName() const;
```

### <a name="return-value"></a>Návratová hodnota

Plně kvalifikovaná cesta dokumentu Tento řetězec je prázdný, pokud dokument nebyl uložen nebo k němu není přidružen soubor disku.

##  <a name="getthumbnail"></a>Objektu CDocument:: GetThumbnail

Vytvoří rastrový obrázek, který má poskytovatel miniatury použít k zobrazení miniatury.

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
Obsahuje popisovač rastrového obrázku, pokud se funkce vrátí úspěšně.

*pdwAlpha*<br/>
Obsahuje DWORD určující hodnotu alfa kanálu, pokud se funkce vrátí úspěšně.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud byla rastrová mapa pro miniaturu vytvořena úspěšně. v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="gettitle"></a>Objektu CDocument:: getTitle

Voláním této funkce získáte název dokumentu, který je obvykle odvozen od názvu souboru dokumentu.

```
const CString& GetTitle() const;
```

### <a name="return-value"></a>Návratová hodnota

Název dokumentu.

##  <a name="initializesearchcontent"></a>Objektu CDocument:: InitializeSearchContent

Volá se, aby se inicializoval obsah hledání pro obslužnou rutinu hledání.

```
virtual void InitializeSearchContent ();
```

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu v odvozené třídě pro inicializaci obsahu hledání. Obsah by měl být řetězec s částmi oddělenými znakem ";". Například "Point; plocha položka OLE ".

##  <a name="ismodified"></a>Objektu CDocument::-Modified

Voláním této funkce zjistíte, zda byl dokument od posledního uložení změněn.

```
virtual BOOL IsModified();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl dokument od posledního uložení změněn; v opačném případě 0.

##  <a name="issearchandorganizehandler"></a>Objektu CDocument:: IsSearchAndOrganizeHandler

Určuje, zda byla vytvořena tato instance `CDocument` pro hledání & uspořádání obslužné rutiny.

```
BOOL IsSearchAndOrganizeHandler() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu pravda, pokud byla tato instance `CDocument` vytvořena pro hledání & uspořádání obslužné rutiny.

### <a name="remarks"></a>Poznámky

V současné době tato funkce vrací hodnotu TRUE pouze pro obslužné rutiny ve verzi Preview, které jsou implementovány na serveru mimo proces. Můžete nastavit odpovídající příznaky (m_bPreviewHandlerMode, m_bSearchMode, m_bGetThumbnailMode) na úrovni aplikace, aby tato funkce vrátila hodnotu TRUE.

##  <a name="loaddocumentfromstream"></a>Objektu CDocument:: LoadDocumentFromStream

Volá se, aby se načetla data dokumentu z datového proudu.

```
virtual HRESULT LoadDocumentFromStream(
    IStream* pStream,
    DWORD dwGrfMode);
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
Ukazatel na datový proud. Tento datový proud poskytuje prostředí.

*dwGrfMode*<br/>
Režim přístupu ke streamu.

### <a name="return-value"></a>Návratová hodnota

S_OK, zda je operace načítání úspěšná, jinak HRESULT s kódem chyby.

### <a name="remarks"></a>Poznámky

Tuto metodu můžete přepsat v odvozené třídě a přizpůsobit tak, jak načíst data z datového proudu.

##  <a name="m_bgetthumbnailmode"></a>Objektu CDocument:: m_bGetThumbnailMode

Určuje, že objekt Dllhost vytvořil pro miniatury objekt `CDocument`. By mělo být vráceno se změnami `CView::OnDraw`.

```
BOOL m_bGetThumbnailMode;
```

### <a name="remarks"></a>Poznámky

`TRUE` označuje, že byl dokument vytvořen pomocí procesu Dllhost pro miniatury.

##  <a name="m_bpreviewhandlermode"></a>Objektu CDocument:: m_bPreviewHandlerMode

Určuje, že objekt `CDocument` byl vytvořen pomocí prevhost pro bohatou verzi Preview. By mělo být vráceno se změnami `CView::OnDraw`.

```
BOOL m_bPreviewHandlerMode;
```

### <a name="remarks"></a>Poznámky

Hodnota TRUE označuje, že byl dokument vytvořen pomocí prevhost pro Rich Preview.

##  <a name="m_bsearchmode"></a>Objektu CDocument:: m_bSearchMode

Určuje, že objekt `CDocument` byl vytvořen pomocí indexeru nebo jiné vyhledávací aplikace.

```
BOOL m_bSearchMode;
```

### <a name="remarks"></a>Poznámky

`TRUE` označuje, že dokument byl vytvořen pomocí indexeru nebo jiné vyhledávací aplikace.

##  <a name="m_clrrichpreviewbackcolor"></a>Objektu CDocument:: m_clrRichPreviewBackColor

Určuje barvu pozadí okna s bohatou náhledem. Tato barva je nastavena hostitelem.

```
COLORREF m_clrRichPreviewBackColor;
```

### <a name="remarks"></a>Poznámky

##  <a name="m_clrrichpreviewtextcolor"></a>Objektu CDocument:: m_clrRichPreviewTextColor

Určuje barvu popředí okna s bohatou náhledem. Tato barva je nastavena hostitelem.

```
COLORREF m_clrRichPreviewTextColor;
```

### <a name="remarks"></a>Poznámky

##  <a name="m_lfrichpreviewfont"></a>Objektu CDocument:: m_lfRichPreviewFont

Určuje písmo textu pro okno s bohatou náhledem. Informace o tomto písmu nastavuje hostitel.

```
CFont m_lfRichPreviewFont;
```

### <a name="remarks"></a>Poznámky

##  <a name="onbeforerichpreviewfontchanged"></a>Objektu CDocument:: OnBeforeRichPreviewFontChanged

Volá se před změnou písma s bohatou náhledem.

```
virtual void OnBeforeRichPreviewFontChanged();
```

### <a name="remarks"></a>Poznámky

##  <a name="onchangedviewlist"></a>Objektu CDocument:: OnChangedViewList

Volá se rozhraním po přidání nebo odebrání zobrazení z dokumentu.

```
virtual void OnChangedViewList();
```

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce kontroluje, zda bylo odebráno poslední zobrazení, a pokud ano, tento dokument odstraní. Tuto funkci potlačíte, pokud chcete provádět zvláštní zpracování, když rozhraní přidá nebo odebere zobrazení. Například pokud chcete, aby dokument zůstal otevřený i v případě, že k němu nejsou připojená žádná zobrazení, přepište tuto funkci.

##  <a name="onclosedocument"></a>Objektu CDocument:: OnCloseDocument

Volá se rozhraním, když je dokument uzavřený, obvykle jako součást příkazu Zavřít soubor.

```
virtual void OnCloseDocument();
```

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce zničí všechny snímky použité pro zobrazení dokumentu, zavře zobrazení, vyčistí obsah dokumentu a pak zavolá členskou funkci [DeleteContents](#deletecontents) , která odstraní data dokumentu.

Tuto funkci přepište, pokud chcete provést speciální zpracování čištění, když rozhraní zavírá dokument. Pokud dokument například představuje záznam v databázi, může být vhodné tuto funkci přepsat, aby se databáze zavřela. Měli byste volat verzi základní třídy této funkce z přepsání.

##  <a name="oncreatepreviewframe"></a>Objektu CDocument:: OnCreatePreviewFrame

Volá se rozhraním, když je potřeba vytvořit rámec verze Preview pro bohatou verzi Preview.

```
virtual BOOL OnCreatePreviewFrame();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je snímek vytvořen úspěšně; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="ondocumentevent"></a>Objektu CDocument:: OnDocumentEvent

Volá se rozhraním v reakci na událost dokumentu.

```
virtual void OnDocumentEvent(DocumentEvent deEvent);
```

### <a name="parameters"></a>Parametry

*bez ohledu*<br/>
pro Výčtový datový typ, který popisuje typ události.

### <a name="remarks"></a>Poznámky

Události dokumentu mohou ovlivnit více tříd. Tato metoda zodpovídá za zpracování událostí dokumentu, které ovlivňují jiné třídy než [Třída objektu CDocument](../../mfc/reference/cdocument-class.md). V současné době je jediná třída, která musí reagovat na události dokumentu, [Třída CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md). Třída `CDocument` má jiné metody s přepsáním, které jsou zodpovědné za zpracování efektu na `CDocument`.

V následující tabulce jsou uvedeny možné hodnoty pro možnosti *nerovnoměrného* a pro události, které odpovídají.

|Hodnota|Odpovídající událost|
|-----------|-------------------------|
|`onAfterNewDocument`|Byl vytvořen nový dokument.|
|`onAfterOpenDocument`|Byl otevřen nový dokument.|
|`onAfterSaveDocument`|Dokument byl uložen.|
|`onAfterCloseDocument`|Dokument byl zavřen.|

##  <a name="ondrawthumbnail"></a>Objektu CDocument:: metodu ondrawthumbnail

Přepište tuto metodu v odvozené třídě pro vykreslení miniatury.

```
virtual void OnDrawThumbnail(
    CDC& dc,
    LPRECT lprcBounds);
```

### <a name="parameters"></a>Parametry

*DC*<br/>
Odkaz na kontext zařízení.

*lprcBounds*<br/>
Určuje ohraničující obdélník oblasti, kde má být vykreslena miniatura.

### <a name="remarks"></a>Poznámky

##  <a name="onfilesendmail"></a>Objektu CDocument:: OnFileSendMail

Pošle zprávu prostřednictvím hostitele rezidentního e-mailu (pokud existuje) s dokumentem jako přílohou.

```
void OnFileSendMail();
```

### <a name="remarks"></a>Poznámky

`OnFileSendMail` volá [OnSaveDocument](#onsavedocument) k serializaci (uložení) bez názvu a změněných dokumentů do dočasného souboru, který se pak pošle prostřednictvím elektronické pošty. Pokud dokument nebyl upraven, dočasný soubor není potřeba. původní odeslání. `OnFileSendMail` načte MAPI32. DLL, pokud ještě nebyla načtena.

Speciální implementace `OnFileSendMail` pro [COleDocument](../../mfc/reference/coledocument-class.md) zpracovává složené soubory správně.

`CDocument` podporuje odesílání dokumentů prostřednictvím pošty, pokud je k dispozici podpora pošty (MAPI). Viz články [rozhraní MAPI](../../mfc/mapi.md) a [Podpora rozhraní MAPI v knihovně MFC](../../mfc/mapi-support-in-mfc.md).

##  <a name="onloaddocumentfromstream"></a>Objektu CDocument:: OnLoadDocumentFromStream

Volá se rozhraním, když potřebuje načíst data dokumentu z datového proudu.

```
virtual HRESULT OnLoadDocumentFromStream(
    IStream* pStream,
    DWORD grfMode);
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
Ukazatel na příchozí datový proud.

*grfMode*<br/>
Režim přístupu ke streamu.

### <a name="return-value"></a>Návratová hodnota

S_OK, pokud je zatížení úspěšné; v opačném případě kód chyby.

### <a name="remarks"></a>Poznámky

##  <a name="onnewdocument"></a>Objektu CDocument:: OnNewDocument

Volá se rozhraním jako součást příkazu soubor nový.

```
virtual BOOL OnNewDocument();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl dokument úspěšně inicializován; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce volá členskou funkci [DeleteContents](#deletecontents) , aby zajistila, že je dokument prázdný, a označí nový dokument jako čistý. Přepište tuto funkci pro inicializaci struktury dat pro nový dokument. Měli byste volat verzi základní třídy této funkce z přepsání.

Pokud uživatel zvolí příkaz soubor New v aplikaci SDI, rozhraní použije tuto funkci k opětovné inicializaci stávajícího dokumentu místo vytvoření nového. Pokud uživatel zvolí v aplikaci MDI (Multiple Document Interface) nový soubor, rozhraní vytvoří nový dokument pokaždé, když zavolá tuto funkci, aby ji inicializoval. Do této funkce je nutné umístit inicializační kód místo v konstruktoru pro příkaz File New, který bude platný v aplikacích SDI.

Všimněte si, že existují případy, kdy je `OnNewDocument` volána dvakrát. K tomu dochází, když je dokument vložený jako server dokumentu ActiveX. Funkce je nejprve volána metodou `CreateInstance` (zpřístupněna třídou odvozenou `COleObjectFactory`) a druhým časem metodou `InitNew` (vystavenou třídou odvozenou od `COleServerDoc`).

### <a name="example"></a>Příklad

Následující příklady ilustrují alternativní metody inicializace objektu dokumentu.

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

##  <a name="onopendocument"></a>Objektu CDocument:: OnOpenDocument

Volá se rozhraním jako součást příkazu otevřít soubor.

```
virtual BOOL OnOpenDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
Odkazuje na cestu k dokumentu, který má být otevřen.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl dokument úspěšně načten; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce otevře zadaný soubor, zavolá členskou funkci [DeleteContents](#deletecontents) , aby zajistila, že je dokument prázdný, volá [CObject:: serializovat](../../mfc/reference/cobject-class.md#serialize) pro čtení obsahu souboru a pak označí dokument jako čistý. Tuto funkci potlačíte, pokud chcete použít jinou hodnotu než archivní mechanizmus nebo souborový mechanismus. Můžete například napsat aplikaci, kde dokumenty reprezentují záznamy v databázi, a ne samostatné soubory.

Pokud uživatel zvolí příkaz Otevřít v aplikaci SDI, rozhraní použije tuto funkci k opětovné inicializaci stávajícího `CDocument` objektu místo vytvoření nového. Pokud uživatel zvolí soubor otevřený v aplikaci MDI, rozhraní vytvoří nový objekt `CDocument` pokaždé, když zavolá tuto funkci, aby ji inicializoval. Místo v konstruktoru příkazu pro otevření souboru, který bude platný v aplikacích SDI, je nutné do této funkce umístit inicializační kód.

### <a name="example"></a>Příklad

Následující příklady ilustrují alternativní metody inicializace objektu dokumentu.

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

[!code-cpp[NVC_MFCDocView#63](../../mfc/codesnippet/cpp/cdocument-class_8.cpp)]

##  <a name="onpreviewhandlerqueryfocus"></a>Objektu CDocument:: OnPreviewHandlerQueryFocus

Nasměruje obslužnou rutinu Preview tak, aby vracela HWND načtený z volání funkce `GetFocus`.

```
virtual HRESULT OnPreviewHandlerQueryFocus(HWND* phwnd);
```

### <a name="parameters"></a>Parametry

*phwnd*<br/>
mimo Když tato metoda vrátí, obsahuje ukazatel na HWND vrácený voláním funkce `GetFocus` z vlákna popředí obslužné rutiny ve verzi Preview.

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí S_OK. nebo jinak chybová hodnota.

### <a name="remarks"></a>Poznámky

##  <a name="onpreviewhandlertranslateaccelerator"></a>Objektu CDocument:: OnPreviewHandlerTranslateAccelerator

Nasměruje obslužnou rutinu Preview tak, aby zpracovala klávesovou zkratku, která je předána od čerpadla zpráv procesu, ve kterém je spuštěná obslužná rutina náhledu.

```
virtual HRESULT OnPreviewHandlerTranslateAccelerator(MSG* pmsg);
```

### <a name="parameters"></a>Parametry

*pmsg*<br/>
pro Ukazatel na zprávu okna.

### <a name="return-value"></a>Návratová hodnota

Pokud může být zpráva klávesová zkratka zpracována obslužnou rutinou Preview, obslužná rutina ji zpracuje a vrátí S_OK. Pokud obslužná rutina náhledu nemůže zpracovat zprávu s klávesovou zkratkou, nabídne ji hostiteli prostřednictvím `IPreviewHandlerFrame::TranslateAccelerator`. Pokud hostitel tuto zprávu zpracuje, vrátí tato metoda S_OK. Pokud hostitel zprávu nezpracovává, vrátí tato metoda S_FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="onrichpreviewbackcolorchanged"></a>Objektu CDocument:: OnRichPreviewBackColorChanged

Volá se, když se změní barva pozadí s bohatou náhledem.

```
virtual void OnRichPreviewBackColorChanged();
```

### <a name="remarks"></a>Poznámky

##  <a name="onrichpreviewfontchanged"></a>Objektu CDocument:: OnRichPreviewFontChanged

Volá se, když se změní písmo s bohatou náhledem.

```
virtual void OnRichPreviewFontChanged();
```

### <a name="remarks"></a>Poznámky

##  <a name="onrichpreviewsitechanged"></a>Objektu CDocument:: OnRichPreviewSiteChanged

Volá se, když se změní web s bohatou verzí Preview.

```
virtual void OnRichPreviewSiteChanged();
```

### <a name="remarks"></a>Poznámky

##  <a name="onrichpreviewtextcolorchanged"></a>Objektu CDocument:: OnRichPreviewTextColorChanged

Volá se, když se změní barva textu s bohatou funkcí Preview.

```
virtual void OnRichPreviewTextColorChanged();
```

### <a name="remarks"></a>Poznámky

##  <a name="onsavedocument"></a>Objektu CDocument:: OnSaveDocument

Volá se rozhraním jako součást příkazu soubor uložit nebo Uložit jako.

```
virtual BOOL OnSaveDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
Odkazuje na plně kvalifikovanou cestu, do které má být soubor uložen.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl dokument úspěšně uložen; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce otevře zadaný soubor, zavolá [CObject:: serializovat](../../mfc/reference/cobject-class.md#serialize) k zápisu dat dokumentu do souboru a pak označí dokument jako čistý. Tuto funkci přepište, pokud chcete provádět zvláštní zpracování, když rozhraní ukládá dokument. Můžete například napsat aplikaci, kde dokumenty reprezentují záznamy v databázi, a ne samostatné soubory.

##  <a name="onunloadhandler"></a>Objektu CDocument:: OnUnloadHandler

Volá se rozhraním, když je obslužná rutina náhledu uvolněná.

```
virtual void OnUnloadHandler();
```

### <a name="remarks"></a>Poznámky

##  <a name="onupdatefilesendmail"></a>Objektu CDocument:: OnUpdateFileSendMail

Povolí příkaz ID_FILE_SEND_MAIL, pokud je k dispozici podpora pošty (MAPI).

```
void OnUpdateFileSendMail(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Ukazatel na objekt [CCmdUI –](../../mfc/reference/ccmdui-class.md) přidružený k příkazu ID_FILE_SEND_MAIL.

### <a name="remarks"></a>Poznámky

V opačném případě funkce z nabídky odstraní příkaz ID_FILE_SEND_MAIL, včetně oddělovačů výše nebo pod položkou nabídky. Rozhraní MAPI je povoleno v případě MAPI32. Knihovna DLL je k dispozici v cestě a v části [pošta] v souboru WIN. Soubor INI, MAPI = 1. Většina aplikací tento příkaz umístí do nabídky soubor.

`CDocument` podporuje odesílání dokumentů prostřednictvím pošty, pokud je k dispozici podpora pošty (MAPI). Viz články [rozhraní MAPI](../../mfc/mapi.md) a [Podpora rozhraní MAPI v knihovně MFC](../../mfc/mapi-support-in-mfc.md).

##  <a name="precloseframe"></a>Objektu CDocument::P reCloseFrame

Tato členská funkce je volána rozhraním před zničením okna rámce.

```
virtual void PreCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>Parametry

*pFrame*<br/>
Ukazatel na [CFrameWnd](../../mfc/reference/cframewnd-class.md) , který obsahuje přidružený objekt `CDocument`.

### <a name="remarks"></a>Poznámky

Může být přepsáno, aby poskytovalo vlastní vyčištění, ale měli byste volat také základní třídu.

Výchozí hodnota `PreCloseFrame` neprovede žádné akce v `CDocument`. Třídy odvozené od `CDocument`[COleDocument](../../mfc/reference/coledocument-class.md) a [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) používají tuto členskou funkci.

##  <a name="readnextchunkvalue"></a>Objektu CDocument:: ReadNextChunkValue

Přečte další hodnotu bloku.

```
virtual BOOL ReadNextChunkValue(IFilterChunkValue** ppValue);
```

### <a name="parameters"></a>Parametry

*ppValue*<br/>
mimo Když funkce vrátí, *ppValue* obsahuje hodnotu, která byla přečtena.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

##  <a name="releasefile"></a>Objektu CDocument:: ReleaseFile

Tato členská funkce je volána rozhraním k uvolnění souboru, takže je k dispozici pro použití v jiných aplikacích.

```
virtual void ReleaseFile(
    CFile* pFile,
    BOOL bAbort);
```

### <a name="parameters"></a>Parametry

*pFile*<br/>
Ukazatel na objekt CFile –, který se má uvolnit.

*bAbort*<br/>
Určuje, zda se má soubor vydat pomocí `CFile::Close` nebo `CFile::Abort`. FALSE, pokud se má soubor vydat pomocí [CFile –:: Close](../../mfc/reference/cfile-class.md#close); Hodnota TRUE, pokud má být soubor vydaný pomocí [CFile –:: Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="remarks"></a>Poznámky

Pokud má *bAbort* hodnotu TRUE, `ReleaseFile` volá `CFile::Abort`a soubor se uvolní. `CFile::Abort` nevyvolá výjimku.

Pokud má *bAbort* hodnotu FALSE, `ReleaseFile` volání `CFile::Close` a soubor se uvolní.

Přepište tuto členskou funkci tak, aby vyžadovala akci uživatele předtím, než se soubor uvolní.

##  <a name="removechunk"></a>Objektu CDocument:: RemoveChunk

Odebere blok dat se zadaným identifikátorem GUID.

```
virtual void RemoveChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>Parametry

*Hlavních*<br/>
Určuje identifikátor GUID bloku, který se má odebrat.

*PID*<br/>
Určuje PID bloku, který se má odebrat.

### <a name="remarks"></a>Poznámky

##  <a name="removeview"></a>Objektu CDocument:: RemoveView

Voláním této funkce odpojíte zobrazení od dokumentu.

```
void RemoveView(CView* pView);
```

### <a name="parameters"></a>Parametry

*pView*<br/>
Odkazuje na zobrazení, které se odebírá.

### <a name="remarks"></a>Poznámky

Tato funkce Odebere zadané zobrazení ze seznamu zobrazení přidružených k dokumentu. také nastaví ukazatel dokumentu zobrazení na hodnotu NULL. Tato funkce je volána rozhraním, když je zavřeno okno rámce nebo je zavřeno podokno okna s rozdělovačem.

Tuto funkci volejte pouze v případě ručního odpojení některého zobrazení. Obvykle umožníte rozhraní odpojit dokumenty a zobrazení definováním objektu [CDocTemplate –](../../mfc/reference/cdoctemplate-class.md) k přidružení třídy dokumentu třída, třídy zobrazení a třídy okna s rámečkem.

Ukázkovou implementaci najdete v příkladu na adrese [AddView](#addview) .

##  <a name="reportsaveloadexception"></a>Objektu CDocument:: ReportSaveLoadException

Volá se, pokud se při ukládání nebo načítání dokumentu vyvolá výjimka (obvykle se jedná o [CFileException](../../mfc/reference/cfileexception-class.md) nebo [CArchiveException](../../mfc/reference/carchiveexception-class.md)).

```
virtual void ReportSaveLoadException(
    LPCTSTR lpszPathName,
    CException* e,
    BOOL bSaving,
    UINT nIDPDefault);
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
Odkazuje na název dokumentu, který byl uložen nebo načten.

*cerebrální*<br/>
Odkazuje na výjimku, která byla vyvolána. Může mít hodnotu NULL.

*bSaving*<br/>
Příznak označující, která operace probíhala; nenulová, pokud byl dokument uložen, 0, pokud byl dokument načten.

*nIDPDefault*<br/>
Identifikátor chybové zprávy, která se má zobrazit, pokud funkce neurčí konkrétnější.

### <a name="remarks"></a>Poznámky

Výchozí implementace prozkoumá objekt výjimky a vyhledá chybovou zprávu, která konkrétně popisuje příčinu. Pokud se konkrétní zpráva nenajde nebo pokud je hodnota *e* null, použije se obecná zpráva určená parametrem *nIDPDefault* . Funkce pak zobrazí okno se zprávou obsahující chybovou zprávu. Tuto funkci přepište, pokud chcete zadat další, přizpůsobené zprávy o chybách. Toto je pokročilá přepsatelné.

##  <a name="savemodified"></a>Objektu CDocument:: SaveModified

Volá se rozhraním, aby se zavřel upravený dokument.

```
virtual BOOL SaveModified();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je bezpečné pokračovat a zavřít dokument; 0, pokud by se dokument neměl zavřít.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce zobrazí okno se zprávou s dotazem, zda chcete změny uložit do dokumentu, pokud byly provedeny nějaké změny. Tuto funkci popište, pokud váš program vyžaduje jinou proceduru dotazování. Toto je pokročilá přepsatelné.

##  <a name="setchunkvalue"></a>Objektu CDocument:: SetChunkValue

Nastaví hodnotu bloku.

```
virtual BOOL SetChunkValue (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>Parametry

*pValue*<br/>
Určuje hodnotu bloku, která se má nastavit.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

##  <a name="setmodifiedflag"></a>Objektu CDocument:: SetModifiedFlag

Po provedení jakýchkoli úprav dokumentu volejte tuto funkci.

```
virtual void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Parametry

*bModified*<br/>
Příznak označující, zda byl dokument změněn

### <a name="remarks"></a>Poznámky

Když zavoláte tuto funkci konzistentně, zajistíte, že rozhraní před zavřením dokumentu vyzve uživatele k uložení změn. Obvykle byste měli použít výchozí hodnotu TRUE pro parametr *bModified* . Chcete-li dokument označit jako čistý (nezměněný), zavolejte tuto funkci s hodnotou FALSE.

##  <a name="setpathname"></a>Objektu CDocument:: SetPathName

Voláním této funkce určíte plně kvalifikovanou cestu k souboru na disku dokumentu.

```
virtual void SetPathName(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
Odkazuje na řetězec, který má být použit jako cesta k dokumentu.

*bAddToMRU*<br/>
Určuje, zda je název souboru přidán do seznamu naposledy použitých souborů (MRU). Pokud je nastaveno na TRUE, název souboru se přidá; Pokud je hodnota FALSE, není přidána.

### <a name="remarks"></a>Poznámky

V závislosti na hodnotě *bAddToMRU* se cesta přidá nebo nepřidá do seznamu naposledy udržovaných aplikací. Všimněte si, že některé dokumenty nejsou přidruženy k souboru na disku. Tuto funkci volejte pouze v případě, že přepisujete výchozí implementaci pro otevírání a ukládání souborů používaných rozhraním.

##  <a name="settitle"></a>Objektu CDocument:: SetTitle

Voláním této funkce určíte název dokumentu (řetězec zobrazený v záhlaví okna rámce).

```
virtual void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>Parametry

*lpszTitle*<br/>
Odkazuje na řetězec, který má být použit jako nadpis dokumentu.

### <a name="remarks"></a>Poznámky

Volání této funkce aktualizuje názvy všech oken snímků, které dokument zobrazují.

##  <a name="updateallviews"></a>Objektu CDocument:: UpdateAllViews

Po úpravě dokumentu volejte tuto funkci.

```
void UpdateAllViews(
    CView* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL);
```

### <a name="parameters"></a>Parametry

*pSender*<br/>
Odkazuje na zobrazení, které upravilo dokument, nebo hodnotu NULL, pokud mají být aktualizována všechna zobrazení.

*lHint*<br/>
Obsahuje informace o změně.

*pHint*<br/>
Odkazuje na objekt, který ukládá informace o změně.

### <a name="remarks"></a>Poznámky

Tuto funkci byste měli zavolat po volání členské funkce [SetModifiedFlag](#setmodifiedflag) . Tato funkce informuje všechna zobrazení připojená k dokumentu s výjimkou zobrazení zadaného parametrem *pSender*, že byl dokument změněn. Tato funkce se obvykle volá z vaší třídy zobrazení poté, co uživatel změnil dokument v zobrazení.

Tato funkce volá členskou funkci [CView:: proupdate](../../mfc/reference/cview-class.md#onupdate) pro každé zobrazení dokumentu s výjimkou zobrazení odeslání a předávání *pHint* a *lHint*. Tyto parametry použijte k předání informací do zobrazení o změnách provedených v dokumentu. Můžete kódovat informace pomocí *lHint* a/nebo můžete definovat třídu odvozenou [CObject](../../mfc/reference/cobject-class.md)pro ukládání informací o úpravách a předání objektu této třídy pomocí *pHint*. Přepište členskou funkci `CView::OnUpdate` v třídě odvozené do programu [CView](../../mfc/reference/cview-class.md)za účelem optimalizace aktualizace zobrazení zobrazení na základě předaných informací.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#64](../../mfc/codesnippet/cpp/cdocument-class_9.cpp)]

## <a name="see-also"></a>Viz také

[MDIDOCVW Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[SNAPVW Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[NPP Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[CView – třída](../../mfc/reference/cview-class.md)<br/>
[CDocTemplate – třída](../../mfc/reference/cdoctemplate-class.md)
