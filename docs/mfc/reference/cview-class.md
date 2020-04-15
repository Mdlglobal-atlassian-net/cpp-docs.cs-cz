---
title: Třída CView
ms.date: 11/04/2016
f1_keywords:
- CView
- AFXWIN/CView
- AFXWIN/CView::CView
- AFXWIN/CView::DoPreparePrinting
- AFXWIN/CView::GetDocument
- AFXWIN/CView::IsSelected
- AFXWIN/CView::OnDragEnter
- AFXWIN/CView::OnDragLeave
- AFXWIN/CView::OnDragOver
- AFXWIN/CView::OnDragScroll
- AFXWIN/CView::OnDrop
- AFXWIN/CView::OnDropEx
- AFXWIN/CView::OnInitialUpdate
- AFXWIN/CView::OnPrepareDC
- AFXWIN/CView::OnScroll
- AFXWIN/CView::OnScrollBy
- AFXWIN/CView::OnActivateFrame
- AFXWIN/CView::OnActivateView
- AFXWIN/CView::OnBeginPrinting
- AFXWIN/CView::OnDraw
- AFXWIN/CView::OnEndPrinting
- AFXWIN/CView::OnEndPrintPreview
- AFXWIN/CView::OnPreparePrinting
- AFXWIN/CView::OnPrint
- AFXWIN/CView::OnUpdate
helpviewer_keywords:
- CView [MFC], CView
- CView [MFC], DoPreparePrinting
- CView [MFC], GetDocument
- CView [MFC], IsSelected
- CView [MFC], OnDragEnter
- CView [MFC], OnDragLeave
- CView [MFC], OnDragOver
- CView [MFC], OnDragScroll
- CView [MFC], OnDrop
- CView [MFC], OnDropEx
- CView [MFC], OnInitialUpdate
- CView [MFC], OnPrepareDC
- CView [MFC], OnScroll
- CView [MFC], OnScrollBy
- CView [MFC], OnActivateFrame
- CView [MFC], OnActivateView
- CView [MFC], OnBeginPrinting
- CView [MFC], OnDraw
- CView [MFC], OnEndPrinting
- CView [MFC], OnEndPrintPreview
- CView [MFC], OnPreparePrinting
- CView [MFC], OnPrint
- CView [MFC], OnUpdate
ms.assetid: 9cff3c56-7564-416b-b9a4-71a9254ed755
ms.openlocfilehash: 763e36b0736ce588e7e2aded25e50347f9e0ca70
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373205"
---
# <a name="cview-class"></a>Třída CView

