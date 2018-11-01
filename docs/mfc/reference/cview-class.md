---
title: CView – třída
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
ms.openlocfilehash: f325423c940df46940d7074c599eb8e502e90586
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50669076"
---
# <a name="cview-class"></a>CView – třída

Poskytuje základní funkce pro třídy zobrazení definované uživatelem.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE CView : public CWnd
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Název|Popis|
|----------|-----------------|
|[CView::CView](#cview)|Vytvoří `CView` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CView::DoPreparePrinting](#doprepareprinting)|Zobrazí dialogové okno Tisk a vytvoří kontext zařízení tiskárny volat metodu, pokud přepsání `OnPreparePrinting` členskou funkci.|
|[CView::GetDocument](#getdocument)|Vrátí dokument přidružený k zobrazení.|
|[CView::IsSelected](#isselected)|Ověřuje, zda je položka dokumentu vybraná. Vyžaduje se pro podporu technologie OLE.|
|[CView::OnDragEnter](#ondragenter)|Volá se, když položka je nejprve přetažen-přetažením oblasti zobrazení.|
|[CView::OnDragLeave](#ondragleave)|Volá se při přetahování myší oblast zobrazení opustí přetaženou položku.|
|[CView::OnDragOver](#ondragover)|Volá se, když položka přesune-přetažením oblasti zobrazení.|
|[CView::OnDragScroll](#ondragscroll)|Voláno k určení, zda je kurzor přetáhnout do oblasti posuvníku okna.|
|[CView::OnDrop](#ondrop)|Volá se, když položka byla vyřazena, do oblasti a přetahování zobrazení, výchozí obslužnou rutinu.|
|[CView::OnDropEx](#ondropex)|Volá se, když položka byla vyřazena, do oblasti a přetahování zobrazení, primární obslužnou rutinu.|
|[CView::OnInitialUpdate](#oninitialupdate)|Volá se po zobrazení je nejprve připojené k dokumentu.|
|[CView::OnPrepareDC](#onpreparedc)|Volá se před `OnDraw` členská funkce je volána pro obrazovku nebo `OnPrint` členská funkce je volána pro tisku nebo náhledu.|
|[CView::OnScroll](#onscroll)|Volá se při přetažení položky OLE přesahuje hranice zobrazení.|
|[CView::OnScrollBy](#onscrollby)|Volá se při posunu zobrazení obsahující aktivní v umístěných položek OLE.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CView::OnActivateFrame](#onactivateframe)|Volá se, když se aktivuje nebo deaktivuje okno rámce obsahující zobrazení.|
|[CView::OnActivateView](#onactivateview)|Volá se, když se aktivuje zobrazení.|
|[CView::OnBeginPrinting](#onbeginprinting)|Volá se, když začne tiskovou úlohu; přepsání nastavení za účelem přidělení grafické prostředky rozhraní GDI systému zařízení.|
|[CView::OnDraw](#ondraw)|Volá se, aby se vykreslil obraz dokumentu pro zobrazení, tisku nebo náhledu tisku. Implementace vyžaduje.|
|[CView::OnEndPrinting](#onendprinting)|Volá se, když tiskové úlohy končí; přepsání za účelem uvolnění prostředků GDI.|
|[CView::OnEndPrintPreview](#onendprintpreview)|Volá se, když se ukončil režim náhledu.|
|[CView::OnPreparePrinting](#onprepareprinting)|Volá se, než se dokument vytiskne nebo zobrazení náhledu; přepsání nastavení za účelem inicializace dialogové okno Tisk.|
|[CView::OnPrint](#onprint)|Volá se, aby tisk nebo náhled stránky z dokumentu.|
|[CView::OnUpdate](#onupdate)|Volá se, aby upozornění zobrazení, které bylo jeho dokument upravovat.|

## <a name="remarks"></a>Poznámky

Zobrazení je připojené k dokumentu a funguje jako prostředník mezi dokumentem a uživatelem: zobrazení vykreslí obrázek dokumentu na obrazovce nebo tiskárny a interpretuje jako operace prováděné na dokument vstup uživatele.

Zobrazení je podřízená okna rámce. Více než jedno zobrazení můžete sdílet okno rámce, stejně jako v případě rozděleného okna. Vztah mezi zobrazení třídy třídy oken s rámečkem a dokumentové třídy je zřízený `CDocTemplate` objektu. Když uživatel otevře nové okno nebo rozdělí existující jeden rozhraní vytvoří nové zobrazení a připojí ho k tomuto dokumentu.

Zobrazení lze připojit pouze jeden dokument, ale dokumentu může mít více zobrazení k němu připojená najednou – například, pokud dokument se zobrazí okno s rozdělovačem nebo více podřízených oken v aplikaci (MDI interface) více dokumentů. Vaše aplikace může podporovat různé typy zobrazení pro daný dokument typ; textový editor může například poskytnout úplný text zobrazení dokumentu a zobrazení osnovy, která zobrazuje pouze část záhlaví. Tyto různé typy zobrazení mohou být umístěny v samostatných okna s rámečkem nebo v samostatné podokna jeden snímek okna použití okno s rozdělovačem.

Zobrazení může být zodpovědná za zpracování několik různých typů vstupu, jako je vstup z klávesnice, myš vstup nebo vstup pomocí přetahování myší, jakož i příkazy z nabídky, panely nástrojů nebo posuvníky. Zobrazení přijímá příkazy, které jsou předávány podle jeho rámce okna. Pokud zobrazení nezpracovává zadaný příkaz, předá příkazu jeho přidružený dokument. Stejně jako všechny cíle příkazů zobrazení zpracovává zprávy přes mapu zpráv.

Zobrazení zodpovídá pro zobrazení a úpravy dat dokumentu, ale nikoli pro jeho uložení. Dokument obsahuje zobrazení s nezbytné podrobnosti o jeho data. Můžete umožnit přístup k zobrazení, poskytované dokumentu datové členy přímo, nebo můžete členské funkce ve třídě dokumentů pro danou třídu zobrazení volání.

Při změně dat dokumentu, zobrazení, která je zodpovědná za změny obvykle volá [CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) funkce pro dokument, který upozorní všech ostatních zobrazeních voláním `OnUpdate` členské funkce pro Každý. Výchozí implementace `OnUpdate` zruší platnost celou klientskou oblast zobrazení. Můžete přepsat tak zneplatnit pouze ty oblasti od klientské oblasti, které mapují na změněné části dokumentu.

Použití `CView`odvodit třídu z něj a implementovat `OnDraw` členskou funkci provádět displejem. Můžete také použít `OnDraw` provést náhled tisku a tisk. Rozhraní framework zpracovává tisku smyčky pro tisk a náhled dokumentu.

Zobrazení zpracovává zprávy posuvníku s [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) a [CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) členské funkce. Můžete implementovat posuvníku zpracování zpráv v těchto funkcí, nebo můžete použít `CView` odvozené třídy [cscrollview –](../../mfc/reference/cscrollview-class.md) zpracování posouvání za vás.

Kromě `CScrollView`, poskytuje devět ostatních tříd odvozených z knihovny Microsoft Foundation Class `CView`:

- [Cctrlview –](../../mfc/reference/cctrlview-class.md), zobrazení, která umožňuje využití dokumentu – zobrazení architektury s využitím strom, list a bohaté ovládacích prvcích pro úpravy.

- [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md), zobrazení, které zobrazuje záznamy databáze v ovládacích prvcích dialogového okna.

- [CEditView](../../mfc/reference/ceditview-class.md), zobrazení, které poskytuje jednoduché víceřádkovém textovém editoru. Můžete použít `CEditView` objektu jako ovládací prvek dialogového okna, jakož i zobrazení dokumentu.

- [CFormView](../../mfc/reference/cformview-class.md), posuvný zobrazení, která obsahuje ovládací prvky dialogového okna a je založena na prostředku šablony dialogového okna.

- [CListView](../../mfc/reference/clistview-class.md), zobrazení, která umožňuje využití dokumentu – zobrazení architektury s využitím ovládacích prvcích seznam.

- [CRecordView](../../mfc/reference/crecordview-class.md), zobrazení, které zobrazuje záznamy databáze v ovládacích prvcích dialogového okna.

- [Cricheditview –](../../mfc/reference/cricheditview-class.md), zobrazení, která umožňuje využití dokumentu – zobrazení architektury s využitím bohatých ovládacích prvcích pro úpravy.

- [Cscrollview –](../../mfc/reference/cscrollview-class.md), zobrazení, které automaticky poskytuje podporu posouvání.

- [CTreeView](../../mfc/reference/ctreeview-class.md), zobrazení, která umožňuje využití dokumentu – zobrazení architektury s využitím ovládacích prvků strom.

`CView` Třída také obsahuje implementaci odvozené třídy s názvem `CPreviewView`, rozhraním, který se používá k provedení zobrazení náhledu tisku. Tato třída poskytuje podporu pro funkce, které jsou jedinečné pro okno náhledu tisku, jako je panel nástrojů, nebo double – jednostránkové ve verzi preview, a změna měřítka zobrazení, který je, zvětšení zobrazená v náhledu obrázku. Není nutné volat nebo přepsat některý `CPreviewView`pro členské funkce, pokud chcete implementovat vlastní rozhraní pro zobrazení náhledu tisku (například pokud chcete zajistit podporu úpravy v režimu náhledu). Další informace o používání `CView`, naleznete v tématu [architekturu Document/View](../../mfc/document-view-architecture.md) a [tisk](../../mfc/printing.md). Kromě toho najdete v článku [Technická poznámka 30](../../mfc/tn030-customizing-printing-and-print-preview.md) podrobné informace o přizpůsobení náhledu tisku.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CView`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

##  <a name="cview"></a>  CView::CView

Vytvoří `CView` objektu.

```
CView();
```

### <a name="remarks"></a>Poznámky

Rozhraní volá konstruktor, když se vytvoří nový objekt okna rámce nebo je rozdělit okno. Přepsat [OnInitialUpdate](#oninitialupdate) členskou funkci k inicializaci zobrazení po dokumentu.

##  <a name="doprepareprinting"></a>  CView::DoPreparePrinting

Voláním této funkce z přepsání metody [OnPreparePrinting –](#onprepareprinting) pro vyvolání dialogového okna Tisk a vytvoří kontext zařízení tiskárny.

```
BOOL DoPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*pInfo*<br/>
Odkazuje [cprintinfo –](../../mfc/reference/cprintinfo-structure.md) struktura, která popisuje aktuální tiskové úlohy.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud můžete začít tisku nebo náhledu; 0, pokud byla přerušena.

### <a name="remarks"></a>Poznámky

Chování této funkce závisí na tom, jestli je volána pro tisku nebo náhledu (určená `m_bPreview` člena *pInfo* parametr). Pokud je soubor tisku, tato funkce vyvolá dialogové okno Tisk, pomocí hodnot v [cprintinfo –](../../mfc/reference/cprintinfo-structure.md) struktury, která *pInfo* odkazuje na; po zavření dialogových oken uživatel vytvoří funkci kontext zařízení tiskárny na základě nastavení zadané v dialogovém okně vyberte uživatele a vrátí tento kontext zařízení prostřednictvím *pInfo* parametru. Kontext zařízení slouží k tisku dokumentu.

Pokud soubor je náhledu, tato funkce vytvoří kontext zařízení tiskárny pomocí aktuální nastavení tiskárny. kontext zařízení se používá pro simulaci tiskárny ve verzi preview.

##  <a name="getdocument"></a>  CView::GetDocument

Volání této funkce získáte ukazatel na dokument v zobrazení.

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel [CDocument](../../mfc/reference/cdocument-class.md) objekt přidružený k zobrazení. Hodnota NULL, pokud zobrazení není připojené k dokumentu.

### <a name="remarks"></a>Poznámky

To umožňuje volat členské funkce dokumentu.

##  <a name="isselected"></a>  CView::IsSelected

Volá se rozhraním, chcete-li zkontrolovat, zda je vybrána položka zadaný dokument.

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>Parametry

*pDocItem*<br/>
Odkazuje na položku dokumentu testován.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je vybraná položka určeného dokumentu; jinak 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce vrátí hodnotu FALSE. Přepsat tuto funkci při implementaci výběr pomocí [cdocitem –](../../mfc/reference/cdocitem-class.md) objekty. Tato funkce je nutné přepsat, pokud zobrazení obsahuje položky OLE.

##  <a name="onactivateframe"></a>  CView::OnActivateFrame

Volá se rozhraním, když se aktivuje nebo deaktivuje okno rámce obsahující zobrazení.

```
virtual void OnActivateFrame(
    UINT nState,
    CFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>Parametry

*nInformace*<br/>
Určuje, zda je okno rámce se aktivuje nebo deaktivuje. Může být jeden z následujících hodnot:

- WA_INACTIVE okno rámce je právě deaktivována.

- WA_ACTIVE okno rámce je se aktivuje pomocí některé jiné metody než myši klikněte na tlačítko (například pomocí rozhraní klávesnice pro výběr v okně).

- WA_CLICKACTIVE okno rámce je právě aktivován kliknutí myší

*pFrameWnd*<br/>
Ukazatel na rámec okna, který má být aktivován.

### <a name="remarks"></a>Poznámky

Tato členská funkce přepište, pokud chcete provést zvláštní zpracování, když se aktivuje nebo deaktivuje okno rámce, který je přidružený k zobrazení. Například [CFormView](../../mfc/reference/cformview-class.md) provádí toto přepsání, když se uloží a obnoví ovládací prvek, který má právě fokus.

##  <a name="onactivateview"></a>  CView::OnActivateView

Volá se rozhraním, když se aktivuje nebo deaktivuje zobrazení.

```
virtual void OnActivateView(
    BOOL bActivate,
    CView* pActivateView,
    CView* pDeactiveView);
```

### <a name="parameters"></a>Parametry

*bActivate*<br/>
Určuje, zda je zobrazení se aktivuje nebo deaktivuje.

*pActivateView*<br/>
Odkazuje na objekt zobrazení, která se aktivuje.

*pDeactiveView*<br/>
Odkazuje na objekt zobrazení, která je právě deaktivována.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce nastaví fokus na zobrazení, které je aktivováno. Tato funkce přepište, pokud chcete provést zvláštní zpracování, když se aktivuje nebo deaktivuje zobrazení. Například pokud chcete zadat speciální vizuální prvky, které odlišují od neaktivní zobrazení aktivní zobrazení, které prozkoumá *bActivate* parametr a aktualizujte zobrazení vzhled odpovídajícím způsobem.

*PActivateView* a *pDeactiveView* parametry přejděte na stejné zobrazení, pokud je aktivovaná okna hlavního rámce aplikace beze změny v aktivním zobrazení – například pokud je fokus přenos z jiné aplikace na tento jeden, nikoli z jednoho zobrazení do jiného v rámci aplikace nebo při přepínání mezi podřízených oken MDI. V případě potřeby díky tomu zobrazení znovu realizovat svoji paletu.

Tyto parametry se liší při [CFrameWnd::SetActiveView](../../mfc/reference/cframewnd-class.md#setactiveview) volána s zobrazení, které se liší od co [CFrameWnd::GetActiveView](../../mfc/reference/cframewnd-class.md#getactiveview) vrátí. K tomu nejčastěji s rozdělovače oken.

##  <a name="onbeginprinting"></a>  CView::OnBeginPrinting

Volá se rozhraním na začátku úlohy tisku nebo náhledu tisku, po `OnPreparePrinting` byla volána.

```
virtual void OnBeginPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*primární řadič domény*<br/>
Odkazuje na kontext zařízení tiskárny.

*pInfo*<br/>
Odkazuje [cprintinfo –](../../mfc/reference/cprintinfo-structure.md) struktura, která popisuje aktuální tiskové úlohy.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce nemá žádný účinek. Přepsání této funkce můžete přidělit všechny GDI prostředky, jako je například písma, nebo pera potřebné speciálně pro tisk. Vyberte objekty GDI do kontextu zařízení v rámci [OnPrint –](#onprint) členskou funkci pro každou stránku, která je používá. Pokud používáte stejný objekt zobrazení provádět obrazovky a tisk, použití samostatných proměnné pro GDI prostředky potřebné pro každé zobrazení; můžete aktualizovat obrazovky při tisku.

Tuto funkci můžete použít také k provedení inicializace, které závisí na vlastnosti kontextu zařízení tiskárny. Například počet stránek potřeby se dokument vytiskne na může záviset na nastavení, která uživatel zadal z dialogového okna Tisk (jako je délka stránky). V takové situaci nelze zadat délku dokumentu v [OnPreparePrinting –](#onprepareprinting) členská funkce, kde by obvykle tak učiníte, musíte počkat, dokud kontextu zařízení tiskárny byly vytvořeny podle nastavení v dialogovém okně. [OnBeginPrinting –](#onbeginprinting) je první přepisovatelné funkce, které poskytuje přístup k [CDC](../../mfc/reference/cdc-class.md) objekt představující kontext zařízení tiskárny, abyste mohli nastavit délku dokumentu z této funkce. Všimněte si, že pokud v tuto chvíli není zadána délka dokumentu, posuvník se nezobrazí v náhledu.

##  <a name="ondragenter"></a>  CView::OnDragEnter

Volá se rozhraním, když ukazatel myši poprvé vstoupí neposouvaných oblast okna cíl přetažení.

```
virtual DROPEFFECT OnDragEnter(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pDataObject*<br/>
Odkazuje [coledataobject –](../../mfc/reference/coledataobject-class.md) se přetáhnout do oblasti zobrazení.

*dwKeyState*<br/>
Obsahuje informace o stavu modifikační klávesy. Jedná se o kombinaci libovolný počet následující: MK_CONTROL MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON a MK_RBUTTON.

*Bod*<br/>
Aktuální pozicí myši vzhledem ke klientské oblasti zobrazení.

### <a name="return-value"></a>Návratová hodnota

Maximum DROPEFFECT Výčtový typ, který označuje typ přetažení, ke kterým by uživatel vyřadit objekt na této pozici. Typ rozevírací obvykle závisí na aktuální stav klíčů indikován *dwKeyState*. Standardní mapování keystates DROPEFFECT hodnoty je:

- DROPEFFECT_NONE datový objekt nelze vyřadit, v tomto okně.

- DROPEFFECT_LINK pro MK_CONTROL &#124; MK_SHIFT vytvoří propojení mezi objekt a jeho serverem.

- DROPEFFECT_COPY pro MK_CONTROL vytvoří kopii přetažený objekt.

- DROPEFFECT_MOVE pro MK_ALT vytvoří kopii přetažený objekt a odstranění původního objektu. To je obvykle výchozí odkládací efekt, pokud zobrazení může přijmout tímto datovým objektem.

Další informace najdete v ukázce MFC Advanced Concepts [OCLIENT](../../visual-cpp-samples.md).

### <a name="remarks"></a>Poznámky

Výchozí implementace je Neprovádět žádnou akci a vrátí DROPEFFECT_NONE.

Přepsání této funkce můžete připravit pro budoucí volání [ondragover –](#ondragover) členskou funkci. V tuto chvíli pro pozdější použití v mají být načtena žádná data z datového objektu vyžaduje `OnDragOver` členskou funkci. Zobrazení se musí aktualizovat také v tuto chvíli poskytnout uživateli vizuální zpětnou vazbu. Další informace najdete v článku [přetažení: implementace cíle přetažení](../../mfc/drag-and-drop-implementing-a-drop-target.md).

##  <a name="ondragleave"></a>  CView::OnDragLeave

Volá se rozhraním během operace přetažení. když se ukazatel myši přesune mimo platnou oblast přetažení pro toto okno.

```
virtual void OnDragLeave();
```

### <a name="remarks"></a>Poznámky

Potlačí tuto funkci v případě, že aktuální zobrazení musí vyčistit všechny akce prováděné během [ondragenter –](#ondragenter) nebo [ondragover –](#ondragover) volání, například odebrání jakoukoli zpětnou vazbu visual uživatele, zatímco byl přetáhnout objekt .

##  <a name="ondragover"></a>  CView::OnDragOver

Po přesunutí v okně cíl přetažení myší, volá se rozhraním při operaci přetažení.

```
virtual DROPEFFECT OnDragOver(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pDataObject*<br/>
Odkazuje [coledataobject –](../../mfc/reference/coledataobject-class.md) přetažen přes cíl přetažení.

*dwKeyState*<br/>
Obsahuje informace o stavu modifikační klávesy. Jedná se o kombinaci libovolný počet následující: MK_CONTROL MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON a MK_RBUTTON.

*Bod*<br/>
Aktuální pozice myši vzhledem ke klientské oblasti zobrazení.

### <a name="return-value"></a>Návratová hodnota

Maximum DROPEFFECT Výčtový typ, který označuje typ přetažení, ke kterým by uživatel vyřadit objekt na této pozici. Typ rozevírací často závisí na aktuální stav klíče je určeno *dwKeyState*. Standardní mapování keystates DROPEFFECT hodnoty je:

- DROPEFFECT_NONE datový objekt nelze vyřadit, v tomto okně.

- DROPEFFECT_LINK pro MK_CONTROL &#124; MK_SHIFT vytvoří propojení mezi objekt a jeho serverem.

- DROPEFFECT_COPY pro MK_CONTROL vytvoří kopii přetažený objekt.

- DROPEFFECT_MOVE pro MK_ALT vytvoří kopii přetažený objekt a odstranění původního objektu. To je obvykle výchozí odkládací efekt, pokud zobrazení může přijmout datový objekt.

Další informace najdete v ukázce MFC Advanced Concepts [OCLIENT](../../visual-cpp-samples.md).

### <a name="remarks"></a>Poznámky

Výchozí implementace je Neprovádět žádnou akci a vrátí DROPEFFECT_NONE.

Přepsání této funkce můžete poskytnout uživateli vizuální zpětnou vazbu během operace přetažení. Protože tato funkce je volána nepřetržitě, jakýkoli kód, jsou v něm obsaženy by mělo být optimalizované co největší míře. Další informace najdete v článku [přetažení: implementace cíle přetažení](../../mfc/drag-and-drop-implementing-a-drop-target.md).

##  <a name="ondragscroll"></a>  CView::OnDragScroll

Volá se rozhraním před voláním [ondragenter –](#ondragenter) nebo [ondragover –](#ondragover) zjistit, jestli je bod v posuvné oblasti.

```
virtual DROPEFFECT OnDragScroll(
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*dwKeyState*<br/>
Obsahuje informace o stavu modifikační klávesy. Jedná se o kombinaci libovolný počet následující: MK_CONTROL MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON a MK_RBUTTON.

*Bod*<br/>
Obsahuje umístění kurzoru v pixelech, vzhledem k obrazovce.

### <a name="return-value"></a>Návratová hodnota

Maximum DROPEFFECT Výčtový typ, který označuje typ přetažení, ke kterým by uživatel vyřadit objekt na této pozici. Typ rozevírací obvykle závisí na aktuální stav klíčů indikován *dwKeyState*. Standardní mapování keystates DROPEFFECT hodnoty je:

- DROPEFFECT_NONE datový objekt nelze vyřadit, v tomto okně.

- DROPEFFECT_LINK pro MK_CONTROL &#124; MK_SHIFT vytvoří propojení mezi objekt a jeho serverem.

- DROPEFFECT_COPY pro MK_CONTROL vytvoří kopii přetažený objekt.

- DROPEFFECT_MOVE pro MK_ALT vytvoří kopii přetažený objekt a odstranění původního objektu.

- DROPEFFECT_SCROLL znamená, že operace přetažení posuvníku se použije nebo ke kterým dochází v cílové zobrazení.

Další informace najdete v ukázce MFC Advanced Concepts [OCLIENT](../../visual-cpp-samples.md).

### <a name="remarks"></a>Poznámky

Tato funkce přepište, pokud chcete zadat zvláštní chování pro tuto událost. Výchozí implementace automaticky posouvá windows, pokud kurzor je přetáhnout do oblasti posuvníku výchozí uvnitř ohraničení okna. Další informace najdete v článku [přetažení: implementace cíle přetažení](../../mfc/drag-and-drop-implementing-a-drop-target.md).

##  <a name="ondraw"></a>  CView::OnDraw

Volá se rozhraním, aby se vykreslil obraz dokumentu.

```
virtual void OnDraw(CDC* pDC) = 0;
```

### <a name="parameters"></a>Parametry

*primární řadič domény*<br/>
Odkazuje na kontext zařízení má být použit pro vykreslení bitovou kopii dokumentu.

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto funkci provádět zobrazení, tisku a tiskového náhledu a v každém případě předá kontextu jiného zařízení. Neexistuje žádný výchozí implementaci.

Je nutné přepsat tuto funkci chcete-li zobrazit zobrazení dokumentu. Bude možné volat grafického zařízení (GDI) rozhraní pomocí [CDC](../../mfc/reference/cdc-class.md) objekt, který odkazuje *primárního řadiče domény* parametru. Můžete vybrat prostředků GDI, jako je například písma, nebo pera do kontextu zařízení před vykreslením a potom později zrušit. Kreslení kód často může být nezávislé na zařízení; To znamená nevyžaduje informace o typu zařízení se zobrazuje obrázek.

Chcete-li optimalizovat kreslení, zavolejte [RectVisible](../../mfc/reference/cdc-class.md#rectvisible) členská funkce kontextu zařízení a zjistěte, zda bude vykreslen dané obdélník. Pokud je potřeba rozlišovat mezi normálním obrazovky a tisk, zavolejte [IsPrinting](../../mfc/reference/cdc-class.md#isprinting) členská funkce kontextu zařízení.

##  <a name="ondrop"></a>  CView::OnDrop

Volá se rozhraním, když uživatel uvolní objekt dat přes cíle přetažení platný.

```
virtual BOOL OnDrop(
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>Parametry

"pDataObject * body [coledataobject –](../../mfc/reference/coledataobject-class.md) , který je přetáhnout do cíl přetažení.

*dropEffect*<br/>
Přetažení efekt, který uživatel požaduje.

- DROPEFFECT_COPY vytvoří kopii datového objektu probíhá vyřazování.

- DROPEFFECT_MOVE přesune do aktuální kurzor myši datový objekt.

- DROPEFFECT_LINK vytvoří propojení mezi datový objekt a jeho serverem.

*Bod*<br/>
Aktuální pozice myši vzhledem ke klientské oblasti zobrazení.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud rozevírací byla úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace neprovede žádnou akci a vrátí hodnotu FALSE.

Potlačí tuto funkci, která implementuje vliv OLE – přetažení do klientské oblasti zobrazení. Datový objekt se dají prozkoumat prostřednictvím *pDataObject* dat schránky formátů a data zahozena na zadaný bod.

> [!NOTE]
>  Rozhraní není voláním této funkce, pokud dojde k přepsání [ondropex –](#ondropex) v této třídě zobrazení.

##  <a name="ondropex"></a>  CView::OnDropEx

Volá se rozhraním, když uživatel uvolní objekt dat přes cíle přetažení platný.

```
virtual DROPEFFECT OnDropEx(
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pDataObject*<br/>
Odkazuje [coledataobject –](../../mfc/reference/coledataobject-class.md) , který je přetáhnout do cíl přetažení.

*dropDefault*<br/>
Efekt, který uživatel vybral pro operaci přetažení výchozí na základě aktuálního stavu klíče. To může být DROPEFFECT_NONE. Přetažení efekty jsou popsány v části poznámky.

*rozevíracího seznamu*<br/>
Seznam rozevírací efekty, které podporuje zdroje přemístění. Přetažení efekt hodnoty lze spojovat pomocí bitový operátor OR ( **&#124;**) operace. Přetažení efekty jsou popsány v části poznámky.

*Bod*<br/>
Aktuální pozice myši vzhledem ke klientské oblasti zobrazení.

### <a name="return-value"></a>Návratová hodnota

Přetažení efekt, který je výsledkem pokus odkládací umístění, které určuje *bodu*. Musí to být jedna z hodnot indikován *dropEffectList*. Přetažení efekty jsou popsány v části poznámky.

### <a name="remarks"></a>Poznámky

Výchozí implementace je Neprovádět žádnou akci a vrátí fiktivní hodnoty (-1) k označení, že by měly volat rozhraní [OnDrop](#ondrop) obslužné rutiny.

Potlačí tuto funkci, která implementuje účinek stisknutí pravého tlačítka myši přetáhnout. Stisknutí pravého tlačítka myši přetáhnout obvykle zobrazí nabídku možností, když se uvolní pravé tlačítko myši.

Přepsání metody `OnDropEx` by měl dotázat na pravé tlačítko myši. Můžete volat [GetKeyState](https://msdn.microsoft.com/library/windows/desktop/ms646301) nebo ukládání stavu stisknutí pravého tlačítka myši z vaší [ondragenter –](#ondragenter) obslužné rutiny.

- Pokud pravého tlačítka myši je vypnutý, přepsání zobrazeno v místní nabídce, která nabízí podporu účinky rozevírací podle zdroje přemístění.

   - Prozkoumejte *rozbalovacího seznamu* umožňuje zjistit dopady rozevírací podporována zdroji přetažení. Povolte jenom tyto akce v místní nabídce.

   - Použití [SetMenuDefaultItem](/windows/desktop/api/winuser/nf-winuser-setmenudefaultitem) nastavit výchozí akce na základě *dropDefault*.

   - Nakonec proveďte akci indikován výběr uživatele z místní nabídky.

- Nejsou-li pravým tlačítkem myši dolů, má to jako standardní rozevírací požadavek zpracovat přepsání. Použijte rozevírací efekt podle *dropDefault*. Alternativně můžete přepsání vrátit fiktivní hodnoty (-1) k označení, že `OnDrop` zpracuje operaci přetažení.

Použití *pDataObject* k prozkoumání `COleDataObject` pro data ze schránky. formát a data zahozena na zadaný bod.

Přetažení účinky popisují akci přidruženou k operaci přetažení. Najdete v následujícím seznamu rozevírací účinky:

- Přetažení A DROPEFFECT_NONE nebude povolen.

- Operace kopírování A DROPEFFECT_COPY by byla prováděna.

- Operace přesunu A DROPEFFECT_MOVE by byla prováděna.

- Odkaz A DROPEFFECT_LINK z vyřazené dat na původní data by byla založena.

- DROPEFFECT_SCROLL znamená, že operace přetažení posuvníku se použije nebo dochází v cíli.

Další informace o nastavení výchozí příkaz nabídky, naleznete v tématu [SetMenuDefaultItem](/windows/desktop/api/winuser/nf-winuser-setmenudefaultitem) v sadě Windows SDK a [CMenu::GetSafeHmenu](../../mfc/reference/cmenu-class.md#getsafehmenu) v tomto svazku.

##  <a name="onendprinting"></a>  CView::OnEndPrinting

Volá se rozhraním po vytištění nebo zobrazení náhledu dokumentu.

```
virtual void OnEndPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*primární řadič domény*<br/>
Odkazuje na kontext zařízení tiskárny.

*pInfo*<br/>
Odkazuje [cprintinfo –](../../mfc/reference/cprintinfo-structure.md) struktura, která popisuje aktuální tiskové úlohy.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce nemá žádný účinek. Přepsat uvolněte veškeré prostředky GDI jste přidělili v této funkce [OnBeginPrinting –](#onbeginprinting) členskou funkci.

##  <a name="onendprintpreview"></a>  CView::OnEndPrintPreview

Volá se rozhraním, když uživatel ukončí režim náhledu tisku.

```
virtual void OnEndPrintPreview(
    CDC* pDC,
    CPrintInfo* pInfo,
    POINT point,
    CPreviewView* pView);
```

### <a name="parameters"></a>Parametry

*primární řadič domény*<br/>
Odkazuje na kontext zařízení tiskárny.

*pInfo*<br/>
Odkazuje [cprintinfo –](../../mfc/reference/cprintinfo-structure.md) struktura, která popisuje aktuální tiskové úlohy.

*Bod*<br/>
Určuje bod na stránku, která byla naposledy zobrazená v režimu náhledu.

*pView*<br/>
Odkazuje na objekt zobrazení použitý pro zobrazení náhledu.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce se volá [OnEndPrinting –](#onendprinting) členské funkce a obnoví začal hlavní okno rámce do stavu před náhledu tisku. Potlačí tuto funkci provést zvláštní zpracování, když se ukončí režim náhledu. Například pokud chcete zachovat pozici uživatele v dokumentu, při přepnutí z režimu náhledu na režim zobrazení Normální, vám umožní posouvání, aby pozice popsaného *bodu* parametr a `m_nCurPage` člena `CPrintInfo` struktury, která *pInfo* parametr odkazuje na.

Vždy volat základní třídy verzi `OnEndPrintPreview` z přepsání, obvykle na konci funkce.

##  <a name="oninitialupdate"></a>  CView::OnInitialUpdate

Volá se rozhraním po zobrazení je nejprve připojen k dokumentu, ale před začátku zobrazení.

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>Poznámky

Volá výchozí implementaci této funkce [OnUpdate](#onupdate) členská funkce se žádné informace nápovědy (to znamená, že použití výchozí hodnoty 0 pro *lHint* parametru a hodnota NULL pro  *pHint* parametr). Přepsání této funkce provedla jednorázová inicializace, která vyžaduje informace o dokumentu. Například pokud vaše aplikace má pevnou velikostí dokumenty, můžete použít tuto funkci inicializace umožňující posouvání omezení zobrazení na základě velikosti dokumentu. Pokud vaše aplikace podporuje dokumenty proměnlivé velikosti, použijte [OnUpdate](#onupdate) aktualizovat posouvání omezuje pokaždé, když změny dokumentu.

##  <a name="onpreparedc"></a>  CView::OnPrepareDC

Volá se rozhraním před [OnDraw](#ondraw) členská funkce je volána pro zobrazení na obrazovce a před [OnPrint –](#onprint) členská funkce je volána pro každou stránku během tisku nebo náhledu.

```
virtual void OnPrepareDC(
    CDC* pDC,
    CPrintInfo* pInfo = NULL);
```

### <a name="parameters"></a>Parametry

*primární řadič domény*<br/>
Odkazuje na kontext zařízení má být použit pro vykreslení bitovou kopii dokumentu.

*pInfo*<br/>
Odkazuje na [cprintinfo –](../../mfc/reference/cprintinfo-structure.md) struktura, která popisuje aktuální tiskové úlohy, pokud `OnPrepareDC` je volána pro tisku nebo náhledu; `m_nCurPage` člen Určuje stránku, o které se mají vytisknout. Tento parametr hodnotu NULL, pokud `OnPrepareDC` je volána pro zobrazení na obrazovce.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce nemá žádný účinek, pokud je tato funkce volána pro zobrazení na obrazovce. Ale tato funkce je v odvozených třídách přepsána, jako například [cscrollview –](../../mfc/reference/cscrollview-class.md), aby se upravily atributy kontextu zařízení; v důsledku toho musí vždy volat implementaci základní třídy na začátku přepsání.

Funkce je volána pro tisk, výchozí implementace prozkoumá stránka informací uložených v *pInfo* parametru. Pokud nebyla zadána délka dokumentu, `OnPrepareDC` předpokládá dokumentu, který má být jednu stránku dlouhé a tisku smyčky se ukončí po vytisknutí jednu stránku. Funkce zastaví smyčka tisku nastavením `m_bContinuePrinting` členu struktury na hodnotu FALSE.

Přepsat `OnPrepareDC` pro některý z následujících důvodů:

- Aby se upravily atributy kontextu zařízení podle potřeby pro zadanou stránku. Například pokud je potřeba nastavit režim mapování nebo dalších vlastností kontextu zařízení, tak učinit v této funkci.

- K provedení čas tisku stránkování. Obvykle se po zahájení tisk pomocí zadejte délku dokumentu [OnPreparePrinting –](#onprepareprinting) členskou funkci. Ale pokud si nejste jisti předem jak dlouho dokument je (například při tisku neurčeném počet záznamů z databáze), přepište `OnPrepareDC` pro testování konec dokumentu během jeho tisku. Když neexistuje žádné další dokumentu, které se mají vytisknout, nastavte `m_bContinuePrinting` člena `CPrintInfo` struktury na hodnotu FALSE.

- K odeslání řídícími kódy tiskárny na základě stránku po stránce. K odeslání řídícími kódy z `OnPrepareDC`, volání `Escape` členskou funkci *primárního řadiče domény* parametru.

Volání základní třídy verzi `OnPrepareDC` na začátku přepsání.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#183](../../mfc/codesnippet/cpp/cview-class_1.cpp)]

##  <a name="onprepareprinting"></a>  CView::OnPreparePrinting

Volá se rozhraním, než je vytištění nebo zobrazení náhledu dokumentu.

```
virtual BOOL OnPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*pInfo*<br/>
Odkazuje [cprintinfo –](../../mfc/reference/cprintinfo-structure.md) struktura, která popisuje aktuální tiskové úlohy.

### <a name="return-value"></a>Návratová hodnota

Nenulový začátek tisku; 0, pokud tisková úloha byla zrušena.

### <a name="remarks"></a>Poznámky

Výchozí implementace nemá žádný účinek.

Je nutné přepsat tuto funkci povolit tisku a tiskového náhledu. Volání [DoPreparePrinting](#doprepareprinting) členskou funkci, předají se jí *pInfo* parametr a pak se vraťte vrácená hodnota; `DoPreparePrinting` zobrazí dialogové okno Tisk a vytvoří kontext zařízení tiskárny. Pokud chcete inicializovat dialogové okno Tisk s hodnoty jiné než výchozí hodnoty, přiřadit hodnoty k členům *pInfo*. Například pokud znáte délku dokumentu, předat hodnotu do [SetMaxPage](../../mfc/reference/cprintinfo-structure.md#setmaxpage) členskou funkci *pInfo* před voláním `DoPreparePrinting`. Tato hodnota se zobrazí v poli Komu: pole v rozsahu části dialogového okna Tisk.

`DoPreparePrinting` nezobrazuje dialogového okna Tisk pro úlohu ve verzi preview. Pokud chcete obejít dialogového okna Tisk tiskové úlohy, zkontrolujte, že `m_bPreview` členem *pInfo* hodnotu FALSE a nastavte ho na hodnotu TRUE před předáním do `DoPreparePrinting`; později obnovit na hodnotu FALSE.

Pokud je potřeba provést inicializace, které vyžadují přístup k `CDC` objekt představující tiskárny kontextu zařízení (například, pokud je potřeba vědět velikost stránky před určením délky dokumentu), přepsat `OnBeginPrinting` člena funkce.

Pokud chcete nastavit hodnotu `m_nNumPreviewPages` nebo `m_strPageDesc` členy *pInfo* parametr, Uděláte to tak po volání `DoPreparePrinting`. `DoPreparePrinting` Členské funkce sad `m_nNumPreviewPages` na hodnotu nalezenou v vaší aplikace. Soubor INI a nastaví `m_strPageDesc` na výchozí hodnotu.

### <a name="example"></a>Příklad

  Přepsat `OnPreparePrinting` a volat `DoPreparePrinting` z přepsání tak, aby rozhraní zobrazit dialogové okno Tisk, který se pro vás vytvořil tiskárny řadiče domény.

[!code-cpp[NVC_MFCDocView#184](../../mfc/codesnippet/cpp/cview-class_2.cpp)]

Pokud víte, kolik stránek obsahuje dokument, nastavit maximální stránku `OnPreparePrinting` před voláním `DoPreparePrinting`. Rozhraní se zobrazí číslo poslední stránky v poli "do" z dialogového okna Tisk.

[!code-cpp[NVC_MFCDocView#185](../../mfc/codesnippet/cpp/cview-class_3.cpp)]

##  <a name="onprint"></a>  CView::OnPrint

Volá se rozhraním pro tisk nebo náhled stránky z dokumentu.

```
virtual void OnPrint(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*primární řadič domény*<br/>
Odkazuje na kontext zařízení tiskárny.

*pInfo*<br/>
Odkazuje `CPrintInfo` struktura, která popisuje aktuální tiskové úlohy.

### <a name="remarks"></a>Poznámky

Pro každou tištěnou stránku volá framework ihned po volání této funkce [OnPrepareDC](#onpreparedc) členskou funkci. Je určená tištěnou stránku `m_nCurPage` člena [cprintinfo –](../../mfc/reference/cprintinfo-structure.md) struktury, která *pInfo* odkazuje na. Výchozí implementace volá [OnDraw](#ondraw) členskou funkci a předává je kontext zařízení tiskárny.

Tato funkce přepsání pro některý z následujících důvodů:

- Chcete-li povolit tisk vícestránkové dokumenty. Vykreslujte jen část dokumentu, který odpovídá právě tištěné stránky. Pokud používáte `OnDraw` provádět vykreslování můžete upravit původní zobrazení tak, aby vytiskla pouze odpovídající část dokumentu.

- Aby byl obraz tištěné lišit od obrazovky (tj. Pokud vaše aplikace není WYSIWYG). Místo předání kontextu zařízení do tiskárny `OnDraw`, kontext zařízení použít k vykreslení obrázku pomocí atributů není zobrazené na obrazovce.

   Pokud potřebujete prostředků GDI pro tisk, který nebudete používat pro obrazovku, vyberte je do kontextu zařízení před vykreslením a později zrušit. Tyto prostředky GDI by měla být přidělená v [OnBeginPrinting –](#onbeginprinting) a vydanou v [OnEndPrinting –](#onendprinting).

- K implementaci záhlaví a zápatí. Můžete dál používat `OnDraw` udělat tak, že omezíte oblasti, která můžete vytisknout na vykreslování.

Všimněte si, že `m_rectDraw` člena *pInfo* parametr popisuje oblasti mimo rozsah tisku stránky v logických jednotkách.

Nevolejte `OnPrepareDC` v přepsání metody `OnPrint`; volání rozhraní framework `OnPrepareDC` automaticky před voláním `OnPrint`.

### <a name="example"></a>Příklad

Tady je kostru pro překryté `OnPrint` funkce:

[!code-cpp[NVC_MFCDocView#186](../../mfc/codesnippet/cpp/cview-class_4.cpp)]

Další příklad naleznete v tématu [CRichEditView::PrintInsideRect](../../mfc/reference/cricheditview-class.md#printinsiderect).

##  <a name="onscroll"></a>  CView::OnScroll

Volá se rozhraním k určení, zda posouvání je možné.

```
virtual BOOL OnScroll(
    UINT nScrollCode,
    UINT nPos,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parametry

*nScrollCode*<br/>
Posuvníku kód, který označuje, že uživatel je posouvání požadavku. Tento parametr se skládá ze dvou částí: nejnižší bajt, který určuje typ vodorovně posuvný dochází, a implikovaný bajt, který určuje typ svisle posuvný výskytu:

- Posune SB_BOTTOM dolů.

- Posune SB_LINEDOWN jeden řádek dolů.

- Posune SB_LINEUP jeden řádek nahoru.

- Posune SB_PAGEDOWN jednu stránku dolů.

- Posune SB_PAGEUP jednu stránku nahoru.

- Posuňte se SB_THUMBTRACK Drags pole na určenou pozici. Aktuální pozice je zadána v *nPos*.

- Posune SB_TOP nahoru.

*nPos –*<br/>
Obsahuje aktuální pozice posuvníku – Pokud je kód posuvníku SB_THUMBTRACK; v opačném případě se nepoužívá. V závislosti na rozsahu počáteční posuvníku *nPos* může být záporný a by měl být přetypovat na **int** v případě potřeby.

*bDoScroll*<br/>
Určuje, zda by měla skutečně provést zadanou akci posouvání. Pokud je hodnota TRUE, pak posouvání by měla probíhat; Pokud má hodnotu FALSE, pak posouvání neproběhne.

### <a name="return-value"></a>Návratová hodnota

Pokud *bDoScroll* hodnotu TRUE a zobrazení bylo ve skutečnosti posunul, potom vrátí nenulovou hodnotu; jinak vrátí hodnotu 0. Pokud *bDoScroll* je FALSE, pak se vrátíte hodnotu, která jste by být vrácena, jestliže *bDoScroll* byly hodnotu TRUE, i když neprovedete skutečně posouvání.

### <a name="remarks"></a>Poznámky

V jednom případě tato funkce je volána rozhraním s *bDoScroll* nastavena na hodnotu TRUE, pokud zobrazení obdrží zprávu posuvník. V takovém případě by ve skutečnosti posuňte zobrazení. V ostatních případech tato funkce se volá s *bDoScroll* nastavena na hodnotu FALSE, pokud položka OLE. původně přetáhnout do oblast automatického posouvání cíle přetažení než posouvání ve skutečnosti. V takovém případě by neměla posunete skutečně zobrazení.

##  <a name="onscrollby"></a>  CView::OnScrollBy

Volá se rozhraním, když uživatel na oblast po k dispozici zobrazení dokumentu, buď přetažením položky OLE. pro zobrazení aktuálního ohraničení nebo manipulace s svislé nebo vodorovné posuvníky.

```
virtual BOOL OnScrollBy(
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parametry

*sizeScroll*<br/>
Počet pixelů posunul vodorovně a svisle.

*bDoScroll*<br/>
Určuje, zda posouvání zobrazení dojde k. Pokud je hodnota TRUE, pak posouvání probíhá; Pokud má hodnotu FALSE, pak posouvání se nevyskytuje.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud zobrazení bylo možné posunout; jinak 0.

### <a name="remarks"></a>Poznámky

V odvozených třídách tato metoda zkontroluje, zda je zobrazení posuvný ve směru požadované uživatele a následně aktualizuje nové oblasti v případě potřeby. Voláním této funkce se automaticky [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) a [CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) provádět skutečnou žádost posouvání.

Výchozí implementace této metody nedojde ke změně zobrazení, ale pokud není volána, nebude posouvejte zobrazení `CScrollView`-odvozené třídy.

Pokud dokument šířka nebo výška překročí 32767 pixelů, posouvání minulé 32767 selže, protože `OnScrollBy` volat pomocí neplatného *sizeScroll* argument.

##  <a name="onupdate"></a>  CView::OnUpdate

Volá se rozhraním po zobrazení dokumentu byla změněna; Tato funkce je volána [CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) a umožní zobrazení aktualizovat zobrazení tak, aby odrážela tyto změny.

```
virtual void OnUpdate(
    CView* pSender,
    LPARAM lHint,
    CObject* pHint);
```

### <a name="parameters"></a>Parametry

*pSender*<br/>
Odkazuje na zobrazení, úpravy dokumentů, nebo hodnota NULL, pokud jsou všechna zobrazení aktualizovat.

*lHint*<br/>
Obsahuje informace o změny.

*pHint*<br/>
Odkazuje na objekt ukládání informací o změny.

### <a name="remarks"></a>Poznámky

Výchozí implementace zkratka [OnInitialUpdate](#oninitialupdate). Výchozí implementace zruší platnost celou klientskou oblast, označení pro kreslení, když je obdržena další zprávu WM_PAINT. Tato funkce přepište, pokud chcete aktualizovat jenom do oblastí, které mapují na změněné části dokumentu. K tomu musíte předat informace o změny pomocí parametrů pomocný parametr.

Chcete-li použít *lHint*definovat zvláštní pomocný parametr hodnoty, většinou bitová maska nebo výčtového typu a mít dokumentu předat jednu z těchto hodnot. Použití *pHint*, odvoďte třídu pomocný parametr z [CObject](../../mfc/reference/cobject-class.md) a dokument předat ukazatel na objekt pomocný parametr; při přepisování `OnUpdate`, použijte [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof) Členská funkce k určení typu za běhu pomocný parametr objektu.

Obvykle by neměl provedením kreslení přímo z `OnUpdate`. Místo toho určete obdélník popisující, v souřadnicích zařízení, oblasti, která vyžaduje aktualizaci; předejte tento obdélník [CWnd::InvalidateRect](../../mfc/reference/cwnd-class.md#invalidaterect). To způsobí, že vykreslování po příštím [WM_PAINT](/windows/desktop/gdi/wm-paint) doručení zprávy.

Pokud *lHint* je 0 a *pHint* má hodnotu NULL, dokument odeslala oznámení obecné aktualizace. Pokud zobrazení obdrží upozornění na obecné aktualizace nebo jej nelze dekódovat pomocné parametry, by měl zneplatnit její celou klientskou oblast.

## <a name="see-also"></a>Viz také

[Ukázky knihovny MFC MDIDOCVW](../../visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[CFrameWnd – třída](../../mfc/reference/cframewnd-class.md)<br/>
[CSplitterWnd – třída](../../mfc/reference/csplitterwnd-class.md)<br/>
[CDC – třída](../../mfc/reference/cdc-class.md)<br/>
[CDocTemplate – třída](../../mfc/reference/cdoctemplate-class.md)<br/>
[CDocument – třída](../../mfc/reference/cdocument-class.md)
