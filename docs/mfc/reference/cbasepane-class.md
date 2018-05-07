---
title: Třída CBasePane | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CBasePane
- AFXBASEPANE/CBasePane
- AFXBASEPANE/CBasePane::AccNotifyObjectFocusEvent
- AFXBASEPANE/CBasePane::AddPane
- AFXBASEPANE/CBasePane::AdjustDockingLayout
- AFXBASEPANE/CBasePane::AdjustLayout
- AFXBASEPANE/CBasePane::CalcFixedLayout
- AFXBASEPANE/CBasePane::CanAcceptPane
- AFXBASEPANE/CBasePane::CanAutoHide
- AFXBASEPANE/CBasePane::CanBeAttached
- AFXBASEPANE/CBasePane::CanBeClosed
- AFXBASEPANE/CBasePane::CanBeDocked
- AFXBASEPANE/CBasePane::CanBeResized
- AFXBASEPANE/CBasePane::CanBeTabbedDocument
- AFXBASEPANE/CBasePane::CanFloat
- AFXBASEPANE/CBasePane::CanFocus
- AFXBASEPANE/CBasePane::CopyState
- AFXBASEPANE/CBasePane::CreateDefaultMiniframe
- AFXBASEPANE/CBasePane::CreateEx
- AFXBASEPANE/CBasePane::DockPane
- AFXBASEPANE/CBasePane::DockPaneUsingRTTI
- AFXBASEPANE/CBasePane::DockToFrameWindow
- AFXBASEPANE/CBasePane::DoesAllowDynInsertBefore
- AFXBASEPANE/CBasePane::EnableDocking
- AFXBASEPANE/CBasePane::EnableGripper
- AFXBASEPANE/CBasePane::FloatPane
- AFXBASEPANE/CBasePane::get_accHelpTopic
- AFXBASEPANE/CBasePane::get_accSelection
- AFXBASEPANE/CBasePane::GetCaptionHeight
- AFXBASEPANE/CBasePane::GetControlBarStyle
- AFXBASEPANE/CBasePane::GetCurrentAlignment
- AFXBASEPANE/CBasePane::GetDockingMode
- AFXBASEPANE/CBasePane::GetDockSiteFrameWnd
- AFXBASEPANE/CBasePane::GetEnabledAlignment
- AFXBASEPANE/CBasePane::GetMFCStyle
- AFXBASEPANE/CBasePane::GetPaneIcon
- AFXBASEPANE/CBasePane::GetPaneRow
- AFXBASEPANE/CBasePane::GetPaneStyle
- AFXBASEPANE/CBasePane::GetParentDockSite
- AFXBASEPANE/CBasePane::GetParentMiniFrame
- AFXBASEPANE/CBasePane::GetParentTabbedPane
- AFXBASEPANE/CBasePane::GetParentTabWnd
- AFXBASEPANE/CBasePane::GetRecentVisibleState
- AFXBASEPANE/CBasePane::HideInPrintPreviewMode
- AFXBASEPANE/CBasePane::InsertPane
- AFXBASEPANE/CBasePane::IsAccessibilityCompatible
- AFXBASEPANE/CBasePane::IsAutoHideMode
- AFXBASEPANE/CBasePane::IsDialogControl
- AFXBASEPANE/CBasePane::IsDocked
- AFXBASEPANE/CBasePane::IsFloating
- AFXBASEPANE/CBasePane::IsHorizontal
- AFXBASEPANE/CBasePane::IsInFloatingMultiPaneFrameWnd
- AFXBASEPANE/CBasePane::IsMDITabbed
- AFXBASEPANE/CBasePane::IsPaneVisible
- AFXBASEPANE/CBasePane::IsPointNearDockSite
- AFXBASEPANE/CBasePane::IsResizable
- AFXBASEPANE/CBasePane::IsRestoredFromRegistry
- AFXBASEPANE/CBasePane::IsTabbed
- AFXBASEPANE/CBasePane::IsVisible
- AFXBASEPANE/CBasePane::LoadState
- AFXBASEPANE/CBasePane::MoveWindow
- AFXBASEPANE/CBasePane::OnAfterChangeParent
- AFXBASEPANE/CBasePane::OnBeforeChangeParent
- AFXBASEPANE/CBasePane::OnDrawCaption
- AFXBASEPANE/CBasePane::OnMovePaneDivider
- AFXBASEPANE/CBasePane::OnPaneContextMenu
- AFXBASEPANE/CBasePane::OnRemoveFromMiniFrame
- AFXBASEPANE/CBasePane::OnSetAccData
- AFXBASEPANE/CBasePane::PaneFromPoint
- AFXBASEPANE/CBasePane::RecalcLayout
- AFXBASEPANE/CBasePane::RemovePaneFromDockManager
- AFXBASEPANE/CBasePane::SaveState
- AFXBASEPANE/CBasePane::SelectDefaultFont
- AFXBASEPANE/CBasePane::SetControlBarStyle
- AFXBASEPANE/CBasePane::SetDockingMode
- AFXBASEPANE/CBasePane::SetPaneAlignment
- AFXBASEPANE/CBasePane::SetPaneStyle
- AFXBASEPANE/CBasePane::SetWindowPos
- AFXBASEPANE/CBasePane::ShowPane
- AFXBASEPANE/CBasePane::StretchPane
- AFXBASEPANE/CBasePane::UndockPane
- AFXBASEPANE/CBasePane::DoPaint
dev_langs:
- C++
helpviewer_keywords:
- CBasePane [MFC], AccNotifyObjectFocusEvent
- CBasePane [MFC], AddPane
- CBasePane [MFC], AdjustDockingLayout
- CBasePane [MFC], AdjustLayout
- CBasePane [MFC], CalcFixedLayout
- CBasePane [MFC], CanAcceptPane
- CBasePane [MFC], CanAutoHide
- CBasePane [MFC], CanBeAttached
- CBasePane [MFC], CanBeClosed
- CBasePane [MFC], CanBeDocked
- CBasePane [MFC], CanBeResized
- CBasePane [MFC], CanBeTabbedDocument
- CBasePane [MFC], CanFloat
- CBasePane [MFC], CanFocus
- CBasePane [MFC], CopyState
- CBasePane [MFC], CreateDefaultMiniframe
- CBasePane [MFC], CreateEx
- CBasePane [MFC], DockPane
- CBasePane [MFC], DockPaneUsingRTTI
- CBasePane [MFC], DockToFrameWindow
- CBasePane [MFC], DoesAllowDynInsertBefore
- CBasePane [MFC], EnableDocking
- CBasePane [MFC], EnableGripper
- CBasePane [MFC], FloatPane
- CBasePane [MFC], get_accHelpTopic
- CBasePane [MFC], get_accSelection
- CBasePane [MFC], GetCaptionHeight
- CBasePane [MFC], GetControlBarStyle
- CBasePane [MFC], GetCurrentAlignment
- CBasePane [MFC], GetDockingMode
- CBasePane [MFC], GetDockSiteFrameWnd
- CBasePane [MFC], GetEnabledAlignment
- CBasePane [MFC], GetMFCStyle
- CBasePane [MFC], GetPaneIcon
- CBasePane [MFC], GetPaneRow
- CBasePane [MFC], GetPaneStyle
- CBasePane [MFC], GetParentDockSite
- CBasePane [MFC], GetParentMiniFrame
- CBasePane [MFC], GetParentTabbedPane
- CBasePane [MFC], GetParentTabWnd
- CBasePane [MFC], GetRecentVisibleState
- CBasePane [MFC], HideInPrintPreviewMode
- CBasePane [MFC], InsertPane
- CBasePane [MFC], IsAccessibilityCompatible
- CBasePane [MFC], IsAutoHideMode
- CBasePane [MFC], IsDialogControl
- CBasePane [MFC], IsDocked
- CBasePane [MFC], IsFloating
- CBasePane [MFC], IsHorizontal
- CBasePane [MFC], IsInFloatingMultiPaneFrameWnd
- CBasePane [MFC], IsMDITabbed
- CBasePane [MFC], IsPaneVisible
- CBasePane [MFC], IsPointNearDockSite
- CBasePane [MFC], IsResizable
- CBasePane [MFC], IsRestoredFromRegistry
- CBasePane [MFC], IsTabbed
- CBasePane [MFC], IsVisible
- CBasePane [MFC], LoadState
- CBasePane [MFC], MoveWindow
- CBasePane [MFC], OnAfterChangeParent
- CBasePane [MFC], OnBeforeChangeParent
- CBasePane [MFC], OnDrawCaption
- CBasePane [MFC], OnMovePaneDivider
- CBasePane [MFC], OnPaneContextMenu
- CBasePane [MFC], OnRemoveFromMiniFrame
- CBasePane [MFC], OnSetAccData
- CBasePane [MFC], PaneFromPoint
- CBasePane [MFC], RecalcLayout
- CBasePane [MFC], RemovePaneFromDockManager
- CBasePane [MFC], SaveState
- CBasePane [MFC], SelectDefaultFont
- CBasePane [MFC], SetControlBarStyle
- CBasePane [MFC], SetDockingMode
- CBasePane [MFC], SetPaneAlignment
- CBasePane [MFC], SetPaneStyle
- CBasePane [MFC], SetWindowPos
- CBasePane [MFC], ShowPane
- CBasePane [MFC], StretchPane
- CBasePane [MFC], UndockPane
- CBasePane [MFC], DoPaint
ms.assetid: 8163dd51-d7c7-4def-9c74-61f8ecdfad82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5cbd24042e7f309a28cea5e72b6a134f3205e541
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cbasepane-class"></a>CBasePane – třída
Základní třída pro všechny podokna v prostředí MFC.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CBasePane : public CWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|`CBasePane::CBasePane`|Výchozí konstruktor.|  
|`CBasePane::~CBasePane`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|`CBasePane::accHitTest`|Voláno rámcem načíst podřízený element nebo podřízený objekt k danému bodu na obrazovce. (Přepisuje [CWnd::accHitTest](../../mfc/reference/cwnd-class.md#acchittest).)|  
|`CBasePane::accLocation`|Voláno rámcem načíst aktuální umístění obrazovky pro zadaný objekt. (Přepisuje [CWnd::accLocation](../../mfc/reference/cwnd-class.md#acclocation).)|  
|[CBasePane::AccNotifyObjectFocusEvent](#accnotifyobjectfocusevent)|`CBasePane` Tato metoda nepoužívá.|  
|`CBasePane::accSelect`|Voláno rámcem změnit výběr nebo přesunout fokus klávesnice zadaného objektu. (Přepisuje [CWnd::accSelect](../../mfc/reference/cwnd-class.md#accselect).)|  
|[CBasePane::AddPane](#addpane)|Přidá podokno správce ukotvení.|  
|[CBasePane::AdjustDockingLayout](#adjustdockinglayout)|Přesměruje volání na ukotvení manager upravit ukotvení rozložení.|  
|[CBasePane::AdjustLayout](#adjustlayout)|Voláno rámcem, když v podokně má upravit jeho vnitřní rozložení.|  
|[CBasePane::CalcFixedLayout](#calcfixedlayout)|Vypočítá vodorovné velikosti ovládacích pruhů.|  
|[CBasePane::CanAcceptPane](#canacceptpane)|Určuje, zda lze do podokna ukotvit jiného podokna.|  
|[CBasePane::CanAutoHide](#canautohide)|Určuje, zda v podokně podporuje režim automaticky skrýt.|  
|[CBasePane::CanBeAttached](#canbeattached)|Určuje, zda lze ukotvit podokně do jiného podokna.|  
|[CBasePane::CanBeClosed](#canbeclosed)|Určuje, zda je možné uzavřít podokně.|  
|[CBasePane::CanBeDocked](#canbedocked)|Určuje, zda lze ukotvit podokně do jiného podokna.|  
|[CBasePane::CanBeResized](#canberesized)|Určuje, zda jde změnit, v podokně.|  
|[CBasePane::CanBeTabbedDocument](#canbetabbeddocument)|Určuje, zda v podokně můžete převést na dokument s kartami MDI.|  
|[CBasePane::CanFloat](#canfloat)|Určuje, zda můžete v podokně float.|  
|[CBasePane::CanFocus](#canfocus)|Určuje, zda v podokně mohou získat fokus.|  
|[CBasePane::CopyState](#copystate)|Zkopíruje stav daného podokně.|  
|[CBasePane::CreateDefaultMiniframe](#createdefaultminiframe)|Pokud v podokně můžete float, vytvoří zkrácená rámce okna.|  
|[CBasePane::CreateEx](#createex)|Vytvoří ovládacího prvku podokno.|  
|[CBasePane::DockPane](#dockpane)|Podokno ukotvené jiného podokna nebo okně s rámečkem.|  
|[CBasePane::DockPaneUsingRTTI](#dockpaneusingrtti)|V podokně ukotvené pomocí informace běhového typu.|  
|[CBasePane::DockToFrameWindow](#docktoframewindow)|Lze ukotvit podokně ukotvené na snímek.|  
|[CBasePane::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Určuje, zda jiný podokně můžete dynamicky vložen mezi v tomto podokně a nadřazeného rámce.|  
|[CBasePane::EnableDocking](#enabledocking)|Umožňuje ukotvení podokna do hlavního rámce.|  
|[CBasePane::EnableGripper](#enablegripper)|Povolí nebo zakáže úchytu. Pokud je povoleno úchytu, můžete přetáhnout uživatele, aby přemístil v podokně.|  
|`CBasePane::FillWindowRect`|Interně.|  
|[CBasePane::FloatPane](#floatpane)|Obtéká podokně.|  
|`CBasePane::get_accChild`|Voláno rámcem načíst adresu `IDispatch` rozhraní pro zadaný podřízený. (Přepisuje [CWnd::get_accChild](../../mfc/reference/cwnd-class.md#get_accchild).)|  
|`CBasePane::get_accChildCount`|Voláno rámcem načíst počet podřízených prvků, které patří k tomuto objektu. (Přepisuje [CWnd::get_accChildCount](../../mfc/reference/cwnd-class.md#get_accchildcount).)|  
|`CBasePane::get_accDefaultAction`|Voláno rámcem načíst řetězec, který popisuje výchozí akce pro objekt. (Přepisuje [CWnd::get_accDefaultAction](../../mfc/reference/cwnd-class.md#get_accdefaultaction).)|  
|`CBasePane::get_accDescription`|Voláno rámcem načíst řetězec, který popisuje vzhled zadaného objektu. (Přepisuje [CWnd::get_accDescription](../../mfc/reference/cwnd-class.md#get_accdescription).)|  
|`CBasePane::get_accFocus`|Voláno rámcem k načtení objektu, který má právě fokus klávesnice. (Přepisuje [CWnd::get_accFocus](../../mfc/reference/cwnd-class.md#get_accfocus).)|  
|`CBasePane::get_accHelp`|Voláno rámcem načíst řetězec nápovědy vlastností pro objekt. (Přepisuje [CWnd::get_accHelp](../../mfc/reference/cwnd-class.md#get_acchelp).)|  
|[CBasePane::get_accHelpTopic](#get_acchelptopic)|Voláno rámcem získat úplnou cestu souboru WinHelp, která souvisí se zadaným objektem a identifikátor příslušné téma v tomto souboru. (Přepisuje [CWnd::get_accHelpTopic](../../mfc/reference/cwnd-class.md#get_acchelptopic).)|  
|`CBasePane::get_accKeyboardShortcut`|Voláno rámcem načíst zadaný klávesovou zkratku pro objekt. (Přepisuje [CWnd::get_accKeyboardShortcut](../../mfc/reference/cwnd-class.md#get_acckeyboardshortcut).)|  
|`CBasePane::get_accName`|Voláno rámcem načíst název zadaného objektu. (Přepisuje [CWnd::get_accName](../../mfc/reference/cwnd-class.md#get_accname).)|  
|`CBasePane::get_accParent`|Voláno rámcem načíst `IDispatch` rozhraní pro nadřazený objekt tohoto objektu. (Přepisuje [CWnd::get_accParent](../../mfc/reference/cwnd-class.md#get_accparent).)|  
|`CBasePane::get_accRole`|Voláno rámcem načíst informace, které popisuje roli zadaného objektu. (Přepisuje [CWnd::get_accRole](../../mfc/reference/cwnd-class.md#get_accrole).)|  
|[CBasePane::get_accSelection](#get_accselection)|Voláno rámcem načíst vybrané podřízené objekty tohoto objektu. (Přepisuje [CWnd::get_accSelection](../../mfc/reference/cwnd-class.md#get_accselection).)|  
|`CBasePane::get_accState`|Voláno rámcem načíst aktuální stav zadaného objektu. (Přepisuje [CWnd::get_accState](../../mfc/reference/cwnd-class.md#get_accstate).)|  
|`CBasePane::get_accValue`|Voláno rámcem k načtení hodnoty vlastností zadaného objektu. (Přepisuje [CWnd::get_accValue](../../mfc/reference/cwnd-class.md#get_accvalue).)|  
|[CBasePane::GetCaptionHeight](#getcaptionheight)|Vrátí popisek výšku.|  
|[CBasePane::GetControlBarStyle](#getcontrolbarstyle)|Vrátí ovládací prvek panelu styl.|  
|[CBasePane::GetCurrentAlignment](#getcurrentalignment)|Vrátí aktuální zarovnání podokně.|  
|[CBasePane::GetDockingMode](#getdockingmode)|Vrátí aktuální ukotvení režim pro podokně.|  
|[CBasePane::GetDockSiteFrameWnd](#getdocksiteframewnd)|Vrací ukazatel na okně, které je lokalita ukotvení pro podokně.|  
|[CBasePane::GetEnabledAlignment](#getenabledalignment)|Vrátí CBRS_ALIGN_ stylů, které se použijí do podokna.|  
|[CBasePane::GetMFCStyle](#getmfcstyle)|Vrátí styly podokně podle MFC.|  
|[CBasePane::GetPaneIcon](#getpaneicon)|Vrátí popisovač na ikonu podokně.|  
|`CBasePane::GetPaneRect`|Interně.|  
|[CBasePane::GetPaneRow](#getpanerow)|Vrátí ukazatel [CDockingPanesRow](../../mfc/reference/cdockingpanesrow-class.md)objektu, kde je ukotvena podokně.|  
|[CBasePane::GetPaneStyle](#getpanestyle)|Vrátí styl podokně.|  
|[CBasePane::GetParentDockSite](#getparentdocksite)|Vrátí ukazatel na nadřazenou lokalitu ukotvení.|  
|[CBasePane::GetParentMiniFrame](#getparentminiframe)|Vrací ukazatel na nadřazeného zkrácená rámce okna.|  
|[CBasePane::GetParentTabbedPane](#getparenttabbedpane)|Vrátí ukazatel do podokna s kartami nadřazené.|  
|[CBasePane::GetParentTabWnd](#getparenttabwnd)|Vrátí ukazatel do nadřazeného okna, který je uvnitř na kartě.|  
|[CBasePane::GetRecentVisibleState](#getrecentvisiblestate)|Tato metoda volá framework podokno po obnovení z archivu.|  
|[CBasePane::HideInPrintPreviewMode](#hideinprintpreviewmode)|Určuje, zda je v náhledu tisku skryté v podokně.|  
|[CBasePane::InsertPane](#insertpane)|Zaregistruje zadané podokně se správce ukotvení.|  
|[CBasePane::IsAccessibilityCompatible](#isaccessibilitycompatible)|Určuje, jestli v podokně podporuje Active Accessibility.|  
|[CBasePane::IsAutoHideMode](#isautohidemode)|Určuje, zda podokno v režimu automaticky skrýt.|  
|[CBasePane::IsDialogControl](#isdialogcontrol)|Určuje, jestli je v podokně ovládací prvek dialogového okna.|  
|[CBasePane::IsDocked](#isdocked)|Určuje, zda je ukotvena podokně.|  
|[CBasePane::IsFloating](#isfloating)|Určuje, zda je číslo s plovoucí čárkou podokně.|  
|[CBasePane::IsHorizontal](#ishorizontal)|Určuje, zda je v podokně umístěn vodorovně.|  
|[CBasePane::IsInFloatingMultiPaneFrameWnd](#isinfloatingmultipaneframewnd)|Určuje, zda v podokně v rámci více podokně okna.|  
|[CBasePane::IsMDITabbed](#ismditabbed)|Určuje, zda v podokně se přidal do okna MDI podřízené jako dokumentů s kartami.|  
|[CBasePane::IsPaneVisible](#ispanevisible)|Určuje, zda `WS_VISIBLE` je pro podokně nastaven příznak.|  
|[CBasePane::IsPointNearDockSite](#ispointneardocksite)|Určuje, zda zadaný bod je téměř webu ukotvení.|  
|[CBasePane::IsResizable](#isresizable)|Určuje, zda jde změnit, v podokně.|  
|[CBasePane::IsRestoredFromRegistry](#isrestoredfromregistry)|Určuje, zda je v podokně Obnovit z registru.|  
|[CBasePane::IsTabbed](#istabbed)|Určuje, zda byl vložen v podokně ovládacího prvku karta záložkách okna.|  
|`CBasePane::IsTooltipTopmost`|Interně.|  
|[CBasePane::IsVisible](#isvisible)|Určuje, zda je zobrazen v podokně.|  
|[CBasePane::LoadState](#loadstate)|Načte stav podokně z registru.|  
|[CBasePane::MoveWindow](#movewindow)|Přesune podokně.|  
|[CBasePane::OnAfterChangeParent](#onafterchangeparent)|Voláno rámcem, pokud byl změněn v podokně nadřazené.|  
|[CBasePane::OnBeforeChangeParent](#onbeforechangeparent)|Voláno rámcem těsně před podokně změní jeho nadřazeného okna.|  
|[CBasePane::OnDrawCaption](#ondrawcaption)|Tato metoda volá framework při sestavování titulek.|  
|[CBasePane::OnMovePaneDivider](#onmovepanedivider)|Tato metoda není aktuálně používá.|  
|[CBasePane::OnPaneContextMenu](#onpanecontextmenu)|Voláno rámcem při vytváření nabídky, která má seznam podokna.|  
|[CBasePane::OnRemoveFromMiniFrame](#onremovefromminiframe)|Voláno rámcem Pokud podokno je odebrán z jeho nadřazeného mini rámce okna.|  
|[CBasePane::OnSetAccData](#onsetaccdata)|`CBasePane` Tato metoda nepoužívá.|  
|`CBasePane::OnUpdateCmdUI`|Interně.|  
|[CBasePane::PaneFromPoint](#panefrompoint)|Vrátí panel, který obsahuje danému bodu.|  
|`CBasePane::PreTranslateMessage`|Používá třída [CWinApp](../../mfc/reference/cwinapp-class.md) přeložit zprávy oken, než jsou odeslány do [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) a [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funkce systému Windows. (Přepisuje [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|  
|[CBasePane::RecalcLayout](#recalclayout)|`CBasePane` Tato metoda nepoužívá.|  
|[CBasePane::RemovePaneFromDockManager](#removepanefromdockmanager)|Zruší registraci podokno a odstraní ji ze seznamu ve Správci ukotvení.|  
|[CBasePane::SaveState](#savestate)|V podokně Stav uloží do registru.|  
|[CBasePane::SelectDefaultFont](#selectdefaultfont)|Vybere písmo výchozího kontextu daného zařízení.|  
|`CBasePane::Serialize`|Čtení nebo zápisu tento objekt z nebo do archivu. (Přepisuje [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize).)|  
|[CBasePane::SetControlBarStyle](#setcontrolbarstyle)|Nastaví styl panelu ovládacího prvku.|  
|[CBasePane::SetDockingMode](#setdockingmode)|Nastaví ukotvení režim pro podokně.|  
|`CBasePane::SetMDITabbed`|Interně.|  
|[CBasePane::SetPaneAlignment](#setpanealignment)|Nastaví zarovnání v podokně.|  
|`CBasePane::SetPaneRect`|Interně.|  
|[CBasePane::SetPaneStyle](#setpanestyle)|Nastavuje styl podokna.|  
|`CBasePane::SetRestoredFromRegistry`|Interně.|  
|[CBasePane::SetWindowPos](#setwindowpos)|Změní velikost, umístění a pořadí Z-order podokna.|  
|[CBasePane::ShowPane](#showpane)|Zobrazí či skryje panel.|  
|[CBasePane::StretchPane](#stretchpane)|Podokno roztahovány vodorovně nebo svisle.|  
|[CBasePane::UndockPane](#undockpane)|V podokně se odebere z webu ukotvení, výchozí posuvníku nebo zkrácená rámec okna, kde je aktuálně ukotven.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CBasePane::DoPaint](#dopaint)|Doplní na pozadí v podokně.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud chcete vytvořit podokně třídu, která podporuje rozšířené ukotvení funkce dostupné v prostředí MFC, musí být odvozen z `CBasePane` nebo z [CPane třída](../../mfc/reference/cpane-class.md).  
  
## <a name="customization-tips"></a>Tipy k přizpůsobení  
 Následující tipy k přizpůsobení týkají `CBasePane Class` a všechny třídy, které dědí z tohoto:  
  
-   Když vytvoříte podokno, můžete použít několik nových stylů:  
  
    - `AFX_CBRS_FLOAT` Díky podokně float.  
  
    - `AFX_CBRS_AUTOHIDE` Umožňuje automaticky skrýt režimu.  
  
    - `AFX_CBRS_CLOSE` Umožňuje v podokně bude uzavřen (skryté).  
  
     Jedná se o příznaky, které můžete kombinovat s bitové operace OR operaci.  
  
 `CBasePane` implementuje virtuální Boolean metodu tak, aby odrážela tyto příznaky: [CBasePane::CanBeClosed](#canbeclosed), [CBasePane::CanAutoHide](#canautohide), [CBasePane::CanFloat](#canfloat). V odvozených třídách k přizpůsobení jejich chování můžete přepsat je.  
  
-   Můžete přizpůsobit ukotvení chování přepisování [CBasePane::CanAcceptPane](#canacceptpane). Vaše podokno vrátit `FALSE` z tuto metodu za účelem zabránit jiného podokna ukotvení na ni.  
  
-   Pokud chcete vytvořit statické podokně, který nelze float a, který brání jiných podokně ukotvení dříve, než se (podobně jako v příkladu OutlookDemo panel aplikace Outlook), vytvořte ho ne plovoucí a přepsat [CBasePane::DoesAllowDynInsertBefore](#doesallowdyninsertbefore) vrátit `FALSE`. Výchozí implementace vrací `FALSE` Pokud podokně je vytvořen bez `AFX_CBRS_FLOAT` stylu.  
  
-   Vytvořte všechny podokna s ID než -1.  
  
-   Chcete-li určit viditelnost podokně, použijte [CBasePane::IsVisible](#isvisible). Správně zpracovává stav viditelnosti v s kartami a automaticky skrýt režimy.  
  
-   Pokud chcete vytvořit s plovoucí umožňující změnu velikosti podokna, vytvořte ho bez `AFX_CBRS_FLOAT` style a volání [CFrameWnd::DockControlBar](../../mfc/reference/cframewnd-class.md#dockcontrolbar).  
  
-   Chcete vyloučit z dokovací rozložení podokno nebo panel nástrojů odeberete z jeho ukotvení panelu volání [CBasePane::UndockPane](#undockpane). Nevolejte tuto metodu pro podokna v režimu automaticky skrýt nebo podokna, které jsou umístěny na kartách záložkách Windows.  
  
-   Pokud chcete float nebo zrušení ukotvení podokně, který je v režimu automaticky skrýt, musí volat [CDockablePane::SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode) s `FALSE` jako první argument před voláním [CBasePane::FloatPane](#floatpane) nebo [ CBasePane::UndockPane](#undockpane).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí různých metod v nástroji `CBasePane` třídy. Příklad ukazuje, jak načíst podokně z `CFrameWndEx` třídy a jak nastavit ukotvení režimu, zarovnání podokně a podokně stylu. Kód je z [ukázkové aplikace Word Pad](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad#2](../../mfc/reference/codesnippet/cpp/cbasepane-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxbasepane.h  
  
##  <a name="accnotifyobjectfocusevent"></a>  CBasePane::AccNotifyObjectFocusEvent  
 `CBasePane` Tato metoda nepoužívá.  
  
```  
virtual void AccNotifyObjectFocusEvent(int);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `int`  
 Nepoužívá se.  
  
##  <a name="addpane"></a>  CBasePane::AddPane  
 Přidá podokno správce ukotvení.  
  
```  
void AddPane(CBasePane* pBar);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pBar`  
 Ukazatel na podokno pro přidání.  
  
### <a name="remarks"></a>Poznámky  
 Toto je užitečný metodu, která přidá podokno manažera ukotvení. Pomocí této metody nemáte napsat kód, který analyzuje typ nadřazeného rámce.  
  
 Další informace najdete v tématu [CDockingManager třída](../../mfc/reference/cdockingmanager-class.md) a [CMDIFrameWndEx::AddPane](../../mfc/reference/cmdiframewndex-class.md#addpane).  
  
##  <a name="adjustdockinglayout"></a>  CBasePane::AdjustDockingLayout  
 Přesměruje volání na ukotvení manager upravit ukotvení rozložení.  
  
```  
virtual void AdjustDockingLayout(HDWP hdwp=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [out] `hdwp`  
 Obslužná rutina pro strukturu obsahující více pozic okno.  
  
### <a name="remarks"></a>Poznámky  
 Toto je užitečný metodu, která upraví rozložení ukotvení. Pomocí této metody nemáte napsat kód, který analyzuje typ nadřazeného rámce.  
  
 Další informace najdete v tématu [CDockingManager::AdjustDockingLayout](../../mfc/reference/cdockingmanager-class.md#adjustdockinglayout)  
  
##  <a name="adjustlayout"></a>  CBasePane::AdjustLayout  
 Voláno rámcem upravit interní rozložení podokno.  
  
```  
virtual void AdjustLayout();
```  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework volá tuto metodu, když má podokno upravit jeho vnitřní rozložení. Základní implementaci neprovede žádnou akci.  
  
##  <a name="calcfixedlayout"></a>  CBasePane::CalcFixedLayout  
 Vypočítá vodorovné velikosti ovládacích pruhů.  
  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bStretch`  
 Určuje, zda by měl být roztažen tak panelu, aby velikost rámečku. `bStretch` Parametr je nenulové hodnoty v případě, že na panelu není ukotvení panelu (není k dispozici pro ukotvení) a 0, když je ukotveného nebo plovoucí (k dispozici pro ukotvení).  
  
 [v] `bHorz`  
 Označuje, že je na panelu orientované vodorovně nebo svisle. `bHorz` Parametr je nenulové hodnoty v případě panelu orientován vodorovně a je 0, pokud je to svisle orientovaný.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ovládacích pruhů velikost, v pixelech, nástroje `CSize` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Najdete v tématu Poznámky [CControlBar::CalcFixedLayout](../../mfc/reference/ccontrolbar-class.md#calcfixedlayout)  
  
##  <a name="canacceptpane"></a>  CBasePane::CanAcceptPane  
 Určuje, zda lze do podokna ukotvit jiného podokna.  
  
```  
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pBar`  
 Ukazatel na podokno ukotvení.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud nelze přijmout jiného podokna; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá framework předtím, než ho ukotvené podokně určeného `pBar` do podokna aktuální.  
  
 Tuto metodu použít a [CBasePane::CanBeDocked](#canbedocked) metoda řídit, jak podokna ukotvení na Další podokna ve vaší aplikaci.  
  
 Výchozí implementace vrací `FALSE`.  
  
##  <a name="canautohide"></a>  CBasePane::CanAutoHide  
 Určuje, zda v podokně podporuje režim automaticky skrýt.  
  
```  
virtual BOOL CanAutoHide() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud v tomto podokně podporuje režim automaticky skrýt; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Volá rámec této funkci můžete zjistit, jestli v podokně podporuje režim automaticky skrýt.  
  
 Během vytváření, můžete nastavit možnost předáním `AFX_CBRS_AUTOHIDE` příznak, který [CBasePane::CreateEx](#createex).  
  
 Výchozí implementace vyhledává `AFX_CBRS_AUTOHIDE` příznak. Potlačí tuto metodu v odvozené třídě přizpůsobit toto chování.  
  
##  <a name="canbeattached"></a>  CBasePane::CanBeAttached  
 Určuje, zda lze ukotvit podokně do jiného podokno nebo rámec okna.  
  
```  
virtual BOOL CanBeAttached() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud v podokně lze ukotvit do jiného podokno nebo rámec okna; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace vrací `FALSE`. Potlačí tuto metodu v odvozené třídě chcete povolit nebo zakázat možnost ukotvení bez volání [CBasePane::EnableDocking](#enabledocking).  
  
##  <a name="canbeclosed"></a>  CBasePane::CanBeClosed  
 Určuje, zda je možné uzavřít podokně.  
  
```  
virtual BOOL CanBeClosed() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je možné uzavřít podokně; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework volá tuto metodu za účelem určení, zda je možné uzavřít podokně. Pokud metoda vrátí `TRUE`, **Zavřít** tlačítko se přidá do záhlaví v podokně nebo, pokud je v podokně plovoucí, na záhlaví okna miniframe v podokně.  
  
 Během vytváření, můžete nastavit možnost předáním `AFX_CBRS_CLOSE` příznak, který [CBasePane::CreateEx](#createex).  
  
 Výchozí implementace vyhledává `AFX_CBRS_CLOSE` příznak.  
  
##  <a name="canbedocked"></a>  CBasePane::CanBeDocked  
 Určuje, zda lze ukotvit podokně do jiného podokna.  
  
```  
virtual BOOL CanBeDocked(CBasePane* pDockBar) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDockBar`  
 Ukazatel na jiného podokna.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud v tomto podokně můžete ukotven do jiného podokna; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá framework předtím, než ho ukotvené podokně určeného `pDockBar` do podokna aktuální.  
  
 Tuto metodu použít a [CBasePane::CanAcceptPane](#canacceptpane) metoda řídit, jak podokna ukotvení na Další podokna ve vaší aplikaci.  
  
 Výchozí implementace vrací `FALSE`.  
  
##  <a name="canberesized"></a>  CBasePane::CanBeResized  
 Určuje, zda jde změnit, v podokně.  
  
```  
virtual BOOL CanBeResized() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je velikost lze změnit v podokně; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda zkontroluje `AFX_CBRS_RESIZE` příznak, který je určený ve výchozím nastavení v `CBasePane::OnCreate`. Pokud tento příznak není zadán, správce ukotvení příznaky podokně interně nejširší místo ukotvení.  
  
##  <a name="canbetabbeddocument"></a>  CBasePane::CanBeTabbedDocument  
 Určuje, zda v podokně můžete převést na dokument s kartami MDI.  
  
```  
virtual BOOL CanBeTabbedDocument() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud v podokně můžete převést na záložkách dokument; v opačném `FALSE`. `CBasePane::CanBeTabbedDocument` vždy vrátí hodnotu `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Pouze objekty určité `CBasePane`-odvozené typy, jako například [CDockablePane Class](../../mfc/reference/cdockablepane-class.md), může být převeden na dokumentů s kartami.  
  
##  <a name="canfloat"></a>  CBasePane::CanFloat  
 Určuje, zda můžete v podokně float.  
  
```  
virtual BOOL CanFloat() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud v podokně můžete float; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework volá tuto metodu za účelem určení, zda můžete v podokně float.  
  
 Během vytváření, můžete nastavit možnost předáním `AFX_CBRS_FLOAT` příznak, který [CBasePane::CreateEx](#createex).  
  
> [!NOTE]
>  Rozhraní framework předpokládá, že s plovoucí podokna statické a že nelze změnit jejich ukotvení stavu. Rozhraní framework proto neuloží ukotvení stav s plovoucí podokna.  
  
 Výchozí implementace vyhledává `AFX_CBRS_FLOAT` stylu.  
  
##  <a name="canfocus"></a>  CBasePane::CanFocus  
 Určuje, zda v podokně mohou získat fokus.  
  
```  
virtual BOOL CanFocus() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud v podokně mohou získat fokus; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu v odvozené třídě k řízení fokus. Například, protože panely nástrojů nemůže přijmout fokus, tato metoda vrátí `FALSE` když je volána na panelu nástrojů objekty.  
  
 Rozhraní framework pokusí se nastavit zaměření pro vstup, pokud je ukotveno nebo obtékané podokno.  
  
##  <a name="copystate"></a>  CBasePane::CopyState  
 Zkopíruje stav daného podokně.  
  
```  
virtual void CopyState(CBasePane* pOrgBar);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pOrgBar`  
 Ukazatel na jiného podokna.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda zkopíruje stavu z `pOrgBar` na tomto podokně.  
  
##  <a name="createdefaultminiframe"></a>  CBasePane::CreateDefaultMiniframe  
 Pokud v podokně můžete float, tato metoda vytvoří pro ni zkrácená rámce okna.  
  
```  
virtual CPaneFrameWnd* CreateDefaultMiniframe(CRect rectInitial);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `rectInitial`  
 Určuje počáteční souřadnice zkrácená rámce okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nové okno zkrácená rámce nebo `NULL` Pokud vytvoření se nezdařilo.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá framework při podokno se přepne do stavu plovoucí. Metoda vytvoří zkrácená rámce okna a v podokně k toto okno.  
  
 Výchozí implementace vrací `NULL`.  
  
##  <a name="createex"></a>  CBasePane::CreateEx  
 Vytvoří ovládacího prvku podokno.  
  
```  
virtual BOOL CreateEx(
    DWORD dwStyleEx,  
    LPCTSTR lpszClassName,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID,  
    DWORD dwControlBarStyle=0,  
    CCreateContext* pContext=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `dwStyleEx`  
 Rozšířené styly (viz [CWnd::CreateEx](../../mfc/reference/cwnd-class.md#createex) informace).  
  
 [v] `lpszClassName`  
 Název třídy oken.  
  
 [v] `lpszWindowName`  
 Název časového období.  
  
 [v] `dwStyle`  
 Styl okna (viz [CWnd::CreateEx](../../mfc/reference/cwnd-class.md#createex)).  
  
 [v] `rect`  
 Počáteční rámeček.  
  
 [v] `pParentWnd`  
 Ukazatel do nadřazeného okna.  
  
 [v] `nID`  
 Určuje ID podokně. Musí být jedinečný.  
  
 [v] `dwControlBarStyle`  
 Styl příznaky pro podokna.  
  
 [v] `pContext`  
 ukazatele na `CcreateContext`  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud se v podokně se úspěšně; vytvořil. v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoří okno třídy `lpszClassName`. Pokud zadáte `WS_CAPTION`, tato metoda odstraní `WS_CAPTION` bit stylu a nastaví `CBasePane::m_bHasCaption` k `TRUE`, protože knihovny nepodporuje podokna s titulky.  
  
 Můžete použít libovolnou kombinaci styly oken podřízené a MFC ovládací prvek panelu Styly (CBRS_).  
  
 Knihovny přidá několik nových stylů pro podokna. Následující tabulka popisuje nové styly:  
  
|Styl|Popis|  
|-----------|-----------------|  
|`AFX_CBRS_FLOAT`|V podokně můžete float.|  
|`AFX_CBRS_AUTOHIDE`|V podokně podporuje režim automaticky skrýt|  
|`AFX_CBRS_RESIZE`|V podokně můžete změnit. **Důležité:** tento styl není implementována.|  
|`AFX_CBRS_CLOSE`|V podokně je možné uzavřít.|  
|`AFX_CBRS_AUTO_ROLLUP`|V podokně můžete zajišťován, když ji uvolnit.|  
|`AFX_CBRS_REGULAR_TABS`|Pokud jeden podokno ukotvené do jiného podokna, který má tento styl, vytvoří se regulární okno s kartami. (Další informace najdete v tématu [CTabbedPane třída](../../mfc/reference/ctabbedpane-class.md).)|  
|`AFX_CBRS_OUTLOOK_TABS`|Když jeden podokno ukotvené do jiného podokna, který má tento styl, vytvoří se záložkách okno aplikace Outlook stylu. (Další informace najdete v tématu [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md).)|  
  
 Pokud chcete používat nové styly, zadejte je v `dwControlBarStyle`.  
  
##  <a name="dockpane"></a>  CBasePane::DockPane  
 Podokno ukotvené jiného podokna nebo okně s rámečkem.  
  
```  
virtual BOOL DockPane(
    CBasePane* pDockBar,  
    LPCRECT lpRect,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDockBar`  
 Ukazatel na jiného podokna.  
  
 [v] `lpRect`  
 Určuje cílový rámeček.  
  
 [v] `dockMethod`  
 Určuje metodu ukotvení.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud byl úspěšně; ukotven ovládacích pruhů v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce lze ukotvit podokno další podokno nebo ukotvení panelu ( [CDockSite třída](../../mfc/reference/cdocksite-class.md)), který je určen podle `pDockBar`, nebo hlavní rámec Pokud `pDockBar` je `NULL`.  
  
 `dockMethod` Určuje, jak je ukotvena podokně. V tématu [CPane::DockPane](../../mfc/reference/cpane-class.md#dockpane) seznam možných hodnot.  
  
##  <a name="dockpaneusingrtti"></a>  CBasePane::DockPaneUsingRTTI  
 V podokně ukotvené pomocí informace běhového typu.  
  
```  
void DockPaneUsingRTTI(BOOL bUseDockSite);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bUseDockSite`  
 Pokud `TRUE`, ukotvení pro ukotvení lokality. Pokud `FALSE`, ukotvení do nadřazeného rámce.  
  
##  <a name="docktoframewindow"></a>  CBasePane::DockToFrameWindow  
 Lze ukotvit podokně ukotvené na snímek.  
  
```  
virtual BOOL DockToFrameWindow(
    DWORD dwAlignment,  
    LPCRECT lpRect = NULL,  
    DWORD dwDockFlags = DT_DOCK_LAST,  
    CBasePane* pRelativeBar = NULL,  
    int nRelativeIndex = -1,  
    BOOL bOuterEdge = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `dwAlignment`  
 Na straně nadřazené rámce, který chcete ukotvit podokno.  
  
 [v] `lpRect`  
 Požadovaná velikost.  
  
 [v] `dwDockFlags`  
 Ignorovat.  
  
 [v] `pRelativeBar`  
 Ignorovat.  
  
 [v] `nRelativeIndex`  
 Ignorovat.  
  
 [v] `bOuterEdge`  
 Pokud `TRUE` a neexistují další lze ukotvit podokna na stranu určeného `dwAlignment`, v podokně ukotven mimo jiné podokna blíže okraje nadřazeného rámce. Pokud `FALSE`, v podokně ukotven blíže k centru klientské oblasti.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud metoda byla úspěšná. v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda selže, pokud rozdělovací podokně ( [CPaneDivider třída](../../mfc/reference/cpanedivider-class.md)) nelze vytvořit. Jinak vždy vrátí `TRUE`.  
  
##  <a name="doesallowdyninsertbefore"></a>  CBasePane::DoesAllowDynInsertBefore  
 Určuje, zda jiný podokně můžete dynamicky vložen mezi v tomto podokně a nadřazeného rámce.  
  
```  
virtual BOOL DoesAllowDynInsertBefore() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud uživatel můžete vložit další podokna. v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework volá tuto metodu za účelem určení, zda může uživatel dynamicky vkládat podokně před v tomto podokně.  
  
 Předpokládejme například, že vaše aplikace vytvoří podokno ukotven na levé straně rámečku (například panelu aplikace Outlook). Abyste zabránili ukotvení jiného podokna nalevo od podokně první uživatel, přepíše tuto metodu a vrátí `FALSE`.  
  
 Doporučujeme, abyste tuto metodu přepsat a vrátí `FALSE` pro s plovoucí podokna odvozené od [CDockablePane Class](../../mfc/reference/cdockablepane-class.md).  
  
 Výchozí implementace vrací `TRUE`.  
  
##  <a name="dopaint"></a>  CBasePane::DoPaint  
 Doplní na pozadí v podokně.  
  
```  
virtual void DoPaint(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDC`  
 Ukazatel na kontextu zařízení.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace volá aktuální visual správce k vyplnění na pozadí ( [CMFCVisualManager::OnFillBarBackground](../../mfc/reference/cmfcvisualmanager-class.md#onfillbarbackground)).  
  
##  <a name="enabledocking"></a>  CBasePane::EnableDocking  
 Umožňuje ukotvení podokna do hlavního rámce.  
  
```  
virtual void EnableDocking(DWORD dwAlignment);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `dwAlignment`  
 Určuje zarovnání ukotvení povolit.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu za účelem povolení ukotvení zarovnání do hlavního rámce. Můžete předat kombinaci `CBRS_ALIGN_` příznaky (Další informace najdete v tématu [CControlBar::EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking)).  
  
 `EnableDocking` Nastaví příznak interní `CBasePane::m_dwEnabledAlignment` a rozhraní zkontroluje tento příznak, když je ukotvena podokno.  
  
 Volání [CBasePane::GetEnabledAlignment](#getenabledalignment) k určení ukotvení zarovnání podokno.  
  
##  <a name="enablegripper"></a>  CBasePane::EnableGripper  
 Povolí nebo zakáže úchytu. Pokud je povoleno úchytu, můžete přetáhnout uživatele, aby přemístil v podokně.  
  
```  
virtual void EnableGripper(BOOL bEnable);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bEnable`  
 `TRUE` Chcete-li povolit úchytu; `FALSE` ji zakázat.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní používá tato metoda umožňující úchytu místo použití `WS_CAPTION` stylu.  
  
##  <a name="floatpane"></a>  CBasePane::FloatPane  
 Obtéká podokně.  
  
```  
virtual BOOL FloatPane(
    CRect rectFloat,  
    AFX_DOCK_METHOD dockMethod=DM_UNKNOWN,  
    bool bShow=true);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `rectFloat`  
 Určuje souřadnice obrazovky, kde se zobrazí v podokně plovoucí.  
  
 [v] `dockMethod`  
 Určuje metodu ukotvení sloužící k float podokně.  
  
 [v] `bShow`  
 Určuje, jestli je viditelná podokně plovoucí ( `TRUE`) nebo skryté ( `FALSE`).  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud se v podokně obtékané úspěšně; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Volat tuto metodu za účelem uvolnit podokno na pozici obrazovky určeného `rectFloat`.  
  
##  <a name="get_acchelptopic"></a>  CBasePane::get_accHelpTopic  
 Architektura volá tuto metodu za účelem načtení úplnou cestu `WinHelp` soubor, který je přidružen zadaného objektu a tento identifikátor příslušné téma v tomto souboru.  
  
```  
virtual HRESULT get_accHelpTopic(
    BSTR* pszHelpFile,  
    VARIANT varChild,  
    long* pidTopic);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pszHelpFile`  
 Adresa `BSTR` která přijme úplnou cestu `WinHelp` soubor, který je přidružen zadaný objekt, pokud existuje.  
  
 [v] `varChild`  
 Určuje, zda tématu nápovědy k načtení je, že objekt nebo některý z podřízených elementů objektu. Tento parametr může být buď `CHILDID_SELF` (Chcete-li získat téma nápovědy pro objekt) nebo ID podřízeného (k získání tématu nápovědy pro jedné z podřízených elementů objektu).  
  
 [v] `pidTopic`  
 Identifikuje `Help` souboru téma, které souvisí se zadaným objektem.  
  
### <a name="return-value"></a>Návratová hodnota  
 `CBasePane` Tato metoda neimplementuje. Proto `CBasePane::get_accHelpTopic` vždy vrátí hodnotu `S_FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je součástí podpora Active Accessibility v MFC. Potlačí tuto funkci v odvozené třídě poskytuje nápovědu informace o objektu.  
  
##  <a name="get_accselection"></a>  CBasePane::get_accSelection  
 Rozhraní framework volá tuto metodu za účelem načtení vybrané podřízené objekty tohoto objektu.  
  
```  
virtual HRESULT get_accSelection(VARIANT* pvarChildren);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pvarChildren`  
 Přijímá informace, které identifikují vybrané podřízené objekty.  
  
### <a name="return-value"></a>Návratová hodnota  
 `CBasePane` Tato metoda neimplementuje. Pokud `pvarChildren` je `NULL`, vrátí tato metoda `E_INVALIDARG`. Jinak tato metoda vrátí hodnotu `DISP_E_MEMBERNOTFOUND`.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je součástí podpora Active Accessibility v MFC. Funkci v odvozené třídě přepište, pokud máte jiný oddílové prvky rozhraní než – ovládací prvky ActiveX bez oken.  
  
##  <a name="getcaptionheight"></a>  CBasePane::GetCaptionHeight  
 Vrátí popisek výšku.  
  
```  
virtual int GetCaptionHeight() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výška titulek.  
  
##  <a name="getcontrolbarstyle"></a>  CBasePane::GetControlBarStyle  
 Vrátí ovládací prvek panelu styl.  
  
```  
virtual DWORD GetControlBarStyle() const 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Bitový operátor OR kombinace AFX_CBRS_ příznaky.  
  
### <a name="remarks"></a>Poznámky  
 Vrácená hodnota je kombinací následujících hodnot.  
  
|Styl|Popis|  
|-----------|-----------------|  
|`AFX_CBRS_FLOAT`|Díky float panel ovládacího prvku.|  
|`AFX_CBRS_AUTOHIDE`|Umožňuje automaticky skrýt režimu.|  
|`AFX_CBRS_RESIZE`|Umožňuje změnu velikosti panelu ovládacího prvku. Pokud je tento příznak nastaven, ovládacích pruhů můžete umístit do lze ukotvit podokně.|  
|`AFX_CBRS_CLOSE`|Umožňuje skrytí panelu ovládacího prvku.|  
  
##  <a name="getcurrentalignment"></a>  CBasePane::GetCurrentAlignment  
 Vrátí aktuální zarovnání podokně.  
  
```  
virtual DWORD GetCurrentAlignment() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální zarovnání ovládacích pruhů. V následující tabulce jsou uvedeny možné hodnoty:  
  
|Hodnota|Zarovnání|  
|-----------|---------------|  
|`CBRS_ALIGN_LEFT`|Zarovnání doleva.|  
|`CBRS_ALIGN_RIGHT`|Zarovnání doprava.|  
|`CBRS_ALIGN_TOP`|Zarovnání nahoru.|  
|`CBRS_ALIGN_BOTTOM`|Zarovnání dolů.|  
  
##  <a name="getdockingmode"></a>  CBasePane::GetDockingMode  
 Vrátí aktuální ukotvení režim pro podokně.  
  
```  
virtual AFX_DOCK_TYPE GetDockingMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Na obrazovce vyplývá z obdélníku přetáhněte DT_STANDARD Pokud přetahování podokně. DT_IMMEDIATE, pokud jsou přetáhli obsah v podokně.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework volá tuto metodu za účelem určení aktuální režim ukotvení podokna.  
  
 Pokud `CBasePane::m_dockMode` je nedefinovaný (DT_UNDEFINED), pak ukotvení režimu jsou převzaty z globální ukotvení režimu ( `AFX_GLOBAL_DATA::m_dockModeGlobal`).  
  
 Nastavením `m_dockMode` nebo přepsání `GetDockingMode` můžete řídit ukotvení režim pro každý podokně.  
  
##  <a name="getdocksiteframewnd"></a>  CBasePane::GetDockSiteFrameWnd  
 Vrátí ukazatel [CDockingPanesRow](../../mfc/reference/cdockingpanesrow-class.md)objektu, kde je ukotvena podokně.  
  
```  
virtual CWnd* GetDockSiteFrameWnd() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na webu ukotvení podokna.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu za účelem získání ukazatele na webu ukotvení podokna. Ukotvení lokality může být buď okno rámce Pokud podokně ukotven hlavního rámce, nebo zkrácená rámce okna, pokud je plovoucí podokně.  
  
##  <a name="getenabledalignment"></a>  CBasePane::GetEnabledAlignment  
 Vrátí CBRS_ALIGN_ stylů, které se použijí do podokna.  
  
```  
virtual DWORD GetEnabledAlignment() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Kombinace CBRS_ALIGN_ stylů. V následující tabulce jsou uvedeny možné styly:  
  
|Příznak|Povoleno zarovnání|  
|----------|-----------------------|  
|`CBRS_ALIGN_LEFT`|Vlevo.|  
|`CBRS_ALIGN_RIGHT`|Práva.|  
|`CBRS_ALIGN_TOP`|Nejvyšší.|  
|`CBRS_ALIGN_BOTTOM`|Dolní.|  
|`CBRS_ALIGN_ANY`|Kombinace všechny příznaků.|  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu za účelem určení povoleno zarovnání v podokně. Povoleno zarovnání znamená postranní hlavního rámce okna, které můžete podokno ukotvit.  
  
 Povolení ukotvení zarovnání pomocí [CBasePane::EnableDocking](#enabledocking).  
  
##  <a name="getmfcstyle"></a>  CBasePane::GetMFCStyle  
 Vrátí podokně stylů, které jsou specifické pro MFC.  
  
```  
virtual DWORD GetMFCStyle() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Kombinace specifické knihovny (AFX_CBRS_) podokně styly.  
  
##  <a name="getpaneicon"></a>  CBasePane::GetPaneIcon  
 Vrátí popisovač na ikonu podokně.  
  
```  
virtual HICON GetPaneIcon(BOOL bBigIcon);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bBigIcon`  
 Určuje 32 pixelů ikonou 32 pixelů, pokud `TRUE`; Určuje 16 pixelů ikonou 16 pixelů, pokud `FALSE`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro ikonu podokně. Pokud je úspěšné, vrátí `NULL`.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace volá [CWnd::GetIcon](../../mfc/reference/cwnd-class.md#geticon).  
  
##  <a name="getpanerow"></a>  CBasePane::GetPaneRow  
 Vrátí ukazatel [CDockingPanesRow](../../mfc/reference/cdockingpanesrow-class.md)objektu, kde je ukotvena podokně.  
  
```  
CDockingPanesRow* GetPaneRow();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na `CDockingPanesRow` -li v podokně ukotven, nebo `NULL` Pokud je s plovoucí čárkou.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu pro přístup k řádku, kde je ukotvena podokno. Například uspořádat podokna v konkrétního řádku, volání `GetPaneRow` a pak zavolají [CDockingPanesRow::ArrangePanes](../../mfc/reference/cdockingpanesrow-class.md#arrangepanes).  
  
##  <a name="getpanestyle"></a>  CBasePane::GetPaneStyle  
 Vrátí styl podokně.  
  
```  
virtual DWORD GetPaneStyle() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Kombinace styly ovládacího prvku panel (včetně CBRS_ styly) které nastavil [CBasePane::SetPaneStyle](#setpanestyle) metoda v okamžiku vytvoření.  
  
##  <a name="getparentdocksite"></a>  CBasePane::GetParentDockSite  
 Vrátí ukazatel na nadřazenou lokalitu ukotvení.  
  
```  
virtual CDockSite* GetParentDockSite() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukotvení nadřazené lokality.  
  
##  <a name="getparentminiframe"></a>  CBasePane::GetParentMiniFrame  
 Vrací ukazatel na nadřazeného zkrácená rámce okna.  
  
```  
virtual CPaneFrameWnd* GetParentMiniFrame(BOOL bNoAssert=FALSE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bNoAssert`  
 Pokud `TRUE`, tato metoda nekontroluje neplatné ukazatele. Pokud tuto metodu lze volat při ukončení aplikace, nastavte tento parametr `TRUE`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Neplatný ukazatel do nadřazeného okna zkrácená rámečku, pokud je v podokně plovoucí; v opačném případě `NULL`.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce načíst ukazatel na nadřazeného zkrácená rámce okna. Tato metoda iteruje všechny nadřazené objekty a kontroly pro objekt odvozené z [CPaneFrameWnd třída](../../mfc/reference/cpaneframewnd-class.md).  
  
 Použití `GetParentMiniFrame` k určení, zda je číslo s plovoucí čárkou podokně.  
  
##  <a name="getparenttabbedpane"></a>  CBasePane::GetParentTabbedPane  
 Vrátí ukazatel do podokna s kartami nadřazené.  
  
```  
CBaseTabbedPane* GetParentTabbedPane() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na podokno s kartami nadřazené pokud existuje; v opačném případě `NULL`.  
  
##  <a name="getparenttabwnd"></a>  CBasePane::GetParentTabWnd  
 Vrátí ukazatel do nadřazeného okna, který je uvnitř na kartě.  
  
```  
CMFCBaseTabCtrl* GetParentTabWnd(HWND& hWndTab) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out] `hWndTab`  
 Pokud není návratovou hodnotu `NULL`, tento parametr obsahuje popisovač do nadřazeného okna s kartami.  
  
### <a name="return-value"></a>Návratová hodnota  
 Neplatný ukazatel s nadřazeným – záložkami okno nebo `NULL`.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce můžete načíst ukazatel do nadřazeného okna s kartami. Někdy není dostatek volat `GetParent`, protože podokno může být uvnitř ukotvení obálku ( [CDockablePaneAdapter třída](../../mfc/reference/cdockablepaneadapter-class.md)) nebo v podokně adaptér ( [CDockablePaneAdapter třída](../../mfc/reference/cdockablepaneadapter-class.md)). Pomocí `GetParentTabWnd` bude možné načíst platný ukazatel v těchto případech (za předpokladu, že nadřazený je okno s kartami).  
  
##  <a name="getrecentvisiblestate"></a>  CBasePane::GetRecentVisibleState  
 Tato metoda volá framework podokno po obnovení z archivu.  
  
```  
virtual BOOL GetRecentVisibleState() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `BOOL` určující stav poslední viditelné. Pokud `TRUE`, v podokně se v případě viditelné serializovat a by měly jít vidět, když se obnoví. Pokud `FALSE`, v podokně byl skrytý při serializaci a by být skrytý, když se obnoví.  
  
##  <a name="hideinprintpreviewmode"></a>  CBasePane::HideInPrintPreviewMode  
 Určuje, zda je v náhledu tisku skryté v podokně.  
  
```  
virtual BOOL HideInPrintPreviewMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` zda se v podokně se zobrazí v náhledu tisku; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Základní podokna nezobrazují v náhledu tisku. Proto je tato metoda vždy vrátí `TRUE`.  
  
##  <a name="insertpane"></a>  CBasePane::InsertPane  
 Zaregistruje zadané podokně se správce ukotvení.  
  
```  
BOOL InsertPane(
    CBasePane* pControlBar,  
    CBasePane* pTarget,  
    BOOL bAfter = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pControlBar`  
 Ukazatel na podokně Vložit.  
  
 [v] `pTarget`  
 Ukazatel na sousedících podokně.  
  
 [v] `bAfter`  
 Pokud `TRUE`, `pControlBar` vkládají `pTarget`. Pokud `FALSE`, `pControlBar` je vložen před `pTarget`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud metoda bude úspěšná, `FALSE` jinak.  
  
##  <a name="isaccessibilitycompatible"></a>  CBasePane::IsAccessibilityCompatible  
 Určuje, jestli v podokně podporuje Active Accessibility.  
  
```  
virtual BOOL IsAccessibilityCompatible();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud v podokně podporuje Active Accessibility; v opačném `FALSE`.  
  
##  <a name="isautohidemode"></a>  CBasePane::IsAutoHideMode  
 Určuje, zda podokno v režimu automaticky skrýt.  
  
```  
virtual BOOL IsAutoHideMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je v režimu automaticky skrýt podokno v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Základní podokna nelze automaticky skrýt. Tato metoda vždy vrátí hodnotu `FALSE`.  
  
##  <a name="isdialogcontrol"></a>  CBasePane::IsDialogControl  
 Určuje, zda je v podokně ovládací prvek dialogového okna.  
  
```  
BOOL IsDialogControl() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud v podokně je ovládací prvek dialogového okna; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework tato metoda používá k zajištění konzistence rozložení pro všechny podokna.  
  
##  <a name="isdocked"></a>  CBasePane::IsDocked  
 Určuje, zda je ukotvena podokně.  
  
```  
virtual BOOL IsDocked() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud nadřazeného v podokně není zkrácená rámce nebo pokud je v podokně plovoucí zkrácená rámce s jinou podokně; v opačném `FALSE`.  
  
##  <a name="isfloating"></a>  CBasePane::IsFloating  
 Určuje, zda je číslo s plovoucí čárkou podokně.  
  
```  
virtual BOOL IsFloating() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je v podokně plovoucí; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vrátí opačnou hodnotu [CBasePane::IsDocked](#isdocked).  
  
##  <a name="ishorizontal"></a>  CBasePane::IsHorizontal  
 Určuje, zda je v podokně umístěn vodorovně.  
  
```  
virtual BOOL IsHorizontal() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud v podokně ukotven vodorovně; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace zkontroluje aktuální ukotvení zarovnání `CBRS_ORIENT_HORZ`.  
  
##  <a name="isinfloatingmultipaneframewnd"></a>  CBasePane::IsInFloatingMultiPaneFrameWnd  
 Určuje, jestli je v podokně v rámci více podokně okna ( [CMultiPaneFrameWnd třída](../../mfc/reference/cmultipaneframewnd-class.md)).  
  
```  
virtual BOOL IsInFloatingMultiPaneFrameWnd() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud v podokně se v rámci více podokně okna; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 V okně s rámečkem více podokně můžete float pouze lze ukotvit podokna. Proto `CBasePane::IsInFloatingMultiPaneFrameWnd` vždy vrátí hodnotu `FALSE`.  
  
##  <a name="ismditabbed"></a>  CBasePane::IsMDITabbed  
 Určuje, zda v podokně se přidal do okna MDI podřízené jako dokumentů s kartami.  
  
```  
virtual BOOL IsMDITabbed() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud v podokně byl přidán do okna MDI podřízené jako dokument s kartami; v opačném `FALSE`.  
  
##  <a name="ispanevisible"></a>  CBasePane::IsPaneVisible  
 Určuje, zda `WS_VISIBLE` je pro podokně nastaven příznak.  
  
```  
BOOL IsPaneVisible() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud `WS_VISIBLE` je, jinak hodnota `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Použití [CBasePane::IsVisible](#isvisible) určit viditelnost podokně.  
  
##  <a name="ispointneardocksite"></a>  CBasePane::IsPointNearDockSite  
 Určuje, zda zadaný bod je téměř webu ukotvení.  
  
```  
BOOL IsPointNearDockSite(
    CPoint point,  
    DWORD& dwBarAlignment,  
    BOOL& bOuterEdge) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `point`  
 Zadaný bod.  
  
 [out] `dwBarAlignment`  
 Určuje, které hraniční bod je téměř. Možné hodnoty jsou `CBRS_ALIGN_LEFT`, `CBRS_ALIGN_RIGHT`, `CBRS_ALIGN_TOP`, a `CBRS_ALIGN_BOTTOM`  
  
 [out] `bOuterEdge`  
 `TRUE` Pokud je bod téměř vnější ohraničení ukotvení serveru. `FALSE` jinak.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je bod téměř webu ukotvení; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Bod je blízko ukotvení lokality, pokud je v rámci velkých a malých písmen, nastavte v správce ukotvení. Výchozí citlivosti je 15 pixelů.  
  
##  <a name="isresizable"></a>  CBasePane::IsResizable  
 Určuje, zda jde změnit, v podokně.  
  
```  
virtual BOOL IsResizable() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud v podokně můžete změnit uživatelem. v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Podoken programu [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) velikost lze změnit.  
  
 Stavový řádek ( [CMFCStatusBar – třída](../../mfc/reference/cmfcstatusbar-class.md)) a na ukotvení panelu ( [CDockSite třída](../../mfc/reference/cdocksite-class.md)) nelze změnit velikost.  
  
##  <a name="isrestoredfromregistry"></a>  CBasePane::IsRestoredFromRegistry  
 Určuje, zda je v podokně Obnovit z registru.  
  
```  
virtual BOOL IsRestoredFromRegistry() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` v podokně je po obnovení z registru; v opačném `FALSE`.  
  
##  <a name="istabbed"></a>  CBasePane::IsTabbed  
 Určuje, zda byl vložen v podokně ovládacího prvku karta záložkách okna.  
  
```  
virtual BOOL IsTabbed() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je na kartě okno s kartami; vložit ovládacích pruhů v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda načte ukazatel okamžitou nadřazené a určuje, zda nadřazeného runtime třídy [CMFCBaseTabCtrl třída](../../mfc/reference/cmfcbasetabctrl-class.md).  
  
##  <a name="isvisible"></a>  CBasePane::IsVisible  
 Určuje, zda je zobrazen v podokně.  
  
```  
virtual BOOL IsVisible() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je viditelné; podokno v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k určení, zda se podokno. Nepoužívejte `::IsWindowVisible`.  
  
 Pokud není v podokně – se záložkami (najdete v části [CBasePane::IsTabbed](#istabbed)), tato metoda zkontroluje `WS_VISIBLE` stylu. Pokud je v podokně – se záložkami, tato metoda ověří viditelnost nadřazeného okna s kartami. Pokud nadřazeného okna je viditelná, funkce ověří, zda podokně karty pomocí [CMFCBaseTabCtrl::IsTabVisible](../../mfc/reference/cmfcbasetabctrl-class.md#istabvisible).  
  
##  <a name="loadstate"></a>  CBasePane::LoadState  
 V podokně Stav načte z registru.  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName=NULL,  
    int nIndex=-1,  
    UINT uiID=(UINT)-1);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpszProfileName`  
 Název profilu.  
  
 [v] `nIndex`  
 Profil index.  
  
 [v] `uiID`  
 ID podokně.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud podokno stavu byl načten úspěšně; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework volá tuto metodu za účelem načtení stavu podokně z registru. Přepsání v odvozené třídě načíst další informace o ukládaná [CBasePane::SaveState](#savestate).  
  
##  <a name="movewindow"></a>  CBasePane::MoveWindow  
 Přesune podokně.  
  
```  
virtual HDWP MoveWindow(
    CRect& rect,  
    BOOL bRepaint = TRUE,  
    HDWP hdwp = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `rect`  
 Obdélník nové umístění a velikost podokna.  
  
 [v] `bRepaint`  
 Pokud `TRUE`, lze překreslit podokně. Pokud `FALSE`, nelze překreslit podokně.  
  
 [v] `hdwp`  
 Popisovač strukturu pozice odložené okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro strukturu pozice odložené okna, nebo `NULL`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud předáte `NULL` jako `hdwp` parametr, tato metoda Přesune okno normálně. Pokud předáte popisovač, tato metoda provádí přesunu odložené okno. Můžete získat popisovač voláním [BeginDeferWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms632672) nebo ukládání návratovou hodnotu z předchozího volání této metody.  
  
##  <a name="onafterchangeparent"></a>  CBasePane::OnAfterChangeParent  
 Voláno rámcem po provedení změn v podokně nadřazené.  
  
```  
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pWndOldParent`  
 Ukazatel na předchozí nadřazené.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá framework po v podokně nadřazené změn, obvykle kvůli ukotvení nebo plovoucí operaci.  
  
 Výchozí implementace neprovede žádnou akci.  
  
##  <a name="onbeforechangeparent"></a>  CBasePane::OnBeforeChangeParent  
 Voláno rámcem těsně před podokně změní jeho nadřazeného okna.  
  
```  
virtual void OnBeforeChangeParent(
    CWnd* pWndNewParent,  
    BOOL bDelay=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pWndNewParent`  
 Ukazatel do nového nadřazeného okna.  
  
 [v] `bDelay`  
 Určuje, zda úpravy rozložení musí být zpožděna.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework volá tuto metodu těsně před v podokně nadřazené změny, obvykle kvůli ukotvení, číslo s plovoucí čárkou nebo automaticky skrýt operace.  
  
 Výchozí implementace neprovede žádnou akci.  
  
##  <a name="ondrawcaption"></a>  CBasePane::OnDrawCaption  
 Tato metoda volá framework při sestavování titulek.  
  
```  
virtual void OnDrawCaption();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda nemá používat žádné funkce pro `CBasePane` třídy.  
  
##  <a name="onmovepanedivider"></a>  CBasePane::OnMovePaneDivider  
 Tato metoda není aktuálně používá.  
  
```  
virtual void OnMovePaneDivider(CPaneDivider*);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `CPaneDivider*`  
 Nepoužívá se.  
  
##  <a name="onpanecontextmenu"></a>  CBasePane::OnPaneContextMenu  
 Voláno rámcem při vytváření nabídky, která má seznam podokna.  
  
```  
virtual void OnPaneContextMenu(
    CWnd* pParentFrame,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pParentFrame`  
 Ukazatel na rámec nadřazené.  
  
 [v] `point`  
 Určuje umístění v místní nabídce.  
  
### <a name="remarks"></a>Poznámky  
 `OnPaneContextMenu` volá ukotvení správce, který udržuje seznam podokna, které patří do aktuální rámce okna. Tato metoda názvy podoken přidá do místní nabídky a zobrazí. Příkazy v nabídce Zobrazit nebo skrýt jednotlivé podokna.  
  
 Potlačí tuto metodu za účelem přizpůsobení toto chování.  
  
##  <a name="onremovefromminiframe"></a>  CBasePane::OnRemoveFromMiniFrame  
 Voláno rámcem Pokud podokno je odebrán z jeho nadřazeného mini rámce okna.  
  
```  
virtual void OnRemoveFromMiniFrame(CPaneFrameWnd* pMiniFrame);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pMiniFrame`  
 Ukazatel na zkrácená rámce okna, ze kterého je odebrán v podokně.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá framework Pokud podokno je odebrán z jeho nadřazeného zkrácená rámce okna (v důsledku například ukotvení,).  
  
 Výchozí implementace neprovede žádnou akci.  
  
##  <a name="onsetaccdata"></a>  CBasePane::OnSetAccData  
 `CBasePane` Tato metoda nepoužívá.  
  
```  
virtual BOOL OnSetAccData(long lVal);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lVal`  
 Nepoužívá se.  
  
### <a name="return-value"></a>Návratová hodnota  
 Tato metoda vždy vrátí hodnotu `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="panefrompoint"></a>  CBasePane::PaneFromPoint  
 Vrátí panel, který obsahuje danému bodu.  
  
```  
CBasePane* PaneFromPoint(
    CPoint point,  
    int nSensitivity,  
    bool bExactBar = false,  
    CRuntimeClass* pRTCBarType = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `point`  
 Určuje bod, v souřadnice obrazovky ke kontrole.  
  
 [v] `nSensitivity`  
 Toto množství zvýšit oblasti hledání. Podokno budou splňovat kritéria hledání, pokud danému bodu spadá do oblasti vyšší.  
  
 [v] `bExactBar`  
 `TRUE` Ignorovat `nSensitivity` parametr, jinak hodnota `FALSE`.  
  
 [v] `pRTCBarType`  
 Není-li `NULL`, tato metoda vyhledá pouze podokna zadaného typu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `CBasePane`-Odvozené objekt, který obsahuje danému bodu nebo `NULL` Pokud nebyl nalezen žádný podokně.  
  
##  <a name="recalclayout"></a>  CBasePane::RecalcLayout  
 `CBasePane` Tato metoda nepoužívá.  
  
```  
virtual void RecalcLayout();
```  
  
##  <a name="removepanefromdockmanager"></a>  CBasePane::RemovePaneFromDockManager  
 Zruší registraci podokno a odstraní ji ze seznamu ve Správci ukotvení.  
  
```  
void RemovePaneFromDockManager(
    CBasePane* pBar,  
    BOOL bDestroy = TRUE,  
    BOOL bAdjustLayout = FALSE,  
    BOOL bAutoHide = FALSE,  
    CBasePane* pBarReplacement = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pBar`  
 Ukazatel na podokně odeberou.  
  
 [v] `bDestroy`  
 Pokud `TRUE`, odebrané podokně zničena.  
  
 [v] `bAdjustLayout`  
 Pokud `TRUE`, upravte ukotvení rozložení okamžitě.  
  
 [v] `bAutoHide`  
 Pokud `TRUE`, ukotvení rozložení se vztahuje k seznamu autohide – řádky. Pokud `FALSE`, ukotvení rozložení se vztahuje k seznamu regulární podokna.  
  
 [v] `pBarReplacement`  
 Ukazatel na podokně, který nahrazuje podokně odebrané.  
  
##  <a name="savestate"></a>  CBasePane::SaveState  
 V podokně Stav uloží do registru.  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName=NULL,  
    int nIndex=-1,  
    UINT uiID=(UINT)-1);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpszProfileName`  
 Název profilu.  
  
 [v] `nIndex`  
 Profil index.  
  
 [v] `uiID`  
 ID podokně.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud byl úspěšně; uložen stav v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework volá tuto metodu, když ho uloží stav v podokně do registru. Přepsání `SaveState` v odvozené třídě pro uložení dalších informací.  
  
##  <a name="selectdefaultfont"></a>  CBasePane::SelectDefaultFont  
 Vybere písmo výchozího kontextu daného zařízení.  
  
```  
CFont* SelectDefaultFont(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDC`  
 Kontext zařízení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na výchozí [CFont – třída](../../mfc/reference/cfont-class.md) objektu.  
  
##  <a name="setcontrolbarstyle"></a>  CBasePane::SetControlBarStyle  
 Nastaví styl panelu ovládacího prvku.  
  
```  
virtual void SetControlBarStyle(DWORD dwNewStyle);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `dwNewStyle`  
 Bitový operátor OR kombinace následujících hodnot.  
  
|Styl|Popis|  
|-----------|-----------------|  
|`AFX_CBRS_FLOAT`|Díky float panel ovládacího prvku.|  
|`AFX_CBRS_AUTOHIDE`|Umožňuje automaticky skrýt režimu.|  
|`AFX_CBRS_RESIZE`|Umožňuje změnu velikosti panelu ovládacího prvku. Pokud je tento příznak nastaven, ovládacích pruhů můžete umístit do lze ukotvit podokně.|  
|`AFX_CBRS_CLOSE`|Umožňuje skrytí panelu ovládacího prvku.|  
  
##  <a name="setdockingmode"></a>  CBasePane::SetDockingMode  
 Nastaví ukotvení režim pro podokně.  
  
```  
void SetDockingMode(AFX_DOCK_TYPE dockModeNew);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `dockModeNew`  
 Určuje nové ukotvení režim pro podokně.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework podporuje dva režimy ukotvení: standard a okamžitě.  
  
 Ve standardním režimu ukotvení podokna a okna s rámečkem zkrácená se přesunou kolem pomocí přetahování obdélníku. V okamžitou ukotvení režimu ovládací pruhy a okna s rámečkem zkrácená se přesunou okamžitě s jejich kontextu.  
  
 Na začátku ukotvení režimu je definována globálně pomocí [CDockingManager::m_dockModeGlobal](../../mfc/reference/cdockingmanager-class.md#m_dockmodeglobal). Můžete nastavit ukotvení režim pro každý podokně jednotlivě pomocí `SetDockingMode` metoda.  
  
##  <a name="setpanealignment"></a>  CBasePane::SetPaneAlignment  
 Nastaví zarovnání v podokně.  
  
```  
virtual void SetPaneAlignment(DWORD dwAlignment);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `dwAlignment`  
 Určuje zarovnání nové.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework obvykle volá tuto metodu, když podokno ukotven z jedné strany hlavního rámce do jiného.  
  
 V následující tabulce jsou uvedeny možné hodnoty pro `dwAlignment`:  
  
|Hodnota|Zarovnání|  
|-----------|---------------|  
|`CBRS_ALIGN_LEFT`|Zarovnání doleva.|  
|`CBRS_ALIGN_RIGHT`|Zarovnání doprava.|  
|`CBRS_ALIGN_TOP`|Zarovnání nahoru.|  
|`CBRS_ALIGN_BOTTOM`|Zarovnání dolů.|  
  
##  <a name="setpanestyle"></a>  CBasePane::SetPaneStyle  
 Nastavuje styl podokna.  
  
```  
virtual void SetPaneStyle(DWORD dwNewStyle);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `dwNewStyle`  
 Určuje styl nové nastavení.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda slouží k nastavení libovolný CBRS_ styl, které jsou definovány v afxres.h. Styl podokně a podokně zarovnání jsou uloženy společně, že ho propojíte s aktuální zarovnání následujícím způsobem nastavte nový styl.  
  
 `pPane->SetPaneStyle (pPane->GetCurrentAlignment() | CBRS_TOOLTIPS);`  
  
##  <a name="setwindowpos"></a>  CBasePane::SetWindowPos  
 Změní velikost, umístění a pořadí Z-order podokna.  
  
```  
virtual HDWP SetWindowPos(
    const CWnd* pWndInsertAfter,  
    int x,  
    int y,  
    int cx,  
    int cy,  
    UINT nFlags,  
    HDWP hdwp = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pWndInsertAfter`  
 Identifikuje `CWnd` objekt, který jste dostali se předtím, než `CWnd` objekt v pořadí. Další informace najdete v tématu [CWnd::SetWindowPos](../../mfc/reference/cwnd-class.md#setwindowpos).  
  
 [v] `x`  
 Určuje pozici na levé straně okna.  
  
 [v] `y`  
 Určuje pozici horní části okna.  
  
 [v] `cx`  
 Určuje šířku okna.  
  
 [v] `cy`  
 Určuje výšku okna.  
  
 [v] `nFlags`  
 Určuje možnosti, velikost a umístění. Další informace najdete v tématu [CWnd::SetWindowPos](../../mfc/reference/cwnd-class.md#setwindowpos).  
  
 [v] `hdwp`  
 Popisovač strukturu, která obsahuje informace o velikosti a pozice pro jeden nebo více windows.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro strukturu pozice aktualizované odložené okno nebo `NULL`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `pWndInsertAfter` je `NULL`, tato metoda volá [CWnd::SetWindowPos](../../mfc/reference/cwnd-class.md#setwindowpos). Pokud `pWndInsertAfter` jinou hodnotu než `NULL`, tato metoda volá `DeferWindowPos`.  
  
##  <a name="showpane"></a>  CBasePane::ShowPane  
 Zobrazí či skryje panel.  
  
```  
virtual void ShowPane(
    BOOL bShow,  
    BOOL bDelay,  
    BOOL bActivate);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bShow`  
 Určuje, zda chcete zobrazit ( `TRUE`) nebo skrýt ( `FALSE`) podokno.  
  
 [v] `bDelay`  
 Pokud `TRUE`, přepočítání ukotvení rozložení je zpožděno.  
  
 [v] `bActivate`  
 Pokud `TRUE`, je aktivní, pokud se zobrazí v podokně.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda zobrazí nebo skryje podokno. Použít tuto metodu místo `ShowWindow` vzhledem k tomu, že tato metoda upozorní relevantní ukotvení správci o změnách v viditelnost v podokně.  
  
 Použití [CBasePane::IsVisible](#isvisible) k určení aktuální viditelnost podokno.  
  
##  <a name="stretchpane"></a>  CBasePane::StretchPane  
 Podokno roztahovány vodorovně nebo svisle.  
  
```  
virtual CSize StretchPane(
    int nLength,  
    BOOL bVert);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nLength`  
 Délka, podle kterého k roztahování v podokně.  
  
 [v] `bVert`  
 Pokud `TRUE`, funkce stretch podokně svisle. Pokud `FALSE`, vodorovně roztažení v podokně.  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost roztažené podokně.  
  
##  <a name="undockpane"></a>  CBasePane::UndockPane  
 V podokně se odebere z webu ukotvení, výchozí posuvníku nebo zkrácená rámec okna, kde je aktuálně ukotven.  
  
```  
virtual void UndockPane(BOOL bDelay=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `bDelay`  
 V případě hodnoty TRUE ukotvení rozložení není přepočítat okamžitě.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu za účelem zpracování stavu podokně nebo vyloučit z dokovací rozložení v podokně.  
  
 Pokud chcete nadále používat v tomto podokně, zavolejte buď [CBasePane::DockPane](#dockpane) nebo [CBasePane::FloatPane](#floatpane) před voláním této metody.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CPane](../../mfc/reference/cbasepane-class.md)   
 [CWnd – třída](../../mfc/reference/cwnd-class.md)
