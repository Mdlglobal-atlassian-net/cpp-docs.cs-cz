---
title: CFrameWnd – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 35a3fb35115e1fd86a2ccf168e048a697a17dc01
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33378502"
---
# <a name="cframewnd-class"></a>CFrameWnd – třída
Poskytuje funkci Windows jednotlivý dokument (SDI rozhraní) překryté nebo oken s rámečkem automaticky otevírané okno, společně s členů pro správu okna.  
  
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
|[CFrameWnd::ActivateFrame](#activateframe)|Díky rámečku viditelné a k dispozici pro uživatele.|  
|[CFrameWnd::BeginModalState](#beginmodalstate)|Modální nastaví rámce okna.|  
|[CFrameWnd::Create](#create)|Volání vytvoření a inicializace rámce okna Windows přidružené `CFrameWnd` objektu.|  
|[CFrameWnd::CreateView](#createview)|Vytvoří zobrazení v rámci rámce, který není odvozen od `CView`.|  
|[CFrameWnd::DockControlBar](#dockcontrolbar)|Ukotvené ovládacích pruhů.|  
|[CFrameWnd::EnableDocking](#enabledocking)|Umožňuje ovládacích pruhů chcete ukotvit.|  
|[CFrameWnd::EndModalState](#endmodalstate)|Ukončí modální stavu rámce okna. Umožňuje všechna okna zakázal `BeginModalState`.|  
|[CFrameWnd::FloatControlBar](#floatcontrolbar)|Obtéká ovládacích pruhů.|  
|[CFrameWnd::GetActiveDocument](#getactivedocument)|Vrátí aktivní **CDocument** objektu.|  
|[CFrameWnd::GetActiveFrame](#getactiveframe)|Vrátí aktivní `CFrameWnd` objektu.|  
|[CFrameWnd::GetActiveView](#getactiveview)|Vrátí aktivní `CView` objektu.|  
|[CFrameWnd::GetControlBar](#getcontrolbar)|Načte ovládacích pruhů.|  
|[CFrameWnd::GetDockState](#getdockstate)|Načte stav ukotvení okně s rámečkem.|  
|[CFrameWnd::GetMenuBarState](#getmenubarstate)|Načte stav zobrazení v nabídce v aktuální aplikaci MFC.|  
|[CFrameWnd::GetMenuBarVisibility](#getmenubarvisibility)|Určuje, zda je výchozí chování v nabídce v aktuální aplikaci MFC skrytý nebo viditelný.|  
|[CFrameWnd::GetMessageBar](#getmessagebar)|Vrací ukazatel na stavovém řádku patřící do rámce okna.|  
|[CFrameWnd::GetMessageString](#getmessagestring)|Načte zprávu odpovídající ID příkazu.|  
|[CFrameWnd::GetTitle](#gettitle)|Načte název na související ovládací prvek panelu.|  
|[CFrameWnd::InitialUpdateFrame](#initialupdateframe)|Způsobí, že `OnInitialUpdate` – členská funkce patřící do všech zobrazení v rámci okna, která se má volat.|  
|[CFrameWnd::InModalState](#inmodalstate)|Vrátí hodnotu určující, zda je okně s rámečkem v modální stavu.|  
|[CFrameWnd::IsTracking](#istracking)|Určuje, pokud rozdělovač právě přesouvá.|  
|[CFrameWnd::LoadAccelTable](#loadacceltable)|Chcete-li načíst tabulky akcelerátorů volání.|  
|[CFrameWnd::LoadBarState](#loadbarstate)|Chcete-li obnovit nastavení ovládacího prvku panel volání.|  
|[CFrameWnd::LoadFrame](#loadframe)|Chcete-li vytvořit z informací o prostředku dynamicky okně s rámečkem volání.|  
|[CFrameWnd::NegotiateBorderSpace](#negotiateborderspace)|Vyjedná ohraničení místa v rámci okna.|  
|[CFrameWnd::OnBarCheck](#onbarcheck)|Volá se vždy, když akce se provádí na ovládací prvek panelu.|  
|[CFrameWnd::OnContextHelp](#oncontexthelp)|Zpracovává SHIFT + F1 – Nápověda pro položky na místě.|  
|[CFrameWnd::OnSetPreviewMode](#onsetpreviewmode)|Nastaví oken s rámečkem hlavní aplikace do a z režimu náhledu.|  
|[CFrameWnd::OnUpdateControlBarMenu](#onupdatecontrolbarmenu)|Voláno rámcem při aktualizaci přidružené nabídky.|  
|[CFrameWnd::RecalcLayout](#recalclayout)|Ovládací pruhy z přemístí `CFrameWnd` objektu.|  
|[CFrameWnd::SaveBarState](#savebarstate)|Chcete-li uložit nastavení ovládacího prvku panel volání.|  
|[CFrameWnd::SetActivePreviewView](#setactivepreviewview)|Označí zadané zobrazení jako aktivní zobrazení pro náhled formátováním.|  
|[CFrameWnd::SetActiveView](#setactiveview)|Nastaví aktivní `CView` objektu.|  
|[CFrameWnd::SetDockState](#setdockstate)|Volání na ukotvení okně s rámečkem v hlavním okně.|  
|[CFrameWnd::SetMenuBarState](#setmenubarstate)|Nastaví stav zobrazení v nabídce v aktuální aplikaci MFC skrytý nebo zobrazit.|  
|[CFrameWnd::SetMenuBarVisibility](#setmenubarvisibility)|Nastaví výchozí chování v nabídce v aktuální aplikaci MFC být skrytý nebo viditelný.|  
|[CFrameWnd::SetMessageText](#setmessagetext)|Nastaví text standardní stavového řádku.|  
|[CFrameWnd::SetProgressBarPosition](#setprogressbarposition)|Nastaví aktuální pozici pro Windows 7 indikátor průběhu zobrazí na hlavním panelu.|  
|[CFrameWnd::SetProgressBarRange](#setprogressbarrange)|Nastaví rozsah pro Windows 7 indikátor průběhu zobrazí na hlavním panelu.|  
|[CFrameWnd::SetProgressBarState](#setprogressbarstate)|Nastaví typ a stav indikátoru průběhu zobrazené na tlačítka na hlavním panelu.|  
|[CFrameWnd::SetTaskbarOverlayIcon](#settaskbaroverlayicon)|Přetíženo. Překrytí se vztahuje na příslušné tlačítko panelu určete stav aplikace nebo oznámení pro uživatele.|  
|[CFrameWnd::SetTitle](#settitle)|Nastaví název na související ovládací prvek panelu.|  
|[CFrameWnd::ShowControlBar](#showcontrolbar)|Chcete-li zobrazit ovládací prvek panel volání.|  
|[CFrameWnd::ShowOwnedWindows](#showownedwindows)|Zobrazí všechny systémy windows, které jsou následníky `CFrameWnd` objektu.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CFrameWnd::OnCreateClient](#oncreateclient)|Vytvoří okno klienta pro rámečku.|  
|[CFrameWnd::OnHideMenuBar](#onhidemenubar)|Voláno před provedením v nabídce v aktuální aplikaci MFC skryt.|  
|[CFrameWnd::OnShowMenuBar](#onshowmenubar)|Volá se před zobrazením v nabídce v aktuální aplikaci MFC je.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CFrameWnd::m_bAutoMenuEnable](#m_bautomenuenable)|Ovládací prvky automatické povolení a zakázání funkce pro položky nabídky.|  
|[CFrameWnd::rectDefault](#rectdefault)|Předat to statické `CRect` jako parametr při vytváření `CFrameWnd` objekt, který chcete systému Windows vyberte počáteční velikost a umístění okna povolit.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud chcete vytvořit užitečné rámce okna pro vaše aplikace, odvození třídy z `CFrameWnd`. Přidání členské proměnné do odvozené třídy k ukládání dat, které jsou specifické pro vaši aplikaci. Implementace obslužné rutiny zpráv členských funkcí a zprávu mapovat v odvozené třídě k určení, co se stane, když jsou směrované zprávy do okna.  
  
 Existují tři způsoby, jak vytvořit okně s rámečkem:  
  
-   Přímo vytvořit pomocí [vytvořit](#create).  
  
-   Přímo vytvořit pomocí [loadframe –](#loadframe).  
  
-   Nepřímo vytvořte pomocí šablony dokumentu.  
  
 Před voláním buď **vytvořit** nebo `LoadFrame`, je nutné vytvořit objekt oken s rámečkem v haldě pomocí C++ **nové** operátor. Před voláním **vytvořit**, budete taky moct registrovat třídu okno s [afxregisterwndclass –](../../mfc/reference/application-information-and-management.md#afxregisterwndclass) globální funkce nastavit ikonu a třída styly pro rámečku.  
  
 Použití **vytvořit** – členská funkce předat parametry vytvoření rámečku jako okamžitou argumenty.  
  
 `LoadFrame` vyžaduje argumenty méně než **vytvořit**a místo toho načítá většinu jeho výchozí hodnoty z prostředků, včetně titulku rámečku, ikona, tabulka akcelerátoru a nabídky. Chcete-li být přístupné `LoadFrame`, tyto prostředky musí mít stejné ID prostředku (například **IDR_MAINFRAME**).  
  
 Když `CFrameWnd` objekt obsahuje zobrazení a dokumenty, jsou nepřímo vytvořené pomocí rozhraní místo přímo z programátorů. `CDocTemplate` Objekt orchestruje vytvoření rámečku, vytvoření obsahující zobrazení a připojení k zobrazení odpovídající dokumentu. Parametry `CDocTemplate` zadejte konstruktor `CRuntimeClass` tří tříd podílejí (dokumentu, rámečkem a zobrazení). A `CRuntimeClass` objekt používají rozhraní dynamicky vytvořit nové rámce při zadané uživatelem (například pomocí souboru nový příkaz nebo více okno Nový příkaz dokumentu rozhraní (MDI)).  
  
 Odvozené třídy oken s rámečkem z `CFrameWnd` je třeba deklarovat s `DECLARE_DYNCREATE` v pořadí pro výše `RUNTIME_CLASS` mechanismus fungovala správně.  
  
 A `CFrameWnd` obsahuje výchozí implementace provádět následující funkce hlavní okno v typické aplikaci pro Windows:  
  
-   A `CFrameWnd` oken s rámečkem uchovává informace o aktuálně aktivní zobrazení, která je nezávislá aktivní okno Windows nebo aktuální zaměření pro vstup. Při opětovné aktivaci rámečku aktivní zobrazení upozornění voláním `CView::OnActivateView`.  
  
-   Příkaz zprávy a mnoho běžných zprávy oznámení rámce, včetně těch, které provádí `OnSetFocus`, `OnHScroll`, a `OnVScroll` funkce `CWnd`, jsou delegovaní `CFrameWnd` oken s rámečkem na aktuálně aktivní zobrazení.  
  
-   Zobrazit aktuálně aktivní (nebo aktuálně aktivní MDI podřízeného rámce okna v případě MDI rámečkem) můžete určit titulek rámce okna. Tato funkce lze zakázat pomocí vypnutí **fws_addtotitle –** bit stylu rámce okna.  
  
-   A `CFrameWnd` oken s rámečkem spravuje umístění ovládací pruhy, zobrazení a další podřízená okna uvnitř oblasti klienta rámce okna. Okně s rámečkem zajišťuje také doby nečinnosti aktualizace nástrojů a jiných ovládacích pruhů tlačítka. A `CFrameWnd` oken s rámečkem má také výchozí implementace příkazy pro přepnutím zapnout a vypnout na panelu nástrojů a stav.  
  
-   A `CFrameWnd` oken s rámečkem spravuje panelu přejděte z hlavní nabídky. Pokud se zobrazí místní nabídka, okně s rámečkem použije **UPDATE_COMMAND_UI** mechanismus k určení položky nabídky by měl povolit, zakázat nebo zaškrtnuto. Když uživatel vybere položku nabídky, aktualizuje okně s rámečkem na stavovém řádku řetězec zprávy pro tento příkaz.  
  
-   A `CFrameWnd` oken s rámečkem má tabulky akcelerátorů volitelné, který automaticky převádí klávesové zkratky.  
  
-   A `CFrameWnd` oken s rámečkem má ID volitelné nápovědy nastavit s `LoadFrame` používané pro kontextová nápověda. Okně s rámečkem je hlavní orchestrator z semimodální stavy například kontextové nápovědy (SHIFT + F1) a režim náhledu.  
  
-   A `CFrameWnd` oken s rámečkem, otevře se soubor ze souboru Správce přetáhnout v okně s rámečkem. Pokud přípona souboru je zaregistrované a přiřazené k aplikaci, okně s rámečkem odpoví na žádost otevřete dynamická data systému exchange (DDE), ke kterému dochází, když uživatel otevře soubor dat ve Správci souboru nebo když **ShellExecute** Je volána funkce systému Windows.  
  
-   Pokud je okno rámce okna hlavní aplikace (tedy `CWinThread::m_pMainWnd`), když uživatel nezavře aplikaci, okně s rámečkem vyzývá uživatele k uložit všechny upravené dokumenty (pro `OnClose` a `OnQueryEndSession`).  
  
-   Pokud je okno rámce okna hlavní aplikace, je okně s rámečkem kontext pro spuštění WinHelp. Zavřete okno rámce WINHELP vypne. Soubor EXE, pokud byl spuštěn pro nápovědu pro tuto aplikaci.  
  
 Nepoužívejte C++ **odstranit** operátor zrušení rámce okna. Místo nich se používá `CWnd::DestroyWindow`. `CFrameWnd` Implementace `PostNcDestroy` se odstranit objekt C++, když okno zničena. Když uživatel nezavře okno rámce, výchozí `OnClose` bude volat obslužná rutina `DestroyWindow`.  
  
 Další informace o `CFrameWnd`, najdete v části [okna s rámečkem](../../mfc/frame-windows.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CFrameWnd`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="activateframe"></a>  CFrameWnd::ActivateFrame  
 Volání této funkce člena pro aktivaci a obnoví rámce okna tak, aby se viditelné a k dispozici pro uživatele.  
  
```  
virtual void ActivateFrame(int nCmdShow = -1);
```  
  
### <a name="parameters"></a>Parametry  
 `nCmdShow`  
 Určuje parametr předat [CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow). Ve výchozím nastavení je rámečku vidět a správně obnovit.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen je obvykle volána po události bez uživatelského rozhraní například DDE, OLE nebo další událost, která může zobrazovat okně s rámečkem nebo jeho obsah pro uživatele.  
  
 Výchozí implementace aktivuje rámečku, zobrazí se na začátek pořadí a, v případě potřeby provede stejný postup pro aplikace hlavního rámce okna.  
  
 Chcete-li změnit způsob aktivace rámeček funkci člena přepište. Například můžete vynutit podřízených oken MDI chcete maximalizovat. Přidejte příslušné funkce a pak volat základní třída verzi s explicitního `nCmdShow`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#1](../../mfc/reference/codesnippet/cpp/cframewnd-class_1.cpp)]  
  
##  <a name="beginmodalstate"></a>  CFrameWnd::BeginModalState  
 Volání této funkce člen vytvoření modální okna rámce.  
  
```  
virtual void BeginModalState();
```  
  
##  <a name="cframewnd"></a>  CFrameWnd::CFrameWnd  
 Vytvoří `CFrameWnd` objektu, ale nevytvoří viditelné rámce okna.  
  
```  
CFrameWnd();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání **vytvořit** vytvořit okno viditelné.  
  
##  <a name="create"></a>  CFrameWnd::Create  
 Volání vytvoření a inicializace rámce okna Windows přidružené `CFrameWnd` objektu.  
  
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
 `lpszClassName`  
 Bodů na řetězec znaků ukončené hodnotou null, který názvy třídy Windows. Název třídy může být jakýkoli název zaregistrována `AfxRegisterWndClass` globální funkce nebo **RegisterClass** funkce systému Windows. Pokud **NULL**, používá předdefinovanou výchozí `CFrameWnd` atributy.  
  
 `lpszWindowName`  
 Odkazuje na řetězec znaků ukončené hodnotou null, který představuje název okna. Používá jako text záhlaví.  
  
 `dwStyle`  
 Určuje okno [styl](../../mfc/reference/styles-used-by-mfc.md#window-styles) atributy. Zahrnout **fws_addtotitle –** styl, pokud chcete, aby na záhlaví automaticky zobrazovaný název dokumentu v okně.  
  
 `rect`  
 Určuje velikost a umístění okna. `rectDefault` Systému Windows zadejte velikost a umístění nového okna umožní hodnotu.  
  
 `pParentWnd`  
 Určuje nadřazeného okna rámce okna. Tento parametr by měl být **NULL** pro okna s rámečkem nejvyšší úrovně.  
  
 *lpszMenuName*  
 Určuje název prostředku nabídky pro použití s okna. Použití **MAKEINTRESOURCE** Pokud v nabídce má celé číslo ID místo řetězec. Tento parametr může být **NULL**.  
  
 `dwExStyle`  
 Určuje okno Rozšířené [styl](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) atributy.  
  
 `pContext`  
 Určuje ukazatel [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) struktury. Tento parametr může být **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěšného; inicializace jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Vytvořit `CFrameWnd` objektu ve dvou krocích. Nejprve vyvolat konstruktor, který vytvoří `CFrameWnd` objektu a pak zavolají **vytvořit**, který vytvoří rámce okna Windows a připojí jej k `CFrameWnd` objektu. **Vytvoření** inicializuje okna na název třídy a název časového období a zaregistruje výchozí hodnoty pro svou styl, nadřazené a přidružené nabídky.  
  
 Použití `LoadFrame` místo **vytvořit** načíst okně s rámečkem z prostředku místo zadání její argumenty.  
  
##  <a name="createview"></a>  CFrameWnd::CreateView  
 Volání `CreateView` vytvoření zobrazení v rámci.  
  
```  
CWnd* CreateView(
    CCreateContext* pContext,  
    UINT nID = AFX_IDW_PANE_FIRST);
```  
  
### <a name="parameters"></a>Parametry  
 `pContext`  
 Určuje typ zobrazení a dokumentu.  
  
 `nID`  
 Číslo ID zobrazení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na `CWnd` objekt, je-li úspěšná, jinak hodnota **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce člen vytvořit "zobrazení", které nejsou `CView`-odvozené v rámci. Po volání `CreateView`, musíte ručně nastavit zobrazení na aktivní a nastavte ji viditelné; tyto úlohy nejsou automaticky provádí `CreateView`.  
  
##  <a name="dockcontrolbar"></a>  CFrameWnd::DockControlBar  
 Způsobí, že ovládacích pruhů pro ukotvit rámce okna.  
  
```  
void DockControlBar(
    CControlBar* pBar,  
    UINT nDockBarID = 0,  
    LPCRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pBar`  
 Odkazuje na panelu řízení ukotvit.  
  
 `nDockBarID`  
 Určuje, které strany rámce okna vzít v úvahu pro ukotvení. Může být 0, nebo jednu nebo více následujících akcí:  
  
- `AFX_IDW_DOCKBAR_TOP` Ukotvení do horní části okna rámce.  
  
- **AFX_IDW_DOCKBAR_BOTTOM** ukotvení na dolní straně rámce okna.  
  
- `AFX_IDW_DOCKBAR_LEFT` Ukotvení na levé straně okna rámce.  
  
- `AFX_IDW_DOCKBAR_RIGHT` Ukotvení na pravé straně rámce okna.  
  
 Pokud je 0, ovládacích pruhů lze ukotvit na žádné straně povolené pro ukotvení v rámci okna cílové.  
  
 `lpRect`  
 Určuje, v souřadnice obrazovky, kde budou v oblasti nonclient rámce okna cílové ukotveny ovládacích pruhů.  
  
### <a name="remarks"></a>Poznámky  
 Ovládací prvek panel bude ukotven na jednu z postranní rámce okna zadaný ve volání do obou [CControlBar::EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking) a [CFrameWnd::EnableDocking](#enabledocking). Na straně vybrali je dáno `nDockBarID`.  
  
##  <a name="enabledocking"></a>  CFrameWnd::EnableDocking  
 Volejte tuto funkci povolit lze ukotvit ovládací pruhy v okně s rámečkem.  
  
```  
void EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>Parametry  
 `dwDockStyle`  
 Určuje, které strany rámce okna může sloužit jako lokality pro ovládací pruhy ukotvení. Může být jeden nebo více následujících akcí:  
  
- `CBRS_ALIGN_TOP` Umožňuje ukotvení v horní části oblasti klienta.  
  
- `CBRS_ALIGN_BOTTOM` Umožňuje ukotvení v dolní části klientské oblasti.  
  
- `CBRS_ALIGN_LEFT` Umožňuje ukotvení na levé straně klienta.  
  
- `CBRS_ALIGN_RIGHT` Umožňuje ukotvení na pravé straně klienta.  
  
- `CBRS_ALIGN_ANY` Umožňuje ukotvení na žádné straně klientské oblasti.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení, budou ovládací pruhy ukotveny na straně okna rámce v následujícím pořadí: nahoře, dole, vlevo, vpravo.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CToolBar::Create](../../mfc/reference/ctoolbar-class.md#create).  
  
##  <a name="endmodalstate"></a>  CFrameWnd::EndModalState  
 Volání této funkce člen změna okně s rámečkem modální na nemodální.  
  
```  
virtual void EndModalState();
```  
  
### <a name="remarks"></a>Poznámky  
 `EndModalState` umožňuje všechna okna zakázal [BeginModalState](#beginmodalstate).  
  
##  <a name="floatcontrolbar"></a>  CFrameWnd::FloatControlBar  
 Volání této funkce způsobí ovládacích pruhů k nebyla ukotvena rámce okna.  
  
```  
void FloatControlBar(
    CControlBar* pBar,  
    CPoint point,  
    DWORD dwStyle = CBRS_ALIGN_TOP);
```  
  
### <a name="parameters"></a>Parametry  
 `pBar`  
 Odkazuje na panelu řízení obtékání.  
  
 `point`  
 Umístění, v souřadnice obrazovky, kde budou umístěné levém horním rohu na ovládací prvek panelu.  
  
 `dwStyle`  
 Určuje, jestli chcete-li zarovnat panelu ovládacího prvku v jeho nové oken s rámečkem vodorovně nebo svisle. Může být některého z následujících akcí:  
  
- `CBRS_ALIGN_TOP` Orientuje ovládacích pruhů svisle.  
  
- `CBRS_ALIGN_BOTTOM` Orientuje ovládacích pruhů svisle.  
  
- `CBRS_ALIGN_LEFT` Seznámí ovládacích pruhů vodorovně.  
  
- `CBRS_ALIGN_RIGHT` Seznámí ovládacích pruhů vodorovně.  
  
 Pokud styly jsou předány zadání vodorovného a svislého orientaci, panelu nástrojů bude orientované vodorovně.  
  
### <a name="remarks"></a>Poznámky  
 Obvykle to se provádí při spuštění aplikace při programu je obnovení nastavení z předchozí zpracování.  
  
 Tato funkce je volána rozhraním framework, když uživatel způsobí operace odstranění uvolněním levé tlačítko myši při přetahování ovládacích pruhů přes umístění, které není k dispozici pro ukotvení.  
  
##  <a name="getactivedocument"></a>  CFrameWnd::GetActiveDocument  
 Volání této funkce člen k získání ukazatele na aktuální **CDocument** připojené k aktuální aktivní zobrazení.  
  
```  
virtual CDocument* GetActiveDocument();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na aktuální [CDocument](../../mfc/reference/cdocument-class.md). Pokud není žádná aktuální dokumentu, vrátí **NULL**.  
  
##  <a name="getactiveframe"></a>  CFrameWnd::GetActiveFrame  
 Volání této funkce člen získat rozhraní (MDI) dokumentu více podřízeného okna rámce okna MDI ukazatel na aktivní.  
  
```  
virtual CFrameWnd* GetActiveFrame();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na aktivní podřízeného okna MDI. Pokud aplikace je aplikace SDI nebo rámce okna MDI má žádné aktivní dokument implicitní **to** ukazatel bude vrácen.  
  
### <a name="remarks"></a>Poznámky  
 Pokud není žádná aktivní podřízeného MDI nebo je aplikace jedním dokumentem (SDI rozhraní), implicitní **to** ukazatel je vrácen.  
  
##  <a name="getactiveview"></a>  CFrameWnd::GetActiveView  
 Volání této funkce člen k získání ukazatele na aktivní zobrazení (pokud existuje) připojené k okně s rámečkem ( `CFrameWnd`).  
  
```  
CView* GetActiveView() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na aktuální [CView](../../mfc/reference/cview-class.md). Pokud není žádná aktuální zobrazení, vrátí **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Funkce vrátí hodnotu **NULL** při volání pro hlavního rámce okna MDI ( `CMDIFrameWnd`). V aplikaci MDI hlavního rámce okna MDI nemá zobrazení s ním spojená. Místo toho každé jednotlivé podřízeného okna ( `CMDIChildWnd`) obsahuje jeden nebo více přidružené zobrazení. Aktivní zobrazení v aplikaci MDI je možné získat nejprve hledání active podřízeného okna MDI a vyhledáním aktivní zobrazení pro toto okno podřízené. Aktivní podřízeného okna MDI naleznete voláním funkce `MDIGetActive` nebo **getactiveframe –** jak je ukázáno v následujícím:  
  
 [!code-cpp[NVC_MFCWindowing#2](../../mfc/reference/codesnippet/cpp/cframewnd-class_2.cpp)]  
  
##  <a name="getcontrolbar"></a>  CFrameWnd::GetControlBar  
 Volání `GetControlBar` k získání přístupu k panelu Ovládací prvek, který je přidružen ID.  
  
```  
CControlBar* GetControlBar(UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Číslo ID ovládacích pruhů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na ovládací prvek panel, který je přidružen ID.  
  
### <a name="remarks"></a>Poznámky  
 `nID` Parametr odkazuje na jedinečný identifikátor předaný **vytvořit** metoda ovládacích pruhů. Další informace o ovládací pruhy, naleznete v tématu s názvem [ovládací pruhy](../../mfc/control-bars.md).  
  
 `GetControlBar` vrátí ovládací prvek panelu, i pokud je číslo s plovoucí čárkou a proto není aktuálně podřízeného okna rámečku.  
  
##  <a name="getdockstate"></a>  CFrameWnd::GetDockState  
 Volání této funkce člen ukládat informace o rámce okna Ovládací pruhy ve stavu `CDockState` objektu.  
  
```  
void GetDockState(CDockState& state) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `state`  
 Obsahuje aktuální stav rámce okna Ovládací pruhy po návratu.  
  
### <a name="remarks"></a>Poznámky  
 Poté můžete napsat obsah `CDockState` úložiště pomocí `CDockState::SaveState` nebo `Serialize`. Pokud chcete později obnovit do předchozího stavu ovládací pruhy, načtení stavu se `CDockState::LoadState` nebo `Serialize`, pak zavolají `SetDockState` použít rámce okna Ovládací pruhy předchozího stavu.  
  
##  <a name="getmenubarstate"></a>  CFrameWnd::GetMenuBarState  
 Načte stav zobrazení v nabídce v aktuální aplikaci MFC.  
  
```  
virtual DWORD GetMenuBarState();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Návratová hodnota může mít následující hodnoty:  
  
-   AFX_MBS_VISIBLE (0x01) - je zobrazen v nabídce.  
  
-   AFX_MBS_HIDDEN (0x02) - je skryté v nabídce.  
  
### <a name="remarks"></a>Poznámky  
 Pokud dojde k chybě za běhu, tato metoda vyhodnotí v režimu ladění a vyvolá výjimku odvozené z [CException](../../mfc/reference/cexception-class.md) třídy.  
  
##  <a name="getmenubarvisibility"></a>  CFrameWnd::GetMenuBarVisibility  
 Určuje, zda je výchozí stav nabídky v aktuální aplikaci MFC skrytý nebo viditelný.  
  
```  
virtual DWORD CFrameWnd::GetMenuBarVisibility();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí jednu z následujících hodnot:  
  
-   AFX_MBV_KEEPVISIBLE (0x01) - nabídce se zobrazí na všech časy a ve výchozím nastavení není dosud aktivní.  
  
-   AFX_MBV_DISPLAYONFOCUS (0x02) – ve výchozím nastavení je skryté v nabídce. Pokud je skryté v nabídce, stiskněte klávesu ALT pro zobrazení nabídky a pojmenujte ho fokus. Pokud se zobrazí v nabídce, stisknutím klávesy ALT nebo ESC ho chcete skrýt.  
  
-   AFX_MBV_ DISPLAYONFOCUS (0x02) &#124; AFX_MBV_DISPLAYONF10 (0x04) (bitovou kombinaci (nebo)) – ve výchozím nastavení je skryté v nabídce. Pokud je skryté v nabídce, stiskněte klávesu F10 pro zobrazení nabídky a pojmenujte ho fokus. Pokud se zobrazí v nabídce, stisknutím klávesy F10 Přepnout vstup zapnout nebo vypnout v nabídce. V nabídce se nezobrazí, dokud stisknutím klávesy ALT nebo ESC ho chcete skrýt.  
  
### <a name="remarks"></a>Poznámky  
 Pokud dojde k chybě za běhu, tato metoda vyhodnotí v režimu ladění a vyvolá výjimku odvozené z [CException](../../mfc/reference/cexception-class.md) třídy.  
  
##  <a name="getmessagebar"></a>  CFrameWnd::GetMessageBar  
 Volání této funkce člen k získání ukazatele na stavovém řádku.  
  
```  
virtual CWnd* GetMessageBar();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na stavového řádku okna.  
  
##  <a name="getmessagestring"></a>  CFrameWnd::GetMessageString  
 Přepsání této funkce zajistit vlastní řetězce pro ID příkazů.  
  
```  
virtual void GetMessageString(
    UINT nID,  
    CString& rMessage) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 ID prostředku požadované zprávy.  
  
 `rMessage`  
 `CString` objekt, do níž umístíte zprávy.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace jednoduše načte řetězec určený `nID` ze zdrojového souboru. Tato funkce je volána rámcem, pokud řetězec zprávy ve stavovém řádku je nutné aktualizovat.  
  
##  <a name="gettitle"></a>  CFrameWnd::GetTitle  
 Načte název objektu okna.  
  
```  
CString GetTitle() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt obsahující aktuální název objektu okna.  
  
##  <a name="initialupdateframe"></a>  CFrameWnd::InitialUpdateFrame  
 Volání **IntitialUpdateFrame** po vytvoření nového rámečku s **vytvořit**.  
  
```  
void InitialUpdateFrame(
    CDocument* pDoc,  
    BOOL bMakeVisible);
```  
  
### <a name="parameters"></a>Parametry  
 `pDoc`  
 Body v dokumentu, ke kterému je přidružené rámce okna. Může být **NULL**.  
  
 `bMakeVisible`  
 Pokud **TRUE**, označuje, že by měl rámečku se zobrazí a aktivní. Pokud **FALSE**, žádné potomky jsou dostupná.  
  
### <a name="remarks"></a>Poznámky  
 To způsobí, že všechna zobrazení v okně rámce pro příjem jejich `OnInitialUpdate` volání.  
  
 Navíc pokud nebyl k dispozici dříve aktivní zobrazení, primární zobrazení okna rámce přišla aktivní. Primární zobrazení je zobrazení s ID podřízeného z **AFX_IDW_PANE_FIRST**. Nakonec se provádí okně s rámečkem viditelné pokud `bMakeVisible` nenulový. Pokud `bMakeVisible` je 0, aktuální fokus a stav viditelnosti rámce okna zůstane beze změny. Není nutné volat tuto funkci při pomocí implementace rozhraní framework nový soubor a soubor otevřít.  
  
##  <a name="inmodalstate"></a>  CFrameWnd::InModalState  
 Volání této funkce člen k zkontrolujte, jestli je modální nebo nemodálním okně s rámečkem.  
  
```  
BOOL InModalState() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud ano, nenulové hodnoty jinak 0.  
  
##  <a name="istracking"></a>  CFrameWnd::IsTracking  
 Volání této funkce člen k určení, pokud tento panel v okně právě přesouvá.  
  
```  
BOOL IsTracking() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud operace rozdělovače probíhá; jinak 0.  
  
##  <a name="loadacceltable"></a>  CFrameWnd::LoadAccelTable  
 Chcete-li načíst tabulku zadaný akcelerátoru volání.  
  
```  
BOOL LoadAccelTable(LPCTSTR lpszResourceName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszResourceName`  
 Určuje název prostředku akcelerátoru. Použití **MAKEINTRESOURCE** Pokud se identifikuje prostředek s ID celé číslo.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud tabulka akcelerátoru byl úspěšně načten; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Najednou můžete načíst jenom jedna tabulka.  
  
 Tabulky akcelerátoru načíst z prostředků se uvolní automaticky, když se aplikace ukončí.  
  
 Když zavoláte `LoadFrame` k vytvoření rámce okna, rozhraní načte tabulky akcelerátorů společně s ikona nabídky a prostředky a následných volání funkce tento člen je pak zbytečné.  
  
##  <a name="loadbarstate"></a>  CFrameWnd::LoadBarState  
 Volání této funkce můžete obnovit nastavení jednotlivých ovládacích pruhů vlastníkem rámce okna.  
  
```  
void LoadBarState(LPCTSTR lpszProfileName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszProfileName`  
 Název oddílu v souboru inicializace (INI) nebo klíč v registru systému Windows se uloží informace o stavu.  
  
### <a name="remarks"></a>Poznámky  
 Informace o obnovení zahrnuje viditelnost, vodorovně nebo svisle orientaci, ukotvení stav a pozice ovládacích pruhů.  
  
 Nastavení, které chcete obnovit, musí být zapsané do registru před voláním `LoadBarState`. Zápis informací do registru voláním [CWinApp::SetRegistryKey](../../mfc/reference/cwinapp-class.md#setregistrykey). Zapsat informace o souboru INI voláním [SaveBarState](#savebarstate).  
  
##  <a name="loadframe"></a>  CFrameWnd::LoadFrame  
 Chcete-li vytvořit z informací o prostředku dynamicky okně s rámečkem volání.  
  
```  
virtual BOOL LoadFrame(
    UINT nIDResource,  
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,  
    CWnd* pParentWnd = NULL,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDResource`  
 ID sdílené prostředky, které jsou přidružené k rámce okna.  
  
 *dwDefaultStyle*  
 Rámečku [styl](../../mfc/reference/styles-used-by-mfc.md#window-styles). Zahrnout **fws_addtotitle –** styl, pokud chcete, aby na záhlaví automaticky zobrazovaný název dokumentu v okně.  
  
 `pParentWnd`  
 Ukazatel na hodnotu parent rámečku.  
  
 `pContext`  
 Ukazatel [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) struktury. Tento parametr může být **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Vytvořit `CFrameWnd` objektu ve dvou krocích. Nejprve vyvolat konstruktor, který vytvoří `CFrameWnd` objektu a pak zavolají `LoadFrame`, který načte oken s rámečkem Windows a přidružené prostředky a připojí okně s rámečkem na `CFrameWnd` objektu. `nIDResource` Parametr určuje, v nabídce, tabulky akcelerátorů, ikonu a řetězec prostředku záhlaví okna rámce.  
  
 Použití **vytvořit** – členská funkce místo `LoadFrame` Pokud chcete zadat všechny parametry vytvoření rámce okna.  
  
 Volání framework `LoadFrame` při vytvoří okně s rámečkem pomocí objektu šablony dokumentu.  
  
 Rozhraní používá `pContext` argument určete objekty, které k připojení do okna rámce, včetně všech obsažené objekty zobrazení. Můžete nastavit `pContext` argument **NULL** při volání `LoadFrame`.  
  
##  <a name="m_bautomenuenable"></a>  CFrameWnd::m_bAutoMenuEnable  
 Když je tento člen dat povolené (což je výchozí nastavení), nabídky položek, které nemají `ON_UPDATE_COMMAND_UI` nebo `ON_COMMAND` obslužné rutiny se automaticky zakáže při vrátí uživatele nabídku.  
  
```  
BOOL m_bAutoMenuEnable;  
```  
  
### <a name="remarks"></a>Poznámky  
 Položky nabídky, které mají `ON_COMMAND` obslužná rutina, ale ne `ON_UPDATE_COMMAND_UI` automaticky povolí obslužné rutiny.  
  
 Pokud je tento člen data nastavená, položky nabídky jsou povolené automaticky stejným způsobem, že jsou povoleny tlačítka panelu nástrojů.  
  
> [!NOTE]
> `m_bAutoMenuEnable` nemá žádný vliv na nabídek na nejvyšší úrovni.  
  
 Tento člen dat zjednodušuje implementaci volitelné příkazy na základě aktuálního výběru a snižuje nutnost zápisu `ON_UPDATE_COMMAND_UI` obslužné rutiny pro povolení a zákaz položek nabídky.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#3](../../mfc/reference/codesnippet/cpp/cframewnd-class_3.cpp)]  
  
##  <a name="negotiateborderspace"></a>  CFrameWnd::NegotiateBorderSpace  
 Volání této funkce člena pro vyjednávání ohraničení místa v okně s rámečkem během aktivace inplace OLE.  
  
```  
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,  
    LPRECT lpRectBorder);
```  
  
### <a name="parameters"></a>Parametry  
 *nBorderCmd*  
 Obsahuje jeden z následujících hodnot z **výčtu BorderCmd**:  
  
- **borderGet** = 1  
  
- **borderRequest** = 2  
  
- **borderSet** = 3  
  
 `lpRectBorder`  
 Ukazatel na [Rect –](../../mfc/reference/rect-structure1.md) struktura nebo [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt, který určuje souřadnice ohraničení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Funkce člena **CFrameWnd** implementace OLE ohraničení místo vyjednávání.  
  
##  <a name="onbarcheck"></a>  CFrameWnd::OnBarCheck  
 Volá se vždy, když akce se provádí na ovládací prvek panelu.  
  
```  
afx_msg BOOL OnBarCheck(UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 ID ovládacího panelu se zobrazí.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud existovaly ovládacích pruhů; jinak 0.  
  
##  <a name="oncontexthelp"></a>  CFrameWnd::OnContextHelp  
 Zpracovává SHIFT + F1 – Nápověda pro položky na místě.  
  
```  
afx_msg void OnContextHelp();
```  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li povolit Kontextová nápověda, je nutné přidat  
  
 [!code-cpp[NVC_MFCDocViewSDI#16](../../mfc/codesnippet/cpp/cframewnd-class_4.cpp)]  
  
 příkaz k vaší `CFrameWnd` třídy mapy zpráv a také přidat položku tabulky akcelerátorů obvykle SHIFT + F1, chcete-li povolit tuto funkci člen.  
  
 Pokud je vaše aplikace OLE kontejner, `OnContextHelp` umístí všechny položky na místě, které jsou obsažené v objektu rámce okna do režimu nápovědy. Změní na šipka a otazník a uživatele můžete přesunutí ukazatele myši a stiskněte klávesu levé tlačítko myši a vyberte dialogové okno, oken, nabídek nebo příkazového tlačítka. Tato funkce člen volání funkce systému Windows `WinHelp` s kontextu nápovědy objekt pod kurzor.  
  
##  <a name="oncreateclient"></a>  CFrameWnd::OnCreateClient  
 Voláno rámcem během provádění `OnCreate`.  
  
```  
virtual BOOL OnCreateClient(
    LPCREATESTRUCT lpcs,  
    CCreateContext* pContext);
```  
  
### <a name="parameters"></a>Parametry  
 `lpcs`  
 Ukazatel na Windows [createstruct –](../../mfc/reference/createstruct-structure.md) struktura.  
  
 `pContext`  
 Ukazatel [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) struktury.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Nikdy volání této funkce.  
  
 Výchozí implementace této funkce vytvoří `CView` objekt z informací uvedených v `pContext`, pokud je to možné.  
  
 Přepsání této funkci můžete přepsat hodnoty předané `CCreateContext` objektu nebo chcete-li změnit jsou způsob ovládacích prvků v hlavní klientské oblasti okně s rámečkem vytvořené. `CCreateContext` Členy můžete přepsat jsou popsané v [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) třídy.  
  
> [!NOTE]
>  Nepřepisovat existující hodnoty předané `CREATESTRUCT` struktura. Jsou pouze informativní. Pokud chcete přepsat obdélníku počáteční okna, například přepsání `CWnd` – členská funkce [PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow).  
  
##  <a name="onhidemenubar"></a>  CFrameWnd::OnHideMenuBar  
 Tato funkce je volána, pokud je systém Chystáte se skrýt panelu nabídek v aktuální aplikaci MFC.  
  
```  
virtual void OnHideMenuBar();
```  
  
### <a name="remarks"></a>Poznámky  
 Tuto obslužnou rutinu události umožňuje aplikaci k provedení vlastní akce, pokud je systém Chystáte se skrýt v nabídce. V nabídce nemohou zabránit skryté, ale můžete například volat jiné metody načtěte styl nabídky nebo stavu.  
  
##  <a name="onsetpreviewmode"></a>  CFrameWnd::OnSetPreviewMode  
 Volání této funkce člen nastavit oken s rámečkem hlavní aplikace do a z režimu náhledu.  
  
```  
virtual void OnSetPreviewMode(
    BOOL bPreview,  
    CPrintPreviewState* pState);
```  
  
### <a name="parameters"></a>Parametry  
 *bPreview*  
 Určuje, zda se má umístit aplikace v režimu náhledu. Nastavte na **TRUE** umístit v náhledu tisku **FALSE** režim náhledu zrušit.  
  
 `pState`  
 Ukazatel **CPrintPreviewState** struktury.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace zakáže všechny standardní panely nástrojů a skryje klienta hlavní okno a v hlavní nabídce. Okna s rámečkem MDI se změní do okna s rámečkem dočasné SDI.  
  
 Chcete-li přizpůsobit skrytí a zobrazení ovládacích pruhů a dalšími částmi rámce okna během náhledu tisku funkci člena přepište. Volejte základní třída implementaci z v rámci přepsané verze.  
  
##  <a name="onshowmenubar"></a>  CFrameWnd::OnShowMenuBar  
 Tato funkce je volána, pokud je systém se zobrazí na panelu nabídek v aktuální aplikaci MFC.  
  
```  
virtual void OnShowMenuBar();
```  
  
### <a name="remarks"></a>Poznámky  
 Tuto obslužnou rutinu události umožňuje aplikaci k provedení vlastní akce v nabídce se zobrazí při. V nabídce nelze zabránění zobrazení, ale můžete například volat jiné metody načtěte styl nabídky nebo stavu.  
  
##  <a name="onupdatecontrolbarmenu"></a>  CFrameWnd::OnUpdateControlBarMenu  
 Voláno rámcem při aktualizaci přidružené nabídky.  
  
```  
afx_msg void OnUpdateControlBarMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Parametry  
 `pCmdUI`  
 Ukazatel [CCmdUI](../../mfc/reference/ccmdui-class.md) objekt reprezentující v nabídce, která vygenerovala příkaz update. Volání obslužné rutiny aktualizace [povolit](../../mfc/reference/ccmdui-class.md#enable) členské funkce `CCmdUI` objektu prostřednictvím `pCmdUI` aktualizace uživatelského rozhraní.  
  
##  <a name="recalclayout"></a>  CFrameWnd::RecalcLayout  
 Voláno rámcem, když jsou standardní ovládací pruhy zapnout nebo vypnout, nebo při změně velikosti rámce okna.  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bNotify`  
 Určuje, zda aktivní položky na místě rámce okna obdrží upozornění na změnu rozložení. Pokud **TRUE**, položka je oznámený; jinak hodnota **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace této funkce člen volá `CWnd` – členská funkce `RepositionBars` aby přemístil ovládací pruhy v rámečku stejně jako v okně Hlavní klienta (obvykle `CView` nebo **MDICLIENT**) .  
  
 Člen funkci řídit vzhled a chování ovládací pruhy po změně rozložení rámce okna přepište. Je třeba volejte, když ovládací pruhy vypnutí a zapnutí nebo přidejte další ovládací prvek panelu.  
  
##  <a name="rectdefault"></a>  CFrameWnd::rectDefault  
 Předat to statické `CRect` jako parametr při vytváření a údržbu za účelem systému Windows vyberte počáteční velikost a umístění okna povolit.  
  
```  
static AFX_DATA const CRect rectDefault;  
```  
  
##  <a name="savebarstate"></a>  CFrameWnd::SaveBarState  
 Volání této funkce k uložení informací o jednotlivých ovládacích pruhů vlastníkem rámce okna.  
  
```  
void SaveBarState(LPCTSTR lpszProfileName) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lpszProfileName`  
 Název oddílu v inicializační soubor nebo klíč v registru systému Windows se uloží informace o stavu.  
  
### <a name="remarks"></a>Poznámky  
 Tyto informace lze číst ze souboru pomocí inicializace [LoadBarState](#loadbarstate). Informace uložené zahrnuje viditelnost, vodorovně nebo svisle orientaci, ukotvení stavu a umístění v ovládacím prvku panel.  
  
##  <a name="setactivepreviewview"></a>  CFrameWnd::SetActivePreviewView  
 Označí zadané zobrazení jako aktivní zobrazení pro náhled formátováním.  
  
```  
void SetActivePreviewView(CView* pViewNew);
```  
  
### <a name="parameters"></a>Parametry  
 `pViewNew`  
 Ukazatel na zobrazení chcete aktivovat.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setactiveview"></a>  CFrameWnd::SetActiveView  
 Volání této funkce člen nastavit aktivního zobrazení.  
  
```  
void SetActiveView(
    CView* pViewNew,  
    BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *pViewNew*  
 Určuje ukazatel na [CView](../../mfc/reference/cview-class.md) objekt, nebo **NULL** pro aktivní zobrazení.  
  
 `bNotify`  
 Určuje, zda mají být informování aktivace je zobrazení. Pokud **TRUE**, `OnActivateView` je volána pro nové zobrazení, jinak, pokud **FALSE**, není.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní bude volání této funkce automaticky, když uživatel provede změny zaměřuje na zobrazení v okně s rámečkem. Můžete explicitně volat `SetActiveView` změnit zaměřuje na zadané zobrazení.  
  
##  <a name="setdockstate"></a>  CFrameWnd::SetDockState  
 Volání této funkce člen použít informace o stavu uložené v `CDockState` objekt, který chcete ovládací pruhy rámce okna.  
  
```  
void SetDockState(const CDockState& state);
```  
  
### <a name="parameters"></a>Parametry  
 `state`  
 Uložený stav se vztahují na ovládací pruhy rámce okna.  
  
### <a name="remarks"></a>Poznámky  
 K obnovení předchozího stavu ovládací pruhy, můžete načíst uloženému stavu s `CDockState::LoadState` nebo `Serialize`, pak použít `SetDockState` chcete použít pro ovládací pruhy rámce okna. Předchozí stav je uložený ve `CDockState` objektu s `GetDockState`  
  
##  <a name="setmenubarstate"></a>  CFrameWnd::SetMenuBarState  
 Nastaví stav zobrazení v nabídce v aktuální aplikaci MFC skrytý nebo zobrazit.  
  
```  
virtual BOOL SetMenuBarState(DWORD nState);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] `nState`|Určuje, jestli chcete zobrazit nebo skrýt v nabídce. `nState` Parametr může mít následující hodnoty:<br /><br /> -AFX_MBS_VISIBLE (0x01) - zobrazí v nabídce, pokud je skrytý, ale nemá žádný vliv, pokud je zobrazen.<br />-AFX_MBS_HIDDEN (0x02) - skryje v nabídce, pokud se zobrazí, ale nemá žádný vliv, pokud je skrytý.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud se tato metoda úspěšně změní stav nabídky; v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud dojde k chybě za běhu, tato metoda vyhodnotí v režimu ladění a vyvolá výjimku odvozené z [CException](../../mfc/reference/cexception-class.md) třídy.  
  
##  <a name="setmenubarvisibility"></a>  CFrameWnd::SetMenuBarVisibility  
 Nastaví výchozí chování v nabídce v aktuální aplikaci MFC být skrytý nebo viditelný.  
  
```  
virtual void SetMenuBarVisibility(DWORD nStyle);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] `nStyle`|Určuje, jestli v nabídce je ve výchozím nastavení skryté, nebo je viditelná a je aktivní. `nStyle` Parametr může mít následující hodnoty:<br /><br /> -AFX_MBV_KEEPVISIBLE (0X01)-<br />     V nabídce se zobrazí po celou dobu a ve výchozím nastavení nemá fokus.<br />-AFX_MBV_DISPLAYONFOCUS (0X02)-<br />     Ve výchozím nastavení je skryté v nabídce. Pokud je skryté v nabídce, stiskněte klávesu ALT pro zobrazení nabídky a pojmenujte ho fokus. Pokud se zobrazí v nabídce, stisknutím klávesy ALT nebo ESC skrytí nabídky.<br />-AFX_MBV_ DISPLAYONFOCUS (0x02) &#124; AFX_MBV_DISPLAYONF10 (0x04)<br />     (bitovou kombinaci (nebo)) – ve výchozím nastavení je skryté v nabídce. Pokud je skryté v nabídce, stiskněte klávesu F10 pro zobrazení nabídky a pojmenujte ho fokus. Pokud se zobrazí v nabídce, stisknutím klávesy F10 Přepnout vstup zapnout nebo vypnout v nabídce. V nabídce se nezobrazí, dokud stisknutím klávesy ALT nebo ESC ho chcete skrýt.|  
  
### <a name="remarks"></a>Poznámky  
 Pokud hodnota `nStyle` parametr není platný, tato metoda vyhodnotí v režimu ladění a vyvolá [CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md) v režimu vydání. V případě jiných chyby za běhu, tato metoda vyhodnotí v režimu ladění a vyvolá výjimku odvozené z [CException](../../mfc/reference/cexception-class.md) třídy.  
  
 Tato metoda má vliv na stav nabídky v aplikacích, které jsou napsané pro [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] a novější.  
  
##  <a name="setmessagetext"></a>  CFrameWnd::SetMessageText  
 Volání této funkce umístit řetězec v podokně stavového řádku, který má ID 0.  
  
```  
void SetMessageText(LPCTSTR lpszText);  
void SetMessageText(UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszText`  
 Odkazuje na řetězec, který má být umístěn na stavovém řádku.  
  
 `nID`  
 Řetězec ID prostředku řetězce, který má být umístěn do stavového řádku.  
  
### <a name="remarks"></a>Poznámky  
 Toto je obvykle podokně nejvíce vlevo a nejdelší, stavový řádek.  
  
##  <a name="setprogressbarposition"></a>  CFrameWnd::SetProgressBarPosition  
 Nastaví aktuální pozici pro indikátor průběhu Windows 7, který se zobrazí na hlavním panelu.  
  
```  
void SetProgressBarPosition(int nProgressPos);
```  
  
### <a name="parameters"></a>Parametry  
 `nProgressPos`  
 Určuje pozici nastavit. Musí být v rozsahu, která nastavuje `SetProgressBarRange`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setprogressbarrange"></a>  CFrameWnd::SetProgressBarRange  
 Nastaví rozsah indikátor průběhu Windows 7, který se zobrazí na hlavním panelu.  
  
```  
void SetProgressBarRange(
    int nRangeMin,  
    int nRangeMax);
```  
  
### <a name="parameters"></a>Parametry  
 `nRangeMin`  
 Minimální hodnota.  
  
 `nRangeMax`  
 Maximální hodnota.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setprogressbarstate"></a>  CFrameWnd::SetProgressBarState  
 Nastaví typ a stav indikátoru průběhu zobrazené na tlačítka na hlavním panelu.  
  
```  
void SetProgressBarState(TBPFLAG tbpFlags);
```  
  
### <a name="parameters"></a>Parametry  
 `tbpFlags`  
 Příznaky, které řídí aktuální stav tlačítko průběh. Zadejte jenom jednu z těchto příznaků vzhledem k tomu, že všechny stavy se vzájemně vylučují: TBPF_NOPROGRESS, TBPF_INDETERMINATE, TBPF_NORMAL, TBPF_ERROR, TBPF_PAUSED.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="settaskbaroverlayicon"></a>  CFrameWnd::SetTaskbarOverlayIcon  
 Přetíženo. Překrytí se vztahuje na tlačítka na hlavním panelu označují stav aplikace a upozornit uživatele.  
  
```  
BOOL SetTaskbarOverlayIcon(
    UINT nIDResource,  
    LPCTSTR lpcszDescr);

 
BOOL SetTaskbarOverlayIcon(
    HICON hIcon,  
    LPCTSTR lpcszDescr);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDResource`  
 Určuje ID prostředku ikonu chcete použít jako překrytí. Popis pro `hIcon` podrobnosti.  
  
 `lpcszDescr`  
 Ukazatel na řetězec, který obsahuje verzi informacím vyjádřeným pomocí překrytí za účelem usnadnění přístupu alternativní text.  
  
 `hIcon`  
 Popisovač ikonu chcete použít jako překrytí. To by měl být malé ikony, měření velikosti 16 x 16 pixelů při 96 bodů na palec (dpi). Pokud ikonu překrytí byl již použit pro tlačítko panelu, že existující překrytí nahrazuje. Tato hodnota může být `NULL`. Jak `NULL` zpracována hodnota závisí na tom, jestli představuje tlačítko panelu v jednom okně nebo skupiny systému windows. Zodpovídá volající aplikace k bezplatným `hIcon` Pokud se už nepotřebuje.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` v případě úspěšného; `FALSE` verze operačního systému je menší než Windows 7 nebo pokud dojde k chybě při nastavení na ikonu.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="settitle"></a>  CFrameWnd::SetTitle  
 Nastaví název objektu okna.  
  
```  
void SetTitle(LPCTSTR lpszTitle);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszTitle`  
 Ukazatel na řetězec znaků obsahující název objektu okna.  
  
##  <a name="showcontrolbar"></a>  CFrameWnd::ShowControlBar  
 Volání této funkce člen zobrazení nebo skrytí panelu ovládacího prvku.  
  
```  
void ShowControlBar(
    CControlBar* pBar,  
    BOOL bShow,  
    BOOL bDelay);
```  
  
### <a name="parameters"></a>Parametry  
 `pBar`  
 Ukazatel na panelu řízení zobrazen nebo skryt.  
  
 `bShow`  
 Pokud **TRUE**, určuje, že na ovládací prvek panelu je zobrazený. Pokud **FALSE**, určuje, že je ovládací prvek panelu jako skryté.  
  
 *bDelay*  
 Pokud **TRUE**, zpoždění zobrazující ovládacích pruhů. Pokud **FALSE**, zobrazit ovládací prvek panelu okamžitě.  
  
##  <a name="showownedwindows"></a>  CFrameWnd::ShowOwnedWindows  
 Volání této funkce člen zobrazíte všechny systémy windows, které jsou následníky `CFrameWnd` objektu.  
  
```  
void ShowOwnedWindows(BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 `bShow`  
 Určuje, zda vlastní windows mají být zobrazen nebo skryt.  
  
## <a name="see-also"></a>Viz také  
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [CMDIFrameWnd – třída](../../mfc/reference/cmdiframewnd-class.md)   
 [CMDIChildWnd – třída](../../mfc/reference/cmdichildwnd-class.md)   
 [CView – třída](../../mfc/reference/cview-class.md)   
 [CDocTemplate – třída](../../mfc/reference/cdoctemplate-class.md)   
 [CRuntimeClass – struktura](../../mfc/reference/cruntimeclass-structure.md)
