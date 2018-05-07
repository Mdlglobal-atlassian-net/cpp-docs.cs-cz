---
title: CView – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9ca94e9d1f870fe028faec413a79f13d8a3b8eaa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cview-class"></a>CView – třída
Poskytuje základní funkce pro třídy uživatelem definované zobrazení.  
  
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
|[CView::DoPreparePrinting](#doprepareprinting)|Zobrazí dialogové okno tisku a vytvoří tiskárny kontextu zařízení; volání při přepsání `OnPreparePrinting` – členská funkce.|  
|[CView::GetDocument](#getdocument)|Vrátí dokument přidružené zobrazení.|  
|[CView::IsSelected](#isselected)|Ověřuje, zda je vybraná položka dokumentu. Podpora OLE vyžaduje.|  
|[CView::OnDragEnter](#ondragenter)|Voláno, pokud položka je první přetažen oblasti přetažení myší zobrazení.|  
|[CView::OnDragLeave](#ondragleave)|Volá se při taženou položku opustí oblasti přetažení myší zobrazení.|  
|[CView::OnDragOver](#ondragover)|Volá se při přetažení položku přes oblasti přetažení myší zobrazení.|  
|[CView::OnDragScroll](#ondragscroll)|Voláno k určení, zda je kurzor přetažen Posunout oblast okna.|  
|[CView::OnDrop](#ondrop)|Voláno, pokud byla vyřazena položku do oblasti přetažení myší zobrazení, výchozí obslužnou rutinu.|  
|[CView::OnDropEx](#ondropex)|Voláno, pokud byla vyřazena položku do oblasti přetažení myší zobrazení, primární obslužnou rutinu.|  
|[CView::OnInitialUpdate](#oninitialupdate)|Volá se po zobrazení je nejprve připojen k dokumentu.|  
|[CView::OnPrepareDC](#onpreparedc)|Volá se před `OnDraw` – členská funkce je volána pro zobrazení na obrazovce nebo `OnPrint` – členská funkce je volána pro tisku nebo náhledu.|  
|[CView::OnScroll](#onscroll)|Voláno, když jsou OLE – položky přetáhnout přesahuje hranice zobrazení.|  
|[CView::OnScrollBy](#onscrollby)|Voláno, když je přesunut oblasti zobrazení obsahující položky OLE active na místě.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CView::OnActivateFrame](#onactivateframe)|Voláno, pokud je aktivace nebo deaktivace rámce okna obsahující zobrazení.|  
|[CView::OnActivateView](#onactivateview)|Voláno, když se aktivuje zobrazení.|  
|[CView::OnBeginPrinting](#onbeginprinting)|Volá se, když tiskové úlohy začne; přepsání nastavení za účelem přidělení grafické rozhraní GDI prostředků zařízení.|  
|[CView::OnDraw](#ondraw)|Voláno k vykreslení bitové kopie v dokumentu obrazovky zobrazení, tisku nebo náhledu tisku. Implementace vyžaduje.|  
|[CView::OnEndPrinting](#onendprinting)|Volá se při ukončení tiskové úlohy; přepsání se zrušit přidělení prostředků GDI.|  
|[CView::OnEndPrintPreview](#onendprintpreview)|Voláno, když je byl ukončen režim náhledu.|  
|[CView::OnPreparePrinting](#onprepareprinting)|Voláno před dokumentu je tisku nebo k prohlížení; přepsání nastavení za účelem inicializace dialogové okno tisku.|  
|[CView::OnPrint](#onprint)|Voláno k tisku nebo náhled stránky z dokumentu.|  
|[CView::OnUpdate](#onupdate)|Volá oznámit zobrazení, které bylo jeho dokument upravit.|  
  
## <a name="remarks"></a>Poznámky  
 Zobrazení je připojena k dokumentu a funguje jako zprostředkovatel mezi dokumentu a uživatel: zobrazení vykreslí obrázek dokumentu na obrazovce nebo tiskárny a interpretuje jako operations při dokumentu vstup uživatele.  
  
 Zobrazení je podřízená okně s rámečkem. Více zobrazení můžete sdílet okně s rámečkem, jako v případě rozděleného okna. Vztah mezi zobrazení třídy třídy oken s rámečkem a dokumentové třídy se navazuje `CDocTemplate` objektu. Když uživatel otevře nové okno nebo rozdělí existující jeden rozhraní framework vytvoří nové zobrazení a připojí jej k dokumentu.  
  
 Zobrazení lze připojit pouze jeden dokument, ale dokument může mít více zobrazení, které jsou k němu připojen najednou – například pokud dokument se zobrazí v okně rozdělovače nebo více podřízených oken v aplikaci více rozhraní (MDI) dokumentu. Aplikace může podporovat různé typy zobrazení pro typu daného dokumentu. například může být pro zpracování textu aplikaci dokončení textového zobrazení dokumentu a zobrazení osnovy, které zobrazuje pouze část záhlaví. Tyto různé typy zobrazení mohou být umístěny v oknech s rámečkem samostatné nebo v samostatné podokna okna jeden snímek, pokud používáte rozděleném okně.  
  
 Zobrazení může být zodpovědná za zpracování několika různých typů vstupu, například vstup z klávesnice, myš vstup nebo vstupu pomocí přetahování myší, jakož i příkazy z nabídky, panely nástrojů nebo posuvníky. Zobrazení přijímá příkazy, které jsou předávány podle jeho oken s rámečkem. Pokud zobrazení nezpracovává daného příkazu, předává příkaz jeho přidružené dokumentu. Podobně jako všechny cíle příkazů zobrazení zpracovává zprávy přes mapy zpráv.  
  
 Zodpovídá zobrazení pro zobrazení a úprava data dokumentu, ale ne pro ukládání. Dokument nabízí zobrazení s nezbytné podrobnosti o jeho data. Můžete je nechat přístup k zobrazení, které dokumentu datové členy přímo, nebo může poskytnout členské funkce ve třídě dokumentů pro třídu zobrazení volat.  
  
 Při změně dat dokumentu, zobrazení, která je zodpovědná za změny obvykle volá [CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) funkce pro dokument, který oznámí všechna zobrazení pomocí volání `OnUpdate` – členská funkce pro Každý. Výchozí implementaci `OnUpdate` by způsobila neplatnost zobrazení celého klienta. Je možné přepsat jeho zneplatní pouze tyto oblasti klientské oblasti, které jsou mapovány na změněné části dokumentu.  
  
 Použít `CView`, odvození třídy z něj a implementaci `OnDraw` – členská funkce provést obrazovky zobrazení. Můžete také použít `OnDraw` k tisku a přehled tisku. Rozhraní framework zpracovává tiskové smyčky pro tisk a náhled dokumentu.  
  
 Zobrazení zpracovává zprávy posuvníku s [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) a [CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) členské funkce. Můžete implementovat posuvníku zpracování zpráv v těchto funkcí, nebo můžete použít `CView` odvozené třídy [CScrollView](../../mfc/reference/cscrollview-class.md) pro zpracování posouvání za vás.  
  
 Kromě `CScrollView`, knihovny Microsoft Foundation Class poskytuje devět třídy odvozené z `CView`:  
  
- [CCtrlView](../../mfc/reference/cctrlview-class.md), zobrazení, které umožňuje použití dokument – zobrazení architektura s stromu, seznamu a bohaté ovládacích prvcích pro úpravy.  
  
- [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md), zobrazení, které zobrazuje záznamů databáze v ovládacích prvcích – dialogové okno.  
  
- [CEditView](../../mfc/reference/ceditview-class.md), zobrazení, která poskytuje jednoduché Víceřádkový textový editor. Můžete použít `CEditView` objektu jako ovládací prvek dialogového okna, jakož i zobrazení v dokumentu.  
  
- [Třídy CFormView](../../mfc/reference/cformview-class.md), posouvatelného zobrazení, které obsahuje ovládací prvky dialogového a je založena na prostředku šablony dialogové okno.  
  
- [CListView](../../mfc/reference/clistview-class.md), zobrazení, které umožňuje použití dokumentu - view – architektura s ovládacími prvky seznam.  
  
- [CRecordView](../../mfc/reference/crecordview-class.md), zobrazení, které zobrazuje záznamů databáze v ovládacích prvcích – dialogové okno.  
  
- [Cricheditview –](../../mfc/reference/cricheditview-class.md), zobrazení, které umožňuje použití dokument – zobrazení ovládacích prvcích pro úpravy architektura s formátováním.  
  
- [CScrollView](../../mfc/reference/cscrollview-class.md), zobrazení, která automaticky poskytuje podporu posouvání.  
  
- [CTreeView](../../mfc/reference/ctreeview-class.md), zobrazení, které umožňuje použití dokumentu - view – architektura s ovládacích prvků strom.  
  
 `CView` Třída také obsahuje implementace odvozené třídy s názvem **CPreviewView**, který je využíván jiným rozhraní k zobrazení náhledu tisku. Tato třída poskytuje podporu pro funkce, které jsou jedinečné pro okno náhledu, například panel nástrojů, zobrazení stránek jedním nebo double, a přiblížení a oddálení, který se zvětšení zobrazeného obrazu. Nemusíte volání nebo přepsat kterékoliv **CPreviewView**na členské funkce, pokud chcete implementovat vlastní rozhraní pro náhledu tisku (například pokud chcete zajistit podporu úpravy v režimu náhledu tisku). Další informace o používání `CView`, najdete v části [Document/View – architektura](../../mfc/document-view-architecture.md) a [tisk](../../mfc/printing.md). Kromě toho najdete v části [Technická poznámka 30](../../mfc/tn030-customizing-printing-and-print-preview.md) Další informace o přizpůsobení náhledu tisku.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
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
 Rozhraní framework volá konstruktor při vytvoření nové okně s rámečkem nebo je rozdělit okno. Přepsání [OnInitialUpdate](#oninitialupdate) – členská funkce k inicializaci zobrazení po je dokument připojen.  
  
##  <a name="doprepareprinting"></a>  CView::DoPreparePrinting  
 Volání této funkce z vaší přepsání [OnPreparePrinting –](#onprepareprinting) vyvolat dialogové okno tisku a vytvořit kontextu zařízení tiskárny.  
  
```  
BOOL DoPreparePrinting(CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>Parametry  
 `pInfo`  
 Odkazuje na [cprintinfo –](../../mfc/reference/cprintinfo-structure.md) struktura, která popisuje aktuální tiskové úlohy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud může začít tisku nebo náhledu; 0, pokud operace byla zrušena.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce chování závisí na tom, zda je volána pro tisku nebo náhledu (určená elementem **m_bPreview** členem `pInfo` parametr). Pokud tisku souboru této funkce vyvolá dialogové okno tisku, pomocí hodnoty v [cprintinfo –](../../mfc/reference/cprintinfo-structure.md) struktury, která `pInfo` bodů poté, co uživatel zavřel dialogové okno, funkce vytvoří tiskárny kontextu zařízení na základě nastavení zadané v dialogovém okně vyberte uživatele a vrátí tento kontext zařízení prostřednictvím `pInfo` parametr. Tento kontext zařízení se používá k vytištění dokumentu.  
  
 Pokud soubor prohlíženého, tato funkce vytvoří kontextu zařízení tiskárny pomocí aktuálního nastavení tiskárny; Tento kontext zařízení se používá pro simulaci tiskárny verzi Preview.  
  
##  <a name="getdocument"></a>  CView::GetDocument  
 Volání této funkce získání ukazatele zobrazení dokumentu.  
  
```  
CDocument* GetDocument() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CDocument](../../mfc/reference/cdocument-class.md) objekt přidružený k zobrazení. **NULL** Pokud zobrazení není připojen k dokumentu.  
  
### <a name="remarks"></a>Poznámky  
 To umožňuje volání členských funkcí dokumentu.  
  
##  <a name="isselected"></a>  CView::IsSelected  
 Voláno rámcem zkontrolujte, zda je vybrána položka zadaný dokument.  
  
```  
virtual BOOL IsSelected(const CObject* pDocItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pDocItem`  
 Odkazuje na položku dokumentu testuje.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je vybrána položka zadaný dokument; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace této funkce vrátí **FALSE**. Přepsat tuto funkci při implementaci výběr pomocí [CDocItem](../../mfc/reference/cdocitem-class.md) objekty. Tato funkce je nutné přepsat, pokud zobrazení obsahuje OLE – položky.  
  
##  <a name="onactivateframe"></a>  CView::OnActivateFrame  
 Voláno rámcem, pokud je aktivace nebo deaktivace rámce okna obsahující zobrazení.  
  
```  
virtual void OnActivateFrame(
    UINT nState,  
    CFrameWnd* pFrameWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `nState`  
 Určuje, zda se okně s rámečkem aktivace nebo deaktivace. Může být jedna z následujících hodnot:  
  
- **WA_INACTIVE** rámce okna je právě deaktivována.  
  
- **WA_ACTIVE** rámce okna je právě aktivován prostřednictvím některé metody jiného, než klikněte na tlačítko myši (například pomocí rozhraní klávesnice vyberte okno).  
  
- **WA_CLICKACTIVE** rámce okna je právě aktivován kliknutí myší  
  
 `pFrameWnd`  
 Ukazatel na rámec okna, který má být aktivována.  
  
### <a name="remarks"></a>Poznámky  
 Funkci člena přepište, pokud chcete provést zvláštní zpracování, pokud je aktivace nebo deaktivace rámce okna přidružené zobrazení. Například [CFormView](../../mfc/reference/cformview-class.md) pokud ho uloží a obnoví ovládací prvek, který má právě fokus, provede toto přepsání.  
  
##  <a name="onactivateview"></a>  CView::OnActivateView  
 Voláno rámcem, pokud je aktivace nebo deaktivace zobrazení.  
  
```  
virtual void OnActivateView(
    BOOL bActivate,  
    CView* pActivateView,  
    CView* pDeactiveView);
```  
  
### <a name="parameters"></a>Parametry  
 `bActivate`  
 Určuje, zda zobrazení se aktivace nebo deaktivace.  
  
 `pActivateView`  
 Odkazuje na objekt zobrazení, který je právě aktivována.  
  
 `pDeactiveView`  
 Odkazuje na objekt zobrazení, který je právě deaktivována.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace této funkce se nastaví fokus na zobrazení právě aktivována. Tato funkce přepsání, pokud chcete provést zvláštní zpracování, pokud je aktivace nebo deaktivace zobrazení. Například pokud chcete zadat speciální vizuální upozornění, které rozlišit aktivní zobrazení z neaktivní zobrazení, které by zkoumat `bActivate` parametr a vzhled zobrazení se aktualizují odpovídajícím způsobem.  
  
 `pActivateView` a `pDeactiveView` parametry příkaz stejné zobrazení, pokud aplikace hlavního rámce okna se aktivuje beze změny v aktivním zobrazení – například, pokud je přenášení fokus z jiné aplikace na tento jeden, nikoli z jednoho zobrazení do druhého v aplikaci nebo při přepínání mezi podřízených oken MDI. To umožňuje zobrazení chcete znovu jeho palety, v případě potřeby.  
  
 Tyto parametry se liší při [CFrameWnd::SetActiveView](../../mfc/reference/cframewnd-class.md#setactiveview) je volán s zobrazení, které se liší od co [CFrameWnd::GetActiveView](../../mfc/reference/cframewnd-class.md#getactiveview) by vrátit. K tomu dochází nejčastěji s rozdělovače oken.  
  
##  <a name="onbeginprinting"></a>  CView::OnBeginPrinting  
 Voláno rámcem na začátku úlohu nebo tiskového náhledu po `OnPreparePrinting` byla volána.  
  
```  
virtual void OnBeginPrinting(
    CDC* pDC,  
    CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Body do kontextu zařízení tiskárny.  
  
 `pInfo`  
 Odkazuje na [cprintinfo –](../../mfc/reference/cprintinfo-structure.md) struktura, která popisuje aktuální tiskové úlohy.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace této funkce neprovede žádnou akci. Funkci přidělit všechny GDI prostředky, například pera nebo písem a potřeby speciálně pro tisk přepište. Vyberte objekty GDI do kontextu zařízení v nástroji [při tisku](#onprint) – členská funkce pro jednotlivé stránky, která používá je. Pokud používáte stejný objekt zobrazení k provádění obrazovky zobrazení a tisk, použijte samostatné proměnné GDI prostředky potřebné pro každé zobrazení; To umožňuje aktualizovat obrazovky během tisku.  
  
 Tuto funkci můžete použít také k provedení inicializacích, které jsou závislé na vlastností kontextu zařízení tiskárny. Počet stránek, které jsou potřebné pro tisk dokumentu může například závisí na nastavení, která uživatele zadali v dialogovém okně tisku (například délku stránky). V takové situaci nelze zadat délku dokumentu v [OnPreparePrinting –](#onprepareprinting) – členská funkce, které by normálně uděláte; musíte počkat, dokud kontextu zařízení tiskárny byla vytvořena podle nastavení v dialogovém okně. [OnBeginPrinting –](#onbeginprinting) je první přepisovatelné funkce, která poskytuje přístup k [CDC](../../mfc/reference/cdc-class.md) objekt reprezentující kontextu zařízení tiskárny, abyste mohli nastavit délku dokumentu z této funkce. Všimněte si, že pokud délka dokumentu není zadán té doby, posuvník se nezobrazí během náhledu tisku.  
  
##  <a name="ondragenter"></a>  CView::OnDragEnter  
 Voláno rámcem když myši nejprve zadá oblasti posouvání cílového rozevíracího okna.  
  
```  
virtual DROPEFFECT OnDragEnter(
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 `pDataObject`  
 Odkazuje na [COleDataObject](../../mfc/reference/coledataobject-class.md) přetažen do oblasti přetažení zobrazení.  
  
 `dwKeyState`  
 Obsahuje stav modifikační klávesy. Jedná se o kombinaci libovolný počet následující: **MK_CONTROL**, **MK_SHIFT**, **MK_ALT**, **MK_LBUTTON**, **MK_ MBUTTON**, a **MK_RBUTTON**.  
  
 `point`  
 Aktuální myši pozice relativně k klientské oblasti zobrazení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota z `DROPEFFECT` výčtového typu, který určuje typ drop, která, pokud je uživatel vyřadit objekt v této pozici. Typ rozevírací obvykle závisí na aktuální klíče stavu indikován `dwKeyState`. Standardní mapování keystates k `DROPEFFECT` hodnoty je:  
  
- `DROPEFFECT_NONE` Datový objekt nelze vyřadit, v tomto okně.  
  
- `DROPEFFECT_LINK` pro **MK_CONTROL &#124; MK_SHIFT** vytvoří propojení mezi objektem a jeho serverem.  
  
- `DROPEFFECT_COPY` pro **MK_CONTROL** vytvoří kopii vynechaných objektu.  
  
- `DROPEFFECT_MOVE` pro **MK_ALT** vytvoří kopii vynechaných objektu a původní objekt odstranit. Toto je obvykle rozevírací platit výchozí, pokud zobrazení může přijmout tento objekt data.  
  
 Další informace najdete v tématu ukázku rozšířené koncepty MFC [OCLIENT](../../visual-cpp-samples.md).  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace je Neprovádět žádnou akci a vrátí `DROPEFFECT_NONE`.  
  
 Funkci pro přípravu na budoucí volání přepsat [ondragover –](#ondragover) – členská funkce. V tuto chvíli pro pozdější použití v mají být načtena žádná data, která vyžaduje z datový objekt `OnDragOver` – členská funkce. Zobrazení by měl být i během této doby visual názor uživatele. Další informace najdete v článku [přetažení: implementace cíle přetažení](../../mfc/drag-and-drop-implementing-a-drop-target.md).  
  
##  <a name="ondragleave"></a>  CView::OnDragLeave  
 Voláno rámcem během operace přetažení při přesunutí myši mimo oblast platný přetažení pro toto okno.  
  
```  
virtual void OnDragLeave();
```  
  
### <a name="remarks"></a>Poznámky  
 Funkci přepsat, pokud je aktuální zobrazení potřeba vyčistit všechny akce prováděné během [ondragenter –](#ondragenter) nebo [ondragover –](#ondragover) volání, jako například odebírání žádné vizuální uživatelský zpětné vazby, pokud byl přetáhnout objekt .  
  
##  <a name="ondragover"></a>  CView::OnDragOver  
 Voláno rámcem během operace přetažení po přesunutí myši cílové okno vyřaďte.  
  
```  
virtual DROPEFFECT OnDragOver(
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 `pDataObject`  
 Odkazuje na [COleDataObject](../../mfc/reference/coledataobject-class.md) přetažen přes cíle přetažení.  
  
 `dwKeyState`  
 Obsahuje stav modifikační klávesy. Jedná se o kombinaci libovolný počet následující: **MK_CONTROL**, **MK_SHIFT**, **MK_ALT**, **MK_LBUTTON**, **MK_ MBUTTON**, a **MK_RBUTTON**.  
  
 `point`  
 Aktuální myši pozice relativně k zobrazení klientské oblasti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota z `DROPEFFECT` výčtového typu, který určuje typ drop, která, pokud je uživatel vyřadit objekt v této pozici. Typ rozevírací často závisí na aktuální stav klíče podle `dwKeyState`. Standardní mapování keystates k `DROPEFFECT` hodnoty je:  
  
- `DROPEFFECT_NONE` Datový objekt nelze vyřadit, v tomto okně.  
  
- `DROPEFFECT_LINK` pro **MK_CONTROL &#124; MK_SHIFT** vytvoří propojení mezi objektem a jeho serverem.  
  
- `DROPEFFECT_COPY` pro **MK_CONTROL** vytvoří kopii vynechaných objektu.  
  
- `DROPEFFECT_MOVE` pro **MK_ALT** vytvoří kopii vynechaných objektu a původní objekt odstranit. Toto je obvykle rozevírací platit výchozí, pokud zobrazení může přijmout datový objekt.  
  
 Další informace najdete v tématu ukázku rozšířené koncepty MFC [OCLIENT](../../visual-cpp-samples.md).  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace je Neprovádět žádnou akci a vrátí `DROPEFFECT_NONE`.  
  
 Přepsání této funkce můžete poskytnout zpětnou vazbu od visual uživatelů během operace přetažení. Vzhledem k tomu, že tato funkce je volána nepřetržitě, kód, jsou v něm obsažena by mělo být optimalizované co nejvíc. Další informace najdete v článku [přetažení: implementace cíle přetažení](../../mfc/drag-and-drop-implementing-a-drop-target.md).  
  
##  <a name="ondragscroll"></a>  CView::OnDragScroll  
 Voláno rámcem před voláním [ondragenter –](#ondragenter) nebo [ondragover –](#ondragover) k určení, zda bod je v oblasti s možností posouvání.  
  
```  
virtual DROPEFFECT OnDragScroll(
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 `dwKeyState`  
 Obsahuje stav modifikační klávesy. Jedná se o kombinaci libovolný počet následující: **MK_CONTROL**, **MK_SHIFT**, **MK_ALT**, **MK_LBUTTON**, **MK_ MBUTTON**, a **MK_RBUTTON**.  
  
 `point`  
 Obsahuje umístění kurzoru v pixelech, relativně k obrazovce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota z `DROPEFFECT` výčtového typu, který určuje typ drop, která, pokud je uživatel vyřadit objekt v této pozici. Typ rozevírací obvykle závisí na aktuální klíče stavu indikován `dwKeyState`. Standardní mapování keystates k `DROPEFFECT` hodnoty je:  
  
- `DROPEFFECT_NONE` Datový objekt nelze vyřadit, v tomto okně.  
  
- `DROPEFFECT_LINK` pro **MK_CONTROL &#124; MK_SHIFT** vytvoří propojení mezi objektem a jeho serverem.  
  
- `DROPEFFECT_COPY` pro **MK_CONTROL** vytvoří kopii vynechaných objektu.  
  
- `DROPEFFECT_MOVE` pro **MK_ALT** vytvoří kopii vynechaných objektu a původní objekt odstranit.  
  
- `DROPEFFECT_SCROLL` Označuje, že operaci přetažení scroll dojde nebo dochází v cílové zobrazení.  
  
 Další informace najdete v tématu ukázku rozšířené koncepty MFC [OCLIENT](../../visual-cpp-samples.md).  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce přepsání, pokud chcete zadat speciální chování pro tuto událost. Výchozí implementace automaticky posune windows, když je kurzor přetažen Posunout oblast výchozí uvnitř ohraničení každé okno. Další informace najdete v článku [přetažení: implementace cíle přetažení](../../mfc/drag-and-drop-implementing-a-drop-target.md).  
  
##  <a name="ondraw"></a>  CView::OnDraw  
 Voláno rámcem Vykreslit obrázek dokumentu.  
  
```  
virtual void OnDraw(CDC* pDC) = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Odkazuje na kontext zařízení, který má být používané k vykreslování obrázek dokumentu.  
  
### <a name="remarks"></a>Poznámky  
 Volá rámec této funkci můžete provést obrazovky zobrazení, tisku a tiskového náhledu a předává kontextu různých zařízení v každém případu. Neexistuje žádný výchozí implementace.  
  
 Je nutné přepsat tuto funkci k zobrazení zobrazení dokumentu. Můžete provádět volání rozhraní GDI grafické zařízení pomocí [CDC](../../mfc/reference/cdc-class.md) objektu na kterou odkazuje `pDC` parametr. Můžete vybrat GDI prostředky, například pera nebo písem a do kontextu zařízení před vykreslením a později je zrušte. Kreslení kód často může být nezávislé na zařízení; To znamená nevyžaduje informace o jaký typ zařízení zobrazit bitovou kopii.  
  
 K optimalizaci vykreslování, volání [RectVisible](../../mfc/reference/cdc-class.md#rectvisible) – členská funkce kontextu zařízení a zjistěte, zda se daný obdélníku přidělit. Pokud potřebujete k rozlišení obrazovky normální zobrazení a tisk, zavolejte [IsPrinting](../../mfc/reference/cdc-class.md#isprinting) – členská funkce kontextu zařízení.  
  
##  <a name="ondrop"></a>  CView::OnDrop  
 Voláno rámcem, když uživatel uvolní objekt dat přes cíle přetažení platný.  
  
```  
virtual BOOL OnDrop(
    COleDataObject* pDataObject,  
    DROPEFFECT dropEffect,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 `pDataObject`  
 Odkazuje na [COleDataObject](../../mfc/reference/coledataobject-class.md) , je však zrušeno do cíle přetažení.  
  
 `dropEffect`  
 Rozevírací účinky, které požadoval uživatel.  
  
- `DROPEFFECT_COPY` Vytvoří kopii datový objekt probíhá vyřazování.  
  
- `DROPEFFECT_MOVE` Přesune datový objekt na aktuální umístění myši.  
  
- `DROPEFFECT_LINK` Vytvoří vazbu mezi objekt dat a jeho serverem.  
  
 `point`  
 Aktuální myši pozice relativně k zobrazení klientské oblasti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud se rozevírací byla úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace neprovede žádnou akci a vrátí **FALSE**.  
  
 Potlačí tuto funkci implementovat účinku OLE rozevírací do klientské oblasti zobrazení. Datový objekt může být prověřen prostřednictvím `pDataObject` pro data ze schránky formáty a data vyřazen Zadaný bod.  
  
> [!NOTE]
>  Rozhraní není volání této funkce, pokud dojde přepsání pro [ondropex –](#ondropex) v této třídě zobrazení.  
  
##  <a name="ondropex"></a>  CView::OnDropEx  
 Voláno rámcem, když uživatel uvolní objekt dat přes cíle přetažení platný.  
  
```  
virtual DROPEFFECT OnDropEx(
    COleDataObject* pDataObject,  
    DROPEFFECT dropDefault,  
    DROPEFFECT dropList,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 `pDataObject`  
 Odkazuje na [COleDataObject](../../mfc/reference/coledataobject-class.md) , je však zrušeno do cíle přetažení.  
  
 `dropDefault`  
 O tom, že se uživatel rozhodl pro operace vyřazení výchozí na základě aktuálního stavu klíče. To může být `DROPEFFECT_NONE`. Vyřaďte důsledky jsou popsané v oddílu Poznámky.  
  
 `dropList`  
 Seznam rozevírací účinky, které podporuje zdroji vyřaďte. Vyřaďte vliv hodnoty lze spojovat pomocí bitová hodnota OR ( **&#124;**) operaci. Vyřaďte důsledky jsou popsané v oddílu Poznámky.  
  
 `point`  
 Aktuální myši pozice relativně k zobrazení klientské oblasti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vliv rozevírací rozevírací pokus o umístění, které je výsledkem `point`. Musí být jedna z hodnot indikován *dropEffectList*. Vyřaďte důsledky jsou popsané v oddílu Poznámky.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace je Neprovádět žádnou akci a vrátí fiktivní hodnoty (-1) k označení, že by měly volat rozhraní [OnDrop](#ondrop) obslužné rutiny.  
  
 Tuto funkci implementovat účinku pravé tlačítko myši přetažení přepište. Pravé tlačítko myši přetažení zobrazí nabídku možností obvykle, když se uvolní pravé tlačítko myši.  
  
 Přepsání z `OnDropEx` má dotázat na pravé tlačítko myši. Můžete volat [GetKeyState](http://msdn.microsoft.com/library/windows/desktop/ms646301) nebo uložit stav pravé tlačítko myši z vaší [ondragenter –](#ondragenter) obslužné rutiny.  
  
-   Pokud pravé tlačítko myši je vypnutý, přepsání by měl zobrazit místní nabídky, který nabízí podporu důsledky rozevírací rozevírací zdroj.  
  
    -   Zkontrolujte `dropList` k určení rozevírací důsledky nepodporuje zdroj vynechání. Povolte jenom tyto akce v místní nabídce.  
  
    -   Použití [SetMenuDefaultItem](http://msdn.microsoft.com/library/windows/desktop/ms647996) k nastavení výchozí akce na základě `dropDefault`.  
  
    -   Nakonec proveďte akci indikován výběr uživatele z místní nabídky.  
  
-   Pokud není pravé tlačítko myši dolů, zpracovat tuto jako standardní rozevírací požadavek by měl přepsání. Použijte rozevírací efekt zadaný v `dropDefault`. Alternativně můžete přepsání vrátit fiktivní hodnoty (-1), která označuje, že `OnDrop` zpracuje tato operace odstranění.  
  
 Použití `pDataObject` prozkoumat `COleDataObject` pro data ze schránky formátu a data vyřazen Zadaný bod.  
  
 Účinky rozevírací popisují akce spojené s operace odstranění. Najdete v následujícím seznamu rozevírací důsledky:  
  
- `DROPEFFECT_NONE` Pokles nebude možné.  
  
- `DROPEFFECT_COPY` Operace kopírování by se provedla.  
  
- `DROPEFFECT_MOVE` Operace přesunu by se provedla.  
  
- `DROPEFFECT_LINK` Odkaz z vynechaných dat na původní data by byla založena.  
  
- `DROPEFFECT_SCROLL` Označuje, že posuňte operaci přetažení dojde nebo dochází na cíli.  
  
 Další informace o nastavení výchozí příkaz nabídky najdete v tématu [SetMenuDefaultItem](http://msdn.microsoft.com/library/windows/desktop/ms647996) ve Windows SDK a [CMenu::GetSafeHmenu](../../mfc/reference/cmenu-class.md#getsafehmenu) v tomto svazku.  
  
##  <a name="onendprinting"></a>  CView::OnEndPrinting  
 Voláno rámcem po dokument byl tisknou nebo zobrazují.  
  
```  
virtual void OnEndPrinting(
    CDC* pDC,  
    CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Body do kontextu zařízení tiskárny.  
  
 `pInfo`  
 Odkazuje na [cprintinfo –](../../mfc/reference/cprintinfo-structure.md) struktura, která popisuje aktuální tiskové úlohy.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace této funkce neprovede žádnou akci. Funkci uvolnit všechny GDI prostředky přidělené v přepsat [OnBeginPrinting –](#onbeginprinting) – členská funkce.  
  
##  <a name="onendprintpreview"></a>  CView::OnEndPrintPreview  
 Voláno rámcem při ukončení režimu náhledu tisku uživatelem.  
  
```  
virtual void OnEndPrintPreview(
    CDC* pDC,  
    CPrintInfo* pInfo,  
    POINT point,  
    CPreviewView* pView);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Body do kontextu zařízení tiskárny.  
  
 `pInfo`  
 Odkazuje na [cprintinfo –](../../mfc/reference/cprintinfo-structure.md) struktura, která popisuje aktuální tiskové úlohy.  
  
 `point`  
 Určuje bod na stránku, která byla naposledy zobrazených v režimu preview.  
  
 `pView`  
 Odkazuje na objekt zobrazení použitý pro zobrazení náhledu.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace této funkce volá [OnEndPrinting –](#onendprinting) – členská funkce a obnovení začal hlavního okna rámce do stavu před náhledu tisku. Funkci provést zvláštní zpracování po ukončení režimu preview přepište. Například pokud chcete zachovat pozici uživatele v dokumentu při přepnutí z režimu náhledu na režim Normální zobrazení, můžete procházet pozice popsaného `point` parametr a `m_nCurPage` členem `CPrintInfo` struktura která `pInfo` parametr odkazuje na.  
  
 Vždy volat základní třída verzi `OnEndPrintPreview` z přepsání, obvykle na konci funkce.  
  
##  <a name="oninitialupdate"></a>  CView::OnInitialUpdate  
 Voláno rámcem po zobrazení je nejprve připojen k dokumentu, ale před zpočátku je zobrazeno zobrazení.  
  
```  
virtual void OnInitialUpdate();
```  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace této funkce volá [OnUpdate](#onupdate) – členská funkce bez pomocného parametru informací (tedy pomocí výchozích hodnot 0 pro `lHint` parametr a **NULL** pro `pHint` parametr). Přepsání této funkci můžete provést všechny jednorázové inicializace, který vyžaduje informace o dokumentu. Například pokud aplikace má pevnou velikostí dokumenty, můžete použít tuto funkci k chybě při inicializaci zobrazení posouvání omezení na základě velikosti dokumentu. Pokud vaše aplikace podporuje dokumenty proměnlivé velikosti, použijte [OnUpdate](#onupdate) aktualizovat posouvání omezuje pokaždé, když změny dokumentu.  
  
##  <a name="onpreparedc"></a>  CView::OnPrepareDC  
 Voláno rámcem před [OnDraw –](#ondraw) – členská funkce je volána pro zobrazení na obrazovce a před [při tisku](#onprint) – členská funkce je volána pro jednotlivé stránky během tisku nebo náhledu.  
  
```  
virtual void OnPrepareDC(
    CDC* pDC,  
    CPrintInfo* pInfo = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Odkazuje na kontext zařízení, který má být používané k vykreslování obrázek dokumentu.  
  
 `pInfo`  
 Odkazuje na [cprintinfo –](../../mfc/reference/cprintinfo-structure.md) struktura, která popisuje aktuální tiskové úlohy, pokud `OnPrepareDC` je volána pro tisku nebo náhledu; `m_nCurPage` člen Určuje stránku chystáte jej vytisknout. Tento parametr je **NULL** Pokud `OnPrepareDC` je volána pro zobrazení na obrazovce.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace této funkce se nic nestane. Pokud je tato funkce volána pro zobrazení na obrazovce. Ale tato funkce je přepsání v odvozené třídy, například [CScrollView](../../mfc/reference/cscrollview-class.md), chcete-li upravit atributy kontextu zařízení; v důsledku toho by měly vždy volat základní třída implementaci na začátku přepsání.  
  
 Pokud je tato funkce volána pro tisk, výchozí implementace prozkoumá stránky informace uložené v `pInfo` parametr. Pokud délka dokumentu nebyl zadán, `OnPrepareDC` předpokládá dokumentu, který má být jednu stránku dlouhé a zastaví tiskové smyčky po vytištění jednu stránku. Funkce zastaví tiskové smyčky nastavením `m_bContinuePrinting` členem k strukturu **FALSE**.  
  
 Přepsání `OnPrepareDC` pro některý z následujících důvodů:  
  
-   Chcete-li upravit atributy kontextu zařízení podle potřeby pro zadanou stránku. Například pokud je nutné nastavit mapování režimu nebo dalších vlastností kontextu zařízení, to provést v této funkci.  
  
-   K provedení stránkování čas tisku. Obvykle se po zahájení tisk pomocí zadat délku dokumentu [OnPreparePrinting –](#onprepareprinting) – členská funkce. Ale pokud neznáte předem jak dlouho dokument je (například při tisku neurčená počet záznamů z databáze), přepsání `OnPrepareDC` k otestování tohoto dokumentu, zatímco ho vytisknout. Pokud není žádné další dokumentu pro tisk, nastavit `m_bContinuePrinting` členem `CPrintInfo` struktury k **FALSE**.  
  
-   K odeslání řídicí kódy tiskárny na základě po stránkách. K odeslání řídicí kódy z `OnPrepareDC`, volání **řídicí** členské funkce `pDC` parametr.  
  
 Volat základní třída verzi `OnPrepareDC` na začátku přepsání.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#183](../../mfc/codesnippet/cpp/cview-class_1.cpp)]  
  
##  <a name="onprepareprinting"></a>  CView::OnPreparePrinting  
 Voláno rámcem předtím, než je tisku dokumentu nebo k prohlížení.  
  
```  
virtual BOOL OnPreparePrinting(CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>Parametry  
 `pInfo`  
 Odkazuje na [cprintinfo –](../../mfc/reference/cprintinfo-structure.md) struktura, která popisuje aktuální tiskové úlohy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové zahájíte tisk; 0, pokud se tisková úloha byla zrušena.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace neprovede žádnou akci.  
  
 Je nutné přepsat tuto funkci povolit tisku a přehled tisku. Volání [doprepareprinting –](#doprepareprinting) – členská funkce, předání `pInfo` parametr a pak se vraťte hodnoty; `DoPreparePrinting` zobrazí dialogové okno tisku a vytvoří kontextu zařízení tiskárny. Pokud chcete k chybě při inicializaci dialogové okno tisku s hodnoty jiné než výchozí hodnoty, přiřadit hodnoty k členům `pInfo`. Například pokud znáte délka dokumentu, předejte hodnota, která má [SetMaxPage](../../mfc/reference/cprintinfo-structure.md#setmaxpage) členské funkce `pInfo` před voláním `DoPreparePrinting`. Tato hodnota se zobrazí v Komu: pole v části rozsah dialogovém okně tisku.  
  
 `DoPreparePrinting` Dialogové okno tisku pro úlohu preview nezobrazí. Pokud chcete dialogové okno tisku pro tisková úloha vynechat, zkontrolujte, zda **m_bPreview** členem `pInfo` je **FALSE** a nastavte ji na **TRUE** před předáním na `DoPreparePrinting`; ji obnovit na **FALSE** později.  
  
 Pokud potřebujete provést inicializacích, které vyžadují přístup k `CDC` přepsat objekt reprezentující tiskárny kontextu zařízení (například pokud je potřeba vědět velikost stránky před zadáním délka dokumentu), `OnBeginPrinting` člena funkce.  
  
 Pokud chcete nastavit hodnotu **m_nNumPreviewPages** nebo **m_strPageDesc** členy `pInfo` parametr učinit po volání `DoPreparePrinting`. `DoPreparePrinting` Členské funkce sady **m_nNumPreviewPages** na hodnotu do aplikace. Soubor INI a nastaví **m_strPageDesc** na výchozí hodnotu.  
  
### <a name="example"></a>Příklad  
  Přepsání `OnPreparePrinting` a volání `DoPreparePrinting` z přepsání tak, aby rozhraní bude zobrazit dialogové okno tisku a za vás vytvořit tiskárnu řadiče domény.  
  
 [!code-cpp[NVC_MFCDocView#184](../../mfc/codesnippet/cpp/cview-class_2.cpp)]  
  
 Pokud víte, kolik stránek obsahuje dokument, nastavit maximální stránky `OnPreparePrinting` před voláním `DoPreparePrinting`. Rozhraní se zobrazí v dialogovém okně Tisk políčko "na" číslo maximální stránky.  
  
 [!code-cpp[NVC_MFCDocView#185](../../mfc/codesnippet/cpp/cview-class_3.cpp)]  
  
##  <a name="onprint"></a>  CView::OnPrint  
 Voláno rámcem vytisknout nebo náhled stránky z dokumentu.  
  
```  
virtual void OnPrint(
    CDC* pDC,  
    CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Body do kontextu zařízení tiskárny.  
  
 `pInfo`  
 Odkazuje na `CPrintInfo` struktura, která popisuje aktuální tiskové úlohy.  
  
### <a name="remarks"></a>Poznámky  
 Pro jednotlivé stránky, tisku, volá framework ihned po volání této funkce [onpreparedc –](#onpreparedc) – členská funkce. Je zadána tisku stránky `m_nCurPage` členem [cprintinfo –](../../mfc/reference/cprintinfo-structure.md) struktury, která `pInfo` odkazuje na. Výchozí implementace volá [OnDraw –](#ondraw) – členská funkce a předává je kontextu zařízení tiskárny.  
  
 Přepište tuto funkci pro některý z následujících důvodů:  
  
-   Chcete-li povolit tisk vícestránkové dokumenty. Vykreslení jenom ta část dokumentu, který odpovídá právě tištěné stránky. Pokud používáte `OnDraw` k provedení vykreslování, můžete upravit bod zobrazení tak, aby vytištěn příslušné části dokumentu.  
  
-   Chcete-li obraz vypadat jinak než bitovou kopii obrazovky (tj. Pokud vaše aplikace není WYSIWYG). Neprochází tiskárny kontextu zařízení k `OnDraw`, kontext zařízení použít k vykreslení bitovou kopii pomocí atributů není uvedené na obrazovce.  
  
     Pokud potřebujete prostředků GDI pro tisk, které nepoužívají pro zobrazení na obrazovce, vyberte je do kontextu zařízení před vykreslením a zrušte výběr je později. Tyto prostředky GDI by měla být přidělená v [OnBeginPrinting –](#onbeginprinting) a vydat v [OnEndPrinting –](#onendprinting).  
  
-   K implementaci záhlaví a zápatí stránky. Můžete dál používat `OnDraw` Uděláte to tak, že omezíte k oblasti, která tisku na vykreslování.  
  
 Všimněte si, že **m_rectDraw** členem `pInfo` parametr popisuje tisknutelná oblast stránky v logické jednotky.  
  
 Nevolejte `OnPrepareDC` v přepsání z `OnPrint`; framework volání `OnPrepareDC` automaticky před voláním `OnPrint`.  
  
### <a name="example"></a>Příklad  
 Toto je kostru pro překryté `OnPrint` funkce:  
  
 [!code-cpp[NVC_MFCDocView#186](../../mfc/codesnippet/cpp/cview-class_4.cpp)]  
  
 Jiný příklad najdete v tématu [CRichEditView::PrintInsideRect](../../mfc/reference/cricheditview-class.md#printinsiderect).  
  
##  <a name="onscroll"></a>  CView::OnScroll  
 Voláno rámcem k určení, zda posouvání je možné.  
  
```  
virtual BOOL OnScroll(
    UINT nScrollCode,  
    UINT nPos,  
    BOOL bDoScroll = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `nScrollCode`  
 Posuvníku kód, který označuje uživatele je posouvání požadavku. Tento parametr se skládá ze dvou částí: nejnižší bajtů, která určuje typ posouvání výskytu vodorovně, a horní bajtů, která určuje typ posouvání výskytu svisle:  
  
- **SB_BOTTOM** posouvá dolů.  
  
- **SB_LINEDOWN** jeden řádek posune stránku dolů.  
  
- **SB_LINEUP** posune jeden řádek nahoru.  
  
- **SB_PAGEDOWN** jednu stránku posune stránku dolů.  
  
- **SB_PAGEUP** posune jednu stránku nahoru.  
  
- **SB_THUMBTRACK** Drags posouvacího políčka na zadané pozici. Aktuální pozice je zadána v `nPos`.  
  
- **SB_TOP** posune nahoru.  
  
 `nPos`  
 Obsahuje aktuální pozici posouvací políčko, pokud je kód posuvníku **SB_THUMBTRACK**; v opačném případě se nepoužívá. V závislosti na rozsahu počáteční scroll `nPos` může být záporný a by měl být přetypovat `int` v případě potřeby.  
  
 `bDoScroll`  
 Určuje, zda by měla ve skutečnosti provést zadanou akci posouvání. Pokud **nastavena hodnota TRUE,** pak posouvání by měl proběhnout; Pokud **FALSE**, pak posouvání nedojde.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud `bDoScroll` je **TRUE** a ve skutečnosti přesunut oblasti zobrazení, pak se vraťte nenulové; jinak hodnota 0. Pokud `bDoScroll` je **FALSE**, pak se vraťte hodnotu, která by mít vrácena pokud `bDoScroll` byly **TRUE**, i když neuděláte ve skutečnosti posouvání.  
  
### <a name="remarks"></a>Poznámky  
 V jednom případě tato funkce je volána rámcem s `bDoScroll` nastavena na **TRUE** při zobrazení přijme zprávu o scrollbar. V takovém případě byste měli ve skutečnosti přejít zobrazení. V ostatních případech tato funkce je volána s `bDoScroll` nastavena na **FALSE** při položku OLE je původně přetažen oblast automatické posouvání cíle přetažení před ve skutečnosti posouvání probíhá. V takovém případě by neměl posunete ve skutečnosti zobrazení.  
  
##  <a name="onscrollby"></a>  CView::OnScrollBy  
 Voláno rámcem, když uživatel prohlíží oblasti za existuje zobrazení dokumentu, buď tak, že přetáhnete položky OLE proti ohraničení aktuální zobrazení nebo manipulace s posuvníky svislé nebo vodorovné.  
  
```  
virtual BOOL OnScrollBy(
    CSize sizeScroll,  
    BOOL bDoScroll = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `sizeScroll`  
 Počet pixelů přešli vodorovně a svisle.  
  
 `bDoScroll`  
 Určuje, zda má být provedena posouvání zobrazení. Pokud **nastavena hodnota TRUE,** pak posouvání probíhá; pokud **FALSE**, pak posouvání nedojde.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud zobrazení bylo možné posunout; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 V odvozených třídách tato metoda ověří, zda je zobrazení posouvatelného ve směru uživatel požádal a pak aktualizuje novou oblast v případě potřeby. Tato funkce je volána automaticky [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) a [CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) k provedení této žádosti skutečné posouvání.  
  
 Výchozí implementace této metody nedojde ke změně zobrazení, ale pokud není volán, nebude v posuňte zobrazení `CScrollView`-odvozené třídy.  
  
 Pokud dokument šířky nebo výšky překračuje 32767 pixelů, posouvání po 32767 selže, protože `OnScrollBy` je volán s neplatnou `sizeScroll` argument.  
  
##  <a name="onupdate"></a>  CView::OnUpdate  
 Voláno rámcem po zobrazení byly změny; Tato funkce je volána [CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) a umožňuje zobrazit aktualizace jeho zobrazení tak, aby odrážela tyto změny.  
  
```  
virtual void OnUpdate(
    CView* pSender,  
    LPARAM lHint,  
    CObject* pHint);
```  
  
### <a name="parameters"></a>Parametry  
 `pSender`  
 Odkazuje na úpravy dokumentu, zobrazení nebo **NULL** Pokud jsou všechny zobrazení aktualizovat.  
  
 `lHint`  
 Obsahuje informace o změny.  
  
 `pHint`  
 Odkazuje na objekt ukládání informací o změny.  
  
### <a name="remarks"></a>Poznámky  
 Také je volána metodou výchozí implementaci [OnInitialUpdate](#oninitialupdate). Výchozí implementace by způsobila neplatnost celého klienta, označení k vykreslování při dalším `WM_PAINT` přijata zpráva. Tato funkce přepsání, pokud chcete aktualizovat pouze oblasti, které jsou mapovány na změněné části dokumentu. K tomu musí projít informace o úpravy pomocí pomocného parametru parametrů.  
  
 Chcete-li použít `lHint`, určit speciální pomocný parametr hodnot, obvykle bitová maska nebo výčtového typu, a v dokumentu předat jednu z těchto hodnot. Použít `pHint`, odvození třídy z pomocný parametr [CObject](../../mfc/reference/cobject-class.md) a mít dokumentu ukazatel předat objekt pomocný parametr; při přepisování `OnUpdate`, použijte [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof) členské funkce Určuje typ spuštění objektu pomocný parametr.  
  
 Obvykle neměli proveďte kteroukoli kreslení přímo z `OnUpdate`. Místo toho určete rámečku v souřadnicích zařízení popisující k oblasti, která vyžaduje aktualizaci; předat obdélníku do [CWnd::InvalidateRect](../../mfc/reference/cwnd-class.md#invalidaterect). To způsobí, že Malování příštím [WM_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213) přijata zpráva.  
  
 Pokud `lHint` je 0 a `pHint` je **NULL**, dokumentu odeslal obecné aktualizace oznámení. Pokud zobrazení obdrží upozornění na obecné aktualizace, nebo ho nelze dekódovat pomocné parametry, by měl platnost jeho celého klienta.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC MDIDOCVW](../../visual-cpp-samples.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [CFrameWnd – třída](../../mfc/reference/cframewnd-class.md)   
 [CSplitterWnd – třída](../../mfc/reference/csplitterwnd-class.md)   
 [Třída CDC](../../mfc/reference/cdc-class.md)   
 [CDocTemplate – třída](../../mfc/reference/cdoctemplate-class.md)   
 [CDocument – třída](../../mfc/reference/cdocument-class.md)
