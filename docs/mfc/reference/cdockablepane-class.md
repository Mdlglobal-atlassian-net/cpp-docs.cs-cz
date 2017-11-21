---
title: "Třída CDockablePane | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDockablePane
- AFXDOCKABLEPANE/CDockablePane
- AFXDOCKABLEPANE/CDockablePane::CDockablePane
- AFXDOCKABLEPANE/CDockablePane::AttachToTabWnd
- AFXDOCKABLEPANE/CDockablePane::CalcFixedLayout
- AFXDOCKABLEPANE/CDockablePane::CanAcceptMiniFrame
- AFXDOCKABLEPANE/CDockablePane::CanAcceptPane
- AFXDOCKABLEPANE/CDockablePane::CanAutoHide
- AFXDOCKABLEPANE/CDockablePane::CanBeAttached
- AFXDOCKABLEPANE/CDockablePane::ConvertToTabbedDocument
- AFXDOCKABLEPANE/CDockablePane::CopyState
- AFXDOCKABLEPANE/CDockablePane::Create
- AFXDOCKABLEPANE/CDockablePane::CreateDefaultPaneDivider
- AFXDOCKABLEPANE/CDockablePane::CreateEx
- AFXDOCKABLEPANE/CDockablePane::CreateTabbedPane
- AFXDOCKABLEPANE/CDockablePane::DockPaneContainer
- AFXDOCKABLEPANE/CDockablePane::DockPaneStandard
- AFXDOCKABLEPANE/CDockablePane::DockToRecentPos
- AFXDOCKABLEPANE/CDockablePane::DockToWindow
- AFXDOCKABLEPANE/CDockablePane::EnableAutohideAll
- AFXDOCKABLEPANE/CDockablePane::EnableGripper
- AFXDOCKABLEPANE/CDockablePane::GetAHRestoredRect
- AFXDOCKABLEPANE/CDockablePane::GetAHSlideMode
- AFXDOCKABLEPANE/CDockablePane::GetCaptionHeight
- AFXDOCKABLEPANE/CDockablePane::GetDefaultPaneDivider
- AFXDOCKABLEPANE/CDockablePane::GetDockingStatus
- AFXDOCKABLEPANE/CDockablePane::GetDragSensitivity
- AFXDOCKABLEPANE/CDockablePane::GetLastPercentInPaneContainer
- AFXDOCKABLEPANE/CDockablePane::GetTabArea
- AFXDOCKABLEPANE/CDockablePane::GetTabbedPaneRTC
- AFXDOCKABLEPANE/CDockablePane::HasAutoHideMode
- AFXDOCKABLEPANE/CDockablePane::HitTest
- AFXDOCKABLEPANE/CDockablePane::IsAutohideAllEnabled
- AFXDOCKABLEPANE/CDockablePane::IsAutoHideMode
- AFXDOCKABLEPANE/CDockablePane::IsDocked
- AFXDOCKABLEPANE/CDockablePane::IsHideInAutoHideMode
- AFXDOCKABLEPANE/CDockablePane::IsInFloatingMultiPaneFrameWnd
- AFXDOCKABLEPANE/CDockablePane::IsResizable
- AFXDOCKABLEPANE/CDockablePane::IsTabLocationBottom
- AFXDOCKABLEPANE/CDockablePane::IsTracked
- AFXDOCKABLEPANE/CDockablePane::IsVisible
- AFXDOCKABLEPANE/CDockablePane::OnAfterChangeParent
- AFXDOCKABLEPANE/CDockablePane::OnAfterDockFromMiniFrame
- AFXDOCKABLEPANE/CDockablePane::OnBeforeChangeParent
- AFXDOCKABLEPANE/CDockablePane::OnBeforeFloat
- AFXDOCKABLEPANE/CDockablePane::RemoveFromDefaultPaneDividier
- AFXDOCKABLEPANE/CDockablePane::ReplacePane
- AFXDOCKABLEPANE/CDockablePane::RestoreDefaultPaneDivider
- AFXDOCKABLEPANE/CDockablePane::SetAutoHideMode
- AFXDOCKABLEPANE/CDockablePane::SetAutoHideParents
- AFXDOCKABLEPANE/CDockablePane::SetLastPercentInPaneContainer
- AFXDOCKABLEPANE/CDockablePane::SetRestoredDefaultPaneDivider
- AFXDOCKABLEPANE/CDockablePane::SetTabbedPaneRTC
- AFXDOCKABLEPANE/CDockablePane::ShowPane
- AFXDOCKABLEPANE/CDockablePane::Slide
- AFXDOCKABLEPANE/CDockablePane::ToggleAutoHide
- AFXDOCKABLEPANE/CDockablePane::UndockPane
- AFXDOCKABLEPANE/CDockablePane::CheckAutoHideCondition
- AFXDOCKABLEPANE/CDockablePane::CheckStopSlideCondition
- AFXDOCKABLEPANE/CDockablePane::DrawCaption
- AFXDOCKABLEPANE/CDockablePane::OnPressButtons
- AFXDOCKABLEPANE/CDockablePane::OnSlide
- AFXDOCKABLEPANE/CDockablePane::m_bDisableAnimation
- AFXDOCKABLEPANE/CDockablePane::m_bHideInAutoHideMode
- AFXDOCKABLEPANE/CDockablePane::m_nSlideSteps
dev_langs: C++
helpviewer_keywords:
- CDockablePane [MFC], CDockablePane
- CDockablePane [MFC], AttachToTabWnd
- CDockablePane [MFC], CalcFixedLayout
- CDockablePane [MFC], CanAcceptMiniFrame
- CDockablePane [MFC], CanAcceptPane
- CDockablePane [MFC], CanAutoHide
- CDockablePane [MFC], CanBeAttached
- CDockablePane [MFC], ConvertToTabbedDocument
- CDockablePane [MFC], CopyState
- CDockablePane [MFC], Create
- CDockablePane [MFC], CreateDefaultPaneDivider
- CDockablePane [MFC], CreateEx
- CDockablePane [MFC], CreateTabbedPane
- CDockablePane [MFC], DockPaneContainer
- CDockablePane [MFC], DockPaneStandard
- CDockablePane [MFC], DockToRecentPos
- CDockablePane [MFC], DockToWindow
- CDockablePane [MFC], EnableAutohideAll
- CDockablePane [MFC], EnableGripper
- CDockablePane [MFC], GetAHRestoredRect
- CDockablePane [MFC], GetAHSlideMode
- CDockablePane [MFC], GetCaptionHeight
- CDockablePane [MFC], GetDefaultPaneDivider
- CDockablePane [MFC], GetDockingStatus
- CDockablePane [MFC], GetDragSensitivity
- CDockablePane [MFC], GetLastPercentInPaneContainer
- CDockablePane [MFC], GetTabArea
- CDockablePane [MFC], GetTabbedPaneRTC
- CDockablePane [MFC], HasAutoHideMode
- CDockablePane [MFC], HitTest
- CDockablePane [MFC], IsAutohideAllEnabled
- CDockablePane [MFC], IsAutoHideMode
- CDockablePane [MFC], IsDocked
- CDockablePane [MFC], IsHideInAutoHideMode
- CDockablePane [MFC], IsInFloatingMultiPaneFrameWnd
- CDockablePane [MFC], IsResizable
- CDockablePane [MFC], IsTabLocationBottom
- CDockablePane [MFC], IsTracked
- CDockablePane [MFC], IsVisible
- CDockablePane [MFC], OnAfterChangeParent
- CDockablePane [MFC], OnAfterDockFromMiniFrame
- CDockablePane [MFC], OnBeforeChangeParent
- CDockablePane [MFC], OnBeforeFloat
- CDockablePane [MFC], RemoveFromDefaultPaneDividier
- CDockablePane [MFC], ReplacePane
- CDockablePane [MFC], RestoreDefaultPaneDivider
- CDockablePane [MFC], SetAutoHideMode
- CDockablePane [MFC], SetAutoHideParents
- CDockablePane [MFC], SetLastPercentInPaneContainer
- CDockablePane [MFC], SetRestoredDefaultPaneDivider
- CDockablePane [MFC], SetTabbedPaneRTC
- CDockablePane [MFC], ShowPane
- CDockablePane [MFC], Slide
- CDockablePane [MFC], ToggleAutoHide
- CDockablePane [MFC], UndockPane
- CDockablePane [MFC], CheckAutoHideCondition
- CDockablePane [MFC], CheckStopSlideCondition
- CDockablePane [MFC], DrawCaption
- CDockablePane [MFC], OnPressButtons
- CDockablePane [MFC], OnSlide
- CDockablePane [MFC], m_bDisableAnimation
- CDockablePane [MFC], m_bHideInAutoHideMode
- CDockablePane [MFC], m_nSlideSteps
ms.assetid: e2495f4c-765f-48f9-a2e2-e45e47608d91
caps.latest.revision: "34"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3072e4504fc70e75888607d4f263b39532f69b51
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cdockablepane-class"></a>CDockablePane – třída
Implementuje podokně, která se dá buď ukotven v lokalitě ukotvení nebo zahrnuté v záložkách podokně.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDockablePane : public CPane  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CDockablePane::CDockablePane](#cdockablepane)|Vytvoří a inicializuje `CDockablePane` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDockablePane::AttachToTabWnd](#attachtotabwnd)|Podokno se připojí k jiné podokně. Tím se vytvoří podokno s kartami.|  
|[CDockablePane::CalcFixedLayout](#calcfixedlayout)|Vrátí velikost obdélníku podokně.|  
|[CDockablePane::CanAcceptMiniFrame](#canacceptminiframe)|Určuje, zda lze ukotvit zadaného mini rámce do podokna.|  
|[CDockablePane::CanAcceptPane](#canacceptpane)|Určuje, zda lze do podokna aktuální ukotvit jiného podokna.|  
|[CDockablePane::CanAutoHide](#canautohide)|Určuje, zda v podokně podporuje režim automaticky skrýt. (Přepisuje [CBasePane::CanAutoHide](../../mfc/reference/cbasepane-class.md#canautohide).)|  
|[CDockablePane::CanBeAttached](#canbeattached)|Určuje, zda aktuální podokně lze ukotvit do jiného podokna.|  
|[CDockablePane::ConvertToTabbedDocument](#converttotabbeddocument)|Jeden nebo více lze ukotvit podokna převede do dokumentů s kartami MDI.|  
|[CDockablePane::CopyState](#copystate)|Zkopíruje stav lze ukotvit podokně.|  
|[CDockablePane::Create](#create)|Vytvoří ovládacího prvku Windows a připojí jej k `CDockablePane` objektu.|  
|[CDockablePane::CreateDefaultPaneDivider](#createdefaultpanedivider)|Vytvoří výchozí oddělovač pro podokně jako ukotvena okně s rámečkem.|  
|[CDockablePane::CreateEx](#createex)|Vytvoří ovládacího prvku Windows a připojí jej k `CDockablePane` objektu.|  
|[CDockablePane::CreateTabbedPane](#createtabbedpane)|Vytvoří záložkách podokno z podokna aktuální.|  
|[CDockablePane::DockPaneContainer](#dockpanecontainer)|Kontejner ukotvené do podokna.|  
|[CDockablePane::DockPaneStandard](#dockpanestandard)|Podokno ukotvené pomocí outline (standardní) ukotvení.|  
|`CDockablePane::DockToFrameWindow`|Interně. Chcete-li ukotvit podokno, použijte [CPane::DockPane](../../mfc/reference/cpane-class.md#dockpane) nebo [CDockablePane::DockToWindow](#docktowindow).|  
|[CDockablePane::DockToRecentPos](#docktorecentpos)|Ukotvené podokno k jeho uložené poslední pozici ukotvení.|  
|[CDockablePane::DockToWindow](#docktowindow)|Ukotvené jeden ukotvení podokně do jiného ukotvení panelu.|  
|[CDockablePane::EnableAutohideAll](#enableautohideall)|Povolí nebo zakáže automatické skrytí režim pro toto podokno společně s další podokna v kontejneru.|  
|[CDockablePane::EnableGripper](#enablegripper)|Zobrazí nebo skryje titulek (úchytu).|  
|[CDockablePane::GetAHRestoredRect](#getahrestoredrect)|Určuje pozici v podokně, když je viditelná v režimu automaticky skrýt.|  
|[CDockablePane::GetAHSlideMode](#getahslidemode)|Načte režim automatického skrýt snímku pro podokně.|  
|`CDockablePane::GetAutoHideButton`|Interně.|  
|`CDockablePane::GetAutoHideToolBar`|Interně.|  
|[CDockablePane::GetCaptionHeight](#getcaptionheight)|Vrátí výšku titulek aktuální.|  
|[CDockablePane::GetDefaultPaneDivider](#getdefaultpanedivider)|Vrátí dělicí podokně výchozí pro kontejner v podokně.|  
|[CDockablePane::GetDockingStatus](#getdockingstatus)|Určuje, že podokno schopnost ukotvit v závislosti na umístění zadaná ukazatele.|  
|[CDockablePane::GetDragSensitivity](#getdragsensitivity)|Vrátí velkých a malých písmen přetáhněte ukotvení panelu.|  
|[CDockablePane::GetLastPercentInPaneContainer](#getlastpercentinpanecontainer)|Načítá procentní podíl místa, které zabírá podokno v rámci příslušného kontejneru.|  
|[CDockablePane::GetTabArea](#gettabarea)|Načte oblast karty pro podokně.|  
|[CDockablePane::GetTabbedPaneRTC](#gettabbedpanertc)|Vrací runtime třídy informace o okno s kartami, která se vytvoří při další podokno ukotvené do podokna aktuální.|  
|[CDockablePane::HasAutoHideMode](#hasautohidemode)|Určuje, zda lze ukotvení podokně přepnout do režimu automaticky skrýt.|  
|[CDockablePane::HitTest](#hittest)|Určuje konkrétní umístění v podokně, kde uživatel klikne na tlačítko myši.|  
|`CDockablePane::IsAccessibilityCompatible`|Interně.|  
|[CDockablePane::IsAutohideAllEnabled](#isautohideallenabled)|Určuje, zda ukotvení panelu a všechny ostatní podokna v kontejneru mohou být umístěny v režimu automaticky skrýt.|  
|[CDockablePane::IsAutoHideMode](#isautohidemode)|Určuje, zda podokno v režimu automaticky skrýt.|  
|`CDockablePane::IsChangeState`|Interně.|  
|[CDockablePane::IsDocked](#isdocked)|Určuje, zda je ukotvena podokně aktuální.|  
|[CDockablePane::IsHideInAutoHideMode](#ishideinautohidemode)|Určuje chování panelu, který je v režimu automaticky skrýt, je-li vidět (nebo skrytý) voláním `ShowPane`.|  
|[CDockablePane::IsInFloatingMultiPaneFrameWnd](#isinfloatingmultipaneframewnd)|Určuje, zda v podokně v rámci více podokně okna.|  
|[CDockablePane::IsResizable](#isresizable)|Určuje, zda je v podokně s možností změny velikosti.|  
|[CDockablePane::IsTabLocationBottom](#istablocationbottom)|Určuje, zda jsou umístěny v horní nebo dolní části podokna karty.|  
|[CDockablePane::IsTracked](#istracked)|Určuje, zda je podokno přetažen uživatelem.|  
|[CDockablePane::IsVisible](#isvisible)|Určuje, zda se zobrazuje aktuální podokno.|  
|[CDockablePane::LoadState](http://msdn.microsoft.com/en-us/96110136-4f46-4764-8a76-3b4abaf77917)|Interně.|  
|[CDockablePane::OnAfterChangeParent](#onafterchangeparent)|Voláno rámcem, pokud došlo ke změně nadřazeného podokno. (Přepisuje [CPane::OnAfterChangeParent](../../mfc/reference/cpane-class.md#onafterchangeparent).)|  
|[CDockablePane::OnAfterDockFromMiniFrame](#onafterdockfromminiframe)|Voláno rámcem při plovoucí ukotvení panelu ukotvené v okně s rámečkem.|  
|[CDockablePane::OnBeforeChangeParent](#onbeforechangeparent)|Voláno rámcem po nadřazeného podokně Chystáte se změnit. (Přepisuje [CPane::OnBeforeChangeParent](../../mfc/reference/cpane-class.md#onbeforechangeparent).)|  
|[CDockablePane::OnBeforeFloat](#onbeforefloat)|Voláno rámcem při podokno je o float. (Přepisuje [CPane::OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat).)|  
|[CDockablePane::RemoveFromDefaultPaneDividier](#removefromdefaultpanedividier)|Rozhraní framework volá tuto metodu, když je právě nepřipojený podokno.|  
|[CDockablePane::ReplacePane](#replacepane)|V podokně nahradí zadaný podokně.|  
|[CDockablePane::RestoreDefaultPaneDivider](#restoredefaultpanedivider)|Rozhraní framework volá tuto metodu, jako je podokno deserializovat obnovit dělicí podokně výchozí.|  
|`CDockablePane::SaveState`|Interně.|  
|`CDockablePane::Serialize`|Serializuje podokně. (Přepisuje `CBasePane::Serialize`.)|  
|[CDockablePane::SetAutoHideMode](#setautohidemode)|Přepíná podokně ukotvení mezi viditelné a automaticky skrýt režim.|  
|[CDockablePane::SetAutoHideParents](#setautohideparents)|Nastaví automaticky skrýt tlačítko a automatické skrytí panelu nástrojů pro podokně.|  
|`CDockablePane::SetDefaultPaneDivider`|Interně.|  
|[CDockablePane::SetLastPercentInPaneContainer](#setlastpercentinpanecontainer)|Nastaví v procentech místa, které zabírá podokno v rámci příslušného kontejneru.|  
|`CDockablePane::SetResizeMode`|Interně.|  
|[CDockablePane::SetRestoredDefaultPaneDivider](#setrestoreddefaultpanedivider)|Nastaví dělicí podokně obnovené výchozí.|  
|[CDockablePane::SetTabbedPaneRTC](#settabbedpanertc)|Nastaví informace o třídě modulu runtime pro okno s kartami, která se vytvoří při dvě podokna ukotvení společně.|  
|[CDockablePane::ShowPane](#showpane)|Zobrazit nebo skrýt podokno.|  
|[CDockablePane::Slide](#slide)|Zobrazí či skryje panel se posuvné animace, která zobrazuje jenom v případě, že je v režimu automaticky skrýt podokno.|  
|[CDockablePane::ToggleAutoHide](#toggleautohide)|Přepíná režim automaticky skrýt. (Přepisuje [CPane::ToggleAutoHide](../../mfc/reference/cpane-class.md#toggleautohide) .)|  
|[CDockablePane::UndockPane](#undockpane)|Předchozího podokna z hlavního okna rámce nebo kontejner miniframe okno.|  
|`CDockablePane::UnSetAutoHideMode`|Interně. Pokud chcete nastavit režim automaticky skrýt, použijte [CDockablePane::SetAutoHideMode](#setautohidemode)|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDockablePane::CheckAutoHideCondition](#checkautohidecondition)|Určuje, zda podokně ukotvení skryt (v režimu automaticky skrýt).|  
|[CDockablePane::CheckStopSlideCondition](#checkstopslidecondition)|Určuje, kdy ukotvení podokně aplikace automaticky skrýt by se měla zastavit klouzavé.|  
|[CDockablePane::DrawCaption](#drawcaption)|Nakreslí titulek ukotvení podokně (úchytu).|  
|[CDockablePane::OnPressButtons](#onpressbuttons)|Volá se, když uživatel stiskne tlačítko titulek jiné než `AFX_HTCLOSE` a `AFX_HTMAXBUTTON` tlačítka.|  
|[CDockablePane::OnSlide](#onslide)|Voláno rámcem k vykreslení efekt snímky automaticky skrýt, když se v podokně zobrazí nebo skrytý.|  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CDockablePane::m_bDisableAnimation](#m_bdisableanimation)|Určuje, zda je animace automatické skrytí podokna lze ukotvit zakázána.|  
|[CDockablePane::m_bHideInAutoHideMode](#m_bhideinautohidemode)|Určuje chování v podokně, když je v režimu automaticky skrýt podokno.|  
|[CDockablePane::m_nSlideSteps](#m_nslidesteps)|Určuje rychlost animace podokna při jeho zobrazen nebo skryt v režimu automaticky skrýt.|  
  
## <a name="remarks"></a>Poznámky  
 `CDockablePane`implementuje následující funkce:  
  
-   Ukotvení podokno do hlavního rámce okna.  
  
-   Přepnutí do režimu automaticky skrýt podokno.  
  
-   Podokno se připojuje k okno s kartami.  
  
-   Plovoucí podokno v okně miniframe.  
  
-   Ukotvení podokno do jiného podokna, který je v okně miniframe s plovoucí čárkou.  
  
-   Změna velikosti podokno.  
  
-   Načítání a ukládání stavu pro ukotvení podokně.  
  
    > [!NOTE]
    >  Stavové informace se uloží do registru systému Windows.  
  
-   Vytváření podokno s nebo bez popisek. Popisek může mít textový popisek a může být vyplněn barva barevného přechodu.  
  
-   Při zobrazení obsahu v podokně přetahování podokno  
  
-   Při zobrazování obdélníku přetažení přetahování podokno.  
  
 V aplikaci použít ukotvené podokno, odvozena třídě podokně z `CDockablePane` třídy. Odvozené objekt buď vložit do objektu hlavního rámce okna nebo do okna objekt, který řídí instanci do podokna. Potom zavolejte [CDockablePane::Create](#create) metoda nebo [CDockablePane::CreateEx](#createex) v případě, že při zpracování `WM_CREATE` zprávy v hlavním okně rámce. Nakonec nastavte objekt podokně voláním [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking), [CBasePane::DockPane](../../mfc/reference/cbasepane-class.md#dockpane), nebo [CDockablePane::AttachToTabWnd](#attachtotabwnd).  
  
## <a name="customization-tips"></a>Tipy k přizpůsobení  
 Následující tipy, na které se týkají `CDockablePane` objekty:  
  
-   Když zavoláte [CDockablePane::AttachToTabWnd](#attachtotabwnd) pro dvě podokna s kartami, lze ukotvit ukazatel na okno s kartami, vrátí se `ppTabbedControlBar` parametr. Přidání karet do okna s kartami pomocí tohoto parametru můžete dál.  
  
-   Druh podokno s kartami, který byl vytvořený [CDockablePane::AttachToTabWnd](#attachtotabwnd) je dáno `CDockablePane` objekt v `pTabControlBarAttachTo` parametr. Můžete volat [CDockablePane::SetTabbedPaneRTC](#settabbedpanertc) k nastavení druh podokno s kartami, který `CDockablePane` vytvoří. Výchozí typ je dáno `dwTabbedStyle` z [CDockablePane::Create](#create) při prvním vytvoření `CDockablePane`. Pokud `dwTabbedStyle` je AFX_CBRS_OUTLOOK_TABS je výchozím typem [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md); Pokud `dwTabbedStyle` je AFX_CBRS_REGULAR_TABS je výchozím typem [CTabbedPane třída](../../mfc/reference/ctabbedpane-class.md).  
  
-   Pokud chcete ukotvit jeden lze ukotvit podokno do druhého, zavolejte [CDockablePane::DockToWindow](#docktowindow) metoda. V podokně původní musí být ukotven někde před voláním této metody.  
  
-   Členské proměnné [CDockablePane::m_bHideInAutoHideMode](#m_bhideinautohidemode) ovládací prvky chování lze ukotvit podokna v automaticky skrýt režimu při volání [CDockablePane::ShowPane](#showpane). Pokud tato proměnná člen je nastavená na `TRUE`, budou skryté, lze ukotvit podokna a tlačítek skrýt automaticky. Jinak se bude snímek a odhlášení.  
  
-   Automaticky skrýt animace můžete zakázat nastavením [CDockablePane::m_bDisableAnimation](#m_bdisableanimation) členské proměnné na `TRUE`.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nakonfigurovat `CDockablePane` objektů pomocí různých metod v `CDockablePane` třídy. Příklad ukazuje, jak povolit automaticky skrýt všechny funkce pro podokně lze ukotvit, povolte titulek nebo úchytu, povolit režim automaticky skrýt, zobrazit v podokně a podokně, který je v režimu automaticky skrýt animace. Tento fragment kódu je součástí [Visual Studio Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#27](../../mfc/codesnippet/cpp/cdockablepane-class_1.cpp)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#28](../../mfc/codesnippet/cpp/cdockablepane-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxDockablePane.h  
  
##  <a name="attachtotabwnd"></a>CDockablePane::AttachToTabWnd  
 Připojí podokně aktuální do cílové podokna, vytváření podokno s kartami.  
  
```  
virtual CDockablePane* AttachToTabWnd(
    CDockablePane* pTabControlBarAttachTo,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bSetActive= TRUE,  
    CDockablePane** ppTabbedControlBar = NULL);  
```  
  
### <a name="parameters"></a>Parametry  
 [v] [out]`pTabControlBarAttachTo`  
 Určuje aktuální podokně připojí k podokna cíl. V podokně cíl musí být lze ukotvit podokně.  
  
 [v]`dockMethod`  
 Určuje metodu ukotvení.  
  
 [v]`bSetActive`  
 `TRUE`Chcete-li aktivovat podokně záložkách po operaci připojení; v opačném `FALSE`.  
  
 [out]`ppTabbedControlBar`  
 Obsahuje podokno s kartami, která je výsledkem operace připojení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na aktuální podokně, pokud není záložkách podokně; v opačném případě ukazatel do podokna s kartami, která je výsledkem operace připojení. Vrácená hodnota je `NULL` Pokud podokně aktuální nelze připojit, nebo pokud dojde k chybě.  
  
### <a name="remarks"></a>Poznámky  
 Pokud jeden lze ukotvit podokně připojí k jiné podokně touto metodou, dojde k následujícímu:  
  
1.  Framework kontrol zda podokně cíl `pTabControlBarAttachTo` je běžný ukotvení podokně nebo pokud je odvozený od [CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md).  
  
2.  Pokud je cílový podokno podokno s kartami, rozhraní přidána podokně aktuální jako na kartě.  
  
3.  Pokud je cílový podokno regulární ukotvené podokno, vytvoří rozhraní s kartami podokno.  
  
    -   Volání framework `pTabControlBarAttachTo->CreateTabbedPane`. Styl nové podokno s kartami závisí na `m_pTabbedControlBarRTC` člen. Ve výchozím nastavení, je tento člen hodnotu třídu runtime [CTabbedPane](../../mfc/reference/ctabbedpane-class.md). Pokud předáte `AFX_CBRS_OUTLOOK_TABS` styl jako `dwTabbedStyle` parametru [CDockablePane::Create](#create) metoda, objektu třídy runtime je nastavena na třídu runtime [CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md). Tento člen můžete změnit kdykoli změnit styl nové podokno.  
  
    -   Když tato metoda vytváří podokno s kartami, nahrazuje rozhraní má ukazatel na `pTabControlBarAttachTo` (Pokud v podokně je ukotvený nebo plovoucí v okně více miniframe) s ukazatel na nových záložkách podokně.  
  
    -   Rozhraní framework přidá `pTabControlBarAttachTo` podokně do podokna s kartami jako první kartě. Rozhraní framework potom přidá podokně aktuální jako druhý kartě.  
  
4.  Pokud aktuální podokno je odvozený od `CBaseTabbedPane`, všechny její karty přesunou do `pTabControlBarAttachTo` a podokně aktuální zničena. Proto buďte opatrní při volání této metody, protože ukazatel na aktuální podokno je pravděpodobně neplatný po návratu metody.  
  
 Pokud připojíte jeden podokně na jiný při sestavování ukotvení rozložení, nastavte `dockMethod` k `DM_SHOW`.  
  
 V podokně první by měl ukotvení předtím, než k němu připojí jiného podokna.  
  
##  <a name="calcfixedlayout"></a>CDockablePane::CalcFixedLayout  
 Vrátí velikost obdélníku podokně.  
  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bStretch`  
 Nepoužívá se.  
  
 [v]`bHorz`  
 Nepoužívá se.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CSize` objekt, který obsahuje velikost obdélníku podokně.  
  
##  <a name="canacceptminiframe"></a>CDockablePane::CanAcceptMiniFrame  
 Určuje, zda lze ukotvit zadaného zkrácená rámce do podokna.  
  
```  
virtual BOOL CanAcceptMiniFrame(CPaneFrameWnd* pMiniFrame) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pMiniFrame`  
 Ukazatel na `CPaneFrameWnd` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud `pMiniFrame` může být ukotveného do podokna, jinak hodnota `FALSE`.  
  
##  <a name="canacceptpane"></a>CDockablePane::CanAcceptPane  
 Určuje, zda lze do podokna aktuální ukotvit jiného podokna.  
  
```  
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pBar`  
 Určuje podokno ukotvení do podokna aktuální.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud zadaný podokně můžete ukotvit v tomto podokně; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá framework před podokno ukotven do podokna aktuální.  
  
 Funkci v odvozené třídě k povolení nebo zakázání ukotvení na konkrétní podokno přepište.  
  
 Ve výchozím nastavení, tato metoda vrátí hodnotu `TRUE` Pokud buď `pBar` nebo jeho nadřazený objekt je typu `CDockablePane`.  
  
##  <a name="canautohide"></a>CDockablePane::CanAutoHide  
 Určuje, zda v podokně můžete automaticky skrýt.  
  
```  
virtual BOOL CanAutoHide() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud v podokně můžete automaticky skrýt; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 `CDockablePane::CanAutoHide`Vrátí `FALSE` v následujících situacích:  
  
-   V podokně nemá nadřazený.  
  
-   Ukotvení manager neumožňuje podokna na automaticky skrýt.  
  
-   V podokně není ukotven.  
  
##  <a name="canbeattached"></a>CDockablePane::CanBeAttached  
 Určuje, zda aktuální podokně lze ukotvit do jiného podokna.  
  
```  
virtual BOOL CanBeAttached() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud lze ukotvit podokně lze ukotvit do jiného podokna nebo do hlavního rámce okna; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení, tato metoda vždy vrátí `TRUE`. Potlačí tuto metodu v odvozené třídě k povolení nebo zakázání ukotvení bez volání [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking).  
  
##  <a name="cdockablepane"></a>CDockablePane::CDockablePane  
 Vytvoří a inicializuje [CDockablePane](../../mfc/reference/cdockablepane-class.md) objektu.  
  
```  
CDockablePane();
```  
  
### <a name="remarks"></a>Poznámky  
 Poté, co vytvoříte objekt lze ukotvit podokně, volání [CDockablePane::Create](#create) nebo [CDockablePane::CreateEx](#createex) k jeho vytvoření.  
  
##  <a name="converttotabbeddocument"></a>CDockablePane::ConvertToTabbedDocument  
 Jeden nebo více lze ukotvit podokna převede do dokumentů s kartami MDI.  
  
```  
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bActiveTabOnly`  
 Při převodu `CTabbedPane`, zadejte `TRUE` převést pouze aktivní karty. Zadejte `FALSE` převést všechny karty v podokně.  
  
##  <a name="checkautohidecondition"></a>CDockablePane::CheckAutoHideCondition  
 Určuje, zda je v podokně ukotvení skryty (také označované jako autohide – režim).  
  
```  
virtual BOOL CheckAutoHideCondition();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud je splněna podmínka skrýt; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní používá časovač k pravidelně kontrolovat, zda chcete skrýt lze ukotvit podokně aplikace automaticky skrývat. Vrátí metoda `TRUE` když podokně není aktivní, v podokně není změnu velikosti a ukazatel myši není v podokně.  
  
 Pokud jsou splněny všechny předchozí podmínky, zavolá rozhraní [CDockablePane::Slide](#slide) ke skrytí podokna.  
  
##  <a name="checkstopslidecondition"></a>CDockablePane::CheckStopSlideCondition  
 Určuje, kdy ukotvení podokně aplikace autohide – by se měla zastavit klouzavé.  
  
```  
virtual BOOL CheckStopSlideCondition(BOOL bDirection);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bDirection`  
 `TRUE`Pokud je viditelné; podokno `FALSE` -li v podokně skryt.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud je splněna podmínka zastavení; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud lze ukotvit podokně je nastavená na režim autohide –, systém použije posuvné důsledky k zobrazení nebo skrytí podokna. Když je v podokně klouzavé volá rámec této funkce. `CheckStopSlideCondition`Vrátí `TRUE` po plně zobrazené v podokně nebo když je plně skrytá.  
  
 Potlačí tuto metodu v odvozené třídě implementovat vlastní autohide – účinky.  
  
##  <a name="copystate"></a>CDockablePane::CopyState  
 Zkopíruje stav lze ukotvit podokně.  
  
```  
virtual void CopyState(CDockablePane* pOrgBar);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pOrgBar`  
 Ukazatel na lze ukotvit podokně.  
  
### <a name="remarks"></a>Poznámky  
 `CDockablePane::CopyState`zkopíruje stav `pOrgBar` do podokna aktuální při volání těchto metod:  
  
- [CPane::CopyState](../../mfc/reference/cpane-class.md#copystate)  
  
- [CDockablePane::GetAHRestoredRect](#getahrestoredrect)  
  
- [CDockablePane::GetAHSlideMode](#getahslidemode)  
  
- [CDockablePane::GetLastPercentInPaneContainer](#getlastpercentinpanecontainer)  
  
- [CDockablePane::IsAutohideAllEnabled](#isautohideallenabled)  
  
##  <a name="create"></a>CDockablePane::Create  
 Vytvoří ovládacího prvku Windows a připojí jej k [CDockablePane](../../mfc/reference/cdockablepane-class.md) objektu.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszCaption,  
    CWnd* pParentWnd,  
    const RECT& rect,  
    BOOL bHasGripper,  
    UINT nID,  
    DWORD dwStyle,  
    DWORD dwTabbedStyle = AFX_CBRS_REGULAR_TABS,  
    DWORD dwControlBarStyle = AFX_DEFAULT_DOCKING_PANE_STYLE,  
    CCreateContext* pContext = NULL);

 
virtual BOOL Create(
    LPCTSTR lpszWindowName,  
    CWnd* pParentWnd,  
    CSize sizeDefault,  
    BOOL bHasGripper,  
    UINT nID,  
    DWORD dwStyle = WS_CHILD|WS_VISIBLE|CBRS_TOP|CBRS_HIDE_INPLACE,  
    DWORD dwTabbedStyle = AFX_CBRS_REGULAR_TABS,  
    DWORD dwControlBarStyle = AFX_DEFAULT_DOCKING_PANE_STYLE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszCaption`  
 Určuje název okna.  
  
 [v] [out]`pParentWnd`  
 Určuje nadřazeného okna.  
  
 [v]`rect`  
 Určuje velikost a umístění okna, v souřadnice klienta `pParentWnd`.  
  
 [v]`bHasGripper`  
 `TRUE`Chcete-li vytvořit v podokně s popiskem; v opačném `FALSE`.  
  
 [v]`nID`  
 Určuje ID podřízeného okna. Tato hodnota musí být jedinečný, pokud chcete uložit ukotvení stav pro toto podokno ukotvení.  
  
 [v]`dwStyle`  
 Určuje styl atributů okna.  
  
 [v]`dwTabbedStyle`  
 Určuje styl záložkách v záložkách okno, které se vytvoří, když uživatel nastavuje tažením podokno na titulek v tomto podokně.  
  
 [v]`dwControlBarStyle`  
 Určuje styl další atributy.  
  
 [v] [out]`pContext`  
 Určuje kontext vytvořit okna.  
  
 [v]`lpszWindowName`  
 Určuje název okna.  
  
 [v]`sizeDefault`  
 Určuje velikost okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud lze ukotvit podokně je úspěšně vytvořen; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoří podokno Windows a připojí jej k `CDockablePane` objektu.  
  
 Pokud `dwStyle` má styl oken `CBRS_FLOAT_MULTI` příznak okno miniframe můžete float s další podokna v okně miniframe. Ve výchozím nastavení ukotvení podokna můžete pouze float jednotlivě.  
  
 Pokud `dwTabbedStyle` parametr má `AFX_CBRS_OUTLOOK_TABS` zadán příznak, v podokně vytvoří Outlook stylu – záložkami podokna po připojení k této konfigurace pomocí podokna Další podokno [CDockablePane::AttachToTabWnd](#attachtotabwnd) metoda. Ve výchozím nastavení, lze ukotvit podokna vytvořit regulární záložkách podokna typu [CTabbedPane](../../mfc/reference/ctabbedpane-class.md).  
  
##  <a name="createdefaultpanedivider"></a>CDockablePane::CreateDefaultPaneDivider  
 Vytvoří výchozí oddělovač pro podokně jako ukotvena okně s rámečkem.  
  
```  
static CPaneDivider* __stdcall CreateDefaultPaneDivider(
    DWORD dwAlignment,  
    CWnd* pParent,  
    CRuntimeClass* pSliderRTC = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`dwAlignment`  
 Určuje na straně hlavního rámce, ke kterému je ukotven podokně. Pokud `dwAlignment` obsahuje `CBRS_ALIGN_LEFT` nebo `CBRS_ALIGN_RIGHT` příznak, tato metoda vytvoří svislé ( `CPaneDivider::SS_VERT`) dělicí; jinak tato metoda vytvoří vodorovných ( `CPaneDivider::SS_HORZ`) oddělovač.  
  
 [v]`pParent`  
 Ukazatel na rámec nadřazené.  
  
 [v]`pSliderRTC`  
 Nepoužívá se.  
  
### <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí ukazatel na nově vytvořený oddělovač, nebo `NULL` Pokud rozdělovací vytvoření nezdaří.  
  
### <a name="remarks"></a>Poznámky  
 `dwAlignment`může být jedno z následujících hodnot:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`CBRS_ALIGN_TOP`|V podokně se ukotven k horní části klientské oblasti okně s rámečkem.|  
|`CBRS_ALIGN_BOTTOM`|V podokně se ukotven k dolnímu okraji klientské oblasti okně s rámečkem.|  
|`CBRS_ALIGN_LEFT`|V podokně se ukotven k levé straně klientské oblasti okně s rámečkem.|  
|`CBRS_ALIGN_RIGHT`|V podokně se ukotven na pravé straně klientské oblasti okně s rámečkem.|  
  
##  <a name="createex"></a>CDockablePane::CreateEx  
 Vytvoří ovládacího prvku Windows a připojí jej k [CDockablePane](../../mfc/reference/cdockablepane-class.md) objektu.  
  
```  
virtual BOOL CreateEx(
    DWORD dwStyleEx,  
    LPCTSTR lpszCaption,  
    CWnd* pParentWnd,  
    const RECT& rect,  
    BOOL bHasGripper,  
    UINT nID,  
    DWORD dwStyle,  
    DWORD dwTabbedStyle = AFX_CBRS_REGULAR_TABS,  
    DWORD dwControlBarStyle = AFX_DEFAULT_DOCKING_PANE_STYLE,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`dwStyleEx`  
 Určuje styl rozšířené atributy v novém okně.  
  
 [v]`lpszCaption`  
 Určuje název okna.  
  
 [v] [out]`pParentWnd`  
 Určuje nadřazeného okna.  
  
 [v]`rect`  
 Určuje velikost a umístění okna, v souřadnice klienta `pParentWnd`.  
  
 [v]`bHasGripper`  
 `TRUE`Chcete-li vytvořit v podokně s popiskem; v opačném `FALSE`.  
  
 [v]`nID`  
 Určuje ID podřízeného okna. Tato hodnota musí být jedinečný, pokud chcete uložit ukotvení stav pro toto podokno ukotvení.  
  
 [v]`dwStyle`  
 Určuje styl atributů okna.  
  
 [v]`dwTabbedStyle`  
 Určuje styl záložkách v záložkách okno, které se vytvoří, když uživatel nastavuje tažením podokno na titulek v tomto podokně.  
  
 [v]`dwControlBarStyle`  
 Určuje styl další atributy.  
  
 [v] [out]`pContext`  
 Určuje kontext vytvořit okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud lze ukotvit podokně je úspěšně vytvořen; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoří podokno Windows a připojí jej k `CDockablePane` objektu.  
  
 Pokud `dwStyle` má styl oken `CBRS_FLOAT_MULTI` příznak okno miniframe můžete float s další podokna v okně miniframe. Ve výchozím nastavení ukotvení podokna můžete pouze float jednotlivě.  
  
 Pokud `dwTabbedStyle` parametr má `AFX_CBRS_OUTLOOK_TABS` zadán příznak, v podokně vytvoří Outlook stylu – záložkami podokna po připojení k této konfigurace pomocí podokna Další podokno [CDockablePane::AttachToTabWnd](#attachtotabwnd) metoda. Ve výchozím nastavení, lze ukotvit podokna vytvořit regulární záložkách podokna typu [CTabbedPane](../../mfc/reference/ctabbedpane-class.md).  
  
##  <a name="createtabbedpane"></a>CDockablePane::CreateTabbedPane  
 Vytvoří záložkách podokno z podokna aktuální.  
  
```  
virtual CTabbedPane* CreateTabbedPane();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nové podokno s kartami, nebo `NULL` Pokud operace vytvoření se nezdařilo.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá framework při vytváření podokno s kartami k nahrazení v tomto podokně. Další informace najdete v tématu [CDockablePane::AttachToTabWnd](#attachtotabwnd).  
  
 Přepsat tuto metodu v odvozené třídě a přizpůsobit jak záložkách podokna jsou vytvořeny a inicializovány.  
  
 Podokno s kartami je vytvořena v souladu runtime třídy informace uložené v `m_pTabbedControlBarRTC` člena, který se inicializuje pomocí [CDockablePane::CreateEx](#createex) metoda.  
  
##  <a name="dockpanecontainer"></a>CDockablePane::DockPaneContainer  
 Kontejner ukotvené do podokna.  
  
```  
virtual BOOL DockPaneContainer(
    CPaneContainerManager& barContainerManager,  
    DWORD dwAlignment,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`barContainerManager`  
 Odkaz na kontejner manager kontejneru, který je právě ukotven.  
  
 [v]`dwAlignment`  
 `DWORD`na straně v podokně, ke kterému je ukotven kontejneru, který určuje.  
  
 [v]`dockMethod`  
 Nepoužívá se.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud kontejner byl úspěšně ukotven do podokna; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 `dwAlignment`může být jedno z následujících hodnot:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`CBRS_ALIGN_TOP`|Kontejner se ukotven k horní části podokna.|  
|`CBRS_ALIGN_BOTTOM`|Kontejner se ukotven do spodní části podokna.|  
|`CBRS_ALIGN_LEFT`|Kontejner se ukotven k levé části podokna.|  
|`CBRS_ALIGN_RIGHT`|Kontejner se ukotven pravé části podokna.|  
  
##  <a name="dockpanestandard"></a>CDockablePane::DockPaneStandard  
 Podokno ukotvené pomocí outline (standardní) ukotvení.  
  
```  
virtual CPane* DockPaneStandard(BOOL& bWasDocked);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bWasDocked`  
 Po návratu metody obsahuje tuto hodnotu `TRUE` Pokud podokně byla úspěšně ukotveného jinak, obsahuje `FALSE`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud se v podokně ukotvena okno s kartami, nebo pokud okno s kartami byl vytvořen v důsledku ukotvení, tato metoda vrátí ukazatel do okna s kartami. Pokud v podokně se jinak úspěšně ukotven, vrátí tato metoda `this` ukazatel. Pokud ukotvení chyba, vrátí tato metoda `NULL`.  
  
##  <a name="docktorecentpos"></a>CDockablePane::DockToRecentPos  
 Ukotvené podokno k jeho uložené pozici ukotvení.  
  
```  
BOOL CDockablePane::DockToRecentPos();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud v podokně úspěšně ukotveno; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Lze ukotvit podokna ukládání poslední ukotvení informací v [CRecentDockSiteInfo](../../mfc/reference/crecentdocksiteinfo-class.md) objektu.  
  
##  <a name="docktowindow"></a>CDockablePane::DockToWindow  
 Ukotvené jeden ukotvení podokně do jiného ukotvení panelu.  
  
```  
virtual BOOL DockToWindow(
    CDockablePane* pTargetWindow,  
    DWORD dwAlignment,  
    LPCRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v] [out]`pTargetWindow`  
 Určuje ukotvení – v tomto podokně na podokně lze ukotvit.  
  
 [v]`dwAlignment`  
 Určuje zarovnání ukotvení v podokně. Může být CBRS_ALIGN_LEFT, CBRS_ALIGN_TOP, CBRS_ALIGN_RIGHT, CBRS_ALIGN_BOTTOM nebo cbrs_align_any –. (Definovanou v afxres.h.)  
  
 [v]`lpRect`  
 Určuje ukotvení rámeček pro podokně.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud v podokně se ukotven úspěšně; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Voláním této metody lze ukotvit jeden podokno do jiného podokna s zarovnání určeného `dwAlignment`.  
  
##  <a name="drawcaption"></a>CDockablePane::DrawCaption  
 Nakreslí popisek (také nazývané úchytu) ukotvení panelu.  
  
```  
virtual void DrawCaption(
    CDC* pDC,  
    CRect rectCaption);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Představuje kontext zařízení používá pro vykreslování.  
  
 [v]`rectCaption`  
 Určuje titulek v podokně ohraničující obdélník.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework volá tuto metodu k vykreslení titulek lze ukotvit podokně.  
  
 Potlačí tuto metodu v odvozené třídě přizpůsobit vzhled titulek.  
  
##  <a name="enableautohideall"></a>CDockablePane::EnableAutohideAll  
 Povolí nebo zakáže autohide – režim pro toto podokno a další podokna v kontejneru.  
  
```  
void EnableAutohideAll(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bEnable`  
 `TRUE`Chcete-li povolit autohide – všechny funkce pro lze ukotvit podokna. v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud má uživatel `Ctrl` klíč a klikne na tlačítko pin podokno přepnout do režimu autohide – všechny ostatní podokna ve stejném kontejneru jsou také přepnout do režimu autohide –.  
  
 Volat tuto metodu s `bEnable` nastavena na `FALSE` tuto funkci pro konkrétní podokno zakázat.  
  
##  <a name="enablegripper"></a>CDockablePane::EnableGripper  
 Zobrazí nebo skryje titulek (také nazývané úchytu).  
  
```  
virtual void EnableGripper(BOOL bEnable);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bEnable`  
 `TRUE`Chcete-li povolit titulek; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud systém vytvoří lze ukotvit podokna, nemají **WS_STYLE** styl oken, i když je zadán. To znamená, že v podokně titulek je neklientská oblast, která se řídí rámcem, ale tato oblast se liší od standardní okno titulek.  
  
 Můžete zobrazit nebo skrýt titulek kdykoli. Rozhraní framework skryje titulek při podokno se přidal jako na kartě okno s kartami nebo když je v okně miniframe obtékané podokno.  
  
##  <a name="getahrestoredrect"></a>CDockablePane::GetAHRestoredRect  
 Určuje pozici panelu v režimu automaticky skrýt.  
  
```  
CRect GetAHRestoredRect() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CRect` objekt, který obsahuje pozici v podokně, když je v režimu automaticky skrýt.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getahslidemode"></a>CDockablePane::GetAHSlideMode  
 Načte režim automaticky skrýt snímku pro podokně.  
  
```  
virtual UINT GetAHSlideMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `UINT` , určuje režim automaticky skrýt snímku pro podokně. Vrácená hodnota může být buď `AFX_AHSM_MOVE` nebo `AFX_AHSM_STRETCH`, ale implementace používá jenom `AFX_AHSM_MOVE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getcaptionheight"></a>CDockablePane::GetCaptionHeight  
 Vrátí výšku v pixelech titulek aktuální.  
  
```  
virtual int GetCaptionHeight() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výška titulek v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Výška titulek je 0, pokud titulek byl skrytý za [CDockablePane::EnableGripper](#enablegripper) metoda, nebo není-li v podokně popisek.  
  
##  <a name="getdefaultpanedivider"></a>CDockablePane::GetDefaultPaneDivider  
 Vrátí dělicí podokně výchozí pro kontejner v podokně.  
  
```  
CPaneDivider* GetDefaultPaneDivider() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Platná [CPaneDivider](../../mfc/reference/cpanedivider-class.md) objektu, pokud lze ukotvit podokně ukotven do hlavního rámce okna, nebo `NULL` Pokud není ukotven podokně lze ukotvit nebo pokud je s plovoucí čárkou.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o rozdělení podokně najdete v tématu [CPaneDivider třída](../../mfc/reference/cpanedivider-class.md).  
  
##  <a name="getdockingstatus"></a>CDockablePane::GetDockingStatus  
 Určuje, že podokno schopnost ukotvit v závislosti na umístění zadaná ukazatele.  
  
```  
virtual AFX_CS_STATUS GetDockingStatus(
    CPoint pt,  
    int nSensitivity);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pt`  
 Umístění ukazatele v souřadnice obrazovky.  
  
 [v]`nSensitivity`  
 Vzdálenost v pixelech, od rohu obdélníku ukazatele musí být ukotvení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jedna z následujících hodnot stavu:  
  
|`AFX_CS_STATUS`Hodnota|Význam|  
|---------------------------|-------------|  
|`CS_NOTHING`|Ukazatel není přes lokalitu ukotvení. Rozhraní není ukotvení v podokně.|  
|`CS_DOCK_IMMEDIATELY`|Ukazatel myši nachází prostřednictvím webu ukotvení v přímý režim (používá se v podokně `DT_IMMEDIATE` ukotvení režim). V podokně ukotvené rozhraní okamžitě.|  
|`CS_DELAY_DOCK`|Je ukazatel myši nad ukotvení lokalitu, která je jiného ukotvení panelu nebo okraj hlavního rámce. Rozhraní framework ukotvené podokně po prodlevě. Najdete v části poznámky Další informace o tato prodleva.|  
|`CS_DELAY_DOCK_TO_TAB`|Ukazatel myši nachází přes ukotvení lokalitu, která způsobí, že podokno Ukotvit okno s kartami. K tomu dochází, když ukazatel myši nachází přes titulek jiné ukotvení panelu nebo přes oblast karty na kartách panelu.|  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework volá tuto metodu za účelem zpracování ukotvení plovoucí podokna.  
  
 Plovoucí panely nástrojů nebo ukotvení podokna, které používají `DT_IMMEDIATE` ukotvení režimu, rozhraní zpozdí ukotvení příkaz, který povolí uživateli přesunout mimo klientské oblasti nadřazeného rámce okna, předtím, než dojde k ukotvení. Délka zpoždění se měří v milisekundách a řídí [CDockingManager::m_nTimeOutBeforeToolBarDock](../../mfc/reference/cdockingmanager-class.md#m_ntimeoutbeforetoolbardock) – datový člen... Výchozí hodnota [CDockingManager::m_nTimeOutBeforeToolBarDock](../../mfc/reference/cdockingmanager-class.md#m_ntimeoutbeforetoolbardock) je 200. Toto chování emuluje chování ukotvení [!INCLUDE[ofprword](../../mfc/reference/includes/ofprword_md.md)] 2007.  
  
 Pro odložené ukotvení stavy ( `CS_DELAY_DOCK` a `CS_DELAY_DOCK_TO_TAB`), rozhraní neprovádí ukotvení, dokud bude uživatel tlačítko myši. Pokud podokno používá `DT_STANDARD` ukotvení režimu, rozhraní zobrazí obdélníku v předpokládané ukotvení umístění. Pokud podokno používá `DT_SMART` ukotvení režimu, rozhraní zobrazí inteligentní značky ukotvení a poloprůhledné obdélníky v předpokládané ukotvení umístění. Chcete-li zadat ukotvení režimu pro podokno, zavolejte [CBasePane::SetDockingMode](../../mfc/reference/cbasepane-class.md#setdockingmode) metoda. Další informace o inteligentní ukotvení najdete v tématu [CDockingManager::GetSmartDockingParams](../../mfc/reference/cdockingmanager-class.md#getsmartdockingparams).  
  
##  <a name="getdragsensitivity"></a>CDockablePane::GetDragSensitivity  
 Vrátí velkých a malých písmen přetáhněte ukotvení panelu.  
  
```  
static const CSize& GetDragSensitivity();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md) objekt, který obsahuje šířku a výšku v pixelech obdélníku uprostřed bod přetažení. Operaci přetažení nezačíná, dokud se ukazatel myši přesune mimo obdélníku.  
  
##  <a name="getlastpercentinpanecontainer"></a>CDockablePane::GetLastPercentInPaneContainer  
 Načítá procentní podíl místa, které zabírá podokno v jeho kontejneru ( [CPaneContainer třída](../../mfc/reference/cpanecontainer-class.md)).  
  
```  
int GetLastPercentInPaneContainer() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `int` Určující procento místa, které v podokně zabírá v jeho kontejneru.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda se používá při kontejneru upraví jeho rozložení.  
  
##  <a name="gettabarea"></a>CDockablePane::GetTabArea  
 Načte oblast karty pro podokně.  
  
```  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`rectTabAreaTop`  
 `GetTabArea`Pokud se nachází v horní části podokna karty vyplní tato proměnná oblast karty. Pokud karty se nacházejí ve spodní části podokna, tato proměnná je vyplněn prázdný obdélník.  
  
 [v]`rectTabAreaBottom`  
 `GetTabArea`Tato proměnná vyplní oblast karty Pokud karty jsou umístěné v dolní části podokna. Pokud se nachází v horní části podokna karty Tato proměnná je vyplněn prázdný obdélník.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda se používá pouze v třídy, které jsou odvozeny od `CDockablePane` a karty. Další informace najdete v tématu [CTabbedPane::GetTabArea](../../mfc/reference/ctabbedpane-class.md#gettabarea) a [CMFCOutlookBar::GetTabArea](../../mfc/reference/cmfcoutlookbar-class.md#gettabarea).  
  
##  <a name="gettabbedpanertc"></a>CDockablePane::GetTabbedPaneRTC  
 Vrací runtime třídy informace o okno s kartami, která se vytvoří při další podokno ukotvené do podokna aktuální.  
  
```  
CRuntimeClass* GetTabbedPaneRTC() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Třída informace modulu runtime pro podokně lze ukotvit.  
  
### <a name="remarks"></a>Poznámky  
 Voláním této metody lze načíst informace o třídě modulu runtime pro záložkách podokna, které vytvářejí dynamicky. Tato situace může nastat, když uživatel nastavuje tažením jeden podokně na titulek jiného podokna, nebo když zavoláte [CDockablePane::AttachToTabWnd](#attachtotabwnd) metoda prostřednictvím kódu programu vytvořte záložkách podokně z dvě podokna lze ukotvit.  
  
 Informace o třídě runtime můžete nastavit tak, že zavoláte [CDockablePane::SetTabbedPaneRTC](#settabbedpanertc) metoda.  
  
##  <a name="hasautohidemode"></a>CDockablePane::HasAutoHideMode  
 Určuje, zda lze ukotvení podokně přepnout do režimu autohide –.  
  
```  
virtual BOOL HasAutoHideMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud lze ukotvit podokně můžete přepnout do režimu autohide –; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu v odvozené třídě zakázat režim autohide – pro konkrétní podokno lze ukotvit.  
  
##  <a name="hittest"></a>CDockablePane::HitTest  
 Určuje umístění v podokně, kde uživatel klikne na tlačítko myši.  
  
```  
virtual int HitTest(
    CPoint point,  
    BOOL bDetectCaption = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`point`  
 Určuje bod k testování.  
  
 [v]`bDetectCaption`  
 `TRUE`Pokud `HTCAPTION` má být vrácen, pokud je bod na titulek v podokně; jinak `FALSE`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jedna z následujících hodnot:  
  
- `HTNOWHERE`Pokud `point` není v podokně lze ukotvit.  
  
- `HTCLIENT`Pokud `point` v klientské oblasti podokně lze ukotvit.  
  
- `HTCAPTION`Pokud `point` je v oblasti titulek podokně lze ukotvit.  
  
- `AFX_HTCLOSE`Pokud `point` na tlačítko Zavřít.  
  
- `HTMAXBUTTON`Pokud `point` je na tlačítku PIN kód.  
  
##  <a name="isautohideallenabled"></a>CDockablePane::IsAutohideAllEnabled  
 Určuje, zda ukotvení panelu a všechny ostatní podokna v kontejneru je možné přepnout do režimu autohide –.  
  
```  
virtual BOOL IsAutohideAllEnabled() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud lze ukotvit podokno a všechny ostatní podokna v kontejneru, můžete přepnout do režimu autohide –; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Uživatel umožňuje režimu autohide – kliknutím na tlačítko ukotvení kódu pin při uložení **Ctrl** klíč  
  
 Chcete-li povolit nebo zakázat toto chování, zavolejte [CDockablePane::EnableAutohideAll](#enableautohideall) metoda.  
  
##  <a name="isautohidemode"></a>CDockablePane::IsAutoHideMode  
 Určuje, zda podokno v režimu automaticky skrývat.  
  
```  
virtual BOOL IsAutoHideMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud je lze ukotvit podokno v režimu autohide –; v opačném `FALSE`.  
  
##  <a name="isdocked"></a>CDockablePane::IsDocked  
 Určuje, zda je ukotvena podokně aktuální.  
  
```  
virtual BOOL IsDocked() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud lze ukotvit podokně nepatří do okna miniframe nebo pokud je plovoucí v okně miniframe s jiného podokna. `FALSE`Pokud v podokně je podřízená okna miniframe a neexistují žádná další podokna, které patří do okna miniframe.  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li zjistit, zda je v podokně ukotven do hlavního rámce okna, volejte [CDockablePane::GetDefaultPaneDivider](#getdefaultpanedivider). Pokud metoda vrátí ukazatel jinou hodnotu než NULL, v podokně ukotven v hlavním okně rámce.  
  
##  <a name="ishideinautohidemode"></a>CDockablePane::IsHideInAutoHideMode  
 Určuje chování panelu, který je v režimu autohide – Pokud se zobrazí (nebo skrytý) voláním [CDockablePane::ShowPane](#showpane).  
  
```  
virtual BOOL IsHideInAutoHideMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud lze ukotvit podokně by být skrytý v režimu autohide –; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Je-li lze ukotvit podokno v režimu automaticky skrývat, chová odlišně při volání `ShowPane` pro skrytí nebo zobrazení podokna. Toto chování je řízeno statický člen [CDockablePane::m_bHideInAutoHideMode](#m_bhideinautohidemode). Pokud je tento člen `TRUE`, lze ukotvit podokně a jeho souvisejících autohide – nástrojů nebo autohide – tlačítko je skrytý nebo uvedeném při volání `ShowPane`. Jinak podokně lze ukotvit je aktivace nebo deaktivace a jeho souvisejících autohide – nástrojů nebo tlačítko autohide – je vždy zobrazen.  
  
 Potlačí tuto metodu v odvozené třídě Chcete-li změnit výchozí chování pro jednotlivé podokna.  
  
 Výchozí hodnota pro `m_bHideInAutoHideMode` je `FALSE`.  
  
##  <a name="isinfloatingmultipaneframewnd"></a>CDockablePane::IsInFloatingMultiPaneFrameWnd  
 Určuje, jestli je v podokně v rámci více podokně okna ( [CMultiPaneFrameWnd třída](../../mfc/reference/cmultipaneframewnd-class.md)).  
  
```  
virtual BOOL IsInFloatingMultiPaneFrameWnd() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud v podokně se v rámci více podokně okna; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isresizable"></a>CDockablePane::IsResizable  
 Určuje, zda je v podokně s možností změny velikosti.  
  
```  
virtual BOOL IsResizable() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud je v podokně s možností změny velikosti; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení jsou lze ukotvit podokna s možností změny velikosti. Pokud chcete zabránit, změnu velikosti, přepište tuto metodu v odvozené třídě a vrátit `FALSE`. Všimněte si, že `FALSE` hodnota vede k nezdařené `ASSERT` v [CPane::DockPane](../../mfc/reference/cpane-class.md#dockpane). Použití [CDockingManager::AddPane](../../mfc/reference/cdockingmanager-class.md#addpane) místo toho chcete ukotvit podokno v rámci nadřazené.  
  
 Podokna, které nelze změnit velikost můžete ani float ani zadejte režim automaticky skrýt a se vždycky nacházejí ve vnějšího okraje nadřazeného rámce.  
  
##  <a name="istablocationbottom"></a>CDockablePane::IsTabLocationBottom  
 Určuje, zda jsou umístěny v horní nebo dolní části podokna karty.  
  
```  
virtual BOOL IsTabLocationBottom() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud karty jsou umístěné v dolní části podokna. `FALSE` Pokud karty jsou umístěné v horní části podokna.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [CTabbedPane::IsTabLocationBottom](../../mfc/reference/ctabbedpane-class.md#istablocationbottom).  
  
##  <a name="istracked"></a>CDockablePane::IsTracked  
 Určuje, zda podokno přesouvá uživatelem.  
  
```  
BOOL IsTracked() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud se v podokně se přesune; v opačném `FALSE`.  
  
##  <a name="isvisible"></a>CDockablePane::IsVisible  
 Určuje, zda se zobrazuje aktuální podokno.  
  
```  
virtual BOOL IsVisible() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud se zobrazuje; lze ukotvit podokno v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Voláním této metody lze určit, zda lze ukotvit podokně je viditelné. Tuto metodu můžete použít namísto volání [CWnd::IsWindowVisible](../../mfc/reference/cwnd-class.md#iswindowvisible) nebo testování `WS_VISIBLE` stylu. Stav vrácený viditelnosti závisí na tom, zda povolit nebo zakázat režim autohide – a na základě hodnoty [CDockablePane::IsHideInAutoHideMode](#ishideinautohidemode) vlastnost.  
  
 Pokud je v režimu autohide – lze ukotvit podokno a `IsHideInAutoHideMode` vrátí `FALSE` stav viditelnosti je vždy `FALSE`.  
  
 Pokud je v režimu autohide – lze ukotvit podokno a `IsHideInAutoHideMode` vrátí `TRUE` stav viditelnosti závisí na stavu viditelnost panelu nástrojů související autohide –.  
  
 Pokud lze ukotvit podokně není v režimu automaticky skrývat, je dáno stav viditelnosti [CBasePane::IsVisible](../../mfc/reference/cbasepane-class.md#isvisible) metoda.  
  
##  <a name="m_bdisableanimation"></a>CDockablePane::m_bDisableAnimation  
 Určuje, zda je animace autohide – lze ukotvit podokna zakázána.  
  
```  
AFX_IMPORT_DATA static BOOL m_bDisableAnimation;  
```  
  
##  <a name="m_bhideinautohidemode"></a>CDockablePane::m_bHideInAutoHideMode  
 Určuje chování v podokně, když je v režimu autohide – podokno.  
  
```  
AFX_IMPORT_DATA static BOOL m_bHideInAutoHideMode;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tato hodnota ovlivňuje všechny ukotvení podokna v aplikaci.  
  
 Pokud nastavíte tento člen na `TRUE`, lze ukotvit podokna jsou skrytý nebo uvedeném s jejich související autohide – panely nástrojů a tlačítka při volání [CDockablePane::ShowPane](#showpane).  
  
 Pokud nastavíte tento člen na `FALSE`, lze ukotvit podokna jsou aktivace nebo deaktivace při volání [CDockablePane::ShowPane](#showpane).  
  
##  <a name="m_nslidesteps"></a>CDockablePane::m_nSlideSteps  
 Určuje rychlost animace v podokně, pokud je v režimu automaticky skrývat.  
  
```  
AFX_IMPORT_DATA static int m_nSlideSteps;  
```  
  
### <a name="remarks"></a>Poznámky  
 Rychlejší animace platit snížíte tuto hodnotu. Tuto hodnotu zvýšit efekt pomalejší animace.  
  
##  <a name="onafterchangeparent"></a>CDockablePane::OnAfterChangeParent  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWndOldParent`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onafterdockfromminiframe"></a>CDockablePane::OnAfterDockFromMiniFrame  
 Voláno rámcem při plovoucí ukotvení panelu ukotvené v okně s rámečkem.  
  
```  
virtual void OnAfterDockFromMiniFrame();
```  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tato metoda neprovede žádnou akci.  
  
##  <a name="onbeforechangeparent"></a>CDockablePane::OnBeforeChangeParent  
 Tato metoda volá framework předtím, než změní nadřazené části podokna.  
  
```  
virtual void OnBeforeChangeParent(
    CWnd* pWndNewParent,  
    BOOL bDelay = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWndNewParent`  
 Ukazatel do nového nadřazeného okna.  
  
 [v]`bDelay`  
 `BOOL`který určuje, jestli zpoždění při každém přepočítání ukotvení rozložení, pokud není ukotvený v podokně. Další informace najdete v tématu [CDockablePane::UndockPane](#undockpane).  
  
### <a name="remarks"></a>Poznámky  
 Pokud je ukotveno podokně a do nové nadřazené neumožňuje ukotvení, tato metoda předchozího podokna.  
  
 Pokud v podokně je převáděn na dokumentů s kartami, tato metoda ukládá jeho poslední pozici ukotvení. Rozhraní používá poslední pozici ukotvení obnovit pozici v podokně při převodu zpět do ukotveného stavu.  
  
##  <a name="onbeforefloat"></a>CDockablePane::OnBeforeFloat  
 Rozhraní framework volá tuto metodu před podokno přechody do plovoucí stavu.  
  
```  
virtual BOOL OnBeforeFloat(
    CRect& rectFloat,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`rectFloat`  
 Pokud je ve stavu, plovoucí Určuje umístění a velikost podokna.  
  
 [v]`dockMethod`  
 Určuje metodu ukotvení. V tématu [CPane::DockPane](../../mfc/reference/cpane-class.md#dockpane) seznam možných hodnot.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud v podokně můžete obtékané; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána rámcem při podokno je o float. Pokud chcete provést jakékoli zpracovávání před jako plovoucí podokně můžete přepsat tuto metodu v odvozené třídě.  
  
##  <a name="onpressbuttons"></a>CDockablePane::OnPressButtons  
 Volá se, když uživatel stiskne tlačítko titulek jiné než `AFX_HTCLOSE` a `AFX_HTMAXBUTTON` tlačítka.  
  
```  
virtual void OnPressButtons(UINT nHit);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nHit`  
 Tento parametr není používán.  
  
### <a name="remarks"></a>Poznámky  
 Pokud přidáte vlastní tlačítko titulek lze ukotvit podokně, potlačí tuto metodu pro příjem oznámení po stisknutí tlačítka.  
  
##  <a name="onslide"></a>CDockablePane::OnSlide  
 Voláno rámcem pro animaci podokně, když je v režimu automaticky skrývat.  
  
```  
virtual void OnSlide(BOOL bSlideOut);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bSlideOut`  
 `TRUE`k zobrazení podokna. `FALSE` ke skrytí podokna.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu v odvozené třídě implementovat vlastní autohide – účinky.  
  
##  <a name="removefromdefaultpanedividier"></a>CDockablePane::RemoveFromDefaultPaneDividier  
 Rozhraní framework volá tuto metodu, když je právě nepřipojený podokno.  
  
```  
void RemoveFromDefaultPaneDividier();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda nastaví dělicí podokně výchozí `NULL` a v podokně odebere jeho kontejneru.  
  
##  <a name="replacepane"></a>CDockablePane::ReplacePane  
 V podokně nahradí zadaný podokně.  
  
```  
BOOL ReplacePane(
    CDockablePane* pBarToReplaceWith,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bRegisterWithFrame = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pBarToReplaceWith`  
 Ukazatel na lze ukotvit podokně.  
  
 [v]`dockMethod`  
 Nepoužívá se.  
  
 [v]`bRegisterWithFrame`  
 Pokud `TRUE`, nové podokno není zaregistrována správce ukotvení nadřazené staré podokna. Nové podokno je vložen v indexu stará podokna v seznamu podokna, který se spravuje pomocí Správce ukotvení.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud chcete nahrazení úspěšné; v opačném `FALSE`.  
  
##  <a name="restoredefaultpanedivider"></a>CDockablePane::RestoreDefaultPaneDivider  
 Pokud podokno deserializován, rozhraní volá tuto metodu za účelem obnovení dělicí podokně výchozí.  
  
```  
void RestoreDefaultPaneDivider();
```  
  
### <a name="remarks"></a>Poznámky  
 Grafika podokně obnovené výchozí nahradí aktuální dělicí podokně výchozí, pokud existuje.  
  
##  <a name="setautohidemode"></a>CDockablePane::SetAutoHideMode  
 Přepíná podokně ukotvení mezi viditelné a autohide – režim.  
  
```  
virtual CMFCAutoHideBar* SetAutoHideMode(
    BOOL bMode,  
    DWORD dwAlignment,  
    CMFCAutoHideBar* pCurrAutoHideBar = NULL,  
    BOOL bUseTimer = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bMode`  
 `TRUE`Pokud chcete povolit režim autohide –; `FALSE` povolení regulární ukotvení režimu.  
  
 [v]`dwAlignment`  
 Určuje zarovnání podokně autohide – k vytvoření.  
  
 [v] [out]`pCurrAutoHideBar`  
 Ukazatel na aktuální autohide – nástrojů. Může být `NULL`.  
  
 [v]`bUseTimer`  
 Určuje, jestli účinek autohide – když uživatel přejde do režimu autohide – podokně nebo skrýt podokno okamžitě.  
  
### <a name="return-value"></a>Návratová hodnota  
 Autohide – nástrojů, který byl vytvořen v důsledku přepnutí do režimu autohide – nebo `NULL`.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework volá tuto metodu, když uživatel klikne na tlačítko pin přepnout podokně lze ukotvit autohide – režimu nebo regulární ukotvení režimu.  
  
 Voláním této metody lze přepnout lze ukotvit podokně autohide – režimu prostřednictvím kódu programu. V podokně musí být ukotvena hlavního okna rámce ( [CDockablePane::GetDefaultPaneDivider](#getdefaultpanedivider) musí vrátit platný ukazatel [CPaneDivider](../../mfc/reference/cpanedivider-class.md)).  
  
##  <a name="setautohideparents"></a>CDockablePane::SetAutoHideParents  
 Nastaví automaticky skrýt tlačítko a automatické skrytí panelu nástrojů pro podokně.  
  
```  
void SetAutoHideParents(
    CMFCAutoHideBar* pToolBar,  
    CMFCAutoHideButton* pBtn);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pToolBar`  
 Ukazatel na panelu nástrojů automaticky skrýt.  
  
 [v]`pBtn`  
 Ukazatel na automaticky skrýt tlačítko.  
  
##  <a name="setlastpercentinpanecontainer"></a>CDockablePane::SetLastPercentInPaneContainer  
 Nastaví v procentech místa, které zabírá podokno v jeho kontejneru.  
  
```  
void SetLastPercentInPaneContainer(int n);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`n`  
 `int` Určující procento místa, které v podokně zabírá v jeho kontejneru.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework upraví podokno novou hodnotu použijte, pokud je přepočítat rozložení.  
  
##  <a name="setrestoreddefaultpanedivider"></a>CDockablePane::SetRestoredDefaultPaneDivider  
 Nastaví dělicí podokně obnovené výchozí.  
  
```  
void SetRestoredDefaultPaneDivider(HWND hRestoredSlider);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`hRestoredSlider`  
 Popisovač na podokně oddělovač (posuvníku).  
  
### <a name="remarks"></a>Poznámky  
 Na podokně příčku obnovené výchozí je získán při podokno je deserializovat. Další informace najdete v tématu [CDockablePane::RestoreDefaultPaneDivider](#restoredefaultpanedivider).  
  
##  <a name="settabbedpanertc"></a>CDockablePane::SetTabbedPaneRTC  
 Nastaví informace o třídě modulu runtime pro okno s kartami, která se vytvoří při dvě podokna ukotvení společně.  
  
```  
void SetTabbedPaneRTC(CRuntimeClass* pRTC);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pRTC`  
 Informace třída modulu runtime pro podokno s kartami.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu a nastavit informace o třídě modulu runtime pro záložkách podokna, které vytvářejí dynamicky. Tato situace může nastat, když uživatel nastavuje tažením jeden podokně na titulek jiného podokna, nebo když zavoláte [CDockablePane::AttachToTabWnd](#attachtotabwnd) metoda prostřednictvím kódu programu vytvořte záložkách podokně z dvě podokna lze ukotvit.  
  
 Výchozí modul runtime třídy je nastaven podle požadavků `dwTabbedStyle` parametr [CDockablePane::Create](#create) a [CDockablePane::CreateEx](#createex). Chcete-li přizpůsobit nových záložkách podokna, odvozena třídě z jednoho z následujících tříd:  
  
- [CBaseTabbedPane – třída](../../mfc/reference/cbasetabbedpane-class.md)  
  
- [CTabbedPane – třída](../../mfc/reference/ctabbedpane-class.md)  
  
- [Třída CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md).  
  
 Potom volejte tuto metodu s má ukazatel na jeho informace o třídě modulu runtime.  
  
##  <a name="showpane"></a>CDockablePane::ShowPane  
 Zobrazit nebo skrýt podokno.  
  
```  
virtual void ShowPane(
    BOOL bShow,  
    BOOL bDelay,  
    BOOL bActivate);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bShow`  
 `TRUE`k zobrazení podokna. `FALSE` ke skrytí podokna.  
  
 [v]`bDelay`  
 `TRUE`Chcete-li odložit úpravě ukotvení rozložení; `FALSE` upravit ukotvení rozložení okamžitě.  
  
 [v]`bActivate`  
 `TRUE`Chcete-li aktivovat podokna při vidět; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Volat tuto metodu místo [CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow) zobrazení nebo skrytí podokna lze ukotvit.  
  
##  <a name="slide"></a>CDockablePane::Slide  
 Animuje podokně, který je v režimu automaticky skrývat.  
  
```  
virtual void Slide(
    BOOL bSlideOut,  
    BOOL bUseTimer = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bSlideOut`  
 `TRUE`k zobrazení podokna. `FALSE` ke skrytí podokna.  
  
 [v]`bUseTimer`  
 `TRUE`Chcete-li zobrazit nebo skrýt podokno s autohide – účinek; `FALSE` zobrazit nebo skrýt podokno okamžitě.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu za účelem animace podokně, který je v režimu autohide – volá framework.  
  
 Tato metoda používá `CDockablePane::m_nSlideDefaultTimeOut` hodnotu, která určí vypršení časového limitu pro efekt snímky. Výchozí hodnota pro vypršení časového limitu je 1. Pokud upravíte autohide – algoritmus, upravte tento člen, chcete-li změnit časový limit.  
  
##  <a name="toggleautohide"></a>CDockablePane::ToggleAutoHide  
 Přepne podokno mezi vždy viditelné a automaticky skrýt režimu.  
  
```  
virtual void ToggleAutoHide();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přepíná automaticky skrýt režim pro podokně voláním [CDockablePane::SetAutoHideMode](#setautohidemode).  
  
##  <a name="undockpane"></a>CDockablePane::UndockPane  
 Předchozího podokna z hlavního okna rámce nebo kontejner miniframe okno.  
  
```  
virtual void UndockPane(BOOL bDelay = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bDelay`  
 `TRUE`Chcete-li odložit výpočet ukotvení rozložení; `FALSE` přepočítat rozložení ukotvení okamžitě.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu za účelem zrušení ukotvení podokně z hlavního okna rámce nebo kontejner okno více miniframe (podokno, který je v okně jednoho miniframe s další podokna plovoucí).  
  
 Podokno musí vyjmutím před provedením všechny externí operace, které se provádí pomocí [CDockingManager](../../mfc/reference/cdockingmanager-class.md). Například musí vyjmutím podokně ho přesunout prostřednictvím kódu programu z jednoho umístění do druhého.  
  
 Rozhraní framework automaticky předchozího podokna před jejich zničena.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CPane – třída](../../mfc/reference/cpane-class.md)
