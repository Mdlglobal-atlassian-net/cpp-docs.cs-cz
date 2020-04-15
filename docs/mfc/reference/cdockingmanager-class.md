---
title: Třída CDockingManager
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
ms.openlocfilehash: 339e5d5e464aacb51d1c4ab8fe3c2957a3afbd4e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375586"
---
# <a name="cdockingmanager-class"></a>Třída CDockingManager

Implementuje základní funkce, které řídí rozložení ukotvení v okně hlavního rámce.

## <a name="syntax"></a>Syntaxe

```
class CDockingManager : public CObject
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CDockingManager::AddDockSite](#adddocksite)|Vytvoří podokno ukotvení a přidá ho do seznamu ovládacích panelů.|
|[CDockingManager::AddHiddenMDITabbedBar](#addhiddenmditabbedbar)|Přidá úchyt do podokna pruhu do seznamu skrytých panelů panelů s kartami MDI.|
|[CDockingManager::AddMiniFrame](#addminiframe)|Přidá rámeček do seznamu mini rámečků.|
|[CDockingManager::AddPane](#addpane)|Zaregistruje podokno u správce dokovacích služeb.|
|[CDockingManager::AdjustDockingLayout](#adjustdockinglayout)|Přepočítá a upraví rozložení všech podoken v okně rámce.|
|[CDockingManager::AdjustFrameFrame](#adjustpaneframes)|Způsobí, že zpráva WM_NCCALCSIZE odeslána `CPaneFrameWnd` do všech podoken a oken.|
|[CDockingManager::AdjustRectToClientArea](#adjustrecttoclientarea)|Upraví zarovnání obdélníku.|
|[CDockingManager::AlignAutoHidePane](#alignautohidepane)|Změní velikost dokovacího podokna v režimu automatického skrytí tak, aby zaujímělo celou šířku nebo výšku klientské oblasti rámce obklopené dokovacími sítěmi.|
|[CDockingManager::AutoHidePane](#autohidepane)|Vytvoří panel nástrojů automatického skrytí.|
|[CDockingManager::BringBarsToTop](#bringbarstotop)|Přenese ukotvené pruhy, které mají zadanou trasu, na začátek.|
|[CDockingManager::Nabídka BuildPanes](#buildpanesmenu)|Přidá do nabídky názvy ukotvených panelů a panelů nástrojů.|
|[CDockingManager::CalcExpectedDockedRect](#calcexpecteddockedrect)|Vypočítá očekávaný obdélník ukotveného okna.|
|[CDockingManager::Vytvořit](#create)|Vytvoří správce ukotvení.|
|[CDockingManager::DeterminePaneAndStatus](#determinepaneandstatus)|Určuje podokno, které obsahuje daný bod a jeho stav ukotvení.|
|[CDockingManager::DisableRestoreDockState](#disablerestoredockstate)|Povolí nebo zakáže načítání dokovacího rozložení z registru.|
|[CDockingManager::DockPane](#dockpane)|Ukotví podokno do jiného podokna nebo do okna rámce.|
|[CDockingManager::DockPaneLeftOf](#dockpaneleftof)|Ukotví podokno nalevo od jiného podokna.|
|[CDockingManager::EnableAutoHidePanes](#enableautohidepanes)|Povolí ukotvení podokna do hlavního rámce, vytvoří dokovací podokno a přidá ho do seznamu ovládacích panelů.|
|[CDockingManager::EnableDocking](#enabledocking)|Vytvoří dokovací podokno a povolí ukotvení podokna k hlavnímu rámci.|
|[CDockingManager::EnableDockSiteMenu](#enabledocksitemenu)|Zobrazí další tlačítko, které otevře rozbalovací nabídku v popiscích všech ukotvených podoken.|
|[CDockingManager::Povolitkontextovou nabídku](#enablepanecontextmenu)|Řekne knihovně, aby zobrazila speciální kontextovou nabídku se seznamem panelů nástrojů aplikace a ukotvených panelů, když uživatel klepne pravým tlačítkem myši a knihovna zpracovává WM_CONTEXTMENU zprávu.|
|[CDockingManager::FindDockSite](#finddocksite)|Načte podokno pruhů, které je v zadané poloze a má zadanou trasu.|
|[CDockingManager::FindDockSiteByPane](#finddocksitebypane)|Vrátí podokno panelu, které má id podokna cílového pruhu.|
|[CDockingManager::FindPaneByID](#findpanebyid)|Vyhledá podokno podle zadaného ID ovládacího prvku.|
|[CDockingManager::Oprava virtuálních rektů](#fixupvirtualrects)|Potvrdí všechny aktuální pozice panelu nástrojů do virtuálních obdélníků.|
|[CDockingManager::FrameFromPoint](#framefrompoint)|Vrátí snímek, který obsahuje daný bod.|
|[CDockingManager::GetClientAreaBounds](#getclientareabounds)|Získá obdélník, který obsahuje hranice oblasti klienta.|
|[CDockingManager::GetDockingMode](#getdockingmode)|Vrátí aktuální režim ukotvení.|
|[CDockingManager::GetDockSiteFrameWnd](#getdocksiteframewnd)|Získá ukazatel na nadřazený rámeček okna.|
|[CDockingManager::GetEnabledAutoHideAlignment](#getenabledautohidealignment)|Vrátí povolené zarovnání podoken.|
|[CDockingManager::GetMiniFrames](#getminiframes)|Získá seznam miniframe.|
|[CDockingManager::GetOuterEdgeBounds](#getouteredgebounds)|Získá obdélník, který obsahuje vnější okraje rámce.|
|[CDockingManager::GetPaneList](#getpanelist)|Vrátí seznam podoken, které patří do dokovacího manažera. To zahrnuje všechny plovoucí podokna.|
|[CDockingManager::GetSmartDockingManager](#getsmartdockingmanager)|Načte ukazatel na inteligentní dokovací správce.|
|[CDockingManager::GetSmartDockingManagerPermanent](#getsmartdockingmanagerpermanent)|Načte ukazatel na inteligentní dokovací správce.|
|[CDockingManager::GetSmartDockingParams](#getsmartdockingparams)|Vrátí parametry inteligentního ukotvení pro správce ukotvení.|
|[CDockingManager::GetSmartDockingTheme](#getsmartdockingtheme)|Statická metoda, která vrací motiv používaný k zobrazení inteligentních značek ukotvení.|
|[CDockingManager::Skrýt automatické skatoři](#hideautohidepanes)|Skryje podokno, které je v režimu automatického skrytí.|
|[CDockingManager::InsertDockSite](#insertdocksite)|Vytvoří podokno ukotvení a vloží jej do seznamu ovládacích panelů.|
|[CDockingManager::InsertPane](#insertpane)|Vloží ovládací podokno do seznamu ovládacích panelů.|
|[CDockingManager::IsDockSiteMenu](#isdocksitemenu)|Určuje, zda se rozbalovací nabídka zobrazí v popiscích všech podoken.|
|[CDockingManager::IsInAdjustLayout](#isinadjustlayout)|Určuje, zda jsou upravena rozložení všech podoken.|
|[CDockingManager::IsOLEContainerMode](#isolecontainermode)|Určuje, zda je správce ukotvení v režimu kontejneru OLE.|
|[CDockingManager::IsPointNearDockSite](#ispointneardocksite)|Určuje, zda je zadaný bod v blízkosti lokality dock.|
|[CDockingManager::IsPrintPreviewValid](#isprintpreviewvalid)|Určuje, zda je nastaven režim náhledu tisku.|
|[CDockingManager::LoadState](#loadstate)|Načte stav správce ukotvení z registru.|
|[CDockingManager::LockUpdate](#lockupdate)|Zamkne dané okno.|
|[CDockingManager::OnActivateFrame](#onactivateframe)|Volat rámci při okno rámce je aktivní nebo je deaktivován.|
|[CDockingManager::OnClosePopupMenu](#onclosepopupmenu)|Volat rámci při aktivní rozbalovací nabídky zpracovává WM_DESTROY zprávu.|
|[CDockingManager::OnMoveMiniFrame](#onmoveminiframe)|Volat rámci přesunout okno mini-frame.|
|[CDockingManager::OnPaneContextMenu](#onpanecontextmenu)|Volat rámci při sestavení nabídky, která má seznam podoken.|
|[CDockingManager::PaneFromPoint](#panefrompoint)|Vrátí podokno, které obsahuje daný bod.|
|[CDockingManager::ProcessPaneContextMenuCommand](#processpanecontextmenucommand)|Nazývá rámci vybrat nebo zrušit zaškrtnutí políčka pro zadaný příkaz a přepočítat rozložení zobrazeného podokna.|
|[CDockingManager::RecalcLayout](#recalclayout)|Přepočítá vnitřní rozložení ovládacích prvků v seznamu ovládacích prvků.|
|[CDockingManager::ReleaseEmptyPaneContainers](#releaseemptypanecontainers)|Uvolní prázdné kontejnery podokna.|
|[CDockingManager::RemoveHiddenMDITabbedBar](#removehiddenmditabbedbar)|Odebere zadané skryté podokno pruhů.|
|[CDockingManager::RemoveMiniFrame](#removeminiframe)|Odebere zadaný snímek ze seznamu minirámečků.|
|[CDockingManager::RemovePaneFromDockManager](#removepanefromdockmanager)|Zruší registraci podokna a odebere ho ze seznamu ve správci ukotvení.|
|[CDockingManager::ReplacePane](#replacepane)|Nahradí jedno podokno jiným podoknem.|
|[CDockingManager::ResortMiniFramesForZOrder](#resortminiframesforzorder)|Střediska rámy v seznamu mini snímků.|
|[CDockingManager::SaveState](#savestate)|Uloží stav dokovacího správce do registru.|
|[CDockingManager::SendMessageToMiniFrames](#sendmessagetominiframes)|Odešle zadanou zprávu do všech mini rámců.|
|[CDockingManager::Serializovat](#serialize)|Zapíše správce dokovací služby do archivu. (Přepíše [CObject::Serializovat](../../mfc/reference/cobject-class.md#serialize).)|
|[CDockingManager::SetAutohideZOrder](#setautohidezorder)|Nastaví velikost, šířku a výšku ovládacích panelů a zadaného podokna.|
|[CDockingManager::SetDockingMode](#setdockingmode)|Nastaví režim ukotvení.|
|[CDockingManager::SetDockState](#setdockstate)|Nastaví stav ukotvení ovládacích panelů, mini snímků a pruhů automatického skrytí.|
|[CDockingManager::SetPrintPreviewMode](#setprintpreviewmode)|Nastaví režim náhledu pruhů, které jsou zobrazeny v náhledu tisku.|
|[CDockingManager::SetSmartDockingParams](#setsmartdockingparams)|Nastaví parametry, které definují chování inteligentního dokování.|
|[CDockingManager::ShowDelayShowMiniFrames](#showdelayshowminiframes)|Zobrazí nebo skryje okna minirámečků.|
|[CDockingManager::Zobrazit podokna](#showpanes)|Zobrazí nebo skryje podokna ovládacího prvku a automaticky skrytí pruhů.|
|[CDockingManager::StartSDocking](#startsdocking)|Spustí inteligentní ukotvení zadaného okna podle zarovnání inteligentního správce dokovaní.|
|[CDockingManager::StopSDocking](#stopsdocking)|Zastaví inteligentní dokování.|

### <a name="data-members"></a>Členové dat

|Name (Název)|Popis|
|----------|-----------------|
|[CDockingManager::m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode)|Určuje, zda správce ukotvení skryje podokna v režimu kontejneru OLE.|
|[CDockingManager::m_dockModeGlobal](#m_dockmodeglobal)|Určuje globální režim ukotvení.|
|[CDockingManager::m_nDockSensitivity](#m_ndocksensitivity)|Určuje citlivost ukotvení.|
|[CDockingManager::m_nTimeOutBeforeDockingBarDock](#m_ntimeoutbeforedockingbardock)|Určuje čas v milisekundách, než je dokovací podokno ukotveno v režimu okamžitého ukotvení.|
|[CDockingManager::m_nTimeOutBeforeToolBarDock](#m_ntimeoutbeforetoolbardock)|Určuje čas v milisekundách, než je panel nástrojů ukotven do okna hlavního rámce.|

## <a name="remarks"></a>Poznámky

Okno hlavního rámce vytvoří a inicializuje tuto třídu automaticky.

Objekt správce ukotvení obsahuje seznam všech podoken, které jsou v rozložení ukotvení a také seznam všech oken [CPaneFrameWnd,](../../mfc/reference/cpaneframewnd-class.md) které patří do okna hlavního rámce.

Třída `CDockingManager` implementuje některé služby, které můžete `CPaneFrameWnd` použít k vyhledání podokna nebo okna. Obvykle nevoláte tyto služby přímo, protože jsou zabaleny v objektu okna hlavního rámce. Další informace naleznete v [tématu CPaneFrameWnd Class](../../mfc/reference/cpaneframewnd-class.md).

## <a name="customization-tips"></a>Tipy pro přizpůsobení

Následující tipy platí `CDockingManager` pro objekty:

- [CDockingManager Class](../../mfc/reference/cdockingmanager-class.md) podporuje tyto režimy ukotvení:

  - `AFX_DOCK_TYPE::DT_IMMEDIATE`

  - `AFX_DOCK_TYPE::DT_STANDARD`

  - `AFX_DOCK_TYPE::DT_SMART`

  Tyto režimy ukotvení jsou definovány [CDockingManager::m_dockModeGlobal](#m_dockmodeglobal) a jsou nastaveny voláním [CDockingManager::SetDockingMode](#setdockingmode).

- Pokud chcete vytvořit podokno bez plovoucí, nenastavitelné, zavolejte metodu [CDockingManager::AddPane.](#addpane) Tato metoda zaregistruje podokno u správce ukotvení, který je zodpovědný za rozložení podokna.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat různé `CDockingManager` metody ve `CDockingManager` třídě ke konfiguraci objektu. Příklad ukazuje, jak zobrazit další tlačítko, které otevře rozbalovací nabídku na titulky všech ukotvených panelů a jak nastavit dokovací režim objektu. Tento fragment kódu je součástí [ukázky ukázky aplikace Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#24](../../mfc/codesnippet/cpp/cdockingmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CDockingManager](../../mfc/reference/cdockingmanager-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxDockingManager.h

## <a name="cdockingmanageradddocksite"></a><a name="adddocksite"></a>CDockingManager::AddDockSite

Vytvoří podokno ukotvení a přidá ho do seznamu ovládacích panelů.

```
BOOL AddDockSite(
    const AFX_DOCKSITE_INFO& info,
    CDockSite** ppDockBar = NULL);