Poskytuje základní funkce pro uživatelem definované třídy zobrazení.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE CView : public CWnd
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CView::CView](#cview)|Vytvoří `CView` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CView::DoPreparePrinting](#doprepareprinting)|Zobrazí tiskové dialogové okno a vytvoří kontext zařízení tiskárny; volání při přepsání `OnPreparePrinting` členské funkce.|
|[CView::GetDocument](#getdocument)|Vrátí dokument přidružený k zobrazení.|
|[CView::Jevybráno](#isselected)|Testuje, zda je vybrána položka dokumentu. Požadováno pro podporu OLE.|
|[CView::OnDragEnter](#ondragenter)|Nazývá se při prvním přetažení položky do oblasti přetažení zobrazení.|
|[CView::OnDragLeave](#ondragleave)|Nazývá se, když přetažená položka opustí oblast přetažení zobrazení.|
|[CView::OnDragover](#ondragover)|Nazývá se, když je položka přetažena přes oblast přetažení zobrazení.|
|[cview::OnDragScroll](#ondragscroll)|Volána k určení, zda je kurzor přetažen do oblasti posouvání okna.|
|[CView::OnDrop](#ondrop)|Nazývá se, když byla položka vynechána do oblasti přetažení zobrazení, výchozí obslužná rutina.|
|[CView::OnDropEx](#ondropex)|Nazývá se, když byla položka vynechána do oblasti přetažení zobrazení, primární obslužné rutiny.|
|[CView::OnInitialUpdate](#oninitialupdate)|Volána po zobrazení je nejprve připojen k dokumentu.|
|[CView::OnPrepareDC](#onpreparedc)|Volána `OnDraw` před členské funkce je volána pro zobrazení na obrazovce nebo `OnPrint` členská funkce je volána pro tisk nebo tisk náhledu.|
|[CView::OnScroll](#onscroll)|Nazývá se při ole položky jsou přetaženy za hranice zobrazení.|
|[CView::OnScrollBy](#onscrollby)|Nazývá se při posouvání zobrazení obsahujícího aktivní položky OLE na místě.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[cview::OnActivateFrame](#onactivateframe)|Volána při aktivaci nebo deaktivaci okna rámce obsahujícího zobrazení.|
|[CView::Zobrazení OnActivateView](#onactivateview)|Volána při aktivaci zobrazení.|
|[CView::OnBeginPrinting](#onbeginprinting)|Nazývá se při zahájení tiskové úlohy; přepsání pro přidělení prostředků rozhraní grafického zařízení (GDI).|
|[CView::Ondraw](#ondraw)|Nazývá se vykreslení obrázku dokumentu pro zobrazení obrazovky, tisk nebo náhled tisku. Implementace je nutná.|
|[cview::OnendPrinting](#onendprinting)|Nazývá se, když končí tisková úloha; přepsání navrátit prostředky GDI.|
|[CView::OnEndPrintPreview](#onendprintpreview)|Nazývá se při ukončení režimu náhledu.|
|[cview::OnPreparePrinting](#onprepareprinting)|Volána před tiskem dokumentu nebo náhledem; přepsání pro inicializaci tiskového dialogového okna.|
|[CView::OnPrint](#onprint)|Nazývá se tisk nebo náhled stránky dokumentu.|
|[CView::OnUpdate](#onupdate)|Volána upozornit zobrazení, že jeho dokument byl změněn.|

## <a name="remarks"></a>Poznámky

Zobrazení je připojeno k dokumentu a funguje jako prostředník mezi dokumentem a uživatelem: zobrazení vykreslí obrázek dokumentu na obrazovce nebo tiskárně a interpretuje vstup uživatele jako operace na dokumentu.

Pohled je podřízený majek rámokna. Okno rámce může sdílet více než jedno zobrazení, jako v případě okna rozdělovače. Vztah mezi třídou zobrazení, třídou okna rámce a třídou dokumentu je vytvořen objektem. `CDocTemplate` Když uživatel otevře nové okno nebo rozdělí existující, rozhraní framework vytvoří nové zobrazení a připojí jej k dokumentu.

Zobrazení lze připojit pouze k jednomu dokumentu, ale dokument může mít více zobrazení připojených k němu najednou , například pokud je dokument zobrazen v okně rozdělovače nebo ve více podřízených oknech v aplikaci rozhraní více dokumentů (MDI). Aplikace může podporovat různé typy zobrazení pro daný typ dokumentu; Textový editor může například poskytnout úplné textové zobrazení dokumentu i zobrazení osnovy, které zobrazuje pouze nadpisy oddílů. Tyto různé typy pohledů lze umístit do samostatných oken rámečků nebo do samostatných oken jednoho rámečku, pokud používáte okno rozdělovače.

Zobrazení může být zodpovědné za zpracování několika různých typů vstupů, jako je například vstup z klávesnice, vstup myši nebo vstup pomocí přetažení, stejně jako příkazy z nabídek, panelů nástrojů nebo posuvníků. Zobrazení přijímá příkazy předávané oknem rámce. Pokud zobrazení nezpracovává daný příkaz, předá příkaz do přidruženého dokumentu. Stejně jako všechny cíle příkazu, zobrazení zpracovává zprávy prostřednictvím mapy zpráv.

Zobrazení je zodpovědné za zobrazení a úpravu dat dokumentu, ale ne za jejich uložení. Dokument poskytuje zobrazení potřebné podrobnosti o jeho datech. Můžete ponechat zobrazení přístup k datovým členům dokumentu přímo, nebo můžete poskytnout členské funkce ve třídě dokumentu pro volání třídy zobrazení.

Při změně dat dokumentu zobrazení odpovědné za změny obvykle volá [CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) funkce pro dokument, který upozorní všechna `OnUpdate` ostatní zobrazení voláním členské funkce pro každý. Výchozí implementace `OnUpdate` zruší platnost celé klientské oblasti zobrazení. Můžete přepsat zrušit platnost pouze ty oblasti klientské oblasti, které mapují na upravené části dokumentu.

Chcete-li použít `CView`, odvodit třídu z něj a implementovat `OnDraw` členské funkce k provedení zobrazení na obrazovce. Můžete také `OnDraw` použít k provedení tisku a náhledu. Rozhraní framework zpracovává tiskovou smyčku pro tisk a náhled dokumentu.

Zobrazení zpracovává zprávy posuvníku s funkcemi členů [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) a [CWnd::OnVScroll.](../../mfc/reference/cwnd-class.md#onvscroll) Můžete implementovat zpracování zpráv posuvníku v těchto `CView` funkcích nebo můžete použít odvozené třídy [CScrollView](../../mfc/reference/cscrollview-class.md) pro zpracování posouvání za vás.

Kromě `CScrollView`toho knihovna tříd Microsoft Foundation poskytuje `CView`devět dalších tříd odvozených z :

- [CCtrlView](../../mfc/reference/cctrlview-class.md), zobrazení, které umožňuje použití dokumentu - zobrazení architektury se stromem, seznam a bohaté ovládací prvky pro úpravy.

- [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md), zobrazení, které zobrazuje záznamy databáze v ovládacích prvcích dialogového okna.

- [CEditView](../../mfc/reference/ceditview-class.md), zobrazení, které poskytuje jednoduchý víceřádkový textový editor. `CEditView` Objekt můžete použít jako ovládací prvek v dialogovém okně i jako pohled na dokument.

- [CFormView](../../mfc/reference/cformview-class.md), posuvné zobrazení, které obsahuje ovládací prvky dialogového okna a je založeno na prostředku šablony dialogu.

- [CListView](../../mfc/reference/clistview-class.md), zobrazení, které umožňuje použití dokumentu - zobrazení architektury s ovládacími prvky seznamu.

- [CRecordView](../../mfc/reference/crecordview-class.md), zobrazení, které zobrazuje záznamy databáze v ovládacích prvcích dialogového okna.

- [CRichEditView](../../mfc/reference/cricheditview-class.md), zobrazení, které umožňuje použití dokumentu - zobrazit architekturu s bohatými ovládacími prvky pro úpravy.

- [CScrollView](../../mfc/reference/cscrollview-class.md), zobrazení, které automaticky poskytuje podporu posouvání.

- [CTreeView](../../mfc/reference/ctreeview-class.md), zobrazení, které umožňuje použití dokumentu - zobrazení architektury s ovládacími prvky stromu.

Třída `CView` má také odvozené třídy implementace s názvem `CPreviewView`, který se používá v rámci k provedení náhledu tisku. Tato třída poskytuje podporu pro funkce jedinečné pro okno náhledu tisku, jako je například panel nástrojů, jednostránkový nebo dvoustránkový náhled a přiblížení, to znamená zvětšení náhledu obrazu. Není nutné volat nebo přepisovat některou z `CPreviewView`členských funkcí aplikace , pokud nechcete implementovat vlastní rozhraní pro náhled (například pokud chcete podporovat úpravy v režimu náhledu tisku). Další informace o `CView`použití naleznete v [tématu Document/View Architecture](../../mfc/document-view-architecture.md) and [Printing](../../mfc/printing.md). Další podrobnosti o přizpůsobení náhledu tisku naleznete v [technické poznámce 30.](../../mfc/tn030-customizing-printing-and-print-preview.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CView`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="cviewcview"></a><a name="cview"></a>CView::CView

Vytvoří `CView` objekt.

```
CView();
```

### <a name="remarks"></a>Poznámky

Rozhraní framework volá konstruktor při vytvoření nového okna rámce nebo rozdělení okna. Přepište členská funkci [OnInitialUpdate](#oninitialupdate) a inicializujte zobrazení po připojení dokumentu.

## <a name="cviewdoprepareprinting"></a><a name="doprepareprinting"></a>CView::DoPreparePrinting

Volání této funkce z přepsání [OnPreparePrinting](#onprepareprinting) vyvolat tiskové dialogové okno a vytvořit kontext zařízení tiskárny.

```
BOOL DoPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*pInformace*<br/>
Odkazuje na strukturu [CPrintInfo,](../../mfc/reference/cprintinfo-structure.md) která popisuje aktuální tiskovou úlohu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud může začít tisk nebo náhled; 0, pokud byla operace zrušena.

### <a name="remarks"></a>Poznámky

Chování této funkce závisí na tom, zda je volána pro `m_bPreview` tisk nebo tisk náhledu (určeného členem parametru *pInfo).* Pokud se soubor tiskne, tato funkce vyvolá tiskové dialogové okno pomocí hodnot ve struktuře [CPrintInfo,](../../mfc/reference/cprintinfo-structure.md) na které *pInfo* odkazuje; po zavření dialogového okna uživatelem vytvoří funkce kontext zařízení tiskárny na základě nastavení zadaného uživatelem v dialogovém okně a vrátí tento kontext zařízení prostřednictvím parametru *pInfo.* Tento kontext zařízení se používá k tisku dokumentu.

Pokud je soubor zobrazen v náhledu, vytvoří tato funkce kontext zařízení tiskárny pomocí aktuálního nastavení tiskárny; tento kontext zařízení se používá k simulaci tiskárny během náhledu.

## <a name="cviewgetdocument"></a><a name="getdocument"></a>CView::GetDocument

Voláním této funkce získáte ukazatel na dokument zobrazení.

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CDocument](../../mfc/reference/cdocument-class.md) přidružený k zobrazení. Null, pokud zobrazení není připojeno k dokumentu.

### <a name="remarks"></a>Poznámky

To umožňuje volat členské funkce dokumentu.

## <a name="cviewisselected"></a><a name="isselected"></a>CView::Jevybráno

Volat rámci ke kontrole, zda je vybrána zadaná položka dokumentu.

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>Parametry

*pDocItem*<br/>
Odkazuje na testovnou položku dokladu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je vybrána zadaná položka dokumentu; jinak 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce vrátí hodnotu NEPRAVDA. Přepsat tuto funkci, pokud implementujete výběr pomocí [CDocItem](../../mfc/reference/cdocitem-class.md) objekty. Pokud zobrazení obsahuje položky OLE, je nutné tuto funkci přepsat.

## <a name="cviewonactivateframe"></a><a name="onactivateframe"></a>cview::OnActivateFrame

Volat rámci při okno rámce obsahující zobrazení je aktivován nebo deaktivován.

```
virtual void OnActivateFrame(
    UINT nState,
    CFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>Parametry

*nStát*<br/>
Určuje, zda je okno rámce aktivováno nebo deaktivováno. Může to být jedna z následujících hodnot:

- WA_INACTIVE Okno rámce se deaktivuje.

- WA_ACTIVE Okno rámce je aktivováno jinou metodou než kliknutím myši (například pomocí rozhraní klávesnice pro výběr okna).

- WA_CLICKACTIVE Okno rámce je aktivováno kliknutím myši

*pFrameWnd*<br/>
Ukazatel na okno rámce, které má být aktivováno.

### <a name="remarks"></a>Poznámky

Přepište tuto členovou funkci, pokud chcete provést speciální zpracování, když je okno rámce přidružené k zobrazení aktivováno nebo deaktivováno. [Například CFormView](../../mfc/reference/cformview-class.md) provede toto přepsání při uložení a obnovení ovládacího prvku, který má fokus.

## <a name="cviewonactivateview"></a><a name="onactivateview"></a>CView::Zobrazení OnActivateView

Volat rámci při aktivaci zobrazení nebo deaktivovat.

```
virtual void OnActivateView(
    BOOL bActivate,
    CView* pActivateView,
    CView* pDeactiveView);
```

### <a name="parameters"></a>Parametry

*bAktivovat*<br/>
Označuje, zda je zobrazení aktivováno nebo deaktivováno.

*pActivateView*<br/>
Odkazuje na objekt zobrazení, který je aktivován.

*pDeactiveView*<br/>
Odkazuje na objekt zobrazení, který je deaktivován.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce nastaví fokus na aktivované zobrazení. Tuto funkci přepište, pokud chcete provést speciální zpracování, když je zobrazení aktivováno nebo deaktivováno. Chcete-li například poskytnout speciální vizuální podněty, které odlišují aktivní pohled od neaktivních pohledů, zkontrolujte parametr *bActivate* a odpovídajícím způsobem aktualizujte vzhled zobrazení.

Parametry *pActivateView* a *pDeactiveView* odkazují na stejné zobrazení, pokud je aktivováno okno hlavního rámce aplikace bez evidenčního zobrazení – například pokud je fokus přenášen z jiné aplikace do této, nikoli z jednoho zobrazení do druhého v rámci aplikace nebo při přepínání mezi podřízenými okny MDI. To umožňuje zobrazení re-realizovat jeho paletu, v případě potřeby.

Tyto parametry se liší při [CFrameWnd::SetActiveView](../../mfc/reference/cframewnd-class.md#setactiveview) je volána s zobrazením, které se liší od co [CFrameWnd::GetActiveView](../../mfc/reference/cframewnd-class.md#getactiveview) vrátí. To se nejčastěji děje s rozdělovačem oken.

## <a name="cviewonbeginprinting"></a><a name="onbeginprinting"></a>CView::OnBeginPrinting

Volat rámci na začátku tiskové nebo tiskové úlohy náhledu, po `OnPreparePrinting` byla volána.

```
virtual void OnBeginPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Odkazuje na kontext zařízení tiskárny.

*pInformace*<br/>
Odkazuje na strukturu [CPrintInfo,](../../mfc/reference/cprintinfo-structure.md) která popisuje aktuální tiskovou úlohu.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce neprovede žádné provádění. Přepsat tuto funkci přidělit všechny prostředky GDI, jako jsou pera nebo písma, potřebné speciálně pro tisk. Vyberte objekty GDI do kontextu zařízení z členské funkce [OnPrint](#onprint) pro každou stránku, která je používá. Pokud používáte stejný objekt zobrazení k provedení zobrazení obrazovky i tisku, použijte samostatné proměnné pro prostředky GDI potřebné pro každé zobrazení; to vám umožní aktualizovat obrazovku během tisku.

Tuto funkci můžete také použít k provádění inicializace, které závisí na vlastnostech kontextu zařízení tiskárny. Například počet stránek potřebných k tisku dokumentu může záviset na nastavení, které uživatel zadal v tiskovém dialogovém okně (například délka stránky). V takovém případě nelze zadat délku dokumentu v členské funkci [OnPreparePrinting,](#onprepareprinting) kde byste to normálně udělali; musíte počkat, až bude vytvořen kontext zařízení tiskárny na základě nastavení dialogového okna. [OnBeginPrinting](#onbeginprinting) je první overridable funkce, která umožňuje přístup k [cdc](../../mfc/reference/cdc-class.md) objekt představující kontext zařízení tiskárny, takže můžete nastavit délku dokumentu z této funkce. Všimněte si, že pokud délka dokumentu není určena do této doby, posuvník se nezobrazí během náhledu.

## <a name="cviewondragenter"></a><a name="ondragenter"></a>CView::OnDragEnter

Volat rámci při prvním přechodu myši bez posouvání oblasti cílové okno přetažení.

```
virtual DROPEFFECT OnDragEnter(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*objekt pDataObject*<br/>
Odkazuje na [COleDataObject](../../mfc/reference/coledataobject-class.md) přetahované do oblasti přetažení zobrazení.

*dwKeyState*<br/>
Obsahuje stav modifikačních klíčů. Jedná se o kombinaci libovolného počtu: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON a MK_RBUTTON.

*Bod*<br/>
Aktuální pozice myši vzhledem k oblasti klienta zobrazení.

### <a name="return-value"></a>Návratová hodnota

Hodnota z dropeffect výčtu typu, který označuje typ přetažení, které by došlo, pokud uživatel vynechal objekt na této pozici. Typ poklesu obvykle závisí na aktuálním stavu klíče označeném *dwKeyState*. Standardní mapování keystates na hodnoty DROPEFFECT je:

- DROPEFFECT_NONE Datový objekt nelze v tomto okně vynechat.

- DROPEFFECT_LINK pro MK_CONTROL &#124; MK_SHIFT Vytvoří propojení mezi objektem a jeho serverem.

- DROPEFFECT_COPY pro MK_CONTROL Vytvoří kopii vynechaného objektu.

- DROPEFFECT_MOVE pro MK_ALT Vytvoří kopii vynechaného objektu a odstraní původní objekt. Toto je obvykle výchozí efekt přetažení, pokud zobrazení může přijmout tento datový objekt.

Další informace naleznete v knihovně MFC Advanced Concepts ukázkové [OCLIENT](../../overview/visual-cpp-samples.md).

### <a name="remarks"></a>Poznámky

Výchozí implementace je nedělat nic a vrátit DROPEFFECT_NONE.

Přepsat tuto funkci připravit pro budoucí volání [onDragOver](#ondragover) členské funkce. Všechna data požadovaná z datového objektu by měla `OnDragOver` být načtena v tomto okamžiku pro pozdější použití v členské funkci. Zobrazení by měla být také aktualizována v tomto okamžiku poskytnout uživateli vizuální zpětnou vazbu. Další informace naleznete v článku [OLE přetažení: Implementovat cíl přetažení](../../mfc/drag-and-drop-ole.md#implement-a-drop-target).

## <a name="cviewondragleave"></a><a name="ondragleave"></a>CView::OnDragLeave

Volat rámci během operace přetažení při přesunutí myši z platné oblasti přetažení pro toto okno.

```
virtual void OnDragLeave();
```

### <a name="remarks"></a>Poznámky

Přepsat tuto funkci, pokud aktuální zobrazení potřebuje vyčistit všechny akce provedené během [OnDragEnter](#ondragenter) nebo [OnDragOver](#ondragover) volání, jako je například odebrání jakékoli vizuální zpětné vazby od uživatelů, zatímco objekt byl přetažen a vynechán.

## <a name="cviewondragover"></a><a name="ondragover"></a>CView::OnDragover

Volat rámci během operace přetažení při přesunutí myši přes cílové okno přetažení.

```
virtual DROPEFFECT OnDragOver(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*objekt pDataObject*<br/>
Odkazuje na [COleDataObject](../../mfc/reference/coledataobject-class.md) přetahované přes cíl přetažení.

*dwKeyState*<br/>
Obsahuje stav modifikačních klíčů. Jedná se o kombinaci libovolného počtu: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON a MK_RBUTTON.

*Bod*<br/>
Aktuální pozice myši vzhledem k oblasti klienta zobrazení.

### <a name="return-value"></a>Návratová hodnota

Hodnota z dropeffect výčtu typu, který označuje typ přetažení, které by došlo, pokud uživatel vynechal objekt na této pozici. Typ poklesu často závisí na aktuálním stavu klíče, jak je uvedeno *dwKeyState*. Standardní mapování keystates na hodnoty DROPEFFECT je:

- DROPEFFECT_NONE Datový objekt nelze v tomto okně vynechat.

- DROPEFFECT_LINK pro MK_CONTROL &#124; MK_SHIFT Vytvoří propojení mezi objektem a jeho serverem.

- DROPEFFECT_COPY pro MK_CONTROL Vytvoří kopii vynechaného objektu.

- DROPEFFECT_MOVE pro MK_ALT Vytvoří kopii vynechaného objektu a odstraní původní objekt. Obvykle se jedná o výchozí efekt přetažení, kdy zobrazení může přijmout datový objekt.

Další informace naleznete v knihovně MFC Advanced Concepts ukázkové [OCLIENT](../../overview/visual-cpp-samples.md).

### <a name="remarks"></a>Poznámky

Výchozí implementace je neprovádět žádné a vrátit DROPEFFECT_NONE.

Přepsat tuto funkci poskytnout uživateli vizuální zpětnou vazbu během operace přetažení. Vzhledem k tomu, že tato funkce je volána nepřetržitě, jakýkoli kód obsažený v něm by měl být optimalizován co nejvíce. Další informace naleznete v článku [OLE přetažení: Implementovat cíl přetažení](../../mfc/drag-and-drop-ole.md#implement-a-drop-target).

## <a name="cviewondragscroll"></a><a name="ondragscroll"></a>cview::OnDragScroll

Volat rámci před voláním [OnDragEnter](#ondragenter) nebo [OnDragOver](#ondragover) k určení, zda je bod v oblasti posouvání.

```
virtual DROPEFFECT OnDragScroll(
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*dwKeyState*<br/>
Obsahuje stav modifikačních klíčů. Jedná se o kombinaci libovolného počtu: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON a MK_RBUTTON.

*Bod*<br/>
Obsahuje umístění kurzoru v obrazových bodech vzhledem k obrazovce.

### <a name="return-value"></a>Návratová hodnota

Hodnota z dropeffect výčtu typu, který označuje typ přetažení, které by došlo, pokud uživatel vynechal objekt na této pozici. Typ poklesu obvykle závisí na aktuálním stavu klíče označeném *dwKeyState*. Standardní mapování keystates na hodnoty DROPEFFECT je:

- DROPEFFECT_NONE Datový objekt nelze v tomto okně vynechat.

- DROPEFFECT_LINK pro MK_CONTROL &#124; MK_SHIFT Vytvoří propojení mezi objektem a jeho serverem.

- DROPEFFECT_COPY pro MK_CONTROL Vytvoří kopii vynechaného objektu.

- DROPEFFECT_MOVE pro MK_ALT Vytvoří kopii vynechaného objektu a odstraní původní objekt.

- DROPEFFECT_SCROLL Označuje, že se chystá operace přetahování v cílovém zobrazení.

Další informace naleznete v knihovně MFC Advanced Concepts ukázkové [OCLIENT](../../overview/visual-cpp-samples.md).

### <a name="remarks"></a>Poznámky

Přepsat tuto funkci, pokud chcete poskytnout speciální chování pro tuto událost. Výchozí implementace automaticky posouvá okna při přetažení kurzoru do výchozí oblasti posouvání uvnitř ohraničení každého okna. Další informace naleznete v článku [OLE přetažení: Implementovat cíl přetažení](../../mfc/drag-and-drop-ole.md#implement-a-drop-target).

## <a name="cviewondraw"></a><a name="ondraw"></a>CView::Ondraw

Volat rámci k vykreslení obrázku dokumentu.

```
virtual void OnDraw(CDC* pDC) = 0;
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Odkazuje na kontext zařízení, který se má použít k vykreslení obrazu dokumentu.

### <a name="remarks"></a>Poznámky

Framework volá tuto funkci k provedení zobrazení obrazovky, tisku a náhledu tisku a v každém případě předá jiný kontext zařízení. Neexistuje žádná výchozí implementace.

Chcete-li zobrazit zobrazení dokumentu, musíte tuto funkci přepsat. Můžete provést volání rozhraní grafického zařízení (GDI) pomocí objektu [CDC,](../../mfc/reference/cdc-class.md) na který je odkazováno parametrem *pDC.* Před kreslením můžete do kontextu zařízení vybrat prostředky GDI, například pera nebo písma, a pak je potom odznačit. Často může být váš kreslicí kód nezávislý na zařízení; to znamená, že nevyžaduje informace o tom, jaký typ zařízení zobrazuje obrázek.

Chcete-li optimalizovat kreslení, volání [RectVisible](../../mfc/reference/cdc-class.md#rectvisible) členská funkce kontextu zařízení zjistit, zda daný obdélník bude nakreslena. Pokud potřebujete rozlišovat mezi normálním zobrazením obrazovky a tiskem, zavolejte členskou funkci [IsPrinting](../../mfc/reference/cdc-class.md#isprinting) v kontextu zařízení.

## <a name="cviewondrop"></a><a name="ondrop"></a>CView::OnDrop

Volat rámci při uživatel uvolní datový objekt přes platný cíl přetažení.

```
virtual BOOL OnDrop(
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>Parametry

'pDataObject* Odkazuje na [COleDataObject,](../../mfc/reference/coledataobject-class.md) který je vynechán do cíle přetažení.

*efekt přetažení*<br/>
Efekt přetažení, který uživatel požadoval.

- DROPEFFECT_COPY Vytvoří kopii datového objektu, který je vynechán.

- DROPEFFECT_MOVE Přesune datový objekt do aktuálního umístění myši.

- DROPEFFECT_LINK Vytvoří propojení mezi datovým objektem a jeho serverem.

*Bod*<br/>
Aktuální pozice myši vzhledem k oblasti klienta zobrazení.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl pokles úspěšný; jinak 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace neprovede žádné funkce a vrátí hodnotu FALSE.

Přepsat tuto funkci implementovat efekt ole přetažení do klientské oblasti zobrazení. Datový objekt lze zkontrolován pomocí *pDataObject* pro datové formáty schránky a data vynechaná v určeném bodě.

> [!NOTE]
> Rozhraní Framework nevolá tuto funkci, pokud je přepsání [OnDropEx](#ondropex) v tomto zobrazení třídy.

## <a name="cviewondropex"></a><a name="ondropex"></a>CView::OnDropEx

Volat rámci při uživatel uvolní datový objekt přes platný cíl přetažení.

```
virtual DROPEFFECT OnDropEx(
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*objekt pDataObject*<br/>
Odkazuje na [COleDataObject,](../../mfc/reference/coledataobject-class.md) který je vynechán do cíle přetažení.

*přetaženíVýchozí*<br/>
Efekt, který uživatel zvolil pro výchozí operaci přetažení na základě aktuálního stavu klíče. Může to být DROPEFFECT_NONE. Efekty přetažení jsou popsány v části Poznámky.

*dropList*<br/>
Seznam efektů přetažení, které podporuje zdroj přetažení. Hodnoty efektu přetažení lze kombinovat pomocí bitové operace OR ( **&#124;). ** Efekty přetažení jsou popsány v části Poznámky.

*Bod*<br/>
Aktuální pozice myši vzhledem k oblasti klienta zobrazení.

### <a name="return-value"></a>Návratová hodnota

Efekt přetažení, který byl výsledkem pokusu o přetažení v umístění určeném *bodem*. To musí být jedna z hodnot označených *dropEffectList*. Efekty přetažení jsou popsány v části Poznámky.

### <a name="remarks"></a>Poznámky

Výchozí implementace je neprovádět žádné a vrátit fiktivní hodnotu ( -1 ) označující, že rozhraní by měl volat [onDrop](#ondrop) obslužné rutiny.

Přepsat tuto funkci implementovat efekt pravé ho tlačítka myši přetažení. Pravé tlačítko myši přetažení obvykle zobrazí nabídku voleb při uvolnění pravého tlačítka myši.

Přepsání `OnDropEx` by měl dotaz na pravé tlačítko myši. Můžete volat [GetKeyState](/windows/win32/api/winuser/nf-winuser-getkeystate) nebo uložit správný stav tlačítka myši z obslužné rutiny [OnDragEnter.](#ondragenter)

- Pokud je pravé tlačítko myši vypnuto, přepsání by mělo zobrazit vyskakovací nabídku, která nabízí podporu drop efektů zdrojem přetažení.

  - Zkontrolujte *dropList* k určení efekty přetažení podporované zdroj přetažení. V místní nabídce povolte pouze tyto akce.

  - Pomocí [funkce SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem) nastavte výchozí akci založenou na *přetažení Výchozí*.

  - Nakonec provádějte akci označenou výběrem uživatele z místní nabídky.

- Pokud pravé tlačítko myši není dolů, přepsání by měl zpracovat jako standardní požadavek přetažení. Použijte efekt přetažení zadaný v *poli i9.* Alternativně přepsání může vrátit fiktivní hodnotu ( -1 ) k označení, že `OnDrop` bude zpracovávat tuto operaci přetažení.

Pomocí `COleDataObject` *objektu pDataObject* zkontrolujte formát dat schránky a data vzadaném bodě.

Efekty přetažení popisují akci přidruženou k operaci přetažení. Podívejte se na následující seznam efektů přetažení:

- DROPEFFECT_NONE Kapka by nebyla povolena.

- DROPEFFECT_COPY Bude provedena operace kopírování.

- DROPEFFECT_MOVE Bude provedena operace přesunutí.

- DROPEFFECT_LINK Bylo by vytvořeno propojení z vynechaná data s původními daty.

- DROPEFFECT_SCROLL Označuje, že operace přetahování se chystá dojít nebo dochází v cíli.

Další informace o nastavení výchozího příkazu nabídky naleznete v [tématu SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem) v nabídce Windows SDK a [CMenu::GetSafeHmenu](../../mfc/reference/cmenu-class.md#getsafehmenu) v tomto svazku.

## <a name="cviewonendprinting"></a><a name="onendprinting"></a>cview::OnendPrinting

Volat rámci po dokumentu byl vytištěn nebo náhled.

```
virtual void OnEndPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Odkazuje na kontext zařízení tiskárny.

*pInformace*<br/>
Odkazuje na strukturu [CPrintInfo,](../../mfc/reference/cprintinfo-structure.md) která popisuje aktuální tiskovou úlohu.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce neprovede žádné provádění. Přepsáním této funkce uvolníte všechny prostředky GDI přidělené v členské funkci [OnBeginPrinting.](#onbeginprinting)

## <a name="cviewonendprintpreview"></a><a name="onendprintpreview"></a>CView::OnEndPrintPreview

Volat rámci při uživatel ukončí režim náhledu tisku.

```
virtual void OnEndPrintPreview(
    CDC* pDC,
    CPrintInfo* pInfo,
    POINT point,
    CPreviewView* pView);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Odkazuje na kontext zařízení tiskárny.

*pInformace*<br/>
Odkazuje na strukturu [CPrintInfo,](../../mfc/reference/cprintinfo-structure.md) která popisuje aktuální tiskovou úlohu.

*Bod*<br/>
Určuje bod na stránce, který byl naposledy zobrazen v režimu náhledu.

*pZobrazit*<br/>
Odkazuje na objekt pohledu použitý pro náhled.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce volá členskou funkci [OnEndPrinting](#onendprinting) a obnoví okno hlavního rámce do stavu, ve které se nachází před zahájením náhledu tisku. Přepište tuto funkci a proveďte speciální zpracování při ukončení režimu náhledu. Chcete-li například zachovat pozici uživatele v dokumentu při přepnutí z režimu náhledu do normálního režimu zobrazení, `m_nCurPage` můžete `CPrintInfo` přejít na pozici popsanou parametrem *bodu* a členem struktury, na kterou parametr *pInfo* odkazuje.

Vždy volat verzi základní `OnEndPrintPreview` třídy z přepsání, obvykle na konci funkce.

## <a name="cviewoninitialupdate"></a><a name="oninitialupdate"></a>CView::OnInitialUpdate

Volat rámci po zobrazení je nejprve připojen k dokumentu, ale před zobrazení je zpočátku zobrazena.

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce volá členská funkci [OnUpdate](#onupdate) bez informací nápovědy (to znamená použití výchozích hodnot 0 pro parametr *lHint* a NULL pro parametr *pHint).* Přepište tuto funkci a proveďte jednorázovou inicializaci, která vyžaduje informace o dokumentu. Pokud má například aplikace dokumenty pevné velikosti, můžete pomocí této funkce inicializovat omezení posouvání zobrazení na základě velikosti dokumentu. Pokud vaše aplikace podporuje dokumenty s proměnnou velikosti, použijte [OnUpdate](#onupdate) aktualizovat omezení posouvání pokaždé, když se změní dokument.

## <a name="cviewonpreparedc"></a><a name="onpreparedc"></a>CView::OnPrepareDC

Volat rámci před [OnDraw](#ondraw) členské funkce je volána pro zobrazení na obrazovce a před [OnPrint](#onprint) členská funkce je volána pro každou stránku během tisku nebo náhledu.

```
virtual void OnPrepareDC(
    CDC* pDC,
    CPrintInfo* pInfo = NULL);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Odkazuje na kontext zařízení, který se má použít k vykreslení obrazu dokumentu.

*pInformace*<br/>
Odkazuje na strukturu [CPrintInfo,](../../mfc/reference/cprintinfo-structure.md) která popisuje `OnPrepareDC` aktuální tiskovou úlohu, pokud je volána pro tisk nebo tisk náhledu; `m_nCurPage` člen určí stránku, která má být vytištěna. Tento parametr je `OnPrepareDC` null, pokud je volána pro zobrazení na obrazovce.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce neprovede žádné provádění, pokud je funkce volána pro zobrazení na obrazovce. Tato funkce je však přepsána v odvozených třídách, například [CScrollView](../../mfc/reference/cscrollview-class.md), chcete-li upravit atributy kontextu zařízení; v důsledku toho byste měli vždy volat implementaci základní třídy na začátku přepsání.

Pokud je funkce volána k tisku, výchozí implementace zkontroluje informace o stránce uložené v parametru *pInfo.* Pokud délka dokumentu nebyla zadána, předpokládá, `OnPrepareDC` že dokument je o délce jedné stránky a zastaví tiskovou smyčku po vytištění jedné stránky. Funkce zastaví tiskovou smyčku nastavením `m_bContinuePrinting` člena struktury na HODNOTU NEPRAVDA.

Přepis `OnPrepareDC` z některého z následujících důvodů:

- Chcete-li upravit atributy kontextu zařízení podle potřeby pro zadanou stránku. Například pokud potřebujete nastavit režim mapování nebo jiné charakteristiky kontextu zařízení, učiňte tak v této funkci.

- Chcete-li provést stránkování v době tisku. Obvykle určíte délku dokumentu při zahájení tisku pomocí členské funkce [OnPreparePrinting.](#onprepareprinting) Pokud však předem nevíte, jak dlouhý je dokument (například při tisku neurčeného počtu `OnPrepareDC` záznamů z databáze), přepište a otestujte konec dokumentu během jeho tisku. Pokud již není k dispozici dokument, který `m_bContinuePrinting` má být `CPrintInfo` vytištěn, nastavte člen struktury na HODNOTU NEPRAVDA.

- Odeslání únikových kódů do tiskárny po stránce. Chcete-li odeslat únikové kódy z `OnPrepareDC`, volejte `Escape` členní funkci parametru *pDC.*

Volání verze základní `OnPrepareDC` třídy na začátku přepsání.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#183](../../mfc/codesnippet/cpp/cview-class_1.cpp)]

## <a name="cviewonprepareprinting"></a><a name="onprepareprinting"></a>cview::OnPreparePrinting

Volat rámci před dokument je vytištěn nebo náhled.

```
virtual BOOL OnPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*pInformace*<br/>
Odkazuje na strukturu [CPrintInfo,](../../mfc/reference/cprintinfo-structure.md) která popisuje aktuální tiskovou úlohu.

### <a name="return-value"></a>Návratová hodnota

Nenulová pro zahájení tisku; 0, pokud byla tisková úloha zrušena.

### <a name="remarks"></a>Poznámky

Výchozí implementace neprovede žádné provádění.

Chcete-li povolit náhled tisku a tisku, musíte tuto funkci přepsat. Zavolejte členskou funkci [DoPreparePrinting,](#doprepareprinting) předavejte jí parametr *pInfo* a pak vraťte její vrácenou hodnotu. `DoPreparePrinting` zobrazí tiskové dialogové okno a vytvoří kontext zařízení tiskárny. Pokud chcete inicializovat tiskové dialogové okno s jinými než výchozími hodnotami, přiřaďte hodnoty členům *aplikace pInfo*. Například pokud znáte délku dokumentu, předejte hodnotu [SetMaxPage](../../mfc/reference/cprintinfo-structure.md#setmaxpage) členské funkce `DoPreparePrinting` *pInfo* před voláním . Tato hodnota se zobrazí v poli Do: v části Rozsah tiskového dialogového okna.

`DoPreparePrinting`nezobrazí tiskové dialogové okno pro úlohu náhledu. Pokud chcete obejít tiskové dialogové okno pro tiskovou `m_bPreview` úlohu, zkontrolujte, zda je člen *pInfo* FALSE, a před předáním do něj nastavte hodnotu `DoPreparePrinting`TRUE . poté obnovit hodnotu FALSE.

Pokud potřebujete provést inicializace, které `CDC` vyžadují přístup k objektu představujícíkontext zařízení tiskárny (například pokud potřebujete znát velikost stránky `OnBeginPrinting` před určením délky dokumentu), přepište členskou funkci.

Pokud chcete nastavit hodnotu `m_nNumPreviewPages` nebo `m_strPageDesc` členy *parametru pInfo,* učiňte tak po volání `DoPreparePrinting`. Členská `DoPreparePrinting` funkce `m_nNumPreviewPages` nastaví hodnotu nalezenou v aplikaci . INI a `m_strPageDesc` nastaví na výchozí hodnotu.

### <a name="example"></a>Příklad

  Přepište `OnPreparePrinting` a `DoPreparePrinting` volejte z přepsání tak, aby se v rámci zobrazilo tiskové dialogové okno a vytvořilo řadič domény tiskárny.

[!code-cpp[NVC_MFCDocView#184](../../mfc/codesnippet/cpp/cview-class_2.cpp)]

Pokud víte, kolik stránek dokument obsahuje, nastavte `OnPreparePrinting` před `DoPreparePrinting`voláním maximální počet stránek . V rámci se zobrazí maximální číslo stránky v poli "do" tiskového dialogového okna.

[!code-cpp[NVC_MFCDocView#185](../../mfc/codesnippet/cpp/cview-class_3.cpp)]

## <a name="cviewonprint"></a><a name="onprint"></a>CView::OnPrint

Volat rámci vytisknout nebo zobrazit náhled stránky dokumentu.

```
virtual void OnPrint(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Odkazuje na kontext zařízení tiskárny.

*pInformace*<br/>
Odkazuje na `CPrintInfo` strukturu, která popisuje aktuální tiskovou úlohu.

### <a name="remarks"></a>Poznámky

Pro každou stránku, která je vytištěna, framework volá tuto funkci ihned po volání členské funkce [OnPrepareDC.](#onpreparedc) Stránka, na kterou se `m_nCurPage` tiská, je určena členem struktury [CPrintInfo,](../../mfc/reference/cprintinfo-structure.md) na kterou *odkazuje pInfo.* Výchozí implementace volá členská funkce [OnDraw](#ondraw) a předá ji kontextu zařízení tiskárny.

Přepsat tuto funkci z některého z následujících důvodů:

- Povolení tisku vícestránkových dokumentů. Vykreslení pouze části dokumentu, která odpovídá aktuálně vytištěné stránce. Pokud používáte `OnDraw` k vykreslování, můžete upravit počátek výřezu tak, aby se vytiskla pouze příslušná část dokumentu.

- Chcete-li, aby vytištěný obrázek vypadal jinak než obraz na obrazovce (to znamená, pokud vaše aplikace není WYSIWYG). Místo předání kontextu zařízení `OnDraw`tiskárny aplikaci použijte kontext zařízení k vykreslení obrázku pomocí atributů, které nejsou zobrazeny na obrazovce.

   Pokud potřebujete prostředky GDI pro tisk, které nepoužíváte pro zobrazení na obrazovce, vyberte je před kreslením do kontextu zařízení a odznačte je později. Tyto prostředky GDI by měly být přiděleny v [OnBeginPrinting](#onbeginprinting) a uvolněny v [OnEndPrinting](#onendprinting).

- Chcete-li implementovat záhlaví nebo zápatí. Stále můžete `OnDraw` použít k provedení vykreslování omezením oblasti, na kterou lze tisknout.

Všimněte `m_rectDraw` si, že člen parametru *pInfo* popisuje tisknutelnou oblast stránky v logických jednotkách.

Nevolejte `OnPrepareDC` přepsání `OnPrint`; rozhraní framework `OnPrepareDC` automaticky `OnPrint`volá před voláním .

### <a name="example"></a>Příklad

Následuje kostra pro potlačenou `OnPrint` funkci:

[!code-cpp[NVC_MFCDocView#186](../../mfc/codesnippet/cpp/cview-class_4.cpp)]

Další příklad naleznete v tématu [CRichEditView::PrintInsideRect](../../mfc/reference/cricheditview-class.md#printinsiderect).

## <a name="cviewonscroll"></a><a name="onscroll"></a>CView::OnScroll

Volat rámci k určení, zda posouvání je možné.

```
virtual BOOL OnScroll(
    UINT nScrollCode,
    UINT nPos,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parametry

*nScrollCode*<br/>
Posuvník ový kód, který označuje požadavek uživatele na posouvání. Tento parametr se skládá ze dvou částí: bajtu nízkého řádu, který určuje typ posouvání, ke kterému dochází vodorovně, a bajt vysokého řádu, který určuje typ posouvání, ke kterému dochází svisle:

- SB_BOTTOM posune dolů.

- SB_LINEDOWN posune o řádek dolů.

- SB_LINEUP Posune o řádek nahoru.

- SB_PAGEDOWN posune o jednu stránku dolů.

- SB_PAGEUP Posune o jednu stránku nahoru.

- SB_THUMBTRACK Přetáhne posuvník do určené polohy. Aktuální pozice je zadána v *nPos*.

- SB_TOP posouvá nahoru.

*nPos*<br/>
Obsahuje aktuální pozici posuvníku, pokud je kód posuvníku SB_THUMBTRACK; v opačném případě se nepoužívá. V závislosti na počáteční rozsah posouvání *nPos* může být negativní a by měla být přetypována **na int v** případě potřeby.

*bDoScroll*<br/>
Určuje, zda byste měli skutečně provést zadanou akci posouvání. Pokud true, pak posouvání by mělo probíhat; pokud false, pak by nemělo dojít k posouvání.

### <a name="return-value"></a>Návratová hodnota

Pokud *bDoScroll* je TRUE a zobrazení bylo skutečně posouval, pak vrátit nenulovou; jinak 0. Pokud *bDoScroll* je FALSE, pak vrátí hodnotu, kterou byste vrátili, pokud *bDoScroll* byly TRUE, i když nemáte ve skutečnosti dělat posouvání.

### <a name="remarks"></a>Poznámky

V jednom případě je tato funkce volána frameworkem s *bDoScroll* nastaveným na HODNOTU TRUE, když zobrazení obdrží zprávu s posuvníku. V takovém případě byste měli ve skutečnosti posouvat zobrazení. V druhé případě je tato funkce volána s *bDoScroll* nastavena na FALSE při ole položka je zpočátku přetažena do oblasti automatického posouvání cíl přetažení před posouvání skutečně probíhá. V takovém případě byste ve skutečnosti neměli posouvat zobrazení.

## <a name="cviewonscrollby"></a><a name="onscrollby"></a>CView::OnScrollBy

Volat rámci při zobrazení oblasti mimo současné zobrazení dokumentu, a to buď přetažením položky OLE proti aktuální ohraničení zobrazení nebo manipulací s svislé nebo vodorovné posuvníky.

```
virtual BOOL OnScrollBy(
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parametry

*sizeScroll*<br/>
Počet obrazových bodů posunutých vodorovně a svisle.

*bDoScroll*<br/>
Určuje, zda dojde k posouvání zobrazení. Pokud true, pak posouvání probíhá; pokud false, pak posouvání nedojde.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud bylo možné zobrazení posouvat; jinak 0.

### <a name="remarks"></a>Poznámky

V odvozených třídách tato metoda zkontroluje, zda je zobrazení posuvné ve směru, který uživatel požadoval, a v případě potřeby aktualizuje novou oblast. Tato funkce je automaticky volána [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) a [CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) k provedení skutečného požadavku na posouvání.

Výchozí implementace této metody nezmění zobrazení, ale pokud není volána, zobrazení se `CScrollView`nebude posouvat v odvozené třídě.

Pokud šířka nebo výška dokumentu překročí 32767 pixelů, posouvání `OnScrollBy` kolem 32767 se nezdaří, protože je volána s argumentem neplatný *sizeScroll.*

## <a name="cviewonupdate"></a><a name="onupdate"></a>CView::OnUpdate

Volat rámci po zobrazení dokumentu byla změněna; Tato funkce je volána [CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) a umožňuje zobrazení aktualizovat jeho zobrazení tak, aby odrážely tyto změny.

```
virtual void OnUpdate(
    CView* pSender,
    LPARAM lHint,
    CObject* pHint);
```

### <a name="parameters"></a>Parametry

*pOdesílatelí*<br/>
Odkazuje na zobrazení, které změnilo dokument nebo NULL, pokud mají být aktualizována všechna zobrazení.

*lTip*<br/>
Obsahuje informace o úpravách.

*pHint*<br/>
Odkazuje na objekt ukládající informace o změnách.

### <a name="remarks"></a>Poznámky

Je také volána výchozí implementace [OnInitialUpdate](#oninitialupdate). Výchozí implementace zruší platnost celé oblasti klienta a označí ji pro malování při přijetí další WM_PAINT zprávy. Tuto funkci přepište, pokud chcete aktualizovat pouze oblasti, které mapují na upravené části dokumentu. Chcete-li to provést, musíte předat informace o změnách pomocí parametrů nápovědy.

Chcete-li použít *lHint*, definujte speciální hodnoty nápovědy, obvykle bitovou masku nebo typ výčtu, a nechat dokument předat jednu z těchto hodnot. Chcete-li použít *pHint*, odvodit třídu nápovědy z [CObject](../../mfc/reference/cobject-class.md) a mít dokument předat ukazatel na objekt nápovědy; při přepsání `OnUpdate`použijte člennou funkci [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof) k určení typu run-time objektu nápovědy.

Obvykle byste neměli provádět žádné `OnUpdate`kreslení přímo z aplikace . Místo toho určete obdélník popisující v souřadnicích zařízení oblast, která vyžaduje aktualizaci; předejte tento obdélník [CWnd::InvalidateRect](../../mfc/reference/cwnd-class.md#invalidaterect). To způsobí, že malování dojít při příštím [přijetí WM_PAINT](/windows/win32/gdi/wm-paint) zprávy.

Pokud *lHint* je 0 a *pHint* je NULL, dokument odeslal obecné oznámení o aktualizaci. Pokud zobrazení obdrží obecné oznámení o aktualizaci nebo pokud nemůže dekódovat rady, by mělo zneplatnit celou svou klientskou oblast.

## <a name="see-also"></a>Viz také

[MFC Vzorek MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Třída CFrameWnd](../../mfc/reference/cframewnd-class.md)<br/>
[CSplitterWnd – třída](../../mfc/reference/csplitterwnd-class.md)<br/>
[Třída CDC](../../mfc/reference/cdc-class.md)<br/>
[Třída CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[CDocument – třída](../../mfc/reference/cdocument-class.md)
