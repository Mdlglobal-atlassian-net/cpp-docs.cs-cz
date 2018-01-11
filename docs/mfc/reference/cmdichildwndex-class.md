---
title: "Třída CMDIChildWndEx | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMDIChildWndEx
- AFXMDICHILDWNDEX/CMDIChildWndEx
- AFXMDICHILDWNDEX/CMDIChildWndEx::ActivateTopLevelFrame
- AFXMDICHILDWNDEX/CMDIChildWndEx::AddPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::AddTabbedPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::AdjustDockingLayout
- AFXMDICHILDWNDEX/CMDIChildWndEx::CanShowOnMDITabs
- AFXMDICHILDWNDEX/CMDIChildWndEx::CanShowOnTaskBarTabs
- AFXMDICHILDWNDEX/CMDIChildWndEx::CanShowOnWindowsList
- AFXMDICHILDWNDEX/CMDIChildWndEx::DockPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::DockPaneLeftOf
- AFXMDICHILDWNDEX/CMDIChildWndEx::EnableAutoHidePanes
- AFXMDICHILDWNDEX/CMDIChildWndEx::EnableDocking
- AFXMDICHILDWNDEX/CMDIChildWndEx::EnableTaskbarThumbnailClipRect
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetDockingManager
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetDocumentName
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetFrameIcon
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetFrameText
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetRelatedTabGroup
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetTabbedPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetTabProxyWnd
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetTaskbarPreviewWnd
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetTaskbarThumbnailClipRect
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetToolbarButtonToolTipText
- AFXMDICHILDWNDEX/CMDIChildWndEx::InsertPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::InvalidateIconicBitmaps
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsPointNearDockSite
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsReadOnly
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsRegisteredWithTaskbarTabs
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsTabbedPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsTaskbarTabsSupportEnabled
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsTaskbarThumbnailClipRectEnabled
- AFXMDICHILDWNDEX/CMDIChildWndEx::m_dwDefaultTaskbarTabPropertyFlags
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnGetIconicLivePreviewBitmap
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnGetIconicThumbnail
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnMoveMiniFrame
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnPressTaskbarThmbnailCloseButton
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnSetPreviewMode
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnTaskbarTabThumbnailActivate
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnTaskbarTabThumbnailMouseActivate
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnTaskbarTabThumbnailStretch
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnUpdateFrameTitle
- AFXMDICHILDWNDEX/CMDIChildWndEx::PaneFromPoint
- AFXMDICHILDWNDEX/CMDIChildWndEx::RecalcLayout
- AFXMDICHILDWNDEX/CMDIChildWndEx::RegisterTaskbarTab
- AFXMDICHILDWNDEX/CMDIChildWndEx::RemovePaneFromDockManager
- AFXMDICHILDWNDEX/CMDIChildWndEx::SetRelatedTabGroup
- AFXMDICHILDWNDEX/CMDIChildWndEx::SetTaskbarTabActive
- AFXMDICHILDWNDEX/CMDIChildWndEx::SetTaskbarTabOrder
- AFXMDICHILDWNDEX/CMDIChildWndEx::SetTaskbarTabProperties
- AFXMDICHILDWNDEX/CMDIChildWndEx::SetTaskbarThumbnailClipRect
- AFXMDICHILDWNDEX/CMDIChildWndEx::ShowPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::UnregisterTaskbarTab
- AFXMDICHILDWNDEX/CMDIChildWndEx::UpdateTaskbarTabIcon
dev_langs: C++
helpviewer_keywords:
- CMDIChildWndEx [MFC], ActivateTopLevelFrame
- CMDIChildWndEx [MFC], AddPane
- CMDIChildWndEx [MFC], AddTabbedPane
- CMDIChildWndEx [MFC], AdjustDockingLayout
- CMDIChildWndEx [MFC], CanShowOnMDITabs
- CMDIChildWndEx [MFC], CanShowOnTaskBarTabs
- CMDIChildWndEx [MFC], CanShowOnWindowsList
- CMDIChildWndEx [MFC], DockPane
- CMDIChildWndEx [MFC], DockPaneLeftOf
- CMDIChildWndEx [MFC], EnableAutoHidePanes
- CMDIChildWndEx [MFC], EnableDocking
- CMDIChildWndEx [MFC], EnableTaskbarThumbnailClipRect
- CMDIChildWndEx [MFC], GetDockingManager
- CMDIChildWndEx [MFC], GetDocumentName
- CMDIChildWndEx [MFC], GetFrameIcon
- CMDIChildWndEx [MFC], GetFrameText
- CMDIChildWndEx [MFC], GetPane
- CMDIChildWndEx [MFC], GetRelatedTabGroup
- CMDIChildWndEx [MFC], GetTabbedPane
- CMDIChildWndEx [MFC], GetTabProxyWnd
- CMDIChildWndEx [MFC], GetTaskbarPreviewWnd
- CMDIChildWndEx [MFC], GetTaskbarThumbnailClipRect
- CMDIChildWndEx [MFC], GetToolbarButtonToolTipText
- CMDIChildWndEx [MFC], InsertPane
- CMDIChildWndEx [MFC], InvalidateIconicBitmaps
- CMDIChildWndEx [MFC], IsPointNearDockSite
- CMDIChildWndEx [MFC], IsReadOnly
- CMDIChildWndEx [MFC], IsRegisteredWithTaskbarTabs
- CMDIChildWndEx [MFC], IsTabbedPane
- CMDIChildWndEx [MFC], IsTaskbarTabsSupportEnabled
- CMDIChildWndEx [MFC], IsTaskbarThumbnailClipRectEnabled
- CMDIChildWndEx [MFC], m_dwDefaultTaskbarTabPropertyFlags
- CMDIChildWndEx [MFC], OnGetIconicLivePreviewBitmap
- CMDIChildWndEx [MFC], OnGetIconicThumbnail
- CMDIChildWndEx [MFC], OnMoveMiniFrame
- CMDIChildWndEx [MFC], OnPressTaskbarThmbnailCloseButton
- CMDIChildWndEx [MFC], OnSetPreviewMode
- CMDIChildWndEx [MFC], OnTaskbarTabThumbnailActivate
- CMDIChildWndEx [MFC], OnTaskbarTabThumbnailMouseActivate
- CMDIChildWndEx [MFC], OnTaskbarTabThumbnailStretch
- CMDIChildWndEx [MFC], OnUpdateFrameTitle
- CMDIChildWndEx [MFC], PaneFromPoint
- CMDIChildWndEx [MFC], RecalcLayout
- CMDIChildWndEx [MFC], RegisterTaskbarTab
- CMDIChildWndEx [MFC], RemovePaneFromDockManager
- CMDIChildWndEx [MFC], SetRelatedTabGroup
- CMDIChildWndEx [MFC], SetTaskbarTabActive
- CMDIChildWndEx [MFC], SetTaskbarTabOrder
- CMDIChildWndEx [MFC], SetTaskbarTabProperties
- CMDIChildWndEx [MFC], SetTaskbarThumbnailClipRect
- CMDIChildWndEx [MFC], ShowPane
- CMDIChildWndEx [MFC], UnregisterTaskbarTab
- CMDIChildWndEx [MFC], UpdateTaskbarTabIcon
ms.assetid: d39fec06-0bd6-4271-917d-35aae3b24d8e
caps.latest.revision: "35"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 21b302c14d2b4aa17b2818e489a1400230332521
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmdichildwndex-class"></a>CMDIChildWndEx – třída
`CMDIChildWndEx` Třída poskytuje funkci systému Windows více dokumentů (MDI) rozhraní podřízeného okna. Ji rozšiřuje funkce [CMDIChildWnd – třída](../../mfc/reference/cmdichildwnd-class.md). Rozhraní framework vyžaduje tato třída, pokud aplikace MDI používá některých tříd MFC.  
 
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  

  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMDIChildWndEx : public CMDIChildWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMDIChildWndEx::ActivateTopLevelFrame](#activatetoplevelframe)|Volá se interně rámcem aktivovat nejvyšší úrovně rámce, když aplikace by měl být aktivován z panelu karty.|  
|`CMDIChildWndEx::AddDockSite`|Tato metoda není použít nebo implementovat.|  
|[CMDIChildWndEx::AddPane](#addpane)|Přidá do podokna.|  
|[CMDIChildWndEx::AddTabbedPane](#addtabbedpane)|Přidá podokno s kartami.|  
|[CMDIChildWndEx::AdjustDockingLayout](#adjustdockinglayout)|Upraví rozložení ukotvení.|  
|[CMDIChildWndEx::CanShowOnMDITabs](#canshowonmditabs)||  
|[CMDIChildWndEx::CanShowOnTaskBarTabs](#canshowontaskbartabs)|Informuje rozhraní, jestli tento podřízeného MDI mohou být zobrazeny na kartách panelu Windows 7.|  
|[CMDIChildWndEx::CanShowOnWindowsList](#canshowonwindowslist)|Vrátí `TRUE` Pokud název okna MDI podřízené lze zobrazit v [CMFCWindowsManagerDialog třída](../../mfc/reference/cmfcwindowsmanagerdialog-class.md) dialogové okno. V opačném případě vrátí `FALSE`.|  
|`CMDIChildWndEx::CreateObject`|Voláno rámcem k vytvoření dynamických instance tohoto typu třídy.|  
|[CMDIChildWndEx::DockPane](#dockpane)|Ukotvené podokno.|  
|[CMDIChildWndEx::DockPaneLeftOf](#dockpaneleftof)|Ukotvené jeden podokně nalevo od jiného podokna.|  
|[CMDIChildWndEx::EnableAutoHidePanes](#enableautohidepanes)|Umožňuje automaticky skrýt režim pro podokna při jsou ukotvení v zadané okraje okna.|  
|[CMDIChildWndEx::EnableDocking](#enabledocking)|Umožňuje ukotvení z podřízeného okna do hlavního rámce.|  
|[CMDIChildWndEx::EnableTaskbarThumbnailClipRect](#enabletaskbarthumbnailcliprect)|Povolí nebo zakáže automatický výběr část časového období klientské oblasti zobrazuje jako miniaturu tohoto okna na hlavním panelu.|  
|[CMDIChildWndEx::GetDockingManager](#getdockingmanager)||  
|[CMDIChildWndEx::GetDocumentName](#getdocumentname)|Vrací název dokumentu, který se zobrazí v okně podřízeného MDI.|  
|[CMDIChildWndEx::GetFrameIcon](#getframeicon)|Voláno rámcem načíst na ikonu podřízených oken MDI.|  
|[CMDIChildWndEx::GetFrameText](#getframetext)|Voláno rámcem k získání textu pro podřízené okna MDI.|  
|[CMDIChildWndEx::GetPane](#getpane)|Vyhledá podokně podle ID ovládací prvek.|  
|[CMDIChildWndEx::GetRelatedTabGroup](#getrelatedtabgroup)||  
|[CMDIChildWndEx::GetTabbedPane](#gettabbedpane)|Vrací ukazatel na vložené ukotvení podokně, který byl převeden na dokumentů s kartami.|  
|[CMDIChildWndEx::GetTabProxyWnd](#gettabproxywnd)|Vrátí kartě proxy okno, ve skutečnosti registrovány na kartách panelu Windows 7.|  
|[CMDIChildWndEx::GetTaskbarPreviewWnd](#gettaskbarpreviewwnd)|Voláno rámcem, pokud je potřeba získat podřízeného okna (obvykle okno zobrazení nebo rozdělovače) zobrazený na miniaturu karta hlavního panelu Windows 7.|  
|[CMDIChildWndEx::GetTaskbarThumbnailClipRect](#gettaskbarthumbnailcliprect)|Voláno rámcem, pokud je nutné vybrat část časového období klientské oblasti zobrazuje jako miniaturu tohoto okna na hlavním panelu.|  
|`CMDIChildWndEx::GetThisClass`|Voláno rámcem k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený tento typ třídy.|  
|[CMDIChildWndEx::GetToolbarButtonToolTipText](#gettoolbarbuttontooltiptext)|Voláno rámcem načíst popis tlačítka pro tlačítko panelu nástrojů.|  
|[CMDIChildWndEx::InsertPane](#insertpane)|Zaregistruje zadané podokně se správce ukotvení.|  
|[CMDIChildWndEx::InvalidateIconicBitmaps](#invalidateiconicbitmaps)|Zruší platnost reprezentace podřízeného MDI ikony rastrového obrázku.|  
|[CMDIChildWndEx::IsPointNearDockSite](#ispointneardocksite)|Určuje, zda zadaný bod je téměř webu ukotvení.|  
|[CMDIChildWndEx::IsReadOnly](#isreadonly)|Vrátí `TRUE` Pokud dokument, který se zobrazí v okně podřízené je jen pro čtení. V opačném případě vrátí `FALSE`.|  
|[CMDIChildWndEx::IsRegisteredWithTaskbarTabs](#isregisteredwithtaskbartabs)|Vrátí hodnotu TRUE, pokud podřízeného MDI byl úspěšně zaregistrován karty hlavního panelu Windows 7.|  
|[CMDIChildWndEx::IsTabbedPane](#istabbedpane)|Vrátí `TRUE` Pokud podřízeného okna MDI obsahuje ukotvené podokno. V opačném případě vrátí `FALSE`.|  
|[CMDIChildWndEx::IsTaskbarTabsSupportEnabled](#istaskbartabssupportenabled)|Určuje, zda podřízeného MDI můžete zobrazit na kartách panelu Windows 7.|  
|[CMDIChildWndEx::IsTaskbarThumbnailClipRectEnabled](#istaskbarthumbnailcliprectenabled)|Určuje, zda je povoleno automatické volby část časového období klientské oblasti zobrazuje jako miniaturu tohoto okna na hlavním panelu.|  
|[CMDIChildWndEx::m_dwDefaultTaskbarTabPropertyFlags](#m_dwdefaulttaskbartabpropertyflags)|Kombinace příznaků, která se předá rámcem SetTaskbarTabProperties metodu, když na kartě (podřízeného MDI) registrované s kartami hlavního panelu Windows 7. Kombinace výchozí je STPF_USEAPPTHUMBNAILWHENACTIVE &#124; STPF_USEAPPPEEKWHENACTIVE.|  
|[CMDIChildWndEx::OnGetIconicLivePreviewBitmap](#ongeticoniclivepreviewbitmap)|Voláno rámcem, pokud je nutné získat rastrový obrázek živém náhledu podřízeného MDI.|  
|[CMDIChildWndEx::OnGetIconicThumbnail](#ongeticonicthumbnail)|Voláno rámcem, pokud je nutné získat rastrový obrázek ikony miniaturu podřízeného MDI.|  
|[CMDIChildWndEx::OnMoveMiniFrame](#onmoveminiframe)|Voláno rámcem k přesunutí zkrácená rámce okna.|  
|[CMDIChildWndEx::OnPressTaskbarThmbnailCloseButton](#onpresstaskbarthmbnailclosebutton)|Voláno rámcem, když uživatel stiskne tlačítko Zavřít na hlavním panelu karta miniaturu...|  
|[CMDIChildWndEx::OnSetPreviewMode](#onsetpreviewmode)|Voláno rámcem zadejte nebo ukončit režim náhledu tisku.|  
|[CMDIChildWndEx::OnTaskbarTabThumbnailActivate](#ontaskbartabthumbnailactivate)|Voláno rámcem, pokud by měl zpracovat zprávu WM_ACTIVATE, karta miniaturu panelu.|  
|[CMDIChildWndEx::OnTaskbarTabThumbnailMouseActivate](#ontaskbartabthumbnailmouseactivate)|Voláno rámcem, pokud by měl zpracovat zprávu WM_MOUSEACTIVATE, karta miniaturu panelu.|  
|[CMDIChildWndEx::OnTaskbarTabThumbnailStretch](#ontaskbartabthumbnailstretch)|Voláno rámcem, když potřebuje k roztahování rastrový obrázek pro Windows 7 panelu karta náhled této podřízeného MDI.|  
|[CMDIChildWndEx::OnUpdateFrameTitle](#onupdateframetitle)|Voláno rámcem aktualizovat název rámce. (Přepisuje `CMDIChildWnd::OnUpdateFrameTitle`.)|  
|[CMDIChildWndEx::PaneFromPoint](#panefrompoint)|Vrátí panel, který obsahuje danému bodu.|  
|`CMDIChildWndEx::PreTranslateMessage`|Používá třída [CWinApp](../../mfc/reference/cwinapp-class.md) přeložit zprávy oken, než jsou odeslány do [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) a [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funkce systému Windows. (Přepisuje [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|  
|[CMDIChildWndEx::RecalcLayout](#recalclayout)|Přepočítá rozložení okna.|  
|[CMDIChildWndEx::RegisterTaskbarTab](#registertaskbartab)|Zaregistruje podřízeného MDI karty hlavního panelu Windows 7.|  
|[CMDIChildWndEx::RemovePaneFromDockManager](#removepanefromdockmanager)|Podokno odebere správce ukotvení.|  
|[CMDIChildWndEx::SetRelatedTabGroup](#setrelatedtabgroup)||  
|[CMDIChildWndEx::SetTaskbarTabActive](#settaskbartabactive)|Aktivuje odpovídající kartě hlavního panelu Windows 7.|  
|[CMDIChildWndEx::SetTaskbarTabOrder](#settaskbartaborder)|Vloží podřízeného MDI před vybrané okno na kartách panelu Windows 7.|  
|[CMDIChildWndEx::SetTaskbarTabProperties](#settaskbartabproperties)|Nastaví vlastnosti na kartě hlavního panelu Windows 7.|  
|[CMDIChildWndEx::SetTaskbarThumbnailClipRect](#settaskbarthumbnailcliprect)|Volá se interně rámcem nastavit výstřižek obdélníku vybrat části časového období klientské oblasti zobrazuje jako miniaturu tohoto okna na hlavním panelu.|  
|[CMDIChildWndEx::ShowPane](#showpane)||  
|[CMDIChildWndEx::UnregisterTaskbarTab](#unregistertaskbartab)|Odebere podřízeného MDI z karty hlavního panelu Windows 7.|  
|[CMDIChildWndEx::UpdateTaskbarTabIcon](#updatetaskbartabicon)|Aktualizuje ikonu Karta hlavního panelu Windows 7.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud chcete využít výhod funkce Rozšířené ukotvení v aplikace MDI, odvodíte třídu okno podřízeného MDI aplikace `CMDIChildWndEx` místo [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je odvozena z třídy `CMDIChildWndEx`. Tento fragment kódu pochází z [VisualStudioDemo ukázka: MFC Visual Studio Application](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#3](../../mfc/codesnippet/cpp/cmdichildwndex-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)  
  
 [CMDIChildWndEx](../../mfc/reference/cmdichildwndex-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxMDIChildWndEx.h  
  
##  <a name="addpane"></a>CMDIChildWndEx::AddPane  
 Přidá do podokna.  
  
```  
BOOL AddPane(
    CBasePane* pControlBar,  
    BOOL bTail = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pControlBar`  
 Ukazatel na podokně.  
  
 [v]`bTail`  
 `TRUE`Chcete-li přidat v podokně na konec seznamu podokna pro ukotvení správce; v opačném `FALSE`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud v podokně byl úspěšně zaregistrován pomocí ukotvení správce; v opačném `FALSE`.  
  
##  <a name="addtabbedpane"></a>CMDIChildWndEx::AddTabbedPane  
 Přidá podokno s kartami.  
  
```  
void AddTabbedPane(CDockablePane* pControlBar);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pControlBar`  
 Ukazatel na podokně.  
  
##  <a name="adjustdockinglayout"></a>CMDIChildWndEx::AdjustDockingLayout  
 Upraví rozložení ukotvení.  
  
```  
virtual void AdjustDockingLayout(HDWP hdwp = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`hdwp`  
 Popisovač strukturu pozice odložené okna.  
  
##  <a name="canshowonmditabs"></a>CMDIChildWndEx::CanShowOnMDITabs  

  
```  
virtual BOOL CanShowOnMDITabs();
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="canshowonwindowslist"></a>CMDIChildWndEx::CanShowOnWindowsList  
 Určuje, zda název podřízeného okna MDI lze zobrazit v [CMFCWindowsManagerDialog třída](../../mfc/reference/cmfcwindowsmanagerdialog-class.md) dialogové okno.  
  
```  
virtual BOOL CanShowOnWindowsList();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud okno lze zobrazit v **Windows** dialogové okno, jinak hodnota `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu v odvozené třídě a vrátit `FALSE` Pokud okno by se neměly zobrazovat v **Windows** dialogové okno. Tato funkce je volána z `CMFCWindowsManagerDialog`.  
  
##  <a name="dockpane"></a>CMDIChildWndEx::DockPane  
 Ukotvené podokno.  
  
```  
void DockPane(
    CBasePane* pBar,  
    UINT nDockBarID = 0,  
    LPCRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pBar`  
 Ukazatel na podokně.  
  
 [v]`nDockBarID`  
 ID podokně.  
  
 [v]`lpRect`  
 Ukazatel na obdélník.  
  
### <a name="remarks"></a>Poznámky  
 `lpRect` Parametr se nepoužívá.  
  
##  <a name="dockpaneleftof"></a>CMDIChildWndEx::DockPaneLeftOf  
 Ukotvené jeden podokně nalevo od jiného podokna.  
  
```  
BOOL DockPaneLeftOf(
    CPane* pBar,  
    CPane* pLeftOf);
```  
  
### <a name="parameters"></a>Parametry  
 `pBar`  
 Ukazatel na panel, který má být ukotven.  
  
 `pLeftOf`  
 Ukazatel na podokně, která slouží jako bod odkazu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`v případě úspěchu `FALSE` při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přebírá podokně určeného `pBar` a ukotvené v levé části podokna určeného `pLeftOf`.  
  
 Tuto metodu volejte, když chcete ukotvení několika podoken v předdefinované pořadí.  
  
##  <a name="enableautohidepanes"></a>CMDIChildWndEx::EnableAutoHidePanes  
 Umožňuje automaticky skrýt režim pro podokna při jsou ukotvení v zadané okraje okna.  
  
```  
BOOL EnableAutoHidePanes(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`dwDockStyle`  
 Určuje postranní okna hlavního rámce, který je povolený. Použijte jeden nebo více z následujících příznaků.  
  
- `CBRS_ALIGN_LEFT`  
  
- `CBRS_ALIGN_RIGHT`  
  
- `CBRS_ALIGN_TOP`  
  
- `CBRS_ALIGN_BOTTOM`  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud metoda úspěšně. v opačném případě `FALSE`.  
  
##  <a name="enabledocking"></a>CMDIChildWndEx::EnableDocking  
 Umožňuje ukotvení z podřízeného okna do hlavního rámce.  
  
```  
BOOL EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`dwDockStyle`  
 Určuje zarovnání ukotvení povolit.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud metoda úspěšně. v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu za účelem povolení ukotvení zarovnání do hlavního rámce. Můžete předat kombinaci CBRS_ALIGN_ příznaky (Další informace najdete v tématu [CControlBar::EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking)).  
  
##  <a name="getdockingmanager"></a>CMDIChildWndEx::GetDockingManager  

  
```  
CDockingManager* GetDockingManager();
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getdocumentname"></a>CMDIChildWndEx::GetDocumentName  
 Vrací název dokumentu, který se zobrazí v okně podřízeného MDI.  
  
```  
virtual LPCTSTR GetDocumentName(CObject** pObj);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na řetězec, který obsahuje název dokumentu.  
  
### <a name="remarks"></a>Poznámky  
 Dokument je co podřízeného okna MDI zobrazí. Obecně platí v okně se zobrazí data, která je načten z nebo uloží do souboru. Název dokumentu, proto je název souboru. Výchozí implementaci `GetDocumentName` vrátí řetězec získané z `CDocument::GetPathName`.  
  
 Pokud v okně se zobrazí dokument, který není načtený ze souboru, přepište tuto metodu v odvozené třídě a vrátí dokumentu jedinečný identifikátor.  
  
 `GetDocumentName`je voláno rámcem, když ho uloží stav všechny otevřené dokumenty. Vrácený řetězec je zapsán do registru.  
  
 Když rozhraní je obnovení novější stavu, je název dokumentu přečíst z registru a předaný [CMDIFrameWndEx::CreateDocumentWindow](../../mfc/reference/cmdiframewndex-class.md#createdocumentwindow). Potlačí tuto metodu v [CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md)-odvozené třídy a vytvořit nebo otevřít dokument, který má tento název a přečtěte si v souboru, který má tento název. Není-li u souboru dokumentu, vytvoření dokumentu, na základě identifikátoru dokumentu sám sebe. Pouze v případě, že máte v úmyslu uložení a obnovení dokumenty, měli byste udělat předchozí akce.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje použití `GetDocumentName` metoda. Tento fragment kódu pochází z [VisualStudioDemo ukázka: MFC Visual Studio Application](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#17](../../mfc/codesnippet/cpp/cmdichildwndex-class_2.cpp)]  
  
##  <a name="getframeicon"></a>CMDIChildWndEx::GetFrameIcon  
 Voláno rámcem načíst ikonu podřízeného okna MDI.  
  
```  
virtual HICON GetFrameIcon() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro ikonu okno.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána rámcem určit jaké ikonu zobrazíte na kartě MDI obsahující MDI podřízeného rámce okna.  
  
 Ve výchozím nastavení tato metoda vrátí ikonu okno. Přepsání `GetFrameIcon` v `CMDIChildWndEx`-odvozené třídy, chcete-li přizpůsobit toto chování.  
  
##  <a name="getframetext"></a>CMDIChildWndEx::GetFrameText  
 Voláno rámcem k získání textu pro podřízené okna MDI.  
  
```  
virtual CString GetFrameText() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Řetězec, který obsahuje text rámce okna.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána rámcem rozhodnout, jaký text, který se zobrazí na kartě MDI, který obsahuje podřízeného rámce okna MDI.  
  
 Ve výchozím nastavení tato metoda vrátí text okna. Přepsání `GetFrameText` v `CMDIChildWndEx`-odvozené třídy, chcete-li přizpůsobit toto chování.  
  
##  <a name="getpane"></a>CMDIChildWndEx::GetPane  
 Vyhledá podokně podle ID ovládací prvek.  
  
```  
CBasePane* GetPane(UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nID`  
 ID ovládacího prvku v podokně k vyhledání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na podokně-li nalezena, jinak `NULL`.  
  
##  <a name="getrelatedtabgroup"></a>CMDIChildWndEx::GetRelatedTabGroup  

  
```  
CMFCTabCtrl* GetRelatedTabGroup();
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="gettabbedpane"></a>CMDIChildWndEx::GetTabbedPane  
 Vrátí – ukazatel na ukotvení podokně, která je součástí skupiny MDI se záložkami dokumenty.  
  
```  
CDockablePane* GetTabbedPane() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na ukotvení podokně, která je součástí skupiny MDI dokumenty na kartách.  
  
##  <a name="gettoolbarbuttontooltiptext"></a>CMDIChildWndEx::GetToolbarButtonToolTipText  
 Voláno rámcem načíst popis tlačítka pro tlačítko panelu nástrojů.  
  
```  
virtual BOOL GetToolbarButtonToolTipText(
    CMFCToolBarButton*, 
    CString&);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud je zobrazené v popisku. Výchozí implementace vrací `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu, pokud chcete zobrazit vlastní popisy pro tlačítka panelu nástrojů.  
  
##  <a name="insertpane"></a>CMDIChildWndEx::InsertPane  
 Zaregistruje zadané podokně se správce ukotvení.  
  
```  
BOOL InsertPane(
    CBasePane* pControlBar,  
    CBasePane* pTarget,  
    BOOL bAfter = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pControlBar`  
 Ukazatel na podokně Vložit.  
  
 [v]`pTarget`  
 Ukazatel na sousedících podokně.  
  
 [v]`bAfter`  
 Pokud `TRUE`, `pControlBar` vkládají `pTarget`. Pokud `FALSE`, `pControlBar` je vložen před `pTarget`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud metoda bude úspěšná, `FALSE` jinak.  
  
##  <a name="ispointneardocksite"></a>CMDIChildWndEx::IsPointNearDockSite  
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
  
 [v]`dwBarAlignment`  
 Určuje, které hraniční bod je téměř. Možné hodnoty jsou `CBRS_ALIGN_LEFT`, `CBRS_ALIGN_RIGHT`, `CBRS_ALIGN_TOP`, a`CBRS_ALIGN_BOTTOM`  
  
 [v]`bOuterEdge`  
 `TRUE`Pokud je bod téměř vnější ohraničení ukotvení serveru. `FALSE` jinak.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud je bod téměř webu ukotvení; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Bod je blízko ukotvení lokality, pokud je v rámci velkých a malých písmen, nastavte v správce ukotvení. Výchozí citlivosti je 15 pixelů.  
  
##  <a name="isreadonly"></a>CMDIChildWndEx::IsReadOnly  
 Určuje, zda dokument, který se zobrazí v okně podřízené je jen pro čtení.  
  
```  
virtual BOOL IsReadOnly();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud dokument je jen pro čtení; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce se používá při prevenci ukládání dokumentů jen pro čtení.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje přepsání `IsReadOnly` metoda. Tento fragment kódu pochází z [VisualStudioDemo ukázka: MFC Visual Studio Application](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#2](../../mfc/codesnippet/cpp/cmdichildwndex-class_3.cpp)]  
  
##  <a name="istabbedpane"></a>CMDIChildWndEx::IsTabbedPane  
 Určuje, zda podřízeného okna MDI obsahuje ukotvené podokno.  
  
```  
BOOL IsTabbedPane() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud podřízeného okna MDI obsahuje ukotvení podokno, v němž byl převeden na záložkách dokumentu. v opačném případě `FALSE`.  
  
##  <a name="onmoveminiframe"></a>CMDIChildWndEx::OnMoveMiniFrame  
 Voláno rámcem k přesunutí zkrácená rámce okna.  
  
```  
virtual BOOL OnMoveMiniFrame(CWnd* pFrame);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pFrame`  
 Ukazatel na zkrácená rámce okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud metoda úspěšné, jinak `FALSE`.  
  
##  <a name="onsetpreviewmode"></a>CMDIChildWndEx::OnSetPreviewMode  
 Voláno rámcem zadejte nebo ukončit režim náhledu tisku.  
  
```  
virtual void OnSetPreviewMode(
    BOOL bPreview,  
    CPrintPreviewState* pState);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bPreview`  
 Pokud `TRUE`, zadejte režim náhledu. Pokud `FALSE`, ukončit režim náhledu tisku.  
  
 [v]`pState`  
 Ukazatel na strukturu stavu náhledu tisku.  
  
##  <a name="onupdateframetitle"></a>CMDIChildWndEx::OnUpdateFrameTitle  
 Voláno rámcem aktualizovat název rámce.  
  
```  
virtual void OnUpdateFrameTitle(BOOL bAddToTitle);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bAddToTitle`  
 Pokud `TRUE`, přidejte název dokumentu na název.  
  
##  <a name="panefrompoint"></a>CMDIChildWndEx::PaneFromPoint  
 Vrátí panel, který obsahuje danému bodu.  
  
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
 [v]`point`  
 Určuje bod, v souřadnice obrazovky ke kontrole.  
  
 [v]`nSensitivity`  
 Toto množství zvýšit oblasti hledání. Podokno splňuje kritéria hledání, pokud danému bodu spadá do oblasti vyšší.  
  
 [v]`bExactBar`  
 `TRUE`Ignorovat `nSensitivity` parametr, jinak hodnota `FALSE`.  
  
 [v]`pRTCBarType`  
 Není-li `NULL`, tato metoda vyhledá pouze podokna zadaného typu.  
  
 [v]`dwAlignment`  
 Pokud podokno se nachází zde zadaný bod, tento parametr obsahuje na straně panelu, který je nejblíže k Zadaný bod. Další informace najdete v části poznámky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `CBasePane`-odvozené objekt, který obsahuje danému bodu nebo `NULL` Pokud nebyl nalezen žádný podokně.  
  
### <a name="remarks"></a>Poznámky  
 Voláním této metody lze zjistit, zda podokno obsahuje zadaný bod podle k zadaným podmínkám, jako je například třída runtime a viditelnosti.  
  
 Když funkce vrátí hodnotu a byla nalezena podokno, `dwAlignment` obsahuje zarovnání Zadaný bod. Například, pokud byl bod nejblíže k horní části podokna `dwAlignment` je nastaven na `CBRS_ALIGN_TOP`.  
  
##  <a name="recalclayout"></a>CMDIChildWndEx::RecalcLayout  
 Přepočítá rozložení okna.  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bNotify`  
 Pokud `TRUE`, aktivní položky na místě pro okno obdrží upozornění na změnu rozložení.  
  
##  <a name="removepanefromdockmanager"></a>CMDIChildWndEx::RemovePaneFromDockManager  
 Podokno odebere správce ukotvení.  
  
```  
void RemovePaneFromDockManager(
    CBasePane* pControlBar,  
    BOOL bDestroy,  
    BOOL bAdjustLayout,  
    BOOL bAutoHide,  
    CBasePane* pBarReplacement);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pControlBar`  
 Ukazatel na podokno odebrat.  
  
 [v]`bDestroy`  
 Pokud `TRUE`, odebrané podokně zničena.  
  
 [v]`bAdjustLayout`  
 Pokud `TRUE`, upravte ukotvení rozložení okamžitě.  
  
 [v]`bAutoHide`  
 Pokud `TRUE`, ukotvení rozložení se vztahuje k seznamu autohide – řádky. Pokud `FALSE`, ukotvení rozložení se vztahuje k seznamu regulární podokna.  
  
 [v]`pBarReplacement`  
 Ukazatel na podokně, který nahrazuje podokně odebrané.  
  
##  <a name="setrelatedtabgroup"></a>CMDIChildWndEx::SetRelatedTabGroup  

  
```  
void SetRelatedTabGroup(CMFCTabCtrl* p);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`p`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="showpane"></a>CMDIChildWndEx::ShowPane  

  
```  
void ShowPane(
    CBasePane* pBar,  
    BOOL bShow,  
    BOOL bDelay,  
    BOOL bActivate);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pBar`  
 [v]`bShow`  
 [v]`bDelay`  
 [v]`bActivate`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="updatetaskbartabicon"></a>CMDIChildWndEx::UpdateTaskbarTabIcon  
 Aktualizuje kartu ikona na hlavním panelu Windows 7.  
  
```  
virtual void UpdateTaskbarTabIcon(HICON hIcon);
```  
  
### <a name="parameters"></a>Parametry  
 `hIcon`  
 Popisovač pro ikonu, která se zobrazí na kartě hlavního panelu Windows 7.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="unregistertaskbartab"></a>CMDIChildWndEx::UnregisterTaskbarTab  
 Odebere podřízeného MDI z karty hlavního panelu Windows 7.  
  
```  
void UnregisterTaskbarTab(BOOL bCheckRegisteredMDIChildCount = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bCheckRegisteredMDIChildCount`  
 Určuje, zda tato funkce musí zkontrolovat počet podřízených prvků MDI zaregistrována MDI karty. Pokud toto číslo 0, tato funkce odebere rámeček výstřižek z miniaturu panelu aplikace.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="settaskbarthumbnailcliprect"></a>CMDIChildWndEx::SetTaskbarThumbnailClipRect  
 Voláno rámcem nastavit rámeček výstřižek vybrat části časového období klientské oblasti zobrazuje jako miniaturu tohoto okna na hlavním panelu.  
  
```  
virtual BOOL SetTaskbarThumbnailClipRect(CRect rect);
```  
  
### <a name="parameters"></a>Parametry  
 `rect`  
 Určuje nové výstřižek rámeček. Pokud rámeček je prázdná nebo null, odeberou se výstřižek.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`v případě úspěšného; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="settaskbartabproperties"></a>CMDIChildWndEx::SetTaskbarTabProperties  
 Nastaví vlastnosti na kartě hlavního panelu Windows 7.  
  
```  
void SetTaskbarTabProperties(DWORD dwFlags);
```  
  
### <a name="parameters"></a>Parametry  
 `dwFlags`  
 Kombinace hodnot STPFLAG. Další informace najdete v tématu [ITaskbarList4::SetTabProperties](http://msdn.microsoft.com/library/dd562049\(vs.85\).aspx).  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="settaskbartaborder"></a>CMDIChildWndEx::SetTaskbarTabOrder  
 Vloží podřízeného MDI před zadané okno na kartách panelu Windows 7.  
  
```  
void SetTaskbarTabOrder(CMDIChildWndEx* pWndBefore = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pWndBefore`  
 Ukazatel na podřízeného okna MDI, jejichž miniaturu je vložit do levé straně. Toto okno musí být zaregistrována pomocí `RegisterTaskbarTab`. Pokud je tato hodnota `NULL`, nové miniaturu se přidá na konec seznamu.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="settaskbartabactive"></a>CMDIChildWndEx::SetTaskbarTabActive  
 Aktivuje odpovídající kartě hlavního panelu Windows 7.  
  
```  
void SetTaskbarTabActive();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="registertaskbartab"></a>CMDIChildWndEx::RegisterTaskbarTab  
 Zaregistruje podřízeného MDI karty hlavního panelu Windows 7.  
  
```  
virtual void RegisterTaskbarTab(CMDIChildWndEx* pWndBefore = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pWndBefore`  
 Ukazatel na podřízeného okna MDI, jejichž miniaturu je vložit do levé straně. Toto okno musí být zaregistrována pomocí `RegisterTaskbarTab`. Pokud je tato hodnota `NULL`, nové miniaturu se přidá na konec seznamu.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ontaskbartabthumbnailstretch"></a>CMDIChildWndEx::OnTaskbarTabThumbnailStretch  
 Voláno rámcem, když potřebuje k roztahování rastrový obrázek pro Windows 7 panelu karta náhled této podřízeného MDI.  
  
```  
virtual BOOL OnTaskbarTabThumbnailStretch(
    HBITMAP hBmpDst,  
    const CRect& rectDst,  
    HBITMAP hBmpSrc,  
    const CRect& rectSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `hBmpDst`  
 Popisovač pro rastrový obrázek cílový.  
  
 `rectDst`  
 Určuje cílový rámeček.  
  
 `hBmpSrc`  
 Popisovač pro rastrový obrázek zdroje.  
  
 `rectSrc`  
 Určuje zdroj rámeček.  
  
### <a name="remarks"></a>Poznámky  
 Requirementher nebo mu mu mu mu mu mu mu **:** afxmdichildwndex.h  
  
##  <a name="ontaskbartabthumbnailmouseactivate"></a>CMDIChildWndEx::OnTaskbarTabThumbnailMouseActivate  
 Voláno rámcem, pokud by měl zpracovat zprávu WM_MOUSEACTIVATE, karta miniaturu panelu.  
  
```  
virtual int OnTaskbarTabThumbnailMouseActivate(
    CWnd* pDesktopWnd,  
    UINT nHitTest,  
    UINT message);
```  
  
### <a name="parameters"></a>Parametry  
 `pDesktopWnd`  
 Určuje ukazatel na nejvyšší úrovně nadřazeného okna okna aktivace probíhá. Ukazatele může být v dočasné a by neměly být uloženy.  
  
 `nHitTest`  
 Určuje kód oblasti vstupů do testu. Testu přístupů je test, který určuje umístění kurzoru.  
  
 `message`  
 Určuje číslo zprávy myši.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace aktivuje související rámečku podřízeného MDI.  
  
##  <a name="ontaskbartabthumbnailactivate"></a>CMDIChildWndEx::OnTaskbarTabThumbnailActivate  
 Voláno rámcem, pokud by měl zpracovat zprávu WM_ACTIVATE, karta miniaturu panelu.  
  
```  
virtual void OnTaskbarTabThumbnailActivate(
    UINT nState,  
    CWnd* pWndOther,  
    BOOL bMinimized);
```  
  
### <a name="parameters"></a>Parametry  
 `nState`  
 Určuje, zda `CWnd` je Probíhá aktivace nebo deaktivace.  
  
 `pWndOther`  
 Ukazatel `CWnd` Probíhá aktivace nebo deaktivace. Může být ukazatele `NULL`, a může být dočasné.  
  
 `bMinimized`  
 Určuje minimalizovaném okně Stav `CWnd` Probíhá aktivace nebo deaktivace. Hodnota `TRUE` označuje je minimalizován okna.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace aktivuje související rámečku podřízeného MDI.  
  
##  <a name="onpresstaskbarthmbnailclosebutton"></a>CMDIChildWndEx::OnPressTaskbarThmbnailCloseButton  
 Voláno rámcem, když uživatel na kartě miniaturu panelu stiskne tlačítko Zavřít.  
  
```  
virtual void OnPressTaskbarThmbnailCloseButton();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ongeticonicthumbnail"></a>CMDIChildWndEx::OnGetIconicThumbnail  
 Voláno rámcem, pokud je nutné získat rastrový obrázek ikony miniaturu podřízeného MDI.  
  
```  
virtual HBITMAP OnGetIconicThumbnail(
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>Parametry  
 `nWidth`  
 Určuje šířku požadované rastrového obrázku.  
  
 `nHeight`  
 Určuje výšku požadované rastrového obrázku.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ongeticoniclivepreviewbitmap"></a>CMDIChildWndEx::OnGetIconicLivePreviewBitmap  
 Voláno rámcem, pokud je nutné získat rastrový obrázek živém náhledu podřízeného MDI.  
  
```  
virtual HBITMAP OnGetIconicLivePreviewBitmap(
    BOOL bIsMDIChildActive,  
    CPoint& ptLocation);
```  
  
### <a name="parameters"></a>Parametry  
 `bIsMDIChildActive`  
 Tento parametr je `TRUE` Pokud se pro podřízeného MDI požaduje bitovou mapu, která je aktuálně aktivní a hlavní okno není minimalizovaná. Výchozí zpracování v tomto případě pořídí snímek hlavního okna.  
  
 `ptLocation`  
 Určuje umístění bitmapy v hlavní (nejvyšší úrovně) souřadnice klienta okno. Tento bod by měl být poskytovaný volaného.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud zpracování popisovač na platný 32bpp bitmapu, v opačném případě vrátí `NULL`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu v odvozené třídě a vraťte se platný 32bpp rastrový obrázek živém náhledu podřízeného MDI. Tato metoda je volána, pouze pokud je podřízeného MDI zobrazeny na kartách panelu Windows 7. Pokud vrátíte `NULL`, MFC volá výchozí obslužné rutiny a získá bitmap pomocí `PrintClient` nebo `PrintWindow`.  
  
##  <a name="m_dwdefaulttaskbartabpropertyflags"></a>CMDIChildWndEx::m_dwDefaultTaskbarTabPropertyFlags  
 Kombinace příznaků, je předaná rozhraní k `SetTaskbarTabProperties` metodu, když na kartě (podřízeného MDI) registrované s kartami hlavního panelu Windows 7.  
  
```  
AFX_IMPORT_DATA static DWORD m_dwDefaultTaskbarTabPropertyFlags;  
```  
  
### <a name="remarks"></a>Poznámky  
 Kombinace výchozí je STPF_USEAPPTHUMBNAILWHENACTIVE &#124; STPF_USEAPPPEEKWHENACTIVE.  
  
##  <a name="istaskbarthumbnailcliprectenabled"></a>CMDIChildWndEx::IsTaskbarThumbnailClipRectEnabled  
 Určuje, zda je povoleno automatické volby část časového období klientské oblasti zobrazuje jako miniaturu tohoto okna na hlavním panelu.  
  
```  
BOOL IsTaskbarThumbnailClipRectEnabled() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `TRUE` Pokud automatický výběr část časového období klientské oblasti pro zobrazení je povolené jinak `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="istaskbartabssupportenabled"></a>CMDIChildWndEx::IsTaskbarTabsSupportEnabled  
 Určuje, zda podřízeného MDI můžete zobrazit na kartách panelu Windows 7.  
  
```  
BOOL IsTaskbarTabsSupportEnabled();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud se podřízeného MDI objevit na kartách panelu Windows 7; `FALSE` Pokud podřízeného MDI se nemůže vyskytovat na kartách panelu Windows 7.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isregisteredwithtaskbartabs"></a>CMDIChildWndEx::IsRegisteredWithTaskbarTabs  
 Vrátí `TRUE` Pokud podřízeného MDI byl úspěšně zaregistrován karty hlavního panelu Windows 7.  
  
```  
BOOL IsRegisteredWithTaskbarTabs();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud podřízeného MDI je registrován s kartami hlavního panelu Windows 7; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="invalidateiconicbitmaps"></a>CMDIChildWndEx::InvalidateIconicBitmaps  
 Zruší platnost reprezentaci ikony rastrový obrázek podřízeného MDI.  
  
```  
BOOL InvalidateIconicBitmaps();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `FALSE` Pokud podporu hlavního panelu Windows 7 je zakázán nebo podřízeného MDI není registrován u služby Windows 7 panelu karty; v opačném případě vrátí `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
 By měla být volána, když došlo ke změně živý obsah nebo velikost podřízeného MDI.  
  
##  <a name="gettaskbarthumbnailcliprect"></a>CMDIChildWndEx::GetTaskbarThumbnailClipRect  
 Voláno rámcem, pokud je nutné vybrat část časového období klientské oblasti zobrazuje jako miniaturu tohoto okna na hlavním panelu.  
  
```  
virtual CRect GetTaskbarThumbnailClipRect() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Rámečku v souřadnicích systému windows. Obdélníku, je namapována na klientské oblasti rámečku nejvyšší úrovně. Rámeček by měla být prázdná zrušte výstřižek rámeček.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="gettaskbarpreviewwnd"></a>CMDIChildWndEx::GetTaskbarPreviewWnd  
 Voláno rámcem, pokud je potřeba získat podřízeného okna (obvykle okno zobrazení nebo rozdělovače), který se má zobrazit na kartě miniaturu hlavního panelu Windows 7.  
  
```  
virtual CWnd* GetTaskbarPreviewWnd();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 By měla vrátit platnou ukazatel `CWnd` související objekt, jehož preview se má zobrazit na kartě hlavního panelu Windows 7 se tuto podřízeného MDI. Výchozí implementace vrací podřízeného okna této podřízené jednotky MDI s ID ovládacího prvku AFX_IDW_PANE_FIRST (což je obvykle `CView`-odvozené třídy).  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="gettabproxywnd"></a>CMDIChildWndEx::GetTabProxyWnd  
 Vrátí proxy okno s kartou registrovány na kartách panelu Windows 7.  
  
```  
CMDITabProxyWnd* GetTabProxyWnd();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na `CMDITabProxyWnd` objekt, který je registrován s kartami hlavního panelu Windows 7.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="enabletaskbarthumbnailcliprect"></a>CMDIChildWndEx::EnableTaskbarThumbnailClipRect  
 Povolí nebo zakáže automatický výběr část časového období klientské oblasti zobrazuje jako miniaturu tohoto okna na hlavním panelu.  
  
```  
void EnableTaskbarThumbnailClipRect(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bEnable`  
 Určuje, jestli se má povolit ( `TRUE`), nebo zakázat ( `FALSE`) automatický výběr část časového období klientské oblasti pro zobrazení.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="canshowontaskbartabs"></a>CMDIChildWndEx::CanShowOnTaskBarTabs  
 Informuje rozhraní, jestli tento podřízeného MDI mohou být zobrazeny na kartách panelu Windows 7.  
  
```  
virtual BOOL CanShowOnTaskBarTabs();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud obsah podřízeného MDI lze zobrazit v miniaturách hlavního panelu Windows 7.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu v odvozené třídě a vrátit `FALSE` zakázat vzhled tento podřízeného MDI na kartách panelu Windows 7.  
  
##  <a name="activatetoplevelframe"></a>CMDIChildWndEx::ActivateTopLevelFrame  
 Voláno rámcem aktivovat rámečku nejvyšší úrovně aplikace při aktivaci z panelu karty.  
  
```  
virtual void ActivateTopLevelFrame();
```  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMDIChildWnd – třída](../../mfc/reference/cmdichildwnd-class.md)   
 [CMFCWindowsManagerDialog – třída](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)   
 [CMDIFrameWndEx – třída](../../mfc/reference/cmdiframewndex-class.md)
