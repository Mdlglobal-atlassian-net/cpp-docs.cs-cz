---
title: CFrameWnd – třída
ms.date: 11/04/2016
f1_keywords:
- CFrameWnd
- AFXWIN/CFrameWnd
- AFXWIN/CFrameWnd::CFrameWnd
- AFXWIN/CFrameWnd::ActivateFrame
- AFXWIN/CFrameWnd::BeginModalState
- AFXWIN/CFrameWnd::Create
- AFXWIN/CFrameWnd::CreateView
- AFXWIN/CFrameWnd::DockControlBar
- AFXWIN/CFrameWnd::EnableDocking
- AFXWIN/CFrameWnd::EndModalState
- AFXWIN/CFrameWnd::FloatControlBar
- AFXWIN/CFrameWnd::GetActiveDocument
- AFXWIN/CFrameWnd::GetActiveFrame
- AFXWIN/CFrameWnd::GetActiveView
- AFXWIN/CFrameWnd::GetControlBar
- AFXWIN/CFrameWnd::GetDockState
- AFXWIN/CFrameWnd::GetMenuBarState
- AFXWIN/CFrameWnd::GetMenuBarVisibility
- AFXWIN/CFrameWnd::GetMessageBar
- AFXWIN/CFrameWnd::GetMessageString
- AFXWIN/CFrameWnd::GetTitle
- AFXWIN/CFrameWnd::InitialUpdateFrame
- AFXWIN/CFrameWnd::InModalState
- AFXWIN/CFrameWnd::IsTracking
- AFXWIN/CFrameWnd::LoadAccelTable
- AFXWIN/CFrameWnd::LoadBarState
- AFXWIN/CFrameWnd::LoadFrame
- AFXWIN/CFrameWnd::NegotiateBorderSpace
- AFXWIN/CFrameWnd::OnBarCheck
- AFXWIN/CFrameWnd::OnContextHelp
- AFXWIN/CFrameWnd::OnSetPreviewMode
- AFXWIN/CFrameWnd::OnUpdateControlBarMenu
- AFXWIN/CFrameWnd::RecalcLayout
- AFXWIN/CFrameWnd::SaveBarState
- AFXWIN/CFrameWnd::SetActivePreviewView
- AFXWIN/CFrameWnd::SetActiveView
- AFXWIN/CFrameWnd::SetDockState
- AFXWIN/CFrameWnd::SetMenuBarState
- AFXWIN/CFrameWnd::SetMenuBarVisibility
- AFXWIN/CFrameWnd::SetMessageText
- AFXWIN/CFrameWnd::SetProgressBarPosition
- AFXWIN/CFrameWnd::SetProgressBarRange
- AFXWIN/CFrameWnd::SetProgressBarState
- AFXWIN/CFrameWnd::SetTaskbarOverlayIcon
- AFXWIN/CFrameWnd::SetTitle
- AFXWIN/CFrameWnd::ShowControlBar
- AFXWIN/CFrameWnd::ShowOwnedWindows
- AFXWIN/CFrameWnd::OnCreateClient
- AFXWIN/CFrameWnd::OnHideMenuBar
- AFXWIN/CFrameWnd::OnShowMenuBar
- AFXWIN/CFrameWnd::m_bAutoMenuEnable
- AFXWIN/CFrameWnd::rectDefault
helpviewer_keywords:
- CFrameWnd [MFC], CFrameWnd
- CFrameWnd [MFC], ActivateFrame
- CFrameWnd [MFC], BeginModalState
- CFrameWnd [MFC], Create
- CFrameWnd [MFC], CreateView
- CFrameWnd [MFC], DockControlBar
- CFrameWnd [MFC], EnableDocking
- CFrameWnd [MFC], EndModalState
- CFrameWnd [MFC], FloatControlBar
- CFrameWnd [MFC], GetActiveDocument
- CFrameWnd [MFC], GetActiveFrame
- CFrameWnd [MFC], GetActiveView
- CFrameWnd [MFC], GetControlBar
- CFrameWnd [MFC], GetDockState
- CFrameWnd [MFC], GetMenuBarState
- CFrameWnd [MFC], GetMenuBarVisibility
- CFrameWnd [MFC], GetMessageBar
- CFrameWnd [MFC], GetMessageString
- CFrameWnd [MFC], GetTitle
- CFrameWnd [MFC], InitialUpdateFrame
- CFrameWnd [MFC], InModalState
- CFrameWnd [MFC], IsTracking
- CFrameWnd [MFC], LoadAccelTable
- CFrameWnd [MFC], LoadBarState
- CFrameWnd [MFC], LoadFrame
- CFrameWnd [MFC], NegotiateBorderSpace
- CFrameWnd [MFC], OnBarCheck
- CFrameWnd [MFC], OnContextHelp
- CFrameWnd [MFC], OnSetPreviewMode
- CFrameWnd [MFC], OnUpdateControlBarMenu
- CFrameWnd [MFC], RecalcLayout
- CFrameWnd [MFC], SaveBarState
- CFrameWnd [MFC], SetActivePreviewView
- CFrameWnd [MFC], SetActiveView
- CFrameWnd [MFC], SetDockState
- CFrameWnd [MFC], SetMenuBarState
- CFrameWnd [MFC], SetMenuBarVisibility
- CFrameWnd [MFC], SetMessageText
- CFrameWnd [MFC], SetProgressBarPosition
- CFrameWnd [MFC], SetProgressBarRange
- CFrameWnd [MFC], SetProgressBarState
- CFrameWnd [MFC], SetTaskbarOverlayIcon
- CFrameWnd [MFC], SetTitle
- CFrameWnd [MFC], ShowControlBar
- CFrameWnd [MFC], ShowOwnedWindows
- CFrameWnd [MFC], OnCreateClient
- CFrameWnd [MFC], OnHideMenuBar
- CFrameWnd [MFC], OnShowMenuBar
- CFrameWnd [MFC], m_bAutoMenuEnable
- CFrameWnd [MFC], rectDefault
ms.assetid: e2220aba-5bf4-4002-b960-fbcafcad01f1
ms.openlocfilehash: 7bdb681754a500ab86538f3397b4c07284b850d0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182058"
---
# <a name="cframewnd-class"></a>CFrameWnd – třída

Poskytuje funkce pro Windows rozhraní jednoho dokumentu (SDI) překrytého nebo místního okna rámce, spolu se členy pro správu okna.

## <a name="syntax"></a>Syntaxe

