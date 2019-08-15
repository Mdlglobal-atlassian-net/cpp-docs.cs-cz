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
ms.openlocfilehash: d2e043c8c9f4ad86636cd0e9ea7d695826b6c8fb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506963"
---
# <a name="cframewnd-class"></a>CFrameWnd – třída

Poskytuje funkce překrytého a překryvného okna rámce rozhraní Windows Single Document Interface (SDI) spolu se členy pro správu okna.

## <a name="syntax"></a>Syntaxe

```
class CFrameWnd : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CFrameWnd:: CFrameWnd](#cframewnd)|`CFrameWnd` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CFrameWnd:: ActivateFrame](#activateframe)|Nastaví rámec jako viditelný a dostupný pro uživatele.|
|[CFrameWnd::BeginModalState](#beginmodalstate)|Nastaví okno rámce na modální.|
|[CFrameWnd:: Create](#create)|Zavolejte k vytvoření a inicializaci okna rámce Windows přidruženého `CFrameWnd` k objektu.|
|[CFrameWnd:: CreateView](#createview)|Vytvoří zobrazení v rámci rámce, který není odvozen z `CView`.|
|[CFrameWnd::DockControlBar](#dockcontrolbar)|Ukotví ovládací panel.|
|[CFrameWnd:: EnableDocking](#enabledocking)|Umožňuje ukotvení řídicího panelu.|
|[CFrameWnd:: EndModalState](#endmodalstate)|Ukončí modální stav okna rámce. Povolí všechna okna zakázaná nástrojem `BeginModalState`.|
|[CFrameWnd:: FloatControlBar](#floatcontrolbar)|Odpluje ovládací panel.|
|[CFrameWnd:: GetActiveDocument](#getactivedocument)|Vrátí aktivní `CDocument` objekt.|
|[CFrameWnd:: Getactiveframe –](#getactiveframe)|Vrátí aktivní `CFrameWnd` objekt.|
|[CFrameWnd::GetActiveView](#getactiveview)|Vrátí aktivní `CView` objekt.|
|[CFrameWnd:: GetControlBar](#getcontrolbar)|Načte ovládací panel.|
|[CFrameWnd:: GetDockState](#getdockstate)|Načte stav Dock okna rámce.|
|[CFrameWnd:: GetMenuBarState](#getmenubarstate)|Načte stav zobrazení nabídky v aktuální aplikaci MFC.|
|[CFrameWnd:: GetMenuBarVisibility](#getmenubarvisibility)|Označuje, zda je výchozí chování nabídky v aktuální aplikaci MFC buď skryto, nebo viditelné.|
|[CFrameWnd:: GetMessageBar](#getmessagebar)|Vrátí ukazatel na stavový řádek patřící do okna rámce.|
|[CFrameWnd:: GetMessageString](#getmessagestring)|Načte zprávu odpovídající ID příkazu.|
|[CFrameWnd:: getTitle](#gettitle)|Načte název souvisejícího ovládacího panelu.|
|[CFrameWnd:: InitialUpdateFrame](#initialupdateframe)|Způsobí volání `OnInitialUpdate` členské funkce patřící do všech zobrazení v okně rámce.|
|[CFrameWnd:: InModalState](#inmodalstate)|Vrátí hodnotu, která označuje, zda je okno rámce v modálním stavu.|
|[CFrameWnd:: detracking](#istracking)|Určuje, zda se právě přesouvá Příčkový panel.|
|[CFrameWnd:: LoadAccelTable](#loadacceltable)|Zavolejte pro načtení tabulky akcelerátoru.|
|[CFrameWnd:: LoadBarState](#loadbarstate)|Volá se, aby se obnovilo nastavení ovládacího panelu.|
|[CFrameWnd:: LoadFrame](#loadframe)|Zavolejte k dynamickému vytvoření okna rámce z informací o zdroji.|
|[CFrameWnd:: NegotiateBorderSpace](#negotiateborderspace)|Vyjednává ohraničující místo v okně rámce.|
|[CFrameWnd:: OnBarCheck](#onbarcheck)|Volá se vždy, když se na zadaném řídicím panelu provede akce.|
|[CFrameWnd:: OnContextHelp](#oncontexthelp)|Zpracovává nápovědu SHIFT + F1 pro místní položky.|
|[CFrameWnd:: OnSetPreviewMode](#onsetpreviewmode)|Nastaví hlavní okno rámce aplikace na režim náhledu tisku a ven.|
|[CFrameWnd::OnUpdateControlBarMenu](#onupdatecontrolbarmenu)|Volá se rozhraním, když se aktualizuje přidružená nabídka.|
|[CFrameWnd:: RecalcLayout](#recalclayout)|Přemístí ovládací panely `CFrameWnd` objektu.|
|[CFrameWnd:: SaveBarState](#savebarstate)|Volá se, aby se uložilo nastavení ovládacího panelu.|
|[CFrameWnd::SetActivePreviewView](#setactivepreviewview)|Určí zadané zobrazení jako aktivní zobrazení pro bohatou verzi Preview.|
|[CFrameWnd::SetActiveView](#setactiveview)|Nastaví aktivní `CView` objekt.|
|[CFrameWnd:: SetDockState](#setdockstate)|Volání Dock okna rámce v hlavním okně.|
|[CFrameWnd:: SetMenuBarState](#setmenubarstate)|Nastaví stav zobrazení nabídky v aktuální aplikaci MFC na skryté nebo zobrazené.|
|[CFrameWnd:: SetMenuBarVisibility](#setmenubarvisibility)|Nastaví výchozí chování nabídky v aktuální aplikaci knihovny MFC tak, aby bylo buď skryté, nebo viditelné.|
|[CFrameWnd::SetMessageText](#setmessagetext)|Nastaví text standardního stavového řádku.|
|[CFrameWnd:: SetProgressBarPosition](#setprogressbarposition)|Nastaví aktuální pozici indikátoru průběhu pro systém Windows 7, který je zobrazen na hlavním panelu.|
|[CFrameWnd:: SetProgressBarRange](#setprogressbarrange)|Nastaví rozsah indikátoru průběhu systému Windows 7 zobrazený na hlavním panelu.|
|[CFrameWnd:: SetProgressBarState](#setprogressbarstate)|Nastaví typ a stav indikátoru průběhu zobrazeného na tlačítku na hlavním panelu.|
|[CFrameWnd:: SetTaskbarOverlayIcon](#settaskbaroverlayicon)|Přetíženo. Použije překryv na tlačítko na hlavním panelu k označení stavu aplikace nebo oznámení uživateli.|
|[CFrameWnd:: SetTitle](#settitle)|Nastaví název souvisejícího ovládacího panelu.|
|[CFrameWnd:: ShowControlBar](#showcontrolbar)|Volá se, aby se zobrazil ovládací panel.|
|[CFrameWnd:: ShowOwnedWindows](#showownedwindows)|Zobrazí všechna okna, která jsou následníky `CFrameWnd` objektu.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[CFrameWnd:: OnCreateClient](#oncreateclient)|Vytvoří klientské okno pro daný rámec.|
|[CFrameWnd:: OnHideMenuBar](#onhidemenubar)|Volá se před tím, než je nabídka v aktuální aplikaci MFC skrytá.|
|[CFrameWnd:: OnShowMenuBar](#onshowmenubar)|Volá se před tím, než se zobrazí nabídka v aktuální aplikaci MFC.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CFrameWnd:: m_bAutoMenuEnable](#m_bautomenuenable)|Řídí automatické povolení a zakázání funkcí pro položky nabídky.|
|[CFrameWnd:: rectDefault](#rectdefault)|Předat tuto statickou `CRect` jako parametr při `CFrameWnd` vytváření objektu, aby systém Windows mohl zvolit počáteční velikost a polohu okna.|

## <a name="remarks"></a>Poznámky

Chcete-li vytvořit užitečné okno rámce pro aplikaci, odvodit třídu z `CFrameWnd`. Přidejte členské proměnné do odvozené třídy pro uložení dat specifických pro vaši aplikaci. Implementací členských funkcí obslužných rutin zpráv a mapy zpráv v odvozené třídě určíte, co se stane, když se zprávy přesměrují do okna.

Existují tři způsoby, jak vytvořit okno rámce:

- Přímo se vytvoří pomocí [Create](#create).

- Přímo jej Sestavte pomocí [LoadFrame](#loadframe).

- Nepřímo ji vytvořte pomocí šablony dokumentu.

Před voláním `Create` `LoadFrame`nebo je nutné vytvořit objekt okna rámce na haldě pomocí C++ operátoru **New** . Před voláním `Create`můžete také zaregistrovat třídu okna s globální funkcí [AfxRegisterWndClass –](../../mfc/reference/application-information-and-management.md#afxregisterwndclass) k nastavení ikony a stylů třídy pro daný rámec.

`Create` Pomocí členské funkce předejte parametry vytváření rámce jako okamžité argumenty.

`LoadFrame`vyžaduje méně argumentů než `Create`a místo toho načte většinu jeho výchozích hodnot z prostředků, včetně titulku rámce, ikony, tabulky akcelerátorů a nabídky. Aby k nim měli `LoadFrame`přístup všechny tyto prostředky, musí mít stejné ID prostředku (například IDR_MAINFRAME).

`CFrameWnd` Pokud objekt obsahuje zobrazení a dokumenty, jsou vytvořeny nepřímo rozhraním, nikoli přímo programátorem. `CDocTemplate` Objekt orchestruje vytvoření snímku, vytvoření obsahujícího zobrazení a připojení zobrazení k příslušnému dokumentu. Parametry `CDocTemplate` konstruktoru`CRuntimeClass` určují, jaké tři třídy jsou zahrnuty (dokument, rámeček a zobrazení). `CRuntimeClass` Objekt je používán rozhraním k dynamickému vytváření nových rámců, pokud jsou zadány uživatelem (například pomocí příkazu soubor nový nebo v okně Nový příkaz pro rozhraní více dokumentů (MDI)).

Třída okna rámce odvozená z `CFrameWnd` musí být deklarovaná s DECLARE_DYNCREATE, aby výše uvedený mechanismus RUNTIME_CLASS správně fungoval.

`CFrameWnd` Obsahuje výchozí implementace pro provádění následujících funkcí hlavního okna v typické aplikaci pro Windows:

- Okno `CFrameWnd` rámce uchovává přehled o aktuálně aktivním zobrazení, které je nezávislé na aktivním okně systému Windows nebo v aktuálním vstupním výběru. Po opětovné aktivaci snímku je aktivní zobrazení oznámeno voláním `CView::OnActivateView`.

- Zprávy příkazů a mnoho běžných zpráv s oznámením rámců, včetně těch, které `OnSetFocus`jsou `OnHScroll`zpracovávány `OnVScroll` `CFrameWnd` funkcemi `CWnd`, a, jsou delegovány oknem rámce na aktuálně aktivní zobrazení.

- Aktuálně aktivní zobrazení (nebo aktuálně aktivní okno podřízeného rámce MDI v případě rámce MDI) může určovat titulek okna rámce. Tato funkce se dá zakázat vypnutím bitu stylu FWS_ADDTOTITLE okna rámce.

- Okno `CFrameWnd` rámce spravuje umístění ovládacích panelů, zobrazení a dalších podřízených oken uvnitř klientské oblasti okna rámce. Okno rámce také provádí aktualizace panelu nástrojů a dalších tlačítek ovládacích panelů v době nečinnosti. Okno `CFrameWnd` rámce má také výchozí implementace příkazů pro přepnutí na panel nástrojů a stavový řádek.

- Okno `CFrameWnd` rámce spravuje hlavní panel nabídek. Když se zobrazí místní nabídka, okno rámce použije mechanismus UPDATE_COMMAND_UI k určení, které položky nabídky by se měly povolit, zakázat nebo zkontrolovat. Když uživatel vybere položku nabídky, okno rámce aktualizuje stavový řádek řetězcem zprávy pro daný příkaz.

- Okno `CFrameWnd` rámce má volitelnou tabulku akcelerátorů, která automaticky překládá klávesové zkratky.

- V okně `LoadFrame` rámce je nastavena volitelná Nápověda s ID, která se používá pro kontextovou nápovědu. `CFrameWnd` Okno rámce je hlavním nástrojem Orchestrator pro semimodální stavy, jako je kontextová nápověda (SHIFT + F1) a režimy náhledu tisku.

- Okno `CFrameWnd` rámce otevře soubor přetažený ze Správce souborů a vynechá se v okně rámce. Pokud je přípona souboru registrovaná a přidružená k aplikaci, okno rámce odpoví na požadavek Open Dynamic Data Exchange (DDE), ke kterému dojde, když uživatel otevře datový soubor ve Správci souborů nebo když `ShellExecute` se zavolá funkce Windows.

- Pokud je okno rámce hlavním oknem aplikace (tj `CWinThread::m_pMainWnd`.), když uživatel aplikaci zavře, okno rámce vyzve uživatele k uložení všech upravených dokumentů (pro `OnClose` a `OnQueryEndSession`).

- Pokud je okno rámce hlavním oknem aplikace, okno rámce je kontextem pro spuštění programu WinHelp. Zavřením okna rámce dojde k vypnutí WINHELP. EXE, pokud se spustil pro nápovědu pro tuto aplikaci.

Nepoužívejte C++ operátor **Delete** ke zničení okna rámce. Místo nich se používá `CWnd::DestroyWindow`. Implementace odstraní C++ objekt, když dojde ke zničení okna. `PostNcDestroy` `CFrameWnd` Když uživatel zavře okno rámce, výchozí `OnClose` obslužná rutina bude volat. `DestroyWindow`

Další informace o `CFrameWnd`naleznete v tématu [okna](../../mfc/frame-windows.md)s rámečkem.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CFrameWnd`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="activateframe"></a>CFrameWnd:: ActivateFrame

