---
title: CDockingManager Class
ms.date: 11/04/2016
f1_keywords:
- CDockingManager
- AFXDOCKINGMANAGER/CDockingManager
- AFXDOCKINGMANAGER/CDockingManager::AddDockSite
- AFXDOCKINGMANAGER/CDockingManager::AddHiddenMDITabbedBar
- AFXDOCKINGMANAGER/CDockingManager::AddMiniFrame
- AFXDOCKINGMANAGER/CDockingManager::AddPane
- AFXDOCKINGMANAGER/CDockingManager::AdjustDockingLayout
- AFXDOCKINGMANAGER/CDockingManager::AdjustPaneFrames
- AFXDOCKINGMANAGER/CDockingManager::AdjustRectToClientArea
- AFXDOCKINGMANAGER/CDockingManager::AlignAutoHidePane
- AFXDOCKINGMANAGER/CDockingManager::AutoHidePane
- AFXDOCKINGMANAGER/CDockingManager::BringBarsToTop
- AFXDOCKINGMANAGER/CDockingManager::BuildPanesMenu
- AFXDOCKINGMANAGER/CDockingManager::CalcExpectedDockedRect
- AFXDOCKINGMANAGER/CDockingManager::Create
- AFXDOCKINGMANAGER/CDockingManager::DeterminePaneAndStatus
- AFXDOCKINGMANAGER/CDockingManager::DisableRestoreDockState
- AFXDOCKINGMANAGER/CDockingManager::DockPane
- AFXDOCKINGMANAGER/CDockingManager::DockPaneLeftOf
- AFXDOCKINGMANAGER/CDockingManager::EnableAutoHidePanes
- AFXDOCKINGMANAGER/CDockingManager::EnableDocking
- AFXDOCKINGMANAGER/CDockingManager::EnableDockSiteMenu
- AFXDOCKINGMANAGER/CDockingManager::EnablePaneContextMenu
- AFXDOCKINGMANAGER/CDockingManager::FindDockSite
- AFXDOCKINGMANAGER/CDockingManager::FindDockSiteByPane
- AFXDOCKINGMANAGER/CDockingManager::FindPaneByID
- AFXDOCKINGMANAGER/CDockingManager::FixupVirtualRects
- AFXDOCKINGMANAGER/CDockingManager::FrameFromPoint
- AFXDOCKINGMANAGER/CDockingManager::GetClientAreaBounds
- AFXDOCKINGMANAGER/CDockingManager::GetDockingMode
- AFXDOCKINGMANAGER/CDockingManager::GetDockSiteFrameWnd
- AFXDOCKINGMANAGER/CDockingManager::GetEnabledAutoHideAlignment
- AFXDOCKINGMANAGER/CDockingManager::GetMiniFrames
- AFXDOCKINGMANAGER/CDockingManager::GetOuterEdgeBounds
- AFXDOCKINGMANAGER/CDockingManager::GetPaneList
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingManager
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingManagerPermanent
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingParams
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingTheme
- AFXDOCKINGMANAGER/CDockingManager::HideAutoHidePanes
- AFXDOCKINGMANAGER/CDockingManager::InsertDockSite
- AFXDOCKINGMANAGER/CDockingManager::InsertPane
- AFXDOCKINGMANAGER/CDockingManager::IsDockSiteMenu
- AFXDOCKINGMANAGER/CDockingManager::IsInAdjustLayout
- AFXDOCKINGMANAGER/CDockingManager::IsOLEContainerMode
- AFXDOCKINGMANAGER/CDockingManager::IsPointNearDockSite
- AFXDOCKINGMANAGER/CDockingManager::IsPrintPreviewValid
- AFXDOCKINGMANAGER/CDockingManager::LoadState
- AFXDOCKINGMANAGER/CDockingManager::LockUpdate
- AFXDOCKINGMANAGER/CDockingManager::OnActivateFrame
- AFXDOCKINGMANAGER/CDockingManager::OnClosePopupMenu
- AFXDOCKINGMANAGER/CDockingManager::OnMoveMiniFrame
- AFXDOCKINGMANAGER/CDockingManager::OnPaneContextMenu
- AFXDOCKINGMANAGER/CDockingManager::PaneFromPoint
- AFXDOCKINGMANAGER/CDockingManager::ProcessPaneContextMenuCommand
- AFXDOCKINGMANAGER/CDockingManager::RecalcLayout
- AFXDOCKINGMANAGER/CDockingManager::ReleaseEmptyPaneContainers
- AFXDOCKINGMANAGER/CDockingManager::RemoveHiddenMDITabbedBar
- AFXDOCKINGMANAGER/CDockingManager::RemoveMiniFrame
- AFXDOCKINGMANAGER/CDockingManager::RemovePaneFromDockManager
- AFXDOCKINGMANAGER/CDockingManager::ReplacePane
- AFXDOCKINGMANAGER/CDockingManager::ResortMiniFramesForZOrder
- AFXDOCKINGMANAGER/CDockingManager::SaveState
- AFXDOCKINGMANAGER/CDockingManager::SendMessageToMiniFrames
- AFXDOCKINGMANAGER/CDockingManager::Serialize
- AFXDOCKINGMANAGER/CDockingManager::SetAutohideZOrder
- AFXDOCKINGMANAGER/CDockingManager::SetDockingMode
- AFXDOCKINGMANAGER/CDockingManager::SetDockState
- AFXDOCKINGMANAGER/CDockingManager::SetPrintPreviewMode
- AFXDOCKINGMANAGER/CDockingManager::SetSmartDockingParams
- AFXDOCKINGMANAGER/CDockingManager::ShowDelayShowMiniFrames
- AFXDOCKINGMANAGER/CDockingManager::ShowPanes
- AFXDOCKINGMANAGER/CDockingManager::StartSDocking
- AFXDOCKINGMANAGER/CDockingManager::StopSDocking
- AFXDOCKINGMANAGER/CDockingManager::m_bHideDockingBarsInContainerMode
- AFXDOCKINGMANAGER/CDockingManager::m_dockModeGlobal
- AFXDOCKINGMANAGER/CDockingManager::m_nDockSensitivity
- AFXDOCKINGMANAGER/CDockingManager::m_nTimeOutBeforeDockingBarDock
- AFXDOCKINGMANAGER/CDockingManager::m_nTimeOutBeforeToolBarDock
helpviewer_keywords:
- CDockingManager [MFC], AddDockSite
- CDockingManager [MFC], AddHiddenMDITabbedBar
- CDockingManager [MFC], AddMiniFrame
- CDockingManager [MFC], AddPane
- CDockingManager [MFC], AdjustDockingLayout
- CDockingManager [MFC], AdjustPaneFrames
- CDockingManager [MFC], AdjustRectToClientArea
- CDockingManager [MFC], AlignAutoHidePane
- CDockingManager [MFC], AutoHidePane
- CDockingManager [MFC], BringBarsToTop
- CDockingManager [MFC], BuildPanesMenu
- CDockingManager [MFC], CalcExpectedDockedRect
- CDockingManager [MFC], Create
- CDockingManager [MFC], DeterminePaneAndStatus
- CDockingManager [MFC], DisableRestoreDockState
- CDockingManager [MFC], DockPane
- CDockingManager [MFC], DockPaneLeftOf
- CDockingManager [MFC], EnableAutoHidePanes
- CDockingManager [MFC], EnableDocking
- CDockingManager [MFC], EnableDockSiteMenu
- CDockingManager [MFC], EnablePaneContextMenu
- CDockingManager [MFC], FindDockSite
- CDockingManager [MFC], FindDockSiteByPane
- CDockingManager [MFC], FindPaneByID
- CDockingManager [MFC], FixupVirtualRects
- CDockingManager [MFC], FrameFromPoint
- CDockingManager [MFC], GetClientAreaBounds
- CDockingManager [MFC], GetDockingMode
- CDockingManager [MFC], GetDockSiteFrameWnd
- CDockingManager [MFC], GetEnabledAutoHideAlignment
- CDockingManager [MFC], GetMiniFrames
- CDockingManager [MFC], GetOuterEdgeBounds
- CDockingManager [MFC], GetPaneList
- CDockingManager [MFC], GetSmartDockingManager
- CDockingManager [MFC], GetSmartDockingManagerPermanent
- CDockingManager [MFC], GetSmartDockingParams
- CDockingManager [MFC], GetSmartDockingTheme
- CDockingManager [MFC], HideAutoHidePanes
- CDockingManager [MFC], InsertDockSite
- CDockingManager [MFC], InsertPane
- CDockingManager [MFC], IsDockSiteMenu
- CDockingManager [MFC], IsInAdjustLayout
- CDockingManager [MFC], IsOLEContainerMode
- CDockingManager [MFC], IsPointNearDockSite
- CDockingManager [MFC], IsPrintPreviewValid
- CDockingManager [MFC], LoadState
- CDockingManager [MFC], LockUpdate
- CDockingManager [MFC], OnActivateFrame
- CDockingManager [MFC], OnClosePopupMenu
- CDockingManager [MFC], OnMoveMiniFrame
- CDockingManager [MFC], OnPaneContextMenu
- CDockingManager [MFC], PaneFromPoint
- CDockingManager [MFC], ProcessPaneContextMenuCommand
- CDockingManager [MFC], RecalcLayout
- CDockingManager [MFC], ReleaseEmptyPaneContainers
- CDockingManager [MFC], RemoveHiddenMDITabbedBar
- CDockingManager [MFC], RemoveMiniFrame
- CDockingManager [MFC], RemovePaneFromDockManager
- CDockingManager [MFC], ReplacePane
- CDockingManager [MFC], ResortMiniFramesForZOrder
- CDockingManager [MFC], SaveState
- CDockingManager [MFC], SendMessageToMiniFrames
- CDockingManager [MFC], Serialize
- CDockingManager [MFC], SetAutohideZOrder
- CDockingManager [MFC], SetDockingMode
- CDockingManager [MFC], SetDockState
- CDockingManager [MFC], SetPrintPreviewMode
- CDockingManager [MFC], SetSmartDockingParams
- CDockingManager [MFC], ShowDelayShowMiniFrames
- CDockingManager [MFC], ShowPanes
- CDockingManager [MFC], StartSDocking
- CDockingManager [MFC], StopSDocking
- CDockingManager [MFC], m_bHideDockingBarsInContainerMode
- CDockingManager [MFC], m_dockModeGlobal
- CDockingManager [MFC], m_nDockSensitivity
- CDockingManager [MFC], m_nTimeOutBeforeDockingBarDock
- CDockingManager [MFC], m_nTimeOutBeforeToolBarDock
ms.assetid: 98e69c43-55d8-4f43-b861-4fda80ec1e32
ms.openlocfilehash: 6d3bbafa15ada97f53710f0faf6a18ea8e892f6c
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58771308"
---
# <a name="cdockingmanager-class"></a>CDockingManager Class

