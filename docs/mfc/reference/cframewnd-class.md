---
title: Třída CFrameWnd
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
ms.openlocfilehash: 0fd104e377300233ef1526f6c453346555dd27d3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373792"
---
# <a name="cframewnd-class"></a>Třída CFrameWnd

Poskytuje funkce rozhraní s jedním dokumentem systému Windows (SDI) překrývajícího se nebo rozbalovacího okna rámce spolu s členy pro správu okna.

## <a name="syntax"></a>Syntaxe

```
class CFrameWnd : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CFrameWnd::CFrameWnd](#cframewnd)|Vytvoří `CFrameWnd` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CFrameWnd::Aktivovatrámeč](#activateframe)|Zviditelní rámeček a zpřístupní jej uživateli.|
|[CFrameWnd::BeginModalState](#beginmodalstate)|Nastaví okno rámce na modální.|
|[CFrameWnd::Vytvořit](#create)|Volání k vytvoření a inicializaci okna `CFrameWnd` rámce systému Windows přidruženéka k objektu.|
|[CFrameWnd::CreateView](#createview)|Vytvoří pohled v rámci, který není `CView`odvozen od .|
|[CFrameWnd::DockControlBar](#dockcontrolbar)|Ukotví ovládací panel.|
|[CFrameWnd::EnableDocking](#enabledocking)|Umožňuje ukotvení ovládacího panelu.|
|[CFrameWnd::EndModalState](#endmodalstate)|Ukončí modální stav okna rámce. Povolí všechna okna zakázáná programem `BeginModalState`.|
|[CFrameWnd::FloatControlBar](#floatcontrolbar)|Plovoucí ovládací panel.|
|[CFrameWnd::GetActiveDocument](#getactivedocument)|Vrátí aktivní `CDocument` objekt.|
|[CFrameWnd::GetActiveFrame](#getactiveframe)|Vrátí aktivní `CFrameWnd` objekt.|
|[CFrameWnd::GetActiveView](#getactiveview)|Vrátí aktivní `CView` objekt.|
|[CFrameWnd::Ovládací panel GetControlBar](#getcontrolbar)|Načte ovládací panel.|
|[CFrameWnd::GetDockState](#getdockstate)|Načte stav ukotvení okna rámce.|
|[CFrameWnd::GetMenuBarState](#getmenubarstate)|Načte stav zobrazení nabídky v aktuální aplikaci knihovny MFC.|
|[CFrameWnd::GetMenuBarVisibility](#getmenubarvisibility)|Označuje, zda je výchozí chování nabídky v aktuální aplikaci knihovny MFC skryté nebo viditelné.|
|[CFrameWnd::Panel zpráv GetMessageBar](#getmessagebar)|Vrátí ukazatel na stavový řádek patřící do okna rámce.|
|[CFrameWnd::GetMessageString](#getmessagestring)|Načte zprávu odpovídající ID příkazu.|
|[CFrameWnd::GetTitle](#gettitle)|Načte název souvisejícího ovládacího panelu.|
|[CFrameWnd::InitialUpdateFrame](#initialupdateframe)|Způsobí, `OnInitialUpdate` že členská funkce patřící do všech pohledů v okně rámce, které mají být volány.|
|[CFrameWnd::InModalState](#inmodalstate)|Vrátí hodnotu označující, zda je okno rámce v modálním stavu.|
|[CFrameWnd::IsTracking](#istracking)|Určuje, zda je panel rozdělovače právě přesouván.|
|[CFrameWnd::LoadAccelTable](#loadacceltable)|Volání k načtení tabulky akcelerátoru.|
|[CFrameWnd::LoadBarState](#loadbarstate)|Volání obnovení nastavení ovládacího panelu.|
|[CFrameWnd::LoadFrame](#loadframe)|Volání dynamicky vytvořit okno rámce z informací o prostředku.|
|[CFrameWnd::Vyjednathraniční prostor](#negotiateborderspace)|Vyjedná v okně rámečku prostor ohraničení.|
|[CFrameWnd::OnBarCheck](#onbarcheck)|Volána vždy, když je provedena akce na zadaném ovládacím panelu.|
|[CFrameWnd::OnContextHelp](#oncontexthelp)|Zpracovává nápovědu SHIFT+F1 pro položky na místě.|
|[CFrameWnd::OnSetPreviewMode](#onsetpreviewmode)|Nastaví okno hlavního rámce aplikace do režimu náhledu tisku a mimo něj.|
|[CFrameWnd::OnUpdateControlBarMenu](#onupdatecontrolbarmenu)|Volat rámci při aktualizaci přidružené nabídky.|
|[CFrameWnd::Rozložení recalcLayoutu](#recalclayout)|Přemístí ovládací panely `CFrameWnd` objektu.|
|[CFrameWnd::Uložitstav](#savebarstate)|Volání pro uložení nastavení ovládacího panelu.|
|[CFrameWnd::SetActivePreviewView](#setactivepreviewview)|Označuje zadané zobrazení jako aktivní zobrazení pro rozšířený náhled.|
|[CFrameWnd::SetActiveView](#setactiveview)|Nastaví `CView` aktivní objekt.|
|[CFrameWnd::SetDockState](#setdockstate)|Volání do ukotvení okna rámce v hlavním okně.|
|[CFrameWnd::SetMenuBarState](#setmenubarstate)|Nastaví stav zobrazení nabídky v aktuální aplikaci knihovny MFC na skryté nebo zobrazené.|
|[CFrameWnd::SetMenuBarVisibility](#setmenubarvisibility)|Nastaví výchozí chování nabídky v aktuální aplikaci knihovny MFC tak, aby bylo skryté nebo viditelné.|
|[CFrameWnd::SetMessageText](#setmessagetext)|Nastaví text standardního stavového řádku.|
|[CFrameWnd::SetProgressBarPosition](#setprogressbarposition)|Nastaví aktuální pozici pro ukazatel průběhu systému Windows 7 zobrazený na hlavním panelu.|
|[CFrameWnd::SetProgressBarRange](#setprogressbarrange)|Nastaví rozsah pro ukazatel průběhu systému Windows 7 zobrazený na hlavním panelu.|
|[CFrameWnd::SetProgressBarState](#setprogressbarstate)|Nastaví typ a stav indikátoru průběhu zobrazeného na tlačítku hlavního panelu.|
|[CFrameWnd::SetTaskbarOverlayIcon](#settaskbaroverlayicon)|Přetíženo. Použije překrytí na tlačítko na hlavním panelu k označení stavu aplikace nebo oznámení uživateli.|
|[CFrameWnd::SetTitle](#settitle)|Nastaví název souvisejícího ovládacího panelu.|
|[CFrameWnd::Zobrazitkontrolní panel](#showcontrolbar)|Zavolejte a ukažte ovládací panel.|
|[CFrameWnd::ShowOwnedWindows](#showownedwindows)|Zobrazí všechna okna, která `CFrameWnd` jsou potomky objektu.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CFrameWnd::OnCreateClient](#oncreateclient)|Vytvoří okno klienta pro rámec.|
|[CFrameWnd::OnHideMenuBar](#onhidemenubar)|Volána před nabídkou v aktuální aplikaci knihovny MFC je skryta.|
|[CFrameWnd::OnShowMenuBar](#onshowmenubar)|Volána před zobrazením nabídky v aktuální aplikaci knihovny MFC.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CFrameWnd::m_bAutoMenuEnable](#m_bautomenuenable)|Řídí automatické povolovací a zakazovací funkce pro položky nabídky.|
|[CFrameWnd::rectDefault](#rectdefault)|Předejte `CRect` tuto statickou hodnotu jako parametr při vytváření objektu, `CFrameWnd` který umožní systému Windows zvolit počáteční velikost a polohu okna.|

## <a name="remarks"></a>Poznámky

Chcete-li vytvořit užitečné okno rámce pro `CFrameWnd`vaši aplikaci, odvodit třídu z . Přidejte členské proměnné do odvozené třídy pro ukládání dat specifických pro vaši aplikaci. Implementujte členské funkce obslužné rutiny zpráv a mapu zpráv v odvozené třídě k určení, co se stane, když jsou zprávy směrovány do okna.

Okno rámce lze vytvořit třemi způsoby:

- Přímo jej konstruujte pomocí [funkce Vytvořit](#create).

- Přímo jej konstruujte pomocí [LoadFrame](#loadframe).

- Nepřímo vytvořit pomocí šablony dokumentu.

Před voláním `Create` `LoadFrame`buď nebo , je nutné vytvořit objekt okno rámce na haldě pomocí **c++ nový** operátor. Před `Create`voláním můžete také zaregistrovat třídu okna pomocí globální funkce [AfxRegisterWndClass](../../mfc/reference/application-information-and-management.md#afxregisterwndclass) a nastavit styly ikon a tříd pro rámec.

Pomocí `Create` členské funkce předajte parametry vytvoření rámce jako okamžité argumenty.

`LoadFrame`vyžaduje méně argumentů než `Create`aplikace a místo toho načte většinu svých výchozích hodnot z prostředků, včetně titulku, ikony, tabulky akcelerátoru a nabídky rámce. Chcete-li `LoadFrame`být přístupné podle , všechny tyto prostředky musí mít stejné ID prostředku (například IDR_MAINFRAME).

Pokud `CFrameWnd` objekt obsahuje zobrazení a dokumenty, jsou vytvořeny nepřímo rámci namísto přímo programátorem. Objekt `CDocTemplate` orchestruje vytvoření rámce, vytvoření obsahujících pohledů a připojení pohledů k příslušnému dokumentu. Parametry konstruktoru `CDocTemplate` `CRuntimeClass` určují tři zúčastněné třídy (dokument, rámeček a zobrazení). Objekt `CRuntimeClass` je používán v rámci dynamicky vytvářet nové rámce, když je určen uživatelem (například pomocí příkazu File New nebo více dokumentů rozhraní (MDI) Window New příkaz).

Frame-window třídy odvozené z `CFrameWnd` musí být deklarována s DECLARE_DYNCREATE, aby výše uvedený RUNTIME_CLASS mechanismus pracovat správně.

A `CFrameWnd` obsahuje výchozí implementace k provedení následujících funkcí hlavního okna v typické aplikaci pro Windows:

- Okno `CFrameWnd` rámce sleduje aktuálně aktivní zobrazení, které je nezávislé na aktivním okně systému Windows nebo na aktuálním vstupním fokusu. Po opětovné aktivaci rámce je aktivní pohled `CView::OnActivateView`upozorněn voláním .

- Příkazové zprávy a mnoho běžných zpráv s `OnSetFocus` `OnHScroll`oznámením `OnVScroll` rámce, včetně těch, které zpracovává aplikace , a funkce `CWnd`aplikace , jsou delegovány oknem `CFrameWnd` rámce do aktuálně aktivního zobrazení.

- Aktuálně aktivní zobrazení (nebo aktuálně aktivní okno podřízeného rámce MDI v případě rámce MDI) může určit titulek okna rámce. Tuto funkci lze zakázat vypnutím bitu FWS_ADDTOTITLE stylu okna rámce.

- Okno `CFrameWnd` rámce spravuje umístění ovládacích panelů, pohledů a dalších podřízených oken uvnitř klientské oblasti okna rámce. Okno rámce také provádí aktualizaci panelu nástrojů a dalších tlačítek ovládacího panelu. Okno `CFrameWnd` rámce má také výchozí implementace příkazů pro přepínání na a mimo panel nástrojů a stavový řádek.

- Okno `CFrameWnd` rámce spravuje hlavní řádek nabídek. Při zobrazení rozbalovací nabídky okno rámce používá mechanismus UPDATE_COMMAND_UI k určení, které položky nabídky by měly být povoleny, zakázány nebo zaškrtnuty. Když uživatel vybere položku nabídky, okno rámce aktualizuje stavový řádek řetězcem zprávy pro tento příkaz.

- Okno `CFrameWnd` rámce má volitelnou tabulku akcelerátorů, která automaticky překládá klávesové akcelerátory.

- Okno `CFrameWnd` rámce má volitelnou sadu `LoadFrame` ID nápovědy, která se používá pro kontextovou nápovědu. Okno rámce je hlavním orchestrátorem semimodál ových stavů, jako jsou kontextové nápovědy (SHIFT+F1) a režimy náhledu tisku.

- Okno `CFrameWnd` rámce otevře soubor přetažený ze Správce souborů a vysazený do okna rámce. Pokud je přípona souboru registrována a přidružena k aplikaci, okno rámce reaguje na požadavek otevření dynamické výměny dat `ShellExecute` (DDE), ke kterému dochází, když uživatel otevře datový soubor ve Správci souborů nebo když je volána funkce systému Windows.

- Pokud je okno rámce hlavním oknem `CWinThread::m_pMainWnd`aplikace (tj. ), když uživatel aplikaci zavře, zobrazí okno rámce `OnClose` `OnQueryEndSession`výzvu uživateli k uložení upravených dokumentů (pro a).

- Pokud je okno rámce hlavním oknem aplikace, okno rámce je kontext pro spuštění služby WinHelp. Zavřením okna rámce se vypne WINHELP. EXE, pokud byl spuštěn pro pomoc pro tuto aplikaci.

Nepoužívejte operátor **delete** jazyka C++ ke zničení okna rámce. Místo toho použijte `CWnd::DestroyWindow`. Implementace `CFrameWnd` `PostNcDestroy` odstraní objekt C++ při zničení okna. Když uživatel zavře okno rámce, `OnClose` bude volat `DestroyWindow`výchozí obslužná rutina .

Další informace `CFrameWnd`naleznete v tématu [Frame Windows](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CFrameWnd`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="cframewndactivateframe"></a><a name="activateframe"></a>CFrameWnd::Aktivovatrámeč

