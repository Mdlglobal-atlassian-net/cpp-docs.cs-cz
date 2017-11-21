---
title: "CDocument – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c6cfe4dc779fb4ad50f2171ef8811785f48275a9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cdocument-class"></a>CDocument – třída
Poskytuje základní funkce pro třídy dokumentů definovaný uživatelem.  
  
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
|[CDocument::AddView](#addview)|Zobrazení se připojí k dokumentu.|  
|[CDocument::BeginReadChunks](#beginreadchunks)|Inicializuje bloku dat čtení.|  
|[CDocument::CanCloseFrame](#cancloseframe)|Rozšířené přepisovatelné; volá se před jeho zavřením okně s rámečkem zobrazení tohoto dokumentu.|  
|[CDocument::ClearChunkList](#clearchunklist)|Vymaže seznamu bloků.|  
|[CDocument::ClearPathName](#clearpathname)|Vymaže cestu objektu dokumentu.|  
|[CDocument::DeleteContents](#deletecontents)|Volá se kvůli provedení čištění dokumentu.|  
|[CDocument::FindChunk](#findchunk)|Vyhledá bloku se zadaným identifikátorem GUID.|  
|[CDocument::GetAdapter](#getadapter)|Vrací ukazatel na implementaci objekt `IDocument` rozhraní.|  
|[CDocument::GetDocTemplate](#getdoctemplate)|Vrací ukazatel na Šablona dokumentu, který popisuje typ dokumentu.|  
|[CDocument::GetFile](#getfile)|Vrací ukazatel na požadovanou `CFile` objektu.|  
|[CDocument::GetFirstViewPosition](#getfirstviewposition)|Vrátí první pozici v seznamu zobrazení; používá k zahájení iterací.|  
|[CDocument::GetNextView](#getnextview)|Prochází seznam zobrazení přidružený k dokumentu.|  
|[CDocument::GetPathName](#getpathname)|Vrátí cestu k souboru dat dokumentu.|  
|[CDocument::GetThumbnail](#getthumbnail)|Voláno k vytvoření rastrového obrázku pro použití poskytovatelem miniatur zobrazíte miniaturu.|  
|[CDocument::GetTitle](#gettitle)|Vrátí název dokumentu.|  
|[CDocument::InitializeSearchContent](#initializesearchcontent)|Volat za účelem inicializace vyhledávání obsahu pro obslužnou rutinu vyhledávání.|  
|[CDocument::IsModified](#ismodified)|Určuje, zda dokument byla změněna od posledního uložení.|  
|[CDocument::IsSearchAndOrganizeHandler](#issearchandorganizehandler)|Informuje zda tato instance `CDocument` objekt byl vytvořen pro hledání a uspořádání obslužnou rutinu.|  
|[CDocument::LoadDocumentFromStream](#loaddocumentfromstream)|Voláno k načtení dokumentu dat z datového proudu.|  
|[CDocument::OnBeforeRichPreviewFontChanged](#onbeforerichpreviewfontchanged)|Voláno před provedením Změna písma bohaté Preview.|  
|[CDocument::OnChangedViewList](#onchangedviewlist)|Volá se po zobrazení je přidat nebo odebrat z dokumentu.|  
|[CDocument::OnCloseDocument](#onclosedocument)|Voláno k zavřete dokument.|  
|[CDocument::OnCreatePreviewFrame](#oncreatepreviewframe)|Voláno rámcem, pokud je potřeba vytvořit rámce náhled pro verzi Preview formátováním.|  
|[CDocument::OnDocumentEvent](#ondocumentevent)|Voláno rámcem v reakci na událost dokumentu.|  
|[CDocument::OnDrawThumbnail](#ondrawthumbnail)|Potlačí tuto metodu v odvozené třídě k vykreslení obsahu miniaturu.|  
|[CDocument::OnLoadDocumentFromStream](#onloaddocumentfromstream)|Voláno rámcem, pokud je třeba načíst data dokumentu z datového proudu.|  
|[CDocument::OnNewDocument](#onnewdocument)|Voláno k vytvoření nového dokumentu.|  
|[CDocument::OnOpenDocument](#onopendocument)|Voláno k otevře existující dokument.|  
|[CDocument::OnPreviewHandlerQueryFocus](#onpreviewhandlerqueryfocus)|Určí, že vrátit HWND z volání funkce hodnotu GetFocus obslužná rutina preview.|  
|[CDocument::OnPreviewHandlerTranslateAccelerator](#onpreviewhandlertranslateaccelerator)|Určí, že preview obslužná rutina pro zpracování stisknutí klávesy předat z message pump procesu, ve kterém je spuštěna obslužná rutina preview.|  
|[CDocument::OnRichPreviewBackColorChanged](#onrichpreviewbackcolorchanged)|Voláno, pokud došlo ke změně barvu pozadí náhledu formátováním.|  
|[CDocument::OnRichPreviewFontChanged](#onrichpreviewfontchanged)|Voláno, pokud došlo ke změně bohaté Preview písma.|  
|[CDocument::OnRichPreviewSiteChanged](#onrichpreviewsitechanged)|Voláno, pokud došlo ke změně bohaté náhled webu.|  
|[CDocument::OnRichPreviewTextColorChanged](#onrichpreviewtextcolorchanged)|Voláno, pokud došlo ke změně Preview bohaté barvy.|  
|[CDocument::OnSaveDocument](#onsavedocument)|Volá se dokument uložit na disk.|  
|[CDocument::OnUnloadHandler](#onunloadhandler)|Voláno rámcem při odpojení obslužná rutina preview.|  
|[CDocument::PreCloseFrame](#precloseframe)|Voláno před provedením zavření okna rámce.|  
|[CDocument::ReadNextChunkValue](#readnextchunkvalue)|Přečte další hodnotu bloku.|  
|[CDocument::ReleaseFile](#releasefile)|Uvolní soubor, aby byl k dispozici pro použití jinými aplikacemi.|  
|[CDocument::RemoveChunk](#removechunk)|Odebere bloku se zadaným identifikátorem GUID.|  
|[CDocument::RemoveView](#removeview)|Umožňuje odpojit zobrazení z dokumentu.|  
|[CDocument::ReportSaveLoadException](#reportsaveloadexception)|Rozšířené přepisovatelné; volá se při otevření nebo uložení operaci nelze dokončit z důvodu výjimku.|  
|[CDocument::SaveModified](#savemodified)|Rozšířené přepisovatelné; voláno k požádat uživatele, zda má být uložen v dokumentu.|  
|[CDocument::SetChunkValue](#setchunkvalue)|Nastaví hodnotu bloku.|  
|[CDocument::SetModifiedFlag](#setmodifiedflag)|Nastaví příznak označující, že jste změnili dokumentu, od posledního uložení.|  
|[CDocument::SetPathName](#setpathname)|Nastaví cestu k souboru dat používané v dokumentu.|  
|[CDocument::SetTitle](#settitle)|Nastaví název dokumentu.|  
|[CDocument::UpdateAllViews](#updateallviews)|Upozorní, všechna zobrazení, které dokumentu byla změněna.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDocument::OnFileSendMail](#onfilesendmail)|Odešle e-mailovou zprávu s dokumentem připojen.|  
|[CDocument::OnUpdateFileSendMail](#onupdatefilesendmail)|Umožňuje příkaz Odeslat e-mailu, pokud je k dispozici podporu pošty.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CDocument::m_bGetThumbnailMode](#m_bgetthumbnailmode)|Určuje, že `CDocument` objekt byl vytvořen dllhost pro miniatury. Je třeba kontrolovat na `CView::OnDraw`.|  
|[CDocument::m_bPreviewHandlerMode](#m_bpreviewhandlermode)|Určuje, že `CDocument` objekt byl vytvořen prevhost pro `Rich Preview`. Je třeba kontrolovat na `CView::OnDraw`.|  
|[CDocument::m_bSearchMode](#m_bsearchmode)|Určuje, že `CDocument` indexer nebo jiné vyhledávací aplikaci se objekt vytvořil.|  
|[CDocument::m_clrRichPreviewBackColor](#m_clrrichpreviewbackcolor)|Určuje barvu pozadí z okna náhledu formátováním. Je tato barva nastavena hostitele.|  
|[CDocument::m_clrRichPreviewTextColor](#m_clrrichpreviewtextcolor)|Určuje barvu popředí z okna náhledu formátováním. Je tato barva nastavena hostitele.|  
|[CDocument::m_lfRichPreviewFont](#m_lfrichpreviewfont)|Určuje písmo pro text pro okno náhledu formátováním. Tyto informace písma nastavuje hostitel.|  
  
## <a name="remarks"></a>Poznámky  
 Dokument představuje jednotku data, která uživatel obvykle otevře pomocí příkazu soubor otevřít a uloží pomocí příkazu Uložit soubor.  
  
 **CDocument** podporuje standardní operace, například vytváření dokumentu načte a ho uložit. Rozhraní framework zpracovává dokumenty pomocí rozhraní definované **CDocument**.  
  
 Aplikace může podporovat více než jeden typ dokumentu. například aplikace může podporovat tabulek a text dokumenty. Každý typ dokument má k šabloně přidružená dokumentu; Šablona dokumentu určuje, jaké prostředky (například nabídky, ikony nebo akcelerátoru tabulky) se používají pro tento typ dokumentu. Každý dokument obsahuje ukazatel přidružené `CDocTemplate` objektu.  
  
 Uživatelé pracují s dokumentem prostřednictvím [CView](../../mfc/reference/cview-class.md) objekty, které jsou s ním spojená. Zobrazení vykreslí obrázek dokumentu v okně s rámečkem a uživatelský vstup jako operace v dokumentu. Dokument může mít více zobrazení s ním spojená. Když uživatel otevře okno na dokument, rozhraní framework vytvoří zobrazení a připojí jej k dokumentu. Šablona dokumentu určuje, jaký typ okna zobrazení a rámečku slouží k zobrazení různých typů dokumentů.  
  
 Dokumenty jsou součástí rozhraní framework standardní směrování příkazů a v důsledku toho přijímat příkazy z komponenty standardní uživatelské rozhraní (například soubor uložit položky nabídky). Dokument přijímá příkazy, které jsou předávány active zobrazení. Pokud dokument nemůže pracovat s daného příkazu, předává příkaz šablony dokumentu, která je spravuje.  
  
 Při změně dokumentu dat, každý z jeho zobrazení musí tyto změny projeví. **CDocument** poskytuje [UpdateAllViews](#updateallviews) – členská funkce pro vás upozornit zobrazení tyto změny, takže zobrazení můžete překreslit sami podle potřeby. Rozhraní framework také vyzývá uživatele k před jeho zavřením uložit upravený soubor.  
  
 Chcete-li implementovat dokumenty v typické aplikaci, musíte udělat následující:  
  
-   Odvození třídy z **CDocument** pro každý typ dokumentu.  
  
-   Přidání členské proměnné k ukládání dat pro každý dokument.  
  
-   Implementovat členské funkce pro čtení a úpravy dat dokumentu. Zobrazení dokumentu jsou nejdůležitější uživatelé tyto členských funkcí.  
  
-   Přepsání [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) členské funkce ve třídě dokumentů k zápisu a čtení dokumentu dat do a z disku.  
  
 **CDocument** podporuje odesílání vašeho dokumentu prostřednictvím e-mailu, pokud je k dispozici podporu pošty (MAPI). Najdete v článcích [MAPI](../../mfc/mapi.md) a [Podpora MAPI v MFC](../../mfc/mapi-support-in-mfc.md).  
  
 Další informace o **CDocument**, najdete v části [serializace](../../mfc/serialization-in-mfc.md), [Document/View – architektura témata](../../mfc/document-view-architecture.md), a [Document/View – vytvoření](../../mfc/document-view-creation.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocument`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="addview"></a>CDocument::AddView  
 Volání této funkce můžete připojit k dokumentu, zobrazení.  
  
```  
void AddView(CView* pView);
```  
  
### <a name="parameters"></a>Parametry  
 `pView`  
 Body do zobrazení, který chcete přidat.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce přidá zadané zobrazení do seznamu zobrazení, které jsou přidružené k dokumentu. funkce také nastaví zobrazení dokumentu ukazatele k tomuto dokumentu. Tato funkce volá framework při připojování zobrazení nově vytvořený objekt k dokumentu. k tomu dojde v reakci na příkaz Nový soubor, otevřete soubor nebo nové okno nebo když je rozdělená rozděleném okně.  
  
 Volání této funkce pouze v případě, že jsou ruční vytvoření a připojení zobrazení. Obvykle vám umožní framework připojit dokumentů a zobrazení tak, že definujete [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objekt, který chcete přidružit třída dokumentu, zobrazení třídy a třídy oken s rámečkem.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocViewSDI#12](../../mfc/codesnippet/cpp/cdocument-class_1.cpp)]  
  
##  <a name="beginreadchunks"></a>CDocument::BeginReadChunks  
 Inicializuje bloku dat čtení.  
  
```  
virtual void BeginReadChunks ();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="cancloseframe"></a>CDocument::CanCloseFrame  
 Voláno rámcem před okně s rámečkem v dokumentu zobrazení je uzavřený.  
  
```  
virtual BOOL CanCloseFrame(CFrameWnd* pFrame);
```  
  
### <a name="parameters"></a>Parametry  
 `pFrame`  
 Body do rámce okna zobrazení připojené k dokumentu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, zda je bezpečná zavřete okno rámce; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace kontroluje, zda existují další okna s rámečkem zobrazení dokumentu. Pokud je okno zadaného rámce byl naposledy zobrazí dokument, funkce vyzve uživatele k uložení dokumentu, pokud byl upraven. Tato funkce přepsání, pokud chcete provést zvláštní zpracování při zavření rámce okna. Toto je rozšířené přepisovatelné.  
  
##  <a name="cdocument"></a>CDocument::CDocument  
 Vytvoří **CDocument** objektu.  
  
```  
CDocument();
```  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework zpracovává vytvoření dokumentu pro vás. Přepsání [OnNewDocument](#onnewdocument) – členská funkce k provedení inicializace na jednotlivých dokumentů; to je zvlášť důležité v aplikacích (SDI rozhraní) jednotlivý dokument.  
  
##  <a name="clearchunklist"></a>CDocument::ClearChunkList  
 Vymaže seznamu bloků.  
  
```  
virtual void ClearChunkList ();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="clearpathname"></a>CDocument::ClearPathName  
 Vymaže cestu objektu dokumentu.  
  
```  
virtual void ClearPathName();
```  
  
### <a name="remarks"></a>Poznámky  
 Vymazání cestu z `CDocument` objekt způsobí, že aplikace Dotázat se uživatele při dalším uložení dokumentu. Díky tomu **Uložit** příkaz chovají jako **uložit jako** příkaz.  
  
##  <a name="deletecontents"></a>CDocument::DeleteContents  
 Voláno rámcem odstranit data dokumentu bez zničení **CDocument** samotného objektu.  
  
```  
virtual void DeleteContents();
```  
  
### <a name="remarks"></a>Poznámky  
 Je volána těsně před dokument je zničení. Nazývá se také zajistit, že dokument je prázdný, předtím, než se znovu použije. To je obzvláště důležité pro aplikace SDI, který používá jenom jeden dokument; dokument se znovu použije vždy, když uživatel vytvoří nebo otevře jiného dokumentu. Volejte tuto funkci implementovat "Upravit Vymazat vše" nebo podobně jako příkaz, který odstraní všechna data dokumentu. Výchozí implementace této funkce neprovede žádnou akci. Potlačí tuto funkci můžete odstranit data v dokumentu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#57](../../mfc/codesnippet/cpp/cdocument-class_2.cpp)]  
  
##  <a name="findchunk"></a>CDocument::FindChunk  
 Vyhledá bloku se zadaným identifikátorem GUID.  
  
```  
virtual POSITION FindChunk(
    REFCLSID guid,  
    DWORD pid);
```  
  
### <a name="parameters"></a>Parametry  
 `guid`  
 Určuje identifikátor GUID bloku k vyhledání.  
  
 `pid`  
 Určuje PID od bloku k vyhledání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pozice v seznamu interní bloku v případě úspěchu. V opačném případě `NULL`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getadapter"></a>CDocument::GetAdapter  
 Vrací ukazatel na implementaci k objektu `IDocument` rozhraní.  
  
```  
virtual ATL::IDocument* GetAdapter();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na implementaci k objektu `IDocument` rozhraní.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getdoctemplate"></a>CDocument::GetDocTemplate  
 Volejte tuto funkci k získání ukazatele na šabloně dokumentu pro tento typ dokumentu.  
  
```  
CDocTemplate* GetDocTemplate() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na šabloně dokumentu pro tento typ dokumentu nebo **NULL** Pokud dokument není spravován nástrojem šablony dokumentu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#58](../../mfc/codesnippet/cpp/cdocument-class_3.cpp)]  
  
##  <a name="getfile"></a>CDocument::GetFile  
 Volání této funkce člen získání ukazatele na `CFile` objektu.  
  
```  
virtual CFile* GetFile(
    LPCTSTR lpszFileName,  
    UINT nOpenFlags,  
    CFileException* pError);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFileName`  
 Řetězec, který je cesta k souboru požadovaného. Cesta může být relativní nebo absolutní.  
  
 `pError`  
 Ukazatele na existující objekt výjimky souborů, který označuje stav dokončení operace.  
  
 `nOpenFlags`  
 Režim sdílení a přístup. Určuje akci, která se má provést při otevření souboru. Zkombinováním možnosti uvedené v konstruktoru cfile – [CFile::CFile](../../mfc/reference/cfile-class.md#cfile) bitová hodnota OR (&#124;) pomocí operátor. Jeden přístupová oprávnění a možnost jednu sdílenou složku jsou povinné; **modeCreate** a **modeNoInherit** režimy jsou volitelné.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na `CFile` objektu.  
  
##  <a name="getfirstviewposition"></a>CDocument::GetFirstViewPosition  
 Volání této funkce můžete získat pozice první zobrazení v seznamu zobrazení přidružený k dokumentu.  
  
```  
virtual POSITION GetFirstViewPosition() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A **pozice** hodnotu, která lze použít pro iteraci pomocí [GetNextView](#getnextview) – členská funkce.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]  
  
##  <a name="getnextview"></a>CDocument::GetNextView  
 Volání této funkce k iteraci v rámci všechna zobrazení dokumentu.  
  
```  
virtual CView* GetNextView(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `rPosition`  
 Odkaz na **pozice** hodnoty vrácené z předchozího volání `GetNextView` nebo [GetFirstViewPosition](#getfirstviewposition) členské funkce. Tato hodnota nesmí být **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na zobrazení identifikovaný `rPosition`.  
  
### <a name="remarks"></a>Poznámky  
 Funkce vrátí zobrazení identifikovaný `rPosition` a nastaví `rPosition` k **pozice** hodnota další zobrazení v seznamu. Pokud načtené zobrazení je poslední v seznamu, pak `rPosition` je nastaven na **NULL**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]  
  
##  <a name="getpathname"></a>CDocument::GetPathName  
 Volání této funkce můžete získat plně kvalifikovanou cestu souboru disku dokumentu.  
  
```  
const CString& GetPathName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Plně kvalifikovaná cesta dokumentu. Tento řetězec je prázdný, pokud nebyl uložen dokumentu nebo nemá soubor na disku s ním spojená.  
  
##  <a name="getthumbnail"></a>CDocument::GetThumbnail  
 Vytvoří rastrového obrázku má být používána poskytovateli miniatur zobrazíte miniaturu.  
  
```  
virtual BOOL GetThumbnail(
    UINT cx,  
    HBITMAP* phbmp,  
    DWORD* pdwAlpha);
```  
  
### <a name="parameters"></a>Parametry  
 `cx`  
 Určuje šířku a výšku bitmapy.  
  
 `phbmp`  
 Obsahuje popisovač pro bitové mapy, když se funkce vrátí úspěšně.  
  
 `pdwAlpha`  
 Obsahuje hodnotu DWORD určující hodnotu alfa kanálu, když se funkce vrátí úspěšně.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `TRUE` Pokud rastrový obrázek pro miniaturu byl vytvořen úspěšně; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="gettitle"></a>CDocument::GetTitle  
 Volání této funkce se získat název dokumentu, který je obvykle odvozený od název souboru dokumentu.  
  
```  
const CString& GetTitle() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Název dokumentu.  
  
##  <a name="initializesearchcontent"></a>CDocument::InitializeSearchContent  
 Volat za účelem inicializace vyhledávání obsahu pro obslužnou rutinu vyhledávání.  
  
```  
virtual void InitializeSearchContent ();
```  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu v odvozené třídě pro inicializaci vyhledávání obsahu. Obsah by měl být řetězec s částmi oddělená ";". Například "bodu; rámeček; Položka OLE".  
  
##  <a name="ismodified"></a>CDocument::IsModified  
 Volání této funkce určete, zda dokument byla změněna od posledního uložení.  
  
```  
virtual BOOL IsModified();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud dokumentu byla změněna od jeho posledního uložení; jinak 0.  
  
##  <a name="issearchandorganizehandler"></a>CDocument::IsSearchAndOrganizeHandler  
 Informuje zda tato instance `CDocument` byla vytvořena pro hledání a uspořádání obslužnou rutinu.  
  
```  
BOOL IsSearchAndOrganizeHandler() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `TRUE` Pokud tuto instanci `CDocument` byla vytvořena pro hledání a uspořádání obslužnou rutinu.  
  
### <a name="remarks"></a>Poznámky  
 Aktuálně vrací hodnotu této funkce `TRUE` pouze pro náhled bohaté obslužné rutiny implementované v out procesového serveru. Příslušnými příznaky (m_bPreviewHandlerMode, m_bSearchMode, m_bGetThumbnailMode) můžete nastavit na úrovni vaší aplikace, aby tato funkce návratový `TRUE`.  
  
##  <a name="loaddocumentfromstream"></a>CDocument::LoadDocumentFromStream  
 Voláno k načtení dokumentu dat z datového proudu.  
  
```  
virtual HRESULT LoadDocumentFromStream(
    IStream* pStream,  
    DWORD dwGrfMode);
```  
  
### <a name="parameters"></a>Parametry  
 `pStream`  
 Ukazatel na datový proud. Tento datový proud poskytuje prostředí.  
  
 `dwGrfMode`  
 Režim přístupu do datového proudu.  
  
### <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je zatížení operace úspěšná, jinak hodnota HRESULT s kódem chyby.  
  
### <a name="remarks"></a>Poznámky  
 Mohou přepsat tuto metodu v odvozené třídě přizpůsobit jak načíst data z datového proudu.  
  
##  <a name="m_bgetthumbnailmode"></a>CDocument::m_bGetThumbnailMode  
 Určuje, že `CDocument` objekt byl vytvořen dllhost pro miniatury. Je třeba kontrolovat na `CView::OnDraw`.  
  
```  
BOOL m_bGetThumbnailMode;  
```  
  
### <a name="remarks"></a>Poznámky  
 `TRUE`Označuje, že dokument byl vytvořen dllhost pro miniatury.  
  
##  <a name="m_bpreviewhandlermode"></a>CDocument::m_bPreviewHandlerMode  
 Určuje, že `CDocument` objekt byl vytvořen prevhost pro verzi Preview formátováním. Je třeba kontrolovat na `CView::OnDraw`.  
  
```  
BOOL m_bPreviewHandlerMode;  
```  
  
### <a name="remarks"></a>Poznámky  
 `TRUE`Označuje, že dokument byl vytvořen prevhost pro verzi Preview formátováním.  
  
##  <a name="m_bsearchmode"></a>CDocument::m_bSearchMode  
 Určuje, že `CDocument` objekt byl vytvořen, indexer nebo jinou aplikací pro vyhledávání.  
  
```  
BOOL m_bSearchMode;  
```  
  
### <a name="remarks"></a>Poznámky  
 `TRUE`vyplývá, že byl dokument vytvořila indexer nebo jinou aplikací pro vyhledávání.  
  
##  <a name="m_clrrichpreviewbackcolor"></a>CDocument::m_clrRichPreviewBackColor  
 Určuje barvu pozadí okna náhledu formátováním. Je tato barva nastavena hostitele.  
  
```  
COLORREF m_clrRichPreviewBackColor;  
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="m_clrrichpreviewtextcolor"></a>CDocument::m_clrRichPreviewTextColor  
 Určuje barvu popředí okna náhledu formátováním. Je tato barva nastavena hostitele.  
  
```  
COLORREF m_clrRichPreviewTextColor;  
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="m_lfrichpreviewfont"></a>CDocument::m_lfRichPreviewFont  
 Určuje písmo pro text pro okno náhledu formátováním. Tyto informace písma nastavuje hostitel.  
  
```  
CFont m_lfRichPreviewFont;  
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onbeforerichpreviewfontchanged"></a>CDocument::OnBeforeRichPreviewFontChanged  
 Voláno před provedením Změna písma bohaté Preview.  
  
```  
virtual void OnBeforeRichPreviewFontChanged();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onchangedviewlist"></a>CDocument::OnChangedViewList  
 Voláno rámcem po zobrazení je přidat nebo odebrat z dokumentu.  
  
```  
virtual void OnChangedViewList();
```  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace této funkce ověří, zda poslední zobrazení má být odebrán a pokud ano, odstraní dokumentu. Tato funkce přepsání, pokud chcete provést zvláštní zpracování, pokud rozhraní přidá nebo odebere zobrazení. Pokud chcete, aby dokument zůstane otevřená, i když nejsou žádná zobrazení k němu připojen, například přepsání této funkce.  
  
##  <a name="onclosedocument"></a>CDocument::OnCloseDocument  
 Voláno rámcem při zavření dokumentu, obvykle v rámci příkazu soubor zavřít.  
  
```  
virtual void OnCloseDocument();
```  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace této funkce zničí všechny rámce používá pro zobrazení dokumentu, zavře zobrazení, vyčistí obsah dokumentu a pak zavolá [DeleteContents](#deletecontents) – členská funkce odstranění dokumentu data.  
  
 Tato funkce přepsání, pokud chcete provést čištění zvláštní zpracování rozhraní zavře dokumentu. Například pokud dokument představuje záznam v databázi, můžete funkci zavřete databázi přepsat. Základní třída verze této funkce by měly volat z přepsání.  
  
##  <a name="oncreatepreviewframe"></a>CDocument::OnCreatePreviewFrame  
 Voláno rámcem, pokud je potřeba vytvořit rámce náhled pro verzi Preview formátováním.  
  
```  
virtual BOOL OnCreatePreviewFrame();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `TRUE` Pokud rámečku je vytvořen úspěšně; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ondocumentevent"></a>CDocument::OnDocumentEvent  
 Voláno rámcem v reakci na událost dokumentu.  
  
```  
virtual void OnDocumentEvent(DocumentEvent deEvent);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`deEvent`  
 Výčtové datový typ, který popisuje typ události.  
  
### <a name="remarks"></a>Poznámky  
 Události dokument může ovlivnit více tříd. Tato metoda je zodpovědná za zpracování událostí dokumentu, které ovlivňují třídy jiné než [CDocument – třída](../../mfc/reference/cdocument-class.md). V současné době je jediná třída, která musí reakce na události dokumentu [CDataRecoveryHandler třída](../../mfc/reference/cdatarecoveryhandler-class.md). `CDocument` Třída má jiné přepisovatelné metody zodpovídá za zpracování účinek na `CDocument`.  
  
 Následující tabulka uvádí možné hodnoty pro `deEvent` a události, které odpovídají.  
  
|Hodnota|Odpovídající událost|  
|-----------|-------------------------|  
|`onAfterNewDocument`|Byl vytvořen nový dokument.|  
|`onAfterOpenDocument`|Byl otevřen nový dokument.|  
|`onAfterSaveDocument`|Dokument byl uložen.|  
|`onAfterCloseDocument`|V dokumentu bylo ukončeno.|  
  
##  <a name="ondrawthumbnail"></a>CDocument::OnDrawThumbnail  
 Potlačí tuto metodu v odvozené třídě k vykreslení miniaturu.  
  
```  
virtual void OnDrawThumbnail(
    CDC& dc,  
    LPRECT lprcBounds);
```  
  
### <a name="parameters"></a>Parametry  
 `dc`  
 Odkaz na kontextu zařízení.  
  
 `lprcBounds`  
 Určuje ohraničující obdélník oblasti, kde mají být vykresleny miniaturu.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onfilesendmail"></a>CDocument::OnFileSendMail  
 Odešle zprávu přes hostitele trvalé e-mailu (pokud existuje) s dokumentem jako přílohu.  
  
```  
void OnFileSendMail();
```  
  
### <a name="remarks"></a>Poznámky  
 `OnFileSendMail`volání [OnSaveDocument](#onsavedocument) k serializaci (bez názvu a upravené dokumenty do dočasného souboru, která se pak posílají pomocí e-mailové Uložit). Pokud dokument byl změněn, není potřeba dočasný soubor; Původní se odesílají. `OnFileSendMail`načte MAPI32. Knihovny DLL, pokud již nebyla načtena.  
  
 Speciální provádění `OnFileSendMail` pro [COleDocument](../../mfc/reference/coledocument-class.md) popisovače složené soubory správně.  
  
 **CDocument** podporuje odesílání vašeho dokumentu prostřednictvím e-mailu, pokud je k dispozici podporu pošty (MAPI). Najdete v článcích [MAPI témata](../../mfc/mapi.md) a [Podpora MAPI v MFC](../../mfc/mapi-support-in-mfc.md).  
  
##  <a name="onloaddocumentfromstream"></a>CDocument::OnLoadDocumentFromStream  
 Voláno rámcem, pokud je třeba načíst data dokumentu z datového proudu.  
  
```  
virtual HRESULT OnLoadDocumentFromStream(
    IStream* pStream,  
    DWORD grfMode);
```  
  
### <a name="parameters"></a>Parametry  
 `pStream`  
 Ukazatel na příchozího datového proudu.  
  
 `grfMode`  
 Režim přístupu do datového proudu.  
  
### <a name="return-value"></a>Návratová hodnota  
 S_OK, je-li zatížení úspěšně; v opačném případě chybový kód.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onnewdocument"></a>CDocument::OnNewDocument  
 Voláno rámcem jako součást souboru nový příkaz.  
  
```  
virtual BOOL OnNewDocument();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud dokumentu byl úspěšně inicializován; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace této funkce volá [DeleteContents](#deletecontents) – členská funkce zajistit, že dokument je prázdná a pak označí nový dokument jako čisté. Potlačí tuto funkci k chybě při inicializaci datovou strukturu pro nový dokument. Základní třída verze této funkce by měly volat z přepsání.  
  
 Pokud uživatel vybere nový soubor příkaz v aplikaci SDI, systém použije tato funkce znovu inicializovat stávající dokument, místo vytvoření nového. Pokud uživatel vybere nový soubor v aplikaci více rozhraní (MDI) dokumentu, rozhraní framework vytvoří nový dokument pokaždé, když a pak zavolá této funkci můžete provést jeho inicializaci. V této funkci místo v konstruktoru pro nový soubor příkaz účinný v aplikace SDI musíte umístit inicializace kódu.  
  
 Všimněte si, že existují případech, kdy `OnNewDocument` se volala dvakrát. K tomu dochází, když dokumentu je vložený jako Server ActiveX dokumentu. Funkce nejprve volá `CreateInstance` – metoda (vystavené `COleObjectFactory`-odvozené třídy) a podruhé podle `InitNew` – metoda (vystavené `COleServerDoc`-odvozené třídy).  
  
### <a name="example"></a>Příklad  
 Následující příklady ilustrují alternativní metody pro inicializaci objektu dokumentu.  
  
 [!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]  
  
##  <a name="onopendocument"></a>CDocument::OnOpenDocument  
 Voláno rámcem v rámci příkazu Otevřít soubor.  
  
```  
virtual BOOL OnOpenDocument(LPCTSTR lpszPathName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszPathName`  
 Body k cestě otevření dokumentu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud dokumentu byl úspěšně načten; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace této funkce otevře zadaný soubor volání [DeleteContents](#deletecontents) – členská funkce zajistit, že dokument je prázdná, zavolá [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) pro čtení tohoto souboru obsah a pak označí dokumentu jako vyčistit. Tato funkce přepsání, pokud chcete použít něco než mechanismus archivu nebo mechanismus souborů. Například můžete napsat aplikaci, kde dokumenty představují záznamy v databázi, nikoli samostatné soubory.  
  
 Pokud uživatel vybere příkaz Otevřít soubor v aplikaci SDI, systém použije tato funkce znovu inicializovat existující **CDocument** objektu, místo vytvoření nového. Pokud uživatel vybere soubor otevřete v aplikaci MDI, vytvoří novou rozhraní **CDocument** pokaždé, když objekt a potom zavolá této funkci můžete provést jeho inicializaci. V této funkci místo v konstruktoru pro příkaz Otevřít soubor jsou účinné aplikace SDI musíte umístit inicializace kódu.  
  
### <a name="example"></a>Příklad  
 Následující příklady ilustrují alternativní metody pro inicializaci objektu dokumentu.  
  
 [!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#63](../../mfc/codesnippet/cpp/cdocument-class_8.cpp)]  
  
##  <a name="onpreviewhandlerqueryfocus"></a>CDocument::OnPreviewHandlerQueryFocus  
 Obslužná rutina preview se vrátíte HWND načítají volání přesměruje `GetFocus` funkce.  
  
```  
virtual HRESULT OnPreviewHandlerQueryFocus(HWND* phwnd);
```  
  
### <a name="parameters"></a>Parametry  
 `phwnd`  
 [out] Po návratu tato metoda obsahuje ukazatel HWND vrácená z volání `GetFocus` funkce z vlákna popředí obslužná rutina preview.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěšného; nebo jinak chybovou hodnotu.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onpreviewhandlertranslateaccelerator"></a>CDocument::OnPreviewHandlerTranslateAccelerator  
 Určí, že preview obslužná rutina pro zpracování stisknutí klávesy předat z message pump procesu, ve kterém je spuštěna obslužná rutina preview.  
  
```  
virtual HRESULT OnPreviewHandlerTranslateAccelerator(MSG* pmsg);
```  
  
### <a name="parameters"></a>Parametry  
 `pmsg`  
 [v] Ukazatel na zpráv oken.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud obslužná rutina preview můžete zpracovat zprávu klávesu, obslužná rutina procesy a vrátí S_OK. Pokud obslužná rutina preview nemůže zpracovat zprávu klávesu, nabízí ji k hostiteli prostřednictvím `IPreviewHandlerFrame::TranslateAccelerator`. Pokud hostitel zprávu zpracuje, tato metoda vrátí S_OK. Pokud hostitel není zpracovat zprávu, tato metoda vrátí S_FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onrichpreviewbackcolorchanged"></a>CDocument::OnRichPreviewBackColorChanged  
 Voláno, pokud se změnila na barvu pozadí náhledu formátováním.  
  
```  
virtual void OnRichPreviewBackColorChanged();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onrichpreviewfontchanged"></a>CDocument::OnRichPreviewFontChanged  
 Voláno, pokud došlo ke změně písma bohaté Preview.  
  
```  
virtual void OnRichPreviewFontChanged();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onrichpreviewsitechanged"></a>CDocument::OnRichPreviewSiteChanged  
 Voláno, pokud došlo ke změně webu bohaté Preview.  
  
```  
virtual void OnRichPreviewSiteChanged();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onrichpreviewtextcolorchanged"></a>CDocument::OnRichPreviewTextColorChanged  
 Voláno, pokud došlo ke změně barvu textu bohaté Preview.  
  
```  
virtual void OnRichPreviewTextColorChanged();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onsavedocument"></a>CDocument::OnSaveDocument  
 Voláno rámcem jako část příkazu Uložit soubor nebo soubor uložit jako.  
  
```  
virtual BOOL OnSaveDocument(LPCTSTR lpszPathName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszPathName`  
 Odkazuje na plně kvalifikovanou cestu, která má být uložen soubor.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud dokumentu byl úspěšně uložen; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace této funkce otevře zadaný soubor volání [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) zapisovat data dokumentu do souboru a pak označí dokumentu jako vyčistit. Tato funkce přepsání, pokud chcete provést zvláštní zpracování, pokud rozhraní framework uloží dokument. Například můžete napsat aplikaci, kde dokumenty představují záznamy v databázi, nikoli samostatné soubory.  
  
##  <a name="onunloadhandler"></a>CDocument::OnUnloadHandler  
 Voláno rámcem, pokud obslužná rutina preview je odpojen.  
  
```  
virtual void OnUnloadHandler();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onupdatefilesendmail"></a>CDocument::OnUpdateFileSendMail  
 Umožňuje **ID_FILE_SEND_MAIL** příkaz, pokud je nainstalován podporu pošty (MAPI).  
  
```  
void OnUpdateFileSendMail(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Parametry  
 `pCmdUI`  
 Ukazatel [CCmdUI](../../mfc/reference/ccmdui-class.md) objekt přidružený k **ID_FILE_SEND_MAIL** příkaz.  
  
### <a name="remarks"></a>Poznámky  
 V opačném případě odebere funkce **ID_FILE_SEND_MAIL** příkazu v nabídce, včetně oddělovačů výše nebo níže v nabídce položky podle potřeby. MAPI je povolena, pokud MAPI32. Knihovny DLL se nachází v cestě a v části [e-mailu] WIN. Soubor INI, MAPI = 1. Většina aplikací uveďte tohoto příkazu v nabídce Soubor.  
  
 **CDocument** podporuje odesílání vašeho dokumentu prostřednictvím e-mailu, pokud je k dispozici podporu pošty (MAPI). Najdete v článcích [MAPI témata](../../mfc/mapi.md) a [Podpora MAPI v MFC](../../mfc/mapi-support-in-mfc.md).  
  
##  <a name="precloseframe"></a>CDocument::PreCloseFrame  
 Tato funkce člen je voláno rámcem zničen okně s rámečkem.  
  
```  
virtual void PreCloseFrame(CFrameWnd* pFrame);
```  
  
### <a name="parameters"></a>Parametry  
 `pFrame`  
 Ukazatel [CFrameWnd](../../mfc/reference/cframewnd-class.md) kterém jsou uložena přidruženého **CDocument** objektu.  
  
### <a name="remarks"></a>Poznámky  
 Může být přepsána zadejte vlastní čištění, ale nezapomeňte volat základní třídy.  
  
 Výchozí `PreCloseFrame` se nic nestane. **CDocument**. **CDocument**-odvozených třídách [COleDocument](../../mfc/reference/coledocument-class.md) a [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) tato funkce je člen.  
  
##  <a name="readnextchunkvalue"></a>CDocument::ReadNextChunkValue  
 Přečte další hodnotu bloku.  
  
```  
virtual BOOL ReadNextChunkValue(IFilterChunkValue** ppValue);
```  
  
### <a name="parameters"></a>Parametry  
 `ppValue`  
 [out] Po návratu funkce `ppValue` obsahuje hodnotu, která byla načtena.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="releasefile"></a>CDocument::ReleaseFile  
 Tato funkce člen je voláno rámcem k uvolnění soubor ji dáte k dispozici pro použití jinými aplikacemi.  
  
```  
virtual void ReleaseFile(
    CFile* pFile,  
    BOOL bAbort);
```  
  
### <a name="parameters"></a>Parametry  
 `pFile`  
 Ukazatel na objekt cfile – k uvolnění.  
  
 `bAbort`  
 Určuje, zda soubor k uvolnění pomocí `CFile::Close` nebo `CFile::Abort`. **FALSE** Pokud je soubor k uvolnění pomocí [CFile::Close](../../mfc/reference/cfile-class.md#close); **TRUE** Pokud je soubor k uvolnění pomocí [CFile::Abort](../../mfc/reference/cfile-class.md#abort).  
  
### <a name="remarks"></a>Poznámky  
 Pokud `bAbort` je **TRUE**, `ReleaseFile` volání `CFile::Abort`, a soubor vydání. `CFile::Abort`nebude vyvolat výjimku.  
  
 Pokud `bAbort` je **FALSE**, `ReleaseFile` volání `CFile::Close` a vydání soubor.  
  
 Člen funkci tak, aby vyžadovala akce uživatelem před vydání soubor přepište.  
  
##  <a name="removechunk"></a>CDocument::RemoveChunk  
 Odebere bloků dat s identifikátorem GUID.  
  
```  
virtual void RemoveChunk(
    REFCLSID guid,  
    DWORD pid);
```  
  
### <a name="parameters"></a>Parametry  
 `Guid`  
 Určuje identifikátor GUID bloku dat mají být odebrány.  
  
 `Pid`  
 Určuje ID bloku dat mají být odebrány.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="removeview"></a>CDocument::RemoveView  
 Volání této funkce se odpojit zobrazení z dokumentu.  
  
```  
void RemoveView(CView* pView);
```  
  
### <a name="parameters"></a>Parametry  
 `pView`  
 Body do zobrazení, který je právě odebírán.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce odebere zadané zobrazení ze seznamu zobrazení, které jsou přidružené k dokumentu. také nastaví zobrazení dokumentu ukazatel na **NULL**. Tato funkce je volána rámcem při zavření okna rámce nebo podokně okna rozdělovače je uzavřený.  
  
 Volání této funkce pouze v případě, že jsou ručně odpojování zobrazení. Obvykle vám umožní framework odpojit dokumentů a zobrazení tak, že definujete [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objekt, který chcete přidružit třída dokumentu, zobrazení třídy a třídy oken s rámečkem.  
  
 Podívejte se na příklad na [AddView](#addview) pro implementaci ukázka.  
  
##  <a name="reportsaveloadexception"></a>CDocument::ReportSaveLoadException  
 Volána, pokud je vyvolána výjimka (obvykle [CFileException](../../mfc/reference/cfileexception-class.md) nebo [CArchiveException](../../mfc/reference/carchiveexception-class.md)) při uložení nebo načtení dokumentu.  
  
```  
virtual void ReportSaveLoadException(
    LPCTSTR lpszPathName,  
    CException* e,  
    BOOL bSaving,  
    UINT nIDPDefault);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszPathName`  
 Odkazuje na název dokumentu, který byl právě uloženy ani načíst.  
  
 *e*  
 Odkazuje na výjimku, která byla vyvolána. Může být **NULL**.  
  
 *bSaving*  
 Příznak, který udává, jaké operace se v průběhu; nenulové hodnoty, pokud se dokument uložit, 0 Pokud při načítání dokumentu.  
  
 `nIDPDefault`  
 Identifikátor chybové zprávy, který se má zobrazit, pokud funkce není zadat konkrétnější.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace prozkoumá objekt výjimky a hledá chybovou zprávu, která speciálně popisuje příčinu. Pokud není nalezena konkrétní zprávou, nebo pokud *e* je **NULL**, obecné zprávě určené `nIDPDefault` parametr se používá. Funkce pak zobrazí okno se zprávou obsahující chybovou zprávu. Tato funkce přepsání, pokud byste chtěli poskytnout další, přizpůsobené selhání zprávy. Toto je rozšířené přepisovatelné.  
  
##  <a name="savemodified"></a>CDocument::SaveModified  
 Voláno rámcem před změněný dokument bude uzavřen.  
  
```  
virtual BOOL SaveModified();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je bezpečné pokračovat a zavřete dokument; 0, pokud by neměl být uzavřený dokumentu.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace této funkce zobrazí požadavek na uživatele, jestli se má uložit změny do dokumentu, pokud byly provedeny žádné okno. Tato funkce přepsání, pokud program vyžaduje jiný nabízení postup. Toto je rozšířené přepisovatelné.  
  
##  <a name="setchunkvalue"></a>CDocument::SetChunkValue  
 Nastaví hodnotu bloku.  
  
```  
virtual BOOL SetChunkValue (IFilterChunkValue* pValue);
```  
  
### <a name="parameters"></a>Parametry  
 `pValue`  
 Určuje hodnotu bloku pro nastavení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setmodifiedflag"></a>CDocument::SetModifiedFlag  
 Po provedení veškeré úpravy dokumentu volání této funkce.  
  
```  
virtual void SetModifiedFlag(BOOL bModified = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bModified`  
 Příznak označující, zda dokument byl změněn.  
  
### <a name="remarks"></a>Poznámky  
 Při volání této funkce konzistentně, zajistěte, aby rozhraní vyzývá uživatele k před zavřením dokument uložit změny. Obvykle měli použít výchozí hodnotu **TRUE** pro `bModified` parametr. Označit dokumentu jako vyčistit (beze změny), volání této funkce s hodnotou **FALSE**.  
  
##  <a name="setpathname"></a>CDocument::SetPathName  
 Voláním této funkce zadejte plně kvalifikovanou cestu souboru disku dokumentu.  
  
```  
virtual void SetPathName(
    LPCTSTR lpszPathName,  
    BOOL bAddToMRU = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszPathName`  
 Odkazuje na řetězec, který má být použit jako cestu pro dokument.  
  
 `bAddToMRU`  
 Určuje, zda je název souboru do nejvíc nabízet (naposledy použitých). Pokud **nastavena hodnota TRUE,** přidat název souboru; Pokud **FALSE**, tam není přidaný.  
  
### <a name="remarks"></a>Poznámky  
 V závislosti na hodnotě `bAddToMRU` cesta je přidat, nebo není přidat do seznamu naposledy použitých aplikací. Všimněte si, že některé dokumenty nejsou přidružené soubor na disku. Volání této funkce pouze v případě, že přepíšete výchozí implementace pro otevření a uložení souborů používaných rozhraní.  
  
##  <a name="settitle"></a>CDocument::SetTitle  
 Volání této funkce můžete zadat název dokumentu (řetězec zobrazen v záhlaví okna rámečkem).  
  
```  
virtual void SetTitle(LPCTSTR lpszTitle);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszTitle`  
 Odkazuje na řetězec, který má být použit jako název dokumentu.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce aktualizuje názvy všech okna s rámečkem obsahujících dokumentu.  
  
##  <a name="updateallviews"></a>CDocument::UpdateAllViews  
 Poté, co se změnilo v dokumentu volání této funkce.  
  
```  
void UpdateAllViews(
    CView* pSender,  
    LPARAM lHint = 0L,  
    CObject* pHint = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pSender`  
 Odkazuje na úpravy dokumentu, zobrazení nebo **NULL** Pokud jsou všechny zobrazení aktualizovat.  
  
 `lHint`  
 Obsahuje informace o této úpravy.  
  
 `pHint`  
 Odkazuje na objekt ukládání informací o úpravy.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce by měly volat, jakmile zavoláte [SetModifiedFlag](#setmodifiedflag) – členská funkce. Tato funkce informuje jednotlivých zobrazení připojené k dokumentu, s výjimkou zobrazení určeného `pSender`, která byla změněna dokumentu. Obvykle volání této funkce z vaší třídy zobrazení po změně uživatele prostřednictvím zobrazení dokumentu.  
  
 Tato funkce volá [CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate) – členská funkce pro každou z dokumentu zobrazení kromě odesílání zobrazit předávání `pHint` a `lHint`. Použijte tyto parametry k předání informací k zobrazení o změny provedené v dokumentu. Můžete kódovat pomocí informace `lHint` nebo můžete definovat [CObject](../../mfc/reference/cobject-class.md)-odvozené třídy k ukládání informací o změny a předat objekt této třídy pomocí `pHint`. Přepsání `CView::OnUpdate` členské funkce ve vaší [CView](../../mfc/reference/cview-class.md)-odvozené třídy za účelem optimalizace aktualizace na základě informací předán zobrazení zobrazení.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#64](../../mfc/codesnippet/cpp/cdocument-class_9.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC MDIDOCVW](../../visual-cpp-samples.md)   
 [Ukázka MFC SNAPVW](../../visual-cpp-samples.md)   
 [Ukázka MFC agent NPP](../../visual-cpp-samples.md)   
 [CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)   
 [CView – třída](../../mfc/reference/cview-class.md)   
 [CDocTemplate – třída](../../mfc/reference/cdoctemplate-class.md)
