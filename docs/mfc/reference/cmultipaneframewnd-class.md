---
title: Třída CMultiPaneFrameWnd | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMultiPaneFrameWnd
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::AddPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::AddRecentPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::AdjustLayout
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::AdjustPaneFrames
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CalcExpectedDockedRect
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CanBeAttached
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CanBeDockedToPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CheckGripperVisibility
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CloseMiniFrame
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::ConvertToTabbedDocument
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::DockFrame
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::DockPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::DockRecentPaneToMainFrame
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetCaptionText
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetPaneContainerManager
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetFirstVisiblePane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetPaneCount
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetVisiblePaneCount
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::InsertPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::LoadState
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnDockToRecentPos
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnKillRollUpTimer
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnPaneRecalcLayout
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnSetRollUpTimer
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnShowPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::PaneFromPoint
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::RemoveNonValidPanes
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::RemovePane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::ReplacePane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::SaveState
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::Serialize
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::SetDockState
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::SetLastFocusedPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::SetPreDockState
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::StoreRecentDockSiteInfo
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::StoreRecentTabRelatedInfo
dev_langs:
- C++
helpviewer_keywords:
- CMultiPaneFrameWnd [MFC], AddPane
- CMultiPaneFrameWnd [MFC], AddRecentPane
- CMultiPaneFrameWnd [MFC], AdjustLayout
- CMultiPaneFrameWnd [MFC], AdjustPaneFrames
- CMultiPaneFrameWnd [MFC], CalcExpectedDockedRect
- CMultiPaneFrameWnd [MFC], CanBeAttached
- CMultiPaneFrameWnd [MFC], CanBeDockedToPane
- CMultiPaneFrameWnd [MFC], CheckGripperVisibility
- CMultiPaneFrameWnd [MFC], CloseMiniFrame
- CMultiPaneFrameWnd [MFC], ConvertToTabbedDocument
- CMultiPaneFrameWnd [MFC], DockFrame
- CMultiPaneFrameWnd [MFC], DockPane
- CMultiPaneFrameWnd [MFC], DockRecentPaneToMainFrame
- CMultiPaneFrameWnd [MFC], GetCaptionText
- CMultiPaneFrameWnd [MFC], GetPaneContainerManager
- CMultiPaneFrameWnd [MFC], GetFirstVisiblePane
- CMultiPaneFrameWnd [MFC], GetPane
- CMultiPaneFrameWnd [MFC], GetPaneCount
- CMultiPaneFrameWnd [MFC], GetVisiblePaneCount
- CMultiPaneFrameWnd [MFC], InsertPane
- CMultiPaneFrameWnd [MFC], LoadState
- CMultiPaneFrameWnd [MFC], OnDockToRecentPos
- CMultiPaneFrameWnd [MFC], OnKillRollUpTimer
- CMultiPaneFrameWnd [MFC], OnPaneRecalcLayout
- CMultiPaneFrameWnd [MFC], OnSetRollUpTimer
- CMultiPaneFrameWnd [MFC], OnShowPane
- CMultiPaneFrameWnd [MFC], PaneFromPoint
- CMultiPaneFrameWnd [MFC], RemoveNonValidPanes
- CMultiPaneFrameWnd [MFC], RemovePane
- CMultiPaneFrameWnd [MFC], ReplacePane
- CMultiPaneFrameWnd [MFC], SaveState
- CMultiPaneFrameWnd [MFC], Serialize
- CMultiPaneFrameWnd [MFC], SetDockState
- CMultiPaneFrameWnd [MFC], SetLastFocusedPane
- CMultiPaneFrameWnd [MFC], SetPreDockState
- CMultiPaneFrameWnd [MFC], StoreRecentDockSiteInfo
- CMultiPaneFrameWnd [MFC], StoreRecentTabRelatedInfo
ms.assetid: 989a548e-0d70-46b7-a513-8cf740e1be3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 738c8c3fa25fcfe0a657685b370f8e973d483861
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33375921"
---
# <a name="cmultipaneframewnd-class"></a>CMultiPaneFrameWnd – třída
`CMultiPaneFrameWnd` Rozšiřuje třídu [CPaneFrameWnd třída](../../mfc/reference/cpaneframewnd-class.md). Může podporovat více podoken. Místo jedné embedded popisovač pro ovládacích pruhů `CMultiPaneFrameWnd` obsahuje [CPaneContainerManager třída](../../mfc/reference/cpanecontainermanager-class.md) objekt, který umožňuje uživatelům ukotvení jeden `CMultiPaneFrameWnd` do druhého a dynamicky vytvořit více plovoucí, – záložkami Windows.  

 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMultiPaneFrameWnd : public CPaneFrameWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMultiPaneFrameWnd::AddPane](#addpane)|Přidá do podokna. (Přepisuje [CPaneFrameWnd::AddPane](../../mfc/reference/cpaneframewnd-class.md#addpane).)|  
|[CMultiPaneFrameWnd::AddRecentPane](#addrecentpane)||  
|[CMultiPaneFrameWnd::AdjustLayout](#adjustlayout)|Upraví rozložení zkrácená rámce okna. (Přepisuje [CPaneFrameWnd::AdjustLayout](../../mfc/reference/cpaneframewnd-class.md#adjustlayout).)|  
|[CMultiPaneFrameWnd::AdjustPaneFrames](#adjustpaneframes)|(Přepisuje [CPaneFrameWnd::AdjustPaneFrames](../../mfc/reference/cpaneframewnd-class.md#adjustpaneframes).)|  
|[CMultiPaneFrameWnd::CalcExpectedDockedRect](#calcexpecteddockedrect)|Vypočítá očekávané rámeček ukotveného okna. (Přepisuje [CPaneFrameWnd::CalcExpectedDockedRect](../../mfc/reference/cpaneframewnd-class.md#calcexpecteddockedrect).)|  
|[CMultiPaneFrameWnd::CanBeAttached](#canbeattached)|Určuje, zda lze do jiného podokno nebo rámec okna ukotvení podokně aktuální. (Přepisuje [CPaneFrameWnd::CanBeAttached](../../mfc/reference/cpaneframewnd-class.md#canbeattached).)|  
|[CMultiPaneFrameWnd::CanBeDockedToPane](#canbedockedtopane)|Určuje, zda lze do podokna ukotvení zkrácená rámce okna. (Přepisuje [CPaneFrameWnd::CanBeDockedToPane](../../mfc/reference/cpaneframewnd-class.md#canbedockedtopane).)|  
|[CMultiPaneFrameWnd::CheckGripperVisibility](#checkgrippervisibility)|(Přepisuje [CPaneFrameWnd::CheckGripperVisibility](../../mfc/reference/cpaneframewnd-class.md#checkgrippervisibility).)|  
|[CMultiPaneFrameWnd::CloseMiniFrame](#closeminiframe)|(Přepisuje `CPaneFrameWnd::CloseMiniFrame`.)|  
|[CMultiPaneFrameWnd::ConvertToTabbedDocument](#converttotabbeddocument)|V podokně se převede do dokumentů s kartami. (Přepisuje [CPaneFrameWnd::ConvertToTabbedDocument](../../mfc/reference/cpaneframewnd-class.md#converttotabbeddocument).)|  
|[CMultiPaneFrameWnd::DockFrame](#dockframe)||  
|[CMultiPaneFrameWnd::DockPane](#dockpane)|Ukotvené podokně. (Přepisuje [CPaneFrameWnd::DockPane](../../mfc/reference/cpaneframewnd-class.md#dockpane).)|  
|[CMultiPaneFrameWnd::DockRecentPaneToMainFrame](#dockrecentpanetomainframe)||  
|[CMultiPaneFrameWnd::GetCaptionText](#getcaptiontext)|Vrátí text titulku. (Přepisuje [CPaneFrameWnd::GetCaptionText](../../mfc/reference/cpaneframewnd-class.md#getcaptiontext).)|  
|[CMultiPaneFrameWnd::GetPaneContainerManager](#getpanecontainermanager)|Vrátí odkaz na objekt správce interní kontejneru.|  
|[CMultiPaneFrameWnd::GetFirstVisiblePane](#getfirstvisiblepane)|Vrátí první viditelné podokno, které se nachází v okně s rámečkem zkrácená. (Přepisuje [CPaneFrameWnd::GetFirstVisiblePane](../../mfc/reference/cpaneframewnd-class.md#getfirstvisiblepane).)|  
|[CMultiPaneFrameWnd::GetPane](#getpane)|Vrátí podokno, ve kterém se nachází v zkrácená rámce okna. (Přepisuje [CPaneFrameWnd::GetPane](../../mfc/reference/cpaneframewnd-class.md#getpane).)|  
|[CMultiPaneFrameWnd::GetPaneCount](#getpanecount)|Vrátí počet podokna, které jsou obsaženy v okně s rámečkem zkrácená. (Přepisuje [CPaneFrameWnd::GetPaneCount](../../mfc/reference/cpaneframewnd-class.md#getpanecount).)|  
|[CMultiPaneFrameWnd::GetVisiblePaneCount](#getvisiblepanecount)|Vrátí počet viditelné podokna, které jsou obsaženy v okně s rámečkem zkrácená. (Přepisuje [CPaneFrameWnd::GetVisiblePaneCount](../../mfc/reference/cpaneframewnd-class.md#getvisiblepanecount).)|  
|[CMultiPaneFrameWnd::InsertPane](#insertpane)||  
|[CMultiPaneFrameWnd::LoadState](#loadstate)|V podokně Stav načte z registru. (Přepisuje [CPaneFrameWnd::LoadState](../../mfc/reference/cpaneframewnd-class.md#loadstate).)|  
|[CMultiPaneFrameWnd::OnDockToRecentPos](#ondocktorecentpos)|Ukotvené zkrácená rámce okna na nejnovější pozici. (Přepisuje [CPaneFrameWnd::OnDockToRecentPos](../../mfc/reference/cpaneframewnd-class.md#ondocktorecentpos).)|  
|[CMultiPaneFrameWnd::OnKillRollUpTimer](#onkillrolluptimer)|Zastaví časovač souhrn. (Přepisuje [CPaneFrameWnd::OnKillRollUpTimer](../../mfc/reference/cpaneframewnd-class.md#onkillrolluptimer).)|  
|[CMultiPaneFrameWnd::OnPaneRecalcLayout](#onpanerecalclayout)|Upraví rozložení podokně uvnitř zkrácená rámce okna. (Přepisuje [CPaneFrameWnd::OnPaneRecalcLayout](../../mfc/reference/cpaneframewnd-class.md#onpanerecalclayout).)|  
|[CMultiPaneFrameWnd::OnSetRollUpTimer](#onsetrolluptimer)|Nastaví časovač souhrn. (Přepisuje [CPaneFrameWnd::OnSetRollUpTimer](../../mfc/reference/cpaneframewnd-class.md#onsetrolluptimer).)|  
|[CMultiPaneFrameWnd::OnShowPane](#onshowpane)|Voláno rámcem při je skrytý nebo zobrazení podokna v okně zkrácená rámce. (Přepisuje [CPaneFrameWnd::OnShowPane](../../mfc/reference/cpaneframewnd-class.md#onshowpane).)|  
|[CMultiPaneFrameWnd::PaneFromPoint](#panefrompoint)|Vrátí podokno, pokud obsahuje bod uživatelem zadané v okně s rámečkem zkrácená. (Přepisuje [CPaneFrameWnd::PaneFromPoint](../../mfc/reference/cpaneframewnd-class.md#panefrompoint).)|  
|[CMultiPaneFrameWnd::RemoveNonValidPanes](#removenonvalidpanes)|Voláno rámcem odebrat neplatné podokna. (Přepisuje [CPaneFrameWnd::RemoveNonValidPanes](../../mfc/reference/cpaneframewnd-class.md#removenonvalidpanes).)|  
|[CMultiPaneFrameWnd::RemovePane](#removepane)|Podokno odebere zkrácená rámce okna. (Přepisuje [CPaneFrameWnd::RemovePane](../../mfc/reference/cpaneframewnd-class.md#removepane).)|  
|[CMultiPaneFrameWnd::ReplacePane](#replacepane)|Nahradí jednu podokně jiné. (Přepisuje [CPaneFrameWnd::ReplacePane](../../mfc/reference/cpaneframewnd-class.md#replacepane).)|  
|[CMultiPaneFrameWnd::SaveState](#savestate)|V podokně Stav uloží do registru. (Přepisuje [CPaneFrameWnd::SaveState](../../mfc/reference/cpaneframewnd-class.md#savestate).)|  
|[CMultiPaneFrameWnd::Serialize](#serialize)|(Přepisuje `CPaneFrameWnd::Serialize`.)|  
|[CMultiPaneFrameWnd::SetDockState](#setdockstate)|Nastaví stav ukotvení. (Přepisuje [CPaneFrameWnd::SetDockState](../../mfc/reference/cpaneframewnd-class.md#setdockstate).)|  
|[CMultiPaneFrameWnd::SetLastFocusedPane](#setlastfocusedpane)||  
|[CMultiPaneFrameWnd::SetPreDockState](#setpredockstate)|Nastaví predocking stavu. (Přepisuje [CPaneFrameWnd::SetPreDockState](../../mfc/reference/cpaneframewnd-class.md#setpredockstate).)|  
|[CMultiPaneFrameWnd::StoreRecentDockSiteInfo](#storerecentdocksiteinfo)|(Přepisuje [CPaneFrameWnd::StoreRecentDockSiteInfo](../../mfc/reference/cpaneframewnd-class.md#storerecentdocksiteinfo).)|  
|[CMultiPaneFrameWnd::StoreRecentTabRelatedInfo](#storerecenttabrelatedinfo)|(Přepisuje [CPaneFrameWnd::StoreRecentTabRelatedInfo](../../mfc/reference/cpaneframewnd-class.md#storerecenttabrelatedinfo).)|  
  
## <a name="remarks"></a>Poznámky  
 Většina metod v této třídě přepsání metody v [CPaneFrameWnd třída](../../mfc/reference/cpaneframewnd-class.md) třídy.  
  
 Pokud podokno používá `AFX_CBRS_AUTO_ROLLUP` styl a uživatel ukotvené tomto podokně do více podokně rámce okna, uživatel může souhrnné okno bez ohledu na nastavení styl ukotveného podoken.  
  
 Rozhraní framework automaticky vytvoří `CMultiPaneFrameWnd` objekt při uživatele jako plovoucí podokno, ve kterém se používá `CBRS_FLOAT_MULTI` stylu.  
  
 Informace o odvození třídy z `CPaneFrameWnd` třídy a vytváření dynamicky, najdete v části [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak načíst ukazatel na `CMultiPaneFrameWnd` objektu. Tento fragment kódu je součástí [nastavit velikost podokna ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_SetPaneSize#4](../../mfc/reference/codesnippet/cpp/cmultipaneframewnd-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)  
  
 [CMultiPaneFrameWnd](../../mfc/reference/cmultipaneframewnd-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxMultiPaneFrameWnd.h  
  
##  <a name="addpane"></a>  CMultiPaneFrameWnd::AddPane  

  
```  
virtual void AddPane(CBasePane* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pWnd`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="addrecentpane"></a>  CMultiPaneFrameWnd::AddRecentPane  

  
```  
virtual BOOL AddRecentPane(CDockablePane* pBar);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pBar`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="adjustlayout"></a>  CMultiPaneFrameWnd::AdjustLayout  

  
```  
virtual void AdjustLayout();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="adjustpaneframes"></a>  CMultiPaneFrameWnd::AdjustPaneFrames  

  
```  
virtual void AdjustPaneFrames();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="calcexpecteddockedrect"></a>  CMultiPaneFrameWnd::CalcExpectedDockedRect  

  
```  
virtual void CalcExpectedDockedRect(
    CWnd* pWndToDock,  
    CPoint ptMouse,  
    CRect& rectResult,  
    BOOL& bDrawTab,  
    CDockablePane** ppTargetBar);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pWndToDock`  
 [v] `ptMouse`  
 [v] `rectResult`  
 [v] `bDrawTab`  
 [v] `ppTargetBar`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="canbeattached"></a>  CMultiPaneFrameWnd::CanBeAttached  

  
```  
virtual BOOL CanBeAttached() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="canbedockedtopane"></a>  CMultiPaneFrameWnd::CanBeDockedToPane  

  
```  
virtual BOOL CanBeDockedToPane(const CDockablePane* pDockingBar) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDockingBar`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="checkgrippervisibility"></a>  CMultiPaneFrameWnd::CheckGripperVisibility  

  
```  
virtual void CheckGripperVisibility();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="closeminiframe"></a>  CMultiPaneFrameWnd::CloseMiniFrame  

  
```  
virtual void CloseMiniFrame();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="converttotabbeddocument"></a>  CMultiPaneFrameWnd::ConvertToTabbedDocument  

  
```  
virtual void ConvertToTabbedDocument();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="dockframe"></a>  CMultiPaneFrameWnd::DockFrame  

  
```  
virtual BOOL DockFrame(
    CPaneFrameWnd* pDockedFrame,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDockedFrame`  
 [v] `dockMethod`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="dockpane"></a>  CMultiPaneFrameWnd::DockPane  

  
```  
virtual BOOL DockPane(CDockablePane* pDockedBar);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDockedBar`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="dockrecentpanetomainframe"></a>  CMultiPaneFrameWnd::DockRecentPaneToMainFrame  

  
```  
virtual void DockRecentPaneToMainFrame(CDockablePane* pBar);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pBar`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getcaptiontext"></a>  CMultiPaneFrameWnd::GetCaptionText  

  
```  
virtual CString GetCaptionText();
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getfirstvisiblepane"></a>  CMultiPaneFrameWnd::GetFirstVisiblePane  

  
```  
virtual CWnd* GetFirstVisiblePane() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getpane"></a>  CMultiPaneFrameWnd::GetPane  

  
```  
virtual CWnd* GetPane() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getpanecontainermanager"></a>  CMultiPaneFrameWnd::GetPaneContainerManager  
 Vrátí odkaz na objekt správce interní kontejneru.  
  
```  
CPaneContainerManager& GetPaneContainerManager();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na objekt správce interní kontejneru.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu lze použít pro přístup k interní [CPaneContainerManager třída](../../mfc/reference/cpanecontainermanager-class.md) objektu.  
  
##  <a name="getpanecount"></a>  CMultiPaneFrameWnd::GetPaneCount  

  
```  
virtual int GetPaneCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getvisiblepanecount"></a>  CMultiPaneFrameWnd::GetVisiblePaneCount  

  
```  
virtual int GetVisiblePaneCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="insertpane"></a>  CMultiPaneFrameWnd::InsertPane  

  
```  
virtual BOOL InsertPane(
    CBasePane* pControlBar,  
    CBasePane* pTarget,  
    BOOL bAfter);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pControlBar`  
 [v] `pTarget`  
 [v] `bAfter`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="loadstate"></a>  CMultiPaneFrameWnd::LoadState  

  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpszProfileName`  
 [v] `uiID`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ondocktorecentpos"></a>  CMultiPaneFrameWnd::OnDockToRecentPos  

  
```  
virtual void OnDockToRecentPos();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onkillrolluptimer"></a>  CMultiPaneFrameWnd::OnKillRollUpTimer  

  
```  
virtual void OnKillRollUpTimer();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onpanerecalclayout"></a>  CMultiPaneFrameWnd::OnPaneRecalcLayout  

  
```  
virtual void OnPaneRecalcLayout();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onsetrolluptimer"></a>  CMultiPaneFrameWnd::OnSetRollUpTimer  

  
```  
virtual void OnSetRollUpTimer();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onshowpane"></a>  CMultiPaneFrameWnd::OnShowPane  

  
```  
virtual void OnShowPane(
    CDockablePane* pBar,  
    BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pBar`  
 [v] `bShow`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="panefrompoint"></a>  CMultiPaneFrameWnd::PaneFromPoint  

  
```  
virtual CBasePane* PaneFromPoint(
    CPoint point,  
    int nSensitivity,  
    BOOL bCheckVisibility);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `point`  
 [v] `nSensitivity`  
 [v] `bCheckVisibility`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="removenonvalidpanes"></a>  CMultiPaneFrameWnd::RemoveNonValidPanes  

  
```  
virtual void RemoveNonValidPanes();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="removepane"></a>  CMultiPaneFrameWnd::RemovePane  

  
```  
virtual void RemovePane(
    CBasePane* pBar,  
    BOOL bDestroy = FALSE,  
    BOOL bNoDelayedDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pBar`  
 [v] `bDestroy`  
 [v] `bNoDelayedDestroy`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="replacepane"></a>  CMultiPaneFrameWnd::ReplacePane  

  
```  
virtual void ReplacePane(
    CBasePane* pBarOrg,  
    CBasePane* pBarReplaceWith);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pBarOrg`  
 [v] `pBarReplaceWith`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="savestate"></a>  CMultiPaneFrameWnd::SaveState  

  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpszProfileName`  
 [v] `uiID`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="serialize"></a>  CMultiPaneFrameWnd::Serialize  

  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `ar`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setdockstate"></a>  CMultiPaneFrameWnd::SetDockState  

  
```  
virtual void SetDockState(CDockingManager* pDockManager);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDockManager`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setlastfocusedpane"></a>  CMultiPaneFrameWnd::SetLastFocusedPane  

  
```  
void SetLastFocusedPane(HWND hwnd);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `hwnd`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setpredockstate"></a>  CMultiPaneFrameWnd::SetPreDockState  

  
```  
virtual BOOL SetPreDockState(
    AFX_PREDOCK_STATE preDockState,  
    CBasePane* pBarToDock = NULL,  
    AFX_DOCK_METHOD dockMethod = DM_MOUSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `preDockState`  
 [v] `pBarToDock`  
 [v] `dockMethod`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="storerecentdocksiteinfo"></a>  CMultiPaneFrameWnd::StoreRecentDockSiteInfo  

  
```  
virtual void StoreRecentDockSiteInfo(CPane* pBar);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pBar`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="storerecenttabrelatedinfo"></a>  CMultiPaneFrameWnd::StoreRecentTabRelatedInfo  

  
```  
virtual void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,  
    CDockablePane* pTabbedBar);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDockingBar`  
 [v] `pTabbedBar`  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CPaneFrameWnd – třída](../../mfc/reference/cpaneframewnd-class.md)