```
class CFrameWnd : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CFrameWnd::CFrameWnd](#cframewnd)|Vytvoří `CFrameWnd` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CFrameWnd::ActivateFrame](#activateframe)|Díky rámce viditelné a dostupné pro uživatele.|
|[CFrameWnd::BeginModalState](#beginmodalstate)|Nastaví modální okno rámce.|
|[CFrameWnd::Create](#create)|Volání k vytváření a inicializace okna rámce Windows přidružené `CFrameWnd` objektu.|
|[CFrameWnd::CreateView](#createview)|Vytvoří zobrazení v rámci, která není odvozena od `CView`.|
|[CFrameWnd::DockControlBar](#dockcontrolbar)|Ukotvené ovládací panel.|
|[CFrameWnd::EnableDocking](#enabledocking)|Umožňuje ovládací panel ukotvit.|
|[CFrameWnd::EndModalState](#endmodalstate)|Ukončí modální stav okna rámce. Všechny oken zakázal `BeginModalState`.|
|[CFrameWnd::FloatControlBar](#floatcontrolbar)|Čísel s plovoucí čárkou ovládací panel.|
|[CFrameWnd::GetActiveDocument](#getactivedocument)|Vrátí aktivní `CDocument` objektu.|
|[CFrameWnd::GetActiveFrame](#getactiveframe)|Vrátí aktivní `CFrameWnd` objektu.|
|[CFrameWnd::GetActiveView](#getactiveview)|Vrátí aktivní `CView` objektu.|
|[CFrameWnd::GetControlBar](#getcontrolbar)|Načte ovládací panel.|
|[CFrameWnd::GetDockState](#getdockstate)|Načte stav Ukotvit okno rámce.|
|[CFrameWnd::GetMenuBarState](#getmenubarstate)|Načte stav v nabídce v aktuální aplikaci knihovny MFC.|
|[CFrameWnd::GetMenuBarVisibility](#getmenubarvisibility)|Označuje, zda je výchozí chování v nabídce v aktuální aplikaci knihovny MFC skrytý nebo viditelný.|
|[CFrameWnd::GetMessageBar](#getmessagebar)|Vrací ukazatel na stavovém řádku patřící do okna rámce.|
|[CFrameWnd::GetMessageString](#getmessagestring)|Načte zprávu odpovídající ID příkazu.|
|[CFrameWnd::GetTitle](#gettitle)|Načte název panelu související ovládací prvek.|
|[CFrameWnd::InitialUpdateFrame](#initialupdateframe)|Způsobí, že `OnInitialUpdate` členská funkce, které patří do všech zobrazení v okně rámce, která se má volat.|
|[CFrameWnd::InModalState](#inmodalstate)|Vrátí hodnotu určující, zda je okno rámce v modálního stavu.|
|[CFrameWnd::IsTracking](#istracking)|Určuje, pokud je aktuálně přesunutí příčky.|
|[CFrameWnd::LoadAccelTable](#loadacceltable)|Volání za účelem načtení tabulky akcelerátorů.|
|[CFrameWnd::LoadBarState](#loadbarstate)|Volání za účelem obnovení nastavení panelu ovládacího prvku.|
|[CFrameWnd::LoadFrame](#loadframe)|Volání za účelem dynamicky vytvořit okno rámce z informací o prostředcích.|
|[CFrameWnd::NegotiateBorderSpace](#negotiateborderspace)|Vyjednává ohraničení místo v okně rámce.|
|[CFrameWnd::OnBarCheck](#onbarcheck)|Volá se vždy, když je provedena akce na zadaný ovládací prvek panelu.|
|[CFrameWnd::OnContextHelp](#oncontexthelp)|Zpracovává SHIFT + F1 nápovědy pro místní položky.|
|[CFrameWnd::OnSetPreviewMode](#onsetpreviewmode)|Nastaví oknu hlavního rámce do a z režimu náhledu.|
|[CFrameWnd::OnUpdateControlBarMenu](#onupdatecontrolbarmenu)|Volá se rozhraním, když dojde k aktualizaci příslušné nabídky.|
|[CFrameWnd::RecalcLayout](#recalclayout)|Přemístí pruhů ovládacího prvku `CFrameWnd` objektu.|
|[CFrameWnd::SaveBarState](#savebarstate)|Volání za účelem uložení nastavení panelu ovládacího prvku.|
|[CFrameWnd::SetActivePreviewView](#setactivepreviewview)|Určuje zadané zobrazení aktivní zobrazení pro náhled ve formátu RTF.|
|[CFrameWnd::SetActiveView](#setactiveview)|Nastaví aktivní `CView` objektu.|
|[CFrameWnd::SetDockState](#setdockstate)|Chcete-li ukotvit okno rámce v hlavním okně volání.|
|[CFrameWnd::SetMenuBarState](#setmenubarstate)|Nastaví stav v nabídce v aktuální aplikaci knihovny MFC pro seznamy skrytých nebo zobrazených.|
|[CFrameWnd::SetMenuBarVisibility](#setmenubarvisibility)|Nastaví výchozí chování nabídky v aktuální aplikaci knihovny MFC, která bude skrytý nebo viditelný.|
|[CFrameWnd::SetMessageText](#setmessagetext)|Nastaví text standardní stavový řádek.|
|[CFrameWnd::SetProgressBarPosition](#setprogressbarposition)|Nastaví aktuální pozici pro Windows 7 indikátoru průběhu zobrazí na hlavním panelu.|
|[CFrameWnd::SetProgressBarRange](#setprogressbarrange)|Nastaví rozsah indikátoru průběhu Windows 7 na hlavním panelu.|
|[CFrameWnd::SetProgressBarState](#setprogressbarstate)|Nastaví typ a stav indikátoru průběhu zobrazí na hlavním panelu tlačítko.|
|[CFrameWnd::SetTaskbarOverlayIcon](#settaskbaroverlayicon)|Přetíženo. Překrytí se vztahuje na hlavním panelu tlačítko označující stav aplikace nebo oznámení pro uživatele.|
|[CFrameWnd::SetTitle](#settitle)|Nastaví název panelu související ovládací prvek.|
|[CFrameWnd::ShowControlBar](#showcontrolbar)|Volání za účelem zobrazit panel ovládacího prvku.|
|[CFrameWnd::ShowOwnedWindows](#showownedwindows)|Zobrazí všechny systémy windows, které jsou potomky `CFrameWnd` objektu.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CFrameWnd::OnCreateClient](#oncreateclient)|Vytvoří okno klienta pro rámec.|
|[CFrameWnd::OnHideMenuBar](#onhidemenubar)|Volá se před skryté v nabídce v aktuální aplikaci knihovny MFC.|
|[CFrameWnd::OnShowMenuBar](#onshowmenubar)|Volá se před zobrazením z nabídky aktuální aplikace knihovny MFC.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CFrameWnd::m_bAutoMenuEnable](#m_bautomenuenable)|Ovládací prvky automatické povolit nebo zakázat funkce pro položky nabídky.|
|[CFrameWnd::rectDefault](#rectdefault)|Předá statické `CRect` jako parametr při vytváření `CFrameWnd` objektu, který chcete povolit Windows zvolte v okně počáteční velikost a umístění.|

## <a name="remarks"></a>Poznámky

Chcete-li vytvořit okno rámce užitečné pro vaši aplikaci, odvoďte třídu z `CFrameWnd`. Přidání členské proměnné do odvozené třídy k ukládání dat, které jsou specifické pro vaši aplikaci. Implementujte popisovač zprávy členské funkce a napište zprávu, mapování v odvozené třídě k určení, co se stane, když zprávy jsou přesměrovány do okna.

Existují tři způsoby, jak vytvořit okno rámce:

- Vytvořit přímo pomocí [vytvořit](#create).

- Vytvořit přímo pomocí [loadframe –](#loadframe).

- Konstrukce nepřímo pomocí šablony dokumentu.

Před voláním buď `Create` nebo `LoadFrame`, je nutné vytvořit objekt oken s rámečkem na haldě pomocí jazyka C++ **nové** operátor. Před voláním `Create`, budete taky moct registrovat třídu okna s [afxregisterwndclass –](../../mfc/reference/application-information-and-management.md#afxregisterwndclass) globální funkce nastavit ikonu a třída styly pro rámec.

Použití `Create` členskou funkci pro předání parametrů vytváření rámce jako okamžité argumenty.

`LoadFrame` vyžaduje méně argumentů než `Create`a místo toho načte většinu jeho výchozími hodnotami z prostředků, včetně titulek rámce, ikony, tabulky akcelerátorů a nabídky. Aby byl přístupný `LoadFrame`, tyto prostředky musí mít stejné ID prostředku (například IDR_MAINFRAME).

Když `CFrameWnd` objekt obsahuje zobrazení a dokumenty, jsou vytvořena nepřímo rozhraním namísto přímo programátorem. `CDocTemplate` Objekt orchestruje vytváření rámce, vytvoření nadřazeného zobrazení a připojení zobrazení k příslušné dokumentu. Parametry `CDocTemplate` zadejte konstruktoru `CRuntimeClass` tři třídy zahrnuty (dokument, rámce a zobrazení). A `CRuntimeClass` objektu se používá v rámci rozhraní dynamicky se vytvářejí nové rámce, když uživatel zadá (třeba pomocí příkazu soubor nový nebo více okno Nový příkaz dokumentu (MDI interface)).

Z odvozené třídy oken s rámečkem `CFrameWnd` musí být deklarován s DECLARE_DYNCREATE v pořadí pro výše uvedené mechanismus RUNTIME_CLASS fungovat správně.

A `CFrameWnd` obsahuje výchozí implementace provádět následující funkce hlavní okno v typické aplikaci pro Windows:

- A `CFrameWnd` okno rámce uchovává informace o aktuálně aktivní zobrazení, která je nezávislá aktivního okna Windows nebo aktuální vstupní fokus. Při opětovné aktivaci rámce aktivní vlastnosti view zasláno oznámení, voláním `CView::OnActivateView`.

- Příkaz zprávy a mnoho běžných zprávy oznámení rámce, včetně těch, které zpracovává `OnSetFocus`, `OnHScroll`, a `OnVScroll` funkce `CWnd`, jsou delegovaní `CFrameWnd` okno rámce k aktuálně aktivnímu zobrazení.

- Zobrazit aktuálně aktivní (nebo aktuálně aktivní podřízeným oknem rámce MDI v případě rámce MDI), můžete určit titulek okna rámce. Tuto funkci můžete zakázat tím, že vypíná FWS_ADDTOTITLE bit stylu okna rámce.

- A `CFrameWnd` okno rámce spravuje umisťování ovládacích panelů, zobrazení a další podřízených oken v klientské oblasti okna rámce. Okno rámce také provádí doby nečinnosti aktualizace panelu nástrojů a další tlačítka na ovládacím panelu. A `CFrameWnd` okno rámce má také výchozí implementace příkazy pro přepínání zapnutí a vypnutí nástrojů a stavový řádek.

- A `CFrameWnd` spravuje hlavní nabídek okna rámce. Když se zobrazí místní nabídky, okna rámce používá mechanismus UPDATE_COMMAND_UI k určení položky nabídky, které by měl povolený, zakázaný nebo zaškrtnuté políčko. Když uživatel vybere položku nabídky, okna rámce aktualizuje stavový řádek s řetězec zprávy pro tento příkaz.

- A `CFrameWnd` má okno rámce, který automaticky převádí klávesové zkratky tabulky akcelerátorů volitelné.

- A `CFrameWnd` okno rámce má ID volitelné nápovědy sady s `LoadFrame` , který se používá pro kontextové nápovědy. Okno rámce je hlavní orchestrator semimodální stavy, jako je například režimy Náhled tisku a kontextové nápovědy (SHIFT + F1).

- A `CFrameWnd` okno rámce otevřete soubor ze souboru Správce přetáhnout v okně rámce. Pokud přípona souboru je zaregistrované a přidružené k aplikaci, okno rámce jsou reaguje na dynamických dat (DDE) exchange požadavku na otevření, ke které dochází, když uživatel otevře soubor dat ve Správci souborů, nebo když `ShellExecute` je volána funkce Windows.

- Pokud okno rámce je hlavní okno aplikace (to znamená `CWinThread::m_pMainWnd`), když uživatel nezavře aplikaci, okno rámce vyzve uživatele k uložte všechny upravené dokumenty (pro `OnClose` a `OnQueryEndSession`).

- Pokud okno rámce je hlavní okno aplikace, je okno rámce kontext spuštění WinHelp. Zavření okna rámce vypne WINHELP. Soubor EXE, pokud byl spuštěn pro nápovědu pro tuto aplikaci.

Nepoužívejte C++ **odstranit** operátor zničit okno rámce. Místo nich se používá `CWnd::DestroyWindow`. `CFrameWnd` Provádění `PostNcDestroy` odstraní při zničení okně objekt jazyka C++. Když uživatel zavře okno rámce, výchozí `OnClose` obslužná rutina zavolá `DestroyWindow`.

Další informace o `CFrameWnd`, naleznete v tématu [rámce Windows](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CFrameWnd`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

