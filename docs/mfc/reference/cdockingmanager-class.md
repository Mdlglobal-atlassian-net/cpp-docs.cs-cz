---
title: CDockingManager – třída
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
ms.openlocfilehash: 8709b3a4eb3f57a3d2700ad7aaed16df994245c5
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420468"
---
# <a name="cdockingmanager-class"></a>CDockingManager – třída

Implementuje základní funkce, které řídí ukotvení rozložení v hlavním okně rámce.

## <a name="syntax"></a>Syntaxe

```
class CDockingManager : public CObject
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDockingManager::AddDockSite](#adddocksite)|Vytvoří ukotvené podokno a přidá ho do seznamu ovládacích panelů.|
|[CDockingManager::AddHiddenMDITabbedBar](#addhiddenmditabbedbar)|Přidá popisovač do podokna pruhů do seznamu skrytých podoken panelu MDI.|
|[CDockingManager::AddMiniFrame](#addminiframe)|Přidá rámeček do seznamu Mini rámců.|
|[CDockingManager::AddPane](#addpane)|Zaregistruje podokno pomocí Správce Docker.|
|[CDockingManager::AdjustDockingLayout](#adjustdockinglayout)|Přepočítá a upraví rozložení všech podoken v okně rámce.|
|[CDockingManager::AdjustPaneFrames](#adjustpaneframes)|Způsobí odeslání zprávy WM_NCCALCSIZE do všech podoken a `CPaneFrameWnd` oken.|
|[CDockingManager::AdjustRectToClientArea](#adjustrecttoclientarea)|Upraví zarovnání obdélníku.|
|[CDockingManager::AlignAutoHidePane](#alignautohidepane)|Změní velikost ukotveného podokna v režimu automatické skrývání tak, aby postaral o celou šířku nebo výšku klientské oblasti rámce, která je ohraničena Docky lokalitami.|
|[CDockingManager::AutoHidePane](#autohidepane)|Vytvoří panel nástrojů pro automatické skrývání.|
|[CDockingManager::BringBarsToTop](#bringbarstotop)|Přinese ukotvené pruhy, které mají zadané zarovnání na začátek.|
|[CDockingManager::BuildPanesMenu](#buildpanesmenu)|Přidá do nabídky názvy ukotvených podoken a panelů nástrojů.|
|[CDockingManager::CalcExpectedDockedRect](#calcexpecteddockedrect)|Vypočítá očekávaný obdélník ukotveného okna.|
|[CDockingManager:: Create](#create)|Vytvoří správce Docker.|
|[CDockingManager::D eterminePaneAndStatus](#determinepaneandstatus)|Určuje podokno, které obsahuje daný bod a stav jeho ukotvení.|
|[CDockingManager::D isableRestoreDockState](#disablerestoredockstate)|Povolí nebo zakáže načtení ukotveného rozložení z registru.|
|[CDockingManager::D ockPane](#dockpane)|Ukotví podokno do jiného podokna nebo okna rámce.|
|[CDockingManager::D ockPaneLeftOf](#dockpaneleftof)|Ukotví podokno nalevo od jiného podokna.|
|[CDockingManager::EnableAutoHidePanes](#enableautohidepanes)|Povoluje ukotvení podokna do hlavního rámce, vytvoří ukotvené podokno a přidá jej do seznamu ovládacích panelů.|
|[CDockingManager::EnableDocking](#enabledocking)|Vytvoří ukotvené podokno a povolí ukotvení podokna do hlavního rámce.|
|[CDockingManager::EnableDockSiteMenu](#enabledocksitemenu)|Zobrazí další tlačítko, které otevře místní nabídku s titulky všech ukotvených podoken.|
|[CDockingManager::EnablePaneContextMenu](#enablepanecontextmenu)|Instruuje knihovnu, aby zobrazila speciální kontextovou nabídku, která má seznam panelů nástrojů aplikace a ukotvených podoken, když uživatel klikne pravým tlačítkem myši a knihovna zpracovává zprávu WM_CONTEXTMENU.|
|[CDockingManager::FindDockSite](#finddocksite)|Načte podokno panelu, které je na zadané pozici a které má zadané zarovnání.|
|[CDockingManager::FindDockSiteByPane](#finddocksitebypane)|Vrátí podokno panelu, které má ID podokna cílového řádku.|
|[CDockingManager::FindPaneByID](#findpanebyid)|Najde podokno podle zadaného ID ovládacího prvku.|
|[CDockingManager::FixupVirtualRects](#fixupvirtualrects)|Potvrdí všechny aktuální pozice panelu nástrojů na virtuální obdélníky.|
|[CDockingManager::FrameFromPoint](#framefrompoint)|Vrátí rámec, který obsahuje daný bod.|
|[CDockingManager::GetClientAreaBounds](#getclientareabounds)|Získá obdélník obsahující hranice oblasti klienta.|
|[CDockingManager::GetDockingMode](#getdockingmode)|Vrátí aktuální režim ukotvení.|
|[CDockingManager::GetDockSiteFrameWnd](#getdocksiteframewnd)|Získá ukazatel na nadřazený rámec okna.|
|[CDockingManager::GetEnabledAutoHideAlignment](#getenabledautohidealignment)|Vrátí povolené zarovnání podoken.|
|[CDockingManager::GetMiniFrames](#getminiframes)|Načte seznam miniframes.|
|[CDockingManager::GetOuterEdgeBounds](#getouteredgebounds)|Získá obdélník, který obsahuje vnější okraje rámečku.|
|[CDockingManager:: getPanel](#getpanelist)|Vrátí seznam podoken, které patří do správce Docker. To zahrnuje všechna plovoucí podokna.|
|[CDockingManager::GetSmartDockingManager](#getsmartdockingmanager)|Načte ukazatel na správce inteligentního dokování.|
|[CDockingManager::GetSmartDockingManagerPermanent](#getsmartdockingmanagerpermanent)|Načte ukazatel na správce inteligentního dokování.|
|[CDockingManager::GetSmartDockingParams](#getsmartdockingparams)|Vrátí parametry inteligentního Docker pro správce Docker.|
|[CDockingManager::GetSmartDockingTheme](#getsmartdockingtheme)|Statická metoda, která vrací motiv používaný k zobrazení značek inteligentního Docker.|
|[CDockingManager::HideAutoHidePanes](#hideautohidepanes)|Skryje podokno, které je v režimu automatické skrývání.|
|[CDockingManager::InsertDockSite](#insertdocksite)|Vytvoří ukotvené podokno a vloží ho do seznamu ovládacích panelů.|
|[CDockingManager::InsertPane](#insertpane)|Vloží ovládací podokno do seznamu ovládacích panelů.|
|[CDockingManager::IsDockSiteMenu](#isdocksitemenu)|Určuje, zda se v popiscích všech podoken zobrazí místní nabídka.|
|[CDockingManager::IsInAdjustLayout](#isinadjustlayout)|Určuje, zda jsou upravena rozložení všech podoken.|
|[CDockingManager::IsOLEContainerMode](#isolecontainermode)|Určuje, zda je správce Docker v režimu kontejnerů OLE.|
|[CDockingManager::IsPointNearDockSite](#ispointneardocksite)|Určuje, zda je zadaný bod poblíž webu Dock.|
|[CDockingManager::IsPrintPreviewValid](#isprintpreviewvalid)|Určuje, zda je nastaven režim náhledu tisku.|
|[CDockingManager:: LoadState](#loadstate)|Načte stav správce Docker z registru.|
|[CDockingManager::LockUpdate](#lockupdate)|Zamkne dané okno.|
|[CDockingManager::OnActivateFrame](#onactivateframe)|Volá se rozhraním, když je aktivní okno rámce nebo je deaktivované.|
|[CDockingManager::OnClosePopupMenu](#onclosepopupmenu)|Volá se rozhraním, když aktivní místní nabídka zpracuje zprávu WM_DESTROY.|
|[CDockingManager::OnMoveMiniFrame](#onmoveminiframe)|Volá se rozhraním, aby se přesunulo okno s minimálním rámcem.|
|[CDockingManager::OnPaneContextMenu](#onpanecontextmenu)|Volá se rozhraním, když se vytvoří nabídka, která má seznam podoken.|
|[CDockingManager::P aneFromPoint](#panefrompoint)|Vrátí podokno, které obsahuje daný bod.|
|[CDockingManager::P rocessPaneContextMenuCommand](#processpanecontextmenucommand)|Volá se rozhraním pro výběr nebo zrušení zaškrtnutí políčka pro zadaný příkaz a přepočítání rozložení zobrazeného podokna.|
|[CDockingManager::RecalcLayout](#recalclayout)|Přepočítá interní rozložení ovládacích prvků, které jsou k dispozici v seznamu ovládacích prvků.|
|[CDockingManager::ReleaseEmptyPaneContainers](#releaseemptypanecontainers)|Uvolní prázdné kontejnery podokna.|
|[CDockingManager::RemoveHiddenMDITabbedBar](#removehiddenmditabbedbar)|Odebere zadané skryté podokno pruhů.|
|[CDockingManager::RemoveMiniFrame](#removeminiframe)|Odebere zadaný snímek ze seznamu Mini rámců.|
|[CDockingManager::RemovePaneFromDockManager](#removepanefromdockmanager)|Zruší registraci podokna a odebere ho ze seznamu v Docker Manageru.|
|[CDockingManager::ReplacePane](#replacepane)|Nahradí jedno podokno jiným.|
|[CDockingManager::ResortMiniFramesForZOrder](#resortminiframesforzorder)|Rozrekreační snímky v seznamu Mini rámců.|
|[CDockingManager:: SaveState](#savestate)|Uloží stav správce Docker do registru.|
|[CDockingManager::SendMessageToMiniFrames](#sendmessagetominiframes)|Odešle zadanou zprávu do všech Mini rámců.|
|[CDockingManager:: serializovat](#serialize)|Zapíše správce Docker do archivu. (Overrides [CObject:: serializovat](../../mfc/reference/cobject-class.md#serialize).)|
|[CDockingManager::SetAutohideZOrder](#setautohidezorder)|Nastaví velikost, šířku a výšku ovládacích panelů a určeného podokna.|
|[CDockingManager::SetDockingMode](#setdockingmode)|Nastaví režim uchycení.|
|[CDockingManager::SetDockState](#setdockstate)|Nastaví stav ukotvení řídicích panelů, minimálních rámců a panelů pro automatické skrývání.|
|[CDockingManager::SetPrintPreviewMode](#setprintpreviewmode)|Nastaví režim náhledu tisku pruhů, které se zobrazují v náhledu tisku.|
|[CDockingManager::SetSmartDockingParams](#setsmartdockingparams)|Nastaví parametry, které definují chování inteligentního docking.|
|[CDockingManager::ShowDelayShowMiniFrames](#showdelayshowminiframes)|Zobrazí nebo skryje okna mini rámců.|
|[CDockingManager::ShowPanes](#showpanes)|Zobrazí nebo skryje podokna ovládacího prvku a automaticky skrývat pruhy.|
|[CDockingManager::StartSDocking](#startsdocking)|Spustí inteligentní Docker zadaného okna podle zarovnání správce inteligentního dokování.|
|[CDockingManager::StopSDocking](#stopsdocking)|Zastaví inteligentní Docker.|

### <a name="data-members"></a>Datové členy

|Název|Popis|
|----------|-----------------|
|[CDockingManager:: m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode)|Určuje, zda správce Docker skryje podokna v režimu kontejnerů OLE.|
|[CDockingManager:: m_dockModeGlobal](#m_dockmodeglobal)|Určuje globální režim uchycení.|
|[CDockingManager:: m_nDockSensitivity](#m_ndocksensitivity)|Určuje citlivost ukotvení.|
|[CDockingManager:: m_nTimeOutBeforeDockingBarDock](#m_ntimeoutbeforedockingbardock)|Určuje dobu v milisekundách, po jejímž uplynutí je ukotvené podokno v režimu okamžitého ukotvení.|
|[CDockingManager:: m_nTimeOutBeforeToolBarDock](#m_ntimeoutbeforetoolbardock)|Určuje čas (v milisekundách), po kterém je panel nástrojů ukotven do hlavního okna rámce.|

## <a name="remarks"></a>Poznámky

Hlavní okno rámce vytvoří a automaticky Inicializuje tuto třídu.

Objekt správce Docker obsahuje seznam všech podoken, která jsou v ukotveném rozložení, a také seznam všech oken [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) , která patří do hlavního okna rámce.

Třída `CDockingManager` implementuje některé služby, které můžete použít k vyhledání podokna nebo `CPaneFrameWnd`ho okna. Tyto služby obvykle nebudete volat přímo, protože jsou zabaleny do objektu okna hlavního rámce. Další informace naleznete v tématu [Třída CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md).

## <a name="customization-tips"></a>Tipy pro přizpůsobení

Následující tipy se vztahují na `CDockingManager` objekty:

- [Třída CDockingManager](../../mfc/reference/cdockingmanager-class.md) podporuje tyto režimy ukotvení:

  - `AFX_DOCK_TYPE::DT_IMMEDIATE`

  - `AFX_DOCK_TYPE::DT_STANDARD`

  - `AFX_DOCK_TYPE::DT_SMART`

  Tyto režimy ukotvení jsou definovány pomocí [CDockingManager:: m_dockModeGlobal](#m_dockmodeglobal) a jsou nastaveny pomocí volání [CDockingManager:: SetDockingMode](#setdockingmode).

- Pokud chcete vytvořit neplovoucí podokno bez změny velikosti, zavolejte metodu [CDockingManager:: AddPane](#addpane) . Tato metoda registruje podokno pomocí Správce docking, který je zodpovědný za rozložení podokna.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít různé metody ve třídě `CDockingManager` ke konfiguraci objektu `CDockingManager`. Příklad ukazuje, jak zobrazit další tlačítko, které otevře místní nabídku na titulky všech ukotvených podoken a jak nastavit režim ukotvení objektu. Tento fragment kódu je součástí [ukázkového vzorku sady Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#24](../../mfc/codesnippet/cpp/cdockingmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CDockingManager](../../mfc/reference/cdockingmanager-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxDockingManager. h

##  <a name="adddocksite"></a>CDockingManager::AddDockSite

Vytvoří ukotvené podokno a přidá ho do seznamu ovládacích panelů.

```
BOOL AddDockSite(
    const AFX_DOCKSITE_INFO& info,
    CDockSite** ppDockBar = NULL);
