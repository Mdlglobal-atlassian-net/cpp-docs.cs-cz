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
ms.openlocfilehash: d356ba6b6134221c2fc9595fc6d78f91961c5b7f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753242"
---
# <a name="cdocument-class"></a>CDocument – třída

Poskytuje základní funkce pro uživatelem definované třídy dokumentů.

## <a name="syntax"></a>Syntaxe

```
class CDocument : public CCmdTarget
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDocument::CDocument](#cdocument)|Vytvoří `CDocument` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDocument::AddView](#addview)|Připojí zobrazení k dokumentu.|
|[CDocument::BeginReadChunks](#beginreadchunks)|Inicializuje čtení bloků.|
|[Cdocument::CanCloseFrame](#cancloseframe)|Pokročilé overridable; před zavřením okna rámce, které se prohlížené z tohoto dokumentu.|
|[CDocument::ClearChunkList](#clearchunklist)|Vymaže seznam bloků dat.|
|[CDocument::ClearPathName](#clearpathname)|Vymaže cestu k objektu dokumentu.|
|[CDocument::DeleteContents](#deletecontents)|Nazývá se provést vyčištění dokumentu.|
|[CDocument::FindChunk](#findchunk)|Vyhledá blok s určeným identifikátorem GUID.|
|[CDocument::Adaptér GetAdapter](#getadapter)|Vrátí ukazatel na objekt `IDocument` implementující rozhraní.|
|[CDocument::Šablona GetDoc](#getdoctemplate)|Vrátí ukazatel na šablonu dokumentu, která popisuje typ dokumentu.|
|[CDocument::Soubor GetFile](#getfile)|Vrátí ukazatel na `CFile` požadovaný objekt.|
|[CDocument::GetFirstViewPosition](#getfirstviewposition)|Vrátí pozici prvního v seznamu zobrazení; slouží k zahájení iterace.|
|[CDocument::GetNextView](#getnextview)|Iterates prostřednictvím seznamu zobrazení spojených s dokumentem.|
|[CDocument::GetPathName](#getpathname)|Vrátí cestu k datovému souboru dokumentu.|
|[CDocument::GetThumbnail](#getthumbnail)|Nazývá se vytvoření bitmapy, kterou má poskytovatel miniatur použít k zobrazení miniatur.|
|[CDocument::GetTitle](#gettitle)|Vrátí název dokumentu.|
|[CDocument::InicializovatObsah vyhledávání](#initializesearchcontent)|Nazývá se inicializovat vyhledávací obsah pro obslužnou rutinu vyhledávání.|
|[Cdocument::IsModified](#ismodified)|Označuje, zda byl dokument od posledního uložení změněn.|
|[Cdocument::IsSearchAndOrganizeHandler](#issearchandorganizehandler)|Určuje, zda `CDocument` byla tato instance objektu vytvořena pro obslužnou rutinu Search & Organize.|
|[CDocument::NačístDocumentFromStream](#loaddocumentfromstream)|Nazývá se načíst data dokumentu z datového proudu.|
|[CDocument::OnBeforePředRichPreviewFontChanged](#onbeforerichpreviewfontchanged)|Nazývá se před změnou písma rich preview.|
|[Cdocument::OnChangedViewList](#onchangedviewlist)|Volána po přidání zobrazení nebo odebrání z dokumentu.|
|[Cdocument::OnCloseDocument](#onclosedocument)|Volána k zavření dokumentu.|
|[Cdocument::OnCreatePreviewFrame](#oncreatepreviewframe)|Volat rámci, když potřebuje vytvořit rámec náhledu pro rich preview.|
|[Cdocument::Událost OnDocumentEvent](#ondocumentevent)|Volat rámci v reakci na událost dokumentu.|
|[CDocument::OnDrawThumbnail](#ondrawthumbnail)|Přepsat tuto metodu v odvozené třídě kreslit obsah miniatury.|
|[Cdocument::OnLoadDocumentFromStream](#onloaddocumentfromstream)|Volat rámci, když potřebuje načíst data dokumentu z datového proudu.|
|[Cdocument::OnNewDocument](#onnewdocument)|Nazývá se vytvořit nový dokument.|
|[Cdocument::OnOpenDocument](#onopendocument)|Nazývá se otevření existujícího dokumentu.|
|[Cdocument::OnPreviewHandlerQueryFocus](#onpreviewhandlerqueryfocus)|Přesměruje obslužnou rutinu náhledu vrátit HWND z volání Funkce GetFocus.|
|[CDocument::OnPreviewHandlerTranslateAccelerator](#onpreviewhandlertranslateaccelerator)|Přesměruje obslužnou rutinu náhledu ke zpracování stisknutí klávesy předané z čerpadla zprávy procesu, ve kterém je spuštěna obslužná rutina náhledu.|
|[Cdocument::OnrichPreviewBackColorChanged](#onrichpreviewbackcolorchanged)|Nazývá se při změně barvy pozadí v rozšířeném náhledu.|
|[CDocument::OnRichPreviewFontChanged](#onrichpreviewfontchanged)|Nazývá se při změně písma rich preview.|
|[CDocument::OnRichPreviewSiteChanged](#onrichpreviewsitechanged)|Nazývá se při změně webu Rich Preview.|
|[Cdocument::OnRichPreviewTextColorZměněn](#onrichpreviewtextcolorchanged)|Nazývá se při změně barvy textu v rozšířeném náhledu.|
|[Cdocument::OnSaveDocument](#onsavedocument)|Nazývá se uložení dokumentu na disk.|
|[Cdocument::Obslužné volání po obslanosti](#onunloadhandler)|Volat rámci při uvolnění obslužné rutiny náhledu.|
|[CDocument::PreCloseFrame](#precloseframe)|Volána před zavřením okna rámce.|
|[CDocument::ReadNextChunkValue](#readnextchunkvalue)|Čte další blok hodnotu.|
|[CDocument::ReleaseFile](#releasefile)|Uvolní soubor, aby byl k dispozici pro použití jinými aplikacemi.|
|[CDocument::RemoveChunk](#removechunk)|Odebere blok s zadaným identifikátorem GUID.|
|[CDocument::RemoveView](#removeview)|Odpojí zobrazení od dokumentu.|
|[CDocument::Výjimka pro ukládání zpráv](#reportsaveloadexception)|Pokročilé overridable; volána, pokud nelze dokončit operaci otevření nebo uložení z důvodu výjimky.|
|[CDocument::UložitZměněno](#savemodified)|Pokročilé overridable; volána a zeptat se uživatele, zda má být dokument uložen.|
|[CDocument::SetChunkValue](#setchunkvalue)|Nastaví hodnotu bloku.|
|[CDocument::SetModifiedFlag](#setmodifiedflag)|Nastaví příznak označující, že jste dokument od posledního uložení upravili.|
|[CDocument::SetPathName](#setpathname)|Nastaví cestu k datovému souboru používanému dokumentem.|
|[CDocument::SetTitle](#settitle)|Nastaví název dokumentu.|
|[CDocument::UpdateAllViews](#updateallviews)|Upozorní všechna zobrazení, která byla změněna.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[Cdocument::OnFileSendMail](#onfilesendmail)|Odešle e-mailovou zprávu s připojeným dokumentem.|
|[Cdocument::OnUpdateFileSendMail](#onupdatefilesendmail)|Povolí příkaz Odeslat poštu, pokud je k dispozici podpora pošty.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CDocument::m_bGetThumbnailMode](#m_bgetthumbnailmode)|Určuje, `CDocument` že objekt byl vytvořen dllhost pro miniatury. Je třeba zkontrolovat `CView::OnDraw`.|
|[CDocument::m_bPreviewHandlerMode](#m_bpreviewhandlermode)|Určuje, `CDocument` že objekt byl vytvořen `Rich Preview`prevhost pro . Je třeba zkontrolovat `CView::OnDraw`.|
|[CDocument::m_bSearchMode](#m_bsearchmode)|Určuje, `CDocument` že objekt byl vytvořen indexerem nebo jinou vyhledávací aplikací.|
|[CDocument::m_clrRichPreviewBackColor](#m_clrrichpreviewbackcolor)|Určuje barvu pozadí okna Sypký náhled. Tato barva je nastavena hostitelem.|
|[CDocument::m_clrRichPreviewTextColor](#m_clrrichpreviewtextcolor)|Určuje barvu popředí okna Rich Preview. Tato barva je nastavena hostitelem.|
|[CDocument::m_lfRichPreviewFont](#m_lfrichpreviewfont)|Určuje písmo textu pro okno RtN/l. Tyto informace o písmu jsou nastaveny hostitelem.|

## <a name="remarks"></a>Poznámky

Dokument představuje jednotku dat, kterou uživatel obvykle otevře pomocí příkazu Otevřít soubor a uloží jej pomocí příkazu Uložit soubor.

`CDocument`podporuje standardní operace, jako je vytváření dokumentu, jeho načítání a ukládání. Rozhraní framework manipuluje s dokumenty `CDocument`pomocí rozhraní definovaného rozhraním .

Aplikace může podporovat více než jeden typ dokumentu; Aplikace může například podporovat tabulky i textové dokumenty. Každý typ dokumentu má přidruženou šablonu dokumentu. šablona dokumentu určuje, jaké prostředky (například nabídka, ikona nebo tabulka akcelerátoru) se pro daný typ dokumentu používají. Každý dokument obsahuje ukazatel `CDocTemplate` na přidružený objekt.

Uživatelé pracují s dokumentem prostřednictvím objektů [CView,](../../mfc/reference/cview-class.md) které jsou k němu přidruženy. Zobrazení vykreslí obraz dokumentu v okně rámce a interpretuje vstup uživatele jako operace v dokumentu. K dokumentu může být přidruženo více zobrazení. Když uživatel otevře okno v dokumentu, rozhraní vytvoří zobrazení a připojí jej k dokumentu. Šablona dokumentu určuje, jaký typ zobrazení a okna rámce se použije k zobrazení jednotlivých typů dokumentů.

Dokumenty jsou součástí standardního směrování příkazů rozhraní a následně přijímají příkazy ze standardních součástí uživatelského rozhraní (například položky nabídky Ukládat soubor). Dokument přijímá příkazy předané aktivním zobrazením. Pokud dokument nezpracovává daný příkaz, předá příkaz do šablony dokumentu, která jej spravuje.

Při změně dat dokumentu musí každé jeho zobrazení odrážet tyto změny. `CDocument`poskytuje [UpdateAllViews](#updateallviews) členské funkce pro upozornění zobrazení těchto změn, takže zobrazení můžete překreslit sami podle potřeby. Rozhraní také vyzve uživatele k uložení upraveného souboru před jeho zavřením.

Chcete-li implementovat dokumenty v typické aplikaci, je nutné provést následující kroky:

- Odvodit `CDocument` třídu z pro každý typ dokumentu.

- Přidejte členské proměnné pro ukládání dat každého dokumentu.

- Implementujte členské funkce pro čtení a úpravy dat dokumentu. Zobrazení dokumentu jsou nejdůležitějšími uživateli těchto členských funkcí.

- Přepište členská funkci [CObject::Serializovat](../../mfc/reference/cobject-class.md#serialize) ve třídě dokumentu a zapište a načtěte data dokumentu na disk a z disku.

`CDocument`podporuje odesílání dokumentu poštou, pokud je k dispozici podpora pošty (MAPI). Podívejte se na články [MAPI](../../mfc/mapi.md) a [PODPORA MAPI v knihovně MFC](../../mfc/mapi-support-in-mfc.md).

Další informace `CDocument`naleznete v tématu [Serializace](../../mfc/serialization-in-mfc.md), [Témata architektury dokumentu/zobrazení](../../mfc/document-view-architecture.md)a [Vytvoření dokumentu/zobrazení](../../mfc/document-view-creation.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

`CDocument`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="cdocumentaddview"></a><a name="addview"></a>CDocument::AddView

Voláním této funkce připojte zobrazení k dokumentu.

```cpp
void AddView(CView* pView);
```

### <a name="parameters"></a>Parametry

*pZobrazit*<br/>
Odkazuje na přidaný pohled.

### <a name="remarks"></a>Poznámky

Tato funkce přidá zadané zobrazení do seznamu zobrazení přidružených k dokumentu. funkce také nastaví ukazatel dokumentu zobrazení na tento dokument. Framework volá tuto funkci při připojování nově vytvořeného objektu zobrazení k dokumentu; K tomu dochází v reakci na příkaz Nový soubor, Soubor otevřít nebo Nové okno nebo při rozdělení okna rozdělovače.

Tuto funkci zavolejte pouze v případě, že vytváříte a připojujete zobrazení ručně. Obvykle umožníte rozhraní propojit dokumenty a zobrazení definováním objektu [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) tak, aby přidružoval třídu dokumentu, třídu zobrazení a třídu okna rámce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocViewSDI#12](../../mfc/codesnippet/cpp/cdocument-class_1.cpp)]

## <a name="cdocumentbeginreadchunks"></a><a name="beginreadchunks"></a>CDocument::BeginReadChunks

Inicializuje čtení bloků.

```
virtual void BeginReadChunks ();
```

### <a name="remarks"></a>Poznámky

## <a name="cdocumentcancloseframe"></a><a name="cancloseframe"></a>Cdocument::CanCloseFrame

Volat rámci před zavřením okna rámce zobrazující dokument.

```
virtual BOOL CanCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>Parametry