Volání této členské funkce k aktivaci a obnovení okna rámce tak, aby bylo viditelné a dostupné uživateli.

```
virtual void ActivateFrame(int nCmdShow = -1);
```

### <a name="parameters"></a>Parametry

*nCmdZobrazit*<br/>
Určuje parametr, který má být předaný [cWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow). Ve výchozím nastavení je rámeček zobrazen a správně obnoven.

### <a name="remarks"></a>Poznámky

Tato členská funkce je obvykle volána po události neuživatelského rozhraní, jako je například Událost DDE, OLE nebo jiná událost, která může uživateli zobrazit okno rámce nebo jeho obsah.

Výchozí implementace aktivuje rámec a přenese jej na začátek pořadí vykresl.

Přepsáním této členské funkce můžete změnit způsob aktivace rámce. Můžete například vynutit maximalizaci podřízených oken MDI. Přidejte příslušnou funkci a pak zavolejte verzi základní třídy s explicitním *nCmdShow*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#1](../../mfc/reference/codesnippet/cpp/cframewnd-class_1.cpp)]

## <a name="cframewndbeginmodalstate"></a><a name="beginmodalstate"></a>CFrameWnd::BeginModalState

Volání této členské funkce, aby okno rámce modální.

```
virtual void BeginModalState();
```