```

### <a name="parameters"></a>Parametry

*příjemce*<br/>
pro Odkaz na strukturu informací, která obsahuje zarovnání ukotveného podokna.

*ppDockBar*<br/>
mimo Ukazatel na ukazatel na nové ukotvené podokno.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud bylo ukotvené podokno úspěšně vytvořeno; V opačném případě NEPRAVDA.

##  <a name="addhiddenmditabbedbar"></a>CDockingManager::AddHiddenMDITabbedBar

Přidá popisovač do podokna pruhů do seznamu skrytých podoken panelu MDI.

```
void AddHiddenMDITabbedBar(CDockablePane* pBar);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
pro Ukazatel na podokno pruhů

##  <a name="addpane"></a>CDockingManager::AddPane

Zaregistruje podokno pomocí Správce Docker.

```
BOOL AddPane(
    CBasePane* pWnd,
    BOOL bTail = TRUE,
    BOOL bAutoHide = FALSE,
    BOOL bInsertForOuterEdge = FALSE);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
[in, out] Určuje podokno, které se má přidat do správce Docker.

*bTail*<br/>
pro TRUE pro přidání podokna na konec seznamu podoken pro Docker Manager; v opačném případě FALSE.

*bAutoHide*<br/>
pro Pouze pro interní použití. Vždy použít výchozí hodnotu FALSE.

*bInsertForOuterEdge*<br/>
pro Pouze pro interní použití. Vždy použít výchozí hodnotu FALSE.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se podokno úspěšně zaregistrovalo u správce docking; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Voláním této metody zaregistrujete neplovoucí podokna bez změny velikosti pomocí Správce Docker. Pokud tato podokna nezaregistrujete, nezobrazí se správně, když je program Docker rozložen.

##  <a name="adjustdockinglayout"></a>CDockingManager::AdjustDockingLayout

Přepočítá a upraví rozložení všech podoken v okně rámce.

```
virtual void AdjustDockingLayout(HDWP hdwp = NULL);
```

### <a name="parameters"></a>Parametry

*hdwp*<br/>
pro Určuje strukturu umístění odloženého okna. Další informace najdete v tématu [datové typy Windows](/windows/win32/WinProg/windows-data-types).

### <a name="remarks"></a>Poznámky

##  <a name="addminiframe"></a>CDockingManager::AddMiniFrame

Přidá rámeček do seznamu Mini rámců.

```
virtual BOOL AddMiniFrame(CPaneFrameWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
pro Ukazatel na snímek.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se rámec nenachází v seznamu Mini rámců a byl úspěšně přidán; V opačném případě NEPRAVDA.

##  <a name="adjustpaneframes"></a>CDockingManager::AdjustPaneFrames

Způsobí odeslání zprávy WM_NCCALCSIZE do všech podoken a `CPaneFrameWnd` oken.

```
virtual void AdjustPaneFrames();
```

### <a name="remarks"></a>Poznámky

##  <a name="adjustrecttoclientarea"></a>CDockingManager::AdjustRectToClientArea

Upraví zarovnání obdélníku.

```
virtual BOOL AdjustRectToClientArea(
    CRect& rectResult,
    DWORD dwAlignment);
```

### <a name="parameters"></a>Parametry

*rectResult*<br/>
pro Odkaz na objekt `CRect`

*dwAlignment*<br/>
pro Zarovnání objektu `CRect`

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud bylo upraveno zarovnání objektu `CRect`; V opačném případě NEPRAVDA.

### <a name="remarks"></a>Poznámky

Parametr *dwAlignment* může mít jednu z následujících hodnot:

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

##  <a name="alignautohidepane"></a>CDockingManager::AlignAutoHidePane

Změní velikost ukotveného podokna v režimu automatické skrývání tak, aby postaral o celou šířku nebo výšku klientské oblasti rámce, která je ohraničena Docky lokalitami.

```
void AlignAutoHidePane(
    CPaneDivider* pDefaultSlider,
    BOOL bIsVisible = TRUE);
```

### <a name="parameters"></a>Parametry

*pDefaultSlider*<br/>
pro Podokno posuvník ukotvení.

*bIsVisible*<br/>
pro TRUE, pokud je ukotvené podokno viditelné; V opačném případě NEPRAVDA.

##  <a name="autohidepane"></a>CDockingManager::AutoHidePane

Vytvoří panel nástrojů pro automatické skrývání.

```
CMFCAutoHideToolBar* AutoHidePane(
    CDockablePane* pBar,
    CMFCAutoHideToolBar* pCurrAutoHideToolBar = NULL);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
pro Ukazatel na podokno pruhů.

*pCurrAutoHideToolBar*<br/>
pro Ukazatel na panel nástrojů pro automatické skrývání.

### <a name="return-value"></a>Návratová hodnota

Hodnota NULL, pokud nebyl vytvořen panel nástrojů automaticky schovávat; v opačném případě ukazatel na nový panel nástrojů.

##  <a name="bringbarstotop"></a>CDockingManager::BringBarsToTop

Přinese ukotvené pruhy, které mají zadané zarovnání na začátek.

```
void BringBarsToTop(
    DWORD dwAlignment = 0,
    BOOL bExcludeDockedBars = TRUE);
```

### <a name="parameters"></a>Parametry

*dwAlignment*<br/>
pro Zarovnání ukotvených pruhů, které jsou umístěny v horní části ostatních oken.

*bExcludeDockedBars*<br/>
pro TRUE pro vyloučení ukotvených pruhů shora; v opačném případě FALSE.

##  <a name="buildpanesmenu"></a>CDockingManager::BuildPanesMenu

Přidá do nabídky názvy ukotvených podoken a panelů nástrojů.

```
void BuildPanesMenu(
    CMenu& menu,
    BOOL bToolbarsOnly);
```

### <a name="parameters"></a>Parametry

*nabídce*<br/>
pro Nabídka pro přidání názvů ukotvených podoken a panelů nástrojů do.

*bToolbarsOnly*<br/>
pro TRUE, pokud chcete do nabídky přidat jenom názvy panelů nástrojů; V opačném případě NEPRAVDA.

##  <a name="calcexpecteddockedrect"></a>CDockingManager::CalcExpectedDockedRect

Vypočítá očekávaný obdélník ukotveného okna.

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
pro Ukazatel na ukotvení okna.

*ptMouse*<br/>
pro Umístění myši.

*rectResult*<br/>
mimo Počítaný obdélník.

*bDrawTab*<br/>
pro TRUE, pokud chcete nakreslit kartu; v opačném případě FALSE.

*ppTargetBar*<br/>
mimo Ukazatel na ukazatel na cílové podokno.

### <a name="remarks"></a>Poznámky

Tato metoda vypočítá obdélník, který by okno zabíralo, pokud uživatel přetáhl okno do bodu určeného parametrem *ptMouse* a jeho ukotvený tam.

##  <a name="create"></a>CDockingManager:: Create

Vytvoří správce Docker.

```
BOOL Create(CFrameWnd* pParentWnd);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
pro Ukazatel na nadřazený rámec správce ukotvení. Tato hodnota nesmí být NULL.

### <a name="return-value"></a>Návratová hodnota

Vždy TRUE.

##  <a name="determinepaneandstatus"></a>CDockingManager::D eterminePaneAndStatus

Určuje podokno, které obsahuje daný bod a stav jeho ukotvení.

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

*bodů*<br/>
pro Umístění podokna, které má být zkontrolováno.

*nSensitivity*<br/>
pro Hodnota, která zvětší obdélník okna v každém kontrolovaném podokně. Pokud je daný bod v této rozšířené oblasti, v podokně se vyhovuje kritéria hledání.

*dwEnabledAlignment*<br/>
pro Zarovnání ukotveného podokna.

*ppTargetBar*<br/>
mimo Ukazatel na ukazatel na cílové podokno.

*pBarToIgnore*<br/>
pro Podokno, které metoda ignoruje.

*pBarToDock*<br/>
pro Podokno, které je ukotveno.

### <a name="return-value"></a>Návratová hodnota

Stav ukotvení.

### <a name="remarks"></a>Poznámky

Stav ukotvení může být jedna z následujících hodnot:

|Hodnota AFX_CS_STATUS|Význam|
|---------------------------|-------------|
|CS_NOTHING|Ukazatel není nad dockou lokalitou. Proto nechejte podokno plovoucí.|
|CS_DOCK_IMMEDIATELY|Ukazatel se nachází nad dokovacím webem v přímém režimu (DT_IMMEDIATE styl je povolen), takže podokno musí být ukotveno okamžitě.|
|CS_DELAY_DOCK|Ukazatel je nad dockou lokalitou, která je v jiném dokovacím podokně, nebo je hranou hlavního rámce.|
|CS_DELAY_DOCK_TO_TAB|Ukazatel je nad dockou lokalitou, která způsobuje, že je podokno ukotveno v okně s kartami. K tomu dochází, když je ukazatel myši nad titulkem jiného ukotveného podokna nebo přes oblast karet podokna s kartami.|

##  <a name="disablerestoredockstate"></a>CDockingManager::D isableRestoreDockState

Povolí nebo zakáže načtení ukotveného rozložení z registru.

```
void DisableRestoreDockState(BOOL bDisable = TRUE);
```

### <a name="parameters"></a>Parametry

*bDisable*<br/>
pro TRUE pro zakázání načítání ukotveného rozložení z registru; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tuto metodu zavolejte, pokud při načítání stavu aplikace musíte zachovat aktuální rozložení ukotvených podoken a panelů nástrojů.

##  <a name="dockpane"></a>CDockingManager::D ockPane

Ukotví podokno do jiného podokna nebo okna rámce.

```
void DockPane(
    CBasePane* pBar,
    UINT nDockBarID = 0,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
pro Ukazatel na podokno pruhů, do kterého se má ukotvit.

*nDockBarID*<br/>
pro ID panelu, který se má ukotvit

*lpRect*<br/>
pro Cílový obdélník.

##  <a name="dockpaneleftof"></a>CDockingManager::D ockPaneLeftOf

Ukotví podokno nalevo od jiného podokna.

```
BOOL DockPaneLeftOf(
    CPane* pBarToDock,
    CPane* pTargetBar);
```

### <a name="parameters"></a>Parametry

*pBarToDock*<br/>
pro Ukazatel na panel, který se má ukotvit nalevo od *pTargetBar*.

*pTargetBar*<br/>
pro Ukazatel na cílové podokno.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud bylo podokno úspěšně ukotveno; v opačném případě FALSE.

##  <a name="enableautohidepanes"></a>CDockingManager::EnableAutoHidePanes

Povoluje ukotvení podokna do hlavního rámce, vytvoří ukotvené podokno a přidá jej do seznamu ovládacích panelů.

```
BOOL EnableAutoHidePanes(DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
pro Zarovnání ukotvení.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud bylo ukotvené podokno úspěšně vytvořeno; V opačném případě NEPRAVDA.

##  <a name="enabledocking"></a>CDockingManager::EnableDocking

Vytvoří ukotvené podokno a povolí ukotvení podokna do hlavního rámce.

```
BOOL EnableDocking(DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
pro Zarovnání ukotvení.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud bylo ukotvené podokno úspěšně vytvořeno; V opačném případě NEPRAVDA.

##  <a name="enabledocksitemenu"></a>CDockingManager::EnableDockSiteMenu

Zobrazí další tlačítko, které otevře místní nabídku s titulky všech ukotvených podoken.

```
static void EnableDockSiteMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
pro TRUE pro povolení nabídky ukotvit Web; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

V nabídce ukotvit web se zobrazí následující možnosti pro změnu stavu ukotvení podokna:

- `Floating` – Floatuje podokno

- `Docking` – ukotví podokno v hlavním rámci do umístění, kde bylo podokno naposledy ukotveno.

- `AutoHide` – přepne podokno do režimu automatického skrývání.

- `Hide` – skryje podokno.

Ve výchozím nastavení se tato nabídka nezobrazuje.

##  <a name="enablepanecontextmenu"></a>CDockingManager::EnablePaneContextMenu

Instruuje knihovnu, aby zobrazila speciální kontextovou nabídku, která má seznam panelů nástrojů aplikace a ukotvených podoken, když uživatel klikne pravým tlačítkem myši a knihovna zpracovává zprávu WM_CONTEXTMENU.

```
void EnablePaneContextMenu(
    BOOL bEnable,
    UINT uiCustomizeCmd,
    const CString& strCustomizeText,
    BOOL bToolbarsOnly = FALSE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
pro Pokud má hodnotu TRUE, knihovna zapne podporu pro automatickou kontextovou nabídku. Pokud je hodnota FALSE, knihovna vypne podporu pro automatickou kontextovou nabídku.

*uiCustomizeCmd*<br/>
pro ID příkazu pro **vlastní** položku v nabídce

*strCustomizeText*<br/>
pro Text položky pro **přizpůsobení**

*bToolbarsOnly*<br/>
pro V případě hodnoty TRUE se v nabídce zobrazí pouze seznam panelů nástrojů aplikace. Pokud je hodnota FALSE, knihovna přidá do tohoto seznamu podokna ukotvení aplikace.

##  <a name="finddocksite"></a>CDockingManager::FindDockSite

Načte podokno panelu, které je na zadané pozici a které má zadané zarovnání.

```
virtual CDockSite* FindDockSite(
    DWORD dwAlignment,
    BOOL bOuter);
```

### <a name="parameters"></a>Parametry

*dwAlignment*<br/>
pro Zarovnání podokna pruhů

*bOuter*<br/>
pro Je-li nastavena hodnota TRUE, načtěte v seznamu ovládacích panelů pruh na pozici hlavního panelu. V opačném případě načtěte pruh na koncové pozici v seznamu ovládacích panelů.

### <a name="return-value"></a>Návratová hodnota

Ukotvené podokno, které má zadané zarovnání; V opačném případě hodnota NULL.

##  <a name="findpanebyid"></a>CDockingManager::FindPaneByID

Najde podokno podle zadaného ID ovládacího prvku.

```
virtual CBasePane* FindPaneByID(
    UINT uBarID,
    BOOL bSearchMiniFrames = FALSE);
```

### <a name="parameters"></a>Parametry

*uBarID*<br/>
pro Určuje ID ovládacího prvku podokna, které se má najít.

*bSearchMiniFrames*<br/>
pro TRUE pro zahrnutí všech plovoucích podoken ve vyhledávání. FALSE pro zahrnutí pouze ukotvených podoken.

### <a name="return-value"></a>Návratová hodnota

Objekt [CBasePane](../../mfc/reference/cbasepane-class.md) , který má zadané ID ovládacího prvku, nebo hodnotu null, pokud nebylo nalezeno určené podokno.

### <a name="remarks"></a>Poznámky

##  <a name="finddocksitebypane"></a>CDockingManager::FindDockSiteByPane

Vrátí podokno panelu, které má ID podokna cílového řádku.

```
virtual CDockSite* FindDockSiteByPane(CPane* pTargetBar);
```

### <a name="parameters"></a>Parametry

*pTargetBar*<br/>
pro Ukazatel na cílové podokno panelu.

### <a name="return-value"></a>Návratová hodnota

Podokno panelu, které má ID podokna cílového panelu; Hodnota NULL, pokud takové podokno pruhů neexistuje.

##  <a name="fixupvirtualrects"></a>CDockingManager::FixupVirtualRects

Potvrdí všechny aktuální pozice panelu nástrojů na virtuální obdélníky.

```
virtual void FixupVirtualRects();
```

### <a name="remarks"></a>Poznámky

Když uživatel začne přetahovat panel nástrojů, aplikace si zapamatuje svou původní pozici ve *virtuálním obdélníku*. Když uživatel přesune panel nástrojů napříč jeho lokalitou Dock, panel nástrojů může přesunout další panely nástrojů. Původní pozice ostatních panelů nástrojů jsou uloženy v odpovídajících virtuálních obdélnících.

##  <a name="framefrompoint"></a>CDockingManager::FrameFromPoint

Vrátí rámec, který obsahuje daný bod.

```
virtual CPaneFrameWnd* FrameFromPoint(
    CPoint pt,
    CPaneFrameWnd* pFrameToExclude,
    BOOL bFloatMultiOnly) const;
```

### <a name="parameters"></a>Parametry

*bodů*<br/>
pro Určuje bod, který se má kontrolovat v souřadnicích obrazovky.

*pFrameToExclude*<br/>
pro Ukazatel na rámec, který má být vyloučen.

*bFloatMultiOnly*<br/>
pro TRUE pro vyloučení snímků, které nejsou instancemi `CMultiPaneFrameWnd`; V opačném případě NEPRAVDA.

### <a name="return-value"></a>Návratová hodnota

Rámec, který obsahuje daný bod; V opačném případě hodnota NULL.

##  <a name="getclientareabounds"></a>CDockingManager::GetClientAreaBounds

Získá obdélník obsahující hranice oblasti klienta.

```
CRect GetClientAreaBounds() const;

void GetClientAreaBounds(CRect& rcClient);
```

### <a name="parameters"></a>Parametry

*rcClient*<br/>
mimo Odkaz na obdélník obsahující hranice oblasti klienta.

### <a name="return-value"></a>Návratová hodnota

Obdélník obsahující hranice klientské oblasti.

##  <a name="getdockingmode"></a>CDockingManager::GetDockingMode

Vrátí aktuální režim ukotvení.

```
static AFX_DOCK_TYPE GetDockingMode();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota výčtu, která představuje aktuální režim ukotvení. Může to být jedna z následujících hodnot:

- DT_STANDARD

- DT_IMMEDIATE

- DT_SMART

### <a name="remarks"></a>Poznámky

Chcete-li nastavit režim uchycení, zavolejte [CDockingManager:: SetDockingMode](#setdockingmode).

##  <a name="getdocksiteframewnd"></a>CDockingManager::GetDockSiteFrameWnd

Získá ukazatel na nadřazený rámec okna.

```
CFrameWnd* GetDockSiteFrameWnd() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nadřazený rámec okna.

##  <a name="getenabledautohidealignment"></a>CDockingManager::GetEnabledAutoHideAlignment

Vrátí povolené zarovnání podoken.

```
DWORD GetEnabledAutoHideAlignment() const;
```

### <a name="return-value"></a>Návratová hodnota

Bitová kombinace příznaků CBRS_ALIGN_, nebo 0, pokud nejsou povolena podokna pro automatické skrývání. Další informace najdete v tématu [CFrameWnd:: EnableDocking](../../mfc/reference/cframewnd-class.md#enabledocking).

### <a name="remarks"></a>Poznámky

Metoda vrátí povolené zarovnání pro ovládací panely pro automatické skrývání. Chcete-li povolit automatické skrývání pruhů, zavolejte [CFrameWndEx:: EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes).

##  <a name="getminiframes"></a>CDockingManager::GetMiniFrames

Načte seznam miniframes.

```
const CObList& GetMiniFrames() const;
```

### <a name="return-value"></a>Návratová hodnota

Seznam miniframes, které obsahují ovládací panely, které patří do správce Docker.

##  <a name="getouteredgebounds"></a>CDockingManager::GetOuterEdgeBounds

Získá obdélník, který obsahuje vnější okraje rámečku.

```
CRect GetOuterEdgeBounds() const;
```

### <a name="return-value"></a>Návratová hodnota

Obdélník, který obsahuje vnější okraje rámečku.

##  <a name="getpanelist"></a>CDockingManager:: getPanel

Vrátí seznam podoken, které patří do správce Docker. To zahrnuje všechna plovoucí podokna.

```
void GetPaneList(
    CObList& lstBars,
    BOOL bIncludeAutohide = FALSE,
    CRuntimeClass* pRTCFilter = NULL,
    BOOL bIncludeTabs = FALSE);
```

### <a name="parameters"></a>Parametry

*lstBars*<br/>
[in, out] Obsahuje všechna podokna aktuálního Docker Manageru.

*bIncludeAutohide*<br/>
pro TRUE pro zahrnutí podoken, která jsou v režimu automatické skrývání; v opačném případě FALSE.

*pRTCFilter*<br/>
pro Pokud hodnota není NULL, vrácený seznam obsahuje podokna pouze zadané třídy modulu runtime.

*bIncludeTabs*<br/>
pro TRUE pro zahrnutí karet; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Pokud v Docker Manageru existují podoken s kartami, vrátí metoda ukazatel na objekty [třídy CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md) a je nutné explicitně vytvořit výčet karet.

Pomocí *pRTCFilter* získat konkrétní třídu podoken. Můžete například získat pouze panely nástrojů, a to tak, že nastavíte tuto hodnotu správně.

##  <a name="getsmartdockingmanager"></a>CDockingManager::GetSmartDockingManager

Načte ukazatel na správce inteligentního dokování.

```
CSmartDockingManager* GetSmartDockingManager();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na správce inteligentního dokování.

##  <a name="getsmartdockingmanagerpermanent"></a>CDockingManager::GetSmartDockingManagerPermanent

Načte ukazatel na správce inteligentního dokování.

```
CSmartDockingManager* GetSmartDockingManagerPermanent() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na správce inteligentního dokování.

##  <a name="getsmartdockingparams"></a>CDockingManager::GetSmartDockingParams

Vrátí parametry inteligentního Docker pro správce Docker.

```
static CSmartDockingInfo& GetSmartDockingParams();
```

### <a name="return-value"></a>Návratová hodnota

Třída, která obsahuje parametry inteligentního Docker pro aktuálního správce Docker. Další informace naleznete v tématu [Třída CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md).

### <a name="remarks"></a>Poznámky

##  <a name="hideautohidepanes"></a>CDockingManager::HideAutoHidePanes

Skryje podokno, které je v režimu automatické skrývání.

```
void HideAutoHidePanes(
    CDockablePane* pBarToExclude = NULL,
    BOOL bImmediately = FALSE);
```

### <a name="parameters"></a>Parametry

*pBarToExclude*<br/>
pro Ukazatel na pruh, který má být vyloučen z skrývání.

*bImmediately*<br/>
pro TRUE pro okamžité skrytí podokna; FALSE pro skrytí podokna s efektem skrývání.

##  <a name="insertdocksite"></a>CDockingManager::InsertDockSite

Vytvoří ukotvené podokno a vloží ho do seznamu ovládacích panelů.

```
BOOL InsertDockSite(
    const AFX_DOCKSITE_INFO& info,
    DWORD dwAlignToInsertAfter,
    CDockSite** ppDockBar = NULL);
```

### <a name="parameters"></a>Parametry

*příjemce*<br/>
pro Struktura, která obsahuje informace o zarovnání k podoknu Dock.

*dwAlignToInsertAfter*<br/>
pro Zarovnání podokna ukotvení

*ppDockBar*<br/>
mimo Ukazatel na ukazatel na ukotvené podokno.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud bylo ukotvené podokno úspěšně vytvořeno; V opačném případě NEPRAVDA.

##  <a name="insertpane"></a>CDockingManager::InsertPane

Vloží ovládací podokno do seznamu ovládacích panelů.

```
BOOL InsertPane(
    CBasePane* pControlBar,
    CBasePane* pTarget,
    BOOL bAfter = TRUE);
```

### <a name="parameters"></a>Parametry

*pControlBar*<br/>
pro Ukazatel na podokno ovládacího prvku.

*pTarget*<br/>
pro Ukazatel na cílové podokno.

*bAfter*<br/>
pro TRUE pro vložení podokna za pozici cílového podokna; V opačném případě NEPRAVDA.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je ovládací podokno úspěšně přidáno do seznamu ovládacích panelů; V opačném případě NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí hodnotu false, pokud je ovládací podokno již v seznamu ovládacích panelů nebo pokud cílové podokno neexistuje v seznamu ovládacích panelů.

##  <a name="isdocksitemenu"></a>CDockingManager::IsDockSiteMenu

Určuje, zda se v popiscích všech podoken zobrazí místní nabídka.

```
static BOOL IsDockSiteMenu();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se v nadpisech všech ukotvených podoken zobrazuje nabídka Dock site; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Nabídku Dock site můžete povolit voláním [CDockingManager:: EnableDockSiteMenu](#enabledocksitemenu).

##  <a name="isinadjustlayout"></a>CDockingManager::IsInAdjustLayout

Určuje, zda jsou upravena rozložení všech podoken.

```
BOOL IsInAdjustLayout() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se upraví rozložení všech podoken; V opačném případě NEPRAVDA.

##  <a name="isolecontainermode"></a>CDockingManager::IsOLEContainerMode

Určuje, zda je správce Docker v režimu kontejnerů OLE.

```
BOOL IsOLEContainerMode() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je správce Docker v režimu kontejnerů OLE; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

V režimu kontejnerů OLE jsou všechna ukotvená podokna a panely nástrojů aplikace skryté. Podokna jsou také skryta v tomto režimu, pokud jste nastavili [CDockingManager:: m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode) na hodnotu true.

##  <a name="ispointneardocksite"></a>CDockingManager::IsPointNearDockSite

Určuje, zda je zadaný bod poblíž webu Dock.

```
BOOL IsPointNearDockSite(
    CPoint point,
    DWORD& dwBarAlignment,
    BOOL& bOuterEdge) const;
```

### <a name="parameters"></a>Parametry

*Vyberte*<br/>
pro Zadaný bod.

*dwBarAlignment*<br/>
mimo Určuje, na který okraj se bod blíží. Možné hodnoty jsou CBRS_ALIGN_LEFT, CBRS_ALIGN_RIGHT, CBRS_ALIGN_TOP a CBRS_ALIGN_BOTTOM.

*bOuterEdge*<br/>
mimo TRUE, pokud je bod poblíž vnějšího ohraničení ukotveného webu; V opačném případě NEPRAVDA.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je bod poblíž dokovací lokality; v opačném případě FALSE.

##  <a name="isprintpreviewvalid"></a>CDockingManager::IsPrintPreviewValid

Určuje, zda je nastaven režim náhledu tisku.

```
BOOL IsPrintPreviewValid() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je nastaven režim náhledu tisku; V opačném případě NEPRAVDA.

##  <a name="loadstate"></a>CDockingManager:: LoadState

Načte stav správce Docker z registru.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
pro Název profilu

*uiID*<br/>
pro ID správce Docker

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se stav Docker Manageru úspěšně načetl; v opačném případě FALSE.

##  <a name="lockupdate"></a>CDockingManager::LockUpdate

Zamkne dané okno.

```
void LockUpdate(BOOL bLock);
```

### <a name="parameters"></a>Parametry

*Blokované*<br/>
pro TRUE, pokud je okno uzamčené; V opačném případě NEPRAVDA.

### <a name="remarks"></a>Poznámky

Když je okno uzamčené, nedá se přesunout a nedá se překreslit.

##  <a name="m_bhidedockingbarsincontainermode"></a>CDockingManager:: m_bHideDockingBarsInContainerMode

Určuje, zda správce Docker skryje podokna v režimu kontejnerů OLE.

```
AFX_IMPORT_DATA static BOOL m_bHideDockingBarsInContainerMode;
```

### <a name="remarks"></a>Poznámky

Nastavte tuto hodnotu na FALSE, pokud chcete zachovat všechna podokna ukotvená do hlavního rámce, když je aplikace v režimu kontejneru OLE. Ve výchozím nastavení je tato hodnota TRUE.

##  <a name="m_dockmodeglobal"></a>CDockingManager:: m_dockModeGlobal

Určuje globální režim uchycení.

```
AFX_IMPORT_DATA static AFX_DOCK_TYPE m_dockModeGlobal;
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení používá každý dokovací podokno tento režim ukotvení. Další informace o hodnotách, na které lze toto pole nastavit, naleznete v tématu [CBasePane:: GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode).

##  <a name="m_ndocksensitivity"></a>CDockingManager:: m_nDockSensitivity

Určuje citlivost ukotvení.

```
AFX_IMPORT_DATA static int m_nDockSensitivity;
```

### <a name="remarks"></a>Poznámky

Citlivost ukotvení definuje způsob, jakým se může plovoucí podokno přiblíží k dokovacímu podoknu, dokovacímu webu nebo jinému podoknu, než systém změní stav na ukotveno.

##  <a name="m_ntimeoutbeforedockingbardock"></a>CDockingManager:: m_nTimeOutBeforeDockingBarDock

Určuje dobu v milisekundách, po jejímž uplynutí je ukotvené podokno v režimu okamžitého ukotvení.

```
static UINT m_nTimeOutBeforeDockingBarDock;
```

### <a name="remarks"></a>Poznámky

Předtím, než je podokno ukotveno, rozhraní počká určenou dobu. Tím se zabrání nechtěnému ukotvení podokna do umístění, když ho uživatel stále přetáhne.

##  <a name="m_ntimeoutbeforetoolbardock"></a>CDockingManager:: m_nTimeOutBeforeToolBarDock

Určuje čas (v milisekundách), po kterém je panel nástrojů ukotven do hlavního okna rámce.

```
static UINT m_nTimeOutBeforeToolBarDock;
```

### <a name="remarks"></a>Poznámky

Předtím, než je panel nástrojů ukotven, systém počká zadanou dobu. Tím zabráníte nechtěnému ukotvení panelu nástrojů na místo, když ho uživatel stále přetáhne.

##  <a name="onactivateframe"></a>CDockingManager::OnActivateFrame

Volá se rozhraním, když je aktivní okno rámce nebo je deaktivované.

```
virtual void OnActivateFrame(BOOL bActivate);
```

### <a name="parameters"></a>Parametry

*bActivate*<br/>
pro Při hodnotě TRUE se okno rámce provede jako aktivní; v případě hodnoty FALSE dojde k deaktivaci okna rámce.

##  <a name="onclosepopupmenu"></a>CDockingManager::OnClosePopupMenu

Volá se rozhraním, když aktivní místní nabídka zpracuje zprávu WM_DESTROY.

```
void OnClosePopupMenu();
```

### <a name="remarks"></a>Poznámky

Rozhraní pošle WM_DESTROYovou zprávu, když se chystá Zavřít aktuální hlavní okno. Přepište tuto metodu pro zpracování oznámení z `CMFCPopupMenu` objektů, které patří do okna rámce, když objekt `CMFCPopupMenu` zpracovává zprávu WM_DESTROY.

##  <a name="onmoveminiframe"></a>CDockingManager::OnMoveMiniFrame

Volá se rozhraním, aby se přesunulo okno s minimálním rámcem.

```
virtual BOOL OnMoveMiniFrame(CWnd* pFrame);
```

### <a name="parameters"></a>Parametry

*pFrame*<br/>
pro Ukazatel na okno se zkráceným rámcem.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je metoda úspěšná; v opačném případě FALSE.

##  <a name="onpanecontextmenu"></a>CDockingManager::OnPaneContextMenu

Volá se rozhraním, když se vytvoří nabídka, která má seznam podoken.

```
void OnPaneContextMenu(CPoint point);
```

### <a name="parameters"></a>Parametry

*Vyberte*<br/>
pro Určuje umístění nabídky.

##  <a name="panefrompoint"></a>CDockingManager::P aneFromPoint

Vrátí podokno, které obsahuje daný bod.

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

*Vyberte*<br/>
pro Určuje bod, který se má kontrolovat v souřadnicích obrazovky.

*nSensitivity*<br/>
pro Hodnota pro rozplochý obdélník okna každého kontrolovaného podokna. Pokud je daný bod v této neploché oblasti, v podokně se vyhovuje kritéria hledání.

*bExactBar*<br/>
pro TRUE pro ignorování parametru *nSensitivity* ; v opačném případě FALSE.

*pRTCBarType*<br/>
pro Pokud není NULL, metoda vyhledá pouze podokna zadaného typu.

*bCheckVisibility*<br/>
pro TRUE pro kontrolu pouze viditelných podoken; v opačném případě FALSE.

*dwAlignment*<br/>
mimo Pokud je v zadaném bodě Nalezeno podokno, tento parametr obsahuje stranu podokna, které bylo nejblíže zadanému bodu. Další informace najdete v části poznámky.

*pBarToIgnore*<br/>
pro Pokud hodnota není NULL, metoda ignoruje podokna určené tímto parametrem.

### <a name="return-value"></a>Návratová hodnota

Objekt odvozený od [CBasePane](../../mfc/reference/cbasepane-class.md), který obsahuje daný bod, nebo hodnotu null, pokud nebylo nalezeno žádné podokno.

### <a name="remarks"></a>Poznámky

Když funkce vrátí a najde podokno, *dwAlignment* obsahuje zarovnání zadaného bodu. Například pokud je bod nejblíže horní části podokna, *dwAlignment* je nastaveno na CBRS_ALIGN_TOP.

##  <a name="processpanecontextmenucommand"></a>CDockingManager::P rocessPaneContextMenuCommand

Volá se rozhraním pro výběr nebo zrušení zaškrtnutí políčka pro zadaný příkaz a přepočítání rozložení zobrazeného podokna.

```
BOOL ProcessPaneContextMenuCommand(
    UINT nID,
    int nCode,
    void* pExtra,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
pro ID ovládacího panelu v nabídce

*nCode*<br/>
pro Kód oznámení příkazu

*pExtra*<br/>
pro Ukazatel na typ void, který je převeden na ukazatel na `CCmdUI`, pokud je CN_UPDATE_COMMAND_UI *nCode* .

*pHandlerInfo*<br/>
pro Ukazatel na strukturu informací. Tento parametr není používán.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud *pEXtra* není null a *nCode* se rovná CN_UPDATE_COMMAND_UI, nebo pokud je k dispozici ovládací panel se zadaným *NID*.

##  <a name="recalclayout"></a>CDockingManager::RecalcLayout

Přepočítá interní rozložení ovládacích prvků, které jsou k dispozici v seznamu ovládacích prvků.

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Parametry

*bNotify*<br/>
pro Tento parametr se nepoužívá.

##  <a name="releaseemptypanecontainers"></a>CDockingManager::ReleaseEmptyPaneContainers

Uvolní prázdné kontejnery podokna.

```
void ReleaseEmptyPaneContainers();
```

##  <a name="removehiddenmditabbedbar"></a>CDockingManager::RemoveHiddenMDITabbedBar

Odebere zadané skryté podokno pruhů.

```
void RemoveHiddenMDITabbedBar(CDockablePane* pBar);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
pro Ukazatel na podokno panelu, který se má odebrat.

##  <a name="removeminiframe"></a>CDockingManager::RemoveMiniFrame

Odebere zadaný snímek ze seznamu Mini rámců.

```
virtual BOOL RemoveMiniFrame(CPaneFrameWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
pro Ukazatel na rámec, který chcete odebrat.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je zadaný rámec odebraný; V opačném případě NEPRAVDA.

##  <a name="removepanefromdockmanager"></a>CDockingManager::RemovePaneFromDockManager

Zruší registraci podokna a odebere ho ze seznamu v Docker Manageru.

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
pro Ukazatel na podokno, které se má odebrat

*bDestroy*<br/>
pro Pokud je nastaveno na TRUE, odebrané podokno je zničeno.

*bAdjustLayout*<br/>
pro Pokud má hodnotu TRUE, upravte ukotvené rozložení hned.

*bAutoHide*<br/>
pro Pokud je nastaveno na TRUE, odeberou se podokno ze seznamu automaticky nastavených panelů. Pokud je hodnota FALSE, podokno je odebráno ze seznamu normálních podoken.

*pBarReplacement*<br/>
pro Ukazatel na podokno, které nahrazuje podokno odebráno.

##  <a name="replacepane"></a>CDockingManager::ReplacePane

Nahradí jedno podokno jiným.

```
BOOL ReplacePane(
    CDockablePane* pOriginalBar,
    CDockablePane* pNewBar);
```

### <a name="parameters"></a>Parametry

*pOriginalBar*<br/>
pro Ukazatel na původní podokno.

*pNewBar*<br/>
pro Ukazatel na podokno, které nahrazuje původní podokno.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je podokno úspěšně nahrazeno. V opačném případě NEPRAVDA.

##  <a name="resortminiframesforzorder"></a>CDockingManager::ResortMiniFramesForZOrder

Rozrekreační snímky v seznamu Mini rámců.

```
void ResortMiniFramesForZOrder();
```

##  <a name="savestate"></a>CDockingManager:: SaveState

Uloží stav správce Docker do registru.

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
pro Cesta ke klíči registru.

*uiID*<br/>
pro ID správce Docker.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byl stav úspěšně uložen; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Uložení stavu Docker Manageru do registru zahrnuje ukládání stavů řídicích panelů, stavů pruhů pro automatické skrývání a stavů Mini rámců přítomných v Docker Manageru.

##  <a name="sendmessagetominiframes"></a>CDockingManager::SendMessageToMiniFrames

Odešle zadanou zprávu do všech Mini rámců.

```
BOOL SendMessageToMiniFrames(
    UINT uMessage,
    WPARAM wParam = 0,
    LPARAM lParam = 0);
```

### <a name="parameters"></a>Parametry

*uMessage*<br/>
pro Zpráva, která má být odeslána.

*wParam*<br/>
pro Další informace závislé na zprávě

*lParam*<br/>
pro Další informace závislé na zprávě

### <a name="return-value"></a>Návratová hodnota

Vždy TRUE.

##  <a name="serialize"></a>CDockingManager:: serializovat

Zapíše správce Docker do archivu.

```
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*snížen*<br/>
pro Odkaz na objekt archivu.

### <a name="remarks"></a>Poznámky

Zápis správce Docker do archivu zahrnuje určení počtu ukotvených řídicích panelů a jezdců a napsání ovládacích panelů, minimálních rámečků, panelů automatického skrývání a panelů MDI do archivu.

##  <a name="setautohidezorder"></a>CDockingManager::SetAutohideZOrder

Nastaví velikost, šířku a výšku ovládacích panelů a určeného podokna.

```
void SetAutohideZOrder(CDockablePane* pAHDockingBar);
```

### <a name="parameters"></a>Parametry

*pAHDockingBar*<br/>
pro Ukazatel na podokno ukotvit

##  <a name="setdockingmode"></a>CDockingManager::SetDockingMode

Nastaví režim uchycení.

```
static void SetDockingMode(
    AFX_DOCK_TYPE dockMode,
    AFX_SMARTDOCK_THEME theme = AFX_SDT_DEFAULT);
```

### <a name="parameters"></a>Parametry

*dockMode*<br/>
Určuje nový režim ukotvení. Další informace najdete v části poznámky.

*použit*<br/>
Určuje motiv, který má být použit pro značky inteligentního Docker. Může to být jedna z následujících hodnot výčtu: AFX_SDT_DEFAULT, AFX_SDT_VS2005 AFX_SDT_VS2008.

### <a name="remarks"></a>Poznámky

Zavolejte tuto statickou metodu pro nastavení režimu ukotvení.

*dockMode* může být jedna z následujících hodnot:

- DT_STANDARD – standardní režim docking, jak je implementováno v aplikaci Visual Studio .NET 2003. Podokna jsou přetažena bez kontextu přetahování.

- DT_IMMEDIATE – režim docking, jak je implementován v aplikaci Microsoft Visio. Podokna jsou přetažena pomocí kontextu přetažení, ale nejsou zobrazeny žádné značky.

- DT_SMART – režim inteligentního Docker, jak je implementováno v aplikaci Visual Studio 2005. Podokna jsou přetažena s přetahováním kontextu a jsou zobrazeny inteligentní značky, které ukazují, kde může být podokno ukotveno.

##  <a name="setdockstate"></a>CDockingManager::SetDockState

Nastaví stav ukotvení řídicích panelů, minimálních rámců a panelů pro automatické skrývání.

```
virtual void SetDockState();
```

##  <a name="setprintpreviewmode"></a>CDockingManager::SetPrintPreviewMode

Nastaví režim náhledu tisku pruhů, které se zobrazují v náhledu tisku.

```
void SetPrintPreviewMode(
    BOOL bPreview,
    CPrintPreviewState* pState);
```

### <a name="parameters"></a>Parametry

*bPreview*<br/>
pro TRUE, pokud je nastaven režim náhledu tisku; V opačném případě NEPRAVDA.

*pState*<br/>
pro Ukazatel na stav verze Preview. Tento parametr není používán.

##  <a name="setsmartdockingparams"></a>CDockingManager::SetSmartDockingParams

Nastaví parametry, které definují chování inteligentního docking.

```
static void SetSmartDockingParams(CSmartDockingInfo& params);
```

### <a name="parameters"></a>Parametry

*params*<br/>
[in, out] Definuje parametry pro inteligentní Docker.

### <a name="remarks"></a>Poznámky

Tuto metodu zavolejte, pokud chcete přizpůsobit vzhled, barvu nebo tvar značek inteligentního Docker.

Chcete-li použít výchozí vzhled značek inteligentního Docker, předejte neinicializované instance [třídy CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md) do *paraí*.

##  <a name="showdelayshowminiframes"></a>CDockingManager::ShowDelayShowMiniFrames

Zobrazí nebo skryje okna mini rámců.

```
void ShowDelayShowMiniFrames(BOOL bshow);
```

### <a name="parameters"></a>Parametry

*bShow*<br/>
pro TRUE, pokud chcete, aby okno zobrazeného rámce bylo aktivní; FALSE pro skrytí okna rámce.

##  <a name="showpanes"></a>CDockingManager::ShowPanes

Zobrazí nebo skryje podokna ovládacího prvku a automaticky skrývat pruhy.

```
virtual BOOL ShowPanes(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bShow*<br/>
pro TRUE pro zobrazení podoken; FALSE pro skrytí podoken

### <a name="return-value"></a>Návratová hodnota

Vždy NEPRAVDA.

##  <a name="startsdocking"></a>CDockingManager::StartSDocking

Spustí inteligentní Docker zadaného okna podle zarovnání správce inteligentního dokování.

```
void StartSDocking(CWnd* pDockingWnd);
```

### <a name="parameters"></a>Parametry

*pDockingWnd*<br/>
pro Ukazatel na ukotvení okna.

##  <a name="stopsdocking"></a>CDockingManager::StopSDocking

Zastaví inteligentní Docker.

```
void StopSDocking();
```

##  <a name="getsmartdockingtheme"></a>CDockingManager::GetSmartDockingTheme

Statická metoda, která vrací motiv používaný k zobrazení značek inteligentního Docker.

```
static AFX_SMARTDOCK_THEME __stdcall GetSmartDockingTheme();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí jednu z následujících hodnot výčtu: AFX_SDT_DEFAULT, AFX_SDT_VS2005 AFX_SDT_VS2008.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[CFrameWndEx – třída](../../mfc/reference/cframewndex-class.md)<br/>
[CDockablePane – třída](../../mfc/reference/cdockablepane-class.md)<br/>
[CPaneFrameWnd – třída](../../mfc/reference/cpaneframewnd-class.md)