*pRám*<br/>
Odkazuje na okno rámečku pohledu připojeného k dokumentu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je bezpečné zavřít okno rámce; jinak 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace zkontroluje, zda jsou v dokumentu zobrazena jiná okna rámce. Pokud je zadané okno rámce poslední, které dokument zobrazuje, funkce vyzve uživatele k uložení dokumentu, pokud byl změněn. Přepsat tuto funkci, pokud chcete provést speciální zpracování při zavření okna rámce. Tohle je pokročilé překažné.

## <a name="cdocumentcdocument"></a><a name="cdocument"></a>CDocument::CDocument

Vytvoří `CDocument` objekt.

```
CDocument();
```

### <a name="remarks"></a>Poznámky

Rámec zpracovává vytváření dokumentů za vás. Přepište členská funkci [OnNewDocument](#onnewdocument) a proveďte inicializaci na základě dokumentu. to je důležité zejména v aplikacích rozhraní s jedním dokumentem (SDI).

## <a name="cdocumentclearchunklist"></a><a name="clearchunklist"></a>CDocument::ClearChunkList

Vymaže seznam bloků dat.

```
virtual void ClearChunkList ();
```

### <a name="remarks"></a>Poznámky

## <a name="cdocumentclearpathname"></a><a name="clearpathname"></a>CDocument::ClearPathName

Vymaže cestu k objektu dokumentu.

```
virtual void ClearPathName();
```

### <a name="remarks"></a>Poznámky

Vymazání cesty `CDocument` z objektu způsobí, že aplikace vyzve uživatele při dalším uložení dokumentu. Díky tomu se příkaz **Uložit** chová jako příkaz **Uložit jako.**

## <a name="cdocumentdeletecontents"></a><a name="deletecontents"></a>CDocument::DeleteContents

Volat rámci k odstranění dat dokumentu bez zničení `CDocument` samotného objektu.

```
virtual void DeleteContents();
```

### <a name="remarks"></a>Poznámky

Nazývá se těsně před zničením dokumentu. Je také volána k zajištění, že dokument je prázdný před opětovným použitím. To je obzvláště důležité pro aplikaci SDI, která používá pouze jeden dokument; dokument je znovu použit vždy, když uživatel vytvoří nebo otevře jiný dokument. Volání této funkce implementovat "Upravit vymazat vše" nebo podobný příkaz, který odstraní všechna data dokumentu. Výchozí implementace této funkce neprovede žádné provádění. Přepsáním této funkce odstraníte data v dokumentu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#57](../../mfc/codesnippet/cpp/cdocument-class_2.cpp)]

## <a name="cdocumentfindchunk"></a><a name="findchunk"></a>CDocument::FindChunk

Vyhledá blok s určeným identifikátorem GUID.

```
virtual POSITION FindChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>Parametry

*guid*<br/>
Určuje identifikátor GUID bloku, který má být vyhledání.

*Pid*<br/>
Určuje PID bloku, který má být vyhledání.

### <a name="return-value"></a>Návratová hodnota

Pozice v seznamu vnitřní blok v případě úspěchu. Jinak NULL.

### <a name="remarks"></a>Poznámky

## <a name="cdocumentgetadapter"></a><a name="getadapter"></a>CDocument::Adaptér GetAdapter

Vrátí ukazatel na objekt implementující `IDocument` rozhraní.

```
virtual ATL::IDocument* GetAdapter();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt implementující `IDocument` rozhraní.

### <a name="remarks"></a>Poznámky

## <a name="cdocumentgetdoctemplate"></a><a name="getdoctemplate"></a>CDocument::Šablona GetDoc

Voláním této funkce získáte ukazatel na šablonu dokumentu pro tento typ dokumentu.

```
CDocTemplate* GetDocTemplate() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na šablonu dokumentu pro tento typ dokumentu nebo HODNOTU NULL, pokud dokument není spravován šablonou dokumentu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#58](../../mfc/codesnippet/cpp/cdocument-class_3.cpp)]

## <a name="cdocumentgetfile"></a><a name="getfile"></a>CDocument::Soubor GetFile

Volání této členské funkce získat `CFile` ukazatel na objekt.

```
virtual CFile* GetFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CFileException* pError);
```

### <a name="parameters"></a>Parametry

*název souboru lpsz*<br/>
Řetězec, který je cesta k požadovanému souboru. Cesta může být relativní nebo absolutní.

*chyba*<br/>
Ukazatel na existující objekt výjimky souboru, který označuje stav dokončení operace.

*nOpenFlags*<br/>
Režim sdílení a přístupu. Určuje akci, která má být vyřízení při otevírání souboru. Můžete kombinovat možnosti uvedené v CFile [konstruktoru CFile::CFile](../../mfc/reference/cfile-class.md#cfile) pomocí bitového operátoru OR (&#124;). Je vyžadováno jedno přístupové oprávnění a jedna možnost sdílení. `modeCreate` režimy `modeNoInherit` a jsou volitelné.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CFile` objekt.