##  <a name="activateframe"></a>  CFrameWnd::ActivateFrame

Voláním této členské funkce pro aktivaci a obnoví okno rámce tak, aby se viditelné a dostupné pro uživatele.

```
virtual void ActivateFrame(int nCmdShow = -1);
```

### <a name="parameters"></a>Parametry

*nCmdShow*<br/>
Určuje parametr předat [CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow). Ve výchozím nastavení je rámec uvedeny a správně obnoveny.

### <a name="remarks"></a>Poznámky

Tato členská funkce je obvykle volána po události bez uživatelského rozhraní DDE, OLE nebo jiná událost, kterou může zobrazit okno rámce nebo jeho obsah pro uživatele.

Výchozí implementace aktivuje rámce a ukončí na něm na začátek pořadí vykreslování, v případě potřeby provede tytéž kroky jako při oknu hlavního rámce.

Přepište tato členská funkce, chcete-li změnit způsob aktivace objektu frame. Například můžete vynutit podřízených oken MDI chcete maximalizovat. Přidat správnou funkčnost a potom voláním verzi základní třídy s explicitní *nCmdShow*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#1](../../mfc/reference/codesnippet/cpp/cframewnd-class_1.cpp)]

##  <a name="beginmodalstate"></a>  CFrameWnd::BeginModalState

Voláním této členské funkce, aby modální okno rámce.

```
virtual void BeginModalState();
```

##  <a name="cframewnd"></a>  CFrameWnd::CFrameWnd

Vytvoří `CFrameWnd` objektu, ale nevytváří žádné viditelné rámce okna.

```
CFrameWnd();
```

### <a name="remarks"></a>Poznámky

Volání `Create` vytvořit okno viditelné.

##  <a name="create"></a>  CFrameWnd::Create

Volání k vytváření a inicializace okna rámce Windows přidružené `CFrameWnd` objektu.

