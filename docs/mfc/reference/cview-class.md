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
ms.openlocfilehash: f6be846e80209ce94c84222d61c37a7964baad03
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855474"
---
# <a name="cview-class"></a>CView – třída

Poskytuje základní funkce pro uživatelsky definované třídy zobrazení.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE CView : public CWnd
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Název|Popis|
|----------|-----------------|
|[CView:: CView](#cview)|Vytvoří objekt `CView`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CView::D oPreparePrinting](#doprepareprinting)|Zobrazí dialogové okno Tisk a vytvoří kontext zařízení tiskárny. volá se při přepsání `OnPreparePrinting` členské funkce.|
|[CView:: GetDocument](#getdocument)|Vrátí dokument přidružený k zobrazení.|
|[CView:: s volbou](#isselected)|Testuje, zda je vybrána položka dokumentu. Vyžaduje se pro podporu OLE.|
|[CView:: OnDragEnter](#ondragenter)|Volá se, když se položka nejdřív přetáhne do oblasti zobrazení přetažení.|
|[CView:: OnDragLeave](#ondragleave)|Volá se, když přetažená položka opustí oblast zobrazení.|
|[CView:: OnDragOver](#ondragover)|Volá se, když se položka přetáhne do oblasti zobrazení přetažením.|
|[CView:: OnDragScroll](#ondragscroll)|Volá se, aby se určilo, jestli se kurzor přetáhne do oblasti posouvání okna.|
|[CView:: Drop drop](#ondrop)|Volá se, když se položka přetáhla v oblasti zobrazení, výchozí obslužná rutina.|
|[CView:: OnDropEx](#ondropex)|Volá se v případě, že byla položka přetažena do oblasti přetažení zobrazení, primární obslužné rutiny.|
|[CView:: OnInitialUpdate](#oninitialupdate)|Volá se po prvním připojení zobrazení k dokumentu.|
|[CView:: OnPrepareDC](#onpreparedc)|Volá se před tím, než je volána členská funkce `OnDraw` pro zobrazení obrazovky nebo je volána `OnPrint` členská funkce pro tisk nebo náhled tisku.|
|[CView:: Scroll](#onscroll)|Volá se při přetažení položek OLE za hranice zobrazení.|
|[CView:: OnScrollBy](#onscrollby)|Volá se, když se posune zobrazení obsahující aktivní místní položky OLE.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CView:: OnActivateFrame](#onactivateframe)|Volá se, když se aktivuje nebo deaktivuje okno rámce obsahující zobrazení.|
|[CView:: OnActivateView](#onactivateview)|Volá se, když se aktivuje zobrazení.|
|[CView:: OnBeginPrinting](#onbeginprinting)|Volá se, když se spustí tisková úloha; Přepište pro přidělení prostředků GDI (Graphic Device Interface).|
|[CView:: Draw](#ondraw)|Volá se, aby se vykreslil obrázek dokumentu pro zobrazení, tisk nebo náhled tisku. Vyžaduje se implementace.|
|[CView:: OnEndPrinting](#onendprinting)|Volá se, když se ukončí tisková úloha; přepsáním navrácení prostředků GDI.|
|[CView:: OnEndPrintPreview](#onendprintpreview)|Volá se, když se ukončí režim náhledu.|
|[CView:: OnPreparePrinting](#onprepareprinting)|Volá se před vytištěním nebo zobrazením náhledu dokumentu. přepsáním dialogového okna inicializace tisku.|
|[CView:: Print – tisk](#onprint)|Volá se, aby se zobrazila stránka dokumentu pro tisk nebo náhled.|
|[CView:: inupdate](#onupdate)|Volá se, aby se oznámilo zobrazení, že se dokument změnil.|

## <a name="remarks"></a>Poznámky

Zobrazení je připojeno k dokumentu a funguje jako prostředník mezi dokumentem a uživatelem: zobrazení vykresluje obrázek dokumentu na obrazovce nebo tiskárně a interpretuje vstup uživatele jako operace v dokumentu.

Zobrazení je podřízenou položkou okna rámce. Více než jedno zobrazení může sdílet okno rámce, jako v případě okna s rozdělovačem. Vztah mezi třídou zobrazení, třídou okna s rámečkem a třídou dokumentu je vytvořen objektem `CDocTemplate`. Když uživatel otevře nové okno nebo rozdělí stávající, rozhraní vytvoří nové zobrazení a připojí ho k dokumentu.

Zobrazení lze připojit pouze k jednomu dokumentu, ale k dokumentu může být připojeno více zobrazení najednou – například pokud se dokument zobrazuje v okně s rozdělovačem nebo v několika podřízených oknech v aplikaci MDI (Multiple Document Interface). Vaše aplikace může pro daný typ dokumentu podporovat různé typy zobrazení; například program pro zpracování textu může poskytovat kompletní textové zobrazení dokumentu a zobrazení osnovy, které zobrazuje pouze záhlaví oddílů. Tyto různé typy zobrazení lze umístit do samostatných oken s rámečkem nebo do samostatných podoken jednoho okna s rámečkem, pokud používáte okno s rozdělovačem.

Zobrazení může být zodpovědné za zpracování několika různých typů vstupů, jako je například vstup z klávesnice, vstup myši nebo vstup přes přetahování myší, a také příkazy z nabídek, panelů nástrojů nebo posouvaných panelů. Zobrazení přijímá příkazy předané jeho oknem rámců. Pokud zobrazení daný příkaz nezpracovává, přepošle příkaz do přidruženého dokumentu. Stejně jako všechny cíle příkazů zobrazení zpracovává zprávy přes mapu zpráv.

Zobrazení zodpovídá za zobrazení a úpravu dat dokumentu, ale ne pro ukládání. Dokument poskytuje zobrazení s potřebnými podrobnostmi o datech. Můžete nechat zobrazit přímo přístup k datovým členům dokumentu nebo můžete poskytnout členské funkce v třídě dokumentu pro třídu zobrazení, která se má volat.

Když se změní data dokumentu, zobrazení zodpovědné za tyto změny obvykle zavolá funkci [objektu CDocument:: UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) pro dokument, která upozorní všechna ostatní zobrazení voláním členské funkce `OnUpdate` pro každý. Výchozí implementace `OnUpdate` neověřuje celou klientskou oblast zobrazení. Můžete ji přepsat tak, aby zrušila platnost pouze těch oblastí klientské oblasti, které jsou mapovány na upravené části dokumentu.

Chcete-li použít `CView`, odvodit z něj třídu a implementovat členskou funkci `OnDraw` k provedení zobrazení obrazovky. `OnDraw` můžete použít také k tisku a náhledu tisku. Rozhraní zpracovává tiskovou smyčku pro tisk a náhled dokumentu.

Zobrazení zpracovává zprávy posuvníku pomocí členských funkcí [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) a [CWnd:: OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) . V těchto funkcích můžete implementovat zpracování zpráv s posuvníky, nebo můžete použít `CView` odvozené třídy [CScrollView](../../mfc/reference/cscrollview-class.md) pro zpracování posouvání.

Kromě `CScrollView`poskytuje knihovna Microsoft Foundation Class devět dalších tříd odvozených z `CView`:

- [CCtrlView](../../mfc/reference/cctrlview-class.md), zobrazení, které umožňuje použití architektury dokumentu-zobrazení s ovládacími prvky stromu, seznamu a Rich Edit.

- [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md), zobrazení, které zobrazuje záznamy databáze v ovládacích prvcích dialog box.

- [CEditView](../../mfc/reference/ceditview-class.md), zobrazení, které poskytuje jednoduchý víceřádkový textový editor. Objekt `CEditView` lze použít jako ovládací prvek v dialogovém okně a také zobrazení dokumentu.

- [CFormView](../../mfc/reference/cformview-class.md), rolovací zobrazení obsahující ovládací prvky dialogového okna a je založeno na prostředku šablony dialogového okna.

- [CListView –](../../mfc/reference/clistview-class.md), zobrazení, které umožňuje použití architektury dokumentu-zobrazení s ovládacími prvky seznamu.

- [CRecordView](../../mfc/reference/crecordview-class.md), zobrazení, které zobrazuje záznamy databáze v ovládacích prvcích dialog box.

- [CRichEditView –](../../mfc/reference/cricheditview-class.md), zobrazení, které umožňuje použití architektury dokumentu-zobrazení s bohatě upravenými ovládacími prvky.

- [CScrollView](../../mfc/reference/cscrollview-class.md), zobrazení, které automaticky poskytuje podporu pro posouvání.

- [CTreeView –](../../mfc/reference/ctreeview-class.md), zobrazení, které umožňuje použití architektury dokumentu-zobrazení s ovládacími prvky stromové struktury.

Třída `CView` má také odvozenou implementační třídu s názvem `CPreviewView`, kterou používá rozhraní k provedení náhledu tisku. Tato třída poskytuje podporu pro funkce, které jsou jedinečné pro okno náhledu tisku, jako je například panel nástrojů, náhled s jednou nebo dvojitou stránkou a přiblížení, tj. zvětšení náhledu obrázku. Pokud nechcete implementovat vlastní rozhraní pro náhled tisku (například pokud chcete podporovat úpravy v režimu náhledu tisku), nemusíte volat ani přepisovat žádné členské funkce `CPreviewView`. Další informace o používání `CView`najdete v tématu [Architektura dokumentu/zobrazení](../../mfc/document-view-architecture.md) a [Tisk](../../mfc/printing.md). Další podrobnosti o přizpůsobení náhledu tisku najdete v části [technická Poznámka 30](../../mfc/tn030-customizing-printing-and-print-preview.md) .

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CView`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="cview"></a>CView:: CView

Vytvoří objekt `CView`.

```
CView();
```

### <a name="remarks"></a>Poznámky

Rozhraní volá konstruktor při vytvoření nového okna rámce nebo rozdělení okna. Přepište členskou funkci [OnInitialUpdate](#oninitialupdate) pro inicializaci zobrazení po připojení dokumentu.

##  <a name="doprepareprinting"></a>CView::D oPreparePrinting

Voláním této funkce z přepsání [OnPreparePrinting](#onprepareprinting) vyvoláte dialogové okno Tisk a vytvoříte kontext zařízení tiskárny.

```
BOOL DoPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*pInfo*<br/>
Odkazuje na strukturu [CPrintInfo –](../../mfc/reference/cprintinfo-structure.md) , která popisuje aktuální tiskovou úlohu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud může začít tisk nebo náhled tisku; 0, pokud byla operace zrušena.

### <a name="remarks"></a>Poznámky

Chování této funkce závisí na tom, zda je volána pro tisk nebo náhled tisku (určené `m_bPreview`m členem parametru *pInfo* ). Pokud se soubor tiskne, tato funkce vyvolá dialogové okno Tisk s použitím hodnot ve struktuře [CPrintInfo –](../../mfc/reference/cprintinfo-structure.md) , na kterou *pInfo* odkazuje; poté, co uživatel zavře dialogové okno, funkce vytvoří kontext zařízení tiskárny na základě nastavení uživatele zadaného v dialogovém okně a vrátí tento kontext zařízení pomocí parametru *pInfo* . Tento kontext zařízení slouží k tisku dokumentu.

Pokud se zobrazí náhled souboru, tato funkce vytvoří kontext zařízení tiskárny pomocí aktuálního nastavení tiskárny. Tento kontext zařízení se používá pro simulaci tiskárny během verze Preview.

##  <a name="getdocument"></a>CView:: GetDocument

Voláním této funkce získáte ukazatel na dokument zobrazení.

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [objektu CDocument](../../mfc/reference/cdocument-class.md) přidružený k zobrazení. Hodnota NULL, pokud zobrazení není připojeno k dokumentu.

### <a name="remarks"></a>Poznámky

To umožňuje volat členské funkce dokumentu.

##  <a name="isselected"></a>CView:: s volbou

Volá se rozhraním, aby se zkontrolovalo, jestli zadaná položka dokumentu je vybraná.

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>Parametry

*pDocItem*<br/>
Odkazuje na testovaná položku dokumentu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je vybrána zadaná položka dokumentu; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce vrátí hodnotu FALSE. Tuto funkci můžete přepsat, Pokud implementujete výběr pomocí objektů [CDocItem](../../mfc/reference/cdocitem-class.md) . Pokud vaše zobrazení obsahuje položky OLE, je nutné tuto funkci přepsat.

##  <a name="onactivateframe"></a>CView:: OnActivateFrame

Volá se rozhraním, když se aktivuje nebo deaktivuje okno rámce obsahující zobrazení.

```
virtual void OnActivateFrame(
    UINT nState,
    CFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>Parametry

*nInformace*<br/>
Určuje, zda je okno rámce aktivováno nebo dezaktivováno. Může to být jedna z následujících hodnot:

- WA_INACTIVE dojde k deaktivaci okna rámce.

- WA_ACTIVE okno rámce je aktivováno pomocí jiné metody než kliknutí myší (například pomocí rozhraní klávesnice pro výběr okna).

- WA_CLICKACTIVE okno rámce je aktivováno kliknutím myši

*pFrameWnd*<br/>
Ukazatel na okno rámce, které má být aktivováno.

### <a name="remarks"></a>Poznámky

Tuto členskou funkci přepište, pokud chcete provádět zvláštní zpracování, když je okno rámce přidružené k zobrazení aktivováno nebo dezaktivováno. Například [CFormView](../../mfc/reference/cformview-class.md) provede toto přepsání při uložení a obnovení ovládacího prvku, který má fokus.

##  <a name="onactivateview"></a>CView:: OnActivateView

Volá se rozhraním, když se aktivuje nebo deaktivuje zobrazení.

```
virtual void OnActivateView(
    BOOL bActivate,
    CView* pActivateView,
    CView* pDeactiveView);
```

### <a name="parameters"></a>Parametry

*bActivate*<br/>
Označuje, zda se zobrazení aktivuje nebo deaktivuje.

*pActivateView*<br/>
Odkazuje na objekt zobrazení, který se aktivuje.

*pDeactiveView*<br/>
Odkazuje na objekt zobrazení, který je deaktivovaný.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce nastaví fokus na zobrazení, které se aktivuje. Tuto funkci potlačíte, pokud chcete provádět zvláštní zpracování, když je zobrazení aktivováno nebo dezaktivováno. Například pokud chcete poskytnout speciální vizuální pomůcky, které odlišují aktivní zobrazení z neaktivních zobrazení, prověřte parametr *bActivate* a odpovídajícím způsobem aktualizuje vzhled zobrazení.

Parametry *pActivateView* a *pDeactiveView* odkazují na stejné zobrazení, pokud je okno hlavního rámce aplikace aktivováno bez změny v aktivním zobrazení – například pokud je fokus převáděn z jiné aplikace na tento, nikoli z jednoho zobrazení do jiného v rámci aplikace nebo při přepínání mezi podřízenými okny MDI. V případě potřeby to umožňuje zobrazení své palety znovu realizovat.

Tyto parametry se liší při volání metody [CFrameWnd:: SetActiveView](../../mfc/reference/cframewnd-class.md#setactiveview) se zobrazením, které se liší od toho, co [CFrameWnd:: GetActiveView](../../mfc/reference/cframewnd-class.md#getactiveview) vrátí. K tomu dochází nejčastěji s rozdělovačem okna.

##  <a name="onbeginprinting"></a>CView:: OnBeginPrinting

Volá se rozhraním na začátku úlohy tisku nebo náhledu tisku po volání `OnPreparePrinting`.

```
virtual void OnBeginPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*Emulátor*<br/>
Odkazuje na kontext zařízení tiskárny.

*pInfo*<br/>
Odkazuje na strukturu [CPrintInfo –](../../mfc/reference/cprintinfo-structure.md) , která popisuje aktuální tiskovou úlohu.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce neprovede žádnou akci. Tuto funkci popište, pokud chcete přidělit jakékoli prostředky GDI, jako jsou například pera nebo písma, které jsou potřeba pro tisk. Vyberte objekty GDI do kontextu zařízení v rámci funkce pro [Tisk](#onprint) členské služby pro každou stránku, která je používá. Pokud používáte stejný objekt zobrazení k provádění zobrazení a tisku, použijte samostatné proměnné pro prostředky GDI potřebné pro každé zobrazení. To vám umožní aktualizovat obrazovku během tisku.

Tuto funkci můžete také použít k provedení inicializací, které závisí na vlastnostech kontextu zařízení tiskárny. Například počet stránek potřebných k tisku dokumentu může záviset na nastavení, které uživatel zadal v dialogovém okně Tisk (například délka stránky). V takové situaci nemůžete zadat délku dokumentu ve členské funkci [OnPreparePrinting](#onprepareprinting) , kde byste to normálně provedli. na základě nastavení dialogového okna musíte počkat, až se vytvoří kontext zařízení tiskárny. [OnBeginPrinting](#onbeginprinting) je první přepisovatelných funkcí, která poskytuje přístup k objektu [CDC](../../mfc/reference/cdc-class.md) představujícímu kontext zařízení tiskárny, takže můžete nastavit délku dokumentu z této funkce. Všimněte si, že pokud v tomto čase není Zadaná délka dokumentu, během tisku náhledu se nezobrazí posuvník.

##  <a name="ondragenter"></a>CView:: OnDragEnter

Volá se rozhraním, když ukazatel myši nejdřív vstoupí do oblasti bez posunutí cílového okna přetažení.

```
virtual DROPEFFECT OnDragEnter(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pDataObject*<br/>
Odkazuje na [COleDataObject](../../mfc/reference/coledataobject-class.md) přetažené do odkládací oblasti zobrazení.

*dwKeyState*<br/>
Obsahuje stav modifikačních kláves. Jedná se o kombinaci libovolného počtu následujících: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON a MK_RBUTTON.

*Vyberte*<br/>
Aktuální pozice myši relativní vzhledem ke klientské oblasti zobrazení

### <a name="return-value"></a>Návratová hodnota

Hodnota z DROPEFFECT výčtového typu, který označuje typ vyřazení, ke kterému by došlo, pokud uživatel objekt na této pozici vynechá. Typ přetažení obvykle závisí na aktuálním stavu klíče, který je určen v *dwKeyState*. Standardní mapování stavů DROPEFFECT je na tyto hodnoty:

- DROPEFFECT_NONE datový objekt nelze v tomto okně vyřadit.

- DROPEFFECT_LINK pro MK_CONTROL &#124; MK_SHIFT vytvoří propojení mezi objektem a jeho serverem.

- DROPEFFECT_COPY pro MK_CONTROL vytvoří kopii vynechaného objektu.

- DROPEFFECT_MOVE pro MK_ALT vytvoří kopii vynechaného objektu a odstraní původní objekt. Obvykle se jedná o výchozí efekt přetažení, když zobrazení může přijmout tento datový objekt.

Další informace najdete v tématu Sample [OCLIENT](../../overview/visual-cpp-samples.md)knihovny MFC – pokročilé koncepty.

### <a name="remarks"></a>Poznámky

Výchozí implementace je neprovádět nic a vracet DROPEFFECT_NONE.

Přepište tuto funkci, abyste se připravili na budoucí volání členské funkce [OnDragOver](#ondragover) . Všechna data požadovaná z datového objektu by měla být v tuto chvíli načtena pro pozdější použití ve členské funkci `OnDragOver`. V tuto chvíli by se mělo aktualizovat zobrazení, aby uživatel mohl poskytnout zpětnou vazbu na vizuál. Další informace najdete v článku [přetažení OLE pomocí přetažení: implementace cíle přetažení](../../mfc/drag-and-drop-ole.md#implement-a-drop-target).

##  <a name="ondragleave"></a>CView:: OnDragLeave

Volá se rozhraním během operace přetažení, když se myš přesune mimo platnou oblast přetažení pro toto okno.

```
virtual void OnDragLeave();
```

### <a name="remarks"></a>Poznámky

Tuto funkci můžete přepsat, pokud aktuální zobrazení potřebuje vyčistit všechny akce prováděné během volání [OnDragEnter](#ondragenter) nebo [OnDragOver](#ondragover) , jako je odebrání jakékoli zpětné vazby vizuálního uživatele, když se objekt přetáhl a vynechá.

##  <a name="ondragover"></a>CView:: OnDragOver

Volá se rozhraním během operace přetažení, když se myš přesune přes cílové okno přetažení.

```
virtual DROPEFFECT OnDragOver(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pDataObject*<br/>
Odkazuje na [COleDataObject](../../mfc/reference/coledataobject-class.md) přetažené přes cíl přetažení.

*dwKeyState*<br/>
Obsahuje stav modifikačních kláves. Jedná se o kombinaci libovolného počtu následujících: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON a MK_RBUTTON.

*Vyberte*<br/>
Aktuální pozice myši relativní vzhledem k oblasti zobrazení klienta.

### <a name="return-value"></a>Návratová hodnota

Hodnota z DROPEFFECT výčtového typu, který označuje typ vyřazení, ke kterému by došlo, pokud uživatel objekt na této pozici vynechá. Typ přetažení často závisí na aktuálním stavu klíče, jak je uvedeno v *dwKeyState*. Standardní mapování stavů DROPEFFECT je na tyto hodnoty:

- DROPEFFECT_NONE datový objekt nelze v tomto okně vyřadit.

- DROPEFFECT_LINK pro MK_CONTROL &#124; MK_SHIFT vytvoří propojení mezi objektem a jeho serverem.

- DROPEFFECT_COPY pro MK_CONTROL vytvoří kopii vynechaného objektu.

- DROPEFFECT_MOVE pro MK_ALT vytvoří kopii vynechaného objektu a odstraní původní objekt. Toto je obvykle výchozí efekt odtažení, když zobrazení může přijmout datový objekt.

Další informace najdete v tématu Sample [OCLIENT](../../overview/visual-cpp-samples.md)knihovny MFC – pokročilé koncepty.

### <a name="remarks"></a>Poznámky

Výchozí implementace je neprovádět nic a vracet DROPEFFECT_NONE.

Potlačením této funkce udělíte uživateli vizuální zpětnou vazbu během operace přetažení. Vzhledem k tomu, že tato funkce je volána průběžně, jakýkoli kód obsažený v něm by měl být optimalizován co nejvíce. Další informace najdete v článku [přetažení OLE pomocí přetažení: implementace cíle přetažení](../../mfc/drag-and-drop-ole.md#implement-a-drop-target).

##  <a name="ondragscroll"></a>CView:: OnDragScroll

Volá se rozhraním, než se zavolá [OnDragEnter](#ondragenter) nebo [OnDragOver](#ondragover) , aby se zjistilo, jestli je bod v oblasti posouvání.

```
virtual DROPEFFECT OnDragScroll(
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*dwKeyState*<br/>
Obsahuje stav modifikačních kláves. Jedná se o kombinaci libovolného počtu následujících: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON a MK_RBUTTON.

*Vyberte*<br/>
Obsahuje umístění kurzoru v pixelech vzhledem k obrazovce.

### <a name="return-value"></a>Návratová hodnota

Hodnota z DROPEFFECT výčtového typu, který označuje typ vyřazení, ke kterému by došlo, pokud uživatel objekt na této pozici vynechá. Typ přetažení obvykle závisí na aktuálním stavu klíče, který je určen v *dwKeyState*. Standardní mapování stavů DROPEFFECT je na tyto hodnoty:

- DROPEFFECT_NONE datový objekt nelze v tomto okně vyřadit.

- DROPEFFECT_LINK pro MK_CONTROL &#124; MK_SHIFT vytvoří propojení mezi objektem a jeho serverem.

- DROPEFFECT_COPY pro MK_CONTROL vytvoří kopii vynechaného objektu.

- DROPEFFECT_MOVE pro MK_ALT vytvoří kopii vynechaného objektu a odstraní původní objekt.

- DROPEFFECT_SCROLL označuje, že v cílovém zobrazení dojde k operaci přetáhnutí nebo k ní dochází.

Další informace najdete v tématu Sample [OCLIENT](../../overview/visual-cpp-samples.md)knihovny MFC – pokročilé koncepty.

### <a name="remarks"></a>Poznámky

Tuto funkci popište, pokud chcete pro tuto událost zadat zvláštní chování. Výchozí implementace automaticky posouvá okna, když je kurzor přetažen do výchozí oblasti posunu uvnitř ohraničení každého okna. Další informace najdete v článku [přetažení OLE pomocí přetažení: implementace cíle přetažení](../../mfc/drag-and-drop-ole.md#implement-a-drop-target).

##  <a name="ondraw"></a>CView:: Draw

Volá se rozhraním, aby se vykreslila image dokumentu.

```
virtual void OnDraw(CDC* pDC) = 0;
```

### <a name="parameters"></a>Parametry

*Emulátor*<br/>
Odkazuje na kontext zařízení, který se má použít pro vykreslování obrázku dokumentu.

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto funkci, aby zobrazila obrazovky, tisk a náhled tisku a v každém případě předává jiný kontext zařízení. Neexistuje žádná výchozí implementace.

Chcete-li zobrazit zobrazení dokumentu, je nutné tuto funkci přepsat. Volání GDI (Graphics Interface Interface) můžete využít pomocí objektu [CDC](../../mfc/reference/cdc-class.md) , na který odkazuje parametr *řadiče domény* . Před kreslením můžete vybrat prostředky GDI, například pera nebo písma, do kontextu zařízení a pak je zrušit. Váš kód kresby může být často nezávislý na zařízení; To znamená, že nepotřebuje informace o tom, jaký typ zařízení zobrazuje obrázek.

Pro optimalizaci vykreslování volejte členskou funkci [RectVisible](../../mfc/reference/cdc-class.md#rectvisible) kontextu zařízení, abyste zjistili, zda bude daný obdélník vykreslen. Pokud potřebujete rozlišovat normální zobrazení a tisk obrazovky, zavolejte funkci pro [Tisk](../../mfc/reference/cdc-class.md#isprinting) členů kontextu zařízení.

##  <a name="ondrop"></a>CView:: Drop drop

Volá se rozhraním, když uživatel uvolní datový objekt přes platný cíl přetažení.

```
virtual BOOL OnDrop(
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>Parametry

' pDataObject * odkazuje na [COleDataObject](../../mfc/reference/coledataobject-class.md) , který je vyřazen do cílového umístění.

*dropEffect*<br/>
Efekt přetažení, který uživatel požadoval.

- DROPEFFECT_COPY vytvoří kopii datového objektu, který se vynechává.

- DROPEFFECT_MOVE přesune datový objekt do aktuálního umístění myši.

- DROPEFFECT_LINK vytvoří propojení mezi datovým objektem a jeho serverem.

*Vyberte*<br/>
Aktuální pozice myši relativní vzhledem k oblasti zobrazení klienta.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo přetažení úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Výchozí implementace neprovede žádnou akci a vrátí hodnotu FALSE.

Přepište tuto funkci, aby se naimplementoval účinek OLE přetažení do klientské oblasti zobrazení. Datový objekt lze prozkoumat pomocí *pDataObject* pro formáty dat schránky a data vynechaná v zadaném bodě.

> [!NOTE]
>  Rozhraní nevolá tuto funkci, pokud existuje přepsání pro [OnDropEx](#ondropex) v této třídě zobrazení.

##  <a name="ondropex"></a>CView:: OnDropEx

Volá se rozhraním, když uživatel uvolní datový objekt přes platný cíl přetažení.

```
virtual DROPEFFECT OnDropEx(
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pDataObject*<br/>
Odkazuje na [COleDataObject](../../mfc/reference/coledataobject-class.md) , který je vyřazený do cílového umístění.

*dropDefault*<br/>
Efekt, který uživatel zvolil pro výchozí operaci přetažení založenou na aktuálním stavu klíče. Může být DROPEFFECT_NONE. Efekty přetažení jsou popsány v části poznámky.

*Seznamu*<br/>
Seznam efektů přetažení, které podporuje zdroj přetažení. Hodnoty efektu přetažení lze kombinovat pomocí operace bitového **&#124;** operátoru OR (). Efekty přetažení jsou popsány v části poznámky.

*Vyberte*<br/>
Aktuální pozice myši relativní vzhledem k oblasti zobrazení klienta.

### <a name="return-value"></a>Návratová hodnota

Efekt odtažení, který vyplynule z pokusu o zrušení v umístění určeném *bodem*. Musí se jednat o jednu z hodnot uvedených v *dropEffectList*. Efekty přetažení jsou popsány v části poznámky.

### <a name="remarks"></a>Poznámky

Výchozí implementací je Neprovádět žádnou akci a vracet fiktivní hodnotu (-1), která označuje, že by měl rozhraní zavolat obslužnou rutinu [drop](#ondrop) .

Přepište tuto funkci, aby se naimplementoval efekt pravého tlačítka myši a přetažení myší. Stisknutí pravého tlačítka myši na tlačítko a při uvolnění pravého tlačítka myši obvykle zobrazí nabídku voleb.

Vaše přepsání `OnDropEx` by mělo dotaz na pravé tlačítko myši. Můžete volat [GetKeyState](/windows/win32/api/winuser/nf-winuser-getkeystate) nebo uložit pravý stav tlačítka myši z obslužné rutiny [OnDragEnter](#ondragenter) .

- Pokud je pravé tlačítko myši vypnuté, vaše přepsání by mělo zobrazit místní nabídku, která nabízí efekty odtažení, které podporuje.

   - Projděte *si rozevírací seznam* a určete efekty odtažení podporované zdrojem přetažení. Povolte pouze tyto akce v místní nabídce.

   - Pomocí [SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem) nastavte výchozí akci založenou na *dropDefault*.

   - Nakonec proveďte akci určenou uživatelem výběr z místní nabídky.

- Pokud pravé tlačítko myši není vypnuté, přepsání by se mělo zpracovat jako požadavek na standardní vyřazení. Použijte efekt odtažení určený v *dropDefault*. Alternativně může vaše přepsání vracet fiktivní hodnotu (-1), která indikuje, že `OnDrop` tuto operaci přetažení zpracuje.

Použijte *pDataObject* k prohlédnutí `COleDataObject` pro formát dat schránky a data vynechaná v zadaném bodě.

Efekty přetažení popisují akci přidruženou k operaci drop. Podívejte se na následující seznam efektů přetažení:

- DROPEFFECT_NONE nebudete moct vynechat.

- DROPEFFECT_COPY bude provedena operace kopírování.

- DROPEFFECT_MOVE bude provedena operace přesunutí.

- Bylo navázáno DROPEFFECT_LINK odkaz z vynechaných dat na původní data.

- DROPEFFECT_SCROLL označuje, že v cíli dojde k operaci přetažení, nebo k ní dochází.

Další informace o nastavení příkazu výchozí nabídky najdete v tématu [SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem) v Windows SDK a [CMenu –:: GetSafeHmenu](../../mfc/reference/cmenu-class.md#getsafehmenu) v tomto svazku.

##  <a name="onendprinting"></a>CView:: OnEndPrinting

Volá se rozhraním po vytištění nebo zobrazení náhledu dokumentu.

```
virtual void OnEndPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*Emulátor*<br/>
Odkazuje na kontext zařízení tiskárny.

*pInfo*<br/>
Odkazuje na strukturu [CPrintInfo –](../../mfc/reference/cprintinfo-structure.md) , která popisuje aktuální tiskovou úlohu.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce neprovede žádnou akci. Přepište tuto funkci, pokud chcete uvolnit všechny prostředky GDI, které jste přidělili v členské funkci [OnBeginPrinting](#onbeginprinting) .

##  <a name="onendprintpreview"></a>CView:: OnEndPrintPreview

Volá se rozhraním, když uživatel ukončí režim náhledu tisku.

```
virtual void OnEndPrintPreview(
    CDC* pDC,
    CPrintInfo* pInfo,
    POINT point,
    CPreviewView* pView);
```

### <a name="parameters"></a>Parametry

*Emulátor*<br/>
Odkazuje na kontext zařízení tiskárny.

*pInfo*<br/>
Odkazuje na strukturu [CPrintInfo –](../../mfc/reference/cprintinfo-structure.md) , která popisuje aktuální tiskovou úlohu.

*Vyberte*<br/>
Určuje bod na stránce, který byl naposledy zobrazen v režimu náhledu.

*pView*<br/>
Odkazuje na objekt zobrazení používaný pro náhled.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce volá členskou funkci [OnEndPrinting](#onendprinting) a obnoví hlavní okno rámce do stavu před zahájením náhledu tisku. Přepište tuto funkci, aby se při ukončení režimu náhledu provádělo zvláštní zpracování. Například pokud chcete zachovat pozici uživatele v dokumentu při přepnutí z režimu náhledu do normálního režimu zobrazení, můžete přejít na pozici popsanou parametrem *Point* a `m_nCurPage` členem struktury `CPrintInfo`, na kterou parametr *pInfo* odkazuje.

Vždy volejte verzi `OnEndPrintPreview` základní třídy z přepsání, obvykle na konci funkce.

##  <a name="oninitialupdate"></a>CView:: OnInitialUpdate

Volá se rozhraním po prvním připojení zobrazení k dokumentu, ale před tím, než se zobrazení zpočátku zobrazí.

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce volá členskou funkci [aktualizovat](#onupdate) bez informací nápovědy (to znamená použití výchozích hodnot 0 pro parametr *lHint* a hodnota null pro parametr *pHint* ). Přepište tuto funkci, pokud chcete provést jednorázovou inicializaci, která vyžaduje informace o dokumentu. Například pokud má vaše aplikace dokumenty s pevnou velikostí, můžete tuto funkci použít k inicializaci omezení posouvání zobrazení na základě velikosti dokumentu. Pokud vaše aplikace podporuje dokumenty s proměnlivou velikostí, [použijte k aktualizaci](#onupdate) limitů posouvání pokaždé, když se dokument změní.

##  <a name="onpreparedc"></a>CView:: OnPrepareDC

Volá se rozhraním, než se volá členská funkce pro [vykreslení](#ondraw) pro zobrazení obrazovky a před voláním členské funkce pro [Tisk](#onprint) pro každou stránku během tisku nebo náhledu tisku.

```
virtual void OnPrepareDC(
    CDC* pDC,
    CPrintInfo* pInfo = NULL);
```

### <a name="parameters"></a>Parametry

*Emulátor*<br/>
Odkazuje na kontext zařízení, který se má použít pro vykreslování obrázku dokumentu.

*pInfo*<br/>
Odkazuje na strukturu [CPrintInfo –](../../mfc/reference/cprintinfo-structure.md) , která popisuje aktuální tiskovou úlohu, pokud je `OnPrepareDC` volána pro tisk nebo náhled tisku. člen `m_nCurPage` Určuje stránku, která se má vytisknout. Pokud je `OnPrepareDC` volána pro zobrazení obrazovky, má tento parametr hodnotu NULL.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce neprovede žádnou akci, pokud je funkce volána pro zobrazení obrazovky. Tato funkce je však přepsána v odvozených třídách, jako je například [CScrollView](../../mfc/reference/cscrollview-class.md), pro úpravu atributů kontextu zařízení; v důsledku toho byste měli vždy volat implementaci základní třídy na začátku svého přepsání.

Pokud je funkce volána pro tisk, výchozí implementace prověřuje informace stránky uložené v parametru *pInfo* . Pokud nebyla zadána délka dokumentu, `OnPrepareDC` předpokládá, že dokument bude delší než jedna stránka, a zastaví tiskovou smyčku po vytištění jedné stránky. Funkce zastaví tiskovou smyčku nastavením `m_bContinuePrinting` člena struktury na hodnotu FALSE.

`OnPrepareDC` přepište z některého z následujících důvodů:

- Pro úpravu atributů kontextu zařízení, jak je potřeba pro zadanou stránku. Pokud například potřebujete nastavit režim mapování nebo jiné charakteristiky kontextu zařízení, udělejte to v této funkci.

- K provádění stránkování v době tisku. Při zahájení tisku obvykle zadáte délku dokumentu pomocí členské funkce [OnPreparePrinting](#onprepareprinting) . Pokud ale nevíte předem, jak dlouho je dokument (například při tisku neurčeného počtu záznamů z databáze), přepište `OnPrepareDC` k testování konce dokumentu během jeho tisku. Pokud není k dispozici žádný dokument k vytištění, nastavte člena `m_bContinuePrinting` struktury `CPrintInfo` na hodnotu NEPRAVDA.

- Odeslání řídicích kódů na tiskárně na základě stránky. Chcete-li odeslat řídicí kódy z `OnPrepareDC`, zavolejte členskou funkci `Escape` parametru *primárního řadiče domény* .

Na začátku přepsání volejte verzi `OnPrepareDC` základní třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#183](../../mfc/codesnippet/cpp/cview-class_1.cpp)]

##  <a name="onprepareprinting"></a>CView:: OnPreparePrinting

Volá se rozhraním, než se dokument vytiskne nebo zobrazí náhled.

```
virtual BOOL OnPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*pInfo*<br/>
Odkazuje na strukturu [CPrintInfo –](../../mfc/reference/cprintinfo-structure.md) , která popisuje aktuální tiskovou úlohu.

### <a name="return-value"></a>Návratová hodnota

Nenulové pro zahájení tisku; 0, Pokud tisková úloha byla zrušena.

### <a name="remarks"></a>Poznámky

Výchozí implementace neprovádí žádnou akci.

Tuto funkci musíte přepsat, pokud chcete povolit tisk a náhled tisku. Zavolejte členskou funkci [DoPreparePrinting](#doprepareprinting) , předejte jí parametr *pInfo* a pak vraťte svou návratovou hodnotu; `DoPreparePrinting` zobrazí dialogové okno Tisk a vytvoří kontext zařízení tiskárny. Chcete-li inicializovat dialogové okno Tisk s jinými hodnotami než výchozími, přiřaďte hodnoty členům *pInfo*. Například pokud znáte délku dokumentu, před voláním `DoPreparePrinting`předejte hodnotu členské funkci [SetMaxPage](../../mfc/reference/cprintinfo-structure.md#setmaxpage) *pInfo* . Tato hodnota se zobrazí v poli do: v části rozsah v dialogovém okně Tisk.

`DoPreparePrinting` nezobrazuje dialogové okno Tisk pro úlohu ve verzi Preview. Chcete-li obejít dialogové okno Tisk pro tiskovou úlohu, zkontrolujte, zda je `m_bPreview` člen *PINFO* false, a poté jej nastavte na hodnotu true, než jej předáte do `DoPreparePrinting`. Resetujte ho na FALSE později.

Pokud potřebujete provést inicializace, které vyžadují přístup k objektu `CDC` reprezentujícím kontext zařízení tiskárny (například pokud potřebujete znát velikost stránky před zadáním délky dokumentu), přepište členskou funkci `OnBeginPrinting`.

Chcete-li nastavit hodnotu `m_nNumPreviewPages` nebo `m_strPageDesc` členů parametru *pInfo* , udělejte to po volání `DoPreparePrinting`. Členská funkce `DoPreparePrinting` nastaví `m_nNumPreviewPages` na hodnotu nalezenou v aplikaci. Soubor INI a nastaví `m_strPageDesc` na jeho výchozí hodnotu.

### <a name="example"></a>Příklad

  Přepište `OnPreparePrinting` a zavolejte `DoPreparePrinting` z přepsání, aby se v rozhraní zobrazilo dialogové okno Tisk a pro vás vytvořila řadič domény tiskárny.

[!code-cpp[NVC_MFCDocView#184](../../mfc/codesnippet/cpp/cview-class_2.cpp)]

Pokud víte, kolik stránek dokument obsahuje, nastavte před voláním `DoPreparePrinting`na stránce `OnPreparePrinting` maximum. Rozhraní zobrazí maximální číslo stránky v poli "do" v dialogovém okně Tisk.

[!code-cpp[NVC_MFCDocView#185](../../mfc/codesnippet/cpp/cview-class_3.cpp)]

##  <a name="onprint"></a>CView:: Print – tisk

Volá se rozhraním pro tisk nebo náhled stránky dokumentu.

```
virtual void OnPrint(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*Emulátor*<br/>
Odkazuje na kontext zařízení tiskárny.

*pInfo*<br/>
Odkazuje na strukturu `CPrintInfo`, která popisuje aktuální tiskovou úlohu.

### <a name="remarks"></a>Poznámky

Pro každou tištěnou stránku volá rozhraní tuto funkci ihned po volání členské funkce [OnPrepareDC](#onpreparedc) . Tištěnou stránku určuje `m_nCurPage` člen struktury [CPrintInfo –](../../mfc/reference/cprintinfo-structure.md) , na kterou *pInfo* odkazuje. Výchozí implementace volá členskou funkci [prodraw](#ondraw) a předá jí kontext zařízení tiskárny.

Tuto funkci můžete přepsat z následujících důvodů:

- Povoluje tisk vícestránkovéch dokumentů. Vykreslit pouze část dokumentu, která odpovídá aktuálně vytisknuté stránky. Pokud používáte `OnDraw` k vykreslování, můžete upravit počátek zobrazení, aby byla vytištěna pouze příslušná část dokumentu.

- Aby vytištěný obrázek vypadal jinak než na obrázku obrazovky (tj. Pokud vaše aplikace není WYSIWYG). Místo předání kontextu zařízení tiskárny `OnDraw`použijte kontext zařízení k vykreslení obrázku pomocí atributů, které nejsou zobrazené na obrazovce.

   Potřebujete-li prostředky GDI pro tisk, které nepoužíváte pro zobrazení obrazovky, vyberte je do kontextu zařízení před kreslením a zrušte jejich výběr později. Tyto prostředky GDI by měly být přiděleny v [OnBeginPrinting](#onbeginprinting) a vydané v [OnEndPrinting](#onendprinting).

- K implementaci hlaviček nebo zápatí. I nadále můžete k vykreslování použít `OnDraw` omezením oblasti, na kterou může tisknout.

Všimněte si, že `m_rectDraw` člen parametru *pInfo* popisuje tisknutelnou oblast stránky v logických jednotkách.

Nevolejte `OnPrepareDC` v přepsání `OnPrint`; rozhraní volá `OnPrepareDC` automaticky před voláním `OnPrint`.

### <a name="example"></a>Příklad

Následuje kostra pro přepsanou funkci `OnPrint`:

[!code-cpp[NVC_MFCDocView#186](../../mfc/codesnippet/cpp/cview-class_4.cpp)]

Další příklad naleznete v tématu [CRichEditView –::P rintinsiderect](../../mfc/reference/cricheditview-class.md#printinsiderect).

##  <a name="onscroll"></a>CView:: Scroll

Volá se rozhraním, aby se určilo, jestli je možné posouvání.

```
virtual BOOL OnScroll(
    UINT nScrollCode,
    UINT nPos,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parametry

*nScrollCode*<br/>
Kód posuvníku, který označuje požadavek na posunutí uživatele. Tento parametr se skládá ze dvou částí: bajt nízkého řádu, který určuje typ posouvání, ke kterému dochází vodorovně, a horní bajt, který určuje typ posouvání, ke kterému dochází vertikálně:

- SB_BOTTOM posouvá se dolů.

- SB_LINEDOWN posouvá jeden řádek dolů.

- SB_LINEUP posouvá o jeden řádek nahoru.

- SB_PAGEDOWN posouvá jednu stránku dolů.

- SB_PAGEUP posouvá o jednu stránku nahoru.

- SB_THUMBTRACK přetáhne posuvník na určenou pozici. Aktuální pozice je určena v *nPos*.

- SB_TOP posouvá na začátek.

*nPos*<br/>
Obsahuje aktuální pozici posouvání, pokud je kód posuvníku SB_THUMBTRACK. v opačném případě se nepoužívá. V závislosti na počátečním rozsahu posouvání může být *nPos* záporný a v případě potřeby by měl být převeden na **int** .

*bDoScroll*<br/>
Určuje, zda by měla být skutečně provedena zadaná akce posouvání. Je-li nastavena hodnota TRUE, je třeba probíhat posouvání; v případě hodnoty FALSE by neměl probíhat posouvání.

### <a name="return-value"></a>Návratová hodnota

Pokud má *bDoScroll* hodnotu true a zobrazení se ve skutečnosti posouvá a vrátí nenulovou hodnotu; v opačném případě 0. Pokud má *bDoScroll* hodnotu false, vrátí hodnotu, kterou jste vrátili v případě, že *bDoScroll* byla pravdivá, i když se vám neudělá ve skutečnosti posouvání.

### <a name="remarks"></a>Poznámky

V jednom případě je tato funkce volána rozhraním s *bDoScroll* nastavenou na hodnotu true, když zobrazení obdrží zprávu ScrollBar. V takovém případě byste měli zobrazení ve skutečnosti posouvat. V opačném případě je tato funkce volána s *bDoScroll* nastavenou na hodnotu false v případě, že je původně přetažena položka OLE do oblasti automatického posouvání cíle přetažení, ještě než dojde ke skutečnému posouvání. V takovém případě byste toto zobrazení neměli ve skutečnosti posouvat.

##  <a name="onscrollby"></a>CView:: OnScrollBy

Volá se rozhraním, když uživatel zobrazuje oblast za aktuálním zobrazením dokumentu, a to buď přetažením položky OLE na aktuální hranici zobrazení, nebo pomocí svislých nebo vodorovných posuvníků.

```
virtual BOOL OnScrollBy(
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parametry

*sizeScroll*<br/>
Počet pixelů, které byly posunuty vodorovně a svisle.

*bDoScroll*<br/>
Určuje, zda dojde k posunu zobrazení. Je-li nastavena hodnota TRUE, dojde k posunu. je-li nastavena hodnota false, nebude k rolování.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo zobrazení možné procházet; v opačném případě 0.

### <a name="remarks"></a>Poznámky

V odvozených třídách Tato metoda kontroluje, zda je zobrazení možné procházet ve směru požadovaného uživatelem, a v případě potřeby aktualizuje novou oblast. Tato funkce je automaticky volána pomocí [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) a [CWnd:: OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) , aby se mohla provést skutečná žádost o posouvání.

Výchozí implementace této metody nezmění zobrazení, ale pokud není volána, zobrazení se neposune v `CScrollView`odvozené třídy.

Pokud šířka nebo výška dokumentu překračuje 32767 pixelů, posuny v posledních 32767 selžou, protože `OnScrollBy` je volána s neplatným argumentem *sizeScroll* .

##  <a name="onupdate"></a>CView:: inupdate

Volá se rozhraním po úpravě dokumentu zobrazení. Tato funkce je volána funkcí [objektu CDocument:: UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) a umožňuje zobrazení aktualizovat zobrazení tak, aby odráželo tyto úpravy.

```
virtual void OnUpdate(
    CView* pSender,
    LPARAM lHint,
    CObject* pHint);
```

### <a name="parameters"></a>Parametry

*pSender*<br/>
Odkazuje na zobrazení, které upravilo dokument, nebo hodnotu NULL, pokud mají být aktualizována všechna zobrazení.

*lHint*<br/>
Obsahuje informace o úpravách.

*pHint*<br/>
Odkazuje na objekt, který ukládá informace o změnách.

### <a name="remarks"></a>Poznámky

Je také volána výchozí implementací [OnInitialUpdate](#oninitialupdate). Výchozí implementace zruší platnost celé klientské oblasti a označí ji pro malování při přijetí další WM_PAINT zprávy. Tuto funkci přepište, pokud chcete aktualizovat pouze ty oblasti, které jsou mapovány na upravené části dokumentu. K tomu musíte předat informace o změnách pomocí parametrů pomocného parametru.

Chcete-li použít *lHint*, definujte speciální hodnoty nápovědy, obvykle bitovou masku nebo Výčtový typ a popište, aby dokument předal jednu z těchto hodnot. Chcete-li použít *pHint*, odvodit třídu Hint z [CObject](../../mfc/reference/cobject-class.md) a nechat dokument předat ukazatel na objekt nápovědy; Při přepsání `OnUpdate`použijte členskou funkci [CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof) k určení typu modulu runtime objektu Hint.

Obvykle byste neměli provádět žádné kresby přímo z `OnUpdate`. Místo toho určete obdélník popisující v souřadnicích zařízení, oblast, která vyžaduje aktualizaci. předat tento obdélník do [CWnd:: InvalidateRect](../../mfc/reference/cwnd-class.md#invalidaterect). To způsobí, že při příštím přijetí [WM_PAINT](/windows/win32/gdi/wm-paint) zprávy dojde k malování.

Pokud je *lHint* 0 a *pHint* má hodnotu null, dokument odeslal oznámení o obecné aktualizaci. Pokud zobrazení obdrží oznámení o obecné aktualizaci, nebo pokud nemůže dekódovat doporučení, měla by zrušit platnost celé klientské oblasti.

## <a name="see-also"></a>Viz také

[MDIDOCVW Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[CFrameWnd – třída](../../mfc/reference/cframewnd-class.md)<br/>
[CSplitterWnd – třída](../../mfc/reference/csplitterwnd-class.md)<br/>
[CDC – třída](../../mfc/reference/cdc-class.md)<br/>
[CDocTemplate – třída](../../mfc/reference/cdoctemplate-class.md)<br/>
[CDocument – třída](../../mfc/reference/cdocument-class.md)