Implementuje základní funkce, které řídí dokovací rozložení v rámci hlavního okna.

## <a name="syntax"></a>Syntaxe

```
class CDockingManager : public CObject
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CDockingManager::AddDockSite](#adddocksite)|Vytvoří dock podokno a přidá ji do seznamu Ovládací panely.|
|[CDockingManager::AddHiddenMDITabbedBar](#addhiddenmditabbedbar)|Přidá na panel popisovač podokno do seznamu skrytých panelu podokna s kartami MDI.|
|[CDockingManager::AddMiniFrame](#addminiframe)|Snímek se přidá do seznamu mini snímků.|
|[CDockingManager::AddPane](#addpane)|Zaregistruje do podokna s dokovací správce.|
|[CDockingManager::AdjustDockingLayout](#adjustdockinglayout)|Přepočítá a upraví rozložení všechna podokna v okně s rámečkem.|
|[CDockingManager::AdjustPaneFrames](#adjustpaneframes)|Způsobí, že WM_NCCALCSIZE zprávy k odeslání pro všechna podokna a `CPaneFrameWnd` systému windows.|
|[CDockingManager::AdjustRectToClientArea](#adjustrecttoclientarea)|Nastaví zarovnání obdélníku.|
|[CDockingManager::AlignAutoHidePane](#alignautohidepane)|Změní velikost ukotvené podokno v režimu automatické skrývání tak, aby trvá celou šířku nebo výšku klientskou oblast rámce obklopený ukotvit lokalit.|
|[CDockingManager::AutoHidePane](#autohidepane)|Vytvoří automaticky skrývat panel nástrojů.|
|[CDockingManager::BringBarsToTop](#bringbarstotop)|Přináší ukotvených panelů, které mají zadané zarovnání do horní části.|
|[CDockingManager::BuildPanesMenu](#buildpanesmenu)|Názvy dokovací panely nástrojů a podokna přidá do nabídky.|
|[CDockingManager::CalcExpectedDockedRect](#calcexpecteddockedrect)|Vypočítá očekávané obdélník ukotvené okno.|
|[CDockingManager::Create](#create)|Vytvoří ukotvené správce.|
|[CDockingManager::DeterminePaneAndStatus](#determinepaneandstatus)|Určuje panel, který obsahuje časovém okamžiku a stavu její ukotvení.|
|[CDockingManager::DisableRestoreDockState](#disablerestoredockstate)|Povolí nebo zakáže načítání dokovací rozložení z registru.|
|[CDockingManager::DockPane](#dockpane)|Ukotvené podokno další podokno nebo okno rámce.|
|[CDockingManager::DockPaneLeftOf](#dockpaneleftof)|Ukotvené podokno nalevo od jiného podokna.|
|[CDockingManager::EnableAutoHidePanes](#enableautohidepanes)|Umožňuje ukotvení podokna na hlavní rámec, vytvoří dock podokno a přidá do seznamu ovládacích panelů.|
|[CDockingManager::EnableDocking](#enabledocking)|Vytvoří podokno ukotvení a umožňuje ukotvení podokna na hlavní rámec.|
|[CDockingManager::EnableDockSiteMenu](#enabledocksitemenu)|Zobrazí další tlačítka, které otevře místní nabídku na popisky všechny ukotvitelných podoken.|
|[CDockingManager::EnablePaneContextMenu](#enablepanecontextmenu)|Říká knihovny určené k zobrazení, který má seznam aplikací panely nástrojů a ukotvitelných podoken, když uživatel klikne pravým tlačítkem myši a knihovny se zpracování zprávy WM_CONTEXTMENU speciální místní nabídky.|
|[CDockingManager::FindDockSite](#finddocksite)|Načte panelu podokno, které je na zadané pozici a, který má zadané zarovnání.|
|[CDockingManager::FindDockSiteByPane](#finddocksitebypane)|Vrátí panelu podokno, které mají id panelu stavového řádku cíl.|
|[CDockingManager::FindPaneByID](#findpanebyid)|Vyhledá podokně podle ID zadaný ovládací prvek.|
|[CDockingManager::FixupVirtualRects](#fixupvirtualrects)|Potvrdí všechny aktuální pozice panelu nástrojů na virtuální obdélníky.|
|[CDockingManager::FrameFromPoint](#framefrompoint)|Vrátí rámce, který obsahuje daný bod.|
|[CDockingManager::GetClientAreaBounds](#getclientareabounds)|Načte obdélník, který obsahuje rozsah klientské oblasti.|
|[CDockingManager::GetDockingMode](#getdockingmode)|Vrátí aktuální režim ukotvení.|
|[CDockingManager::GetDockSiteFrameWnd](#getdocksiteframewnd)|Získá ukazatel do nadřazeného okna rámce.|
|[CDockingManager::GetEnabledAutoHideAlignment](#getenabledautohidealignment)|Vrátí povoleno zarovnání podoken.|
|[CDockingManager::GetMiniFrames](#getminiframes)|Získá seznam miniframes.|
|[CDockingManager::GetOuterEdgeBounds](#getouteredgebounds)|Načte obdélník, který obsahuje vnější hrany rámce.|
|[CDockingManager::GetPaneList](#getpanelist)|Vrátí seznam podoken, které patří k dokovací správce. To zahrnuje všechna podokna s plovoucí desetinnou čárkou.|
|[CDockingManager::GetSmartDockingManager](#getsmartdockingmanager)|Načte ukazatel smart manager ukotvení.|
|[CDockingManager::GetSmartDockingManagerPermanent](#getsmartdockingmanagerpermanent)|Načte ukazatel smart manager ukotvení.|
|[CDockingManager::GetSmartDockingParams](#getsmartdockingparams)|Vrátí inteligentního dokování parametry pro ukotvení správce.|
|[CDockingManager::GetSmartDockingTheme](#getsmartdockingtheme)|Statická metoda, která vrací motiv, který slouží k zobrazení značek inteligentního dokování.|
|[CDockingManager::HideAutoHidePanes](#hideautohidepanes)|Skryje podokno, které je v režimu automaticky skrývat.|
|[CDockingManager::InsertDockSite](#insertdocksite)|Vytvoří podokno ukotvení a vloží je do seznamu ovládacích panelů.|
|[CDockingManager::InsertPane](#insertpane)|Vloží ovládací panel do seznamu ovládacích panelů.|
|[CDockingManager::IsDockSiteMenu](#isdocksitemenu)|Určuje, zda rozbalovací nabídky se zobrazí na popisky všechna podokna.|
|[CDockingManager::IsInAdjustLayout](#isinadjustlayout)|Určuje, pokud se upraví rozložení všechna podokna.|
|[CDockingManager::IsOLEContainerMode](#isolecontainermode)|Určuje, zda je ukotvené správce v režimu kontejneru OLE.|
|[CDockingManager::IsPointNearDockSite](#ispointneardocksite)|Určuje, zda zadaný bod nachází v dokovacím místě.|
|[CDockingManager::IsPrintPreviewValid](#isprintpreviewvalid)|Určuje, zda je nastaven režim náhledu tisku.|
|[CDockingManager::LoadState](#loadstate)|Načte stav dokovací manager z registru.|
|[CDockingManager::LockUpdate](#lockupdate)|Zamkne daném okně.|
|[CDockingManager::OnActivateFrame](#onactivateframe)|Volá se rozhraním, když se stane aktivní nebo se deaktivuje okno rámce.|
|[CDockingManager::OnClosePopupMenu](#onclosepopupmenu)|Volá se rozhraním, když aktivní místní nabídka zpracovává zprávu WM_DESTROY.|
|[CDockingManager::OnMoveMiniFrame](#onmoveminiframe)|Volá se rozhraním, aby přesunout okno s minirámcem.|
|[CDockingManager::OnPaneContextMenu](#onpanecontextmenu)|Volá se rozhraním, když sestavení nabídka, která obsahuje seznam podoken.|
|[CDockingManager::PaneFromPoint](#panefrompoint)|Vrátí podokno obsahující časovém okamžiku.|
|[CDockingManager::ProcessPaneContextMenuCommand](#processpanecontextmenucommand)|Volá se rozhraním, chcete-li vybrat nebo a zrušte zaškrtnutí políčka pro zadaný příkaz Přepočítat rozložení je vidět podokno.|
|[CDockingManager::RecalcLayout](#recalclayout)|Přepočítá rozložení vnitřní ovládací prvky, které jsou k dispozici v seznamu ovládacích prvků.|
|[CDockingManager::ReleaseEmptyPaneContainers](#releaseemptypanecontainers)|Uvolní prázdné podokno kontejnery.|
|[CDockingManager::RemoveHiddenMDITabbedBar](#removehiddenmditabbedbar)|Odebere zadaný skrytý panelu podokně.|
|[CDockingManager::RemoveMiniFrame](#removeminiframe)|Odebere ze seznamu mini snímků zadaného rámce.|
|[CDockingManager::RemovePaneFromDockManager](#removepanefromdockmanager)|Zruší registraci na stavového řádku a odebere ze seznamu ve Správci ukotvení.|
|[CDockingManager::ReplacePane](#replacepane)|Nahradí jiným jedno podokno.|
|[CDockingManager::ResortMiniFramesForZOrder](#resortminiframesforzorder)|Používat rámce v seznamu mini snímků.|
|[CDockingManager::SaveState](#savestate)|Uloží stav dokovací správce do registru.|
|[CDockingManager::SendMessageToMiniFrames](#sendmessagetominiframes)|Odešle určenou zprávu na všechny mini snímky.|
|[CDockingManager::Serialize](#serialize)|Ukotvení správce zapíše do archivu. (Přepíše [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize).)|
|[CDockingManager::SetAutohideZOrder](#setautohidezorder)|Nastaví velikost, šířku a výšku ovládacích pruhů a podokna zadané.|
|[CDockingManager::SetDockingMode](#setdockingmode)|Nastaví režim ukotvení.|
|[CDockingManager::SetDockState](#setdockstate)|Nastaví stav dokovací ovládací pruhy, mini snímků a panelů automaticky skrývat.|
|[CDockingManager::SetPrintPreviewMode](#setprintpreviewmode)|Nastaví režim náhledu tisku pruhy, které se zobrazí v náhledu tisku.|
|[CDockingManager::SetSmartDockingParams](#setsmartdockingparams)|Nastaví parametry, které definují chování inteligentního dokování.|
|[CDockingManager::ShowDelayShowMiniFrames](#showdelayshowminiframes)|Zobrazí nebo skryje windows mini snímků.|
|[CDockingManager::ShowPanes](#showpanes)|Zobrazí nebo skryje podokna ovládacího prvku a automatické skrývání pruhy.|
|[CDockingManager::StartSDocking](#startsdocking)|Spustí se inteligentního dokování určené okno podle zarovnání smart manager ukotvení.|
|[CDockingManager::StopSDocking](#stopsdocking)|Zastaví připojení inteligentního dokování.|

### <a name="data-members"></a>Datové členy

|Name|Popis|
|----------|-----------------|
|[CDockingManager::m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode)|Určuje, zda dokovací správce skryje podokna v režimu kontejneru OLE.|
|[CDockingManager::m_dockModeGlobal](#m_dockmodeglobal)|Určuje režim globální ukotvení.|
|[CDockingManager::m_nDockSensitivity](#m_ndocksensitivity)|Určuje citlivost ukotvení.|
|[CDockingManager::m_nTimeOutBeforeDockingBarDock](#m_ntimeoutbeforedockingbardock)|Určuje dobu v milisekundách, než je ukotven ukotvené podokno v režimu okamžité ukotvení.|
|[CDockingManager::m_nTimeOutBeforeToolBarDock](#m_ntimeoutbeforetoolbardock)|Určuje dobu v milisekundách, než se ukotví okna hlavního rámce.|

## <a name="remarks"></a>Poznámky

Hlavní okno rámce vytvoří a inicializuje tuto třídu automaticky.

Ukotvení objekt správce obsahuje seznam všech podoken, které jsou v dokovací rozložení a také seznam všech [cpaneframewnd –](../../mfc/reference/cpaneframewnd-class.md) windows, které patří do okna hlavního rámce.

`CDockingManager` Třída implementuje některé služby, které můžete použít k vyhledání podokno nebo `CPaneFrameWnd` okna. Obvykle není volána tyto služby přímo vzhledem k tomu, že jsou zabaleny v objekt okna hlavního rámce. Další informace najdete v tématu [cpaneframewnd – třída](../../mfc/reference/cpaneframewnd-class.md).

## <a name="customization-tips"></a>Tipy k přizpůsobení

Použijte následující tipy k `CDockingManager` objekty:

- [Cdockingmanager – třída](../../mfc/reference/cdockingmanager-class.md) podporuje tyto dokovací režimy:

  - `AFX_DOCK_TYPE::DT_IMMEDIATE`

  - `AFX_DOCK_TYPE::DT_STANDARD`

  - `AFX_DOCK_TYPE::DT_SMART`

  Tyto dokovací režimy, které jsou definovány pomocí [CDockingManager::m_dockModeGlobal](#m_dockmodeglobal) a jsou nastaveny voláním [CDockingManager::SetDockingMode](#setdockingmode).

- Pokud chcete vytvořit podokno s plovoucí, bez možností změny velikosti, zavolejte [CDockingManager::AddPane](#addpane) metody. Metoda registruje v podokně s dokovací správce, který je zodpovědný za rozložení v podokně.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít různé metody v `CDockingManager` třída ke konfiguraci `CDockingManager` objektu. Příklad ukazuje, jak zobrazit další tlačítka, které otevře místní nabídku na popisky všechny ukotvitelných podoken a jak nastavit dokovací režim objektu. Tento fragment kódu je součástí [Visual Studio demonstrační ukázka](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#24](../../mfc/codesnippet/cpp/cdockingmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CDockingManager](../../mfc/reference/cdockingmanager-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxDockingManager.h

##  <a name="adddocksite"></a>  CDockingManager::AddDockSite

Vytvoří dock podokno a přidá ji do seznamu Ovládací panely.

```
BOOL AddDockSite(
    const AFX_DOCKSITE_INFO& info,
    CDockSite** ppDockBar = NULL);