## <a name="cdocumentgetfirstviewposition"></a><a name="getfirstviewposition"></a>CDocument::GetFirstViewPosition

Voláním této funkce získáte pozici prvního zobrazení v seznamu zobrazení přidružených k dokumentu.

```
virtual POSITION GetFirstViewPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota POSITION, kterou lze použít pro iteraci s člennou funkcí [GetNextView.](#getnextview)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

## <a name="cdocumentgetnextview"></a><a name="getnextview"></a>CDocument::GetNextView

Volání této funkce iterát přes všechny zobrazení dokumentu.

```
virtual CView* GetNextView(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*rPozice*<br/>
Odkaz na hodnotu POSITION vrácenou předchozím `GetNextView` voláním členských funkcí nebo [GetFirstViewPosition.](#getfirstviewposition) Tato hodnota nesmí být null.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na zobrazení označené *rPosition*.

### <a name="remarks"></a>Poznámky

Funkce vrátí zobrazení identifikované *rPosition* a pak nastaví *hodnotu pozice* následujícího zobrazení v seznamu. Pokud je načtené zobrazení poslední v seznamu, je *hodnota rPosition* nastavena na hodnotu NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

## <a name="cdocumentgetpathname"></a><a name="getpathname"></a>CDocument::GetPathName

Voláním této funkce získáte plně kvalifikovanou cestu k souboru disku dokumentu.

```
const CString& GetPathName() const;
```

### <a name="return-value"></a>Návratová hodnota

Plně kvalifikovaná cesta dokumentu. Tento řetězec je prázdný, pokud dokument nebyl uložen nebo k němu není přidružen soubor disku.

## <a name="cdocumentgetthumbnail"></a><a name="getthumbnail"></a>CDocument::GetThumbnail

Vytvoří bitmapu, kterou použije poskytovatel miniatur k zobrazení miniatury.

```
virtual BOOL GetThumbnail(
    UINT cx,
    HBITMAP* phbmp,
    DWORD* pdwAlpha);
```

### <a name="parameters"></a>Parametry

*Cx*<br/>
Určuje šířku a výšku bitmapy.

*phbmp*<br/>
Obsahuje popisovač rastrového mapu, když funkce vrátí úspěšně.

*pdwAlpha*<br/>
Obsahuje DWORD určující hodnotu alfa kanálu, když funkce vrátí úspěšně.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud byla bitmapa miniatury úspěšně vytvořena; jinak FALSE.

### <a name="remarks"></a>Poznámky

## <a name="cdocumentgettitle"></a><a name="gettitle"></a>CDocument::GetTitle

Volánítéto funkce získat název dokumentu, který je obvykle odvozen od názvu souboru dokumentu.

```
const CString& GetTitle() const;
```

### <a name="return-value"></a>Návratová hodnota

Název dokumentu.

## <a name="cdocumentinitializesearchcontent"></a><a name="initializesearchcontent"></a>CDocument::InicializovatObsah vyhledávání

Nazývá se inicializovat vyhledávací obsah pro obslužnou rutinu vyhledávání.

```
virtual void InitializeSearchContent ();
```

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu v odvozené třídě inicializovat vyhledávací obsah. Obsah by měl být řetězec s částmi oddělenými ";". Například "point; obdélník; ole položky".

## <a name="cdocumentismodified"></a><a name="ismodified"></a>Cdocument::IsModified

Volání této funkce k určení, zda byl dokument změněn od posledního uložení.

```
virtual BOOL IsModified();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl dokument od posledního uložení změněn; jinak 0.

## <a name="cdocumentissearchandorganizehandler"></a><a name="issearchandorganizehandler"></a>Cdocument::IsSearchAndOrganizeHandler

Určuje, zda `CDocument` byla tato instance aplikace byla vytvořena pro & obslužnou rutinu organizace.

```
BOOL IsSearchAndOrganizeHandler() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud `CDocument` byla tato instance aplikace vytvořena pro obslužnou rutinu Organizace hledání &.

### <a name="remarks"></a>Poznámky

V současné době tato funkce vrátí hodnotu PRAVDA pouze pro obslužné rutiny rich preview implementované na mimoprocesovém serveru. Můžete nastavit příslušné příznaky (m_bPreviewHandlerMode, m_bSearchMode, m_bGetThumbnailMode) na úrovni aplikace, aby tato funkce vrátila hodnotu TRUE.

## <a name="cdocumentloaddocumentfromstream"></a><a name="loaddocumentfromstream"></a>CDocument::NačístDocumentFromStream

Nazývá se načíst data dokumentu z datového proudu.

```
virtual HRESULT LoadDocumentFromStream(
    IStream* pStream,
    DWORD dwGrfMode);
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
Ukazatel na datový proud. Tento datový proud je dodáván prostředí.

*dwGrfMode*<br/>
Režim přístupu k datovému proudu.

### <a name="return-value"></a>Návratová hodnota

S_OK pokud je operace zatížení úspěšná, jinak HRESULT s kódem chyby.

### <a name="remarks"></a>Poznámky

Tuto metodu můžete přepsat v odvozené třídě přizpůsobit způsob načítání dat z datového proudu.

## <a name="cdocumentm_bgetthumbnailmode"></a><a name="m_bgetthumbnailmode"></a>CDocument::m_bGetThumbnailMode

Určuje, že `CDocument` objekt byl vytvořen dllhost pro miniatury. Je třeba zkontrolovat `CView::OnDraw`.

```
BOOL m_bGetThumbnailMode;
```

### <a name="remarks"></a>Poznámky

`TRUE`označuje, že dokument byl vytvořen dllhost pro miniatury.

## <a name="cdocumentm_bpreviewhandlermode"></a><a name="m_bpreviewhandlermode"></a>CDocument::m_bPreviewHandlerMode

Určuje, že `CDocument` objekt byl vytvořen prevhost pro rich preview. Je třeba zkontrolovat `CView::OnDraw`.

```
BOOL m_bPreviewHandlerMode;
```

### <a name="remarks"></a>Poznámky

TRUE označuje, že dokument byl vytvořen prevhost pro Rich Preview.

## <a name="cdocumentm_bsearchmode"></a><a name="m_bsearchmode"></a>CDocument::m_bSearchMode

Určuje, že `CDocument` objekt byl vytvořen indexerem nebo jinou vyhledávací aplikací.

```
BOOL m_bSearchMode;
```

### <a name="remarks"></a>Poznámky

`TRUE`označuje, že dokument byl vytvořen indexerem nebo jinou vyhledávací aplikací.

## <a name="cdocumentm_clrrichpreviewbackcolor"></a><a name="m_clrrichpreviewbackcolor"></a>CDocument::m_clrRichPreviewBackColor

Určuje barvu pozadí okna Rich Preview. Tato barva je nastavena hostitelem.

```
COLORREF m_clrRichPreviewBackColor;
```

### <a name="remarks"></a>Poznámky

## <a name="cdocumentm_clrrichpreviewtextcolor"></a><a name="m_clrrichpreviewtextcolor"></a>CDocument::m_clrRichPreviewTextColor

Určuje barvu popředí okna Rich Preview. Tato barva je nastavena hostitelem.

```
COLORREF m_clrRichPreviewTextColor;
```

### <a name="remarks"></a>Poznámky

## <a name="cdocumentm_lfrichpreviewfont"></a><a name="m_lfrichpreviewfont"></a>CDocument::m_lfRichPreviewFont

Určuje písmo textu pro okno Rich Preview. Tyto informace o písmu jsou nastaveny hostitelem.

```
CFont m_lfRichPreviewFont;
```

### <a name="remarks"></a>Poznámky

## <a name="cdocumentonbeforerichpreviewfontchanged"></a><a name="onbeforerichpreviewfontchanged"></a>CDocument::OnBeforePředRichPreviewFontChanged

Volána před změnou písma Rich Preview.

```
virtual void OnBeforeRichPreviewFontChanged();
```

### <a name="remarks"></a>Poznámky

## <a name="cdocumentonchangedviewlist"></a><a name="onchangedviewlist"></a>Cdocument::OnChangedViewList

Volat rámci po zobrazení je přidán do dokumentu nebo odebránz dokumentu.

```
virtual void OnChangedViewList();
```

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce zkontroluje, zda je odebráno poslední zobrazení, a pokud ano, odstraní dokument. Přepsat tuto funkci, pokud chcete provést speciální zpracování při rozhraní přidá nebo odebere zobrazení. Pokud například chcete, aby dokument zůstal otevřený i v případě, že k němu nejsou připojeny žádné pohledy, přepište tuto funkci.

## <a name="cdocumentonclosedocument"></a><a name="onclosedocument"></a>Cdocument::OnCloseDocument

Volat rámci při zavření dokumentu, obvykle jako součást file close příkazu.

```
virtual void OnCloseDocument();
```

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce zničí všechny rámce použité k zobrazení dokumentu, zavře zobrazení, vyčistí obsah dokumentu a pak zavolá člennou funkci [DeleteContents](#deletecontents) k odstranění dat dokumentu.

Přepsat tuto funkci, pokud chcete provést speciální vyčištění zpracování při uzavření rámce dokumentu. Pokud například dokument představuje záznam v databázi, můžete tuto funkci přepsat a databázi zavřít. Měli byste volat verzi základní třídy této funkce z přepsání.

## <a name="cdocumentoncreatepreviewframe"></a><a name="oncreatepreviewframe"></a>Cdocument::OnCreatePreviewFrame

Volat rámci, když potřebuje vytvořit rámec náhledu pro rich preview.

```
virtual BOOL OnCreatePreviewFrame();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je rámeček úspěšně vytvořen. jinak FALSE.

### <a name="remarks"></a>Poznámky

## <a name="cdocumentondocumentevent"></a><a name="ondocumentevent"></a>Cdocument::Událost OnDocumentEvent

Volat rámci v reakci na událost dokumentu.

```
virtual void OnDocumentEvent(DocumentEvent deEvent);
```

### <a name="parameters"></a>Parametry

*deEvent*<br/>
[v] Výčtový datový typ, který popisuje typ události.

### <a name="remarks"></a>Poznámky

Události dokumentu mohou ovlivnit více tříd. Tato metoda je zodpovědná za zpracování událostí dokumentu, které ovlivňují jiné třídy než [třídu CDocument](../../mfc/reference/cdocument-class.md). V současné době jedinou třídou, která musí reagovat na události dokumentu, [třída CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md). Třída `CDocument` má jiné přepsatelné metody odpovědné za `CDocument`zpracování vlivu na .

V následující tabulce jsou uvedeny možné hodnoty pro *deEvent* a události, které odpovídají.

|Hodnota|Odpovídající událost|
|-----------|-------------------------|
|`onAfterNewDocument`|Byl vytvořen nový dokument.|
|`onAfterOpenDocument`|Byl otevřen nový dokument.|
|`onAfterSaveDocument`|Dokument byl uložen.|
|`onAfterCloseDocument`|Dokument byl uzavřen.|

## <a name="cdocumentondrawthumbnail"></a><a name="ondrawthumbnail"></a>CDocument::OnDrawThumbnail

Přepsat tuto metodu v odvozené třídě k tomu miniaturu.

```
virtual void OnDrawThumbnail(
    CDC& dc,
    LPRECT lprcBounds);
```

### <a name="parameters"></a>Parametry

*Dc*<br/>
Odkaz na kontext zařízení.

*lprcBounds*<br/>
Určuje ohraničující obdélník oblasti, kde má být miniatura nakreslena.

### <a name="remarks"></a>Poznámky

## <a name="cdocumentonfilesendmail"></a><a name="onfilesendmail"></a>Cdocument::OnFileSendMail

Odešle zprávu prostřednictvím rezidentního poštovního hostitele (pokud existuje) s dokumentem jako přílohou.

```cpp
void OnFileSendMail();
```

### <a name="remarks"></a>Poznámky

`OnFileSendMail`volá [OnSaveDocument](#onsavedocument) serializovat (uložit) bez názvu a upravené dokumenty do dočasného souboru, který je pak odeslán prostřednictvím elektronické pošty. Pokud dokument nebyl změněn, dočasný soubor není potřeba. originál odeslán. `OnFileSendMail`načte MAPI32. DLL, pokud ještě nebyla načtena.

Speciální implementace `OnFileSendMail` pro [COleDocument](../../mfc/reference/coledocument-class.md) zpracovává složené soubory správně.

`CDocument`podporuje odesílání dokumentu poštou, pokud je k dispozici podpora pošty (MAPI). Podívejte se na články [MAPI Témata](../../mfc/mapi.md) a [PODPORA MAPI v knihovně MFC](../../mfc/mapi-support-in-mfc.md).

## <a name="cdocumentonloaddocumentfromstream"></a><a name="onloaddocumentfromstream"></a>Cdocument::OnLoadDocumentFromStream

Volat rámci, když potřebuje načíst data dokumentu z datového proudu.

```
virtual HRESULT OnLoadDocumentFromStream(
    IStream* pStream,
    DWORD grfMode);
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
Ukazatel na příchozí datový proud.

*režim grfMode*<br/>
Režim přístupu k datovému proudu.

### <a name="return-value"></a>Návratová hodnota

S_OK, pokud je zatížení úspěšné; v opačném případě kód chyby.

### <a name="remarks"></a>Poznámky

## <a name="cdocumentonnewdocument"></a><a name="onnewdocument"></a>Cdocument::OnNewDocument

Volat rámci jako součást file new příkazu.

```
virtual BOOL OnNewDocument();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl dokument úspěšně inicializován; jinak 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce volá člennou funkci [DeleteContents,](#deletecontents) aby zajistila, že dokument je prázdný, a poté označí nový dokument jako čistý. Přepište tuto funkci a inicializujte datovou strukturu pro nový dokument. Měli byste volat verzi základní třídy této funkce z přepsání.

Pokud uživatel zvolí příkaz Nový soubor v aplikaci SDI, rozhraní používá tuto funkci k opětovné inicializaci existujícího dokumentu, nikoli k vytvoření nového dokumentu. Pokud uživatel zvolí Soubor nový v aplikaci rozhraní více dokumentů (MDI), rozhraní vytvoří nový dokument pokaždé a potom volá tuto funkci inicializovat. Je nutné umístit inicializační kód v této funkci namísto v konstruktoru pro soubor nový příkaz, aby byla účinná v aplikacích SDI.

Všimněte si, `OnNewDocument` že existují případy, kdy je volána dvakrát. K tomu dochází, když je dokument vložen jako dokument ActiveX. Funkce je nejprve `CreateInstance` volána metodou `COleObjectFactory`(vystavená -derived class) `InitNew` a podruhé `COleServerDoc`metodou (vystavená -derived class).

### <a name="example"></a>Příklad

Následující příklady ilustrují alternativní metody inicializace objektu dokumentu.

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

## <a name="cdocumentonopendocument"></a><a name="onopendocument"></a>Cdocument::OnOpenDocument

Volat rámci jako součást příkazu Otevřít soubor.

```
virtual BOOL OnOpenDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
Ukazuje na cestu dokumentu, který má být otevřen.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl dokument úspěšně načten; jinak 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce otevře zadaný soubor, zavolá člennou funkci [DeleteContents,](#deletecontents) aby zajistila, že dokument je prázdný, zavolá [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) ke čtení obsahu souboru a označí dokument jako čistý. Přepsat tuto funkci, pokud chcete použít něco jiného než mechanismus archivace nebo mechanismus souborů. Můžete například napsat aplikaci, kde dokumenty představují záznamy v databázi, nikoli samostatné soubory.

Pokud uživatel zvolí příkaz Otevřít soubor v aplikaci SDI, rozhraní používá tuto `CDocument` funkci k opětovné inicializaci existujícího objektu, nikoli k vytvoření nového objektu. Pokud uživatel zvolí Soubor Otevřít v aplikaci MDI, `CDocument` rozhraní vytvoří nový objekt pokaždé a pak volá tuto funkci k jeho inicializaci. Je nutné umístit inicializační kód v této funkci namísto v konstruktoru pro soubor otevřít příkaz, aby byla účinná v aplikacích SDI.

### <a name="example"></a>Příklad

Následující příklady ilustrují alternativní metody inicializace objektu dokumentu.

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

[!code-cpp[NVC_MFCDocView#63](../../mfc/codesnippet/cpp/cdocument-class_8.cpp)]

## <a name="cdocumentonpreviewhandlerqueryfocus"></a><a name="onpreviewhandlerqueryfocus"></a>Cdocument::OnPreviewHandlerQueryFocus

Přesměruje obslužnou rutinu náhledu, aby vrátila HWND načtenou z volání `GetFocus` funkce.

```
virtual HRESULT OnPreviewHandlerQueryFocus(HWND* phwnd);
```

### <a name="parameters"></a>Parametry

*fwnd*<br/>
[out] Když tato metoda vrátí, obsahuje ukazatel hwnd `GetFocus` vrácena z volání funkce z vlákna obslužné rutiny náhledu.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK v případě úspěchu. nebo chybovou hodnotu jinak.

### <a name="remarks"></a>Poznámky

## <a name="cdocumentonpreviewhandlertranslateaccelerator"></a><a name="onpreviewhandlertranslateaccelerator"></a>CDocument::OnPreviewHandlerTranslateAccelerator

Přesměruje obslužnou rutinu náhledu ke zpracování stisknutí klávesy předané z čerpadla zprávy procesu, ve kterém je spuštěna obslužná rutina náhledu.

```
virtual HRESULT OnPreviewHandlerTranslateAccelerator(MSG* pmsg);
```

### <a name="parameters"></a>Parametry

*pmsg*<br/>
[v] Ukazatel na zprávu okna.

### <a name="return-value"></a>Návratová hodnota

Pokud zpráva stisknutí klávesy může být zpracována obslužnou rutinou náhledu, obslužná rutina ji zpracuje a vrátí S_OK. Pokud obslužná rutina náhledu nemůže zpracovat `IPreviewHandlerFrame::TranslateAccelerator`zprávu stisku klávesy, nabídne ji hostiteli prostřednictvím aplikace . Pokud hostitel zprávu zpracuje, vrátí tato metoda S_OK. Pokud hostitel zprávu nezpracuje, vrátí tato metoda S_FALSE.

### <a name="remarks"></a>Poznámky

## <a name="cdocumentonrichpreviewbackcolorchanged"></a><a name="onrichpreviewbackcolorchanged"></a>Cdocument::OnrichPreviewBackColorChanged

Nazývá se při změně barvy pozadí v rozšířeném náhledu.

```
virtual void OnRichPreviewBackColorChanged();
```

### <a name="remarks"></a>Poznámky

## <a name="cdocumentonrichpreviewfontchanged"></a><a name="onrichpreviewfontchanged"></a>CDocument::OnRichPreviewFontChanged

Nazývá se při změně písma Rich Preview.

```
virtual void OnRichPreviewFontChanged();
```

### <a name="remarks"></a>Poznámky

## <a name="cdocumentonrichpreviewsitechanged"></a><a name="onrichpreviewsitechanged"></a>CDocument::OnRichPreviewSiteChanged

Nazývá se při změně webu Rich Preview.

```
virtual void OnRichPreviewSiteChanged();
```

### <a name="remarks"></a>Poznámky

## <a name="cdocumentonrichpreviewtextcolorchanged"></a><a name="onrichpreviewtextcolorchanged"></a>Cdocument::OnRichPreviewTextColorZměněn

Nazývá se při změně barvy textu s formátovaným náhledem.

```
virtual void OnRichPreviewTextColorChanged();
```

### <a name="remarks"></a>Poznámky

## <a name="cdocumentonsavedocument"></a><a name="onsavedocument"></a>Cdocument::OnSaveDocument

Nazývá rámci jako součást souboru uložit nebo soubor uložit jako příkaz.

```
virtual BOOL OnSaveDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
Odkazuje na plně kvalifikovanou cestu, do které by měl být soubor uložen.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl dokument úspěšně uložen; jinak 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce otevře zadaný soubor, zavolá [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) pro zápis dat dokumentu do souboru a pak označí dokument jako čistý. Přepsat tuto funkci, pokud chcete provést speciální zpracování při rozhraní uloží dokument. Můžete například napsat aplikaci, kde dokumenty představují záznamy v databázi, nikoli samostatné soubory.

## <a name="cdocumentonunloadhandler"></a><a name="onunloadhandler"></a>Cdocument::Obslužné volání po obslanosti

Volat rámci při uvolnění obslužné rutiny náhledu.

```
virtual void OnUnloadHandler();
```

### <a name="remarks"></a>Poznámky

## <a name="cdocumentonupdatefilesendmail"></a><a name="onupdatefilesendmail"></a>Cdocument::OnUpdateFileSendMail

Povolí příkaz ID_FILE_SEND_MAIL, pokud je k dispozici podpora pošty (MAPI).

```cpp
void OnUpdateFileSendMail(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Ukazatel na objekt [CCmdUI](../../mfc/reference/ccmdui-class.md) přidružený k příkazu ID_FILE_SEND_MAIL.

### <a name="remarks"></a>Poznámky

V opačném případě funkce odebere příkaz ID_FILE_SEND_MAIL z nabídky, včetně oddělovačů nad nebo pod položkou nabídky podle potřeby. MAPI je povolena, pokud MAPI32. DLL je k dispozici v cestě a v části [Mail] win. INI soubor, MAPI=1. Většina aplikací vloží tento příkaz do nabídky Soubor.

`CDocument`podporuje odesílání dokumentu poštou, pokud je k dispozici podpora pošty (MAPI). Podívejte se na články [MAPI Témata](../../mfc/mapi.md) a [PODPORA MAPI v knihovně MFC](../../mfc/mapi-support-in-mfc.md).

## <a name="cdocumentprecloseframe"></a><a name="precloseframe"></a>CDocument::PreCloseFrame

Tato členská funkce je volána rámci před okno rámce je zničen.

```
virtual void PreCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>Parametry

*pRám*<br/>
Ukazatel na [CFrameWnd,](../../mfc/reference/cframewnd-class.md) který `CDocument` obsahuje přidružený objekt.

### <a name="remarks"></a>Poznámky

Může být přepsána poskytnout vlastní vyčištění, ale nezapomeňte volat základní třídy také.

Výchozí neprovede `PreCloseFrame` žádné `CDocument`provede v . -derived `CDocument`třídy [COleDocument](../../mfc/reference/coledocument-class.md) a [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) použít tuto členskou funkci.

## <a name="cdocumentreadnextchunkvalue"></a><a name="readnextchunkvalue"></a>CDocument::ReadNextChunkValue

Přečte další hodnotu bloku.

```
virtual BOOL ReadNextChunkValue(IFilterChunkValue** ppValue);
```

### <a name="parameters"></a>Parametry

*ppValue*<br/>
[out] Když funkce vrátí, *ppValue* obsahuje hodnotu, která byla přečtena.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

## <a name="cdocumentreleasefile"></a><a name="releasefile"></a>CDocument::ReleaseFile

Tato členská funkce je volána rozhraním pro uvolnění souboru, takže je k dispozici pro použití jinými aplikacemi.

```
virtual void ReleaseFile(
    CFile* pFile,
    BOOL bAbort);
```

### <a name="parameters"></a>Parametry

*pSoubor*<br/>
Ukazatel na cfile objektu, který má být uvolněn.

*bPřerušit*<br/>
Určuje, zda má být soubor uvolněn `CFile::Close` `CFile::Abort`pomocí jednoho nebo . FALSE, pokud má být soubor vydán pomocí [cfile::Close](../../mfc/reference/cfile-class.md#close); TRUE, pokud má být soubor vydán pomocí [CFile::Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="remarks"></a>Poznámky

Pokud *je hodnota bAbort* true, `ReleaseFile` volání `CFile::Abort`a uvolnění souboru. `CFile::Abort`nevyvolá výjimku.

Pokud *bAbort* je `ReleaseFile` `CFile::Close` FALSE, volání a soubor je uvolněna.

Přepište tuto členovou funkci tak, aby vyžadovala akci uživatele před vydáním souboru.

## <a name="cdocumentremovechunk"></a><a name="removechunk"></a>CDocument::RemoveChunk

Odebere blok s zadaným identifikátorem GUID.

```
virtual void RemoveChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>Parametry

*Identifikátor guid*<br/>
Určuje identifikátor GUID bloku, který má být odebrán.

*Pid*<br/>
Určuje PID bloku, který má být odebrán.

### <a name="remarks"></a>Poznámky

## <a name="cdocumentremoveview"></a><a name="removeview"></a>CDocument::RemoveView

Voláním této funkce odpojte zobrazení od dokumentu.

```cpp
void RemoveView(CView* pView);
```

### <a name="parameters"></a>Parametry

*pZobrazit*<br/>
Odkazuje na odebírá zobrazení.

### <a name="remarks"></a>Poznámky

Tato funkce odebere zadané zobrazení ze seznamu zobrazení přidružených k dokumentu. také nastaví ukazatel dokumentu zobrazení na HODNOTU NULL. Tato funkce je volána rámci při zavření okna rámce nebo zavření podokna okna rozdělovače.

Tuto funkci zavolejte pouze v případě, že zobrazení odpojíte ručně. Obvykle umožníte rozhraní odpojit dokumenty a zobrazení definováním [cDocTemplate](../../mfc/reference/cdoctemplate-class.md) objektu přidružit třídu dokumentu, třídu zobrazení a třídu okna rámce.

Viz příklad na [AddView](#addview) pro ukázkovou implementaci.

## <a name="cdocumentreportsaveloadexception"></a><a name="reportsaveloadexception"></a>CDocument::Výjimka pro ukládání zpráv

Volána, pokud je vyvolána výjimka (obvykle [CFileException](../../mfc/reference/cfileexception-class.md) nebo [CArchiveException](../../mfc/reference/carchiveexception-class.md)) při ukládání nebo načítání dokumentu.

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

*E*<br/>
Odkazuje na výjimku, která byla vyvolána. Může být null.

*bUkládání*<br/>
Příznak označující, o jaké operaci se dělo; nenulová, pokud byl dokument uložen, 0, pokud byl dokument načítán.

*nIDPVýchozí*<br/>
Identifikátor chybové zprávy, která má být zobrazena, pokud funkce neurčuje konkrétnější zprávu.

### <a name="remarks"></a>Poznámky

Výchozí implementace zkontroluje objekt výjimky a vyhledá chybovou zprávu, která konkrétně popisuje příčinu. Pokud není nalezena určitá zpráva nebo hodnota *e* je NULL, použije se obecná zpráva určená parametrem *nIDPDefault.* Funkce pak zobrazí okno se zprávou obsahující chybovou zprávu. Přepsat tuto funkci, pokud chcete poskytnout další, přizpůsobené zprávy selhání. Tohle je pokročilé překažné.

## <a name="cdocumentsavemodified"></a><a name="savemodified"></a>CDocument::UložitZměněno

Volat rámci před změněný dokument má být uzavřen.

```
virtual BOOL SaveModified();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je bezpečné pokračovat a zavřít dokument; 0, pokud by dokument neměl být uzavřen.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce zobrazí okno se zprávou s dotazem, zda má uživatel uložit změny v dokumentu, pokud byly provedeny. Tuto funkci přepište, pokud program vyžaduje jiný postup dotazování. Tohle je pokročilé překažné.

## <a name="cdocumentsetchunkvalue"></a><a name="setchunkvalue"></a>CDocument::SetChunkValue

Nastaví hodnotu bloku.

```
virtual BOOL SetChunkValue (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>Parametry

*pHodnota*<br/>
Určuje nastavenou hodnotu bloku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

## <a name="cdocumentsetmodifiedflag"></a><a name="setmodifiedflag"></a>CDocument::SetModifiedFlag

Tuto funkci zavolejte po provedené mši dokumentu.

```
virtual void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Parametry

*bZměněno*<br/>
Příznak označující, zda byl dokument změněn.

### <a name="remarks"></a>Poznámky

Voláním této funkce konzistentně zajistíte, že rozhraní framework vyzve uživatele k uložení změn před zavřením dokumentu. Obvykle byste měli použít výchozí hodnotu TRUE pro parametr *bModified.* Chcete-li označit dokument jako čistý (nezměněno), zavolejte tuto funkci s hodnotou FALSE.

## <a name="cdocumentsetpathname"></a><a name="setpathname"></a>CDocument::SetPathName

Voláním této funkce určete plně kvalifikovanou cestu k souboru disku dokumentu.

```
virtual void SetPathName(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
Odkazuje na řetězec, který má být použit jako cesta pro dokument.

*bAddToMRU*<br/>
Určuje, zda je název souboru přidán do seznamu naposledy použitých souborů (MRU). Pokud true, je přidán název souboru; pokud false, není přidán.

### <a name="remarks"></a>Poznámky

V závislosti na hodnotě *bAddToMRU* cesta je přidána nebo není přidána do seznamu MRU spravovaného aplikací. Všimněte si, že některé dokumenty nejsou přidruženy k souboru disku. Tuto funkci zavolejte pouze v případě, že přepíšete výchozí implementaci pro otevírání a ukládání souborů používaných v rámci.

## <a name="cdocumentsettitle"></a><a name="settitle"></a>CDocument::SetTitle

Voláním této funkce určete název dokumentu (řetězec zobrazený v záhlaví okna rámce).

```
virtual void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>Parametry

*lpszNázev*<br/>
Odkazuje na řetězec, který má být použit jako název dokumentu.

### <a name="remarks"></a>Poznámky

Volání této funkce aktualizuje názvy všech oken rámce, které zobrazují dokument.

## <a name="cdocumentupdateallviews"></a><a name="updateallviews"></a>CDocument::UpdateAllViews

Volání této funkce po změně dokumentu.

```cpp
void UpdateAllViews(
    CView* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL);
```

### <a name="parameters"></a>Parametry

*pOdesílatelí*<br/>
Odkazuje na zobrazení, které změnilo dokument nebo NULL, pokud mají být aktualizována všechna zobrazení.

*lTip*<br/>
Obsahuje informace o úpravě.

*pHint*<br/>
Odkazuje na objekt ukládající informace o úpravě.

### <a name="remarks"></a>Poznámky

Tuto funkci byste měli volat po volání členské funkce [SetModifiedFlag.](#setmodifiedflag) Tato funkce informuje každé zobrazení připojené k dokumentu, s výjimkou zobrazení určeného *pSender*, že dokument byl změněn. Obvykle voláte tuto funkci z třídy zobrazení poté, co uživatel změnil dokument prostřednictvím zobrazení.

Tato funkce volá [cview::OnUpdate](../../mfc/reference/cview-class.md#onupdate) člennou funkci pro každý z zobrazení dokumentu s výjimkou zobrazení odesílání, předávání *pHint* a *lHint*. Tyto parametry slouží k předání informací do zobrazení o změnách provedených v dokumentu. Můžete zakódovat informace pomocí *lHint* a/nebo můžete definovat [CObject](../../mfc/reference/cobject-class.md)-odvozené třídy pro ukládání informací o změnách a předat objekt této třídy pomocí *pHint*. Přepište `CView::OnUpdate` členskou funkci ve třídě [CView](../../mfc/reference/cview-class.md)-derived a optimalizujte aktualizaci zobrazení na základě předaných informací.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#64](../../mfc/codesnippet/cpp/cdocument-class_9.cpp)]

## <a name="see-also"></a>Viz také

[MFC Vzorek MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[Ukázka knihovny MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[Ukázková předsazená je knihovna MFC](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Třída CView](../../mfc/reference/cview-class.md)<br/>
[Třída CDocTemplate](../../mfc/reference/cdoctemplate-class.md)
