---
title: Třída CFrameWndEx | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFrameWndEx
- AFXFRAMEWNDEX/CFrameWndEx
- AFXFRAMEWNDEX/CFrameWndEx::ActiveItemRecalcLayout
- AFXFRAMEWNDEX/CFrameWndEx::AddPane
- AFXFRAMEWNDEX/CFrameWndEx::AdjustDockingLayout
- AFXFRAMEWNDEX/CFrameWndEx::DelayUpdateFrameMenu
- AFXFRAMEWNDEX/CFrameWndEx::DockPane
- AFXFRAMEWNDEX/CFrameWndEx::DockPaneLeftOf
- AFXFRAMEWNDEX/CFrameWndEx::EnableAutoHidePanes
- AFXFRAMEWNDEX/CFrameWndEx::EnableDocking
- AFXFRAMEWNDEX/CFrameWndEx::EnableFullScreenMainMenu
- AFXFRAMEWNDEX/CFrameWndEx::EnableFullScreenMode
- AFXFRAMEWNDEX/CFrameWndEx::EnableLoadDockState
- AFXFRAMEWNDEX/CFrameWndEx::EnablePaneMenu
- AFXFRAMEWNDEX/CFrameWndEx::GetActivePopup
- AFXFRAMEWNDEX/CFrameWndEx::GetDefaultResId
- AFXFRAMEWNDEX/CFrameWndEx::GetDockingManager
- AFXFRAMEWNDEX/CFrameWndEx::GetMenuBar
- AFXFRAMEWNDEX/CFrameWndEx::GetPane
- AFXFRAMEWNDEX/CFrameWndEx::GetRibbonBar
- AFXFRAMEWNDEX/CFrameWndEx::GetTearOffBars
- AFXFRAMEWNDEX/CFrameWndEx::GetToolbarButtonToolTipText
- AFXFRAMEWNDEX/CFrameWndEx::InsertPane
- AFXFRAMEWNDEX/CFrameWndEx::IsFullScreen
- AFXFRAMEWNDEX/CFrameWndEx::IsMenuBarAvailable
- AFXFRAMEWNDEX/CFrameWndEx::IsPointNearDockSite
- AFXFRAMEWNDEX/CFrameWndEx::IsPrintPreview
- AFXFRAMEWNDEX/CFrameWndEx::LoadFrame
- AFXFRAMEWNDEX/CFrameWndEx::NegotiateBorderSpace
- AFXFRAMEWNDEX/CFrameWndEx::OnActivate
- AFXFRAMEWNDEX/CFrameWndEx::OnActivateApp
- AFXFRAMEWNDEX/CFrameWndEx::OnChangeVisualManager
- AFXFRAMEWNDEX/CFrameWndEx::OnClose
- AFXFRAMEWNDEX/CFrameWndEx::OnCloseDockingPane
- AFXFRAMEWNDEX/CFrameWndEx::OnCloseMiniFrame
- AFXFRAMEWNDEX/CFrameWndEx::OnClosePopupMenu
- AFXFRAMEWNDEX/CFrameWndEx::OnCmdMsg
- AFXFRAMEWNDEX/CFrameWndEx::OnContextHelp
- AFXFRAMEWNDEX/CFrameWndEx::OnCreate
- AFXFRAMEWNDEX/CFrameWndEx::OnDestroy
- AFXFRAMEWNDEX/CFrameWndEx::OnDrawMenuImage
- AFXFRAMEWNDEX/CFrameWndEx::OnDrawMenuLogo
- AFXFRAMEWNDEX/CFrameWndEx::OnDWMCompositionChanged
- AFXFRAMEWNDEX/CFrameWndEx::OnExitSizeMove
- AFXFRAMEWNDEX/CFrameWndEx::OnGetMinMaxInfo
- AFXFRAMEWNDEX/CFrameWndEx::OnIdleUpdateCmdUI
- AFXFRAMEWNDEX/CFrameWndEx::OnLButtonDown
- AFXFRAMEWNDEX/CFrameWndEx::OnLButtonUp
- AFXFRAMEWNDEX/CFrameWndEx::OnMenuButtonToolHitTest
- AFXFRAMEWNDEX/CFrameWndEx::OnMenuChar
- AFXFRAMEWNDEX/CFrameWndEx::OnMouseMove
- AFXFRAMEWNDEX/CFrameWndEx::OnMoveMiniFrame
- AFXFRAMEWNDEX/CFrameWndEx::OnNcActivate
- AFXFRAMEWNDEX/CFrameWndEx::OnNcCalcSize
- AFXFRAMEWNDEX/CFrameWndEx::OnNcHitTest
- AFXFRAMEWNDEX/CFrameWndEx::OnNcMouseMove
- AFXFRAMEWNDEX/CFrameWndEx::OnNcPaint
- AFXFRAMEWNDEX/CFrameWndEx::OnPaneCheck
- AFXFRAMEWNDEX/CFrameWndEx::OnPostPreviewFrame
- AFXFRAMEWNDEX/CFrameWndEx::OnPowerBroadcast
- AFXFRAMEWNDEX/CFrameWndEx::OnSetMenu
- AFXFRAMEWNDEX/CFrameWndEx::OnSetPreviewMode
- AFXFRAMEWNDEX/CFrameWndEx::OnSetText
- AFXFRAMEWNDEX/CFrameWndEx::OnShowCustomizePane
- AFXFRAMEWNDEX/CFrameWndEx::OnShowPanes
- AFXFRAMEWNDEX/CFrameWndEx::OnShowPopupMenu
- AFXFRAMEWNDEX/CFrameWndEx::OnSize
- AFXFRAMEWNDEX/CFrameWndEx::OnSizing
- AFXFRAMEWNDEX/CFrameWndEx::OnSysColorChange
- AFXFRAMEWNDEX/CFrameWndEx::OnTearOffMenu
- AFXFRAMEWNDEX/CFrameWndEx::OnToolbarContextMenu
- AFXFRAMEWNDEX/CFrameWndEx::OnToolbarCreateNew
- AFXFRAMEWNDEX/CFrameWndEx::OnToolbarDelete
- AFXFRAMEWNDEX/CFrameWndEx::OnUpdateFrameMenu
- AFXFRAMEWNDEX/CFrameWndEx::OnUpdateFrameTitle
- AFXFRAMEWNDEX/CFrameWndEx::OnUpdatePaneMenu
- AFXFRAMEWNDEX/CFrameWndEx::OnWindowPosChanged
- AFXFRAMEWNDEX/CFrameWndEx::PaneFromPoint
- AFXFRAMEWNDEX/CFrameWndEx::PreTranslateMessage
- AFXFRAMEWNDEX/CFrameWndEx::RecalcLayout
- AFXFRAMEWNDEX/CFrameWndEx::RemovePaneFromDockManager
- AFXFRAMEWNDEX/CFrameWndEx::SetDockState
- AFXFRAMEWNDEX/CFrameWndEx::SetPrintPreviewFrame
- AFXFRAMEWNDEX/CFrameWndEx::SetupToolbarMenu
- AFXFRAMEWNDEX/CFrameWndEx::ShowFullScreen
- AFXFRAMEWNDEX/CFrameWndEx::ShowPane
- AFXFRAMEWNDEX/CFrameWndEx::UpdateCaption
- AFXFRAMEWNDEX/CFrameWndEx::WinHelp
dev_langs:
- C++
helpviewer_keywords:
- CFrameWndEx [MFC], ActiveItemRecalcLayout
- CFrameWndEx [MFC], AddPane
- CFrameWndEx [MFC], AdjustDockingLayout
- CFrameWndEx [MFC], DelayUpdateFrameMenu
- CFrameWndEx [MFC], DockPane
- CFrameWndEx [MFC], DockPaneLeftOf
- CFrameWndEx [MFC], EnableAutoHidePanes
- CFrameWndEx [MFC], EnableDocking
- CFrameWndEx [MFC], EnableFullScreenMainMenu
- CFrameWndEx [MFC], EnableFullScreenMode
- CFrameWndEx [MFC], EnableLoadDockState
- CFrameWndEx [MFC], EnablePaneMenu
- CFrameWndEx [MFC], GetActivePopup
- CFrameWndEx [MFC], GetDefaultResId
- CFrameWndEx [MFC], GetDockingManager
- CFrameWndEx [MFC], GetMenuBar
- CFrameWndEx [MFC], GetPane
- CFrameWndEx [MFC], GetRibbonBar
- CFrameWndEx [MFC], GetTearOffBars
- CFrameWndEx [MFC], GetToolbarButtonToolTipText
- CFrameWndEx [MFC], InsertPane
- CFrameWndEx [MFC], IsFullScreen
- CFrameWndEx [MFC], IsMenuBarAvailable
- CFrameWndEx [MFC], IsPointNearDockSite
- CFrameWndEx [MFC], IsPrintPreview
- CFrameWndEx [MFC], LoadFrame
- CFrameWndEx [MFC], NegotiateBorderSpace
- CFrameWndEx [MFC], OnActivate
- CFrameWndEx [MFC], OnActivateApp
- CFrameWndEx [MFC], OnChangeVisualManager
- CFrameWndEx [MFC], OnClose
- CFrameWndEx [MFC], OnCloseDockingPane
- CFrameWndEx [MFC], OnCloseMiniFrame
- CFrameWndEx [MFC], OnClosePopupMenu
- CFrameWndEx [MFC], OnCmdMsg
- CFrameWndEx [MFC], OnContextHelp
- CFrameWndEx [MFC], OnCreate
- CFrameWndEx [MFC], OnDestroy
- CFrameWndEx [MFC], OnDrawMenuImage
- CFrameWndEx [MFC], OnDrawMenuLogo
- CFrameWndEx [MFC], OnDWMCompositionChanged
- CFrameWndEx [MFC], OnExitSizeMove
- CFrameWndEx [MFC], OnGetMinMaxInfo
- CFrameWndEx [MFC], OnIdleUpdateCmdUI
- CFrameWndEx [MFC], OnLButtonDown
- CFrameWndEx [MFC], OnLButtonUp
- CFrameWndEx [MFC], OnMenuButtonToolHitTest
- CFrameWndEx [MFC], OnMenuChar
- CFrameWndEx [MFC], OnMouseMove
- CFrameWndEx [MFC], OnMoveMiniFrame
- CFrameWndEx [MFC], OnNcActivate
- CFrameWndEx [MFC], OnNcCalcSize
- CFrameWndEx [MFC], OnNcHitTest
- CFrameWndEx [MFC], OnNcMouseMove
- CFrameWndEx [MFC], OnNcPaint
- CFrameWndEx [MFC], OnPaneCheck
- CFrameWndEx [MFC], OnPostPreviewFrame
- CFrameWndEx [MFC], OnPowerBroadcast
- CFrameWndEx [MFC], OnSetMenu
- CFrameWndEx [MFC], OnSetPreviewMode
- CFrameWndEx [MFC], OnSetText
- CFrameWndEx [MFC], OnShowCustomizePane
- CFrameWndEx [MFC], OnShowPanes
- CFrameWndEx [MFC], OnShowPopupMenu
- CFrameWndEx [MFC], OnSize
- CFrameWndEx [MFC], OnSizing
- CFrameWndEx [MFC], OnSysColorChange
- CFrameWndEx [MFC], OnTearOffMenu
- CFrameWndEx [MFC], OnToolbarContextMenu
- CFrameWndEx [MFC], OnToolbarCreateNew
- CFrameWndEx [MFC], OnToolbarDelete
- CFrameWndEx [MFC], OnUpdateFrameMenu
- CFrameWndEx [MFC], OnUpdateFrameTitle
- CFrameWndEx [MFC], OnUpdatePaneMenu
- CFrameWndEx [MFC], OnWindowPosChanged
- CFrameWndEx [MFC], PaneFromPoint
- CFrameWndEx [MFC], PreTranslateMessage
- CFrameWndEx [MFC], RecalcLayout
- CFrameWndEx [MFC], RemovePaneFromDockManager
- CFrameWndEx [MFC], SetDockState
- CFrameWndEx [MFC], SetPrintPreviewFrame
- CFrameWndEx [MFC], SetupToolbarMenu
- CFrameWndEx [MFC], ShowFullScreen
- CFrameWndEx [MFC], ShowPane
- CFrameWndEx [MFC], UpdateCaption
- CFrameWndEx [MFC], WinHelp
ms.assetid: 5830aca8-4a21-4f31-91f1-dd5477ffcc8d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e806d622e79fe57039b85dc77860b07b956ece1a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cframewndex-class"></a>CFrameWndEx – třída
Implementuje jeden dokument (SDI rozhraní) překryté nebo oken s rámečkem místní funkci systému Windows a poskytuje členy pro správu okna. Ji rozšiřuje [CFrameWnd](../../mfc/reference/cframewnd-class.md) třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CFrameWndEx : public CFrameWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CFrameWndEx::ActiveItemRecalcLayout](#activeitemrecalclayout)|Upraví rozložení OLE klientské položky a rámečku klientské oblasti.|  
|`CFrameWndEx::AddDockSite`|Tato metoda se nepoužije.|  
|[CFrameWndEx::AddPane](#addpane)|Registruje ovládacích pruhů správce ukotvení.|  
|[CFrameWndEx::AdjustDockingLayout](#adjustdockinglayout)|Přepočítá rozložení všech podoken, které jsou ukotvena rámce okna.|  
|[CFrameWndEx::DelayUpdateFrameMenu](#delayupdateframemenu)|Nastaví v nabídce a pak aktualizuje při zpracování příkazu nečinnosti.|  
|[CFrameWndEx::DockPane](#dockpane)|Ukotvené podokně zadané do rámce okna.|  
|[CFrameWndEx::DockPaneLeftOf](#dockpaneleftof)|Ukotvené jeden podokně nalevo od jiného podokna.|  
|[CFrameWndEx::EnableAutoHidePanes](#enableautohidepanes)|Umožňuje automaticky skrýt režim pro podoken při ukotvena zadaný postranní hlavního rámce okna.|  
|[CFrameWndEx::EnableDocking](#enabledocking)|Umožňuje ukotvení podokna, které patří do rámce okna.|  
|[CFrameWndEx::EnableFullScreenMainMenu](#enablefullscreenmainmenu)|Zobrazí nebo skryje hlavní nabídky v režimu celé obrazovky.|  
|[CFrameWndEx::EnableFullScreenMode](#enablefullscreenmode)|Povolí režim celé obrazovky pro rámce okna.|  
|[CFrameWndEx::EnableLoadDockState](#enableloaddockstate)|Povolí nebo zakáže načítání ukotvení stavu.|  
|[CFrameWndEx::EnablePaneMenu](#enablepanemenu)|Povolí nebo zakáže automatické zpracování nabídky panelu.|  
|[CFrameWndEx::GetActivePopup](#getactivepopup)|Vrací ukazatel na aktuálně zobrazené místní nabídky.|  
|[CFrameWndEx::GetDefaultResId](#getdefaultresid)|Vrátí ID prostředku, který jste zadali při načítání rozhraní rámce okna.|  
|[CFrameWndEx::GetDockingManager](#getdockingmanager)|Načte [CDockingManager třída](../../mfc/reference/cdockingmanager-class.md) objekt pro rámce okna.|  
|[CFrameWndEx::GetMenuBar](#getmenubar)|Vrací ukazatel na objekt nabídky panelu připojené k rámce okna.|  
|[CFrameWndEx::GetPane](#getpane)|Vrací ukazatel na podokně, který má zadané ID.|  
|[CFrameWndEx::GetRibbonBar](#getribbonbar)|Načte ovládacích prvků pásu karet panelu pro rámečku.|  
|[CFrameWndEx::GetTearOffBars](#gettearoffbars)|Vrátí seznam hodnot podokně objekty, které jsou ve stavu úplné vypnutí.|  
|[CFrameWndEx::GetToolbarButtonToolTipText](#gettoolbarbuttontooltiptext)|Voláno rámcem, pokud aplikace zobrazí popisek pro tlačítka panelu nástrojů.|  
|[CFrameWndEx::InsertPane](#insertpane)|Zaregistruje podokno se správce ukotvení.|  
|[CFrameWndEx::IsFullScreen](#isfullscreen)|Určuje, zda okně s rámečkem v režimu celé obrazovky.|  
|[CFrameWndEx::IsMenuBarAvailable](#ismenubaravailable)|Určuje, zda má ukazatel na objekt nabídky panelu je platný.|  
|[CFrameWndEx::IsPointNearDockSite](#ispointneardocksite)|Určuje, zda bod nachází v zóně zarovnání.|  
|[CFrameWndEx::IsPrintPreview](#isprintpreview)|Určuje, zda okně s rámečkem v režimu náhledu tisku.|  
|[CFrameWndEx::LoadFrame](#loadframe)|Tato metoda je volána po konstrukce vytvořit okně s rámečkem a načíst jeho prostředky.|  
|[CFrameWndEx::NegotiateBorderSpace](#negotiateborderspace)|Vyjednávání implementuje OLE klienta ohraničení.|  
|[CFrameWndEx::OnActivate](#onactivate)|Tato metoda volá framework při vstupu uživatele je přepnuta do nebo od rámečku.|  
|[CFrameWndEx::OnActivateApp](#onactivateapp)|Voláno rámcem při vybrané nebo nevybrány aplikace.|  
|[CFrameWndEx::OnChangeVisualManager](#onchangevisualmanager)|Voláno rámcem, kdy ke změně rámečku vyžaduje změnu visual správce.|  
|[CFrameWndEx::OnClose](#onclose)|Rozhraní framework volá tuto metodu za účelem zavřete rámečku.|  
|[CFrameWndEx::OnCloseDockingPane](#onclosedockingpane)|Voláno rámcem, když uživatel klikne **Zavřít** tlačítko v podokně ukotvení.|  
|[CFrameWndEx::OnCloseMiniFrame](#oncloseminiframe)|Voláno rámcem, když uživatel klikne **Zavřít** tlačítko na plovoucího mini rámce okna.|  
|[CFrameWndEx::OnClosePopupMenu](#onclosepopupmenu)|Voláno rámcem když zpracovává zprávu WM_DESTROY active místní nabídky.|  
|[CFrameWndEx::OnCmdMsg](#oncmdmsg)|Odešle příkaz zprávy.|  
|[CFrameWndEx::OnContextHelp](#oncontexthelp)|Voláno rámcem zobrazení kontextu souvisejících s nápovědy.|  
|[CFrameWndEx::OnCreate](#oncreate)|Voláno rámcem po vytvoření rámečku.|  
|[CFrameWndEx::OnDestroy](#ondestroy)|Voláno rámcem při rámečku zničena.|  
|[CFrameWndEx::OnDrawMenuImage](#ondrawmenuimage)|Voláno rámcem, pokud aplikace nakreslí obrázek přidružený k položce nabídky.|  
|[CFrameWndEx::OnDrawMenuLogo](#ondrawmenulogo)|Voláno rámcem při `CMFCPopupMenu` objektu procesy [WM_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213) zprávy.|  
|[CFrameWndEx::OnDWMCompositionChanged](#ondwmcompositionchanged)|Voláno rámcem Pokud složení plochy okno správce (správce) byla zapnutá nebo vypnutá.|  
|[CFrameWndEx::OnExitSizeMove](#onexitsizemove)|Voláno rámcem při zastavení rámečku přesunutí nebo změnou velikosti.|  
|[CFrameWndEx::OnGetMinMaxInfo](#ongetminmaxinfo)|Voláno rámcem při změně velikosti rámečku můžete nastavit omezení okna dimenze.|  
|[CFrameWndEx::OnIdleUpdateCmdUI](#onidleupdatecmdui)|Voláno rámcem aktualizovat zobrazení rámce při zpracování příkazu nečinnosti.|  
|[CFrameWndEx::OnLButtonDown](#onlbuttondown)|Rozhraní framework volá tuto metodu, když uživatel stiskne levé tlačítko.|  
|[CFrameWndEx::OnLButtonUp](#onlbuttonup)|Rozhraní framework volá tuto metodu, když uživatel uvolní levé tlačítko.|  
|[CFrameWndEx::OnMenuButtonToolHitTest](#onmenubuttontoolhittest)|Voláno rámcem při `CMFCToolBarButton` objektu procesy `WM_NCHITTEST` zprávy.|  
|[CFrameWndEx::OnMenuChar](#onmenuchar)|Voláno rámcem, když se zobrazí nabídky a uživatel stiskne klíč, který neodpovídá žádnému příkazu.|  
|[CFrameWndEx::OnMouseMove](#onmousemove)|Tato metoda volá framework při umístění ukazatele.|  
|[CFrameWndEx::OnMoveMiniFrame](#onmoveminiframe)|Voláno rámcem, pokud se přesune podokně okna.|  
|[CFrameWndEx::OnNcActivate](#onncactivate)|Voláno rámcem při neklientská oblast rámečku musí překreslen signalizovat změnu v aktivním stavu.|  
|[CFrameWndEx::OnNcCalcSize](#onnccalcsize)|Voláno rámcem při vypočítat velikost a umístění klienta.|  
|[CFrameWndEx::OnNcHitTest](#onnchittest)|Voláno rámcem při umístění ukazatele nebo při stisknutí tlačítka nebo uvolnění tlačítka myši.|  
|[CFrameWndEx::OnNcMouseMove](#onncmousemove)|Voláno rámcem při umístění ukazatele v neklientská oblast.|  
|[CFrameWndEx::OnNcPaint](#onncpaint)|Voláno rámcem při musí být vykresluje neklientská oblast.|  
|[CFrameWndEx::OnPaneCheck](#onpanecheck)|Voláno rámcem řízení zobrazení podokna.|  
|[CFrameWndEx::OnPostPreviewFrame](#onpostpreviewframe)|Voláno rámcem, když uživatel došlo ke změně režimu náhledu tisku.|  
|[CFrameWndEx::OnPowerBroadcast](#onpowerbroadcast)|Voláno rámcem při výskytu události správy napájení.|  
|[CFrameWndEx::OnSetMenu](#onsetmenu)|Voláno rámcem nahradit nabídku rámce okna.|  
|[CFrameWndEx::OnSetPreviewMode](#onsetpreviewmode)|Voláno rámcem nastavení režimu náhledu tisku pro rámečku.|  
|[CFrameWndEx::OnSetText](#onsettext)|Voláno rámcem nastavit text časového období.|  
|[CFrameWndEx::OnShowCustomizePane](#onshowcustomizepane)|Voláno rámcem při přizpůsobení rychlé podokně je povoleno.|  
|[CFrameWndEx::OnShowPanes](#onshowpanes)|Voláno rámcem zobrazení nebo skrytí podokna.|  
|[CFrameWndEx::OnShowPopupMenu](#onshowpopupmenu)|Voláno rámcem, pokud je povolena místní nabídky.|  
|[CFrameWndEx::OnSize](#onsize)|Tato metoda volá framework po změně velikosti rámečku.|  
|[CFrameWndEx::OnSizing](#onsizing)|Rozhraní framework volá tuto metodu, když uživatel změní velikost rámečku.|  
|[CFrameWndEx::OnSysColorChange](#onsyscolorchange)|Voláno rámcem při změně barvy systému.|  
|[CFrameWndEx::OnTearOffMenu](#ontearoffmenu)|Voláno rámcem, pokud je nabídka, která má panel úplné vypnutí povolena.|  
|[CFrameWndEx::OnToolbarContextMenu](#ontoolbarcontextmenu)|Voláno rámcem k sestavení z kontextové nabídky panelu nástrojů.|  
|[CFrameWndEx::OnToolbarCreateNew](#ontoolbarcreatenew)|Rozhraní framework volá tuto metodu za účelem vytvoření nové panelu nástrojů.|  
|[CFrameWndEx::OnToolbarDelete](#ontoolbardelete)|Voláno rámcem při odstranění panelu nástrojů.|  
|[CFrameWndEx::OnUpdateFrameMenu](#onupdateframemenu)|Voláno rámcem nastavit v nabídce.|  
|[CFrameWndEx::OnUpdateFrameTitle](#onupdateframetitle)|Rozhraní framework volá tuto metodu za účelem aktualizace na záhlaví okna rámce.|  
|[CFrameWndEx::OnUpdatePaneMenu](#onupdatepanemenu)|Voláno rámcem aktualizace nabídky panelu.|  
|[CFrameWndEx::OnWindowPosChanged](#onwindowposchanged)|Voláno rámcem, když velikost rámce, umístění a pořadí z-order se změnil z důvodu volání metody okno správy.|  
|[CFrameWndEx::PaneFromPoint](#panefrompoint)|Vrátí podokně ukotvení, která obsahuje zadaný bod.|  
|[CFrameWndEx::PreTranslateMessage](#pretranslatemessage)|Předtím, než je odesláno, který zpracovává zprávy konkrétní okno.|  
|[CFrameWndEx::RecalcLayout](#recalclayout)|Upraví rozložení rámečku a jeho podřízené systému windows.|  
|[CFrameWndEx::RemovePaneFromDockManager](#removepanefromdockmanager)|Zruší registraci podokno a odstraní ji ze seznamu interní ve Správci ukotvení.|  
|[CFrameWndEx::SetDockState](#setdockstate)|Obnoví ukotvení rozložení ukotvení stavu uložené v registru.|  
|[CFrameWndEx::SetPrintPreviewFrame](#setprintpreviewframe)|Nastaví rámce okna náhledu tisku.|  
|[CFrameWndEx::SetupToolbarMenu](#setuptoolbarmenu)|Vloží příkazy uživatelem definované do nabídky panelu nástrojů.|  
|[CFrameWndEx::ShowFullScreen](#showfullscreen)|Přepne hlavního rámce mezi na celé obrazovce a režimů regulární.|  
|[CFrameWndEx::ShowPane](#showpane)|Zobrazí nebo skryje podokně zadaný.|  
|[CFrameWndEx::UpdateCaption](#updatecaption)|Voláno rámcem aktualizovat titulek rámce okna.|  
|[CFrameWndEx::WinHelp](#winhelp)|Vyvolá buď `WinHelp` aplikace nebo kontext související s nápovědy.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak dědit ze třídy `CFrameWndEx` třídy. Příklad ukazuje, metoda podpisů v podtřídy a jak lze přepsat `OnShowPopupMenu` metoda. Tento fragment kódu je součástí [ukázkové aplikace Word Pad](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad#3](../../mfc/reference/codesnippet/cpp/cframewndex-class_1.h)]  
[!code-cpp[NVC_MFC_WordPad#4](../../mfc/reference/codesnippet/cpp/cframewndex-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CFrameWndEx](../../mfc/reference/cframewndex-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxframewndex.h  
  
##  <a name="activeitemrecalclayout"></a>  CFrameWndEx::ActiveItemRecalcLayout  
 Upraví rozložení OLE klientské položky a rámečku klientské oblasti.  
  
```  
void ActiveItemRecalcLayout();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="addpane"></a>  CFrameWndEx::AddPane  
 Registruje ovládacích pruhů správce ukotvení.  
  
```  
BOOL AddPane(
    CBasePane* pControlBar,  
    BOOL bTail=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pControlBar`  
 Ovládací prvek panelu řádku k registraci.  
  
 [v] `bTail`  
 `TRUE` Pokud chcete přidat panelu řádku ovládací prvek na konec seznamu; `FALSE` jinak.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud byl úspěšně zaregistrován ovládacích pruhů; `FALSE` jinak.  
  
##  <a name="adjustdockinglayout"></a>  CFrameWndEx::AdjustDockingLayout  
 Přepočítá rozložení všech podoken, které jsou ukotvena rámce okna.  
  
```  
virtual void AdjustDockingLayout(HDWP hdwp=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `hdwp`  
 Popisovač pro strukturu, která obsahuje pozice více oken. .  
  
### <a name="remarks"></a>Poznámky  
 Struktura hdwp se inicializuje pomocí [BeginDeferWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms632672) metoda.  
  
##  <a name="delayupdateframemenu"></a>  CFrameWndEx::DelayUpdateFrameMenu  
 Nastaví v nabídce a pak aktualizuje při zpracování příkazu nečinnosti.  
  
```  
virtual void DelayUpdateFrameMenu(HMENU hMenuAlt);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `hMenuAlt`  
 Zpracování do alternativní nabídky.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="dockpane"></a>  CFrameWndEx::DockPane  
 Ukotvené podokně zadané do rámce okna.  
  
```  
void DockPane(
    CBasePane* pBar,  
    UINT nDockBarID=0,  
    LPCRECT lpRect=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pBar`  
 Ukazatel na panelu řízení ukotvit.  
  
 [v] `nDockBarID`  
 ID na straně okna rámce chcete ukotvit k.  
  
 [v] `lpRect`  
 Ukazatel na konstantní Rect – struktura, která určuje pozici obrazovky a velikost okna.  
  
### <a name="remarks"></a>Poznámky  
 `nDockBarID` Parametr může mít jeden z následujících hodnot:  
  
-   AFX_IDW_DOCKBAR_TOP  
  
-   AFX_IDW_DOCKBAR_BOTTOM  
  
-   AFX_IDW_DOCKBAR_LEFT  
  
-   AFX_IDW_DOCKBAR_RIGHT  
  
##  <a name="dockpaneleftof"></a>  CFrameWndEx::DockPaneLeftOf  
 V podokně zadaný ukotvené nalevo od jiného podokna.  
  
```  
BOOL DockPaneLeftOf(
    CPane* pBar,  
    CPane* pLeftOf);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pBar`  
 Ukazatel na podokně objekt, který chcete ukotvit.  
  
 [v] `pLeftOf`  
 Ukazatel do podokna na levé straně, které chcete ukotvit podokně určeného `pBar`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud `pBar` ukotven úspěšně. `FALSE` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přebírá panelu nástrojů určeného `pBar` parametr a přepraviště ho na levé straně panelu nástrojů určeného `pLeftOf` parametr.  
  
##  <a name="enableautohidepanes"></a>  CFrameWndEx::EnableAutoHidePanes  
 Umožňuje automaticky skrýt režim pro podokně při ukotven k zadané straně hlavního okna rámce.  
  
```  
BOOL EnableAutoHidePanes(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `dwDockStyle`  
 Určuje straně okna hlavního rámce, do které chcete ukotvit podokně.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud panelu podokně úspěšně ukotven na straně rámce okna, která je zadána `dwDockStyle`, `FALSE` jinak.  
  
### <a name="remarks"></a>Poznámky  
 `dwDockStyle` Může mít jednu z následujících hodnot:  
  
-   CBRS_ALIGN_TOP: umožňuje panelu řízení ukotvit do horní části klientské oblasti okně s rámečkem.  
  
-   CBRS_ALIGN_BOTTOM: umožňuje panelu řízení ukotvit k dolnímu okraji klientské oblasti okně s rámečkem.  
  
-   CBRS_ALIGN_LEFT: umožňuje panelu řízení ukotveny na levé straně klientské oblasti okně s rámečkem.  
  
-   CBRS_ALIGN_RIGHT: umožňuje panelu řízení ukotveny na pravé straně klientské oblasti okně s rámečkem.  
  
##  <a name="enabledocking"></a>  CFrameWndEx::EnableDocking  
 Umožňuje ukotvení podokna rámce okna.  
  
```  
BOOL EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `dwDockStyle`  
 Určuje na straně, kde panelu podokně ukotvené hlavního rámce okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud panelu podokně můžete úspěšně ukotvení v zadané straně. `FALSE` jinak.  
  
### <a name="remarks"></a>Poznámky  
 `dwDockStyle` Parametr může mít jeden z následujících hodnot:  
  
-   CBRS_ALIGN_TOP  
  
-   CBRS_ALIGN_BOTTOM  
  
-   CBRS_ALIGN_LEFT  
  
-   CBRS_ALIGN_RIGHT  
  
##  <a name="enablefullscreenmainmenu"></a>  CFrameWndEx::EnableFullScreenMainMenu  
 Zobrazí nebo skryje hlavní nabídky v režimu celé obrazovky.  
  
```  
void EnableFullScreenMainMenu(BOOL bEnableMenu);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bEnableMenu`  
 `TRUE` Zobrazit hlavní nabídky v režimu celé obrazovky, `FALSE` jinak.  
  
##  <a name="enablefullscreenmode"></a>  CFrameWndEx::EnableFullScreenMode  
 Umožňuje celoobrazovkový režim pro rámce okna.  
  
```  
void EnableFullScreenMode(UINT uiFullScreenCmd);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `uiFullScreenCmd`  
 ID příkazu, který povolí nebo zakáže režim celé obrazovky.  
  
### <a name="remarks"></a>Poznámky  
 V režimu celé obrazovky ukotvení ovládací pruhy, panely nástrojů a nabídky jsou skryté a aktivní zobrazení se změnila velikost tak, aby zabíral na celé obrazovce.  
  
 Když povolíte celoobrazovkový režim, musíte zadat ID příkazu, který povolí nebo zakáže režim celé obrazovky. Můžete volat `EnableFullScreenMode` z hlavního rámce `OnCreate` funkce. Když okně s rámečkem se přepne do režimu přes celou obrazovku, rozhraní framework vytvoří plovoucí panel nástrojů s jedno tlačítko, který má zadaný příkaz ID.  
  
 Pokud chcete zachovat hlavní nabídky na obrazovce, zavolejte [CFrameWndEx::EnableFullScreenMainMenu](#enablefullscreenmainmenu).  
  
##  <a name="enableloaddockstate"></a>  CFrameWndEx::EnableLoadDockState  
 Povolí nebo zakáže načítání ukotvení stavu.  
  
```  
void EnableLoadDockState(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bEnable`  
 `TRUE` Chcete-li povolit načítání ukotvení stavu `FALSE` zakázat načítání ukotvení stavu.  
  
##  <a name="enablepanemenu"></a>  CFrameWndEx::EnablePaneMenu  
 Povolí nebo zakáže automatické zpracování nabídky panelu.  
  
```  
void EnablePaneMenu(
    BOOL bEnable,  
    UINT uiCustomizeCmd,  
    const CString& strCustomizeLabel,  
    UINT uiViewToolbarsMenuEntryID,  
    BOOL bContextMenuShowsToolbarsOnly=FALSE,  
    BOOL bViewMenuShowsToolbarsOnly=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bEnable`  
 `TRUE` Chcete-li povolit automatické zpracování ovládacího panelu Místní nabídky; `FALSE` zakázat automatické zpracování ovládacího panelu Místní nabídky.  
  
 [v] `uiCustomizeCmd`  
 ID příkazu **přizpůsobit** položku nabídky.  
  
 [v] `strCustomizeLabel`  
 Popisek, který se zobrazí u **přizpůsobit** položky nabídky  
  
 [v] `uiViewToolbarsMenuEntryID`  
 ID položku nabídky panelu nástrojů, které se otevře místní nabídky v ovládacím panelu.  
  
 [v] `bContextMenuShowsToolbarsOnly`  
 Pokud `TRUE`, ovládacího panelu místní nabídce zobrazí seznam pouze panely nástrojů. Pokud `FALSE`, v nabídce zobrazí seznam panely nástrojů a ukotvení řádky.  
  
 [v] `bViewMenuShowsToolbarsOnly`  
 Pokud `TRUE`, v nabídce ovládací prvek panelu zobrazí seznam pouze panely nástrojů. Pokud `FALSE`, v nabídce zobrazí seznam panely nástrojů a ukotvení řádky.  
  
##  <a name="getactivepopup"></a>  CFrameWndEx::GetActivePopup  
 Vrací ukazatel na aktuálně zobrazené místní nabídky.  
  
```  
CMFCPopupMenu* GetActivePopup() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na aktuálně zobrazené místní nabídky; v opačném případě `NULL`.  
  
##  <a name="getdefaultresid"></a>  CFrameWndEx::GetDefaultResId  
 Vrátí ID prostředku, který jste zadali při načítání rozhraní rámce okna.  
  
```  
UINT GetDefaultResId() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota ID prostředku, aby uživatel zadal při načtení rozhraní rámce okna. Nula, pokud okně s rámečkem nemá řádku nabídek.  
  
##  <a name="getdockingmanager"></a>  CFrameWndEx::GetDockingManager  
 Načte [CDockingManager třída](../../mfc/reference/cdockingmanager-class.md) objekt pro rámce okna.  
  
```  
CDockingManager* GetDockingManager();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CDockingManager třída](../../mfc/reference/cdockingmanager-class.md).  
  
### <a name="remarks"></a>Poznámky  
 Okně s rámečkem vytvoří a použije [CDockingManager třída](../../mfc/reference/cdockingmanager-class.md) objekt, který chcete spravovat, podřízené okno ukotvení.  
  
##  <a name="getmenubar"></a>  CFrameWndEx::GetMenuBar  
 Vrací ukazatel na objekt nabídky panelu připojené k rámce okna.  
  
```  
const CMFCMenuBar* GetMenuBar() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na objekt nabídky panelu připojené k rámce okna.  
  
##  <a name="getpane"></a>  CFrameWndEx::GetPane  
 Vrací ukazatel na podokně, který má zadané ID.  
  
```  
CBasePane* GetPane(UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nID`  
 ID ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na podokně, který má zadané ID. `NULL` Pokud žádná taková podokně existuje.  
  
##  <a name="getribbonbar"></a>  CFrameWndEx::GetRibbonBar  
 Načte ovládacích prvků pásu karet panelu pro rámečku.  
  
```  
CMFCRibbonBar* GetRibbonBar();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md) pro rámečku.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="gettearoffbars"></a>  CFrameWndEx::GetTearOffBars  
 Vrátí seznam hodnot podokně objekty, které jsou ve stavu úplné vypnutí.  
  
```  
const CObList& GetTearOffBars() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na `CObList` objekt, který obsahuje kolekci ukazatelé na objekty podokně, které jsou ve stavu úplné vypnutí.  
  
##  <a name="gettoolbarbuttontooltiptext"></a>  CFrameWndEx::GetToolbarButtonToolTipText  
 Voláno rámcem, pokud aplikace zobrazí popisek pro tlačítka panelu nástrojů.  
  
```  
virtual BOOL GetToolbarButtonToolTipText(
    CMFCToolBarButton* pButton,  
    CString& strTTText);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pButton`  
 Ukazatel na tlačítka panelu nástrojů.  
  
 [v] `strTTText`  
 Text popisku, který má být zobrazen pro tlačítko.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je zobrazené v popisku. `FALSE` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tato metoda neprovede žádnou akci. Potlačí tuto metodu, pokud chcete zobrazit popis tlačítka pro tlačítko panelu nástrojů.  
  
##  <a name="insertpane"></a>  CFrameWndEx::InsertPane  
 Vloží do seznamu ovládací pruhy podokno a zaregistruje ho se správce ukotvení.  
  
```  
BOOL InsertPane(
    CBasePane* pControlBar,  
    CBasePane* pTarget,  
    BOOL bAfter=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pControlBar`  
 Ukazatel na ovládací prvek panelu vloženy do seznamu ovládací pruhy a registraci pomocí ukotvení správce.  
  
 `pTarget`  
 Ukazatel na ovládací prvek panelu před nebo po kterém se má vložit v podokně.  
  
 `bAfter`  
 `TRUE` Pokud chcete vložit `pControlBar` po `pTarget`, `FALSE` jinak.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud byl úspěšně vložit, zaregistrovaný, ovládacích pruhů `FALSE` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Každý ovládací prvek panelu je nutné zaregistrovat pomocí [CDockingManager třída](../../mfc/reference/cdockingmanager-class.md) neúčastní ukotvení rozložení.  
  
##  <a name="isfullscreen"></a>  CFrameWndEx::IsFullScreen  
 Určuje, zda okně s rámečkem v režimu celé obrazovky.  
  
```  
BOOL IsFullScreen() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je okně s rámečkem v režimu celé obrazovky; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Režim celé obrazovky můžete nastavit tak, že zavoláte [CFrameWndEx::EnableFullScreenMode](#enablefullscreenmode) metoda.  
  
##  <a name="ismenubaravailable"></a>  CFrameWndEx::IsMenuBarAvailable  
 Určuje, zda má ukazatel na objekt nabídky panelu je platný.  
  
```  
BOOL IsMenuBarAvailable() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud okně s rámečkem má řádek nabídek. v opačném případě `FALSE`.  
  
##  <a name="ispointneardocksite"></a>  CFrameWndEx::IsPointNearDockSite  
 Určuje, zda bod nachází v zóně zarovnání.  
  
```  
BOOL IsPointNearDockSite(
    CPoint point,  
    DWORD& dwBarAlignment,  
    BOOL& bOuterEdge) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `point`  
 Pozice bodu.  
  
 [out] `dwBarAlignment`  
 Kde je zarovnán bodem. Najdete v tabulce v části poznámky pro možné hodnoty.  
  
 [out] `bOuterEdge`  
 `TRUE` Pokud se bod nachází blízko ohraničení rámečku; `FALSE` Pokud se bod nachází v oblasti klienta.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud se bod nachází v zóně zarovnání; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 V následující tabulce jsou uvedeny možné hodnoty `dwBarAlignment` parametr.  
  
 `CBRS_ALIGN_TOP`  
 Zarovnán na začátek.  
  
 `CBRS_ALIGN_RIGHT`  
 Zarovnání doprava.  
  
 `CBRS_ALIGN_BOTTOM`  
 Zarovnané dolů.  
  
 `CBRS_ALIGN_LEFT`  
 Zarovnání na levé straně.  
  
##  <a name="isprintpreview"></a>  CFrameWndEx::IsPrintPreview  
 Určuje, zda okně s rámečkem v režimu náhledu tisku.  
  
```  
BOOL IsPrintPreview();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je okně s rámečkem v režimu náhledu tisku; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="loadframe"></a>  CFrameWndEx::LoadFrame  
 Tato metoda je volána po konstrukce vytvořit okně s rámečkem a načíst jeho prostředky.  
  
```  
virtual BOOL LoadFrame(
    UINT nIDResource,  
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,  
    CWnd* pParentWnd = NULL,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nIDResource`  
 ID prostředku, který slouží k načtení všech zdrojů rámce.  
  
 [v] `dwDefaultStyle`  
 Výchozí styl oken rámce.  
  
 [v] `pParentWnd`  
 Ukazatel do nadřazeného okna rámečku.  
  
 [v] `pContext`  
 Ukazatel na [CCreateContext struktura](../../mfc/reference/ccreatecontext-structure.md) třídu, která používá rozhraní během vytváření aplikace.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud metoda byla úspěšná. v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="negotiateborderspace"></a>  CFrameWndEx::NegotiateBorderSpace  
 Vyjednávání implementuje OLE klienta ohraničení.  
  
```  
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,  
    LPRECT lpRectBorder);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nBorderCmd`  
 Příkaz vyjednávání ohraničení. Možné hodnoty v části poznámky.  
  
 [ve out] `lpRectBorder`  
 Dimenze ohraničení.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud se musí přepočítat rozložení; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 V následující tabulce jsou uvedeny možné hodnoty `nBorderCmd` parametr.  
  
 `borderGet`  
 Získáte volné místo klienta OLE.  
  
 `borderRequest`  
 Žádost místa klienta OLE.  
  
 `borderSet`  
 Nastavení klienta místo OLE.  
  
##  <a name="onactivate"></a>  CFrameWndEx::OnActivate  
 Tato metoda volá framework při vstupu uživatele je přepnuta do nebo od rámečku.  
  
```  
afx_msg void OnActivate(
    UINT nState,  
    CWnd* pWndOther,  
    BOOL bMinimized);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nState`  
 Jestli rámečku je aktivní nebo neaktivní. Najdete v tabulce v části poznámky pro možné hodnoty.  
  
 [v] `pWndOther`  
 Ukazatel na další okno, který je přepínání vstup uživatele s aktuální.  
  
 [v] `bMinimized`  
 Minimalizované stav rámečku. `TRUE` Pokud je minimalizován rámečku; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 V následující tabulce jsou uvedeny možné hodnoty `nState` parametr.  
  
 `WA_ACTIVE`  
 Rámečku je vybrána jako jiné metody než kliknutí myší.  
  
 `WA_CLICKACTIVE`  
 Rámečku je vybrána jako kliknutí myší.  
  
 `WA_INACTIVE`  
 Není vybrán rámečku.  
  
##  <a name="onactivateapp"></a>  CFrameWndEx::OnActivateApp  
 Voláno rámcem při vybrané nebo nevybrány aplikace.  
  
```  
afx_msg void OnActivateApp(
    BOOL bActive,  
    DWORD dwThreadID);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bActive`  
 `TRUE` Pokud je vybrána aplikace; `FALSE` Pokud není vybrané aplikace.  
  
 [v] `dwThreadID`  
 Tento parametr není používán.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onchangevisualmanager"></a>  CFrameWndEx::OnChangeVisualManager  
 Voláno rámcem, kdy ke změně rámečku vyžaduje změnu visual správce.  
  
```  
afx_msg LRESULT OnChangeVisualManager(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `wParam`  
 Tento parametr není používán.  
  
 [v] `lParam`  
 Tento parametr není používán.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu 0.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onclose"></a>  CFrameWndEx::OnClose  
 Rozhraní framework volá tuto metodu za účelem zavřete rámečku.  
  
```  
afx_msg void OnClose();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud se rámečku je v režimu náhledu tisku, odešle zprávu Windows zavřete náhledu tisku; jinak pokud rámečku hostitelem klientem OLE, klient je deaktivována.  
  
##  <a name="onclosedockingpane"></a>  CFrameWndEx::OnCloseDockingPane  
 Voláno rámcem, když uživatel klikne **Zavřít** tlačítko v podokně ukotvení.  
  
```  
virtual BOOL OnCloseDockingPane(CDockablePane* pPane);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je možné uzavřít ukotvení panelu. `FALSE` v opačném případě  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace neprovede žádnou akci. Potlačí tuto metodu, pokud chcete zpracovávat skrytí ukotvení panelu.  
  
##  <a name="oncloseminiframe"></a>  CFrameWndEx::OnCloseMiniFrame  
 Voláno rámcem, když uživatel klikne **Zavřít** tlačítko na plovoucího mini rámce okna.  
  
```  
virtual BOOL OnCloseMiniFrame(CPaneFrameWnd* pWnd);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je možné uzavřít plovoucího mini rámce okna. `FALSE` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace neprovede žádnou akci. Potlačí tuto metodu, pokud chcete zpracovat skrytí plovoucího mini rámce okna.  
  
##  <a name="onclosepopupmenu"></a>  CFrameWndEx::OnClosePopupMenu  
 Voláno rámcem když zpracovává zprávu WM_DESTROY active místní nabídky.  
  
```  
virtual void OnClosePopupMenu(CMFCPopupMenu* pMenuPopup);
```  
  
### <a name="parameters"></a>Parametry  
 `pMenuPopup`  
 Ukazatel na místní nabídky.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework odešle zprávu WM_DESTROY, když je zavřete okno. Potlačí tuto metodu, pokud chcete zpracovat oznámení z `CMFCPopupMenu` objekty, které patří do okna s rámečkem při `CMFCPopupMenu` objekt zpracovává `WM_DESTROY` zpráva byla odeslána rámcem při zavření okna.  
  
##  <a name="oncmdmsg"></a>  CFrameWndEx::OnCmdMsg  
 Odešle příkaz zprávy.  
  
```  
virtual BOOL OnCmdMsg(
    UINT nID,  
    int nCode,  
    void* pExtra,  
    AFX_CMDHANDLERINFO* pHandlerInfo);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nID`  
 ID příkazu.  
  
 [v] `nCode`  
 Příkaz kategorie zpráv.  
  
 [ve out] `pExtra`  
 Ukazatel na objekt příkazu.  
  
 [ve out] `pHandlerInfo`  
 Ukazatel na strukturu obslužná rutina příkazu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud počet zpracovaných zpráv příkaz; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="oncontexthelp"></a>  CFrameWndEx::OnContextHelp  
 Voláno rámcem nápovědu související s kontextu.  
  
```  
afx_msg void OnContextHelp();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="oncreate"></a>  CFrameWndEx::OnCreate  
 Voláno rámcem po vytvoření rámečku.  
  
```  
afx_msg int OnCreate(LPCREATESTRUCT lpCreateStruct);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpCreateStruct`  
 Ukazatel [createstruct – struktura](../../mfc/reference/createstruct-structure.md) pro nové rámečku.  
  
### <a name="return-value"></a>Návratová hodnota  
 0, budou pokračovat ve vytváření rámce; Chcete-li odstranit rámečku hodnotu -1.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ondestroy"></a>  CFrameWndEx::OnDestroy  
 Voláno rámcem při rámečku zničena.  
  
```  
afx_msg void OnDestroy();
```  
  
### <a name="remarks"></a>Poznámky  
 Tabulka akcelerátoru a všechny systémy windows zničena.  
  
##  <a name="ondrawmenuimage"></a>  CFrameWndEx::OnDrawMenuImage  
 Voláno rámcem, pokud aplikace nakreslí obrázek přidružený k položce nabídky.  
  
```  
virtual BOOL OnDrawMenuImage(
    CDC* pDC,  
    const CMFCToolBarMenuButton* pMenuButton,  
    const CRect& rectImage);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDC`  
 Ukazatel na kontextu zařízení.  
  
 [v] `pMenuButton`  
 Ukazatel na tlačítka s nabídkou vykreslované jejichž bitové kopie.  
  
 [v] `rectImage`  
 Ukazatel na `Rect` struktura, která určuje pozici obrazovky a velikost bitové kopie.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud rozhraní úspěšně vykreslí obrázku; `FALSE` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu, pokud chcete přizpůsobit vykreslování obrázků pro položky nabídky, které patří do panelu nabídek vlastníkem `CFrameWndEx` odvozené objektu.  
  
##  <a name="ondrawmenulogo"></a>  CFrameWndEx::OnDrawMenuLogo  
 Voláno rámcem při `CMFCPopupMenu` objekt zpracuje zprávu WM_PAINT.  
  
```  
virtual void OnDrawMenuLogo(
    CDC* pDC,  
    CMFCPopupMenu* pMenu,  
    const CRect& rectLogo);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDC`  
 Ukazatel na kontextu zařízení.  
  
 [v] `pMenu`  
 Ukazatel na položku nabídky.  
  
 [v] `rectLogo`  
 Odkaz na konstantu `CRect` struktura, která určuje obrazovky umístění a velikost loga nabídky.  
  
### <a name="remarks"></a>Poznámky  
 Funkci přepsat, pokud chcete zobrazovat logo v místní nabídce, která patří do panelu nabídek vlastníkem `CFrameWndEx` odvozené objektu.  
  
##  <a name="ondwmcompositionchanged"></a>  CFrameWndEx::OnDWMCompositionChanged  
 Voláno rámcem Pokud složení plochy okno správce (správce) byla zapnutá nebo vypnutá.  
  
```  
afx_msg LRESULT OnDWMCompositionChanged(
    WPARAM wp,  
    LPARAM lp);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `wp`  
 Tento parametr není používán.  
  
 [v] `lp`  
 Tento parametr není používán.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu 0.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onexitsizemove"></a>  CFrameWndEx::OnExitSizeMove  
 Voláno rámcem při zastavení rámečku přesunutí nebo změnou velikosti.  
  
```  
LRESULT OnExitSizeMove(
    WPARAM wp,  
    LPARAM lp);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `wp`  
 Tento parametr není používán.  
  
 [v] `lp`  
 Tento parametr není používán.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu 0.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ongetminmaxinfo"></a>  CFrameWndEx::OnGetMinMaxInfo  
 Voláno rámcem při změně velikosti rámečku můžete nastavit omezení okna dimenze.  
  
```  
afx_msg void OnGetMinMaxInfo(MINMAXINFO FAR* lpMMI);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpMMI`  
 Ukazatel na [minmaxinfo –](http://msdn.microsoft.com/library/windows/desktop/ms632605) struktura.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onidleupdatecmdui"></a>  CFrameWndEx::OnIdleUpdateCmdUI  
 Voláno rámcem aktualizovat zobrazení rámce při zpracování příkazu nečinnosti.  
  
```  
afx_msg LRESULT OnIdleUpdateCmdUI(
    WPARAM wParam = 0,  
    LPARAM lParam = 0);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `wParam`  
 Tento parametr není používán.  
  
 [v] `lParam`  
 Tento parametr není používán.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu 0.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onlbuttondown"></a>  CFrameWndEx::OnLButtonDown  
 Rozhraní framework volá tuto metodu, když uživatel stiskne levé tlačítko.  
  
```  
afx_msg void OnLButtonDown(
    UINT nFlags,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nFlags`  
 Určuje, zda uživatel stisknutí modifikační klávesy. Možné hodnoty najdete v tématu parametr `wParam` v [WM_LBUTTONDOWN oznámení](http://msdn.microsoft.com/library/windows/desktop/ms645607).  
  
 [v] `point`  
 Určuje x a y souřadnic ukazatele, relativně k levém horním rohu okna.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onlbuttonup"></a>  CFrameWndEx::OnLButtonUp  
 Rozhraní framework volá tuto metodu, když uživatel uvolní levé tlačítko.  
  
```  
afx_msg void OnLButtonUp(
    UINT nFlags,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nFlags`  
 Určuje, zda uživatel stisknutí modifikační klávesy. Možné hodnoty najdete v tématu parametr `wParam` v [WM_LBUTTONUP oznámení](http://msdn.microsoft.com/library/windows/desktop/ms645608).  
  
 [v] `point`  
 Určuje x a y souřadnic ukazatele, relativně k levém horním rohu okna.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onmenubuttontoolhittest"></a>  CFrameWndEx::OnMenuButtonToolHitTest  
 Voláno rámcem při `CMFCToolBarButton` objektu procesy `WM_NCHITTEST` zprávy.  
  
```  
virtual BOOL OnMenuButtonToolHitTest(
    CMFCToolBarButton* pButton,  
    TOOLINFO* pTI);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pButton`  
 Ukazatel na tlačítko panelu nástrojů.  
  
 [out] `pTI`  
 Ukazatel na strukturu nástroj informace.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud aplikace doplní `pTI` parametr. `FALSE` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu, pokud chcete zadat popis informace o konkrétní položku.  
  
##  <a name="onmenuchar"></a>  CFrameWndEx::OnMenuChar  
 Voláno rámcem, když se zobrazí nabídky a uživatel stiskne klíč, který neodpovídá žádnému příkazu.  
  
```  
afx_msg LRESULT OnMenuChar(
    UINT nChar,  
    UINT nFlags,  
    CMenu* pMenu);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nChar`  
 Kód znaku stisknuté klávesy.  
  
 [v] `nFlags`  
 Obsahuje `MF_POPUP` příznak, pokud se zobrazí nabídka podnabídky; obsahuje `MF_SYSMENU` příznak, pokud se zobrazí nabídka nabídky ovládací prvek.  
  
 [v] `pMenu`  
 Ukazatel na nabídku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Word horní musí mít jednu z následujících hodnot.  
  
 `0`  
 Rozhraní je třeba ignorovat klávesu.  
  
 `1`  
 Rozhraní framework zavření v nabídce.  
  
 `2`  
 Rozhraní framework měli vybrat jednu z položky zobrazené v nabídce. Word nejnižší obsahuje ID příkazu k výběru.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onmousemove"></a>  CFrameWndEx::OnMouseMove  
 Tato metoda volá framework při umístění ukazatele.  
  
```  
afx_msg void OnMouseMove(
    UINT nFlags,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nFlags`  
 Určuje, zda uživatel stisknutí modifikační klávesy. Možné hodnoty najdete v tématu parametr `wParam` v [WM_MOUSEMOVE oznámení](http://msdn.microsoft.com/library/windows/desktop/ms645616).  
  
 [v] `point`  
 Určuje x a y souřadnic ukazatele relativně k levém horním rohu okna.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onmoveminiframe"></a>  CFrameWndEx::OnMoveMiniFrame  
 Voláno rámcem, pokud se přesune podokně okna.  
  
```  
virtual BOOL OnMoveMiniFrame(CWnd* pFrame);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pFrame`  
 Ukazatel [CPaneFrameWnd třída](../../mfc/reference/cpaneframewnd-class.md) podokně okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud okno podokně nebyl ukotveno; `FALSE` Pokud byl ukotven podokně okna.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onncactivate"></a>  CFrameWndEx::OnNcActivate  
 Voláno rámcem při neklientská oblast rámečku musí překreslen signalizovat změnu v aktivním stavu.  
  
```  
afx_msg BOOL OnNcActivate(BOOL bActive);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bActive`  
 `TRUE` Kreslení rámečku active; `FALSE` k vykreslení rámečku neaktivní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Chcete-li pokračovat s výchozí zpracování; nenulové hodnoty 0 zabráníte neklientská oblast z právě deaktivována.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onnccalcsize"></a>  CFrameWndEx::OnNcCalcSize  
 Voláno rámcem při vypočítat velikost a umístění klienta.  
  
```  
afx_msg void OnNcCalcSize(
    BOOL bCalcValidRects,  
    NCCALCSIZE_PARAMS FAR* lpncsp);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bCalcValidRects`  
 `TRUE` Když aplikace musíte zadat platný klientské oblasti; v opačném `FALSE`.  
  
 [v] `lpncsp`  
 Ukazatel na `NCCALCSIZE_PARAMS` struktura, která obsahuje změny, dimenze rámce.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onnchittest"></a>  CFrameWndEx::OnNcHitTest  
 Voláno rámcem při umístění ukazatele nebo při stisknutí tlačítka nebo uvolnění tlačítka myši.  
  
```  
afx_msg LRESULT OnNcHitTest(CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `point`  
 Umístění ukazatele v souřadnice obrazovky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel dosáhl Výčtová hodnota. Seznam možných hodnot naleznete v části [WM_NCHITTEST oznámení](http://msdn.microsoft.com/library/windows/desktop/ms645618).  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onncmousemove"></a>  CFrameWndEx::OnNcMouseMove  
 Voláno rámcem při umístění ukazatele v neklientská oblast.  
  
```  
afx_msg void OnNcMouseMove(
    UINT nHitTest,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nHitTest`  
 Ukazatel dosáhl Výčtová hodnota. Seznam možných hodnot naleznete v části [WM_NCHITTEST oznámení](http://msdn.microsoft.com/library/windows/desktop/ms645618).  
  
 [v] `point`  
 Umístění ukazatele v souřadnice obrazovky.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onncpaint"></a>  CFrameWndEx::OnNcPaint  
 Voláno rámcem při musí být vykresluje neklientská oblast.  
  
```  
afx_msg void OnNcPaint();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onpanecheck"></a>  CFrameWndEx::OnPaneCheck  
 Voláno rámcem řízení zobrazení podokna.  
  
```  
afx_msg BOOL OnPaneCheck(UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nID`  
 ID ovládacího prvku podokno.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud příkaz bylo zpracováno; `FALSE` pokračujte s zpracování příkazu.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onpostpreviewframe"></a>  CFrameWndEx::OnPostPreviewFrame  
 Voláno rámcem, když uživatel změní režim náhledu tisku.  
  
```  
afx_msg LRESULT OnPostPreviewFrame(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `wParam`  
 Tento parametr není používán.  
  
 [v] `lParam`  
 `TRUE` Pokud rámečku je v režimu náhledu tisku `FALSE` Pokud je vypnut režim náhledu tisku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu 0.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onpowerbroadcast"></a>  CFrameWndEx::OnPowerBroadcast  
 Voláno rámcem při výskytu události správy napájení.  
  
```  
afx_msg LRESULT OnPowerBroadcast(
    WPARAM wp,  
    LPARAM lp);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `wp`  
 Událost řízení spotřeby. Seznam možných hodnot naleznete v části [WM_POWERBROADCAST zpráva](http://msdn.microsoft.com/library/windows/desktop/aa373247).  
  
 [v] `lp`  
 Tento parametr není používán.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výsledkem volání procedury okna výchozí.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onsetmenu"></a>  CFrameWndEx::OnSetMenu  
 Voláno rámcem nahradit nabídku rámce okna.  
  
```  
afx_msg LRESULT OnSetMenu(
    WPARAM wp,  
    LPARAM lp);  
  
BOOL OnSetMenu(HMENU hmenu);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `wp`  
 Popisovač nové nabídky rámce okna.  
  
 [v] `lp`  
 Popisovač nabídce nové okno.  
  
 [v] `hmenu`  
 Popisovač nové nabídky rámce okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 `LRESULT` je výsledek z volání procedury okna výchozí.  
  
 `BOOL` je `TRUE` Pokud událost byla zpracovávaný, jinak hodnota `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onsetpreviewmode"></a>  CFrameWndEx::OnSetPreviewMode  
 Voláno rámcem nastavení režimu náhledu tisku pro rámečku.  
  
```  
virtual void OnSetPreviewMode(
    BOOL bPreview,  
    CPrintPreviewState* pState);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bPreview`  
 `TRUE` Chcete-li povolit náhledu tisku; `FALSE` zakázat náhledu tisku.  
  
 [v] `pState`  
 Ukazatel na `CPrintPreviewState` rámce struktura stavu.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onsettext"></a>  CFrameWndEx::OnSetText  
 Voláno rámcem nastavit text časového období.  
  
```  
afx_msg LRESULT OnSetText(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `wParam`  
 Tento parametr není používán.  
  
 [v] `lParam`  
 Ukazatel na hodnotu text pro okno.  
  
### <a name="return-value"></a>Návratová hodnota  
 Návratová hodnota z volání [DefWindowProc](http://msdn.microsoft.com/library/windows/desktop/ms633572).  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onshowcustomizepane"></a>  CFrameWndEx::OnShowCustomizePane  
 Voláno rámcem, když se zobrazí `QuickCustomizePane`.  
  
```  
virtual BOOL OnShowCustomizePane(
    CMFCPopupMenu* pMenuPane,  
    UINT uiToolbarID);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pMenuPane`  
 Ukazatel na rychlé přizpůsobení podokna.  
  
 [v] `uiToolbarID`  
 ID ovládacího prvku pro přizpůsobení panelu nástrojů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Tato metoda vždy návratový `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
 Rychlé přizpůsobení nabídky je místní nabídky, které se zobrazí po kliknutí na tlačítko přizpůsobit tlačítka panelu nástrojů  
  
##  <a name="onshowpanes"></a>  CFrameWndEx::OnShowPanes  
 Voláno rámcem zobrazení nebo skrytí podokna.  
  
```  
virtual BOOL OnShowPanes(BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bShow`  
 `TRUE` Pokud aplikace zobrazuje podokna; `FALSE` jinak.  
  
### <a name="return-value"></a>Návratová hodnota  
 Tato metoda vždy návratový `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace ukazuje podokna Pokud `bShow` je `TRUE` a podoken jsou skryté. nebo když `bShow` je `FALSE` a jsou viditelné podokna.  
  
 Výchozí implementace skryje podoken, pokud `bShow` je `TRUE` a jsou viditelné podokna nebo když `bShow` je `FALSE` a podoken jsou skryté.  
  
 Potlačí tuto metodu v odvozené třídě provést vlastní kód, pokud rozhraní zobrazí nebo skryje podokna.  
  
##  <a name="onshowpopupmenu"></a>  CFrameWndEx::OnShowPopupMenu  
 Voláno rámcem, pokud se zobrazí místní nabídky.  
  
```  
virtual BOOL OnShowPopupMenu(CMFCPopupMenu* pMenu);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pMenu`  
 Ukazatel na místní nabídky.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je v místní nabídce viditelná; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu v odvozené třídě provést vlastní kód, pokud rozhraní zobrazí místní nabídky. Například přepište tuto metodu za účelem změnit barvu pozadí příkazy v místní nabídce.  
  
##  <a name="onsize"></a>  CFrameWndEx::OnSize  
 Voláno rámcem po změně velikosti rámečku.  
  
```  
afx_msg void OnSize(
    UINT nType,  
    int cx,  
    int cy);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nType`  
 Typ Změna velikosti. Možné hodnoty najdete v tématu parametr `wParam` v [WM_SIZE oznámení](http://msdn.microsoft.com/library/windows/desktop/ms632646).  
  
 [v] `cx`  
 Nové Šířka rámečku v pixelech.  
  
 [v] `cy`  
 Nové výška rámečku v pixelech.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onsizing"></a>  CFrameWndEx::OnSizing  
 Voláno rámcem, když uživatel změní velikost rámečku.  
  
```  
afx_msg void OnSizing(
    UINT fwSide,  
    LPRECT pRect);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `fwSide`  
 Okraj rámce, který je přesunout. V tématu parametr `wParam` v [WM_SIZING oznámení](http://msdn.microsoft.com/library/windows/desktop/ms632647).  
  
 [ve out] `pRect`  
 Ukazatel na [CRect](../../atl-mfc-shared/reference/crect-class.md) nebo [Rect –](../../mfc/reference/rect-structure1.md) struktura, která obsahuje souřadnice rámečku.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onsyscolorchange"></a>  CFrameWndEx::OnSysColorChange  
 Voláno rámcem při změně barvy systému.  
  
```  
void OnSysColorChange();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ontearoffmenu"></a>  CFrameWndEx::OnTearOffMenu  
 Voláno rámcem, pokud aplikace zobrazí nabídky, která má panel úplné vypnutí.  
  
```  
virtual BOOL OnTearOffMenu(
    CMFCPopupMenu* pMenuPopup,  
    CPane* pBar);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pMenuPopup`  
 Ukazatel na místní nabídky.  
  
 [v] `pBar`  
 Ukazatel na panel úplné vypnutí.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je povolena místní nabídka se panel úplné vypnutí; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu v odvozené třídě provést vlastní kód, pokud rozhraní zobrazí ovládacích pruhů.  
  
 Výchozí implementace neprovede žádnou akci a vrátí `TRUE`.  
  
##  <a name="ontoolbarcontextmenu"></a>  CFrameWndEx::OnToolbarContextMenu  
 Voláno rámcem vytvářet místní nabídky panelu nástrojů.  
  
```  
afx_msg LRESULT OnToolbarContextMenu(
    WPARAM wp,  
    LPARAM lp);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `wp`  
 Tento parametr není používán.  
  
 [v] `lp`  
 Tento parametr není používán.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu 1.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ontoolbarcreatenew"></a>  CFrameWndEx::OnToolbarCreateNew  
 Rozhraní framework volá tuto metodu za účelem vytvoření nové panelu nástrojů.  
  
```  
afx_msg LRESULT OnToolbarCreateNew(
    WPARAM wp,  
    LPARAM lp);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `wp`  
 Tento parametr není používán.  
  
 [v] `lp`  
 Ukazatel na hodnotu text pro záhlaví panelu nástrojů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nový panel nástrojů; nebo `NULL` Pokud nebyl vytvořen panelu nástrojů.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ontoolbardelete"></a>  CFrameWndEx::OnToolbarDelete  
 Voláno rámcem při odstranění panelu nástrojů.  
  
```  
afx_msg LRESULT OnToolbarDelete(
    WPARAM, 
    LPARAM lp);
```  
  
### <a name="parameters"></a>Parametry  
 [v]  
 Tento parametr není používán.  
  
 [v] `lp`  
 Ukazatel na panelu nástrojů.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud byl odstraněn panelu nástrojů; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onupdateframemenu"></a>  CFrameWndEx::OnUpdateFrameMenu  
 Voláno rámcem nastavit v nabídce.  
  
```  
virtual void OnUpdateFrameMenu(HMENU hMenuAlt);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `hMenuAlt`  
 Zpracování do alternativní nabídky.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onupdateframetitle"></a>  CFrameWndEx::OnUpdateFrameTitle  
 Rozhraní framework volá tuto metodu za účelem aktualizace na záhlaví okna rámce.  
  
```  
virtual void OnUpdateFrameTitle(BOOL bAddToTitle);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bAddToTitle`  
 `TRUE` Chcete-li přidat název aktivní dokument na záhlaví okna pro rámce; v opačném případě `FALSE.`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onupdatepanemenu"></a>  CFrameWndEx::OnUpdatePaneMenu  
 Voláno rámcem aktualizace nabídky panelu.  
  
```  
afx_msg void OnUpdatePaneMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pCmdUI`  
 Ukazatel na objekt podokně uživatelské rozhraní.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onwindowposchanged"></a>  CFrameWndEx::OnWindowPosChanged  
 Voláno rámcem, když velikost rámce, umístění a pořadí z-order se změnil z důvodu volání metody okno správy.  
  
```  
afx_msg void OnWindowPosChanged(WINDOWPOS FAR* lpwndpos);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpwndpos`  
 Ukazatel na [windowpos –](../../mfc/reference/windowpos-structure1.md) struktura, která obsahuje novou velikost a umístění.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="panefrompoint"></a>  CFrameWndEx::PaneFromPoint  
 Vyhledá každý podokno danému bodu.  
  
```  
CBasePane* PaneFromPoint(
    CPoint point,  
    int nSensitivity,  
    bool bExactBar,  
    CRuntimeClass* pRTCBarType) const;  
  
CBasePane* PaneFromPoint(
    CPoint point,  
    int nSensitivity,  
    DWORD& dwAlignment,  
    CRuntimeClass* pRTCBarType) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `point`  
 Souřadnice obrazovky bodu ke kontrole.  
  
 [v] `nSensitivity`  
 Při hledání bodu rozbalte ohraničující obdélník jednotlivých ovládacích pruhů toto množství.  
  
 [v] `bExactBar`  
 `TRUE` Ignorovat `nSensitivity` parametr, jinak hodnota `FALSE`.  
  
 [v] `pRTCBarType`  
 Není-li `NULL`, tato metoda vyhledá ovládací pruhy zadaného typu.  
  
 [out] `dwAlignment`  
 V případě úspěchu se tento parametr obsahuje na straně panelu Ovládací prvek, který je nejblíže k Zadaný bod. Tento parametr, jinak hodnota není inicializován.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na ovládací prvek panel, který obsahuje `point`; `NULL` Pokud se nenajde žádný ovládací prvek neexistuje.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vyhledá všechny ovládací pruhy v aplikaci pro `point`.  
  
 Použití `nSensitivity` zvětšete velikost oblasti hledání. Použití `pRTCBarType` omezit typy ovládací pruhy, které tato metoda vyhledá.  
  
##  <a name="pretranslatemessage"></a>  CFrameWndEx::PreTranslateMessage  
 Předtím, než je odesláno, který zpracovává zprávy konkrétní okno.  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pMsg`  
 Ukazatel [MSG](../../mfc/reference/msg-structure1.md) struktura, která obsahuje zprávu zpracovat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulová Pokud zpráva bylo zpracováno a nesmí být odeslán; 0, pokud zpráva nebyla zpracována a by měla být odeslána.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="recalclayout"></a>  CFrameWndEx::RecalcLayout  
 Upraví rozložení rámečku a jeho podřízené systému windows.  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bNotify`  
 Určuje, jestli oznámit položce OLE klienta o změně rozložení.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána, když došlo ke změně velikosti rámce okna nebo když ovládací pruhy zobrazení nebo skrytí.  
  
##  <a name="removepanefromdockmanager"></a>  CFrameWndEx::RemovePaneFromDockManager  
 Zruší registraci podokno a odstraní ji ze ukotvení správce.  
  
```  
void RemovePaneFromDockManager(
    CBasePane* pControlBar,  
    BOOL bDestroy,  
    BOOL bAdjustLayout,  
    BOOL bAutoHide,  
    CBasePane* pBarReplacement);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pControlBar`  
 Ukazatel na panelu řádku řízení k odebrání.  
  
 [v] `bDestroy`  
 `TRUE` Chcete-li odstranit ovládacích pruhů po odebrání; `FALSE` jinak.  
  
 [v] `bAdjustLayout`  
 `TRUE` Chcete-li upravit ukotvení rozložení; `FALSE` jinak.  
  
 [v] `bAutoHide`  
 `TRUE` Pokud je ovládací prvek panel v režimu automaticky skrýt; `FALSE` jinak.  
  
 [v] `pBarReplacement`  
 Ukazatel na podokně, který nahrazuje podokně odebrané.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k odebrání ovládacích pruhů ukotvení rozložení rámce okna.  
  
 [CDockingManager třída](../../mfc/reference/cdockingmanager-class.md) zpracovává rozložení ovládací pruhy. Je nutné zaregistrovat každý ovládací prvek panel s dokovací manager pomocí [CFrameWndEx::AddPane](#addpane) metoda nebo [CFrameWndEx::InsertPane](#insertpane) metoda.  
  
##  <a name="setdockstate"></a>  CFrameWndEx::SetDockState  
 Obnoví ukotvení rozložení ukotvení stavu uložené v registru.  
  
```  
void SetDockState(const CDockState& state);
```  
  
### <a name="parameters"></a>Parametry  
 `state`  
 Ukotvení stavu. Tento parametr je ignorován.  
  
##  <a name="setprintpreviewframe"></a>  CFrameWndEx::SetPrintPreviewFrame  
 Nastaví rámce okna náhledu tisku.  
  
```  
void SetPrintPreviewFrame(CFrameWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pWnd`  
 Ukazatel na rámec okna náhledu tisku.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setuptoolbarmenu"></a>  CFrameWndEx::SetupToolbarMenu  
 Vloží příkazy uživatelem definované do nabídky panelu nástrojů.  
  
```  
void SetupToolbarMenu(
    CMenu& menu,  
    const UINT uiViewUserToolbarCmdFirst,  
    const UINT uiViewUserToolbarCmdLast);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `menu`  
 A `CMenu` objekt, který chcete upravit.  
  
 [v] `uiViewUserToolbarCmdFirst`  
 První příkaz definovaný uživatelem.  
  
 [v] `uiViewUserToolbarCmdLast`  
 Poslední příkaz definovaný uživatelem.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework uloží příkazy uživatelem definované v seznamu. Použití `uiViewUserToolbarCmdFirst` a `uiViewUserToolbarCmdList` k určení indexy příkazy k vložení.  
  
##  <a name="showfullscreen"></a>  CFrameWndEx::ShowFullScreen  
 Přepne hlavního rámce mezi celoobrazovkový režim a režim regulární.  
  
```  
void ShowFullScreen();
```  
  
##  <a name="showpane"></a>  CFrameWndEx::ShowPane  
 Zobrazí nebo skryje podokně zadaný.  
  
```  
void ShowPane(
    CBasePane* pBar,  
    BOOL bShow,  
    BOOL bDelay,  
    BOOL bActivate);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pBar`  
 Ukazatel na panelu řízení umožňuje zobrazit nebo skrýt.  
  
 [v] `bShow`  
 Pokud `TRUE`, aplikace zobrazí panel ovládacího prvku. Aplikace, jinak hodnota skryje panel ovládacího prvku.  
  
 [v] `bDelay`  
 Pokud `TRUE`, dokud volání framework zpoždění úpravou ukotvení rozložení [CFrameWndEx::AdjustDockingLayout](#adjustdockinglayout). Ukotvení rozložení, jinak hodnota přepočítejte okamžitě.  
  
 [v] `bActivate`  
 Pokud `TRUE`, aktivujte panel ovládacího prvku. Jinak zobrazte panel ovládacího prvku v neaktivním stavu.  
  
##  <a name="updatecaption"></a>  CFrameWndEx::UpdateCaption  
 Voláno rámcem aktualizovat titulek rámce okna.  
  
```  
void UpdateCaption();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="winhelp"></a>  CFrameWndEx::WinHelp  
 Vyvolá WinHelp aplikace nebo kontext související nápovědy.  
  
```  
virtual void WinHelp(
    DWORD dwData,  
    UINT nCmd = HELP_CONTEXT);
```  
  
### <a name="parameters"></a>Parametry  
 `dwData`  
 Data, která závisí na `nCmd` parametr. Seznam možných hodnot naleznete v části [WinHelp](http://msdn.microsoft.com/library/windows/desktop/bb762267).  
  
 `nCmd`  
 Příkaz help. Seznam možných hodnot naleznete v části [WinHelp](http://msdn.microsoft.com/library/windows/desktop/bb762267).  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)