```

### <a name="parameters"></a>Parametry

*Info*<br/>
[v] Odkaz na informační strukturu, která obsahuje zarovnání podokna ukotvení.

*ppDockBar*<br/>
[out] Ukazatel na ukazatel na nové podokno ukotvení.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud bylo podokno ukotvení úspěšně vytvořeno. FALSE jinak.

## <a name="cdockingmanageraddhiddenmditabbedbar"></a><a name="addhiddenmditabbedbar"></a>CDockingManager::AddHiddenMDITabbedBar

Přidá úchyt do podokna pruhu do seznamu skrytých panelů panelů s kartami MDI.

```
void AddHiddenMDITabbedBar(CDockablePane* pBar);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[v] Ukazatel na podokno pruhu

## <a name="cdockingmanageraddpane"></a><a name="addpane"></a>CDockingManager::AddPane

Zaregistruje podokno u správce dokovacích služeb.

```
BOOL AddPane(
    CBasePane* pWnd,
    BOOL bTail = TRUE,
    BOOL bAutoHide = FALSE,
    BOOL bInsertForOuterEdge = FALSE);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
[dovnitř, ven] Určuje podokno, které má být přidejte do správce ukotvení.

*bOcas*<br/>
[v] TRUE pro přidání podokna na konec seznamu podoken pro správce ukotvení; jinak NEPRAVDA.

*bAutoHide*<br/>
[v] Pouze pro vnitřní použití. Vždy používejte výchozí hodnotu FALSE.

*bInsertForOuterEdge*<br/>
[v] Pouze pro vnitřní použití. Vždy používejte výchozí hodnotu FALSE.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud bylo podokno úspěšně zaregistrováno u správce ukotvení; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Volání této metody zaregistrovat neplovoucí, non-resizable podokna s dokovací správce. Pokud podokna nezaregistrujete, nezobrazí se správně, když je umístěn správce doku.

## <a name="cdockingmanageradjustdockinglayout"></a><a name="adjustdockinglayout"></a>CDockingManager::AdjustDockingLayout

Přepočítá a upraví rozložení všech podoken v okně rámce.

```
virtual void AdjustDockingLayout(HDWP hdwp = NULL);
```

### <a name="parameters"></a>Parametry

*hdwp*<br/>
[v] Určuje strukturu odložené polohy okna. Další informace naleznete v tématu [Datové typy systému Windows](/windows/win32/WinProg/windows-data-types).

### <a name="remarks"></a>Poznámky

## <a name="cdockingmanageraddminiframe"></a><a name="addminiframe"></a>CDockingManager::AddMiniFrame

Přidá rámeček do seznamu mini rámečků.

```
virtual BOOL AddMiniFrame(CPaneFrameWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
[v] Ukazatel na rámeček.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud rámeček není v seznamu mini snímků a byl úspěšně přidán; FALSE jinak.

## <a name="cdockingmanageradjustpaneframes"></a><a name="adjustpaneframes"></a>CDockingManager::AdjustFrameFrame

Způsobí, že zpráva WM_NCCALCSIZE odeslána `CPaneFrameWnd` do všech podoken a oken.

```
virtual void AdjustPaneFrames();
```

### <a name="remarks"></a>Poznámky

## <a name="cdockingmanageradjustrecttoclientarea"></a><a name="adjustrecttoclientarea"></a>CDockingManager::AdjustRectToClientArea

Upraví zarovnání obdélníku.

```
virtual BOOL AdjustRectToClientArea(
    CRect& rectResult,
    DWORD dwAlignment);
```

### <a name="parameters"></a>Parametry

*rectVýsledek*<br/>
[v] Odkaz na `CRect` objekt

*dwAlignment*<br/>
[v] Zarovnání `CRect` objektu

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud bylo `CRect` zarovnání objektu upraveno; FALSE jinak.

### <a name="remarks"></a>Poznámky

Parametr *dwAlignment* může mít jednu z následujících hodnot:

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

## <a name="cdockingmanageralignautohidepane"></a><a name="alignautohidepane"></a>CDockingManager::AlignAutoHidePane

Změní velikost dokovacího podokna v režimu automatického skrytí tak, aby zaujímělo celou šířku nebo výšku klientské oblasti rámce obklopené dokovacími sítěmi.

```
void AlignAutoHidePane(
    CPaneDivider* pDefaultSlider,
    BOOL bIsVisible = TRUE);
```

### <a name="parameters"></a>Parametry

*pVýchozíJezdec*<br/>
[v] Podokno dokovacího jezdce.

*bIsVisible*<br/>
[v] PRAVDA, pokud je dokovací podokno viditelné; FALSE jinak.

## <a name="cdockingmanagerautohidepane"></a><a name="autohidepane"></a>CDockingManager::AutoHidePane

Vytvoří panel nástrojů automatického skrytí.

```
CMFCAutoHideToolBar* AutoHidePane(
    CDockablePane* pBar,
    CMFCAutoHideToolBar* pCurrAutoHideToolBar = NULL);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[v] Ukazatel na podokno pruhu.

*pCurrAutoHideToolBar*<br/>
[v] Ukazatel na automatický skrytí panelu nástrojů

### <a name="return-value"></a>Návratová hodnota

NULL, pokud nebyl vytvořen automatický skrytý panel nástrojů; jinak ukazatel na nový panel nástrojů.

## <a name="cdockingmanagerbringbarstotop"></a><a name="bringbarstotop"></a>CDockingManager::BringBarsToTop

Přenese ukotvené pruhy, které mají zadanou trasu, na začátek.

```
void BringBarsToTop(
    DWORD dwAlignment = 0,
    BOOL bExcludeDockedBars = TRUE);
```

### <a name="parameters"></a>Parametry

*dwAlignment*<br/>
[v] Zarovnání dokovacích pruhů, které jsou přeneseny na začátek ostatních oken.

*bExcludeDockedBars*<br/>
[v] TRUE chcete-li vyloučit ukotvené pruhy z bytí nahoře; jinak FALSE.

## <a name="cdockingmanagerbuildpanesmenu"></a><a name="buildpanesmenu"></a>CDockingManager::Nabídka BuildPanes

Přidá do nabídky názvy ukotvených panelů a panelů nástrojů.

```
void BuildPanesMenu(
    CMenu& menu,
    BOOL bToolbarsOnly);
```

### <a name="parameters"></a>Parametry

*Nabídky*<br/>
[v] Nabídka pro přidání názvů ukotvených panelů a panelů nástrojů.

*bPanelypouze*<br/>
[v] TRUE chcete-li do nabídky přidat pouze názvy panelů nástrojů; FALSE jinak.

## <a name="cdockingmanagercalcexpecteddockedrect"></a><a name="calcexpecteddockedrect"></a>CDockingManager::CalcExpectedDockedRect

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
[v] Ukazatel na okno do ukotvení.

*ptMouse*<br/>
[v] Umístění myši.

*rectVýsledek*<br/>
[out] Vypočítaný obdélník.

*bDrawTab*<br/>
[v] TRUE nakreslit kartu; jinak FALSE.

*ppCílový bar*<br/>
[out] Ukazatel na ukazatel na cílové podokno.

### <a name="remarks"></a>Poznámky

Tato metoda vypočítá obdélník, který by okno obsadit, pokud uživatel přetáhl okno do bodu určeného *ptMouse* a ukotvil ji tam.

## <a name="cdockingmanagercreate"></a><a name="create"></a>CDockingManager::Vytvořit

Vytvoří správce ukotvení.

```
BOOL Create(CFrameWnd* pParentWnd);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
[v] Ukazatel na nadřazený rámec správce ukotvení. Tato hodnota nesmí být null.

### <a name="return-value"></a>Návratová hodnota

TRUE vždy.

## <a name="cdockingmanagerdeterminepaneandstatus"></a><a name="determinepaneandstatus"></a>CDockingManager::DeterminePaneAndStatus

Určuje podokno, které obsahuje daný bod a jeho stav ukotvení.

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

*Pt*<br/>
[v] Umístění podokna ke kontrole.

*nCitlivost*<br/>
[v] Hodnota pro zvýšení obdélníku okna každého kontrolovaného podokna. Podokno splňuje kritéria hledání, pokud je daný bod v této zvýšené oblasti.

*dwEnabledAlignment*<br/>
[v] Zarovnání dokovacího podokna.

*ppCílový bar*<br/>
[out] Ukazatel na ukazatel na cílové podokno.

*pBarChcete-li ignorovat*<br/>
[v] Podokno, které metoda ignoruje.

*pBarToDock*<br/>
[v] Podokno, které je ukotveno.

### <a name="return-value"></a>Návratová hodnota

Stav doku.

### <a name="remarks"></a>Poznámky

Stav ukotvení může být jedna z následujících hodnot:

|AFX_CS_STATUS hodnota|Význam|
|---------------------------|-------------|
|CS_NOTHING|Ukazatel není nad dokovací sítí. Proto zachovat plovoucí podokno.|
|CS_DOCK_IMMEDIATELY|Ukazatel je nad dokovací sítí v bezprostředním režimu (DT_IMMEDIATE je povolen styl), takže podokno musí být okamžitě ukotveno.|
|CS_DELAY_DOCK|Ukazatel je nad dokovací mitý web, který je jiný dokovací podokno nebo je okraj hlavního rámce.|
|CS_DELAY_DOCK_TO_TAB|Ukazatel je nad dokovacím webem, který způsobí ukotvení podokna v okně s kartami. K tomu dochází, když je myš nad titulkem jiného dokovacího podokna nebo nad oblastí tabulátoru podokna s kartami.|

## <a name="cdockingmanagerdisablerestoredockstate"></a><a name="disablerestoredockstate"></a>CDockingManager::DisableRestoreDockState

Povolí nebo zakáže načítání dokovacího rozložení z registru.

```
void DisableRestoreDockState(BOOL bDisable = TRUE);
```

### <a name="parameters"></a>Parametry

*bZakázat*<br/>
[v] TRUE zakázat načítání dokovací rozložení z registru; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tuto metodu zavolejte, když je nutné zachovat aktuální rozložení ukotvených panelů a panelů nástrojů při načítání stavu aplikace.

## <a name="cdockingmanagerdockpane"></a><a name="dockpane"></a>CDockingManager::DockPane

Ukotví podokno do jiného podokna nebo do okna rámce.

```
void DockPane(
    CBasePane* pBar,
    UINT nDockBarID = 0,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[v] Ukazatel na podokno panelu panelu, ke které chcete ukotvit.

*nDockBarID*<br/>
[v] Id baru do docku.

*lpRect*<br/>
[v] Cílový obdélník.

## <a name="cdockingmanagerdockpaneleftof"></a><a name="dockpaneleftof"></a>CDockingManager::DockPaneLeftOf

Ukotví podokno nalevo od jiného podokna.

```
BOOL DockPaneLeftOf(
    CPane* pBarToDock,
    CPane* pTargetBar);
```

### <a name="parameters"></a>Parametry

*pBarToDock*<br/>
[v] Ukazatel na podokno, které má být ukotveno vlevo od *pTargetBar*.

*pCílový panel*<br/>
[v] Ukazatel na cílové podokno.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud bylo podokno úspěšně ukotveno; jinak NEPRAVDA.

## <a name="cdockingmanagerenableautohidepanes"></a><a name="enableautohidepanes"></a>CDockingManager::EnableAutoHidePanes

Povolí ukotvení podokna do hlavního rámce, vytvoří dokovací podokno a přidá ho do seznamu ovládacích panelů.

```
BOOL EnableAutoHidePanes(DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

*dwStyl*<br/>
[v] Dokovací zarovnání.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud bylo podokno ukotvení úspěšně vytvořeno. FALSE jinak.

## <a name="cdockingmanagerenabledocking"></a><a name="enabledocking"></a>CDockingManager::EnableDocking

Vytvoří dokovací podokno a povolí ukotvení podokna k hlavnímu rámci.

```
BOOL EnableDocking(DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

*dwStyl*<br/>
[v] Dokovací zarovnání.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud bylo podokno ukotvení úspěšně vytvořeno. FALSE jinak.

## <a name="cdockingmanagerenabledocksitemenu"></a><a name="enabledocksitemenu"></a>CDockingManager::EnableDockSiteMenu

Zobrazí další tlačítko, které otevře rozbalovací nabídku v popiscích všech ukotvených podoken.

```
static void EnableDockSiteMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[v] TRUE pro povolení nabídky dokovacího webu; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

V nabídce ukotvení se zobrazí následující možnosti pro změnu stavu ukotvení podokna:

- `Floating`- Plave podokno

- `Docking`- Ukotví podokno v hlavním snímku v místě, kde bylo podokno naposledy ukotveno

- `AutoHide`- Přepne podokno do režimu automatického skrytí

- `Hide`- Skryje podokno

Ve výchozím nastavení se tato nabídka nezobrazí.

## <a name="cdockingmanagerenablepanecontextmenu"></a><a name="enablepanecontextmenu"></a>CDockingManager::Povolitkontextovou nabídku

Řekne knihovně, aby zobrazila speciální kontextovou nabídku se seznamem panelů nástrojů aplikace a ukotvených panelů, když uživatel klepne pravým tlačítkem myši a knihovna zpracovává WM_CONTEXTMENU zprávu.

```
void EnablePaneContextMenu(
    BOOL bEnable,
    UINT uiCustomizeCmd,
    const CString& strCustomizeText,
    BOOL bToolbarsOnly = FALSE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[v] Pokud true, knihovna zapne podporu pro automatické kontextové nabídky; pokud false, knihovna vypne podporu pro automatické kontextové nabídky.

*uiCustomizeCmd*<br/>
[v] ID příkazu pro položku **Přizpůsobit** v nabídce.

*strCustomizeText*<br/>
[v] Text položky **Přizpůsobit.**

*bPanelypouze*<br/>
[v] Pokud je hodnota TRUE, zobrazí se v nabídce pouze seznam panelů nástrojů aplikace; Pokud nepravda, knihovna přidá do tohoto seznamu dokovací podokna aplikace.

## <a name="cdockingmanagerfinddocksite"></a><a name="finddocksite"></a>CDockingManager::FindDockSite

Načte podokno pruhů, které je v zadané poloze a má zadanou trasu.

```
virtual CDockSite* FindDockSite(
    DWORD dwAlignment,
    BOOL bOuter);
```

### <a name="parameters"></a>Parametry

*dwAlignment*<br/>
[v] Zarovnání podokna panelu.

*bVnější*<br/>
[v] Pokud true, načíst pruh v pozici hlavy v seznamu ovládacích panelů. V opačném případě načtěte pruh v koncové poloze v seznamu ovládacích panelů.

### <a name="return-value"></a>Návratová hodnota

Dokovací podokno, které má zadanou trasu; Null jinak.

## <a name="cdockingmanagerfindpanebyid"></a><a name="findpanebyid"></a>CDockingManager::FindPaneByID

Vyhledá podokno podle zadaného ID ovládacího prvku.

```
virtual CBasePane* FindPaneByID(
    UINT uBarID,
    BOOL bSearchMiniFrames = FALSE);
```

### <a name="parameters"></a>Parametry

*uBarID*<br/>
[v] Určuje ID ovládacího prvku podokna, které má být vyhledání.

*bSearchMiniFrames*<br/>
[v] PRAVDA, chcete-li zahrnout do hledání všechna plovoucí podokna. NEPRAVDA, aby zahrnovala pouze ukotvená podokna.

### <a name="return-value"></a>Návratová hodnota

Objekt [CBasePane,](../../mfc/reference/cbasepane-class.md) který má zadané ID ovládacího prvku, nebo NULL, pokud zadané podokno nelze najít.

### <a name="remarks"></a>Poznámky

## <a name="cdockingmanagerfinddocksitebypane"></a><a name="finddocksitebypane"></a>CDockingManager::FindDockSiteByPane

Vrátí podokno panelu, které má id podokna cílového pruhu.

```
virtual CDockSite* FindDockSiteByPane(CPane* pTargetBar);
```

### <a name="parameters"></a>Parametry

*pCílový panel*<br/>
[v] Ukazatel na podokno cílového pruhu.

### <a name="return-value"></a>Návratová hodnota

Podokno panelu, které má id podokna cílového panelu; NULL, pokud takové podokno panelu neexistuje.

## <a name="cdockingmanagerfixupvirtualrects"></a><a name="fixupvirtualrects"></a>CDockingManager::Oprava virtuálních rektů

Potvrdí všechny aktuální pozice panelu nástrojů do virtuálních obdélníků.

```
virtual void FixupVirtualRects();
```

### <a name="remarks"></a>Poznámky

Když uživatel začne přetahovat panel nástrojů, aplikace si zapamatuje svou původní pozici ve *virtuálním obdélníku*. Když uživatel přesune panel nástrojů přes svůj dokovací web, panel nástrojů může posunout ostatní panely nástrojů. Původní umístění ostatních panelů nástrojů jsou uloženy v odpovídajících virtuálních obdélníkech.

## <a name="cdockingmanagerframefrompoint"></a><a name="framefrompoint"></a>CDockingManager::FrameFromPoint

Vrátí snímek, který obsahuje daný bod.

```
virtual CPaneFrameWnd* FrameFromPoint(
    CPoint pt,
    CPaneFrameWnd* pFrameToExclude,
    BOOL bFloatMultiOnly) const;
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
[v] Určuje bod, který má být v souřadnicích obrazovky zkontrolován.

*pFrameToExclude*<br/>
[v] Ukazatel na snímek, který chcete vyloučit.

*bFloatMultiOnly*<br/>
[v] TRUE pro vyloučení rámců, `CMultiPaneFrameWnd`které nejsou instancemi ; FALSE jinak.

### <a name="return-value"></a>Návratová hodnota

Rámeček, který obsahuje daný bod; Null jinak.

## <a name="cdockingmanagergetclientareabounds"></a><a name="getclientareabounds"></a>CDockingManager::GetClientAreaBounds

Získá obdélník, který obsahuje hranice oblasti klienta.

```
CRect GetClientAreaBounds() const;

void GetClientAreaBounds(CRect& rcClient);
```

### <a name="parameters"></a>Parametry

*rcClient*<br/>
[out] Odkaz na obdélník, který obsahuje hranice oblasti klienta.

### <a name="return-value"></a>Návratová hodnota

Obdélník, který obsahuje hranice oblasti klienta.

## <a name="cdockingmanagergetdockingmode"></a><a name="getdockingmode"></a>CDockingManager::GetDockingMode

Vrátí aktuální režim ukotvení.

```
static AFX_DOCK_TYPE GetDockingMode();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota čítače výčtu, která představuje aktuální režim ukotvení. Může to být jedna z následujících hodnot:

- DT_STANDARD

- DT_IMMEDIATE

- DT_SMART

### <a name="remarks"></a>Poznámky

Chcete-li nastavit režim ukotvení, zavolejte [CDockingManager::SetDockingMode](#setdockingmode).

## <a name="cdockingmanagergetdocksiteframewnd"></a><a name="getdocksiteframewnd"></a>CDockingManager::GetDockSiteFrameWnd

Získá ukazatel na nadřazený rámeček okna.

```
CFrameWnd* GetDockSiteFrameWnd() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nadřazený rámeček okna.

## <a name="cdockingmanagergetenabledautohidealignment"></a><a name="getenabledautohidealignment"></a>CDockingManager::GetEnabledAutoHideAlignment

Vrátí povolené zarovnání podoken.

```
DWORD GetEnabledAutoHideAlignment() const;
```

### <a name="return-value"></a>Návratová hodnota

Bitová kombinace příznaků CBRS_ALIGN_ nebo 0, pokud nejsou povolena podokna automatického skrytí. Další informace naleznete v [tématu CFrameWnd::EnableDocking](../../mfc/reference/cframewnd-class.md#enabledocking).

### <a name="remarks"></a>Poznámky

Metoda vrátí povolené zarovnání pro ovládací panely automatického skrytí. Chcete-li povolit automatické skrytí pruhů, zavolejte [CFrameWndEx::EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes).

## <a name="cdockingmanagergetminiframes"></a><a name="getminiframes"></a>CDockingManager::GetMiniFrames

Získá seznam miniframe.

```
const CObList& GetMiniFrames() const;
```

### <a name="return-value"></a>Návratová hodnota

Seznam miniframe, které obsahují ovládací panely, které patří dokovací ho.

## <a name="cdockingmanagergetouteredgebounds"></a><a name="getouteredgebounds"></a>CDockingManager::GetOuterEdgeBounds

Získá obdélník, který obsahuje vnější okraje rámce.

```
CRect GetOuterEdgeBounds() const;
```

### <a name="return-value"></a>Návratová hodnota

Obdélník, který obsahuje vnější okraje rámečku.

## <a name="cdockingmanagergetpanelist"></a><a name="getpanelist"></a>CDockingManager::GetPaneList

Vrátí seznam podoken, které patří do dokovacího manažera. To zahrnuje všechny plovoucí podokna.

```
void GetPaneList(
    CObList& lstBars,
    BOOL bIncludeAutohide = FALSE,
    CRuntimeClass* pRTCFilter = NULL,
    BOOL bIncludeTabs = FALSE);
```

### <a name="parameters"></a>Parametry

*LstBary*<br/>
[dovnitř, ven] Obsahuje všechna podokna aktuálního správce ukotvení.

*bIncludeAutohide*<br/>
[v] PRAVDA, chcete-li zahrnout podokna, která jsou v režimu automatického skrytí; jinak NEPRAVDA.

*pRTCFiltr*<br/>
[v] Pokud není null, vrácený seznam obsahuje podokna pouze zadané třídy runtime.

*bIncludeTabs*<br/>
[v] PRAVDA, chcete-li zahrnout karty; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Pokud jsou ve správci ukotvení podokna s kartami, metoda vrátí ukazatele na objekty [třídy CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md) a je nutné explicitně vytvořit výčet karet.

Pomocí *filtru pRTCFilter* získáte určitou třídu podoken. Například můžete získat pouze panely nástrojů nastavením této hodnoty odpovídajícím způsobem.

## <a name="cdockingmanagergetsmartdockingmanager"></a><a name="getsmartdockingmanager"></a>CDockingManager::GetSmartDockingManager

Načte ukazatel na inteligentní dokovací správce.

```
CSmartDockingManager* GetSmartDockingManager();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na inteligentní správce dokování.

## <a name="cdockingmanagergetsmartdockingmanagerpermanent"></a><a name="getsmartdockingmanagerpermanent"></a>CDockingManager::GetSmartDockingManagerPermanent

Načte ukazatel na inteligentní dokovací správce.

```
CSmartDockingManager* GetSmartDockingManagerPermanent() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na inteligentní správce dokování.

## <a name="cdockingmanagergetsmartdockingparams"></a><a name="getsmartdockingparams"></a>CDockingManager::GetSmartDockingParams

Vrátí parametry inteligentního ukotvení pro správce ukotvení.

```
static CSmartDockingInfo& GetSmartDockingParams();
```

### <a name="return-value"></a>Návratová hodnota

Třída, která obsahuje parametry inteligentního ukotvení pro aktuálního správce ukotvení. Další informace naleznete v tématu [CSmartDockingInfo Class](../../mfc/reference/csmartdockinginfo-class.md).

### <a name="remarks"></a>Poznámky

## <a name="cdockingmanagerhideautohidepanes"></a><a name="hideautohidepanes"></a>CDockingManager::Skrýt automatické skatoři

Skryje podokno, které je v režimu automatického skrytí.

```
void HideAutoHidePanes(
    CDockablePane* pBarToExclude = NULL,
    BOOL bImmediately = FALSE);
```

### <a name="parameters"></a>Parametry

*pBarToVyloučit*<br/>
[v] Ukazatel na pruh vyloučit z skrytí.

*bOkamžitě*<br/>
[v] TRUE chcete-li podokno okamžitě skrýt; NEPRAVDA, chcete-li skrýt podokno s efektem automatického skrytí.

## <a name="cdockingmanagerinsertdocksite"></a><a name="insertdocksite"></a>CDockingManager::InsertDockSite

Vytvoří podokno ukotvení a vloží jej do seznamu ovládacích panelů.

```
BOOL InsertDockSite(
    const AFX_DOCKSITE_INFO& info,
    DWORD dwAlignToInsertAfter,
    CDockSite** ppDockBar = NULL);
```

### <a name="parameters"></a>Parametry

*Info*<br/>
[v] Struktura, která obsahuje informace o zarovnání podokna ukotvení.

*dwAlignToInsertAfter*<br/>
[v] Zarovnání podokna ukotvení.

*ppDockBar*<br/>
[out] Ukazatel na ukazatel na podokno ukotvení.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud bylo podokno ukotvení úspěšně vytvořeno. FALSE jinak.

## <a name="cdockingmanagerinsertpane"></a><a name="insertpane"></a>CDockingManager::InsertPane

Vloží ovládací podokno do seznamu ovládacích panelů.

```
BOOL InsertPane(
    CBasePane* pControlBar,
    CBasePane* pTarget,
    BOOL bAfter = TRUE);
```

### <a name="parameters"></a>Parametry

*pControlBar*<br/>
[v] Ukazatel na ovládací podokno.

*pCíl*<br/>
[v] Ukazatel na cílové podokno.

*bPo*<br/>
[v] TRUE pro vložení podokna za umístění cílového podokna; FALSE jinak.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je řídicí podokno úspěšně přidáno do seznamu ovládacích panelů; FALSE jinak.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí false, pokud je ovládací podokno již v seznamu ovládacích panelů nebo pokud cílové podokno neexistuje v seznamu ovládacích panelů.

## <a name="cdockingmanagerisdocksitemenu"></a><a name="isdocksitemenu"></a>CDockingManager::IsDockSiteMenu

Určuje, zda se rozbalovací nabídka zobrazí v popiscích všech podoken.

```
static BOOL IsDockSiteMenu();
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je nabídka dokovacího webu zobrazena na titulky všech ukotvených panelů; jinak FALSE.

### <a name="remarks"></a>Poznámky

Nabídku dokovacího webu můžete povolit voláním [CDockingManager::EnableDockSiteMenu](#enabledocksitemenu).

## <a name="cdockingmanagerisinadjustlayout"></a><a name="isinadjustlayout"></a>CDockingManager::IsInAdjustLayout

Určuje, zda jsou upravena rozložení všech podoken.

```
BOOL IsInAdjustLayout() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud jsou upravena rozložení všech podoken; FALSE jinak.

## <a name="cdockingmanagerisolecontainermode"></a><a name="isolecontainermode"></a>CDockingManager::IsOLEContainerMode

Určuje, zda je správce ukotvení v režimu kontejneru OLE.

```
BOOL IsOLEContainerMode() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je správce dokovacích služeb v režimu kontejneru OLE; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

V režimu kontejneru OLE jsou všechna ukotvená podokna a panely nástrojů aplikace skryty. Podokna jsou také skryta v tomto režimu, pokud jste nastavili [CDockingManager::m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode) na HODNOTU TRUE.

## <a name="cdockingmanagerispointneardocksite"></a><a name="ispointneardocksite"></a>CDockingManager::IsPointNearDockSite

Určuje, zda je zadaný bod v blízkosti lokality dock.

```
BOOL IsPointNearDockSite(
    CPoint point,
    DWORD& dwBarAlignment,
    BOOL& bOuterEdge) const;
```

### <a name="parameters"></a>Parametry

*Bod*<br/>
[v] Zadaný bod.

*dwBarAlignment*<br/>
[out] Určuje, která hrana bodu je blízko. Možné hodnoty jsou CBRS_ALIGN_LEFT, CBRS_ALIGN_RIGHT, CBRS_ALIGN_TOP a CBRS_ALIGN_BOTTOM.

*bOuterEdge*<br/>
[out] PRAVDA, pokud je bod blízko vnějšího okraje doku; FALSE jinak.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je bod v blízkosti místa doku; jinak FALSE.

## <a name="cdockingmanagerisprintpreviewvalid"></a><a name="isprintpreviewvalid"></a>CDockingManager::IsPrintPreviewValid

Určuje, zda je nastaven režim náhledu tisku.

```
BOOL IsPrintPreviewValid() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je nastaven režim náhledu; FALSE jinak.

## <a name="cdockingmanagerloadstate"></a><a name="loadstate"></a>CDockingManager::LoadState

Načte stav správce ukotvení z registru.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[v] Název profilu.

*uiID*<br/>
[v] Id dokovacího manažera.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byl stav správce ukotvení úspěšně načten; jinak FALSE.

## <a name="cdockingmanagerlockupdate"></a><a name="lockupdate"></a>CDockingManager::LockUpdate

Zamkne dané okno.

```
void LockUpdate(BOOL bLock);
```

### <a name="parameters"></a>Parametry

*Blok*<br/>
[v] PRAVDA, pokud je okno zamknuté; FALSE jinak.

### <a name="remarks"></a>Poznámky

Pokud je okno zamknuto, nelze jej přesunout a nelze jej překreslit.

## <a name="cdockingmanagerm_bhidedockingbarsincontainermode"></a><a name="m_bhidedockingbarsincontainermode"></a>CDockingManager::m_bHideDockingBarsInContainerMode

Určuje, zda správce ukotvení skryje podokna v režimu kontejneru OLE.

```
AFX_IMPORT_DATA static BOOL m_bHideDockingBarsInContainerMode;
```

### <a name="remarks"></a>Poznámky

Pokud chcete zachovat všechny podlozy ukotvené k hlavnímu snímku viditelné, když je aplikace v režimu kontejneru OLE, nastavte tuto hodnotu na hodnotu NEPRAVDA. Ve výchozím nastavení je tato hodnota true.

## <a name="cdockingmanagerm_dockmodeglobal"></a><a name="m_dockmodeglobal"></a>CDockingManager::m_dockModeGlobal

Určuje globální režim ukotvení.

```
AFX_IMPORT_DATA static AFX_DOCK_TYPE m_dockModeGlobal;
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení používá každé dokovací podokno tento režim ukotvení. Další informace o hodnotách, na které lze toto pole nastavit, naleznete v [tématu CBasePane::GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode).

## <a name="cdockingmanagerm_ndocksensitivity"></a><a name="m_ndocksensitivity"></a>CDockingManager::m_nDockSensitivity

Určuje citlivost ukotvení.

```
AFX_IMPORT_DATA static int m_nDockSensitivity;
```

### <a name="remarks"></a>Poznámky

Citlivost ukotvení definuje, jak blízko může plovoucí podokno přiblížit k dokovacímu podoknu, dokovacímu webu nebo jinému podoknu před tím, než architektura změní svůj stav na ukotvený.

## <a name="cdockingmanagerm_ntimeoutbeforedockingbardock"></a><a name="m_ntimeoutbeforedockingbardock"></a>CDockingManager::m_nTimeOutBeforeDockingBarDock

Určuje čas v milisekundách, než je dokovací podokno ukotveno v režimu okamžitého ukotvení.

```
static UINT m_nTimeOutBeforeDockingBarDock;
```

### <a name="remarks"></a>Poznámky

Před ukotvenípodokna, rozhraní čeká zadanou dobu. Tím zabráníte náhodnému ukotvení podokna do umístění, zatímco jej uživatel stále přetahuje.

## <a name="cdockingmanagerm_ntimeoutbeforetoolbardock"></a><a name="m_ntimeoutbeforetoolbardock"></a>CDockingManager::m_nTimeOutBeforeToolBarDock

Určuje čas v milisekundách, než je panel nástrojů ukotven do okna hlavního rámce.

```
static UINT m_nTimeOutBeforeToolBarDock;
```

### <a name="remarks"></a>Poznámky

Před ukotvením panelu nástrojů čeká rozhraní zadanou dobu. Tím zabráníte náhodnému ukotvení panelu nástrojů do umístění, zatímco jej uživatel stále přetahuje.

## <a name="cdockingmanageronactivateframe"></a><a name="onactivateframe"></a>CDockingManager::OnActivateFrame

Volat rámci při okno rámce je aktivní nebo je deaktivován.

```
virtual void OnActivateFrame(BOOL bActivate);
```

### <a name="parameters"></a>Parametry

*bAktivovat*<br/>
[v] Pokud true, okno rámce je aktivní; pokud false, okno rámce je deaktivováno.

## <a name="cdockingmanageronclosepopupmenu"></a><a name="onclosepopupmenu"></a>CDockingManager::OnClosePopupMenu

Volat rámci při aktivní rozbalovací nabídky zpracovává WM_DESTROY zprávu.

```
void OnClosePopupMenu();
```

### <a name="remarks"></a>Poznámky

Rozhraní framework odešle zprávu WM_DESTROY, když se chystá zavřít aktuální hlavní okno. Přepsat tuto metodu pro `CMFCPopupMenu` zpracování oznámení z objektů, `CMFCPopupMenu` které patří do okna rámce, když objekt zpracuje WM_DESTROY zprávu.

## <a name="cdockingmanageronmoveminiframe"></a><a name="onmoveminiframe"></a>CDockingManager::OnMoveMiniFrame

Volat rámci přesunout okno mini-frame.

```
virtual BOOL OnMoveMiniFrame(CWnd* pFrame);
```

### <a name="parameters"></a>Parametry

*pRám*<br/>
[v] Ukazatel na okno minirámečku.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je metoda úspěšná; jinak FALSE.

## <a name="cdockingmanageronpanecontextmenu"></a><a name="onpanecontextmenu"></a>CDockingManager::OnPaneContextMenu

Volat rámci při sestavení nabídky, která má seznam podoken.

```
void OnPaneContextMenu(CPoint point);
```

### <a name="parameters"></a>Parametry

*Bod*<br/>
[v] Určuje umístění nabídky.

## <a name="cdockingmanagerpanefrompoint"></a><a name="panefrompoint"></a>CDockingManager::PaneFromPoint

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

*Bod*<br/>
[v] Určuje bod, který má být v souřadnicích obrazovky zkontrolován.

*nCitlivost*<br/>
[v] Hodnota nafouknout obdélník okna každé zaškrtnuté podokno. Podokno splňuje kritéria hledání, pokud je daný bod v této nafouknuté oblasti.

*bPřesný pruh*<br/>
[v] TRUE ignorovat *parametr nSensitivity;* jinak NEPRAVDA.

*pRTCBarTyp*<br/>
[v] Pokud není null, metoda prohledá pouze podokna zadaného typu.

*bCheckVisibility*<br/>
[v] TRUE pro kontrolu pouze viditelných podoken; jinak NEPRAVDA.

*dwAlignment*<br/>
[out] Pokud je v zadaném bodě nalezeno podokno, obsahuje tento parametr stranu podokna, která byla nejblíže zadanému bodu. Další informace naleznete v části Poznámky.

*pBarChcete-li ignorovat*<br/>
[v] Pokud není null, metoda ignoruje podokna určená tímto parametrem.

### <a name="return-value"></a>Návratová hodnota

[CBasePane](../../mfc/reference/cbasepane-class.md)-odvozený objekt, který obsahuje daný bod, nebo NULL, pokud nebylo nalezeno žádné podokno.

### <a name="remarks"></a>Poznámky

Když se funkce vrátí a bylo nalezeno podokno, *dwAlignment* obsahuje zarovnání zadaného bodu. Například pokud bod byl nejblíže k horní části podokna, *dwAlignment* je nastavena na CBRS_ALIGN_TOP.

## <a name="cdockingmanagerprocesspanecontextmenucommand"></a><a name="processpanecontextmenucommand"></a>CDockingManager::ProcessPaneContextMenuCommand

Nazývá rámci vybrat nebo zrušit zaškrtnutí políčka pro zadaný příkaz a přepočítat rozložení zobrazeného podokna.

```
BOOL ProcessPaneContextMenuCommand(
    UINT nID,
    int nCode,
    void* pExtra,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
[v] Id ovládacího panelu v nabídce.

*nKód*<br/>
[v] Kód oznámení příkazu.

*pExtra*<br/>
[v] Ukazatel void, který je převržen `CCmdUI` na ukazatel, pokud *nCode* je CN_UPDATE_COMMAND_UI.

*pHandlerInfo*<br/>
[v] Ukazatel na informační strukturu. Tento parametr není používán.

### <a name="return-value"></a>Návratová hodnota

TRUE Pokud *pEXtra* není NULL a *nCode* se rovná CN_UPDATE_COMMAND_UI, nebo pokud je ovládací panel se zadaným *nID*.

## <a name="cdockingmanagerrecalclayout"></a><a name="recalclayout"></a>CDockingManager::RecalcLayout

Přepočítá vnitřní rozložení ovládacích prvků v seznamu ovládacích prvků.

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Parametry

*bUpozornit*<br/>
[v] Tento parametr se nepoužívá.

## <a name="cdockingmanagerreleaseemptypanecontainers"></a><a name="releaseemptypanecontainers"></a>CDockingManager::ReleaseEmptyPaneContainers

Uvolní prázdné kontejnery podokna.

```
void ReleaseEmptyPaneContainers();
```

## <a name="cdockingmanagerremovehiddenmditabbedbar"></a><a name="removehiddenmditabbedbar"></a>CDockingManager::RemoveHiddenMDITabbedBar

Odebere zadané skryté podokno pruhů.

```
void RemoveHiddenMDITabbedBar(CDockablePane* pBar);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[v] Ukazatel na podokno pruhu odebrat.

## <a name="cdockingmanagerremoveminiframe"></a><a name="removeminiframe"></a>CDockingManager::RemoveMiniFrame

Odebere zadaný snímek ze seznamu minirámečků.

```
virtual BOOL RemoveMiniFrame(CPaneFrameWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
[v] Ukazatel na snímek, který chcete odebrat.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je zadaný snímek odebrán; FALSE jinak.

## <a name="cdockingmanagerremovepanefromdockmanager"></a><a name="removepanefromdockmanager"></a>CDockingManager::RemovePaneFromDockManager

Zruší registraci podokna a odebere ho ze seznamu ve správci ukotvení.

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
[v] Ukazatel na podokno, které má být odebráno.

*bZničit*<br/>
[v] Pokud true, odstraněné podokno je zničeno.

*bAdjustLayout*<br/>
[v] Pokud true, okamžitě upravte rozložení ukotvení.

*bAutoHide*<br/>
[v] Pokud je hodnota TRUE, bude podokno odebráno ze seznamu pruhů automatického skrytí. Pokud false, podokno je odebránze seznamu pravidelných podoken.

*pNahrazení bar*<br/>
[v] Ukazatel na podokno, které nahradí odebrané podokno.

## <a name="cdockingmanagerreplacepane"></a><a name="replacepane"></a>CDockingManager::ReplacePane

Nahradí jedno podokno jiným podoknem.

```
BOOL ReplacePane(
    CDockablePane* pOriginalBar,
    CDockablePane* pNewBar);
```

### <a name="parameters"></a>Parametry

*pOriginalBar*<br/>
[v] Ukazatel na původní podokno.

*pNewBar*<br/>
[v] Ukazatel na podokno, které nahrazuje původní podokno.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je podokno úspěšně nahrazeno; FALSE jinak.

## <a name="cdockingmanagerresortminiframesforzorder"></a><a name="resortminiframesforzorder"></a>CDockingManager::ResortMiniFramesForZOrder

Střediska rámy v seznamu mini snímků.

```
void ResortMiniFramesForZOrder();
```

## <a name="cdockingmanagersavestate"></a><a name="savestate"></a>CDockingManager::SaveState

Uloží stav dokovacího správce do registru.

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[v] Cesta ke klíči registru.

*uiID*<br/>
[v] ID správce doku.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byl stav úspěšně uložen; jinak FALSE.

### <a name="remarks"></a>Poznámky

Uložení stavu správce ukotvení do registru zahrnuje uložení stavů ovládacích panelů, stavů automatických skrytí a stavů mini rámců přítomných ve správci ukotvení.

## <a name="cdockingmanagersendmessagetominiframes"></a><a name="sendmessagetominiframes"></a>CDockingManager::SendMessageToMiniFrames

Odešle zadanou zprávu do všech mini rámců.

```
BOOL SendMessageToMiniFrames(
    UINT uMessage,
    WPARAM wParam = 0,
    LPARAM lParam = 0);
```

### <a name="parameters"></a>Parametry

*uMessage*<br/>
[v] Zpráva, která má být odeslána.

*wParam*<br/>
[v] Další informace závislé na zprávě.

*Lparam*<br/>
[v] Další informace závislé na zprávě.

### <a name="return-value"></a>Návratová hodnota

TRUE vždy.

## <a name="cdockingmanagerserialize"></a><a name="serialize"></a>CDockingManager::Serializovat

Zapíše správce dokovací služby do archivu.

```
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*ar*<br/>
[v] Odkaz na objekt archivu.

### <a name="remarks"></a>Poznámky

Zápis správce ukotvení do archivu zahrnuje určení počtu ovládacích panelů a jezdců ukotvení a zápis ovládacích panelů, mini rámečků, pruhů automatického skrytí a pruhů s kartami MDI do archivu.

## <a name="cdockingmanagersetautohidezorder"></a><a name="setautohidezorder"></a>CDockingManager::SetAutohideZOrder

Nastaví velikost, šířku a výšku ovládacích panelů a zadaného podokna.

```
void SetAutohideZOrder(CDockablePane* pAHDockingBar);
```

### <a name="parameters"></a>Parametry

*pAHDockingBar*<br/>
[v] Ukazatel na dokovatelné podokno.

## <a name="cdockingmanagersetdockingmode"></a><a name="setdockingmode"></a>CDockingManager::SetDockingMode

Nastaví režim ukotvení.

```
static void SetDockingMode(
    AFX_DOCK_TYPE dockMode,
    AFX_SMARTDOCK_THEME theme = AFX_SDT_DEFAULT);
```

### <a name="parameters"></a>Parametry

*dockMode*<br/>
Určuje nový režim ukotvení. Další informace naleznete v části Poznámky.

*Téma*<br/>
Určuje motiv, který se má použít pro inteligentní značky ukotvení. Může se jedná o jednu z následujících výčtových hodnot: AFX_SDT_DEFAULT, AFX_SDT_VS2005, AFX_SDT_VS2008.

### <a name="remarks"></a>Poznámky

Volání této statické metody pro nastavení dokovacího režimu.

*dockMode* může být jedna z následujících hodnot:

- DT_STANDARD – standardní dokovací režim implementovaný v sadě Visual Studio .NET 2003. Podokna jsou přetažena bez přetahování kontextu.

- DT_IMMEDIATE – režim okamžitého ukotvení, jak je implementován v aplikaci Microsoft Visio. Podokna jsou přetažena s přetahovaným kontextem, ale nejsou zobrazeny žádné značky.

- DT_SMART – inteligentní dokovací režim implementovaný v sadě Visual Studio 2005. Podokna jsou přetažena s přetahovaným kontextem a jsou zobrazeny inteligentní značky, které ukazují, kde lze podokno ukotvit.

## <a name="cdockingmanagersetdockstate"></a><a name="setdockstate"></a>CDockingManager::SetDockState

Nastaví stav ukotvení ovládacích panelů, mini snímků a pruhů automatického skrytí.

```
virtual void SetDockState();
```

## <a name="cdockingmanagersetprintpreviewmode"></a><a name="setprintpreviewmode"></a>CDockingManager::SetPrintPreviewMode

Nastaví režim náhledu pruhů, které jsou zobrazeny v náhledu tisku.

```
void SetPrintPreviewMode(
    BOOL bPreview,
    CPrintPreviewState* pState);
```

### <a name="parameters"></a>Parametry

*bNáhled*<br/>
[v] TRUE, pokud je nastaven režim náhledu; FALSE jinak.

*pStát*<br/>
[v] Ukazatel na stav náhledu. Tento parametr není používán.

## <a name="cdockingmanagersetsmartdockingparams"></a><a name="setsmartdockingparams"></a>CDockingManager::SetSmartDockingParams

Nastaví parametry, které definují chování inteligentního dokování.

```
static void SetSmartDockingParams(CSmartDockingInfo& params);
```

### <a name="parameters"></a>Parametry

*params*<br/>
[dovnitř, ven] Definuje parametry pro inteligentní ukotvení.

### <a name="remarks"></a>Poznámky

Tuto metodu zavolejte, pokud chcete přizpůsobit vzhled, barvu nebo tvar inteligentních značek ukotvení.

Chcete-li použít výchozí vzhled inteligentních značek ukotvení, předajte neinicializovanou instanci [třídy CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md) *paramům*.

## <a name="cdockingmanagershowdelayshowminiframes"></a><a name="showdelayshowminiframes"></a>CDockingManager::ShowDelayShowMiniFrames

Zobrazí nebo skryje okna minirámečků.

```
void ShowDelayShowMiniFrames(BOOL bshow);
```

### <a name="parameters"></a>Parametry

*bZobrazit*<br/>
[v] TRUE, aby bylo okno zobrazeného rámečku aktivní; NEPRAVDA, chcete-li skrýt okno rámce.

## <a name="cdockingmanagershowpanes"></a><a name="showpanes"></a>CDockingManager::Zobrazit podokna

Zobrazí nebo skryje podokna ovládacího prvku a automaticky skrytí pruhů.

```
virtual BOOL ShowPanes(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bZobrazit*<br/>
[v] TRUE pro zobrazení podoken; NEPRAVDA, chcete-li podokna skrýt.

### <a name="return-value"></a>Návratová hodnota

Vždy FALSE

## <a name="cdockingmanagerstartsdocking"></a><a name="startsdocking"></a>CDockingManager::StartSDocking

Spustí inteligentní ukotvení zadaného okna podle zarovnání inteligentního správce dokovaní.

```
void StartSDocking(CWnd* pDockingWnd);
```

### <a name="parameters"></a>Parametry

*pDockingWnd*<br/>
[v] Ukazatel na okno do ukotvení.

## <a name="cdockingmanagerstopsdocking"></a><a name="stopsdocking"></a>CDockingManager::StopSDocking

Zastaví inteligentní dokování.

```
void StopSDocking();
```

## <a name="cdockingmanagergetsmartdockingtheme"></a><a name="getsmartdockingtheme"></a>CDockingManager::GetSmartDockingTheme

Statická metoda, která vrací motiv používaný k zobrazení inteligentních značek ukotvení.

```
static AFX_SMARTDOCK_THEME __stdcall GetSmartDockingTheme();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí jednu z následujících výčtových hodnot: AFX_SDT_DEFAULT, AFX_SDT_VS2005, AFX_SDT_VS2008.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[CFrameWndEx – třída](../../mfc/reference/cframewndex-class.md)<br/>
[Třída CDockablePane](../../mfc/reference/cdockablepane-class.md)<br/>
[Třída CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)