```

### <a name="parameters"></a>Parametry

*info*<br/>
[in] Odkaz na informace o struktuře, která obsahuje ukotvit podokně zarovnání.

*ppDockBar*<br/>
[out] Ukazatel na ukazatel na nové podokno ukotvení.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud úspěšně; vytvořil podokně ukotvení FALSE v opačném případě.

##  <a name="addhiddenmditabbedbar"></a>  CDockingManager::AddHiddenMDITabbedBar

Přidá na panel popisovač podokno do seznamu skrytých panelu podokna s kartami MDI.

```
void AddHiddenMDITabbedBar(CDockablePane* pBar);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[in] Ukazatel na panel podokno

##  <a name="addpane"></a>  CDockingManager::AddPane

Zaregistruje do podokna s dokovací správce.

```
BOOL AddPane(
    CBasePane* pWnd,
    BOOL bTail = TRUE,
    BOOL bAutoHide = FALSE,
    BOOL bInsertForOuterEdge = FALSE);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
[out v] Určuje, v podokně pro přidání do ukotvení správce.

*bTail*<br/>
[in] TRUE, pokud chcete přidat v podokně na konec seznamu podokna pro ukotvení správce; v opačném případě hodnota FALSE.

*bAutoHide*<br/>
[in] Pouze pro interní použití. Vždy použijte výchozí hodnotu FALSE.

*bInsertForOuterEdge*<br/>
[in] Pouze pro interní použití. Vždy použijte výchozí hodnotu FALSE.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud se v podokně byl úspěšně zaregistrován ve službě dokovací správce; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Volejte tuto metodu za účelem registrace s plovoucí, bez možností změny velikosti podoken s dokovací správce. Pokud nezaregistrujete podoken, nebude zobrazovat správně po ukotvení správce vytvoří rozložení.

##  <a name="adjustdockinglayout"></a>  CDockingManager::AdjustDockingLayout

Přepočítá a upraví rozložení všechna podokna v okně s rámečkem.

```
virtual void AdjustDockingLayout(HDWP hdwp = NULL);
```

### <a name="parameters"></a>Parametry

*hdwp*<br/>
[in] Určuje pozici strukturu odložené okna. Další informace najdete v tématu [datové typy Windows](/windows/desktop/WinProg/windows-data-types).

### <a name="remarks"></a>Poznámky

##  <a name="addminiframe"></a>  CDockingManager::AddMiniFrame

Snímek se přidá do seznamu mini snímků.

```
virtual BOOL AddMiniFrame(CPaneFrameWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
[in] Ukazatele rámce.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud se nenachází v seznamu objektů Frame mini rámce a byl úspěšně; přidán FALSE v opačném případě.

##  <a name="adjustpaneframes"></a>  CDockingManager::AdjustPaneFrames

Způsobí, že WM_NCCALCSIZE zprávy k odeslání pro všechna podokna a `CPaneFrameWnd` systému windows.

```
virtual void AdjustPaneFrames();
```

### <a name="remarks"></a>Poznámky

##  <a name="adjustrecttoclientarea"></a>  CDockingManager::AdjustRectToClientArea

Nastaví zarovnání obdélníku.

```
virtual BOOL AdjustRectToClientArea(
    CRect& rectResult,
    DWORD dwAlignment);
```

### <a name="parameters"></a>Parametry

*rectResult*<br/>
[in] Odkaz na `CRect` objektu

*dwAlignment*<br/>
[in] Zarovnání `CRect` objektu

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE v případě zarovnání `CRect` byl upraven objekt; FALSE v opačném případě.

### <a name="remarks"></a>Poznámky

*DwAlignment* parametr může mít jednu z následujících hodnot:

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

##  <a name="alignautohidepane"></a>  CDockingManager::AlignAutoHidePane

Změní velikost ukotvené podokno v režimu automatické skrývání tak, aby trvá celou šířku nebo výšku klientskou oblast rámce obklopený ukotvit lokalit.

```
void AlignAutoHidePane(
    CPaneDivider* pDefaultSlider,
    BOOL bIsVisible = TRUE);
```

### <a name="parameters"></a>Parametry

*pDefaultSlider*<br/>
[in] Ukotvené podokno posuvníku.

*bIsVisible*<br/>
[in] Hodnota TRUE, pokud se zobrazuje; ukotvené podokno FALSE v opačném případě.

##  <a name="autohidepane"></a>  CDockingManager::AutoHidePane

Vytvoří automaticky skrývat panel nástrojů.

```
CMFCAutoHideToolBar* AutoHidePane(
    CDockablePane* pBar,
    CMFCAutoHideToolBar* pCurrAutoHideToolBar = NULL);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[in] Ukazatel na panelu podokně.

*pCurrAutoHideToolBar*<br/>
[in] Ukazatel na automatické skrytí panelu nástrojů.

### <a name="return-value"></a>Návratová hodnota

Hodnota NULL, pokud automaticky skrýt panel nástrojů nebyl vytvořen; v opačném případě ukazatel na nový panel nástrojů.

##  <a name="bringbarstotop"></a>  CDockingManager::BringBarsToTop

Přináší ukotvených panelů, které mají zadané zarovnání do horní části.

```
void BringBarsToTop(
    DWORD dwAlignment = 0,
    BOOL bExcludeDockedBars = TRUE);
```

### <a name="parameters"></a>Parametry

*dwAlignment*<br/>
[in] Zarovnání dock panely, které přesměrují se na začátek ostatní okna.

*bExcludeDockedBars*<br/>
[in] TRUE, pokud chcete vyloučit ukotvených panelů z na maximum. v opačném případě FALSE.

##  <a name="buildpanesmenu"></a>  CDockingManager::BuildPanesMenu

Názvy dokovací panely nástrojů a podokna přidá do nabídky.

```
void BuildPanesMenu(
    CMenu& menu,
    BOOL bToolbarsOnly);
```

### <a name="parameters"></a>Parametry

*Nabídky*<br/>
[in] Nabídka Přidat názvy dokovací podokna a panely nástrojů.

*bToolbarsOnly*<br/>
[in] TRUE, pokud chcete přidat názvy pouze nástrojů v nabídce; FALSE v opačném případě.

##  <a name="calcexpecteddockedrect"></a>  CDockingManager::CalcExpectedDockedRect

Vypočítá očekávané obdélník ukotvené okno.

```
void CalcExpectedDockedRect(
    CWnd* pWnd,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
[in] Ukazatel na okno ukotvení.

*ptMouse*<br/>
[in] Kurzor myši.

*rectResult*<br/>
[out] Počítaný obdélník.

*bDrawTab*<br/>
[in] True pro vykreslování karet; v opačném případě FALSE.

*ppTargetBar*<br/>
[out] Ukazatel na ukazatel do podokna cíl.

### <a name="remarks"></a>Poznámky

Tato metoda vypočítá obdélník, který by zabírat okno, pokud uživatel přetáhli do bodu určeného v okně *ptMouse* a ukotven existuje.

##  <a name="create"></a>  CDockingManager::Create

Vytvoří ukotvené správce.

```
BOOL Create(CFrameWnd* pParentWnd);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
[in] Ukazatel na nadřazeného rámce dokovací správce. Tato hodnota nesmí být NULL.

### <a name="return-value"></a>Návratová hodnota

Vždy TRUE.

##  <a name="determinepaneandstatus"></a>  CDockingManager::DeterminePaneAndStatus

Určuje panel, který obsahuje časovém okamžiku a stavu její ukotvení.

```
virtual AFX_CS_STATUS DeterminePaneAndStatus(
    CPoint pt,
    int nSensitivity,
    DWORD dwEnabledAlignment,
    CBasePane** ppTargetBar,
    const CBasePane* pBarToIgnore,
    const CBasePane* pBarToDock);
```

### <a name="parameters"></a>Parametry

*pt*<br/>
[in] Umístění v podokně zkontrolovat.

*nSensitivity*<br/>
[in] Hodnotu pro zvýšení obdélníku každý kontrolovaný stavového řádku okna. Podokno splňuje kritéria hledání, pokud daný bod je v této oblasti zvýšení.

*dwEnabledAlignment*<br/>
[in] Zarovnání ukotvené podokno.

*ppTargetBar*<br/>
[out] Ukazatel na ukazatel do podokna cíl.

*pBarToIgnore*<br/>
[in] Podokno, které metoda ignoruje.

*pBarToDock*<br/>
[in] Podokno, které je ukotven.

### <a name="return-value"></a>Návratová hodnota

Stav ukotvení.

### <a name="remarks"></a>Poznámky

Ukotvení stav může být jeden z následujících hodnot:

|Hodnota AFX_CS_STATUS|Význam|
|---------------------------|-------------|
|CS_NOTHING|Ukazatel není přes dokovacího webu. Proto se zachovat v podokně s plovoucí desetinnou čárkou.|
|CS_DOCK_IMMEDIATELY|Ukazatel myši je nad dokovacím místě v přímý režim (DT_IMMEDIATE style je povoleno), tak v podokně musí být ukotveno, okamžitě.|
|CS_DELAY_DOCK|Ukazatel myši je nad dokovacího webu, který je jiný ukotvené podokno nebo okraj hlavního rámce.|
|CS_DELAY_DOCK_TO_TAB|Ukazatel myši je nad dokovacího webu, který způsobí, že v podokně ukotvit v okně s kartami. K tomu dojde, když je ukazatel myši přes popisek jiný ukotvené podokno nebo ke kartě oblasti podokna s kartami.|

##  <a name="disablerestoredockstate"></a>  CDockingManager::DisableRestoreDockState

Povolí nebo zakáže načítání dokovací rozložení z registru.

```
void DisableRestoreDockState(BOOL bDisable = TRUE);
```

### <a name="parameters"></a>Parametry

*bDisable*<br/>
[in] Pokud chcete zakázat načítání dokovací rozložení z registru. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tuto metodu volejte, když musíte zachovat aktuální rozložení dokovací panely nástrojů a podokna při načítání stavu aplikace.

##  <a name="dockpane"></a>  CDockingManager::DockPane

Ukotvené podokno další podokno nebo okno rámce.

```
void DockPane(
    CBasePane* pBar,
    UINT nDockBarID = 0,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[in] Ukazatel na panel podokně ukotvit.

*nDockBarID*<br/>
[in] Id ukotvení panelu.

*lpRect*<br/>
[in] Cílového obdélníku.

##  <a name="dockpaneleftof"></a>  CDockingManager::DockPaneLeftOf

Ukotvené podokno nalevo od jiného podokna.

```
BOOL DockPaneLeftOf(
    CPane* pBarToDock,
    CPane* pTargetBar);
```

### <a name="parameters"></a>Parametry

*pBarToDock*<br/>
[in] Ukazatel do podokna ukotvit vlevo od *pTargetBar*.

*pTargetBar*<br/>
[in] Ukazatel do podokna cíl.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud byl úspěšně; ukotven podokna v opačném případě hodnota FALSE.

##  <a name="enableautohidepanes"></a>  CDockingManager::EnableAutoHidePanes

Umožňuje ukotvení podokna na hlavní rámec, vytvoří dock podokno a přidá do seznamu ovládacích panelů.

```
BOOL EnableAutoHidePanes(DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
[in] Ukotvení zarovnání.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud úspěšně; vytvořil podokně ukotvení FALSE v opačném případě.

##  <a name="enabledocking"></a>  CDockingManager::EnableDocking

Vytvoří podokno ukotvení a umožňuje ukotvení podokna na hlavní rámec.

```
BOOL EnableDocking(DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
[in] Ukotvení zarovnání.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud úspěšně; vytvořil podokně ukotvení FALSE v opačném případě.

##  <a name="enabledocksitemenu"></a>  CDockingManager::EnableDockSiteMenu

Zobrazí další tlačítka, které otevře místní nabídku na popisky všechny ukotvitelných podoken.

```
static void EnableDockSiteMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[in] TRUE, pokud chcete povolit ukotvenou nabídku lokality; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

V nabídce webu ukotvení se zobrazí následující možnosti pro změnu stavu ukotvení panelu:

- `Floating` -Čísel s plovoucí čárkou podokno

- `Docking` -Ukotvené podokno v hlavního rámce v umístění, kde se v podokně poslední ukotven

- `AutoHide` – Přepne podokna do režimu automatické skrývání

- `Hide` -Skryje podokno

Ve výchozím nastavení tato nabídka se nezobrazí.

##  <a name="enablepanecontextmenu"></a>  CDockingManager::EnablePaneContextMenu

Říká knihovny určené k zobrazení, který má seznam aplikací panely nástrojů a ukotvitelných podoken, když uživatel klikne pravým tlačítkem myši a knihovny se zpracování zprávy WM_CONTEXTMENU speciální místní nabídky.

```
void EnablePaneContextMenu(
    BOOL bEnable,
    UINT uiCustomizeCmd,
    const CString& strCustomizeText,
    BOOL bToolbarsOnly = FALSE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[in] Při hodnotě TRUE se knihovny zapne podpora pro automatické místní nabídku Pokud je FALSE knihovny vypne podporu pro automatické kontextové nabídky.

*uiCustomizeCmd*<br/>
[in] Id příkazu pro **vlastní** položky v nabídce.

*strCustomizeText*<br/>
[in] Text **vlastní** položky.

*bToolbarsOnly*<br/>
[in] Pokud je hodnota TRUE, v nabídce zobrazuje pouze seznam panelů nástrojů aplikace; Pokud má hodnotu FALSE, přidá knihovnu ukotvitelných podoken aplikace do tohoto seznamu.

##  <a name="finddocksite"></a>  CDockingManager::FindDockSite

Načte panelu podokno, které je na zadané pozici a, který má zadané zarovnání.

```
virtual CDockSite* FindDockSite(
    DWORD dwAlignment,
    BOOL bOuter);
```

### <a name="parameters"></a>Parametry

*dwAlignment*<br/>
[in] Zarovnání panelu podokně.

*bOuter*<br/>
[in] Při hodnotě TRUE se načtení panelu v hlavní pozice v seznamu ovládacích panelů. V opačném případě načtení panelu v koncové pozici v seznamu ovládacích panelů.

### <a name="return-value"></a>Návratová hodnota

Ukotvené podokno, který má zadané zarovnání; V opačném případě hodnota NULL.

##  <a name="findpanebyid"></a>  CDockingManager::FindPaneByID

Vyhledá podokně podle ID zadaný ovládací prvek.

```
virtual CBasePane* FindPaneByID(
    UINT uBarID,
    BOOL bSearchMiniFrames = FALSE);
```

### <a name="parameters"></a>Parametry

*uBarID*<br/>
[in] Určuje ID ovládacího prvku podokna najít.

*bSearchMiniFrames*<br/>
[in] Hodnota TRUE, chcete-li do hledání zahrnout všechny plovoucího podokna. FALSE, zahrnuta budou pouze ukotveného podokna.

### <a name="return-value"></a>Návratová hodnota

[Cbasepane –](../../mfc/reference/cbasepane-class.md) objekt, který má zadaný ovládací prvek ID nebo hodnota NULL, pokud nelze najít zadaný podokně.

### <a name="remarks"></a>Poznámky

##  <a name="finddocksitebypane"></a>  CDockingManager::FindDockSiteByPane

Vrátí panelu podokno, které mají id panelu stavového řádku cíl.

```
virtual CDockSite* FindDockSiteByPane(CPane* pTargetBar);
```

### <a name="parameters"></a>Parametry

*pTargetBar*<br/>
[in] Ukazatel panelu stavového řádku cíl.

### <a name="return-value"></a>Návratová hodnota

Na panelu podokno, které mají id panelu stavového řádku cíl; Hodnota NULL, pokud není žádná taková panelu podokně neexistuje.

##  <a name="fixupvirtualrects"></a>  CDockingManager::FixupVirtualRects

Potvrdí všechny aktuální pozice panelu nástrojů na virtuální obdélníky.

```
virtual void FixupVirtualRects();
```

### <a name="remarks"></a>Poznámky

Při spuštění uživatelem přetáhněte panel nástrojů, aplikace si zapamatuje jeho původní pozice v *virtuální obdélník*. Když se uživatel přesune panel nástrojů v jeho dokovacím místě, mohou posunout panelu nástrojů panelů nástrojů. Původní umístění panelů jsou uloženy v příslušné virtuální obdélníků.

##  <a name="framefrompoint"></a>  CDockingManager::FrameFromPoint

Vrátí rámce, který obsahuje daný bod.

```
virtual CPaneFrameWnd* FrameFromPoint(
    CPoint pt,
    CPaneFrameWnd* pFrameToExclude,
    BOOL bFloatMultiOnly) const;
```

### <a name="parameters"></a>Parametry

*pt*<br/>
[in] Určuje bod, v souřadnicovém systému obrazovky, chcete-li zkontrolovat.

*pFrameToExclude*<br/>
[in] Ukazatel na objekt frame, který vyloučit.

*bFloatMultiOnly*<br/>
[in] True pro vyloučení rámce, které nejsou instance `CMultiPaneFrameWnd`; FALSE v opačném případě.

### <a name="return-value"></a>Návratová hodnota

Rámce, který obsahuje daný bod; V opačném případě hodnota NULL.

##  <a name="getclientareabounds"></a>  CDockingManager::GetClientAreaBounds

Načte obdélník, který obsahuje rozsah klientské oblasti.

```
CRect GetClientAreaBounds() const;

void GetClientAreaBounds(CRect& rcClient);
```

### <a name="parameters"></a>Parametry

*rcClient*<br/>
[out] Odkaz na obdélník, který obsahuje rozsah klientské oblasti.

### <a name="return-value"></a>Návratová hodnota

Obdélník, který obsahuje rozsah klientské oblasti.

##  <a name="getdockingmode"></a>  CDockingManager::GetDockingMode

Vrátí aktuální režim ukotvení.

```
static AFX_DOCK_TYPE GetDockingMode();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota výčtu, která představuje aktuální režim ukotvení. Může být jeden z následujících hodnot:

- DT_STANDARD

- DT_IMMEDIATE

- DT_SMART

### <a name="remarks"></a>Poznámky

Chcete-li nastavit režim ukotvení, zavolejte [CDockingManager::SetDockingMode](#setdockingmode).

##  <a name="getdocksiteframewnd"></a>  CDockingManager::GetDockSiteFrameWnd

Získá ukazatel do nadřazeného okna rámce.

```
CFrameWnd* GetDockSiteFrameWnd() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rámec nadřazeného okna.

##  <a name="getenabledautohidealignment"></a>  CDockingManager::GetEnabledAutoHideAlignment

Vrátí povoleno zarovnání podoken.

```
DWORD GetEnabledAutoHideAlignment() const;
```

### <a name="return-value"></a>Návratová hodnota

Bitová kombinace příznaků CBRS_ALIGN_ nebo 0, pokud nejsou povolené automatické skrývání podoken. Další informace najdete v tématu [CFrameWnd::EnableDocking](../../mfc/reference/cframewnd-class.md#enabledocking).

### <a name="remarks"></a>Poznámky

Metoda vrátí zarovnání povolené automatické skrývání ovládacích panelů. Chcete-li povolit automatické skrývání pruhy, zavolejte [CFrameWndEx::EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes).

##  <a name="getminiframes"></a>  CDockingManager::GetMiniFrames

Získá seznam miniframes.

```
const CObList& GetMiniFrames() const;
```

### <a name="return-value"></a>Návratová hodnota

Seznam miniframes obsahující ovládací pruhy, které patří k dokovací správce.

##  <a name="getouteredgebounds"></a>  CDockingManager::GetOuterEdgeBounds

Načte obdélník, který obsahuje vnější hrany rámce.

```
CRect GetOuterEdgeBounds() const;
```

### <a name="return-value"></a>Návratová hodnota

Obdélník, který obsahuje vnější hrany rámce.

##  <a name="getpanelist"></a>  CDockingManager::GetPaneList

Vrátí seznam podoken, které patří k dokovací správce. To zahrnuje všechna podokna s plovoucí desetinnou čárkou.

```
void GetPaneList(
    CObList& lstBars,
    BOOL bIncludeAutohide = FALSE,
    CRuntimeClass* pRTCFilter = NULL,
    BOOL bIncludeTabs = FALSE);
```

### <a name="parameters"></a>Parametry

*lstBars*<br/>
[out v] Obsahuje všechny podokna aktuálního dokovacího správce.

*bIncludeAutohide*<br/>
[in] TRUE pro zahrnutí podoken, které jsou v režimu automatické skrývání v opačném případě hodnota FALSE.

*pRTCFilter*<br/>
[in] Pokud není NULL, vrácený seznam obsahuje podokna pouze třídy zadaného modulu runtime.

*bIncludeTabs*<br/>
[in] TRUE pro zahrnutí karet; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Pokud v dokovací manager nejsou žádné podokně s kartami, vrátí metoda ukazatele na [cbasetabbedpane – třída](../../mfc/reference/cbasetabbedpane-class.md) objektů a vy musíte vytvořit výčet karty explicitně.

Použití *pRTCFilter* získat určitou třídu podoken. Pouze panely nástrojů lze například získat nastavením této hodnoty odpovídajícím způsobem.

##  <a name="getsmartdockingmanager"></a>  CDockingManager::GetSmartDockingManager

Načte ukazatel smart manager ukotvení.

```
CSmartDockingManager* GetSmartDockingManager();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na smart manager ukotvení.

##  <a name="getsmartdockingmanagerpermanent"></a>  CDockingManager::GetSmartDockingManagerPermanent

Načte ukazatel smart manager ukotvení.

```
CSmartDockingManager* GetSmartDockingManagerPermanent() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na smart manager ukotvení.

##  <a name="getsmartdockingparams"></a>  CDockingManager::GetSmartDockingParams

Vrátí inteligentního dokování parametry pro ukotvení správce.

```
static CSmartDockingInfo& GetSmartDockingParams();
```

### <a name="return-value"></a>Návratová hodnota

Třída, která obsahuje inteligentního dokování parametry pro aktuální dokovací správce. Další informace najdete v tématu [csmartdockinginfo – třída](../../mfc/reference/csmartdockinginfo-class.md).

### <a name="remarks"></a>Poznámky

##  <a name="hideautohidepanes"></a>  CDockingManager::HideAutoHidePanes

Skryje podokno, které je v režimu automaticky skrývat.

```
void HideAutoHidePanes(
    CDockablePane* pBarToExclude = NULL,
    BOOL bImmediately = FALSE);
```

### <a name="parameters"></a>Parametry

*pBarToExclude*<br/>
[in] Ukazatel na panel chcete vyloučit z skrytí.

*bImmediately*<br/>
[in] TRUE, pokud chcete skrýt podokno okamžitě; FALSE, pokud chcete skrýt podokno s efektem automaticky skrývat.

##  <a name="insertdocksite"></a>  CDockingManager::InsertDockSite

Vytvoří podokno ukotvení a vloží je do seznamu ovládacích panelů.

```
BOOL InsertDockSite(
    const AFX_DOCKSITE_INFO& info,
    DWORD dwAlignToInsertAfter,
    CDockSite** ppDockBar = NULL);
```

### <a name="parameters"></a>Parametry

*info*<br/>
[in] Struktura, která obsahuje informace o zarovnání podokno ukotvení.

*dwAlignToInsertAfter*<br/>
[in] Zarovnání ukotvení panelu.

*ppDockBar*<br/>
[out] Ukazatel na ukazatel na podokno ukotvení.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud úspěšně; vytvořil podokně ukotvení FALSE v opačném případě.

##  <a name="insertpane"></a>  CDockingManager::InsertPane

Vloží ovládací panel do seznamu ovládacích panelů.

```
BOOL InsertPane(
    CBasePane* pControlBar,
    CBasePane* pTarget,
    BOOL bAfter = TRUE);
```

### <a name="parameters"></a>Parametry

*pControlBar*<br/>
[in] Ukazatel na ovládací prvek stavového řádku.

*pTarget*<br/>
[in] Ukazatel na cílové stavového řádku.

*bAfter*<br/>
[in] TRUE, pokud chcete vložit v podokně po pozici cílové podokna. FALSE v opačném případě.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud se v podokně ovládacího prvku se úspěšně přidal do seznamu ovládací pruhy; FALSE v opačném případě.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí hodnotu false, pokud v podokně ovládacího prvku je již v seznamu ovládacích panelů nebo pokud podokně cíl neexistuje v seznamu ovládacích panelů.

##  <a name="isdocksitemenu"></a>  CDockingManager::IsDockSiteMenu

Určuje, zda rozbalovací nabídky se zobrazí na popisky všechna podokna.

```
static BOOL IsDockSiteMenu();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud ukotvenou nabídku webu se zobrazí na popisky všechny ukotvitelných podoken; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Můžete povolit ukotvenou nabídku lokality voláním [CDockingManager::EnableDockSiteMenu](#enabledocksitemenu).

##  <a name="isinadjustlayout"></a>  CDockingManager::IsInAdjustLayout

Určuje, pokud se upraví rozložení všechna podokna.

```
BOOL IsInAdjustLayout() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud se upraví rozložení všechna podokna; FALSE v opačném případě.

##  <a name="isolecontainermode"></a>  CDockingManager::IsOLEContainerMode

Určuje, zda je ukotvené správce v režimu kontejneru OLE.

```
BOOL IsOLEContainerMode() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud ukotvení manager je v režimu kontejneru OLE v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

V režimu kontejneru OLE jsou skryté všechny ukotvitelných podoken a panelů nástrojů aplikace. Podokna jsou rovněž skryté v tomto režimu, pokud jste nastavili [CDockingManager::m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode) na hodnotu TRUE.

##  <a name="ispointneardocksite"></a>  CDockingManager::IsPointNearDockSite

Určuje, zda zadaný bod nachází v dokovacím místě.

```
BOOL IsPointNearDockSite(
    CPoint point,
    DWORD& dwBarAlignment,
    BOOL& bOuterEdge) const;
```

### <a name="parameters"></a>Parametry

*point*<br/>
[in] Zadaný bod.

*dwBarAlignment*<br/>
[out] Určuje, které edge se bod nachází blízko. Možné hodnoty jsou CBRS_ALIGN_LEFT, CBRS_ALIGN_RIGHT, CBRS_ALIGN_TOP a CBRS_ALIGN_BOTTOM.

*bOuterEdge*<br/>
[out] Hodnota TRUE, pokud je bod se blíží vnější okraj dokovacím místě; FALSE v opačném případě.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud se bod nachází v dokovacím místě; v opačném případě FALSE.

##  <a name="isprintpreviewvalid"></a>  CDockingManager::IsPrintPreviewValid

Určuje, zda je nastaven režim náhledu tisku.

```
BOOL IsPrintPreviewValid() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud má nastaven režim náhledu tisku; FALSE v opačném případě.

##  <a name="loadstate"></a>  CDockingManager::LoadState

Načte stav dokovací manager z registru.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[in] Název profilu.

*uiID*<br/>
[in] Id ukotvení správce.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud ukotvení stavu Správce byl úspěšně; načten. v opačném případě FALSE.

##  <a name="lockupdate"></a>  CDockingManager::LockUpdate

Zamkne daném okně.

```
void LockUpdate(BOOL bLock);
```

### <a name="parameters"></a>Parametry

*bLock*<br/>
[in] Hodnota TRUE, pokud je uzamčen v okně; FALSE v opačném případě.

### <a name="remarks"></a>Poznámky

Když okno zašifrovaná, nelze jej přesunout a nemůže být vystavena.

##  <a name="m_bhidedockingbarsincontainermode"></a>  CDockingManager::m_bHideDockingBarsInContainerMode

Určuje, zda dokovací správce skryje podokna v režimu kontejneru OLE.

```
AFX_IMPORT_DATA static BOOL m_bHideDockingBarsInContainerMode;
```

### <a name="remarks"></a>Poznámky

Tuto hodnotu nastavte na hodnotu FALSE, pokud chcete zachovat všechny podokna ukotven na hlavní rámec viditelné, když je aplikace v režimu kontejneru OLE. Ve výchozím nastavení tato hodnota je TRUE.

##  <a name="m_dockmodeglobal"></a>  CDockingManager::m_dockModeGlobal

Určuje režim globální ukotvení.

```
AFX_IMPORT_DATA static AFX_DOCK_TYPE m_dockModeGlobal;
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení používá každá ukotvené podokno režimem ukotvení. Další informace o hodnotách, které toto pole lze nastavit na najdete v tématu [CBasePane::GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode).

##  <a name="m_ndocksensitivity"></a>  CDockingManager::m_nDockSensitivity

Určuje citlivost ukotvení.

```
AFX_IMPORT_DATA static int m_nDockSensitivity;
```

### <a name="remarks"></a>Poznámky

Ukotvení citlivosti definuje, jak blízko plovoucí podokno můžete přistupovat ukotvené podokno, dokovacího webu nebo jiného podokna před rozhraní framework změnit její stav na ukotvení.

##  <a name="m_ntimeoutbeforedockingbardock"></a>  CDockingManager::m_nTimeOutBeforeDockingBarDock

Určuje dobu v milisekundách, než je ukotven ukotvené podokno v režimu okamžité ukotvení.

```
static UINT m_nTimeOutBeforeDockingBarDock;
```

### <a name="remarks"></a>Poznámky

Předtím, než je ukotven na stavového řádku, rozhraní framework čeká zadanou dobu. To zabrání v podokně se omylem ukotven do umístění, zatímco uživatel je stále přetažením.

##  <a name="m_ntimeoutbeforetoolbardock"></a>  CDockingManager::m_nTimeOutBeforeToolBarDock

Určuje dobu v milisekundách, než se ukotví okna hlavního rámce.

```
static UINT m_nTimeOutBeforeToolBarDock;
```

### <a name="remarks"></a>Poznámky

Předtím, než je ukotven na panel nástrojů, rozhraní framework čeká zadanou dobu. To zabrání se omylem ukotven do umístění, zatímco uživatel je stále jeho přetažením panelu nástrojů.

##  <a name="onactivateframe"></a>  CDockingManager::OnActivateFrame

Volá se rozhraním, když se stane aktivní nebo se deaktivuje okno rámce.

```
virtual void OnActivateFrame(BOOL bActivate);
```

### <a name="parameters"></a>Parametry

*bActivate*<br/>
[in] Při hodnotě TRUE se stane oknem rámce aktivní; Pokud má hodnotu FALSE, je deaktivuje okno rámce.

##  <a name="onclosepopupmenu"></a>  CDockingManager::OnClosePopupMenu

Volá se rozhraním, když aktivní místní nabídka zpracovává zprávu WM_DESTROY.

```
void OnClosePopupMenu();
```

### <a name="remarks"></a>Poznámky

Rozhraní pošle zprávu WM_DESTROY po Chystáte se zavřít aktuální hlavní okno. Potlačí tuto metodu za účelem zpracovat oznámení z `CMFCPopupMenu` objekty, které patří do okna rámce při `CMFCPopupMenu` objekt zpracovává zprávu WM_DESTROY.

##  <a name="onmoveminiframe"></a>  CDockingManager::OnMoveMiniFrame

Volá se rozhraním, aby přesunout okno s minirámcem.

```
virtual BOOL OnMoveMiniFrame(CWnd* pFrame);
```

### <a name="parameters"></a>Parametry

*pFrame*<br/>
[in] Ukazatel na okno s minirámcem.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud metoda uspěje; v opačném případě FALSE.

##  <a name="onpanecontextmenu"></a>  CDockingManager::OnPaneContextMenu

Volá se rozhraním, když sestavení nabídka, která obsahuje seznam podoken.

```
void OnPaneContextMenu(CPoint point);
```

### <a name="parameters"></a>Parametry

*point*<br/>
[in] Určuje umístění v nabídce.

##  <a name="panefrompoint"></a>  CDockingManager::PaneFromPoint

Vrátí podokno obsahující časovém okamžiku.

```
virtual CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    bool bExactBar = false,
    CRuntimeClass* pRTCBarType = NULL,
    BOOL bCheckVisibility = FALSE,
    const CBasePane* pBarToIgnore = NULL) const;

virtual CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    DWORD& dwAlignment,
    CRuntimeClass* pRTCBarType = NULL,
    const CBasePane* pBarToIgnore = NULL) const;
```

### <a name="parameters"></a>Parametry

*point*<br/>
[in] Určuje bod, v souřadnicovém systému obrazovky, chcete-li zkontrolovat.

*nSensitivity*<br/>
[in] Hodnota určená k rozšiřování obdélníku každý kontrolovaný stavového řádku okna. Podokno splňuje kritéria hledání, pokud daný bod je v této oblasti zvýšeným.

*bExactBar*<br/>
[in] Hodnota TRUE pro ignorování *nSensitivity* parametr; jinak hodnota FALSE.

*pRTCBarType*<br/>
[in] Pokud není NULL, tato metoda vyhledá pouze podokna zadaného typu.

*bCheckVisibility*<br/>
[in] TRUE, pokud chcete zkontrolovat jenom viditelné podokna; v opačném případě hodnota FALSE.

*dwAlignment*<br/>
[out] Pokud podokno se nachází zde zadaný bod, tento parametr obsahuje straně podokna, která je nejblíž k určitému bodu. Další informace najdete v části poznámky.

*pBarToIgnore*<br/>
[in] Pokud není NULL, metoda ignoruje podokna zadána tímto parametrem.

### <a name="return-value"></a>Návratová hodnota

[Cbasepane –](../../mfc/reference/cbasepane-class.md)-objektu, který obsahuje časovém okamžiku nebo hodnota NULL, pokud nebyla nalezena žádná podokně.

### <a name="remarks"></a>Poznámky

Když funkce vrátí hodnotu, ale na stavového řádku se nenašla, *dwAlignment* obsahuje zarovnání Zadaný bod. Například, pokud je bod byl co nejblíže k hornímu okraji v podokně *dwAlignment* je nastavena na CBRS_ALIGN_TOP.

##  <a name="processpanecontextmenucommand"></a>  CDockingManager::ProcessPaneContextMenuCommand

Volá se rozhraním, chcete-li vybrat nebo a zrušte zaškrtnutí políčka pro zadaný příkaz Přepočítat rozložení je vidět podokno.

```
BOOL ProcessPaneContextMenuCommand(
    UINT nID,
    int nCode,
    void* pExtra,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
[in] Id ovládacího prvku panelu v nabídce.

*nCode*<br/>
[in] Kód upozornění příkazu.

*pExtra*<br/>
[in] Ukazatel na void, která je převedena na ukazatele na `CCmdUI` Pokud *nCode* je CN_UPDATE_COMMAND_UI.

*pHandlerInfo*<br/>
[in] Ukazatel na strukturu informace. Tento parametr není používán.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE v případě *pEXtra* nemá hodnotu NULL a *nCode* rovná CN_UPDATE_COMMAND_UI, nebo pokud není ovládací panel se zadaným *nID*.

##  <a name="recalclayout"></a>  CDockingManager::RecalcLayout

Přepočítá rozložení vnitřní ovládací prvky, které jsou k dispozici v seznamu ovládacích prvků.

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Parametry

*bNotify*<br/>
[in] Tento parametr se nepoužívá.

##  <a name="releaseemptypanecontainers"></a>  CDockingManager::ReleaseEmptyPaneContainers

Uvolní prázdné podokno kontejnery.

```
void ReleaseEmptyPaneContainers();
```

##  <a name="removehiddenmditabbedbar"></a>  CDockingManager::RemoveHiddenMDITabbedBar

Odebere zadaný skrytý panelu podokně.

```
void RemoveHiddenMDITabbedBar(CDockablePane* pBar);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[in] Ukazatel na panel podokně odebrat.

##  <a name="removeminiframe"></a>  CDockingManager::RemoveMiniFrame

Odebere ze seznamu mini snímků zadaného rámce.

```
virtual BOOL RemoveMiniFrame(CPaneFrameWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
[in] Ukazatel na objekt frame, který odebrat.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je odebrán zadaného rámce; FALSE v opačném případě.

##  <a name="removepanefromdockmanager"></a>  CDockingManager::RemovePaneFromDockManager

Zruší registraci na stavového řádku a odebere ze seznamu ve Správci ukotvení.

```
void RemovePaneFromDockManager(
    CBasePane* pWnd,
    BOOL bDestroy,
    BOOL bAdjustLayout,
    BOOL bAutoHide = FALSE,
    CBasePane* pBarReplacement = NULL);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
[in] Ukazatel na podokno, které má být odebrán.

*bDestroy*<br/>
[in] Při hodnotě TRUE je zničen podokně odebrané.

*bAdjustLayout*<br/>
[in] Pokud je hodnota TRUE, upravte okamžitě dokovací rozložení.

*bAutoHide*<br/>
[in] Při hodnotě TRUE se v podokně je odebrán ze seznamu automatické skrývání pruhy. Pokud má hodnotu FALSE, v podokně je odebrán ze seznamu regulární podoken.

*pBarReplacement*<br/>
[in] Ukazatel na stavového řádku, který nahrazuje podokně odebrané.

##  <a name="replacepane"></a>  CDockingManager::ReplacePane

Nahradí jiným jedno podokno.

```
BOOL ReplacePane(
    CDockablePane* pOriginalBar,
    CDockablePane* pNewBar);
```

### <a name="parameters"></a>Parametry

*pOriginalBar*<br/>
[in] Ukazatel na původní podokně.

*pNewBar*<br/>
[in] Ukazatel na podokno, které nahradí původní podokně.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud se v podokně se úspěšně nahradí; FALSE v opačném případě.

##  <a name="resortminiframesforzorder"></a>  CDockingManager::ResortMiniFramesForZOrder

Používat rámce v seznamu mini snímků.

```
void ResortMiniFramesForZOrder();
```

##  <a name="savestate"></a>  CDockingManager::SaveState

Uloží stav dokovací správce do registru.

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[in] Cesta ke klíči registru.

*uiID*<br/>
[in] Ukotvení ID správce.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud státu byla uložena úspěšně; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Ukládání stavu dokovací správce do registru zahrnuje ukládání stavů ovládací pruhy, stavy automatické skrývání pruhy a stavy mini rámce v dokovací správce.

##  <a name="sendmessagetominiframes"></a>  CDockingManager::SendMessageToMiniFrames

Odešle určenou zprávu na všechny mini snímky.

```
BOOL SendMessageToMiniFrames(
    UINT uMessage,
    WPARAM wParam = 0,
    LPARAM lParam = 0);
```

### <a name="parameters"></a>Parametry

*uMessage*<br/>
[in] Zprávy k odeslání.

*wParam*<br/>
[in] Informace závislé další zpráva.

*lParam*<br/>
[in] Informace závislé další zpráva.

### <a name="return-value"></a>Návratová hodnota

Vždy TRUE.

##  <a name="serialize"></a>  CDockingManager::Serialize

Ukotvení správce zapíše do archivu.

```
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*ar*<br/>
[in] Odkaz na objekt archivu.

### <a name="remarks"></a>Poznámky

Zápis dokovací správce do archivu zahrnuje určení počtu ukotvení ovládacích pruhů a posuvníky a zápis do archivu ovládací pruhy, minimální počet snímků, automatické skrývání pruhů a panely s kartami MDI.

##  <a name="setautohidezorder"></a>  CDockingManager::SetAutohideZOrder

Nastaví velikost, šířku a výšku ovládacích pruhů a podokna zadané.

```
void SetAutohideZOrder(CDockablePane* pAHDockingBar);
```

### <a name="parameters"></a>Parametry

*pAHDockingBar*<br/>
[in] Ukazatel na ukotvitelné stavového řádku.

##  <a name="setdockingmode"></a>  CDockingManager::SetDockingMode

Nastaví režim ukotvení.

```
static void SetDockingMode(
    AFX_DOCK_TYPE dockMode,
    AFX_SMARTDOCK_THEME theme = AFX_SDT_DEFAULT);
```

### <a name="parameters"></a>Parametry

*dockMode*<br/>
Určuje nový režim ukotvení. Další informace najdete v části poznámky.

*Motiv*<br/>
Určuje motivu, který se použije pro značek inteligentního dokování. Může být jeden z následujících hodnot výčtu: AFX_SDT_DEFAULT, AFX_SDT_VS2005, AFX_SDT_VS2008.

### <a name="remarks"></a>Poznámky

Voláním této metody statické nastavte režim na ukotvení.

*dockMode* může být jedna z následujících hodnot:

- DT_STANDARD – standardní režim ukotvení jako implementováno ve Visual Studio .NET 2003. Podokna jsou kvůli usnadnění použití vypsány bez přetahování kontextu.

- DT_IMMEDIATE – přímý režim ukotvení jako implementovaná v aplikaci Microsoft Visio. Podokna jsou kvůli usnadnění použití vypsány pomocí přetahování kontextu, ale budou zobrazeny žádné značky.

- DT_SMART – inteligentní dokovací režimu jako implementovaná v sadě Visual Studio 2005. Podokna jsou kvůli usnadnění použití vypsány pomocí přetahování kontextu a inteligentní značky jsou zobrazeny, které uvádí, kde lze ukotvit v podokně.

##  <a name="setdockstate"></a>  CDockingManager::SetDockState

Nastaví stav dokovací ovládací pruhy, mini snímků a panelů automaticky skrývat.

```
virtual void SetDockState();
```

##  <a name="setprintpreviewmode"></a>  CDockingManager::SetPrintPreviewMode

Nastaví režim náhledu tisku pruhy, které se zobrazí v náhledu tisku.

```
void SetPrintPreviewMode(
    BOOL bPreview,
    CPrintPreviewState* pState);
```

### <a name="parameters"></a>Parametry

*bPreview*<br/>
[in] Hodnota TRUE, pokud má nastaven režim náhledu tisku; FALSE v opačném případě.

*pState*<br/>
[in] Ukazatel na stav ve verzi preview. Tento parametr není používán.

##  <a name="setsmartdockingparams"></a>  CDockingManager::SetSmartDockingParams

Nastaví parametry, které definují chování inteligentního dokování.

```
static void SetSmartDockingParams(CSmartDockingInfo& params);
```

### <a name="parameters"></a>Parametry

*params*<br/>
[out v] Definuje parametry pro inteligentního dokování.

### <a name="remarks"></a>Poznámky

Pokud chcete přizpůsobit vzhled, barvy a tvar značek inteligentního dokování volání této metody.

Chcete-li použít výchozí vzhled značek inteligentního dokování, předejte neinicializované instance [csmartdockinginfo – třída](../../mfc/reference/csmartdockinginfo-class.md) k *params*.

##  <a name="showdelayshowminiframes"></a>  CDockingManager::ShowDelayShowMiniFrames

Zobrazí nebo skryje windows mini snímků.

```
void ShowDelayShowMiniFrames(BOOL bshow);
```

### <a name="parameters"></a>Parametry

*bShow*<br/>
[in] TRUE, pokud chcete aktivovat okno rámce je vidět; FALSE, pokud chcete skrýt okno rámce.

##  <a name="showpanes"></a>  CDockingManager::ShowPanes

Zobrazí nebo skryje podokna ovládacího prvku a automatické skrývání pruhy.

```
virtual BOOL ShowPanes(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bShow*<br/>
[in] TRUE, pokud chcete zobrazit podokna; FALSE pro skrytí podokna.

### <a name="return-value"></a>Návratová hodnota

Vždy hodnotu FALSE.

##  <a name="startsdocking"></a>  CDockingManager::StartSDocking

Spustí se inteligentního dokování určené okno podle zarovnání smart manager ukotvení.

```
void StartSDocking(CWnd* pDockingWnd);
```

### <a name="parameters"></a>Parametry

*pDockingWnd*<br/>
[in] Ukazatel na okno ukotvení.

##  <a name="stopsdocking"></a>  CDockingManager::StopSDocking

Zastaví připojení inteligentního dokování.

```
void StopSDocking();
```

##  <a name="getsmartdockingtheme"></a>  CDockingManager::GetSmartDockingTheme

Statická metoda, která vrací motiv, který slouží k zobrazení značek inteligentního dokování.

```
static AFX_SMARTDOCK_THEME __stdcall GetSmartDockingTheme();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí jednu z následujících hodnot výčtu: AFX_SDT_DEFAULT, AFX_SDT_VS2005, AFX_SDT_VS2008.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[CFrameWndEx – třída](../../mfc/reference/cframewndex-class.md)<br/>
[CDockablePane – třída](../../mfc/reference/cdockablepane-class.md)<br/>
[CPaneFrameWnd – třída](../../mfc/reference/cpaneframewnd-class.md)