## <a name="cframewndcframewnd"></a><a name="cframewnd"></a>CFrameWnd::CFrameWnd

Vytvoří `CFrameWnd` objekt, ale nevytvoří okno viditelného rámečku.

```
CFrameWnd();
```

### <a name="remarks"></a>Poznámky

Volání `Create` k vytvoření viditelného okna.

## <a name="cframewndcreate"></a><a name="create"></a>CFrameWnd::Vytvořit

Volání k vytvoření a inicializaci okna `CFrameWnd` rámce systému Windows přidruženéka k objektu.

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

*název lpszClassName*<br/>
Odkazuje na řetězec znaků ukončený nulou, který pojmenovává třídu systému Windows. Název třídy může být libovolný `AfxRegisterWndClass` název registrovaný `RegisterClass` pomocí globální funkce nebo funkce systému Windows. Pokud null, používá předdefinované výchozí `CFrameWnd` atributy.

*lpszNázev_okna*<br/>
Odkazuje na řetězec znaků ukončený hodnotou null, který představuje název okna. Používá se jako text pro záhlaví.

*dwStyl*<br/>
Určuje atributy [stylu](../../mfc/reference/styles-used-by-mfc.md#window-styles) okna. Pokud chcete, aby se v záhlaví automaticky zobrazoval název dokumentu reprezentovaného v okně, zahrňte styl FWS_ADDTOTITLE.

*Rect*<br/>
Určuje velikost a umístění okna. Hodnota *rectDefault* umožňuje systému Windows určit velikost a umístění nového okna.

*pParentWnd*<br/>
Určuje nadřazené okno tohoto okna rámce. Tento parametr by měl být null pro okna rámce nejvyšší úrovně.

*název lpszMenuName*<br/>
Identifikuje název prostředku nabídky, který má být použit s oknem. MakeinTRESOURCE použijte, pokud nabídka má celé číslo ID místo řetězce. Tento parametr může být NULL.

*dwExStyl*<br/>
Určuje atributy rozšířeného [stylu](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) okna.

*pKontext*<br/>
Určuje ukazatel na strukturu [CCreateContext.](../../mfc/reference/ccreatecontext-structure.md) Tento parametr může být NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je inicializace úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Vytvořte `CFrameWnd` objekt ve dvou krocích. Nejprve vyvolat konstruktor, který `CFrameWnd` vytvoří objekt a `Create`potom volání , který vytvoří okno `CFrameWnd` rámce systému Windows a připojí jej k objektu. `Create`inicializuje název třídy a název okna okna a zaregistruje výchozí hodnoty pro jeho styl, nadřazený a přidruženou nabídku.

Místo `LoadFrame` `Create` načtení okna rámce z prostředku použijte místo určení jeho argumentů.

## <a name="cframewndcreateview"></a><a name="createview"></a>CFrameWnd::CreateView

Volání `CreateView` k vytvoření zobrazení v rámci.

```
CWnd* CreateView(
    CCreateContext* pContext,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>Parametry

*pKontext*<br/>
Určuje typ zobrazení a dokumentu.

*Nid*<br/>
Číslo ID zobrazení.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CWnd` objekt v případě úspěchu; jinak NULL.

### <a name="remarks"></a>Poznámky

Tato členská funkce slouží k vytvoření `CView`"zobrazení", které nejsou odvozeny v rámci. Po `CreateView`volání je nutné ručně nastavit zobrazení na aktivní a nastavit tak, aby bylo viditelné. Tyto úkoly nejsou `CreateView`automaticky prováděny společností .

## <a name="cframewnddockcontrolbar"></a><a name="dockcontrolbar"></a>CFrameWnd::DockControlBar

Způsobí, že ovládací panel, který má být ukotven do okna rámce.

```
void DockControlBar(
    CControlBar* pBar,
    UINT nDockBarID = 0,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
Odkazuje na ovládací panel, který má být ukotven.

*nDockBarID*<br/>
Určuje, které strany okna rámce je třeba zvážit pro ukotvení. Může to být 0 nebo jedna nebo více z následujících možností:

- AFX_IDW_DOCKBAR_TOP ukotvení na horní stranu okna rámce.

- AFX_IDW_DOCKBAR_BOTTOM Dock na spodní straně okna rámce.

- AFX_IDW_DOCKBAR_LEFT ukotvení na levé straně okna rámce.

- AFX_IDW_DOCKBAR_RIGHT Ukotvení na pravé straně okna rámce.

Pokud 0, ovládací panel může být ukotven na libovolnou stranu povolenou pro ukotvení v okně cílového rámce.

*lpRect*<br/>
Určuje, kde bude ovládací panel ukotven v neklientské oblasti okna cílového rámce, na souřadnicích obrazovky.

### <a name="remarks"></a>Poznámky

Ovládací panel bude ukotven k jedné ze stran okna rámce určenému ve volání [ccontrolbar::EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking) a [CFrameWnd::EnableDocking](#enabledocking). Zvolená strana je určena *nDockBarID*.

## <a name="cframewndenabledocking"></a><a name="enabledocking"></a>CFrameWnd::EnableDocking

Volání této funkce povolit dokovatelné ovládací panely v okně rámce.

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Parametry

*dwDockStyl*<br/>
Určuje, které strany okna rámce mohou sloužit jako dokovací lokality pro ovládací panely. Může to být jedna nebo více z následujících možností:

- CBRS_ALIGN_TOP Umožňuje ukotvení v horní části klientské oblasti.

- CBRS_ALIGN_BOTTOM Umožňuje ukotvení v dolní části klientské oblasti.

- CBRS_ALIGN_LEFT Umožňuje ukotvení na levé straně klientské oblasti.

- CBRS_ALIGN_RIGHT Umožňuje ukotvení na pravé straně klientské oblasti.

- CBRS_ALIGN_ANY Umožňuje ukotvení na libovolné straně klientské oblasti.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení budou ovládací panely ukotveny na stranu okna rámce v následujícím pořadí: nahoře, dole, vlevo, vpravo.

### <a name="example"></a>Příklad

  Viz příklad [ctoolbar::create](../../mfc/reference/ctoolbar-class.md#create).

## <a name="cframewndendmodalstate"></a><a name="endmodalstate"></a>CFrameWnd::EndModalState

Volání této členské funkce změnit okno rámce z modální moderování.

```
virtual void EndModalState();
```

### <a name="remarks"></a>Poznámky

`EndModalState`povolí všechna okna zakázána [BeginModalState](#beginmodalstate).

## <a name="cframewndfloatcontrolbar"></a><a name="floatcontrolbar"></a>CFrameWnd::FloatControlBar

Volání této funkce způsobí, že ovládací panel není ukotven do okna rámce.

```
void FloatControlBar(
    CControlBar* pBar,
    CPoint point,
    DWORD dwStyle = CBRS_ALIGN_TOP);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
Odkazuje na ovládací panel, který má být plovoucí.

*Bod*<br/>
Umístění na souřadnicích obrazovky, kde bude umístěn levý horní roh ovládacího panelu.

*dwStyl*<br/>
Určuje, zda má být ovládací panel zarovnán vodorovně nebo svisle v novém okně rámce. Může to být některá z následujících možností:

- CBRS_ALIGN_TOP Orientuje ovládací panel svisle.

- CBRS_ALIGN_BOTTOM Orientuje ovládací panel svisle.

- CBRS_ALIGN_LEFT Orientuje ovládací panel vodorovně.

- CBRS_ALIGN_RIGHT Orientuje ovládací panel vodorovně.

Pokud jsou styly předány určující vodorovnou i svislou orientaci, bude panel nástrojů orientován vodorovně.

### <a name="remarks"></a>Poznámky

Obvykle se to provádí při spuštění aplikace při obnovení nastavení programu z předchozího spuštění.

Tato funkce je volána rámci, když uživatel způsobí operaci přetažení uvolněním levé tlačítko myši při přetažení ovládacího panelu přes umístění, které není k dispozici pro ukotvení.

## <a name="cframewndgetactivedocument"></a><a name="getactivedocument"></a>CFrameWnd::GetActiveDocument

Volání této členské funkce získat ukazatel `CDocument` na aktuální připojené k aktuální aktivní zobrazení.

```
virtual CDocument* GetActiveDocument();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktuální [CDocument](../../mfc/reference/cdocument-class.md). Pokud neexistuje žádný aktuální dokument, vrátí hodnotu NULL.

## <a name="cframewndgetactiveframe"></a><a name="getactiveframe"></a>CFrameWnd::GetActiveFrame

Volání této členské funkce získat ukazatel na aktivní rozhraní více dokumentů (MDI) podřízené okno okna rámce MDI.

```
virtual CFrameWnd* GetActiveFrame();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktivní podřízené okno MDI. Pokud je aplikace aplikace SDI nebo okno rámce MDI nemá žádný aktivní dokument, implicitní **tento** ukazatel bude vrácena.

### <a name="remarks"></a>Poznámky

Pokud neexistuje žádný aktivní Podřízený MDI nebo aplikace je jeden dokument rozhraní (SDI), implicitní **tento** ukazatel je vrácena.

## <a name="cframewndgetactiveview"></a><a name="getactiveview"></a>CFrameWnd::GetActiveView

Volánítéto členské funkce získat ukazatel na aktivní zobrazení (pokud existuje) `CFrameWnd`připojené k oknu rámce ( ).

```
CView* GetActiveView() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktuální [CView](../../mfc/reference/cview-class.md). Pokud neexistuje žádné aktuální zobrazení, vrátí hodnotu NULL.

### <a name="remarks"></a>Poznámky

Tato funkce vrátí hodnotu NULL při volání `CMDIFrameWnd`okna hlavního rámce MDI ( ). V aplikaci MDI okno hlavního rámce MDI nemá přidružené zobrazení. Místo toho má každé `CMDIChildWnd`jednotlivé podřízené okno ( ) jedno nebo více přidružených zobrazení. Aktivní zobrazení v aplikaci MDI lze získat nejprve najít aktivní podřízené okno MDI a potom najít aktivní zobrazení pro toto podřízené okno. Aktivní podřízené okno MDI lze nalézt `MDIGetActive` `GetActiveFrame` voláním funkce nebo jak je znázorněno v následujícím textu:

[!code-cpp[NVC_MFCWindowing#2](../../mfc/reference/codesnippet/cpp/cframewnd-class_2.cpp)]

## <a name="cframewndgetcontrolbar"></a><a name="getcontrolbar"></a>CFrameWnd::Ovládací panel GetControlBar

Volání `GetControlBar` získat přístup k ovládacímu panelu, který je spojen s ID.

```
CControlBar* GetControlBar(UINT nID);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
ID číslo ovládacího panelu.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na ovládací panel, který je přidružen k ID.

### <a name="remarks"></a>Poznámky

Parametr *nID* odkazuje na jedinečný identifikátor `Create` předaný metodě ovládacího panelu. Další informace o ovládacích panelech naleznete v tématu [Kontrolní panely](../../mfc/control-bars.md).

`GetControlBar`vrátí ovládací panel, i když je plovoucí, a proto není aktuálně podřízeným oknem rámečku.

## <a name="cframewndgetdockstate"></a><a name="getdockstate"></a>CFrameWnd::GetDockState

Volání této členské funkce k uložení informací o stavu `CDockState` ovládacích panelů okna rámce v objektu.

```
void GetDockState(CDockState& state) const;
```

### <a name="parameters"></a>Parametry

*Státu*<br/>
Obsahuje aktuální stav ovládacích panelů okna rámce při návratu.

### <a name="remarks"></a>Poznámky

Obsah aplikace můžete potom `CDockState` zapsat `CDockState::SaveState` `Serialize`do úložiště pomocí aplikace nebo . Pokud později chcete obnovit ovládací panely do předchozího `CDockState::LoadState` stavu, načtěte stav s nebo `Serialize`, pak volání `SetDockState` použít předchozí stav na ovládací panely okna rámce.

## <a name="cframewndgetmenubarstate"></a><a name="getmenubarstate"></a>CFrameWnd::GetMenuBarState

Načte stav zobrazení nabídky v aktuální aplikaci knihovny MFC.

```
virtual DWORD GetMenuBarState();
```

### <a name="return-value"></a>Návratová hodnota

Vrácená hodnota může mít následující hodnoty:

- AFX_MBS_VISIBLE (0x01) - Nabídka je viditelná.

- AFX_MBS_HIDDEN (0x02) - Nabídka je skrytá.

### <a name="remarks"></a>Poznámky

Pokud dojde k chybě za běhu, tato metoda uplatňuje v režimu ladění a vyvolá výjimku odvozenou z třídy [CException.](../../mfc/reference/cexception-class.md)

## <a name="cframewndgetmenubarvisibility"></a><a name="getmenubarvisibility"></a>CFrameWnd::GetMenuBarVisibility

Označuje, zda je výchozí stav nabídky v aktuální aplikaci knihovny MFC skrytý nebo viditelný.

```
virtual DWORD CFrameWnd::GetMenuBarVisibility();
```

### <a name="return-value"></a>Návratová hodnota

Tato metoda vrátí jednu z následujících hodnot:

- AFX_MBV_KEEPVISIBLE (0x01) - Nabídka se zobrazí po celou dobu a ve výchozím nastavení nemá fokus.

- AFX_MBV_DISPLAYONFOCUS (0x02) - Nabídka je ve výchozím nastavení skrytá. Pokud je nabídka skrytá, stisknutím klávesy ALT zobrazte nabídku a zaostřete ji. Pokud se zobrazí nabídka, skryjte ji stisknutím klávesy ALT nebo ESC.

- AFX_MBV_ DISPLAYONFOCUS (0x02) &#124; AFX_MBV_DISPLAYONF10 (0x04) (bitová kombinace (OR)) - Nabídka je ve výchozím nastavení skrytá. Pokud je nabídka skrytá, stisknutím klávesy F10 zobrazte nabídku a zaostřete ji. Pokud se zobrazí nabídka, stisknutím klávesy F10 přepněte zaostření na nabídku nebo mimo ni. Nabídka se zobrazí, dokud ji nestisknete klávesou ALT nebo ESC, abyste ji skryli.

### <a name="remarks"></a>Poznámky

Pokud dojde k chybě za běhu, tato metoda uplatňuje v režimu ladění a vyvolá výjimku odvozenou z třídy [CException.](../../mfc/reference/cexception-class.md)

## <a name="cframewndgetmessagebar"></a><a name="getmessagebar"></a>CFrameWnd::Panel zpráv GetMessageBar

Volání této členské funkce získat ukazatel na stavový řádek.

```
virtual CWnd* GetMessageBar();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na okno stavového řádku.

## <a name="cframewndgetmessagestring"></a><a name="getmessagestring"></a>CFrameWnd::GetMessageString

Přepsat tuto funkci poskytnout vlastní řetězce pro ID příkazu.

```
virtual void GetMessageString(
    UINT nID,
    CString& rMessage) const;
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
ID prostředku požadované zprávy.

*rZpráva*<br/>
`CString`objekt, do kterého chcete umístit zprávu.

### <a name="remarks"></a>Poznámky

Výchozí implementace jednoduše načte řetězec určený *nID* ze souboru prostředků. Tato funkce je volána v rámci, když řetězec zprávy ve stavovém řádku potřebuje aktualizaci.

## <a name="cframewndgettitle"></a><a name="gettitle"></a>CFrameWnd::GetTitle

Načte název objektu okna.

```
CString GetTitle() const;
```

### <a name="return-value"></a>Návratová hodnota

[CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt obsahující aktuální název objektu okna.

## <a name="cframewndinitialupdateframe"></a><a name="initialupdateframe"></a>CFrameWnd::InitialUpdateFrame

Volat `IntitialUpdateFrame` po vytvoření nového rámce s . `Create`

```
void InitialUpdateFrame(
    CDocument* pDoc,
    BOOL bMakeVisible);
```

### <a name="parameters"></a>Parametry

*pDoc*<br/>
Odkazuje na dokument, ke kterému je okno rámce přidruženo. Může být NULL.

*bMakeVisible*<br/>
Pokud TRUE, označuje, že snímek by měl být viditelný a aktivní. Pokud false, žádné potomky jsou viditelné.

### <a name="remarks"></a>Poznámky

To způsobí, že všechny pohledy `OnInitialUpdate` v tomto okně rámce přijímat jejich volání.

Také pokud dříve nebyl aktivní pohled, primární pohled okna rámce je aktivní. Primární zobrazení je zobrazení s podřízeným ID AFX_IDW_PANE_FIRST. Nakonec okno rámce je zviditelněn, pokud *bMakeVisible* je nenulová. Pokud *bMakeVisible* je 0, aktuální fokus a viditelný stav okna rámce zůstane beze změny. Není nutné volat tuto funkci při použití implementace rozhraní File New a File Open.

## <a name="cframewndinmodalstate"></a><a name="inmodalstate"></a>CFrameWnd::InModalState

Volání této členské funkce ke kontrole, zda okno rámce je modální nebo nemodální.

```
BOOL InModalState() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud ano; jinak 0.

## <a name="cframewndistracking"></a><a name="istracking"></a>CFrameWnd::IsTracking

Volání této členské funkce k určení, zda je nyní přesouván rozdělovač v okně.

```
BOOL IsTracking() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud probíhá operace rozdělovače; jinak 0.

## <a name="cframewndloadacceltable"></a><a name="loadacceltable"></a>CFrameWnd::LoadAccelTable

Volání k načtení zadané tabulky akcelerátoru.

```
BOOL LoadAccelTable(LPCTSTR lpszResourceName);
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Identifikuje název prostředku akcelerátoru. MakeinTRESOURCE použijte, pokud je prostředek identifikován s ID celého čísla.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla tabulka akcelerátoru úspěšně načtena; jinak 0.

### <a name="remarks"></a>Poznámky

Najednou lze načíst pouze jednu tabulku.

Tabulky akcelerátorů načtené z prostředků jsou uvolněny automaticky při ukončení aplikace.

Pokud voláte `LoadFrame` k vytvoření okna rámce, rozhraní načte tabulku akcelerátoru spolu s prostředky nabídky a ikony a následné volání této členské funkce je pak zbytečné.

## <a name="cframewndloadbarstate"></a><a name="loadbarstate"></a>CFrameWnd::LoadBarState

Volánítéto funkce obnovit nastavení každého ovládacího panelu ve vlastnictví okna rámce.

```
void LoadBarState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
Název oddílu v inicializačním souboru (INI) nebo klíče v registru systému Windows, kde jsou uloženy informace o stavu.

### <a name="remarks"></a>Poznámky

Obnovené informace zahrnují viditelnost, vodorovnou/svislou orientaci, stav ukotvení a polohu ovládacího panelu.

Nastavení, která chcete obnovit, musí být před `LoadBarState`voláním zapsáno do registru . Napište informace do registru voláním [CWinApp::SetRegistryKey](../../mfc/reference/cwinapp-class.md#setregistrykey). Napište informace do souboru INI voláním [SaveBarState](#savebarstate).

## <a name="cframewndloadframe"></a><a name="loadframe"></a>CFrameWnd::LoadFrame

Volání dynamicky vytvořit okno rámce z informací o prostředku.

```
virtual BOOL LoadFrame(
    UINT nIDResource,
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,
    CWnd* pParentWnd = NULL,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Parametry

*nIDZdroj*<br/>
ID sdílených prostředků přidružených k oknu rámce.

*dwDefaultStyle*<br/>
[Styl rámečku](../../mfc/reference/styles-used-by-mfc.md#window-styles). Pokud chcete, aby se v záhlaví automaticky zobrazoval název dokumentu reprezentovaného v okně, zahrňte styl FWS_ADDTOTITLE.

*pParentWnd*<br/>
Ukazatel na nadřazený snímek.

*pKontext*<br/>
Ukazatel na [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) struktury. Tento parametr může být NULL.

### <a name="remarks"></a>Poznámky

Vytvořte `CFrameWnd` objekt ve dvou krocích. Nejprve vyvoláte konstruktor, který `CFrameWnd` vytvoří objekt, `LoadFrame`a potom volejte , který načte okno rámce `CFrameWnd` systému Windows a přidružené prostředky a připojí okno rámce k objektu. Parametr *nIDResource* určuje nabídku, tabulku akcelerátoru, ikonu a zdroj řetězce názvu okna rámce.

Použijte `Create` členovou funkci, nikoli `LoadFrame` pokud chcete zadat všechny parametry vytvoření okna rámce.

Rozhraní Framework `LoadFrame` volá při vytvoření okna rámce pomocí objektu šablony dokumentu.

Framework používá argument *pContext* k určení objektů, které mají být připojeny k oknu rámce, včetně všech obsažených objektů zobrazení. Při volání můžete nastavit argument *pContext* na HODNOTU `LoadFrame`NULL.

## <a name="cframewndm_bautomenuenable"></a><a name="m_bautomenuenable"></a>CFrameWnd::m_bAutoMenuEnable

Pokud je tento datový člen povolen (což je výchozí), položky nabídky, které nemají ON_UPDATE_COMMAND_UI nebo obslužné rutiny ON_COMMAND, budou automaticky zakázány, když uživatel stáhne nabídku dolů.

```
BOOL m_bAutoMenuEnable;
```

### <a name="remarks"></a>Poznámky

Položky nabídky, které mají obslužnou rutinu ON_COMMAND, ale žádnou obslužnou rutinu ON_UPDATE_COMMAND_UI, budou automaticky povoleny.

Je-li tento datový člen nastaven, jsou položky nabídky automaticky povoleny stejným způsobem jako tlačítka panelu nástrojů.

> [!NOTE]
> `m_bAutoMenuEnable`nemá žádný vliv na položky nabídky nejvyšší úrovně.

Tento datový člen zjednodušuje implementaci volitelných příkazů na základě aktuálního výběru a snižuje potřebu zápisu ON_UPDATE_COMMAND_UI obslužných rutin pro povolení a zakázání položek nabídky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#3](../../mfc/reference/codesnippet/cpp/cframewnd-class_3.cpp)]

## <a name="cframewndnegotiateborderspace"></a><a name="negotiateborderspace"></a>CFrameWnd::Vyjednathraniční prostor

Volání této členské funkce vyjednat ohraničení prostoru v okně rámce během aktivace ole.

```
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,
    LPRECT lpRectBorder);
```

### <a name="parameters"></a>Parametry

*nBorderCmd*<br/>
Obsahuje jednu z následujících hodnot z `enum BorderCmd`:

- `borderGet`= 1

- `borderRequest`= 2

- `borderSet`= 3

*lpRectBorder*<br/>
Ukazatel na [rect](/windows/win32/api/windef/ns-windef-rect) struktury nebo [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt, který určuje souřadnice ohraničení.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská `CFrameWnd` funkce je implementace vyjednávání ole prostoru ohraničení.

## <a name="cframewndonbarcheck"></a><a name="onbarcheck"></a>CFrameWnd::OnBarCheck

Volána vždy, když je provedena akce na zadaném ovládacím panelu.

```
afx_msg BOOL OnBarCheck(UINT nID);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Zobrazí se ID ovládacího panelu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud ovládací panel existoval; jinak 0.

## <a name="cframewndoncontexthelp"></a><a name="oncontexthelp"></a>CFrameWnd::OnContextHelp

Zpracovává nápovědu SHIFT+F1 pro položky na místě.

```
afx_msg void OnContextHelp();
```

### <a name="remarks"></a>Poznámky

Chcete-li povolit kontextovou nápovědu, je nutné přidat

[!code-cpp[NVC_MFCDocViewSDI#16](../../mfc/codesnippet/cpp/cframewnd-class_4.cpp)]

příkaz do `CFrameWnd` mapy zpráv třídy a také přidejte položku tabulky akcelerátoru, obvykle SHIFT+F1, abyste tuto členskou funkci povolili.

Pokud je vaše aplikace `OnContextHelp` kontejner OLE, umístí všechny položky na místě obsažené v objektu okna rámce do režimu nápovědy. Kurzor se změní na šipku a otazník a uživatel pak může pohybovat ukazatelem myši a stisknutím levého tlačítka myši vybrat dialogové okno, okno, nabídku nebo příkazové tlačítko. Tato členská funkce `WinHelp` volá funkci systému Windows s kontextem nápovědy objektu pod kurzorem.

## <a name="cframewndoncreateclient"></a><a name="oncreateclient"></a>CFrameWnd::OnCreateClient

Volal rámci během provádění `OnCreate`.

```
virtual BOOL OnCreateClient(
    LPCREATESTRUCT lpcs,
    CCreateContext* pContext);
```

### <a name="parameters"></a>Parametry

*lpcs*<br/>
Ukazatel na strukturu Windows [CREATESTRUCT.](/windows/win32/api/winuser/ns-winuser-createstructw)

*pKontext*<br/>
Ukazatel na [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) struktury.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Nikdy nevolejte tuto funkci.

Výchozí implementace této funkce `CView` vytvoří objekt z informací poskytnutých v *pContext*, pokud je to možné.

Přepsáním této funkce přepište `CCreateContext` hodnoty předané v objektu nebo změňte způsob vytváření ovládacích prvků v hlavní klientské oblasti okna rámce. Členové, `CCreateContext` které můžete přepsat, jsou popsány ve třídě [CCreateContext.](../../mfc/reference/ccreatecontext-structure.md)

> [!NOTE]
> Nenahrazujte hodnoty `CREATESTRUCT` předané ve struktuře. Jsou určeny pouze pro informační použití. Pokud chcete přepsat počáteční obdélník okna, například přepsat `CWnd` členská funkce [PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow).

## <a name="cframewndonhidemenubar"></a><a name="onhidemenubar"></a>CFrameWnd::OnHideMenuBar

Tato funkce je volána, když se systém chystá skrýt řádek nabídek v aktuální aplikaci knihovny MFC.

```
virtual void OnHideMenuBar();
```

### <a name="remarks"></a>Poznámky

Tato obslužná rutina události umožňuje aplikaci provádět vlastní akce, když se systém chystá skrýt nabídku. Nemůžete zabránit skrytí nabídky, ale můžete například volat jiné metody pro načtení stylu nebo stavu nabídky.

## <a name="cframewndonsetpreviewmode"></a><a name="onsetpreviewmode"></a>CFrameWnd::OnSetPreviewMode

Volání této členské funkce nastavit okno hlavního rámce aplikace do a z režimu náhledu tisku.

```
virtual void OnSetPreviewMode(
    BOOL bPreview,
    CPrintPreviewState* pState);
```

### <a name="parameters"></a>Parametry

*bNáhled*<br/>
Určuje, zda má být aplikace v režimu náhledu tisku. Nastavte hodnotu TRUE, chcete-li umístit do náhledu tisku, NEPRAVDA, chcete-li zrušit režim náhledu.

*pStát*<br/>
Ukazatel na `CPrintPreviewState` strukturu.

### <a name="remarks"></a>Poznámky

Výchozí implementace zakáže všechny standardní panely nástrojů a skryje hlavní nabídku a okno hlavního klienta. Tím se změní okna rámce MDI na dočasná okna rámce SDI.

Přepsáním této členské funkce můžete přizpůsobit skrytí a zobrazení ovládacích panelů a dalších částí okna rámů během náhledu. Volání implementace základní třídy z v rámci popsané verze.

## <a name="cframewndonshowmenubar"></a><a name="onshowmenubar"></a>CFrameWnd::OnShowMenuBar

Tato funkce je volána, když se systém chystá zobrazit řádek nabídek v aktuální aplikaci knihovny MFC.

```
virtual void OnShowMenuBar();
```

### <a name="remarks"></a>Poznámky

Tato obslužná rutina události umožňuje aplikaci provádět vlastní akce při zobrazení nabídky. Nemůžete zabránit zobrazení nabídky, ale můžete například volat jiné metody pro načtení stylu nebo stavu nabídky.

## <a name="cframewndonupdatecontrolbarmenu"></a><a name="onupdatecontrolbarmenu"></a>CFrameWnd::OnUpdateControlBarMenu

Volat rámci při aktualizaci přidružené nabídky.

```
afx_msg void OnUpdateControlBarMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Ukazatel na objekt [CCmdUI](../../mfc/reference/ccmdui-class.md) představující nabídku, která generovala příkaz aktualizace. Obslužná rutina aktualizace `CCmdUI` volá [povolit](../../mfc/reference/ccmdui-class.md#enable) členská funkce objektu prostřednictvím *pCmdUI* aktualizovat uživatelské rozhraní.

## <a name="cframewndrecalclayout"></a><a name="recalclayout"></a>CFrameWnd::Rozložení recalcLayoutu

Volat rámci při standardní ovládací panely jsou přepnutí zapnutí nebo vypnutí nebo při velikosti okna rámce.

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Parametry

*bUpozornit*<br/>
Určuje, zda aktivní položka na místě pro okno rámce obdrží oznámení o změně rozložení. Pokud true, položka je upozorněn; jinak FALSE.

### <a name="remarks"></a>Poznámky

Výchozí implementace této členské funkce `CWnd` volá `RepositionBars` členskou funkci pro přemístění všech ovládacích panelů v rámci `CView` i v hlavním okně klienta (obvykle a nebo MDICLIENT).

Přepište tuto členovou funkci a ovládejte vzhled a chování ovládacích panelů po změně rozložení okna rámce. Například jej zavolejte, když zapnete nebo vypnete ovládací panely nebo přidáte další ovládací panel.

## <a name="cframewndrectdefault"></a><a name="rectdefault"></a>CFrameWnd::rectDefault

Předejte `CRect` tuto statickou hodnotu jako parametr při vytváření okna, aby systém Windows mohl zvolit počáteční velikost a polohu okna.

```
static AFX_DATA const CRect rectDefault;
```

## <a name="cframewndsavebarstate"></a><a name="savebarstate"></a>CFrameWnd::Uložitstav

Volání této funkce k uložení informací o každém ovládacím panelu vlastněném oknem rámce.

```
void SaveBarState(LPCTSTR lpszProfileName) const;
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
Název oddílu v inicializačním souboru nebo klíče v registru systému Windows, kde jsou uloženy informace o stavu.

### <a name="remarks"></a>Poznámky

Tyto informace lze číst z inicializačního souboru pomocí [LoadBarState](#loadbarstate). Uložené informace zahrnují viditelnost, vodorovnou/svislou orientaci, stav ukotvení a polohu ovládacího panelu.

## <a name="cframewndsetactivepreviewview"></a><a name="setactivepreviewview"></a>CFrameWnd::SetActivePreviewView

Označuje zadané zobrazení jako aktivní zobrazení pro rozšířený náhled.

```
void SetActivePreviewView(CView* pViewNew);
```

### <a name="parameters"></a>Parametry

*pViewNew*<br/>
Ukazatel na zobrazení, které má být aktivováno.

### <a name="remarks"></a>Poznámky

## <a name="cframewndsetactiveview"></a><a name="setactiveview"></a>CFrameWnd::SetActiveView

Volánítéto členské funkce pro nastavení aktivního zobrazení.

```
void SetActiveView(
    CView* pViewNew,
    BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Parametry

*pViewNew*<br/>
Určuje ukazatel na objekt [CView](../../mfc/reference/cview-class.md) nebo HODNOTU NULL pro žádné aktivní zobrazení.

*bUpozornit*<br/>
Určuje, zda má být zobrazení oznámeno aktivaci. Pokud TRUE, `OnActivateView` je volána pro nové zobrazení; pokud false, není.

### <a name="remarks"></a>Poznámky

Rozhraní Framework bude tuto funkci volat automaticky, když uživatel změní fokus na zobrazení v okně rámce. Můžete explicitně `SetActiveView` volat a změnit fokus na zadané zobrazení.

## <a name="cframewndsetdockstate"></a><a name="setdockstate"></a>CFrameWnd::SetDockState

Volání této členské funkce použít informace `CDockState` o stavu uložené v objektu na ovládací panely okna rámce.

```
void SetDockState(const CDockState& state);
```

### <a name="parameters"></a>Parametry

*Státu*<br/>
Použijte uložený stav na ovládací panely okna rámce.

### <a name="remarks"></a>Poznámky

Chcete-li obnovit předchozí stav ovládacích panelů, `CDockState::LoadState` můžete `Serialize`načíst `SetDockState` uložený stav pomocí nástroje nebo , který slouží k jeho použití na ovládací panely okna rámce. Předchozí stav je uložen `CDockState` v objektu s`GetDockState`

## <a name="cframewndsetmenubarstate"></a><a name="setmenubarstate"></a>CFrameWnd::SetMenuBarState

Nastaví stav zobrazení nabídky v aktuální aplikaci knihovny MFC na skryté nebo zobrazené.

```
virtual BOOL SetMenuBarState(DWORD nState);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*nStát*|[v] Určuje, zda se má nabídka zobrazit nebo skrýt. Parametr *nState* může mít následující hodnoty:<br /><br />- AFX_MBS_VISIBLE (0x01) - Zobrazí nabídku, pokud je skrytá, ale nemá žádný vliv, pokud je viditelná.<br />- AFX_MBS_HIDDEN (0x02) - Skryje menu, pokud je viditelné, ale nemá žádný vliv, pokud je skrytý.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud tato metoda úspěšně změní stav nabídky; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Pokud dojde k chybě za běhu, tato metoda uplatňuje v režimu ladění a vyvolá výjimku odvozenou z třídy [CException.](../../mfc/reference/cexception-class.md)

## <a name="cframewndsetmenubarvisibility"></a><a name="setmenubarvisibility"></a>CFrameWnd::SetMenuBarVisibility

Nastaví výchozí chování nabídky v aktuální aplikaci knihovny MFC tak, aby bylo skryté nebo viditelné.

```
virtual void SetMenuBarVisibility(DWORD nStyle);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*nStyl*|[v] Určuje, zda je nabídka ve výchozím nastavení skrytá, zda je viditelná a zda je fokusována. Parametr *nStyle* může mít následující hodnoty:<br /><br />- AFX_MBV_KEEPVISIBLE (0x01) -<br />     Nabídka se zobrazí po celou dobu a ve výchozím nastavení nemá fokus.<br />- AFX_MBV_DISPLAYONFOCUS (0x02) -<br />     Nabídka je ve výchozím nastavení skrytá. Pokud je nabídka skrytá, stisknutím klávesy ALT zobrazte nabídku a zaostřete ji. Pokud se zobrazí nabídka, stisknutím klávesy ALT nebo ESC nabídku skryjete.<br />- AFX_MBV_ DISPLAYONFOCUS (0x02) &#124; AFX_MBV_DISPLAYONF10 (0x04)<br />     (bitová kombinace (OR)) - Nabídka je ve výchozím nastavení skrytá. Pokud je nabídka skrytá, stisknutím klávesy F10 zobrazte nabídku a zaostřete ji. Pokud se zobrazí nabídka, stisknutím klávesy F10 přepněte zaostření na nabídku nebo mimo ni. Nabídka se zobrazí, dokud ji nestisknete klávesou ALT nebo ESC, abyste ji skryli.|

### <a name="remarks"></a>Poznámky

Pokud hodnota parametru *nStyle* není platná, tato metoda se uplatňuje v režimu ladění a vyvolá [cinvalidargexception](../../mfc/reference/cinvalidargexception-class.md) v režimu vydání. V případě jiných chyb runtime tato metoda uplatňuje v režimu ladění a vyvolává výjimku odvozenou z třídy [CException.](../../mfc/reference/cexception-class.md)

Tato metoda ovlivňuje stav nabídek v aplikacích napsaných pro systém Windows Vista a novější.

## <a name="cframewndsetmessagetext"></a><a name="setmessagetext"></a>CFrameWnd::SetMessageText

Volání této funkce umístit řetězec v podokně stavového řádku, který má ID 0.

```
void SetMessageText(LPCTSTR lpszText);
void SetMessageText(UINT nID);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
Odkazuje na řetězec, který má být umístěn na stavovém řádku.

*Nid*<br/>
ID řetězce, který má být umístěn na stavovém řádku.

### <a name="remarks"></a>Poznámky

Obvykle se jedná o podokno stavového řádku zcela vlevo a nejdéle.

## <a name="cframewndsetprogressbarposition"></a><a name="setprogressbarposition"></a>CFrameWnd::SetProgressBarPosition

Nastaví aktuální pozici indikátoru průběhu systému Windows 7 zobrazeného na hlavním panelu.

```
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>Parametry

*nProgressPos*<br/>
Určuje polohu, kterou chcete nastavit. Musí být v rozsahu `SetProgressBarRange`nastaveném .

### <a name="remarks"></a>Poznámky

## <a name="cframewndsetprogressbarrange"></a><a name="setprogressbarrange"></a>CFrameWnd::SetProgressBarRange

Nastaví rozsah indikátoru průběhu systému Windows 7 zobrazený na hlavním panelu.

```
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>Parametry

*nRangeMin*<br/>
Minimální hodnota.

*nRozsahMax*<br/>
Maximální hodnota.

### <a name="remarks"></a>Poznámky

## <a name="cframewndsetprogressbarstate"></a><a name="setprogressbarstate"></a>CFrameWnd::SetProgressBarState

Nastaví typ a stav indikátoru průběhu zobrazeného na tlačítku hlavního panelu.

```
void SetProgressBarState(TBPFLAG tbpFlags);
```

### <a name="parameters"></a>Parametry

*tbpFlags*<br/>
Příznaky, které řídí aktuální stav tlačítka průběhu. Zadejte pouze jeden z následujících příznaků, protože se vzájemně vylučují všechny stavy: TBPF_NOPROGRESS, TBPF_INDETERMINATE, TBPF_NORMAL, TBPF_ERROR, TBPF_PAUSED.

### <a name="remarks"></a>Poznámky

## <a name="cframewndsettaskbaroverlayicon"></a><a name="settaskbaroverlayicon"></a>CFrameWnd::SetTaskbarOverlayIcon

Přetíženo. Použije překrytí na tlačítko na hlavním panelu, které označuje stav aplikace nebo upozorní uživatele.

```
BOOL SetTaskbarOverlayIcon(
    UINT nIDResource,
    LPCTSTR lpcszDescr);

BOOL SetTaskbarOverlayIcon(
    HICON hIcon,
    LPCTSTR lpcszDescr);
```

### <a name="parameters"></a>Parametry

*nIDZdroj*<br/>
Určuje ID prostředku ikony, která má být používána jako překrytí. Podrobnosti naleznete v popisu *funkce hIcon.*

*lpcszDescr*<br/>
Ukazatel na řetězec, který poskytuje alternativní textovou verzi informací přeprostředkovaných překrytím pro účely usnadnění přístupu.

*hIkona*<br/>
Úchyt ikony, která se má použít jako překrytí. Měla by to být malá ikona o rozměrech 16 x 16 pixelů při 96 bodech na palec (dpi). Pokud je na tlačítko hlavního panelu již použita ikona překrytí, bude toto existující překrytí nahrazeno. Tato hodnota může být NULL. Způsob zpracování hodnoty NULL závisí na tom, zda tlačítko na hlavním panelu představuje jedno okno nebo skupinu oken. Je odpovědností volající aplikace k uvolnění *hIcon,* když již není potřeba.

### <a name="return-value"></a>Návratová hodnota

PRAVDA v případě úspěchu; FALSE, pokud je verze operačního systému menší než Windows 7 nebo pokud dojde k chybě nastavení ikony.

### <a name="remarks"></a>Poznámky

## <a name="cframewndsettitle"></a><a name="settitle"></a>CFrameWnd::SetTitle

Nastaví název objektu okna.

```
void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>Parametry

*lpszNázev*<br/>
Ukazatel na řetězec znaku obsahující název objektu okna.

## <a name="cframewndshowcontrolbar"></a><a name="showcontrolbar"></a>CFrameWnd::Zobrazitkontrolní panel

Volání této členské funkce zobrazí nebo skryje ovládací panel.

```
void ShowControlBar(
    CControlBar* pBar,
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
Ukazatel na ovládací panel, který má být zobrazen nebo skrytý.

*bZobrazit*<br/>
Pokud true, určuje, že ovládací panel má být zobrazen. Pokud false, určuje, že ovládací panel má být skrytý.

*bZpoždění*<br/>
Pokud true, zpoždění zobrazující ovládací panel. Pokud false, okamžitě zobrazte ovládací panel.

## <a name="cframewndshowownedwindows"></a><a name="showownedwindows"></a>CFrameWnd::ShowOwnedWindows

Volání této členské funkce zobrazí všechna okna, `CFrameWnd` která jsou potomky objektu.

```
void ShowOwnedWindows(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bZobrazit*<br/>
Určuje, zda mají být vlastněná okna zobrazena nebo skryta.

## <a name="see-also"></a>Viz také

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Třída CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)<br/>
[Třída CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)<br/>
[Třída CView](../../mfc/reference/cview-class.md)<br/>
[Třída CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[CRuntimeClass – struktura](../../mfc/reference/cruntimeclass-structure.md)
