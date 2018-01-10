---
title: "Třída CDockingManager | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "37"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2f1a436ab6bfbc5e21e43267d3992310ed6f6a20
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cdockingmanager-class"></a>CDockingManager – třída
Implementuje základní funkce, které řídí ukotvení rozložení v okně s rámečkem hlavní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDockingManager : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDockingManager::AddDockSite](#adddocksite)|Vytvoří podokno ukotvení a přidá ho do seznamu ovládací pruhy.|  
|[CDockingManager::AddHiddenMDITabbedBar](#addhiddenmditabbedbar)|Přidá popisovač na panel podokně do seznamu skrytých MDI na kartách panelu podokna.|  
|[CDockingManager::AddMiniFrame](#addminiframe)|Rámeček se přidá do seznamu mini snímků.|  
|[CDockingManager::AddPane](#addpane)|Zaregistruje podokno se správce ukotvení.|  
|[CDockingManager::AdjustDockingLayout](#adjustdockinglayout)|Přepočítá a upraví rozložení všechny podokna v okně s rámečkem.|  
|[CDockingManager::AdjustPaneFrames](#adjustpaneframes)|Způsobí, že `WM_NCCALCSIZE` zpráva k odeslání do všech podokna a `CPaneFrameWnd` systému windows.|  
|[CDockingManager::AdjustRectToClientArea](#adjustrecttoclientarea)|Upraví zarovnání obdélníku.|  
|[CDockingManager::AlignAutoHidePane](#alignautohidepane)|Změní velikost ukotvené podokno v režimu autohide – tak, aby trvá úplné šířka nebo výška rámečku klientské oblasti obklopená ukotvení lokalit.|  
|[CDockingManager::AutoHidePane](#autohidepane)|Vytvoří automaticky skrývat nástrojů.|  
|[CDockingManager::BringBarsToTop](#bringbarstotop)|Přináší ukotveného řádky, které mají zadané zarovnání k nejvyšší.|  
|[CDockingManager::BuildPanesMenu](#buildpanesmenu)|Přidá názvy ukotvení podokna a panelů nástrojů k nabídce.|  
|[CDockingManager::CalcExpectedDockedRect](#calcexpecteddockedrect)|Vypočítá očekávané rámeček ukotveného okna.|  
|[CDockingManager::Create](#create)|Vytvoří ukotvení správce.|  
|[CDockingManager::DeterminePaneAndStatus](#determinepaneandstatus)|Určuje, v podokně obsahující k danému bodu a stavu její ukotvení.|  
|[CDockingManager::DisableRestoreDockState](#disablerestoredockstate)|Povolí nebo zakáže načítání ukotvení rozložení z registru.|  
|[CDockingManager::DockPane](#dockpane)|Podokno ukotvené jiného podokna nebo okně s rámečkem.|  
|[CDockingManager::DockPaneLeftOf](#dockpaneleftof)|Ukotvené podokno nalevo od jiného podokna.|  
|[CDockingManager::EnableAutoHidePanes](#enableautohidepanes)|Umožňuje ukotvení podokna do hlavního rámce, vytvoří podokno ukotvení a přidá ji do seznamu ovládací pruhy.|  
|[CDockingManager::EnableDocking](#enabledocking)|Vytvoří podokno ukotvení a umožňuje ukotvení podokna do hlavního rámce.|  
|[CDockingManager::EnableDockSiteMenu](#enabledocksitemenu)|Zobrazí další tlačítko, které se otevře místní nabídky na titulky všechny ukotvení podokna.|  
|[CDockingManager::EnablePaneContextMenu](#enablepanecontextmenu)|Říká knihovna zobrazíte speciální kontextové nabídky, která má seznam panelů nástrojů aplikace a ukotvení podokna při kliknutí pravým tlačítkem myši a knihovny je zpracování zpráv WM_CONTEXTMENU.|  
|[CDockingManager::FindDockSite](#finddocksite)|Načte panelu podokně, který je na zadané pozici a který má zadané zarovnání.|  
|[CDockingManager::FindDockSiteByPane](#finddocksitebypane)|Vrátí panelu podokno, které má id panelu cílového řádku.|  
|[CDockingManager::FindPaneByID](#findpanebyid)|Vyhledá podokně podle ID ovládací prvek.|  
|[CDockingManager::FixupVirtualRects](#fixupvirtualrects)|Potvrdí všechny aktuální pozic panelu nástrojů, který má virtuální obdélníky.|  
|[CDockingManager::FrameFromPoint](#framefrompoint)|Vrátí rámce, který obsahuje danému bodu.|  
|[CDockingManager::GetClientAreaBounds](#getclientareabounds)|Získá obdélníku, která obsahuje hranice klientské oblasti.|  
|[CDockingManager::GetDockingMode](#getdockingmode)|Vrátí aktuální režim ukotvení.|  
|[CDockingManager::GetDockSiteFrameWnd](#getdocksiteframewnd)|Získá ukazatel na rámec okna nadřazené.|  
|[CDockingManager::GetEnabledAutoHideAlignment](#getenabledautohidealignment)|Vrátí povoleno zarovnání podoken.|  
|[CDockingManager::GetMiniFrames](#getminiframes)|Získá seznam miniframes.|  
|[CDockingManager::GetOuterEdgeBounds](#getouteredgebounds)|Získá obdélníku, který obsahuje vnější okrajů rámečku.|  
|[CDockingManager::GetPaneList](#getpanelist)|Vrátí seznam hodnot podokna, které patří do správce ukotvení. To zahrnuje všechny plovoucí podokna.|  
|[CDockingManager::GetSmartDockingManager](#getsmartdockingmanager)|Načte ukazatel správce inteligentní ukotvení.|  
|[CDockingManager::GetSmartDockingManagerPermanent](#getsmartdockingmanagerpermanent)|Načte ukazatel správce inteligentní ukotvení.|  
|[CDockingManager::GetSmartDockingParams](#getsmartdockingparams)|Vrátí parametry inteligentní ukotvení pro ukotvení správce.|  
|[CDockingManager::GetSmartDockingTheme](#getsmartdockingtheme)|Statickou metodu, která vrátí motiv slouží k zobrazení inteligentní značky ukotvení.|  
|[CDockingManager::HideAutoHidePanes](#hideautohidepanes)|Skryje podokně, který je v režimu automaticky skrývat.|  
|[CDockingManager::InsertDockSite](#insertdocksite)|Vytvoří podokno ukotvení a vloží je do seznamu ovládací pruhy.|  
|[CDockingManager::InsertPane](#insertpane)|Vloží do seznamu ovládací pruhy podokně ovládacího prvku.|  
|[CDockingManager::IsDockSiteMenu](#isdocksitemenu)|Určuje, zda místní nabídky se zobrazí na titulky všech podoken.|  
|[CDockingManager::IsInAdjustLayout](#isinadjustlayout)|Určuje, pokud se upraví rozložení všech podoken.|  
|[CDockingManager::IsOLEContainerMode](#isolecontainermode)|Určuje, zda ukotvení manager je v režimu kontejneru OLE.|  
|[CDockingManager::IsPointNearDockSite](#ispointneardocksite)|Určuje, zda zadaný bod je téměř webu ukotvení.|  
|[CDockingManager::IsPrintPreviewValid](#isprintpreviewvalid)|Určuje, pokud má nastaven režim náhledu tisku.|  
|[CDockingManager::LoadState](#loadstate)|Načte stav ukotvení manager z registru.|  
|[CDockingManager::LockUpdate](#lockupdate)|Zamkne daného období.|  
|[CDockingManager::OnActivateFrame](#onactivateframe)|Voláno rámcem, když okně s rámečkem přišla active nebo je deaktivována.|  
|[CDockingManager::OnClosePopupMenu](#onclosepopupmenu)|Voláno rámcem když zpracovává zprávu WM_DESTROY active místní nabídky.|  
|[CDockingManager::OnMoveMiniFrame](#onmoveminiframe)|Voláno rámcem k přesunutí zkrácená rámce okna.|  
|[CDockingManager::OnPaneContextMenu](#onpanecontextmenu)|Voláno rámcem při vytváření nabídky, která má seznam podokna.|  
|[CDockingManager::PaneFromPoint](#panefrompoint)|Vrátí panel, který obsahuje danému bodu.|  
|[CDockingManager::ProcessPaneContextMenuCommand](#processpanecontextmenucommand)|Voláno rozhraním framework vyberte nebo zrušte zaškrtnutí políčka pro tento příkaz a přepočítat rozložení uvedené podokně.|  
|[CDockingManager::RecalcLayout](#recalclayout)|Přepočítá interní rozložení ovládacích prvků, která je uvedena v seznamu ovládacích prvků.|  
|[CDockingManager::ReleaseEmptyPaneContainers](#releaseemptypanecontainers)|Uvolní kontejnery prázdný podokně.|  
|[CDockingManager::RemoveHiddenMDITabbedBar](#removehiddenmditabbedbar)|Odebere zadaný skrytý panelu podokně.|  
|[CDockingManager::RemoveMiniFrame](#removeminiframe)|Odebere ze seznamu mini snímků zadaného rámce.|  
|[CDockingManager::RemovePaneFromDockManager](#removepanefromdockmanager)|Zruší registraci podokno a odstraní ji ze seznamu ve Správci ukotvení.|  
|[CDockingManager::ReplacePane](#replacepane)|Nahradí jednu podokně jiné.|  
|[CDockingManager::ResortMiniFramesForZOrder](#resortminiframesforzorder)|Používat rámce v seznamu mini snímků.|  
|[CDockingManager::SaveState](#savestate)|Uloží ukotvení správce stavu do registru.|  
|[CDockingManager::SendMessageToMiniFrames](#sendmessagetominiframes)|Odešle určenou zprávu na všechny mini snímky.|  
|[CDockingManager::Serialize](#serialize)|Ukotvení manager zapíše do archivu. (Přepisuje [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize).)|  
|[CDockingManager::SetAutohideZOrder](#setautohidezorder)|Nastaví velikost, šířku a výšku ovládacích pruhů a podokně zadaný.|  
|[CDockingManager::SetDockingMode](#setdockingmode)|Nastaví režim ukotvení.|  
|[CDockingManager::SetDockState](#setdockstate)|Nastaví ukotvení stav ovládací pruhy, mini rámce a autohide – řádky.|  
|[CDockingManager::SetPrintPreviewMode](#setprintpreviewmode)|Nastaví režim náhledu tisku pruhů, které se zobrazují v náhledu tisku.|  
|[CDockingManager::SetSmartDockingParams](#setsmartdockingparams)|Nastavuje parametry, které definují chování inteligentní ukotvení.|  
|[CDockingManager::ShowDelayShowMiniFrames](#showdelayshowminiframes)|Zobrazí nebo skryje windows mini snímků.|  
|[CDockingManager::ShowPanes](#showpanes)|Zobrazí nebo skryje podokna řízení a autohide – pruhů.|  
|[CDockingManager::StartSDocking](#startsdocking)|Spustí se inteligentní ukotvení zadané okno podle zarovnání správce inteligentní ukotvení.|  
|[CDockingManager::StopSDocking](#stopsdocking)|Zastaví inteligentní ukotvení.|  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CDockingManager::m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode)|Určuje, zda správce ukotvení skryje podokna v režimu kontejneru OLE.|  
|[CDockingManager::m_dockModeGlobal](#m_dockmodeglobal)|Určuje režim globální ukotvení.|  
|[CDockingManager::m_nDockSensitivity](#m_ndocksensitivity)|Určuje ukotvení velkých a malých písmen.|  
|[CDockingManager::m_nTimeOutBeforeDockingBarDock](#m_ntimeoutbeforedockingbardock)|Určuje čas v milisekundách, než je ukotvena ukotvené podokno v režimu okamžité ukotvení.|  
|[CDockingManager::m_nTimeOutBeforeToolBarDock](#m_ntimeoutbeforetoolbardock)|Určuje dobu v milisekundách, než panelu nástrojů ukotven do hlavního rámce okna.|  
  
## <a name="remarks"></a>Poznámky  
 Hlavní okno rámce vytvoří a automaticky inicializuje tuto třídu.  
  
 Ukotvení objekt správce obsahuje seznam všech podokna, které jsou v ukotvení rozložení a taky seznam všech [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) windows, které patří do hlavního rámce okna.  
  
 `CDockingManager` Třída implementuje některé služby, které můžete použít k vyhledání podokno nebo `CPaneFrameWnd` okno. Obvykle Nevolejte tyto služby přímo vzhledem k tomu, že jsou zabaleny v objektu hlavního rámce okna. Další informace najdete v tématu [CPaneFrameWnd třída](../../mfc/reference/cpaneframewnd-class.md).  
  
## <a name="customization-tips"></a>Tipy k přizpůsobení  
 Následující tipy, na které se týkají `CDockingManager` objekty:  
  
- [Třída CDockingManager](../../mfc/reference/cdockingmanager-class.md) podporuje tyto ukotvení režimy:  
  
    - `AFX_DOCK_TYPE::DT_IMMEDIATE`  
  
    - `AFX_DOCK_TYPE::DT_STANDARD`  
  
    - `AFX_DOCK_TYPE::DT_SMART`  
  
     Tyto režimy ukotvení jsou definovány [CDockingManager::m_dockModeGlobal](#m_dockmodeglobal) a jsou nastavené voláním [CDockingManager::SetDockingMode](#setdockingmode).  
  
-   Pokud chcete vytvořit s plovoucí, bez umožňující změnu velikosti podokna, zavolejte [CDockingManager::AddPane](#addpane) metoda. Tato metoda registruje v podokně ukotvení správce, který je zodpovědný za rozložení v podokně.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí různých metod v nástroji `CDockingManager` třída ke konfiguraci `CDockingManager` objektu. Příklad ukazuje, jak zobrazit další tlačítka, které se otevře místní nabídky na titulky všechny ukotvení podokna a jak nastavit ukotvení režimu objektu. Tento fragment kódu je součástí [Visual Studio Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#24](../../mfc/codesnippet/cpp/cdockingmanager-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDockingManager](../../mfc/reference/cdockingmanager-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxDockingManager.h  
  
##  <a name="adddocksite"></a>CDockingManager::AddDockSite  
 Vytvoří podokno ukotvení a přidá ho do seznamu ovládací pruhy.  
  
```  
BOOL AddDockSite(
    const AFX_DOCKSITE_INFO& info,  
    CDockSite** ppDockBar = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`info`  
 Odkaz na informace o struktuře, která obsahuje ukotvení podokně zarovnání.  
  
 [out]`ppDockBar`  
 Ukazatel na ukazatel na nové podokno ukotvení.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud se v podokně ukotvení úspěšně; vytvořil `FALSE` jinak.  
  
##  <a name="addhiddenmditabbedbar"></a>CDockingManager::AddHiddenMDITabbedBar  
 Přidá popisovač na panel podokně do seznamu skrytých MDI na kartách panelu podokna.  
  
```  
void AddHiddenMDITabbedBar(CDockablePane* pBar);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pBar`  
 Ukazatel na panel podokno  
  
##  <a name="addpane"></a>CDockingManager::AddPane  
 Zaregistruje podokno se správce ukotvení.  
  
```  
BOOL AddPane(
    CBasePane* pWnd,  
    BOOL bTail = TRUE,  
    BOOL bAutoHide = FALSE,  
    BOOL bInsertForOuterEdge = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [ve out]`pWnd`  
 Určuje, v podokně pro přidání do správce ukotvení.  
  
 [v]`bTail`  
 `TRUE`Chcete-li přidat v podokně na konec seznamu podokna pro ukotvení správce; v opačném `FALSE`.  
  
 [v]`bAutoHide`  
 Pouze pro interní použití. Vždy použijte výchozí hodnotu `FALSE`.  
  
 [v]`bInsertForOuterEdge`  
 Pouze pro interní použití. Vždy použijte výchozí hodnotu `FALSE`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud v podokně byl úspěšně zaregistrován pomocí ukotvení správce; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu pro registraci s plovoucí, bez umožňující změnu velikosti podokna se správce ukotvení. Pokud podokna nezaregistrujete, nezobrazí se správně při rozložená správce ukotvení.  
  
##  <a name="adjustdockinglayout"></a>CDockingManager::AdjustDockingLayout  
 Přepočítá a upraví rozložení všechny podokna v okně s rámečkem.  
  
```  
virtual void AdjustDockingLayout(HDWP hdwp = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`hdwp`  
 Určuje pozici strukturu odložené okna. Další informace najdete v tématu [Windows datové typy](http://msdn.microsoft.com/library/windows/desktop/aa383751).  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="addminiframe"></a>CDockingManager::AddMiniFrame  
 Rámeček se přidá do seznamu mini snímků.  
  
```  
virtual BOOL AddMiniFrame(CPaneFrameWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWnd`  
 Ukazatel na rámec.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud rámečku není v seznamu mini snímků a byl úspěšně; přidán `FALSE` jinak.  
  
##  <a name="adjustpaneframes"></a>CDockingManager::AdjustPaneFrames  
 Způsobí, že `WM_NCCALCSIZE` zpráva k odeslání do všech podokna a `CPaneFrameWnd` systému windows.  
  
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
 [v]`rectResult`  
 Odkaz na `CRect` objektu  
  
 [v]`dwAlignment`  
 Zarovnání `CRect` objektu  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud zarovnání `CRect` objektu byla upravena; `FALSE` jinak.  
  
### <a name="remarks"></a>Poznámky  
 `dwAlignment` Parametr může mít jeden z následujících hodnot:  
  
-   CBRS_ALIGN_TOP  
  
-   CBRS_ALIGN_BOTTOM  
  
-   CBRS_ALIGN_LEFT  
  
-   CBRS_ALIGN_RIGHT  
  
##  <a name="alignautohidepane"></a>CDockingManager::AlignAutoHidePane  
 Změní velikost ukotvené podokno v režimu autohide – tak, aby trvá úplné šířka nebo výška rámečku klientské oblasti obklopená ukotvení lokalit.  
  
```  
void AlignAutoHidePane(
    CPaneDivider* pDefaultSlider,  
    BOOL bIsVisible = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDefaultSlider`  
 V podokně ukotvení posuvníku.  
  
 [v]`bIsVisible`  
 `TRUE`Pokud se zobrazuje; ukotvení podokno `FALSE` jinak.  
  
##  <a name="autohidepane"></a>CDockingManager::AutoHidePane  
 Vytvoří automaticky skrývat nástrojů.  
  
```  
CMFCAutoHideToolBar* AutoHidePane(
    CDockablePane* pBar,  
    CMFCAutoHideToolBar* pCurrAutoHideToolBar = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pBar`  
 Ukazatel na panelu podokně.  
  
 [v]`pCurrAutoHideToolBar`  
 Ukazatel na automaticky skrytí panelu nástrojů.  
  
### <a name="return-value"></a>Návratová hodnota  
 `NULL`Pokud automatického skrytí panelu nástrojů nebyl vytvořen; v opačném případě ukazatel na nový panel nástrojů.  
  
##  <a name="bringbarstotop"></a>CDockingManager::BringBarsToTop  
 Přináší ukotveného řádky, které mají zadané zarovnání k nejvyšší.  
  
```  
void BringBarsToTop(
    DWORD dwAlignment = 0,  
    BOOL bExcludeDockedBars = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`dwAlignment`  
 Zarovnání ukotvení pruhů, které přesměrováni na začátku jiných windows.  
  
 [v]`bExcludeDockedBars`  
 `TRUE`vyloučit ukotveného řádky nebudou na maximum. v opačném případě `FALSE`.  
  
##  <a name="buildpanesmenu"></a>CDockingManager::BuildPanesMenu  
 Přidá názvy ukotvení podokna a panelů nástrojů k nabídce.  
  
```  
void BuildPanesMenu(
    CMenu& menu,  
    BOOL bToolbarsOnly);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`menu`  
 Nabídky přidat názvy ukotvení podokna a panelů nástrojů.  
  
 [v]`bToolbarsOnly`  
 `TRUE`Chcete-li přidat pouze názvy panelu nástrojů do nabídky; `FALSE` jinak.  
  
##  <a name="calcexpecteddockedrect"></a>CDockingManager::CalcExpectedDockedRect  
 Vypočítá očekávané rámeček ukotveného okna.  
  
```  
void CalcExpectedDockedRect(
    CWnd* pWnd,  
    CPoint ptMouse,  
    CRect& rectResult,  
    BOOL& bDrawTab,  
    CDockablePane** ppTargetBar);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWnd`  
 Ukazatel na okno na ukotvení.  
  
 [v]`ptMouse`  
 Umístění myši.  
  
 [out]`rectResult`  
 Počítaný obdélník.  
  
 [v]`bDrawTab`  
 `TRUE`Kreslení na kartě; v opačném případě `FALSE`.  
  
 [out]`ppTargetBar`  
 Ukazatel na ukazatel do podokna cíl.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vypočítá obdélníku, která by zabírají okno, pokud uživatel přetáhli okno bodu určeného `ptMouse` a jej ukotven existuje.  
  
##  <a name="create"></a>CDockingManager::Create  
 Vytvoří ukotvení správce.  
  
```  
BOOL Create(CFrameWnd* pParentWnd);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pParentWnd`  
 Ukazatel na rámec nadřazené ukotvení správce. Tato hodnota nesmí být `NULL`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`vždy.  
  
##  <a name="determinepaneandstatus"></a>CDockingManager::DeterminePaneAndStatus  
 Určuje, v podokně obsahující k danému bodu a stavu její ukotvení.  
  
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
 [v]`pt`  
 Umístění v podokně ke kontrole.  
  
 [v]`nSensitivity`  
 Hodnotu pro zvýšení obdélníku okna každý zaškrtnuté podokna. Podokno splňuje kritéria hledání, pokud je daný bod v této oblasti vyšší.  
  
 [v]`dwEnabledAlignment`  
 Zarovnání ukotvení panelu.  
  
 [out]`ppTargetBar`  
 Ukazatel na ukazatel do podokna cíl.  
  
 [v]`pBarToIgnore`  
 V podokně, která metoda bude ignorovat.  
  
 [v]`pBarToDock`  
 V podokně, který je ukotvena.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukotvení stav.  
  
### <a name="remarks"></a>Poznámky  
 Ukotvení stav může být jedna z následujících hodnot:  
  
|Hodnota AFX_CS_STATUS|Význam|  
|---------------------------|-------------|  
|CS_NOTHING|Ukazatel není přes lokalitu ukotvení. Proto ponechat podokno plovoucí.|  
|CS_DOCK_IMMEDIATELY|Je ukazatel myši nad webu ukotvení v přímý režim (DT_IMMEDIATE styl je povolená), tak v podokně musí být ukotven okamžitě.|  
|CS_DELAY_DOCK|Je ukazatel myši nad ukotvení lokalitu, která je jiného ukotvení panelu nebo okraj hlavního rámce.|  
|CS_DELAY_DOCK_TO_TAB|Ukazatele je nad ukotvení lokalitu, která způsobí, že podokno Ukotvit okno s kartami. K tomu dochází, při přesunutí myši na přes popisek jiné ukotvení panelu nebo přes oblast karty na kartách panelu.|  
  
##  <a name="disablerestoredockstate"></a>CDockingManager::DisableRestoreDockState  
 Povolí nebo zakáže načítání ukotvení rozložení z registru.  
  
```  
void DisableRestoreDockState(BOOL bDisable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bDisable`  
 `TRUE`Chcete-li zakázat načítání ukotvení rozložení z registru; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu volejte, když musíte zachovat aktuální rozložení ukotvení podokna a panelů nástrojů při načítání stavu aplikace.  
  
##  <a name="dockpane"></a>CDockingManager::DockPane  
 Podokno ukotvené jiného podokna nebo okně s rámečkem.  
  
```  
void DockPane(
    CBasePane* pBar,  
    UINT nDockBarID = 0,  
    LPCRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pBar`  
 Ukazatel na panel podokně ukotvit.  
  
 [v]`nDockBarID`  
 Id ukotvení panelu.  
  
 [v]`lpRect`  
 Cílový rámeček.  
  
##  <a name="dockpaneleftof"></a>CDockingManager::DockPaneLeftOf  
 Ukotvené podokno nalevo od jiného podokna.  
  
```  
BOOL DockPaneLeftOf(
    CPane* pBarToDock,  
    CPane* pTargetBar);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pBarToDock`  
 Ukazatel na podokno ukotvit nalevo od `pTargetBar`.  
  
 [v]`pTargetBar`  
 Ukazatel na podokně cíl.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud v podokně se ukotven úspěšně; v opačném `FALSE`.  
  
##  <a name="enableautohidepanes"></a>CDockingManager::EnableAutoHidePanes  
 Umožňuje ukotvení podokna do hlavního rámce, vytvoří podokno ukotvení a přidá ji do seznamu ovládací pruhy.  
  
```  
BOOL EnableAutoHidePanes(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`dwStyle`  
 Ukotvení zarovnání.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud se v podokně ukotvení úspěšně; vytvořil `FALSE` jinak.  
  
##  <a name="enabledocking"></a>CDockingManager::EnableDocking  
 Vytvoří podokno ukotvení a umožňuje ukotvení podokna do hlavního rámce.  
  
```  
BOOL EnableDocking(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`dwStyle`  
 Ukotvení zarovnání.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud se v podokně ukotvení úspěšně; vytvořil `FALSE` jinak.  
  
##  <a name="enabledocksitemenu"></a>CDockingManager::EnableDockSiteMenu  
 Zobrazí další tlačítko, které se otevře místní nabídky na titulky všechny ukotvení podokna.  
  
```  
static void EnableDockSiteMenu(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bEnable`  
 `TRUE`Chcete-li povolit v nabídce lokality ukotvení; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 V nabídce ukotvení lokality zobrazí následující možnosti pro změnu ukotvení stav v podokně:  
  
- `Floating`-Jako plovoucí podokno  
  
- `Docking`-Ukotvené panelu v hlavní rámečku tam, kde se v podokně poslední ukotveno  
  
- `AutoHide`-Přepne podokně do režimu autohide –  
  
- `Hide`-Skryje podokno  
  
 Ve výchozím nastavení tato nabídka se nezobrazí.  
  
##  <a name="enablepanecontextmenu"></a>CDockingManager::EnablePaneContextMenu  
 Říká knihovna zobrazíte speciální kontextové nabídky, která má seznam panelů nástrojů aplikace a ukotvení podokna při kliknutí pravým tlačítkem myši a knihovny je zpracování zpráv WM_CONTEXTMENU.  
  
```  
void EnablePaneContextMenu(
    BOOL bEnable,  
    UINT uiCustomizeCmd,  
    const CString& strCustomizeText,  
    BOOL bToolbarsOnly = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bEnable`  
 Pokud `TRUE`, knihovny zapne podpora pro automatické kontextovou nabídku; Pokud `FALSE` knihovny vypne podporu pro automatické kontextové nabídky.  
  
 [v]`uiCustomizeCmd`  
 Id příkazu pro **přizpůsobit** položky v nabídce.  
  
 [v]`strCustomizeText`  
 Text **přizpůsobit** položky.  
  
 [v]`bToolbarsOnly`  
 Pokud `TRUE`, v nabídce zobrazuje pouze seznam panelů nástrojů aplikace; Pokud `FALSE`, knihovny aplikace ukotvení podokna přidá do tohoto seznamu.  
  
##  <a name="finddocksite"></a>CDockingManager::FindDockSite  
 Načte panelu podokně, který je na zadané pozici a který má zadané zarovnání.  
  
```  
virtual CDockSite* FindDockSite(
    DWORD dwAlignment,  
    BOOL bOuter);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`dwAlignment`  
 Zarovnání panelu podokně.  
  
 [v]`bOuter`  
 Pokud `TRUE`, načtení panelu v head pozici v seznamu ovládací pruhy. Na panelu v tail pozici v seznamu ovládací pruhy, jinak hodnota načtěte.  
  
### <a name="return-value"></a>Návratová hodnota  
 V podokně ukotvení, který má zadané zarovnání; `NULL` jinak.  
  
##  <a name="findpanebyid"></a>CDockingManager::FindPaneByID  
 Vyhledá podokně podle ID ovládací prvek.  
  
```  
virtual CBasePane* FindPaneByID(
    UINT uBarID,  
    BOOL bSearchMiniFrames = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uBarID`  
 Určuje ID ovládacího prvku v podokně k vyhledání.  
  
 [v]`bSearchMiniFrames`  
 `TRUE`Chcete-li do vyhledávání přidat všechny plovoucí podokna. `FALSE`Zahrnout pouze ukotveného podokna.  
  
### <a name="return-value"></a>Návratová hodnota  
 [CBasePane](../../mfc/reference/cbasepane-class.md) objekt, který má zadaný ovládací prvek ID, nebo `NULL` Pokud nelze nalézt zadaný podokně.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="finddocksitebypane"></a>CDockingManager::FindDockSiteByPane  
 Vrátí panelu podokno, které má id panelu cílového řádku.  
  
```  
virtual CDockSite* FindDockSiteByPane(CPane* pTargetBar);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pTargetBar`  
 Ukazatel na panelu cílového řádku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Na panelu podokně, který má id panelu cílového řádku; `NULL` Pokud není žádná taková panelu podokně existuje.  
  
##  <a name="fixupvirtualrects"></a>CDockingManager::FixupVirtualRects  
 Potvrdí všechny aktuální pozic panelu nástrojů, který má virtuální obdélníky.  
  
```  
virtual void FixupVirtualRects();
```  
  
### <a name="remarks"></a>Poznámky  
 Když uživatel spustí přetáhněte panel nástrojů, aplikace si zapamatuje původní pozici v *virtuální obdélníku*. Když se uživatel přesune panel nástrojů napříč jeho ukotvení lokality, mohou být posunuty panelů nástrojů panelu nástrojů. Původní pozice jiných panelů jsou uloženy v odpovídající virtuální obdélníky.  
  
##  <a name="framefrompoint"></a>CDockingManager::FrameFromPoint  
 Vrátí rámce, který obsahuje danému bodu.  
  
```  
virtual CPaneFrameWnd* FrameFromPoint(
    CPoint pt,  
    CPaneFrameWnd* pFrameToExclude,  
    BOOL bFloatMultiOnly) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pt`  
 Určuje bod, v souřadnice obrazovky ke kontrole.  
  
 [v]`pFrameToExclude`  
 Ukazatel na rámec vyloučit.  
  
 [v]`bFloatMultiOnly`  
 `TRUE`vyloučit rámců, které nejsou instancí `CMultiPaneFrameWnd`; `FALSE` jinak.  
  
### <a name="return-value"></a>Návratová hodnota  
 Rámce, který obsahuje danému bodu; `NULL` jinak.  
  
##  <a name="getclientareabounds"></a>CDockingManager::GetClientAreaBounds  
 Získá obdélníku, která obsahuje hranice klientské oblasti.  
  
```  
CRect GetClientAreaBounds() const;

void GetClientAreaBounds(CRect& rcClient);
```  
  
### <a name="parameters"></a>Parametry  
 [out]`rcClient`  
 Odkaz na obdélníku, která obsahuje hranice klientské oblasti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Obdélníku, která obsahuje hranice klientské oblasti.  
  
##  <a name="getdockingmode"></a>CDockingManager::GetDockingMode  
 Vrátí aktuální režim ukotvení.  
  
```  
static AFX_DOCK_TYPE GetDockingMode();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnotu výčtu, který představuje aktuální režim ukotvení. Může být jedna z následujících hodnot:  
  
- `DT_STANDARD`  
  
- `DT_IMMEDIATE`  
  
- `DT_SMART`  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li nastavit ukotvení režim, volejte [CDockingManager::SetDockingMode](#setdockingmode).  
  
##  <a name="getdocksiteframewnd"></a>CDockingManager::GetDockSiteFrameWnd  
 Získá ukazatel na rámec okna nadřazené.  
  
```  
CFrameWnd* GetDockSiteFrameWnd() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rámec okna nadřazené.  
  
##  <a name="getenabledautohidealignment"></a>CDockingManager::GetEnabledAutoHideAlignment  
 Vrátí povoleno zarovnání podoken.  
  
```  
DWORD GetEnabledAutoHideAlignment() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Bitové kombinace `CBRS_ALIGN_` příznaky, nebo 0, pokud nejsou povolené autohide – podokna. Další informace najdete v tématu [CFrameWnd::EnableDocking](../../mfc/reference/cframewnd-class.md#enabledocking).  
  
### <a name="remarks"></a>Poznámky  
 Metoda vrátí povoleno zarovnání autohide – ovládací pruhy. Chcete-li povolit autohide – řádky, volejte [CFrameWndEx::EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes).  
  
##  <a name="getminiframes"></a>CDockingManager::GetMiniFrames  
 Získá seznam miniframes.  
  
```  
const CObList& GetMiniFrames() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Seznam miniframes, které obsahují ovládací pruhy, které patří do správce ukotvení.  
  
##  <a name="getouteredgebounds"></a>CDockingManager::GetOuterEdgeBounds  
 Získá obdélníku, který obsahuje vnější okrajů rámečku.  
  
```  
CRect GetOuterEdgeBounds() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Obdélníku, která obsahuje vnější okrajů rámečku.  
  
##  <a name="getpanelist"></a>CDockingManager::GetPaneList  
 Vrátí seznam hodnot podokna, které patří do správce ukotvení. To zahrnuje všechny plovoucí podokna.  
  
```  
void GetPaneList(
    CObList& lstBars,  
    BOOL bIncludeAutohide = FALSE,  
    CRuntimeClass* pRTCFilter = NULL,  
    BOOL bIncludeTabs = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [ve out]`lstBars`  
 Obsahuje všechny podokna aktuální ukotvení správce.  
  
 [v]`bIncludeAutohide`  
 `TRUE`Zahrnout podokna, které jsou v režimu autohide –; v opačném `FALSE`.  
  
 [v]`pRTCFilter`  
 Není-li `NULL`, vrácený seznam obsahuje podokna pouze třídy zadaného modulu runtime.  
  
 [v]`bIncludeTabs`  
 `TRUE`Zahrnout karty; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud nejsou žádné záložkách podokna ve ukotvení správci, vrátí metoda ukazatele na [CBaseTabbedPane třída](../../mfc/reference/cbasetabbedpane-class.md) objektů a vy musíte vytvořit výčet karty explicitně.  
  
 Použití `pRTCFilter` získat určité třídy podokna. Například můžete získat pouze panely nástrojů nastavením této hodnoty správně.  
  
##  <a name="getsmartdockingmanager"></a>CDockingManager::GetSmartDockingManager  
 Načte ukazatel správce inteligentní ukotvení.  
  
```  
CSmartDockingManager* GetSmartDockingManager();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [inteligentní ukotvení manager](http://msdn.microsoft.com/en-us/f537a1a6-fb9e-41d7-952f-0f25d5ee7534).  
  
##  <a name="getsmartdockingmanagerpermanent"></a>CDockingManager::GetSmartDockingManagerPermanent  
 Načte ukazatel správce inteligentní ukotvení.  
  
```  
CSmartDockingManager* GetSmartDockingManagerPermanent() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na inteligentní ukotvení správce.  
  
##  <a name="getsmartdockingparams"></a>CDockingManager::GetSmartDockingParams  
 Vrátí parametry inteligentní ukotvení pro ukotvení správce.  
  
```  
static CSmartDockingInfo& GetSmartDockingParams();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Třída, která obsahuje inteligentní ukotvení parametry pro aktuální ukotvení správce. Další informace najdete v tématu [CSmartDockingInfo třída](../../mfc/reference/csmartdockinginfo-class.md).  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="hideautohidepanes"></a>CDockingManager::HideAutoHidePanes  
 Skryje podokně, který je v režimu automaticky skrývat.  
  
```  
void HideAutoHidePanes(
    CDockablePane* pBarToExclude = NULL,  
    BOOL bImmediately = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pBarToExclude`  
 Ukazatel na panelu chcete vyloučit z skryté.  
  
 [v]`bImmediately`  
 `TRUE`Chcete-li skrýt podokno okamžitě; `FALSE` ke skrytí podokna s autohide – účinek.  
  
##  <a name="insertdocksite"></a>CDockingManager::InsertDockSite  
 Vytvoří podokno ukotvení a vloží je do seznamu ovládací pruhy.  
  
```  
BOOL InsertDockSite(
    const AFX_DOCKSITE_INFO& info,  
    DWORD dwAlignToInsertAfter,  
    CDockSite** ppDockBar = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`info`  
 Struktura, která obsahuje zarovnání informace o podokně ukotvení.  
  
 [v]`dwAlignToInsertAfter`  
 Zarovnání ukotvení panelu.  
  
 [out]`ppDockBar`  
 Ukazatel na ukazatel na podokně ukotvení.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud se v podokně ukotvení úspěšně; vytvořil `FALSE` jinak.  
  
##  <a name="insertpane"></a>CDockingManager::InsertPane  
 Vloží do seznamu ovládací pruhy podokně ovládacího prvku.  
  
```  
BOOL InsertPane(
    CBasePane* pControlBar,  
    CBasePane* pTarget,  
    BOOL bAfter = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pControlBar`  
 Ukazatel na podokně ovládacího prvku.  
  
 [v]`pTarget`  
 Ukazatel na cílové podokně.  
  
 [v]`bAfter`  
 `TRUE`Chcete-li vložit v podokně po pozici v podokně cíl; `FALSE` jinak.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud v podokně ovládacího prvku se úspěšně přidal do seznamu ovládací pruhy; `FALSE` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vrátí hodnotu false, pokud v podokně ovládacího prvku je již v seznamu ovládací pruhy nebo pokud podokně cíl neexistuje v seznamu ovládací pruhy.  
  
##  <a name="isdocksitemenu"></a>CDockingManager::IsDockSiteMenu  
 Určuje, zda místní nabídky se zobrazí na titulky všech podoken.  
  
```  
static BOOL IsDockSiteMenu();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud ukotvení lokality nabídky se zobrazí na titulky všechny ukotvení podokna; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Můžete povolit v nabídce lokality ukotvení voláním [CDockingManager::EnableDockSiteMenu](#enabledocksitemenu).  
  
##  <a name="isinadjustlayout"></a>CDockingManager::IsInAdjustLayout  
 Určuje, pokud se upraví rozložení všech podoken.  
  
```  
BOOL IsInAdjustLayout() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud se upraví rozložení všech podoken; `FALSE` jinak.  
  
##  <a name="isolecontainermode"></a>CDockingManager::IsOLEContainerMode  
 Určuje, zda ukotvení manager je v režimu kontejneru OLE.  
  
```  
BOOL IsOLEContainerMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud správce ukotvení je v režimu OLE kontejneru; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 V režimu kontejneru OLE všechny ukotvení podokna a panelů nástrojů aplikace jsou skryté. Podokna jsou rovněž skryté v tomto režimu, pokud jste nastavili [CDockingManager::m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode) k `TRUE`.  
  
##  <a name="ispointneardocksite"></a>CDockingManager::IsPointNearDockSite  
 Určuje, zda zadaný bod je téměř webu ukotvení.  
  
```  
BOOL IsPointNearDockSite(
    CPoint point,  
    DWORD& dwBarAlignment,  
    BOOL& bOuterEdge) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`point`  
 Zadaný bod.  
  
 [out]`dwBarAlignment`  
 Určuje, které hraniční bod je téměř. Možné hodnoty jsou `CBRS_ALIGN_LEFT`, `CBRS_ALIGN_RIGHT`, `CBRS_ALIGN_TOP`, a `CBRS_ALIGN_BOTTOM`.  
  
 [out]`bOuterEdge`  
 `TRUE`Pokud je bod téměř vnější ohraničení ukotvení serveru. `FALSE` jinak.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud je bod téměř webu ukotvení; v opačném případě `FALSE`.  
  
##  <a name="isprintpreviewvalid"></a>CDockingManager::IsPrintPreviewValid  
 Určuje, pokud má nastaven režim náhledu tisku.  
  
```  
BOOL IsPrintPreviewValid() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud má nastaven režim náhledu tisku; `FALSE` jinak.  
  
##  <a name="loadstate"></a>CDockingManager::LoadState  
 Načte stav ukotvení manager z registru.  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszProfileName`  
 Název profilu.  
  
 [v]`uiID`  
 Id správce ukotvení.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud stav ukotvení manager byl úspěšně; načten. v opačném případě `FALSE`.  
  
##  <a name="lockupdate"></a>CDockingManager::LockUpdate  
 Zamkne daného období.  
  
```  
void LockUpdate(BOOL bLock);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bLock`  
 `TRUE`Pokud okno uzamčen; `FALSE` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Pokud okno je uzamčena, nelze jej přesunout a nemůže být vystavena.  
  
##  <a name="m_bhidedockingbarsincontainermode"></a>CDockingManager::m_bHideDockingBarsInContainerMode  
 Určuje, zda správce ukotvení skryje podokna v režimu kontejneru OLE.  
  
```  
AFX_IMPORT_DATA static BOOL m_bHideDockingBarsInContainerMode;  
```  
  
### <a name="remarks"></a>Poznámky  
 Nastavte hodnotu `FALSE` Pokud chcete zachovat všechny podokna ukotvena hlavního rámce viditelné pokud aplikace je v režimu kontejneru OLE. Ve výchozím nastavení, tato hodnota je `TRUE`.  
  
##  <a name="m_dockmodeglobal"></a>CDockingManager::m_dockModeGlobal  
 Určuje režim globální ukotvení.  
  
```  
AFX_IMPORT_DATA static AFX_DOCK_TYPE m_dockModeGlobal;  
```  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení používá každý ukotvení podokně tento režim ukotvení. Další informace o hodnoty, které toto pole může být nastaveno na najdete v tématu [CBasePane::GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode).  
  
##  <a name="m_ndocksensitivity"></a>CDockingManager::m_nDockSensitivity  
 Určuje ukotvení velkých a malých písmen.  
  
```  
AFX_IMPORT_DATA static int m_nDockSensitivity;  
```  
  
### <a name="remarks"></a>Poznámky  
 Ukotvení citlivosti definuje, jak blízko plovoucí podokně můžete postupovat ukotvené podokno, ukotvení lokality nebo jiného podokna před rozhraní změnit její stav na ukotven.  
  
##  <a name="m_ntimeoutbeforedockingbardock"></a>CDockingManager::m_nTimeOutBeforeDockingBarDock  
 Určuje čas v milisekundách, než je ukotvena ukotvené podokno v režimu okamžité ukotvení.  
  
```  
static UINT m_nTimeOutBeforeDockingBarDock;  
```  
  
### <a name="remarks"></a>Poznámky  
 Předtím, než je ukotvena podokno, rozhraní framework čeká Zadaná délka času. V podokně zabrání se omylem ukotven do umístění, když uživatel je stále přetáhnete ho.  
  
##  <a name="m_ntimeoutbeforetoolbardock"></a>CDockingManager::m_nTimeOutBeforeToolBarDock  
 Určuje dobu v milisekundách, než panelu nástrojů ukotven do hlavního rámce okna.  
  
```  
static UINT m_nTimeOutBeforeToolBarDock;  
```  
  
### <a name="remarks"></a>Poznámky  
 Předtím, než je ukotvena panel nástrojů, rozhraní framework čeká Zadaná délka času. To brání se omylem ukotven do umístění, když uživatel je stále přetáhnete ji panelu nástrojů.  
  
##  <a name="onactivateframe"></a>CDockingManager::OnActivateFrame  
 Voláno rámcem, když okně s rámečkem přišla active nebo je deaktivována.  
  
```  
virtual void OnActivateFrame(BOOL bActivate);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bActivate`  
 Pokud `TRUE`, okně s rámečkem přišla active; Pokud `FALSE`, okně s rámečkem je deaktivována.  
  
##  <a name="onclosepopupmenu"></a>CDockingManager::OnClosePopupMenu  
 Voláno rámcem když zpracovává zprávu WM_DESTROY active místní nabídky.  
  
```  
void OnClosePopupMenu();
```  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework odešle zprávu WM_DESTROY, pokud je aktuální hlavní okno zavřít. Potlačí tuto metodu pro zpracování oznámení z `CMFCPopupMenu` objekty, které patří do okna s rámečkem při `CMFCPopupMenu` objektu procesy `WM_DESTROY` zprávy.  
  
##  <a name="onmoveminiframe"></a>CDockingManager::OnMoveMiniFrame  
 Voláno rámcem k přesunutí zkrácená rámce okna.  
  
```  
virtual BOOL OnMoveMiniFrame(CWnd* pFrame);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pFrame`  
 Ukazatel na zkrácená rámce okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud metoda úspěšně. v opačném případě `FALSE`.  
  
##  <a name="onpanecontextmenu"></a>CDockingManager::OnPaneContextMenu  
 Voláno rámcem při vytváření nabídky, která má seznam podokna.  
  
```  
void OnPaneContextMenu(CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`point`  
 Určuje umístění v nabídce.  
  
##  <a name="panefrompoint"></a>CDockingManager::PaneFromPoint  
 Vrátí panel, který obsahuje danému bodu.  
  
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
 [v]`point`  
 Určuje bod, v souřadnice obrazovky ke kontrole.  
  
 [v]`nSensitivity`  
 Hodnota k zvýšilo obdélníku okna každý zaškrtnuté podokna. Podokno splňuje kritéria hledání, pokud je daný bod v této oblasti zvýšeným.  
  
 [v]`bExactBar`  
 `TRUE`Ignorovat `nSensitivity` parametr, jinak hodnota `FALSE`.  
  
 [v]`pRTCBarType`  
 Není-li `NULL`, tato metoda vyhledá pouze podokna zadaného typu.  
  
 [v]`bCheckVisibility`  
 `TRUE`Chcete-li zkontrolovat jenom viditelné podokna; v opačném `FALSE`.  
  
 [out]`dwAlignment`  
 Pokud podokno se nachází zde zadaný bod, tento parametr obsahuje na straně panelu, který je nejblíže k Zadaný bod. Další informace najdete v části poznámky.  
  
 [v]`pBarToIgnore`  
 Není-li `NULL`, metoda ignoruje podokna určeného tento parametr.  
  
### <a name="return-value"></a>Návratová hodnota  
 [CBasePane](../../mfc/reference/cbasepane-class.md)-odvozené objekt, který obsahuje danému bodu nebo `NULL` Pokud nebyl nalezen žádný podokně.  
  
### <a name="remarks"></a>Poznámky  
 Když funkce vrátí hodnotu a byla nalezena podokno, `dwAlignment` obsahuje zarovnání Zadaný bod. Například, pokud byl bod nejblíže k horní části podokna `dwAlignment` je nastaven na `CBRS_ALIGN_TOP`.  
  
##  <a name="processpanecontextmenucommand"></a>CDockingManager::ProcessPaneContextMenuCommand  
 Voláno rozhraním framework vyberte nebo zrušte zaškrtnutí políčka pro tento příkaz a přepočítat rozložení uvedené podokně.  
  
```  
BOOL ProcessPaneContextMenuCommand(
    UINT nID,  
    int nCode,  
    void* pExtra,  
    AFX_CMDHANDLERINFO* pHandlerInfo);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nID`  
 Id ovládacích pruhů v nabídce.  
  
 [v]`nCode`  
 Příkaz oznámení kód.  
  
 [v]`pExtra`  
 Ukazatel na void, která je převedena na ukazatel na `CCmdUI` Pokud `nCode` je CN_UPDATE_COMMAND_UI.  
  
 [v]`pHandlerInfo`  
 Ukazatel na strukturu informace. Tento parametr není používán.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud `pEXtra` není NULL a `nCode` rovná CN_UPDATE_COMMAND_UI, nebo pokud je panel prvek se zadaným `nID`.  
  
##  <a name="recalclayout"></a>CDockingManager::RecalcLayout  
 Přepočítá interní rozložení ovládacích prvků, která je uvedena v seznamu ovládacích prvků.  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bNotify`  
 Tento parametr není používán.  
  
##  <a name="releaseemptypanecontainers"></a>CDockingManager::ReleaseEmptyPaneContainers  
 Uvolní kontejnery prázdný podokně.  
  
```  
void ReleaseEmptyPaneContainers();
```  
  
##  <a name="removehiddenmditabbedbar"></a>CDockingManager::RemoveHiddenMDITabbedBar  
 Odebere zadaný skrytý panelu podokně.  
  
```  
void RemoveHiddenMDITabbedBar(CDockablePane* pBar);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pBar`  
 Ukazatel na panel podokně odebrat.  
  
##  <a name="removeminiframe"></a>CDockingManager::RemoveMiniFrame  
 Odebere ze seznamu mini snímků zadaného rámce.  
  
```  
virtual BOOL RemoveMiniFrame(CPaneFrameWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWnd`  
 Ukazatel na rámec odebrat.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud je odebrán zadaného rámce; `FALSE` jinak.  
  
##  <a name="removepanefromdockmanager"></a>CDockingManager::RemovePaneFromDockManager  
 Zruší registraci podokno a odstraní ji ze seznamu ve Správci ukotvení.  
  
```  
void RemovePaneFromDockManager(
    CBasePane* pWnd,  
    BOOL bDestroy,  
    BOOL bAdjustLayout,  
    BOOL bAutoHide = FALSE,  
    CBasePane* pBarReplacement = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWnd`  
 Ukazatel na podokně odeberou.  
  
 [v]`bDestroy`  
 Pokud `TRUE`, odebrané podokně zničena.  
  
 [v]`bAdjustLayout`  
 Pokud `TRUE`, upravte ukotvení rozložení okamžitě.  
  
 [v]`bAutoHide`  
 Pokud `TRUE`, v podokně se odebere ze seznamu autohide – řádky. Pokud `FALSE`, v podokně se odebere ze seznamu regulární podokna.  
  
 [v]`pBarReplacement`  
 Ukazatel na podokně, který nahrazuje podokně odebrané.  
  
##  <a name="replacepane"></a>CDockingManager::ReplacePane  
 Nahradí jednu podokně jiné.  
  
```  
BOOL ReplacePane(
    CDockablePane* pOriginalBar,  
    CDockablePane* pNewBar);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pOriginalBar`  
 Ukazatel na původní podokně.  
  
 [v]`pNewBar`  
 Ukazatel na podokně, který nahrazuje původní podokně.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud je v podokně úspěšně nahradil; `FALSE` jinak.  
  
##  <a name="resortminiframesforzorder"></a>CDockingManager::ResortMiniFramesForZOrder  
 Používat rámce v seznamu mini snímků.  
  
```  
void ResortMiniFramesForZOrder();
```  
  
##  <a name="savestate"></a>CDockingManager::SaveState  
 Uloží ukotvení správce stavu do registru.  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszProfileName`  
 Cesta ke klíči registru.  
  
 [v]`uiID`  
 Ukotvení ID správce.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud byl úspěšně; uložen stav v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Ukládání stavu ukotvení manager registru uloženo stavy ovládací pruhy, stavy autohide – řádky a stavy mini rámce, který je součástí Správce ukotvení.  
  
##  <a name="sendmessagetominiframes"></a>CDockingManager::SendMessageToMiniFrames  
 Odešle určenou zprávu na všechny mini snímky.  
  
```  
BOOL SendMessageToMiniFrames(
    UINT uMessage,  
    WPARAM wParam = 0,  
    LPARAM lParam = 0);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uMessage`  
 Zpráva, která má být odeslána.  
  
 [v]`wParam`  
 Informace závislé další zprávy.  
  
 [v]`lParam`  
 Informace závislé další zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`vždy.  
  
##  <a name="serialize"></a>CDockingManager::Serialize  
 Ukotvení manager zapíše do archivu.  
  
```  
void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`ar`  
 Odkaz na objekt archivu.  
  
### <a name="remarks"></a>Poznámky  
 Zápis do archivu ukotvení manager zahrnuje určení počtu ukotvení ovládací pruhy a posuvníky a zápis ovládací pruhy, mini rámce, autohide – řádky a řádky MDI – záložkami do archivu.  
  
##  <a name="setautohidezorder"></a>CDockingManager::SetAutohideZOrder  
 Nastaví velikost, šířku a výšku ovládacích pruhů a podokně zadaný.  
  
```  
void SetAutohideZOrder(CDockablePane* pAHDockingBar);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pAHDockingBar`  
 Ukazatel na lze ukotvit podokně.  
  
##  <a name="setdockingmode"></a>CDockingManager::SetDockingMode  
 Nastaví režim ukotvení.  
  
```  
static void SetDockingMode(
    AFX_DOCK_TYPE dockMode,  
    AFX_SMARTDOCK_THEME theme = AFX_SDT_DEFAULT);
```  
  
### <a name="parameters"></a>Parametry  
 `dockMode`  
 Určuje nový režim ukotvení. Další informace najdete v části poznámky.  
  
 `theme`  
 Určuje, jaký motiv se použije pro inteligentní značky ukotvení. Může být jeden z následujících výčtové hodnoty: AFX_SDT_DEFAULT, AFX_SDT_VS2005, AFX_SDT_VS2008.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu statické nastavení ukotvení režimu.  
  
 `dockMode`může být jedna z následujících hodnot:  
  
- `DT_STANDARD`-Ukotvení režimu, jak jsou implementované ve Visual Studio .NET 2003 standard. Podokna jsou přetáhnout bez přetahování kontextu.  
  
- `DT_IMMEDIATE`-Přímý režim ukotvení jako implementována v aplikaci Microsoft Visio. Podokna jsou přetáhnout pomocí přetahování kontextu, ale budou zobrazeny žádné značky.  
  
- `DT_SMART`-Inteligentní ukotvení režimu, jak jsou implementované v sadě Visual Studio 2005. Podokna jsou přetáhnout pomocí přetahování kontextu a budou zobrazeny inteligentní značky, zobrazit, kde můžete v podokně ukotven.  
  
##  <a name="setdockstate"></a>CDockingManager::SetDockState  
 Nastaví ukotvení stav ovládací pruhy, mini rámce a autohide – řádky.  
  
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
 [v]`bPreview`  
 `TRUE`Pokud má nastaven režim náhledu tisku; `FALSE` jinak.  
  
 [v]`pState`  
 Ukazatel na stav preview. Tento parametr není používán.  
  
##  <a name="setsmartdockingparams"></a>CDockingManager::SetSmartDockingParams  
 Nastavuje parametry, které definují chování inteligentní ukotvení.  
  
```  
static void SetSmartDockingParams(CSmartDockingInfo& params);
```  
  
### <a name="parameters"></a>Parametry  
 [ve out]`params`  
 Definuje parametry pro inteligentní ukotvení.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu, pokud chcete přizpůsobit vzhled, barvu nebo tvar značky inteligentního ukotvení.  
  
 Chcete-li používat výchozí vzhled pro inteligentní značky ukotvení, předat Neinicializovaný instance [CSmartDockingInfo třída](../../mfc/reference/csmartdockinginfo-class.md) k `params`.  
  
##  <a name="showdelayshowminiframes"></a>CDockingManager::ShowDelayShowMiniFrames  
 Zobrazí nebo skryje windows mini snímků.  
  
```  
void ShowDelayShowMiniFrames(BOOL bshow);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bShow`  
 `TRUE`Chcete-li aktivovat okno zobrazené rámce; `FALSE to` skrýt okna rámečku.  
  
##  <a name="showpanes"></a>CDockingManager::ShowPanes  
 Zobrazí nebo skryje podokna řízení a autohide – pruhů.  
  
```  
virtual BOOL ShowPanes(BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bShow`  
 `TRUE`k zobrazení podokna; `FALSE to` skryta.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy `FALSE`.  
  
##  <a name="startsdocking"></a>CDockingManager::StartSDocking  
 Spustí se inteligentní ukotvení zadané okno podle zarovnání správce inteligentní ukotvení.  
  
```  
void StartSDocking(CWnd* pDockingWnd);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDockingWnd`  
 Ukazatel na okno chcete ukotvit.  
  
##  <a name="stopsdocking"></a>CDockingManager::StopSDocking  
 Zastaví inteligentní ukotvení.  
  
```  
void StopSDocking();
```  
  
##  <a name="getsmartdockingtheme"></a>CDockingManager::GetSmartDockingTheme  
 Statickou metodu, která vrátí motiv slouží k zobrazení inteligentní značky ukotvení.  
  
```  
static AFX_SMARTDOCK_THEME __stdcall GetSmartDockingTheme();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících výčtové hodnoty: AFX_SDT_DEFAULT, AFX_SDT_VS2005, AFX_SDT_VS2008.  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [CFrameWndEx – třída](../../mfc/reference/cframewndex-class.md)   
 [CDockablePane – třída](../../mfc/reference/cdockablepane-class.md)   
 [CPaneFrameWnd – třída](../../mfc/reference/cpaneframewnd-class.md)