```
virtual BOOL Create(
    LPCTSTR lpszClassName,
    LPCTSTR lpszWindowName,
    DWORD dwStyle = WS_OVERLAPPEDWINDOW,
    const RECT& rect = rectDefault,
    CWnd* pParentWnd = NULL,
    LPCTSTR lpszMenuName = NULL,
    DWORD dwExStyle = 0,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Parametry

*lpszClassName*<br/>
Odkazuje na řetězec znaků zakončené znakem null, která pojmenuje třídu Windows. Název třídy může být jakýkoli název zaregistrované `AfxRegisterWndClass` globální funkce nebo `RegisterClass` funkce Windows. Pokud má hodnotu NULL, používá předdefinované výchozí `CFrameWnd` atributy.

*lpszWindowName*<br/>
Odkazuje na řetězec znaků zakončené znakem null představující název okna. Používá jako text záhlaví.

*dwStyle*<br/>
Určuje, okno [styl](../../mfc/reference/styles-used-by-mfc.md#window-styles) atributy. Zahrňte FWS_ADDTOTITLE styl, pokud chcete, aby záhlavím, aby automaticky zobrazovaný název dokumentu v okně.

*Rect*<br/>
Určuje velikost a pozice okna. *RectDefault* hodnota umožňuje určit velikost a umístění nového okna Windows.

*pParentWnd*<br/>
Určuje nadřazené okno rámce okna. Tento parametr by měl mít hodnotu NULL pro oken s rámečkem nejvyšší úrovně.

*lpszMenuName*<br/>
Určuje název prostředku nabídky pro použití s oknem. MAKEINTRESOURCE použijte, pokud v nabídce má celočíselný identifikátor ID namísto řetězce. Tento parametr může mít hodnotu NULL.

*dwExStyle*<br/>
Určuje okno Rozšířené [styl](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) atributy.

*pContext*<br/>
Určuje ukazatel [ccreatecontext –](../../mfc/reference/ccreatecontext-structure.md) struktury. Tento parametr může mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se inicializace je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Vytvoření `CFrameWnd` objektu ve dvou krocích. Nejprve volat konstruktor, který vytvoří `CFrameWnd` objekt a následně zavolat `Create`, vytvoří okno rámce Windows a připojí ho k `CFrameWnd` objektu. `Create` Inicializuje název třídy okna a okna názvu a zaregistruje výchozí hodnoty pro jeho styl, nadřazený a související nabídky.

Použití `LoadFrame` spíše než `Create` načíst okno rámce z prostředku místo zadávání argumentů.

##  <a name="createview"></a>  CFrameWnd::CreateView

Volání `CreateView` vytvoření zobrazení v rámci.

```
CWnd* CreateView(
    CCreateContext* pContext,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>Parametry

*pContext*<br/>
Určuje typ zobrazení a dokumentu.

*nID*<br/>
Číslo ID zobrazení.

### <a name="return-value"></a>Návratová hodnota

Ukazatel `CWnd` objekt Pokud úspěšné; jinak hodnota NULL.

### <a name="remarks"></a>Poznámky

Použijte tato členská funkce k vytvoření "zobrazení", které nejsou `CView`-odvozené v rámci. Po volání `CreateView`, musíte ručně nastavit zobrazení na aktivní a nastavit ji uvidí; tyto úlohy nejsou automaticky provádí `CreateView`.

##  <a name="dockcontrolbar"></a>  CFrameWnd::DockControlBar

Způsobí, že se ovládací panel Ukotvit okno rámce.

```
void DockControlBar(
    CControlBar* pBar,
    UINT nDockBarID = 0,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
Odkazuje na ovládacím panelu, ukotvit.

*nDockBarID*<br/>
Určuje, které strany okna rámce, které je potřeba zvážit ukotvení. Může být 0, nebo jeden nebo více z následujících akcí:

- Ukotvit AFX_IDW_DOCKBAR_TOP do horní části okna rámce.

- Ukotvit AFX_IDW_DOCKBAR_BOTTOM do dolní části okna rámce.

- Ukotvit AFX_IDW_DOCKBAR_LEFT na levé straně okna rámce.

- Ukotvit AFX_IDW_DOCKBAR_RIGHT na pravé straně okna rámce.

Pokud je 0, ovládacím panelu lze ukotvit stran povoleno pro ukotvení v rámci okna cílové.

*lpRect*<br/>
Určuje, v souřadnicovém systému obrazovky, ve kterém se ovládací panel ukotvit myši v neklientské oblasti okna rámce cílové.

### <a name="remarks"></a>Poznámky

Ovládací panel budou ukotveny na jeden z okrajů okna rámce zadanou ve volání do obou [CControlBar::EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking) a [CFrameWnd::EnableDocking](#enabledocking). Zvolený na straně je určeno *nDockBarID*.

##  <a name="enabledocking"></a>  CFrameWnd::EnableDocking

Voláním této funkce umožňující ukotvitelné ovládací pruhy v okně s rámečkem.

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Parametry

*dwDockStyle*<br/>
Určuje, které strany okna rámce může sloužit jako ukotvení lokalit pro ovládacích panelů. Může být jeden nebo více z následujících akcí:

- CBRS_ALIGN_TOP umožňuje ukotvení v horní části klientské oblasti.

- CBRS_ALIGN_BOTTOM umožňuje ukotvení v dolní části klientské oblasti.

- CBRS_ALIGN_LEFT umožňuje Ukotvování na levé straně od klientské oblasti.

- CBRS_ALIGN_RIGHT umožňuje ukotvení na pravé straně, od klientské oblasti.

- CBRS_ALIGN_ANY umožňuje ukotvení na žádné straně od klientské oblasti.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení, budou ovládací pruhy ukotven k okraji okna rámce v následujícím pořadí: horní, dolní, levý, pravý.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CToolBar::Create](../../mfc/reference/ctoolbar-class.md#create).

##  <a name="endmodalstate"></a>  CFrameWnd::EndModalState

Voláním této členské funkce, chcete-li změnit okno rámce od modálních pro nemodální.

```
virtual void EndModalState();
```

### <a name="remarks"></a>Poznámky

`EndModalState` všechny oken zakázal [BeginModalState](#beginmodalstate).

##  <a name="floatcontrolbar"></a>  CFrameWnd::FloatControlBar

Voláním této funkce způsobí ovládací panel pro nesmí být ukotveno okno rámce.

```
void FloatControlBar(
    CControlBar* pBar,
    CPoint point,
    DWORD dwStyle = CBRS_ALIGN_TOP);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
Odkazuje na ovládacím panelu k být ponechán v neurčitém stavu.

*point*<br/>
Umístění, v souřadnicovém systému obrazovky, kde budou umístěné levého horního rohu ovládacího panelu.

*dwStyle*<br/>
Určuje, zda chcete-li zarovnat ovládací panel vodorovně nebo svisle v rámci jeho nový objekt okna rámce. Může být některý z následujících akcí:

- CBRS_ALIGN_TOP orientuje ovládacím panelu svisle.

- CBRS_ALIGN_BOTTOM orientuje ovládacím panelu svisle.

- CBRS_ALIGN_LEFT orientuje ovládacím panelu vodorovně.

- CBRS_ALIGN_RIGHT orientuje ovládacím panelu vodorovně.

Pokud styly jsou předány zadání vodorovné a svislé orientaci, panelu nástrojů se být orientovaný vodorovně.

### <a name="remarks"></a>Poznámky

Obvykle se to při spuštění aplikace při program je obnovení nastavení z předchozího zpracování.

Tato funkce je volána rozhraním, když uživatel způsobí, že operace přetažení uvolněním levé tlačítko myši při přetažení přes umístění, které není k dispozici pro ukotvení panelu ovládacího prvku.

##  <a name="getactivedocument"></a>  CFrameWnd::GetActiveDocument

Voláním této členské funkce na ukazatel na aktuální `CDocument` připojen k aktivnímu zobrazení. aktuální.

```
virtual CDocument* GetActiveDocument();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktuální [CDocument](../../mfc/reference/cdocument-class.md). Pokud neexistuje žádný aktuální dokument, vrátí hodnotu NULL.

##  <a name="getactiveframe"></a>  CFrameWnd::GetActiveFrame

Voláním této členské funkce získání ukazatele na aktivní více dokumentů (MDI) interface podřízené okno okna rámce MDI.

```
virtual CFrameWnd* GetActiveFrame();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktivní podřízené okno MDI. Pokud aplikace je aplikace SDI nebo okna rámce MDI nemá žádné aktivní dokument implicitní **to** bude vrácen ukazatel.

### <a name="remarks"></a>Poznámky

Pokud neexistuje žádná aktivní podřízený formulář MDI nebo aplikace je rozhraní jednoho dokumentu (SDI), implicitní **to** je vrácen ukazatel.

##  <a name="getactiveview"></a>  CFrameWnd::GetActiveView

Voláním této členské funkce na ukazatel na aktivní vlastnosti view (pokud existuje) připojené k okně s rámečkem ( `CFrameWnd`).

```
CView* GetActiveView() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktuální [CView](../../mfc/reference/cview-class.md). Pokud neexistuje žádné aktuální zobrazení, vrátí hodnotu NULL.

### <a name="remarks"></a>Poznámky

Tato funkce vrátí hodnotu NULL při volání okna hlavního rámce MDI ( `CMDIFrameWnd`). V aplikaci MDI oknem hlavního rámce MDI nemá zobrazení s ním spojená. Místo toho každé jednotlivé podřízené okno ( `CMDIChildWnd`) má jednu nebo více přidružených zobrazení. Nejprve hledání aktivní podřízené okno MDI a pak pro podřízené okno hledání aktivní zobrazení je možné získat aktivní zobrazení v aplikaci MDI. Aktivní podřízené okno MDI najdete voláním funkce `MDIGetActive` nebo `GetActiveFrame` jak je ukázáno v následujícím:

[!code-cpp[NVC_MFCWindowing#2](../../mfc/reference/codesnippet/cpp/cframewnd-class_2.cpp)]

##  <a name="getcontrolbar"></a>  CFrameWnd::GetControlBar

Volání `GetControlBar` získat přístup k panelu ovládacího prvku, který je spojen s ID.

```
CControlBar* GetControlBar(UINT nID);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Číslo ID ovládacího panelu.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na ovládací panel, který je spojen s ID.

### <a name="remarks"></a>Poznámky

*NID* parametr odkazuje na jedinečný identifikátor předán `Create` metoda ovládacím panelu. Další informace o ovládacích panelů, najdete v tématu s názvem [ovládací pruhy](../../mfc/control-bars.md).

`GetControlBar` vrátí ovládací panel, i když je plovoucí a proto není aktuálně podřízeného okna rámce.

##  <a name="getdockstate"></a>  CFrameWnd::GetDockState

Voláním této členské funkce ukládat informace o okno rámce ovládací pruhy ve stavu `CDockState` objektu.

```
void GetDockState(CDockState& state) const;
```

### <a name="parameters"></a>Parametry

*state*<br/>
Obsahuje informace o aktuálním stavu okno rámce ovládací pruhy po návratu.

### <a name="remarks"></a>Poznámky

Pak můžou zapisovat obsah `CDockState` do úložiště pomocí `CDockState::SaveState` nebo `Serialize`. Pokud chcete později obnovit do předchozího stavu ovládací pruhy, načtení stavu se `CDockState::LoadState` nebo `Serialize`, zavolejte `SetDockState` vyrovnat ovládací pruhy okno rámce do předchozího stavu.

##  <a name="getmenubarstate"></a>  CFrameWnd::GetMenuBarState

Načte stav v nabídce v aktuální aplikaci knihovny MFC.

```
virtual DWORD GetMenuBarState();
```

### <a name="return-value"></a>Návratová hodnota

Návratová hodnota může mít následující hodnoty:

- AFX_MBS_VISIBLE (0x01) – v nabídce je viditelný.

- AFX_MBS_HIDDEN (0x02) - skryté v nabídce.

### <a name="remarks"></a>Poznámky

Pokud dojde k chybě za běhu, tato metoda nepodmíněné výrazy v režimu ladění a vyvolá výjimku, odvozený z [cexception –](../../mfc/reference/cexception-class.md) třídy.

##  <a name="getmenubarvisibility"></a>  CFrameWnd::GetMenuBarVisibility

Určuje, zda výchozí stav v nabídce v aktuální aplikaci knihovny MFC je skrytý nebo viditelný.

```
virtual DWORD CFrameWnd::GetMenuBarVisibility();
```

### <a name="return-value"></a>Návratová hodnota

Tato metoda vrátí jednu z následujících hodnot:

- AFX_MBV_KEEPVISIBLE (0x01) – v nabídce se zobrazí na všech časy a ve výchozím nastavení nemá fokus.

- AFX_MBV_DISPLAYONFOCUS (0x02) – v nabídce je ve výchozím nastavení skrytá. Pokud je skrytý nabídky, stiskněte klávesu ALT k zobrazení nabídky a přiřaďte mu fokus. Pokud se zobrazí v nabídce, stisknutím klávesy ALT nebo ESC ho chcete skrýt.

- AFX_MBV_ DISPLAYONFOCUS (0x02) &#124; AFX_MBV_DISPLAYONF10 (0x04) (bitová kombinace (nebo)) – v nabídce je ve výchozím nastavení skrytá. Když je skrytý nabídky, stiskněte klávesu F10 zobrazení nabídky a přiřaďte jí fokus. Pokud se zobrazí v nabídce, stiskněte klávesu F10 Chcete-li přepnout fokus zapnout nebo vypnout v nabídce. V nabídce se zobrazí, dokud nestisknete klávesu ALT nebo ESC ho chcete skrýt.

### <a name="remarks"></a>Poznámky

Pokud dojde k chybě za běhu, tato metoda nepodmíněné výrazy v režimu ladění a vyvolá výjimku, odvozený z [cexception –](../../mfc/reference/cexception-class.md) třídy.

##  <a name="getmessagebar"></a>  CFrameWnd::GetMessageBar

Voláním této členské funkce získání ukazatele na stavovém řádku.

```
virtual CWnd* GetMessageBar();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na okno stavový řádek.

##  <a name="getmessagestring"></a>  CFrameWnd::GetMessageString

Přepsání této funkce můžete poskytnout vlastní řetězce pro ID příkazů.

```
virtual void GetMessageString(
    UINT nID,
    CString& rMessage) const;
```

### <a name="parameters"></a>Parametry

*nID*<br/>
ID prostředku požadované zprávy.

*rMessage*<br/>
`CString` objekt, do kterého chcete zprávu.

### <a name="remarks"></a>Poznámky

Výchozí implementace jednoduše načte řetězec určený *nID* ze souboru prostředků. Tato funkce je volána rozhraním, když řetězec zprávy ve stavovém řádku musí aktualizovat.

##  <a name="gettitle"></a>  CFrameWnd::GetTitle

Načte název objekt okna.

```
CString GetTitle() const;
```

### <a name="return-value"></a>Návratová hodnota

A [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt, který obsahuje název aktuální objekt okna.

##  <a name="initialupdateframe"></a>  CFrameWnd::InitialUpdateFrame

Volání `IntitialUpdateFrame` po vytvoření nový rámec s `Create`.

```
void InitialUpdateFrame(
    CDocument* pDoc,
    BOOL bMakeVisible);
```

### <a name="parameters"></a>Parametry

*pDoc*<br/>
Ukazuje na dokument, ke kterému je přidružené okno rámce. Může mít hodnotu NULL.

*bMakeVisible*<br/>
Hodnota TRUE určuje to, že rámec by měla být viditelné a aktivní. Pokud má hodnotu FALSE, jsou dostupná bez následníků.

### <a name="remarks"></a>Poznámky

To způsobí, že všechna zobrazení v tomto okně rámce pro příjem jejich `OnInitialUpdate` volání.

Také pokud nebyl k dispozici dříve aktivní zobrazení, primární zobrazení okna rámce se stane aktivní. Primární zobrazení je zobrazení s ID AFX_IDW_PANE_FIRST podřízený. Nakonec okno rámce je nastavena jako viditelná Pokud *bMakeVisible* nenulové. Pokud *bMakeVisible* je 0, aktuálním zaměřením a stav viditelnosti okna rámce zůstane beze změny. Není nutné volat tuto funkci při použití v rámci implementace nový soubor a soubor otevřít.

##  <a name="inmodalstate"></a>  CFrameWnd::InModalState

Voláním této členské funkce zkontrolujte, jestli je okno rámce modálním nebo nemodálním.

```
BOOL InModalState() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud ano, ale jinak 0.

##  <a name="istracking"></a>  CFrameWnd::IsTracking

Voláním této členské funkce k určení, pokud je aktuálně přesunutí příčky v okně.

```
BOOL IsTracking() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud operace rozdělovač probíhá; jinak 0.

##  <a name="loadacceltable"></a>  CFrameWnd::LoadAccelTable

Volání za účelem načtení tabulky určený akcelerátor.

```
BOOL LoadAccelTable(LPCTSTR lpszResourceName);
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Určuje název prostředku akcelerátoru. Pokud prostředek je identifikován s celé číslo ID. použijte MAKEINTRESOURCE

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud tabulky akcelerátorů byl úspěšně načten. jinak 0.

### <a name="remarks"></a>Poznámky

Najednou lze načíst pouze jednu tabulku.

Tabulky akcelerátoru načtené z prostředků jsou uvolněny automaticky při ukončení aplikace.

Při volání `LoadFrame` vytvořit okno rámce, rozhraní načte tabulky akcelerátorů spolu s prostředky nabídky a ikony a následné volání tato členská funkce je zbytečné.

##  <a name="loadbarstate"></a>  CFrameWnd::LoadBarState

Voláním této funkce Obnovení nastavení každý ovládací prvek panel vlastní okna rámce.

```
void LoadBarState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
Název oddílu v souboru inicializace (INI) nebo klíče v registru Windows ukládat informace o stavu.

### <a name="remarks"></a>Poznámky

Informace o obnovení zahrnuje viditelnost, vodorovné nebo svislé orientaci, dokovací stavu a pozice ovládacích panelů.

Nastavení chcete obnovit, musí být zapsané do registru před voláním `LoadBarState`. Zápis informací do registru voláním [CWinApp::SetRegistryKey](../../mfc/reference/cwinapp-class.md#setregistrykey). Zápis informací do souboru INI voláním [SaveBarState](#savebarstate).

##  <a name="loadframe"></a>  CFrameWnd::LoadFrame

Volání za účelem dynamicky vytvořit okno rámce z informací o prostředcích.

```
virtual BOOL LoadFrame(
    UINT nIDResource,
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,
    CWnd* pParentWnd = NULL,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Parametry

*nIDResource*<br/>
ID sdílené prostředky spojené s oknem rámce.

*dwDefaultStyle*<br/>
Rámce [styl](../../mfc/reference/styles-used-by-mfc.md#window-styles). Zahrňte FWS_ADDTOTITLE styl, pokud chcete, aby záhlavím, aby automaticky zobrazovaný název dokumentu v okně.

*pParentWnd*<br/>
Ukazatel na nadřazeného rámce.

*pContext*<br/>
Ukazatel [ccreatecontext –](../../mfc/reference/ccreatecontext-structure.md) struktury. Tento parametr může mít hodnotu NULL.

### <a name="remarks"></a>Poznámky

Vytvoření `CFrameWnd` objektu ve dvou krocích. Nejprve volat konstruktor, který vytvoří `CFrameWnd` objekt a následně zavolat `LoadFrame`, který načte okna rámce Windows a souvisejících zdrojů a připojí okno rámce `CFrameWnd` objektu. *NIDResource* parametr určuje, v nabídce, tabulky akcelerátorů, ikona a prostředek řetězce názvu pro okno rámce.

Použití `Create` členskou funkci spíše než `LoadFrame` Pokud chcete zadat všechny parametry vytvoření okno rámce.

Rámec volá `LoadFrame` když vytvoří okno rámce pomocí objektu šablony dokumentu.

Rozhraní používá *pContext* argument určit objekty, které chcete připojit do okna rámce, včetně všech obsažených objektů zobrazení. Můžete nastavit *pContext* argumentu na hodnotu NULL při volání `LoadFrame`.

##  <a name="m_bautomenuenable"></a>  CFrameWnd::m_bAutoMenuEnable

Když tomuto datovému členu je povolené (což je výchozí hodnota), položky nabídky, které nemají žádné obslužné rutiny ON_UPDATE_COMMAND_UI nebo ON_COMMAND se automaticky zakáže při uživatel stáhne nabídky.

```
BOOL m_bAutoMenuEnable;
```

### <a name="remarks"></a>Poznámky

Položky nabídky, které mají obslužné rutiny ON_COMMAND, ale žádná obslužná rutina ON_UPDATE_COMMAND_UI bude automaticky povoleno.

Pokud je nastavena k tomuto datovému členu, položky nabídky jsou automaticky povoleny stejným způsobem, že jsou povolené tlačítka na panelu nástrojů.

> [!NOTE]
> `m_bAutoMenuEnable` nemá žádný vliv na položky nabídek nejvyšší úrovně.

Tento datový člen zjednodušuje provádění volitelné příkazy na základě aktuálního výběru a snižuje nutnost psaní ON_UPDATE_COMMAND_UI obslužné rutiny pro povolení a zákaz položek nabídky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#3](../../mfc/reference/codesnippet/cpp/cframewnd-class_3.cpp)]

##  <a name="negotiateborderspace"></a>  CFrameWnd::NegotiateBorderSpace

Voláním této členské funkce pro vyjednávání ohraničení místo v okně s rámečkem během místní aktivace OLE.

```
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,
    LPRECT lpRectBorder);
```

### <a name="parameters"></a>Parametry

*nBorderCmd*<br/>
Obsahuje nejméně jednu z následujících hodnot z `enum BorderCmd`:

- `borderGet` = 1

- `borderRequest` = 2

- `borderSet` = 3

*lpRectBorder*<br/>
Ukazatel [RECT](/windows/desktop/api/windef/ns-windef-tagrect) struktury nebo [crect –](../../atl-mfc-shared/reference/crect-class.md) objekt, který určuje souřadnice ohraničení.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce je `CFrameWnd` provádění OLE ohraničení místo vyjednávání.

##  <a name="onbarcheck"></a>  CFrameWnd::OnBarCheck

Volá se vždy, když je provedena akce na zadaný ovládací prvek panelu.

```
afx_msg BOOL OnBarCheck(UINT nID);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
ID ovládacího prvku panelu zobrazení.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud ovládací panel existoval; jinak 0.

##  <a name="oncontexthelp"></a>  CFrameWnd::OnContextHelp

Zpracovává SHIFT + F1 nápovědy pro místní položky.

```
afx_msg void OnContextHelp();
```

### <a name="remarks"></a>Poznámky

Povolit kontextové nápovědy, je nutné přidat

[!code-cpp[NVC_MFCDocViewSDI#16](../../mfc/codesnippet/cpp/cframewnd-class_4.cpp)]

příkaz k vaší `CFrameWnd` třídy mapu zpráv a také přidat záznam tabulky akcelerátoru, obvykle SHIFT + F1, chcete-li povolit tuto funkci člena.

Pokud je vaše aplikace OLE kontejnerem, `OnContextHelp` umístí všechny místní položky obsažené v rámci objekt okna rámce do režimu nápovědy. Změní se kurzor na šipku, otazník a uživatel může pak přesuňte ukazatel myši a stiskněte klávesu levým tlačítkem myši a vyberte dialogové okno, okna, nabídky nebo příkazové tlačítko. Tato členská funkce volá funkci Windows `WinHelp` s kontextem nápovědy objekt pod kurzor.

##  <a name="oncreateclient"></a>  CFrameWnd::OnCreateClient

Volá se rozhraním při provádění `OnCreate`.

```
virtual BOOL OnCreateClient(
    LPCREATESTRUCT lpcs,
    CCreateContext* pContext);
```

### <a name="parameters"></a>Parametry

*lpcs*<br/>
Ukazatel Windows [soubor CREATESTRUCT](/windows/desktop/api/winuser/ns-winuser-tagcreatestructa) struktury.

*pContext*<br/>
Ukazatel [ccreatecontext –](../../mfc/reference/ccreatecontext-structure.md) struktury.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Nikdy voláním této funkce.

Vytvoří výchozí implementaci této funkce `CView` objekt z informací uvedených v *pContext*, pokud je to možné.

Přepsání přepsat hodnoty předané v této funkce `CCreateContext` objektu nebo chcete-li změnit vytvoření ovládacích prvků způsob, jak v hlavní klientské oblasti okna rámce. `CCreateContext` Můžete přepsat členy jsou popsány v [ccreatecontext –](../../mfc/reference/ccreatecontext-structure.md) třídy.

> [!NOTE]
>  Nahradit hodnoty předané `CREATESTRUCT` struktury. Jsou pouze informativní. Pokud chcete přepsat obdélníku počáteční okna, například přepsání `CWnd` členskou funkci [PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow).

##  <a name="onhidemenubar"></a>  CFrameWnd::OnHideMenuBar

Tato funkce je volána, když systém se chystá skrytí panelu nabídek v aktuální aplikaci knihovny MFC.

```
virtual void OnHideMenuBar();
```

### <a name="remarks"></a>Poznámky

Tato obslužná rutina události umožňuje vaší aplikaci provést vlastní akce, když systém se chystá skrytí nabídky. V nabídce nemůže zabránit skryté, ale můžete například volat jiné metody načtěte styl nabídky nebo stavu.

##  <a name="onsetpreviewmode"></a>  CFrameWnd::OnSetPreviewMode

Voláním této členské funkce pro nastavení aplikace hlavní okno rámce do a z režimu náhledu.

```
virtual void OnSetPreviewMode(
    BOOL bPreview,
    CPrintPreviewState* pState);
```

### <a name="parameters"></a>Parametry

*bPreview*<br/>
Určuje, jestli se mají umístit aplikace v režimu náhledu. Nastavte na hodnotu TRUE, umístíte do náhledu tisku, FALSE pro režim náhledu zrušit.

*pState*<br/>
Ukazatel `CPrintPreviewState` struktury.

### <a name="remarks"></a>Poznámky

Výchozí implementace zakáže všechny standardní panel nástrojů a zobrazovat v hlavní nabídce a hlavní okno klienta. Tím se změní okna rámce MDI dočasné rámečků oken SDI.

Potlačí tuto členskou funkci přizpůsobení skrytí a zobrazení ovládacích pruhů a jiné části okna rámce během náhledu tisku. Volejte implementaci základní třídy z v rámci přepsaného verze.

##  <a name="onshowmenubar"></a>  CFrameWnd::OnShowMenuBar

Tato funkce je volána, když systém se chystá zobrazení nabídek v aktuální aplikaci knihovny MFC.

```
virtual void OnShowMenuBar();
```

### <a name="remarks"></a>Poznámky

Tato obslužná rutina události umožňuje vaší aplikaci k provedení vlastní akce v nabídce se zobrazí. V nabídce nelze zabránit zobrazení, ale můžete například volat jiné metody načtěte styl nabídky nebo stavu.

##  <a name="onupdatecontrolbarmenu"></a>  CFrameWnd::OnUpdateControlBarMenu

Volá se rozhraním, když dojde k aktualizaci příslušné nabídky.

```
afx_msg void OnUpdateControlBarMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Ukazatel [ccmdui –](../../mfc/reference/ccmdui-class.md) objekt představující nabídky, která vygeneruje příkazu update. Volání obslužné rutiny aktualizace [povolit](../../mfc/reference/ccmdui-class.md#enable) členskou funkci `CCmdUI` objektu *pCmdUI* k aktualizaci uživatelského rozhraní.

##  <a name="recalclayout"></a>  CFrameWnd::RecalcLayout

Volá se rozhraním, když jsou standardní ovládací panely přepínat zapnutí nebo vypnutí nebo při změně velikosti okna rámce.

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Parametry

*bNotify*<br/>
Určuje, zda aktivní položky v místě pro okno rámce obdrží oznámení o změně rozložení. Pokud je hodnota TRUE, je oznámení položky; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Výchozí implementace tato členská funkce se volá `CWnd` členskou funkci `RepositionBars` do umístění v rámci stejně jako v okně hlavní klient ovládací pruhy (obvykle `CView` nebo MDICLIENT).

Potlačí tuto členskou funkci řídit vzhled a chování ovládacích pruhů po změně rozložení okna rámce. Je třeba volejte, pokud ovládací pruhy zapnout nebo vypnout nebo přidat další ovládací prvek panel.

##  <a name="rectdefault"></a>  CFrameWnd::rectDefault

Předá statické `CRect` jako parametr při vytváření okna Povolit Windows zvolte v okně počáteční velikost a umístění.

```
static AFX_DATA const CRect rectDefault;
```

##  <a name="savebarstate"></a>  CFrameWnd::SaveBarState

Voláním této funkce pro ukládání informací o jednotlivých ovládacích pruhů vlastní okna rámce.

```
void SaveBarState(LPCTSTR lpszProfileName) const;
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
Název oddílu v souboru inicializace nebo klíče v registru Windows ukládat informace o stavu.

### <a name="remarks"></a>Poznámky

Tyto informace lze číst ze souboru pomocí inicializace [LoadBarState](#loadbarstate). Informace uložené zahrnují viditelnost, vodorovně nebo svisle orientace ukotvení stav a umístění řádku v ovládacím prvku.

##  <a name="setactivepreviewview"></a>  CFrameWnd::SetActivePreviewView

Určuje zadané zobrazení aktivní zobrazení pro náhled ve formátu RTF.

```
void SetActivePreviewView(CView* pViewNew);
```

### <a name="parameters"></a>Parametry

*pViewNew*<br/>
Ukazatel na zobrazení aktivovat.

### <a name="remarks"></a>Poznámky

##  <a name="setactiveview"></a>  CFrameWnd::SetActiveView

Voláním této členské funkce se nastavit aktivní zobrazení.

```
void SetActiveView(
    CView* pViewNew,
    BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Parametry

*pViewNew*<br/>
Určuje ukazatel [CView](../../mfc/reference/cview-class.md) objekt nebo hodnota NULL pro žádné aktivní zobrazení.

*bNotify*<br/>
Určuje, zda zobrazení informováni o aktivaci. Při hodnotě TRUE se `OnActivateView` se volá pro nové zobrazení; Pokud FALSE, nebude.

### <a name="remarks"></a>Poznámky

Rozhraní bude automaticky voláním této funkce, když uživatel provede změny fokus na zobrazení v rámci okna rámce. Můžete explicitně volat `SetActiveView` změnit fokus na určené zobrazení.

##  <a name="setdockstate"></a>  CFrameWnd::SetDockState

Voláním této členské funkce použít informace o stavu uložené v `CDockState` objekt okna rámce ovládací panely.

```
void SetDockState(const CDockState& state);
```

### <a name="parameters"></a>Parametry

*state*<br/>
Platí pro okno rámce ovládacích panelů uloženého stavu.

### <a name="remarks"></a>Poznámky

Obnovit do předchozího stavu ovládací pruhy, můžete načíst uloženého stavu s `CDockState::LoadState` nebo `Serialize`, pak použijte `SetDockState` vyrovnat okno rámce ovládací panely. Předchozí stav je uložený ve službě `CDockState` objektu `GetDockState`

##  <a name="setmenubarstate"></a>  CFrameWnd::SetMenuBarState

Nastaví stav v nabídce v aktuální aplikaci knihovny MFC pro seznamy skrytých nebo zobrazených.

```
virtual BOOL SetMenuBarState(DWORD nState);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*nState*|[in] Určuje, jestli se má zobrazit nebo skrýt v nabídce. *NInformace* parametr může mít následující hodnoty:<br /><br />-AFX_MBS_VISIBLE (0x01) - zobrazí nabídku, pokud je skrytý, ale nemá žádný vliv, pokud je zobrazen.<br />-AFX_MBS_HIDDEN (0x02) – skryje v nabídce, pokud je zobrazen, ale nemá žádný vliv, pokud je skrytá.|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda úspěšně změní stav nabídky; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Pokud dojde k chybě za běhu, tato metoda nepodmíněné výrazy v režimu ladění a vyvolá výjimku, odvozený z [cexception –](../../mfc/reference/cexception-class.md) třídy.

##  <a name="setmenubarvisibility"></a>  CFrameWnd::SetMenuBarVisibility

Nastaví výchozí chování nabídky v aktuální aplikaci knihovny MFC, která bude skrytý nebo viditelný.

```
virtual void SetMenuBarVisibility(DWORD nStyle);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*nStyle*|[in] Určuje, zda v nabídce je standardně skrytý, nebo je viditelná a má fokus. *NStyle* parametr může mít následující hodnoty:<br /><br />- AFX_MBV_KEEPVISIBLE (0x01) -<br />     V nabídce se zobrazí po celou dobu a ve výchozím nastavení nemá fokus.<br />-AFX_MBV_DISPLAYONFOCUS (0X02)-<br />     V nabídce je ve výchozím nastavení skrytá. Pokud je skrytý nabídky, stiskněte klávesu ALT k zobrazení nabídky a přiřaďte mu fokus. Pokud se zobrazí v nabídce, stiskněte klávesu ALT nebo ESC, chcete-li skrýt nabídku.<br />- AFX_MBV_ DISPLAYONFOCUS (0x02) &#124; AFX_MBV_DISPLAYONF10 (0x04)<br />     (bitová kombinace (nebo)) – v nabídce je ve výchozím nastavení skrytá. Když je skrytý nabídky, stiskněte klávesu F10 zobrazení nabídky a přiřaďte jí fokus. Pokud se zobrazí v nabídce, stiskněte klávesu F10 Chcete-li přepnout fokus zapnout nebo vypnout v nabídce. V nabídce se zobrazí, dokud nestisknete klávesu ALT nebo ESC ho chcete skrýt.|

### <a name="remarks"></a>Poznámky

Pokud hodnota *nStyle* parametr není platný, vyhodnotí tuto metodu v režimu ladění a vyvolá [cinvalidargexception –](../../mfc/reference/cinvalidargexception-class.md) v režimu vydání. V případě jiných chyby za běhu, tato metoda nepodmíněné výrazy v režimu ladění a vyvolá výjimku odvozenou z [cexception –](../../mfc/reference/cexception-class.md) třídy.

Tato metoda má vliv na stav nabídky v aplikace napsané pro Windows Vista nebo novější.

##  <a name="setmessagetext"></a>  CFrameWnd::SetMessageText

Voláním této funkce, které mají být umístěny panelu stavového řádku, který má ID 0 řetězce.

```
void SetMessageText(LPCTSTR lpszText);
void SetMessageText(UINT nID);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
Odkazuje na řetězec, který má být umístěn na stavovém řádku.

*nID*<br/>
Řetězec ID prostředku řetězce umístit na stavovém řádku.

### <a name="remarks"></a>Poznámky

Obvykle se jedná o podokně úplně vlevo a nejdelší, ve stavovém řádku.

##  <a name="setprogressbarposition"></a>  CFrameWnd::SetProgressBarPosition

Nastaví aktuální umístění indikátoru průběhu Windows 7, zobrazí na hlavním panelu.

```
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>Parametry

*nProgressPos*<br/>
Určuje pozici pro nastavení. Musí být v rozsahu nastavil `SetProgressBarRange`.

### <a name="remarks"></a>Poznámky

##  <a name="setprogressbarrange"></a>  CFrameWnd::SetProgressBarRange

Nastaví rozsah indikátoru průběhu Windows 7, zobrazí na hlavním panelu.

```
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>Parametry

*nRangeMin*<br/>
Minimální hodnota.

*nRangeMax*<br/>
Maximální hodnota.

### <a name="remarks"></a>Poznámky

##  <a name="setprogressbarstate"></a>  CFrameWnd::SetProgressBarState

Nastaví typ a stav indikátoru průběhu zobrazí na hlavním panelu tlačítko.

```
void SetProgressBarState(TBPFLAG tbpFlags);
```

### <a name="parameters"></a>Parametry

*tbpFlags*<br/>
Příznaky, které řídí aktuální stav tlačítka průběh. Zadejte pouze jednu z následujících příznaků, protože všechny stavy se vzájemně vylučují: TBPF_NOPROGRESS, TBPF_INDETERMINATE, TBPF_NORMAL, TBPF_ERROR, TBPF_PAUSED.

### <a name="remarks"></a>Poznámky

##  <a name="settaskbaroverlayicon"></a>  CFrameWnd::SetTaskbarOverlayIcon

Přetíženo. Překrytí se vztahuje na tlačítka na hlavním panelu označuje stav aplikace nebo zobrazit uživateli.

```
BOOL SetTaskbarOverlayIcon(
    UINT nIDResource,
    LPCTSTR lpcszDescr);

BOOL SetTaskbarOverlayIcon(
    HICON hIcon,
    LPCTSTR lpcszDescr);
```

### <a name="parameters"></a>Parametry

*nIDResource*<br/>
Určuje Identifikátor prostředku ikony použít jako překrytí. Zobrazit popis *hIcon* podrobnosti.

*lpcszDescr*<br/>
Ukazatel na řetězec, který poskytuje alternativní text verzi informace vyjádřené překrytí, v zájmu usnadnění přístupu.

*hIcon*<br/>
Popisovač ikony pro použití jako překrytí. To by měla být malá ikona měření 16 × 16 pixelů při 96 bodů na palec (dpi). Pokud překrytí ikony byl již použit pro tlačítko na hlavním panelu, že existující překrytí se nahradí. Tato hodnota může být NULL. Jak se zpracovává hodnotu NULL, závisí na Určuje, zda tlačítko na hlavním panelu představuje jednom okně nebo skupinu systému windows. Zodpovídá volající aplikace k bezplatným *hIcon* když je už nepotřebujete.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE v případě úspěchu; FALSE, pokud verze operačního systému je menší než Windows 7 nebo pokud dojde k chybě při nastavení na ikonu.

### <a name="remarks"></a>Poznámky

##  <a name="settitle"></a>  CFrameWnd::SetTitle

Nastaví název objekt okna.

```
void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>Parametry

*lpszTitle*<br/>
Ukazatel na znak řetězec obsahující název objekt okna.

##  <a name="showcontrolbar"></a>  CFrameWnd::ShowControlBar

Voláním této členské funkce k zobrazení nebo skrytí panelu ovládacího prvku.

```
void ShowControlBar(
    CControlBar* pBar,
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
Ukazatel na panel ovládacího prvku na zobrazený nebo skrytý.

*bShow*<br/>
Při hodnotě TRUE Určuje, že má být zobrazen ovládací panel. Pokud má hodnotu FALSE, určuje, zda ovládací prvek panelu jako skryté.

*bDelay*<br/>
Pokud je hodnota TRUE, zpoždění zobrazující ovládací panel. Pokud má hodnotu FALSE, zobrazit ovládací prvek panelu okamžitě.

##  <a name="showownedwindows"></a>  CFrameWnd::ShowOwnedWindows

Voláním této členské funkce, chcete-li zobrazit všechny systémy windows, které jsou potomky `CFrameWnd` objektu.

```
void ShowOwnedWindows(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bShow*<br/>
Určuje, zda jsou vlastněné windows na zobrazený nebo skrytý.

## <a name="see-also"></a>Viz také:

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[CMDIFrameWnd – třída](../../mfc/reference/cmdiframewnd-class.md)<br/>
[CMDIChildWnd – třída](../../mfc/reference/cmdichildwnd-class.md)<br/>
[CView – třída](../../mfc/reference/cview-class.md)<br/>
[CDocTemplate – třída](../../mfc/reference/cdoctemplate-class.md)<br/>
[CRuntimeClass – struktura](../../mfc/reference/cruntimeclass-structure.md)