Voláním této členské funkce aktivujete a obnovíte okno rámce tak, aby bylo viditelné a dostupné pro uživatele.

```
virtual void ActivateFrame(int nCmdShow = -1);
```

### <a name="parameters"></a>Parametry

*nCmdShow*<br/>
Určuje parametr, který bude předávat do [CWnd::: ShowWindow](../../mfc/reference/cwnd-class.md#showwindow). Ve výchozím nastavení je rámec zobrazen a správně obnoven.

### <a name="remarks"></a>Poznámky

Tato členská funkce se obvykle volá po události nesouvisející s uživatelským rozhraním, jako je DDE, OLE nebo jiná událost, která může uživateli zobrazit okno rámce nebo jeho obsah.

Výchozí implementace aktivuje rámec a přesune ho do horní části pořadí vykreslování a v případě potřeby provede stejné kroky pro okno hlavního rámce aplikace.

Tuto členskou funkci přepište, pokud chcete změnit způsob, jakým je rámec aktivovaný. Můžete například vynutit maximalizaci podřízených oken MDI. Přidejte příslušné funkce a pak zavolejte verzi základní třídy s explicitním *nCmdShow*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#1](../../mfc/reference/codesnippet/cpp/cframewnd-class_1.cpp)]

##  <a name="beginmodalstate"></a>CFrameWnd:: BeginModalState

Zavolejte tuto členskou funkci, aby bylo okno rámce modální.

```
virtual void BeginModalState();
```

##  <a name="cframewnd"></a>CFrameWnd:: CFrameWnd

`CFrameWnd` Vytvoří objekt, ale nevytvoří viditelné okno rámce.

```
CFrameWnd();
```

### <a name="remarks"></a>Poznámky

Voláním `Create` pro vytvoření viditelného okna.

##  <a name="create"></a>CFrameWnd:: Create

Zavolejte k vytvoření a inicializaci okna rámce Windows přidruženého `CFrameWnd` k objektu.

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
Odkazuje na řetězec znaků zakončený hodnotou null, který pojmenovává třídu systému Windows. Název třídy může být jakýkoli název, který je `AfxRegisterWndClass` zaregistrován s globální funkcí `RegisterClass` nebo funkcí Windows. Pokud má hodnotu null, používá předdefinované `CFrameWnd` výchozí atributy.

*lpszWindowName*<br/>
Odkazuje na řetězec znaků zakončený hodnotou null, který představuje název okna. Slouží jako text záhlaví.

*dwStyle*<br/>
Určuje atributy [stylu](../../mfc/reference/styles-used-by-mfc.md#window-styles) okna. Zahrňte styl FWS_ADDTOTITLE, pokud chcete, aby záhlaví automaticky zobrazilo název dokumentu reprezentovaného v okně.

*OBD*<br/>
Určuje velikost a polohu okna. Hodnota *rectDefault* umožňuje systému Windows určit velikost a polohu nového okna.

*pParentWnd*<br/>
Určuje nadřazené okno tohoto okna rámce. Tento parametr by měl mít hodnotu NULL pro okna rámce nejvyšší úrovně.

*lpszMenuName*<br/>
Určuje název prostředku nabídky, který se má v okně použít. Použijte MAKEINTRESOURCE, pokud má nabídka celočíselné ID místo řetězce. Tento parametr může mít hodnotu NULL.

*dwExStyle*<br/>
Určuje rozšířené atributy [stylu](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) okna.

*pContext*<br/>
Určuje ukazatel na strukturu [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) . Tento parametr může mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je inicializace úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

`CFrameWnd` Vytvořte objekt ve dvou krocích. Nejprve volejte konstruktor, který sestaví `CFrameWnd` objekt a potom zavolejte `Create`, čímž se vytvoří okno rámce Windows a `CFrameWnd` připojí ho k objektu. `Create`Inicializuje název třídy okna a název okna a registruje výchozí hodnoty pro svůj styl, nadřazenou a přidruženou nabídku.

`LoadFrame` Použijte`Create` místo toho, abyste načetli okno rámce z prostředku místo zadání argumentů.

##  <a name="createview"></a>CFrameWnd:: CreateView

Voláním `CreateView` pro vytvoření zobrazení v rámci rámce.

```
CWnd* CreateView(
    CCreateContext* pContext,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>Parametry

*pContext*<br/>
Určuje typ zobrazení a dokument.

*nID*<br/>
Číslo ID zobrazení

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CWnd` objekt v případě úspěchu; jinak null.

### <a name="remarks"></a>Poznámky

Tuto členskou funkci použijte k vytvoření "zobrazení", která nejsou `CView`odvozena v rámci rámečku. Po volání `CreateView`je nutné ručně nastavit zobrazení na aktivní a nastavit tak, aby bylo viditelné. tyto úkoly nejsou automaticky provedeny nástrojem `CreateView`.

##  <a name="dockcontrolbar"></a>CFrameWnd::D ockControlBar

Způsobí, že se ovládací panel ukotví do okna rámce.

```
void DockControlBar(
    CControlBar* pBar,
    UINT nDockBarID = 0,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
Odkazuje na ovládací panel, který se má ukotvit.

*nDockBarID*<br/>
Určuje, které strany okna rámce budou zváženy pro docking. Může to být 0 nebo jedna z následujících:

- AFX_IDW_DOCKBAR_TOP Docker na horní stranu okna rámce.

- AFX_IDW_DOCKBAR_BOTTOM Docker na spodní stranu okna rámce.

- AFX_IDW_DOCKBAR_LEFT Docker na levou stranu okna rámce.

- AFX_IDW_DOCKBAR_RIGHT Docker do pravé strany okna rámce.

Pokud je hodnota 0, ovládací panel může být ukotven na libovolnou stranu povolenou pro ukotvení v cílovém okně rámce.

*lpRect*<br/>
Určuje v souřadnicích obrazovky, kde bude ovládací panel ukotven v neklientské oblasti cílového okna rámce.

### <a name="remarks"></a>Poznámky

Ovládací panel bude ukotven na jednu ze stran okna rámce určeného v volání metody [CControlBar –:: EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking) a [CFrameWnd:: EnableDocking](#enabledocking). Zvolená strana je určena *nDockBarID*.

##  <a name="enabledocking"></a>CFrameWnd:: EnableDocking

Voláním této funkce povolíte ovládací panely ukotvit v okně rámce.

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Parametry

*dwDockStyle*<br/>
Určuje, které strany okna rámce mohou sloužit jako dokovací weby pro ovládací panely. Může to být jedna nebo víc z těchto možností:

- CBRS_ALIGN_TOP umožňuje ukotvení v horní části klientské oblasti.

- CBRS_ALIGN_BOTTOM umožňuje ukotvení v dolní části klientské oblasti.

- CBRS_ALIGN_LEFT umožňuje ukotvení na levé straně klientské oblasti.

- CBRS_ALIGN_RIGHT umožňuje ukotvení na pravé straně klientské oblasti.

- CBRS_ALIGN_ANY umožňuje ukotvení na kterékoli straně klientské oblasti.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení budou ovládací panely ukotveny na stranu okna rámce v následujícím pořadí: nahoře, dole, vlevo, vpravo.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CToolBar –:: Create](../../mfc/reference/ctoolbar-class.md#create).

##  <a name="endmodalstate"></a>CFrameWnd:: EndModalState

Chcete-li změnit okno rámce z modální na nemodální, zavolejte tuto členskou funkci.

```
virtual void EndModalState();
```

### <a name="remarks"></a>Poznámky

`EndModalState`povolí všechna okna zakázaná [BeginModalState](#beginmodalstate).

##  <a name="floatcontrolbar"></a>CFrameWnd:: FloatControlBar

Voláním této funkce dojde k tomu, že ovládací panel nebude ukotven do okna rámce.

```
void FloatControlBar(
    CControlBar* pBar,
    CPoint point,
    DWORD dwStyle = CBRS_ALIGN_TOP);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
Odkazuje na ovládací panel, který se má uvolnit.

*Vyberte*<br/>
Umístění v souřadnicích obrazovky, kde bude umístěn levý horní roh ovládacího panelu.

*dwStyle*<br/>
Určuje, zda se má ovládací panel v novém okně rámce Zarovnat vodorovně nebo svisle. Může to být jedna z následujících možností:

- CBRS_ALIGN_TOP orientuje ovládací panel svisle.

- CBRS_ALIGN_BOTTOM orientuje ovládací panel svisle.

- CBRS_ALIGN_LEFT orientuje ovládací panel vodorovně.

- CBRS_ALIGN_RIGHT orientuje ovládací panel vodorovně.

Pokud jsou předány styly, které určují vodorovnou i svislou orientaci, panel nástrojů bude orientovaný na sebe vodorovně.

### <a name="remarks"></a>Poznámky

Typicky se to provádí při spuštění aplikace, když program obnovuje nastavení z předchozího spuštění.

Tato funkce je volána rozhraním, když uživatel způsobí operaci přetažení uvolněním levého tlačítka myši při přetahování ovládacího panelu na místo, které není k dispozici pro ukotvení.

##  <a name="getactivedocument"></a>CFrameWnd:: GetActiveDocument

Chcete-li získat ukazatel na aktuální `CDocument` připojení k aktuálnímu aktivnímu zobrazení, zavolejte tuto členskou funkci.

```
virtual CDocument* GetActiveDocument();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktuální [objektu CDocument](../../mfc/reference/cdocument-class.md). Pokud není k dispozici žádný aktuální dokument, vrátí hodnotu NULL.

##  <a name="getactiveframe"></a>CFrameWnd:: Getactiveframe –

Voláním této členské funkce získáte ukazatel na aktivní podřízené okno MDI (Multiple Document Interface) v okně rámce MDI.

```
virtual CFrameWnd* GetActiveFrame();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktivní podřízené okno MDI. Pokud je aplikace aplikace SDI nebo okno rámce MDI nemá žádný aktivní dokument, bude vrácen implicitní **Tento** ukazatel.

### <a name="remarks"></a>Poznámky

Pokud není k dispozici žádný aktivní podřízený objekt MDI nebo je aplikace rozhraní SDI (Single Document Interface), bude vrácen implicitní **Tento** ukazatel.

##  <a name="getactiveview"></a>CFrameWnd:: GetActiveView

Zavolejte tuto členskou funkci, aby získala ukazatel na aktivní zobrazení (pokud existuje) připojené k oknu rámce ( `CFrameWnd`).

```
CView* GetActiveView() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktuální [CView](../../mfc/reference/cview-class.md). Pokud neexistuje aktuální zobrazení, vrátí hodnotu NULL.

### <a name="remarks"></a>Poznámky

Tato funkce vrací hodnotu NULL při volání pro hlavní okno rámce MDI ( `CMDIFrameWnd`). V aplikaci MDI nemá okno hlavního rámce MDI přidružené zobrazení. Místo toho má každé jednotlivá podřízená `CMDIChildWnd`okna () jedno nebo více přidružených zobrazení. Aktivní zobrazení v aplikaci MDI lze získat tak, že nejprve najde aktivní podřízené okno MDI a pak najde aktivní zobrazení pro toto podřízené okno. Aktivní podřízené okno MDI lze najít voláním funkce `MDIGetActive` nebo `GetActiveFrame` , jak je znázorněno v následujícím seznamu:

[!code-cpp[NVC_MFCWindowing#2](../../mfc/reference/codesnippet/cpp/cframewnd-class_2.cpp)]

##  <a name="getcontrolbar"></a>CFrameWnd:: GetControlBar

Volání `GetControlBar` pro získání přístupu k ovládacímu panelu, který je spojen s ID.

```
CControlBar* GetControlBar(UINT nID);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Číslo ID ovládacího panelu

### <a name="return-value"></a>Návratová hodnota

Ukazatel na ovládací panel, který je spojen s IDENTIFIKÁTORem.

### <a name="remarks"></a>Poznámky

Parametr *NID* odkazuje na jedinečný identifikátor předaný `Create` metodě ovládacího panelu. Další informace o ovládacích panelech najdete v tématu s názvem [Ovládací panely](../../mfc/control-bars.md).

`GetControlBar`vrátí ovládací panel, i když je plovoucí, a proto není aktuálně podřízené okno rámce.

##  <a name="getdockstate"></a>CFrameWnd:: GetDockState

Tuto členskou funkci volejte pro uložení informací o stavu ovládacích panelů okna rámce v `CDockState` objektu.

```
void GetDockState(CDockState& state) const;
```

### <a name="parameters"></a>Parametry

*státech*<br/>
Obsahuje aktuální stav ovládacích pruhů okna rámce při návratu.

### <a name="remarks"></a>Poznámky

Pak můžete zapsat obsah `CDockState` do úložiště pomocí `CDockState::SaveState` nebo `Serialize`. Pokud později chcete obnovit ovládací panely do předchozího stavu, načtěte stav pomocí `CDockState::LoadState` nebo `Serialize`a potom zavolejte `SetDockState` k použití předchozího stavu na ovládací panely okna rámce.

##  <a name="getmenubarstate"></a>CFrameWnd:: GetMenuBarState

Načte stav zobrazení nabídky v aktuální aplikaci MFC.

```
virtual DWORD GetMenuBarState();
```

### <a name="return-value"></a>Návratová hodnota

Návratová hodnota může mít následující hodnoty:

- AFX_MBS_VISIBLE (0x01) – nabídka je viditelná.

- AFX_MBS_HIDDEN (0x02) – nabídka je skrytá.

### <a name="remarks"></a>Poznámky

Pokud dojde k chybě modulu runtime, tato metoda provede vyhodnocení v režimu ladění a vyvolá výjimku odvozenou z třídy [CException –](../../mfc/reference/cexception-class.md) .

##  <a name="getmenubarvisibility"></a>CFrameWnd:: GetMenuBarVisibility

Označuje, zda je výchozí stav nabídky v aktuální aplikaci MFC skrytý nebo viditelný.

```
virtual DWORD CFrameWnd::GetMenuBarVisibility();
```

### <a name="return-value"></a>Návratová hodnota

Tato metoda vrátí jednu z následujících hodnot:

- AFX_MBV_KEEPVISIBLE (0x01) – nabídka se zobrazuje za všech okolností a ve výchozím nastavení nemá fokus.

- AFX_MBV_DISPLAYONFOCUS (0x02) – nabídka je ve výchozím nastavení skrytá. Pokud je nabídka skrytá, stiskněte klávesu ALT k zobrazení nabídky a poskytněte jí fokus. Pokud je nabídka zobrazená, stiskněte klávesu ALT nebo ESC pro její skrytí.

- AFX_MBV_ DISPLAYONFOCUS (0x02) &#124; AFX_MBV_DISPLAYONF10 (0x04) (Bitová kombinace (nebo)) – nabídka je ve výchozím nastavení skrytá. Pokud je nabídka skrytá, stiskněte klávesu F10 k zobrazení nabídky a pojmenujte ji jako fokus. Pokud se nabídka zobrazí, stisknutím klávesy F10 přepněte fokus na nabídku nebo mimo ni. Nabídka se zobrazí až po stisknutí klávesy ALT nebo klávesy ESC k jejímu skrytí.

### <a name="remarks"></a>Poznámky

Pokud dojde k chybě modulu runtime, tato metoda provede vyhodnocení v režimu ladění a vyvolá výjimku odvozenou z třídy [CException –](../../mfc/reference/cexception-class.md) .

##  <a name="getmessagebar"></a>CFrameWnd:: GetMessageBar

Chcete-li získat ukazatel na stavový řádek, zavolejte tuto členskou funkci.

```
virtual CWnd* GetMessageBar();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na okno stavového řádku.

##  <a name="getmessagestring"></a>CFrameWnd:: GetMessageString

Tuto funkci můžete přepsat tak, aby poskytovala vlastní řetězce pro ID příkazů.

```
virtual void GetMessageString(
    UINT nID,
    CString& rMessage) const;
```

### <a name="parameters"></a>Parametry

*nID*<br/>
ID prostředku požadované zprávy

*rMessage*<br/>
`CString`objekt, do kterého se má umístit zpráva

### <a name="remarks"></a>Poznámky

Výchozí implementace jednoduše načte řetězec určený parametrem *NID* ze souboru prostředků. Tato funkce je volána rozhraním, když je potřeba aktualizovat řetězec zprávy ve stavovém řádku.

##  <a name="gettitle"></a>CFrameWnd:: getTitle

Načte název objektu window.

```
CString GetTitle() const;
```

### <a name="return-value"></a>Návratová hodnota

Objekt [CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahující aktuální název objektu window.

##  <a name="initialupdateframe"></a>CFrameWnd:: InitialUpdateFrame

Zavolejte `IntitialUpdateFrame` po vytvoření nového rámce pomocí `Create`.

```
void InitialUpdateFrame(
    CDocument* pDoc,
    BOOL bMakeVisible);
```

### <a name="parameters"></a>Parametry

*pDoc*<br/>
Odkazuje na dokument, ke kterému je okno rámce přidruženo. Může mít hodnotu NULL.

*bMakeVisible*<br/>
V případě hodnoty TRUE označuje, že by měl být snímek viditelný a aktivní. Je-li nastavena hodnota FALSE, nejsou zobrazeny žádné následníky.

### <a name="remarks"></a>Poznámky

To způsobí, že všechna zobrazení v tomto okně rámce budou `OnInitialUpdate` přijímat volání.

V případě, že dříve existovalo aktivní zobrazení, je primární zobrazení okna rámce aktivní. Primární zobrazení je zobrazení s podřízeným ID AFX_IDW_PANE_FIRST. Nakonec je okno rámce viditelné, pokud je *bMakeVisible* nenulové. Pokud je *bMakeVisible* 0, aktuální fokus a viditelný stav okna rámce zůstanou beze změny. Není nutné volat tuto funkci při použití implementace souboru New a souboru Open v rozhraní Framework.

##  <a name="inmodalstate"></a>CFrameWnd:: InModalState

Voláním této členské funkce zkontrolujete, zda je okno rámce modální nebo nemodální.

```
BOOL InModalState() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud ano; v opačném případě 0.

##  <a name="istracking"></a>CFrameWnd:: detracking

Voláním této členské funkce určíte, zda je dělicí příčka v okně právě přesunuta.

```
BOOL IsTracking() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud probíhá operace rozdělovače; v opačném případě 0.

##  <a name="loadacceltable"></a>CFrameWnd:: LoadAccelTable

Zavolejte pro načtení zadané tabulky akcelerátorů.

```
BOOL LoadAccelTable(LPCTSTR lpszResourceName);
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Určuje název prostředku akcelerátoru. Použijte MAKEINTRESOURCE, pokud je prostředek identifikován pomocí celočíselného IDENTIFIKÁTORu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla tabulka akcelerátorů úspěšně načtena; v opačném případě 0.

### <a name="remarks"></a>Poznámky

V jednom okamžiku může být načtena pouze jedna tabulka.

Tabulky akcelerátorů načtené z prostředků se po ukončení aplikace uvolňují automaticky.

Pokud zavoláte `LoadFrame` , aby se vytvořilo okno rámce, rozhraní načte tabulku akcelerátorů spolu s nabídkou a ikonami prostředků a následné volání této členské funkce je pak zbytečné.

##  <a name="loadbarstate"></a>CFrameWnd:: LoadBarState

Voláním této funkce obnovíte nastavení všech ovládacích panelů vlastněných oknem rámců.

```
void LoadBarState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
Název oddílu v inicializačním souboru (INI) nebo klíč v registru systému Windows, kde jsou uloženy informace o stavu.

### <a name="remarks"></a>Poznámky

Obnovené informace zahrnují viditelnost, vodorovnou a svislou orientaci, stav ukotvení a pozici na ovládacím panelu.

Nastavení, která chcete obnovit, musí být před voláním `LoadBarState`zapsána do registru. Zapište informace do registru voláním [CWinApp:: SetRegistryKey](../../mfc/reference/cwinapp-class.md#setregistrykey). Zapište informace do souboru INI voláním [SaveBarState](#savebarstate).

##  <a name="loadframe"></a>CFrameWnd:: LoadFrame

Zavolejte k dynamickému vytvoření okna rámce z informací o zdroji.

```
virtual BOOL LoadFrame(
    UINT nIDResource,
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,
    CWnd* pParentWnd = NULL,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Parametry

*nIDResource*<br/>
ID sdílených prostředků přidružených k oknu rámce.

*dwDefaultStyle*<br/>
[Styl](../../mfc/reference/styles-used-by-mfc.md#window-styles)rámečku Zahrňte styl FWS_ADDTOTITLE, pokud chcete, aby záhlaví automaticky zobrazilo název dokumentu reprezentovaného v okně.

*pParentWnd*<br/>
Ukazatel na nadřazenou položku rámce.

*pContext*<br/>
Ukazatel na strukturu [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) . Tento parametr může mít hodnotu NULL.

### <a name="remarks"></a>Poznámky

`CFrameWnd` Vytvořte objekt ve dvou krocích. Nejprve volejte konstruktor, který sestaví `CFrameWnd` objekt a potom zavolejte `LoadFrame`, čímž se načte okno rámce systému Windows a přidružené prostředky a připojí okno rámce k `CFrameWnd` objektu. Parametr *nIDResource* určuje nabídku, tabulku akcelerátorů, ikonu a prostředek řetězce pro název okna rámce.

Použijte spíše `Create` členskou funkci, než `LoadFrame` když chcete zadat všechny parametry vytvoření okna rámce.

Rozhraní volá `LoadFrame` , když vytvoří okno rámce pomocí objektu šablony dokumentu.

Rozhraní používá argument *pContext* k určení objektů, které mají být připojeny k oknu rámce, včetně všech objektů zobrazení s omezením. Při volání `LoadFrame`můžete nastavit argument *pContext* na hodnotu null.

##  <a name="m_bautomenuenable"></a>CFrameWnd:: m_bAutoMenuEnable

Pokud je tento datový člen povolen (což je výchozí nastavení), položky nabídky, které nemají obslužné rutiny ON_UPDATE_COMMAND_UI nebo ON_COMMAND, budou automaticky zakázány, když uživatel vyžádá nabídku.

```
BOOL m_bAutoMenuEnable;
```

### <a name="remarks"></a>Poznámky

Položky nabídky, které mají obslužnou rutinu ON_COMMAND, ale nebude automaticky povolena obslužná rutina ON_UPDATE_COMMAND_UI.

Když je tento datový člen nastaven, položky nabídky jsou automaticky povoleny stejným způsobem, jakým jsou povolena tlačítka panelu nástrojů.

> [!NOTE]
> `m_bAutoMenuEnable`nemá žádný vliv na položky nabídky nejvyšší úrovně.

Tento datový člen zjednodušuje implementaci volitelných příkazů na základě aktuálního výběru a omezuje nutnost psaní obslužných rutin ON_UPDATE_COMMAND_UI pro povolení a zakázání položek nabídky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#3](../../mfc/reference/codesnippet/cpp/cframewnd-class_3.cpp)]

##  <a name="negotiateborderspace"></a>CFrameWnd:: NegotiateBorderSpace

Vyvolejte tuto členskou funkci pro vyjednání ohraničení v okně rámce během aktivace OLE.

```
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,
    LPRECT lpRectBorder);
```

### <a name="parameters"></a>Parametry

*nBorderCmd*<br/>
Obsahuje jednu z následujících hodnot z `enum BorderCmd`:

- `borderGet` = 1

- `borderRequest` = 2

- `borderSet` = 3

*lpRectBorder*<br/>
Ukazatel na strukturu [Rect](/windows/win32/api/windef/ns-windef-rect) nebo objekt [CRect](../../atl-mfc-shared/reference/crect-class.md) , který určuje souřadnice ohraničení.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce je `CFrameWnd` implementací funkce vyjednání ohraničení OLE.

##  <a name="onbarcheck"></a>CFrameWnd:: OnBarCheck

Volá se vždy, když se na zadaném řídicím panelu provede akce.

```
afx_msg BOOL OnBarCheck(UINT nID);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
ID zobrazeného ovládacího panelu

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud ovládací panel existoval; v opačném případě 0.

##  <a name="oncontexthelp"></a>CFrameWnd:: OnContextHelp

Zpracovává nápovědu SHIFT + F1 pro místní položky.

```
afx_msg void OnContextHelp();
```

### <a name="remarks"></a>Poznámky

Chcete-li povolit kontextově závislé Nápověda, je nutné přidat

[!code-cpp[NVC_MFCDocViewSDI#16](../../mfc/codesnippet/cpp/cframewnd-class_4.cpp)]

příkaz pro `CFrameWnd` mapu zpráv třídy a také přidejte položku akcelerátor-Table, obvykle SHIFT + F1, chcete-li povolit tuto členskou funkci.

Pokud je vaše aplikace kontejnerem OLE, `OnContextHelp` všechny místní položky, které jsou obsaženy v rámci objektu okna rámce, do režimu help. Kurzor se změní na šipku a otazník a uživatel pak může přesunout ukazatel myši a stisknutím levého tlačítka myši vybrat dialogové okno, okno, nabídku nebo příkazové tlačítko. Tato členská funkce volá funkci `WinHelp` systému Windows s kontextem nápovědě objektu pod kurzorem.

##  <a name="oncreateclient"></a>CFrameWnd:: OnCreateClient

Volá se rozhraním během provádění `OnCreate`.

```
virtual BOOL OnCreateClient(
    LPCREATESTRUCT lpcs,
    CCreateContext* pContext);
```

### <a name="parameters"></a>Parametry

*lpcs*<br/>
Ukazatel na strukturu [CREATESTRUCT –](/windows/win32/api/winuser/ns-winuser-createstructw) systému Windows.

*pContext*<br/>
Ukazatel na strukturu [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) .

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tuto funkci nikdy Nevolejte.

Výchozí implementace této funkce vytvoří `CView` objekt z informací uvedených v *pContext*, pokud je to možné.

Přepište tuto funkci, pokud chcete přepsat hodnoty `CCreateContext` předané v objektu nebo změnit způsob, jakým jsou vytvořeny ovládací prvky v hlavní klientské oblasti okna rámce. Členy, které můžete přepsat, jsou popsány ve třídě [CCreateContext.](../../mfc/reference/ccreatecontext-structure.md) `CCreateContext`

> [!NOTE]
>  Neměňte hodnoty předané ve `CREATESTRUCT` struktuře. Používají se jenom pro informativní použití. Pokud chcete přepsat počáteční obdélník okna, například, přepište `CWnd` členskou funkci. [](../../mfc/reference/cwnd-class.md#precreatewindow)

##  <a name="onhidemenubar"></a>CFrameWnd:: OnHideMenuBar

Tato funkce se volá, když systém chystá skrýt panel nabídek v aktuální aplikaci MFC.

```
virtual void OnHideMenuBar();
```

### <a name="remarks"></a>Poznámky

Tato obslužná rutina události umožňuje aplikaci provádět vlastní akce, když se systém chystá tuto nabídku skrýt. Nemůžete zabránit skrytí nabídky, ale můžete například volat jiné metody pro načtení stylu nebo stavu nabídky.

##  <a name="onsetpreviewmode"></a>CFrameWnd:: OnSetPreviewMode

Voláním této členské funkce nastavíte hlavní okno rámce aplikace na režim náhledu tisku a ven.

```
virtual void OnSetPreviewMode(
    BOOL bPreview,
    CPrintPreviewState* pState);
```

### <a name="parameters"></a>Parametry

*bPreview*<br/>
Určuje, jestli se má aplikace umístit do režimu náhledu tisku. Nastavte na hodnotu TRUE, pokud chcete umístit do náhledu tisku, FALSE pro zrušení režimu náhledu.

*pState*<br/>
Ukazatel na `CPrintPreviewState` strukturu.

### <a name="remarks"></a>Poznámky

Výchozí implementace zakáže všechny standardní panely nástrojů a skryje hlavní nabídku a hlavní okno klienta. Tím se okna s rámečkem MDI přepíná do dočasných oken s rámečkem SDI.

Přepište tuto členskou funkci pro přizpůsobení skrývání a zobrazování ovládacích panelů a dalších částí okna s rámečkem během náhledu tisku. Volání implementace základní třídy z přepsané verze.

##  <a name="onshowmenubar"></a>CFrameWnd:: OnShowMenuBar

Tato funkce se volá, když se systém chystá zobrazit panel nabídek v aktuální aplikaci MFC.

```
virtual void OnShowMenuBar();
```

### <a name="remarks"></a>Poznámky

Tato obslužná rutina události umožňuje aplikaci provádět vlastní akce při zobrazení nabídky. Nelze zabránit zobrazení nabídky, ale můžete například volat jiné metody pro načtení stylu nebo stavu nabídky.

##  <a name="onupdatecontrolbarmenu"></a>CFrameWnd:: OnUpdateControlBarMenu

Volá se rozhraním, když se aktualizuje přidružená nabídka.

```
afx_msg void OnUpdateControlBarMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Ukazatel na objekt [CCmdUI –](../../mfc/reference/ccmdui-class.md) představující nabídku, která vygenerovala příkaz Update. Obslužná rutina aktualizace volá [](../../mfc/reference/ccmdui-class.md#enable) členskou funkci `CCmdUI` Enable objektu prostřednictvím *pCmdUI* k aktualizaci uživatelského rozhraní.

##  <a name="recalclayout"></a>CFrameWnd:: RecalcLayout

Volá se rozhraním, když se změní nebo vypnou standardní ovládací panely nebo když se změní velikost okna rámce.

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Parametry

*bNotify*<br/>
Určuje, zda aktivní místní položka pro okno rámce obdrží oznámení o změně rozložení. Pokud má hodnotu TRUE, je tato položka oznámena. v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Výchozí implementace této členské funkce volá `CWnd` členskou funkci `RepositionBars` pro změnu umístění všech ovládacích panelů v rámci rámce i v hlavním okně `CView` klienta (obvykle nebo MdiClient).

Přepište tuto členskou funkci pro řízení vzhledu a chování ovládacích panelů po změně rozložení okna rámce. Například ji zavolejte, když zapnete nebo vypnete ovládací panely nebo přidáte další ovládací panel.

##  <a name="rectdefault"></a>CFrameWnd:: rectDefault

Při vytváření okna `CRect` předat tento statický jako parametr, aby systém Windows mohl zvolit počáteční velikost a polohu okna.

```
static AFX_DATA const CRect rectDefault;
```

##  <a name="savebarstate"></a>CFrameWnd:: SaveBarState

Voláním této funkce uložíte informace o každém ovládacím panelu, který patří do okna rámce.

```
void SaveBarState(LPCTSTR lpszProfileName) const;
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
Název oddílu v inicializačním souboru nebo klíče v registru systému Windows, kde jsou uloženy informace o stavu.

### <a name="remarks"></a>Poznámky

Tyto informace je možné číst z inicializačního souboru pomocí [LoadBarState](#loadbarstate). Uložené informace zahrnují viditelnost, vodorovnou a svislou orientaci, stav ukotvení a pozici ovládacího panelu.

##  <a name="setactivepreviewview"></a>CFrameWnd:: SetActivePreviewView

Určí zadané zobrazení jako aktivní zobrazení pro bohatou verzi Preview.

```
void SetActivePreviewView(CView* pViewNew);
```

### <a name="parameters"></a>Parametry

*pViewNew*<br/>
Ukazatel na zobrazení, které má být aktivováno.

### <a name="remarks"></a>Poznámky

##  <a name="setactiveview"></a>CFrameWnd:: SetActiveView

Chcete-li nastavit aktivní zobrazení, zavolejte tuto členskou funkci.

```
void SetActiveView(
    CView* pViewNew,
    BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Parametry

*pViewNew*<br/>
Určuje ukazatel na objekt [CView](../../mfc/reference/cview-class.md) nebo hodnotu null pro žádné aktivní zobrazení.

*bNotify*<br/>
Určuje, zda má být zobrazení upozorňováno na aktivaci. Je-li `OnActivateView` nastavena hodnota true, je pro nové zobrazení volána hodnota, pokud má hodnotu false.

### <a name="remarks"></a>Poznámky

Rozhraní bude volat tuto funkci automaticky, když uživatel změní fokus na zobrazení v rámci okna rámce. Chcete-li změnit `SetActiveView` fokus na zadané zobrazení, můžete explicitně zavolat.

##  <a name="setdockstate"></a>CFrameWnd:: SetDockState

Tuto členskou funkci volejte pro použití informací o stavu uložených v `CDockState` objektu na ovládací panely okna rámce.

```
void SetDockState(const CDockState& state);
```

### <a name="parameters"></a>Parametry

*státech*<br/>
Použije uložený stav na ovládací panely okna rámce.

### <a name="remarks"></a>Poznámky

Chcete-li obnovit předchozí stav ovládacích panelů, můžete načíst uložený stav pomocí `CDockState::LoadState` nebo `Serialize`a potom použít `SetDockState` pro použití v ovládacím panelu okna rámce. Předchozí stav je uložen v `CDockState` objektu s`GetDockState`

##  <a name="setmenubarstate"></a>CFrameWnd:: SetMenuBarState

Nastaví stav zobrazení nabídky v aktuální aplikaci MFC na skryté nebo zobrazené.

```
virtual BOOL SetMenuBarState(DWORD nState);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*nInformace*|pro Určuje, zda se má zobrazit nebo skrýt nabídka. Parametr *nInformace* může mít následující hodnoty:<br /><br />-AFX_MBS_VISIBLE (0x01) – zobrazí nabídku, pokud je skrytá, ale nemá žádný vliv, pokud je zobrazená.<br />-AFX_MBS_HIDDEN (0x02) – skryje nabídku, pokud je viditelná, ale nemá žádný vliv, pokud je skrytá.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud tato metoda úspěšně změní stav nabídky; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Pokud dojde k chybě modulu runtime, tato metoda provede vyhodnocení v režimu ladění a vyvolá výjimku odvozenou z třídy [CException –](../../mfc/reference/cexception-class.md) .

##  <a name="setmenubarvisibility"></a>CFrameWnd:: SetMenuBarVisibility

Nastaví výchozí chování nabídky v aktuální aplikaci knihovny MFC tak, aby bylo buď skryté, nebo viditelné.

```
virtual void SetMenuBarVisibility(DWORD nStyle);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*nStyle*|pro Určuje, zda je nabídka ve výchozím nastavení skryta nebo je zobrazena a má fokus. Parametr *nStyle* může mít následující hodnoty:<br /><br />- AFX_MBV_KEEPVISIBLE (0x01) -<br />     Nabídka se zobrazí ve všech časech a ve výchozím nastavení nemá fokus.<br />-AFX_MBV_DISPLAYONFOCUS (0x02) –<br />     Nabídka je ve výchozím nastavení skrytá. Pokud je nabídka skrytá, stiskněte klávesu ALT k zobrazení nabídky a poskytněte jí fokus. Pokud je nabídka zobrazená, stiskněte klávesu ALT nebo ESC pro skrytí nabídky.<br />– AFX_MBV_ DISPLAYONFOCUS (0x02) &#124; AFX_MBV_DISPLAYONF10 (0x04)<br />     (Bitová kombinace (nebo)) – nabídka je ve výchozím nastavení skrytá. Pokud je nabídka skrytá, stiskněte klávesu F10 k zobrazení nabídky a pojmenujte ji jako fokus. Pokud se nabídka zobrazí, stisknutím klávesy F10 přepněte fokus na nabídku nebo mimo ni. Nabídka se zobrazí až po stisknutí klávesy ALT nebo klávesy ESC k jejímu skrytí.|

### <a name="remarks"></a>Poznámky

Pokud hodnota parametru *nStyle* není platná, tato metoda vyhodnotí v režimu ladění a vyvolá [CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md) v režimu vydání. V případě jiných běhových chyb Tato metoda vyhodnotí v režimu ladění a vyvolá výjimku odvozenou od třídy [CException –](../../mfc/reference/cexception-class.md) .

Tato metoda ovlivňuje stav nabídek v aplikacích napsaných pro systém Windows Vista a novější.

##  <a name="setmessagetext"></a>CFrameWnd:: SetMessageText

Voláním této funkce umístíte řetězec do podokna stavového řádku s ID 0.

```
void SetMessageText(LPCTSTR lpszText);
void SetMessageText(UINT nID);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
Odkazuje na řetězec, který má být umístěn na stavovém řádku.

*nID*<br/>
ID prostředku řetězce, který má být umístěn na stavovém řádku.

### <a name="remarks"></a>Poznámky

Většinou se jedná o podokno na stavovém řádku nejvíce vlevo a nejdelší.

##  <a name="setprogressbarposition"></a>CFrameWnd:: SetProgressBarPosition

Nastaví aktuální pozici indikátoru průběhu systému Windows 7 zobrazeného na hlavním panelu.

```
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>Parametry

*nProgressPos*<br/>
Určuje pozici, kterou chcete nastavit. Musí být v rozsahu nastaveném `SetProgressBarRange`na.

### <a name="remarks"></a>Poznámky

##  <a name="setprogressbarrange"></a>CFrameWnd:: SetProgressBarRange

Nastaví rozsah indikátoru průběhu systému Windows 7 zobrazeného na hlavním panelu.

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

##  <a name="setprogressbarstate"></a>CFrameWnd:: SetProgressBarState

Nastaví typ a stav indikátoru průběhu zobrazeného na tlačítku na hlavním panelu.

```
void SetProgressBarState(TBPFLAG tbpFlags);
```

### <a name="parameters"></a>Parametry

*tbpFlags*<br/>
Příznaky, které řídí aktuální stav tlačítka průběh. Zadejte jenom jeden z následujících příznaků, protože všechny stavy se vzájemně vylučují: TBPF_NOPROGRESS, TBPF_INDETERMINATE, TBPF_NORMAL, TBPF_ERROR, TBPF_PAUSED.

### <a name="remarks"></a>Poznámky

##  <a name="settaskbaroverlayicon"></a>CFrameWnd:: SetTaskbarOverlayIcon

Přetíženo. Použije překryv na tlačítko na hlavním panelu k označení stavu aplikace nebo oznámení uživateli.

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
Určuje ID prostředku ikony, která se má použít jako překryv. Podrobnosti najdete v popisu pro *HICON* .

*lpcszDescr*<br/>
Ukazatel na řetězec, který poskytuje alternativní textovou verzi informací předaných překryvem pro účely usnadnění přístupu.

*hIcon*<br/>
Popisovač ikony, která má být použita jako překryvná. Mělo by se jednat o malou ikonu, která měří 16 × 96 bodů na palec (dpi). Pokud je ikona překrytí již použita na tlačítko na hlavním panelu, je nahrazena existující překryvná. Tato hodnota může být NULL. Způsob zpracování hodnoty NULL závisí na tom, zda tlačítko na hlavním panelu představuje jedno okno nebo skupinu oken. Je zodpovědností za volání aplikace na bezplatné *HICON* , pokud už ji nepotřebujete.

### <a name="return-value"></a>Návratová hodnota

TRUE v případě úspěchu; FALSE, pokud je verze operačního systému menší než Windows 7 nebo pokud při nastavení ikony dojde k chybě.

### <a name="remarks"></a>Poznámky

##  <a name="settitle"></a>CFrameWnd:: SetTitle

Nastaví název objektu window.

```
void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>Parametry

*lpszTitle*<br/>
Ukazatel na řetězec znaků obsahující název objektu window.

##  <a name="showcontrolbar"></a>CFrameWnd:: ShowControlBar

Chcete-li zobrazit nebo skrýt ovládací panel, zavolejte tuto členskou funkci.

```
void ShowControlBar(
    CControlBar* pBar,
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
Ukazatel na ovládací panel, který se má zobrazit nebo skrýt.

*bShow*<br/>
Je-li nastavena hodnota TRUE, určuje, zda má být zobrazeno ovládací panel. Pokud má hodnotu FALSE, určuje, že ovládací panel bude skrytý.

*bDelay*<br/>
Je-li nastavena hodnota TRUE, zpoždění zobrazení ovládacího panelu. Je-li nastavena hodnota FALSE, ovládací panel je okamžitě zobrazen.

##  <a name="showownedwindows"></a>CFrameWnd:: ShowOwnedWindows

Zavolejte tuto členskou funkci pro zobrazení všech oken, která jsou následníky `CFrameWnd` objektu.

```
void ShowOwnedWindows(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bShow*<br/>
Určuje, zda mají být vlastní okna zobrazena nebo skryta.

## <a name="see-also"></a>Viz také:

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[CMDIFrameWnd – třída](../../mfc/reference/cmdiframewnd-class.md)<br/>
[CMDIChildWnd – třída](../../mfc/reference/cmdichildwnd-class.md)<br/>
[CView – třída](../../mfc/reference/cview-class.md)<br/>
[CDocTemplate – třída](../../mfc/reference/cdoctemplate-class.md)<br/>
[CRuntimeClass – struktura](../../mfc/reference/cruntimeclass-structure.md)
