---
title: "Třída CPaneFrameWnd | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPaneFrameWnd
- AFXPANEFRAMEWND/CPaneFrameWnd
- AFXPANEFRAMEWND/CPaneFrameWnd::AddPane
- AFXPANEFRAMEWND/CPaneFrameWnd::AddRemovePaneFromGlobalList
- AFXPANEFRAMEWND/CPaneFrameWnd::AdjustLayout
- AFXPANEFRAMEWND/CPaneFrameWnd::AdjustPaneFrames
- AFXPANEFRAMEWND/CPaneFrameWnd::CalcBorderSize
- AFXPANEFRAMEWND/CPaneFrameWnd::CalcExpectedDockedRect
- AFXPANEFRAMEWND/CPaneFrameWnd::CanBeAttached
- AFXPANEFRAMEWND/CPaneFrameWnd::CanBeDockedToPane
- AFXPANEFRAMEWND/CPaneFrameWnd::CheckGripperVisibility
- AFXPANEFRAMEWND/CPaneFrameWnd::ConvertToTabbedDocument
- AFXPANEFRAMEWND/CPaneFrameWnd::Create
- AFXPANEFRAMEWND/CPaneFrameWnd::CreateEx
- AFXPANEFRAMEWND/CPaneFrameWnd::DockPane
- AFXPANEFRAMEWND/CPaneFrameWnd::FindFloatingPaneByID
- AFXPANEFRAMEWND/CPaneFrameWnd::FrameFromPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionHeight
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionRect
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionText
- AFXPANEFRAMEWND/CPaneFrameWnd::GetDockingManager
- AFXPANEFRAMEWND/CPaneFrameWnd::GetDockingMode
- AFXPANEFRAMEWND/CPaneFrameWnd::GetFirstVisiblePane
- AFXPANEFRAMEWND/CPaneFrameWnd::GetHotPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPane
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPaneCount
- AFXPANEFRAMEWND/CPaneFrameWnd::GetParent
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPinState
- AFXPANEFRAMEWND/CPaneFrameWnd::GetRecentFloatingRect
- AFXPANEFRAMEWND/CPaneFrameWnd::GetVisiblePaneCount
- AFXPANEFRAMEWND/CPaneFrameWnd::HitTest
- AFXPANEFRAMEWND/CPaneFrameWnd::IsCaptured
- AFXPANEFRAMEWND/CPaneFrameWnd::IsDelayShow
- AFXPANEFRAMEWND/CPaneFrameWnd::IsRollDown
- AFXPANEFRAMEWND/CPaneFrameWnd::IsRollUp
- AFXPANEFRAMEWND/CPaneFrameWnd::KillDockingTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::LoadState
- AFXPANEFRAMEWND/CPaneFrameWnd::OnBeforeDock
- AFXPANEFRAMEWND/CPaneFrameWnd::OnDockToRecentPos
- AFXPANEFRAMEWND/CPaneFrameWnd::OnKillRollUpTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::OnMovePane
- AFXPANEFRAMEWND/CPaneFrameWnd::OnPaneRecalcLayout
- AFXPANEFRAMEWND/CPaneFrameWnd::OnSetRollUpTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::OnShowPane
- AFXPANEFRAMEWND/CPaneFrameWnd::PaneFromPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::Pin
- AFXPANEFRAMEWND/CPaneFrameWnd::RedrawAll
- AFXPANEFRAMEWND/CPaneFrameWnd::RemoveNonValidPanes
- AFXPANEFRAMEWND/CPaneFrameWnd::RemovePane
- AFXPANEFRAMEWND/CPaneFrameWnd::ReplacePane
- AFXPANEFRAMEWND/CPaneFrameWnd::SaveState
- AFXPANEFRAMEWND/CPaneFrameWnd::SetCaptionButtons
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDelayShow
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockingManager
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockingTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockState
- AFXPANEFRAMEWND/CPaneFrameWnd::SetHotPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::SetPreDockState
- AFXPANEFRAMEWND/CPaneFrameWnd::SizeToContent
- AFXPANEFRAMEWND/CPaneFrameWnd::StartTearOff
- AFXPANEFRAMEWND/CPaneFrameWnd::StoreRecentDockSiteInfo
- AFXPANEFRAMEWND/CPaneFrameWnd::StoreRecentTabRelatedInfo
- AFXPANEFRAMEWND/CPaneFrameWnd::OnCheckRollState
- AFXPANEFRAMEWND/CPaneFrameWnd::OnDrawBorder
- AFXPANEFRAMEWND/CPaneFrameWnd::m_bUseSaveBits
dev_langs: C++
helpviewer_keywords:
- CPaneFrameWnd [MFC], AddPane
- CPaneFrameWnd [MFC], AddRemovePaneFromGlobalList
- CPaneFrameWnd [MFC], AdjustLayout
- CPaneFrameWnd [MFC], AdjustPaneFrames
- CPaneFrameWnd [MFC], CalcBorderSize
- CPaneFrameWnd [MFC], CalcExpectedDockedRect
- CPaneFrameWnd [MFC], CanBeAttached
- CPaneFrameWnd [MFC], CanBeDockedToPane
- CPaneFrameWnd [MFC], CheckGripperVisibility
- CPaneFrameWnd [MFC], ConvertToTabbedDocument
- CPaneFrameWnd [MFC], Create
- CPaneFrameWnd [MFC], CreateEx
- CPaneFrameWnd [MFC], DockPane
- CPaneFrameWnd [MFC], FindFloatingPaneByID
- CPaneFrameWnd [MFC], FrameFromPoint
- CPaneFrameWnd [MFC], GetCaptionHeight
- CPaneFrameWnd [MFC], GetCaptionRect
- CPaneFrameWnd [MFC], GetCaptionText
- CPaneFrameWnd [MFC], GetDockingManager
- CPaneFrameWnd [MFC], GetDockingMode
- CPaneFrameWnd [MFC], GetFirstVisiblePane
- CPaneFrameWnd [MFC], GetHotPoint
- CPaneFrameWnd [MFC], GetPane
- CPaneFrameWnd [MFC], GetPaneCount
- CPaneFrameWnd [MFC], GetParent
- CPaneFrameWnd [MFC], GetPinState
- CPaneFrameWnd [MFC], GetRecentFloatingRect
- CPaneFrameWnd [MFC], GetVisiblePaneCount
- CPaneFrameWnd [MFC], HitTest
- CPaneFrameWnd [MFC], IsCaptured
- CPaneFrameWnd [MFC], IsDelayShow
- CPaneFrameWnd [MFC], IsRollDown
- CPaneFrameWnd [MFC], IsRollUp
- CPaneFrameWnd [MFC], KillDockingTimer
- CPaneFrameWnd [MFC], LoadState
- CPaneFrameWnd [MFC], OnBeforeDock
- CPaneFrameWnd [MFC], OnDockToRecentPos
- CPaneFrameWnd [MFC], OnKillRollUpTimer
- CPaneFrameWnd [MFC], OnMovePane
- CPaneFrameWnd [MFC], OnPaneRecalcLayout
- CPaneFrameWnd [MFC], OnSetRollUpTimer
- CPaneFrameWnd [MFC], OnShowPane
- CPaneFrameWnd [MFC], PaneFromPoint
- CPaneFrameWnd [MFC], Pin
- CPaneFrameWnd [MFC], RedrawAll
- CPaneFrameWnd [MFC], RemoveNonValidPanes
- CPaneFrameWnd [MFC], RemovePane
- CPaneFrameWnd [MFC], ReplacePane
- CPaneFrameWnd [MFC], SaveState
- CPaneFrameWnd [MFC], SetCaptionButtons
- CPaneFrameWnd [MFC], SetDelayShow
- CPaneFrameWnd [MFC], SetDockingManager
- CPaneFrameWnd [MFC], SetDockingTimer
- CPaneFrameWnd [MFC], SetDockState
- CPaneFrameWnd [MFC], SetHotPoint
- CPaneFrameWnd [MFC], SetPreDockState
- CPaneFrameWnd [MFC], SizeToContent
- CPaneFrameWnd [MFC], StartTearOff
- CPaneFrameWnd [MFC], StoreRecentDockSiteInfo
- CPaneFrameWnd [MFC], StoreRecentTabRelatedInfo
- CPaneFrameWnd [MFC], OnCheckRollState
- CPaneFrameWnd [MFC], OnDrawBorder
- CPaneFrameWnd [MFC], m_bUseSaveBits
ms.assetid: ea3423a3-2763-482e-b763-817036ded10d
caps.latest.revision: "28"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e93061da24ac148ac47d96f84d6dfcea67045235
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cpaneframewnd-class"></a>CPaneFrameWnd – třída
[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 Implementuje zkrácená rámec okna, který obsahuje jeden podokně. V podokně doplní klientské oblasti okna.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CPaneFrameWnd : public CWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CPaneFrameWnd::AddPane](#addpane)|Přidá do podokna.|  
|[CPaneFrameWnd::AddRemovePaneFromGlobalList](#addremovepanefromgloballist)|Přidá nebo odebere ze seznamu pro globální podokno.|  
|[CPaneFrameWnd::AdjustLayout](#adjustlayout)|Upraví rozložení zkrácená rámce okna.|  
|[CPaneFrameWnd::AdjustPaneFrames](#adjustpaneframes)||  
|[CPaneFrameWnd::CalcBorderSize](#calcbordersize)|Vypočítá velikost ohraničení pro zkrácená rámce okna.|  
|[CPaneFrameWnd::CalcExpectedDockedRect](#calcexpecteddockedrect)|Vypočítejte očekávané rámeček ukotveného okna.|  
|[CPaneFrameWnd::CanBeAttached](#canbeattached)|Určuje, zda aktuální podokně lze ukotvit do jiného podokno nebo rámec okna.|  
|[CPaneFrameWnd::CanBeDockedToPane](#canbedockedtopane)|Určuje, zda lze do podokna ukotvit zkrácená rámce okna.|  
|[CPaneFrameWnd::CheckGripperVisibility](#checkgrippervisibility)||  
|[CPaneFrameWnd::ConvertToTabbedDocument](#converttotabbeddocument)|V podokně se převede do dokumentů s kartami.|  
|[CPaneFrameWnd::Create](#create)|Zkrácená rámce okna vytvoří a připojí jej k `CPaneFrameWnd` objektu.|  
|[CPaneFrameWnd::CreateEx](#createex)|Zkrácená rámce okna vytvoří a připojí jej k `CPaneFrameWnd` objektu.|  
|[CPaneFrameWnd::DockPane](#dockpane)|Ukotvené podokně.|  
|[CPaneFrameWnd::FindFloatingPaneByID](#findfloatingpanebyid)|Podokno s ID ovládací prvek vyhledá v seznamu pro globální plovoucí podoken.|  
|[CPaneFrameWnd::FrameFromPoint](#framefrompoint)|Vyhledá okně s rámečkem zkrácená obsahující bod zadanou uživatelem.|  
|[CPaneFrameWnd::GetCaptionHeight](#getcaptionheight)|Vrátí výšku titulek zkrácená rámce okna.|  
|[CPaneFrameWnd::GetCaptionRect](#getcaptionrect)|Vypočítá ohraničující obdélník popisek zkrácená rámce okna.|  
|[CPaneFrameWnd::GetCaptionText](#getcaptiontext)|Vrátí text titulku.|  
|[CPaneFrameWnd::GetDockingManager](#getdockingmanager)||  
|[CPaneFrameWnd::GetDockingMode](#getdockingmode)|Vrátí hodnotu režimu ukotvení.|  
|[CPaneFrameWnd::GetFirstVisiblePane](#getfirstvisiblepane)|Vrátí první viditelné podokno, které se nachází v okně s rámečkem zkrácená.|  
|[CPaneFrameWnd::GetHotPoint](#gethotpoint)||  
|[CPaneFrameWnd::GetPane](#getpane)|Vrátí podokno, ve kterém se nachází v zkrácená rámce okna.|  
|[CPaneFrameWnd::GetPaneCount](#getpanecount)|Vrátí počet podokna, které jsou obsaženy v okně s rámečkem zkrácená.|  
|[CPaneFrameWnd::GetParent](#getparent)||  
|[CPaneFrameWnd::GetPinState](#getpinstate)||  
|[CPaneFrameWnd::GetRecentFloatingRect](#getrecentfloatingrect)||  
|[CPaneFrameWnd::GetVisiblePaneCount](#getvisiblepanecount)|Vrátí počet viditelné podokna, které jsou obsaženy v okně s rámečkem zkrácená.|  
|[CPaneFrameWnd::HitTest](#hittest)|Určuje, jaká část zkrácená rámce okna je k danému bodu.|  
|[CPaneFrameWnd::IsCaptured](#iscaptured)||  
|[CPaneFrameWnd::IsDelayShow](#isdelayshow)||  
|[CPaneFrameWnd::IsRollDown](#isrolldown)|Určuje, zda mají být zahrnuty zkrácená rámce okna dolů.|  
|[CPaneFrameWnd::IsRollUp](#isrollup)|Určuje, zda mají být okně s rámečkem zkrácená zahrnuty.|  
|[CPaneFrameWnd::KillDockingTimer](#killdockingtimer)|Zastaví časovač ukotvení.|  
|[CPaneFrameWnd::LoadState](#loadstate)|V podokně Stav načte z registru.|  
|[CPaneFrameWnd::OnBeforeDock](#onbeforedock)|Určuje, zda je možné ukotvení.|  
|[CPaneFrameWnd::OnDockToRecentPos](#ondocktorecentpos)|Ukotvené zkrácená rámce okna na nejnovější pozici.|  
|[CPaneFrameWnd::OnKillRollUpTimer](#onkillrolluptimer)|Zastaví časovač souhrn.|  
|[CPaneFrameWnd::OnMovePane](#onmovepane)|Zadaný posun přesune zkrácená rámce okna.|  
|[CPaneFrameWnd::OnPaneRecalcLayout](#onpanerecalclayout)|Upraví rozložení obsažené podokně.|  
|[CPaneFrameWnd::OnSetRollUpTimer](#onsetrolluptimer)|Nastaví časovač souhrn.|  
|[CPaneFrameWnd::OnShowPane](#onshowpane)|Voláno rámcem při je skrytý nebo zobrazení podokna v okně zkrácená rámce.|  
|[CPaneFrameWnd::PaneFromPoint](#panefrompoint)|Vrátí podokno, pokud obsahuje bod uživatelem zadané v okně s rámečkem zkrácená.|  
|[CPaneFrameWnd::Pin](#pin)||  
|`CPaneFrameWnd::PreTranslateMessage`|Používá třída [CWinApp](../../mfc/reference/cwinapp-class.md) přeložit zprávy oken, než jsou odeslány do [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) a [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funkce systému Windows.|  
|[CPaneFrameWnd::RedrawAll](#redrawall)|Překreslí všechna okna s rámečkem zkrácená.|  
|[CPaneFrameWnd::RemoveNonValidPanes](#removenonvalidpanes)|Voláno rámcem odebrat neplatné podokna.|  
|[CPaneFrameWnd::RemovePane](#removepane)|Podokno odebere zkrácená rámce okna.|  
|[CPaneFrameWnd::ReplacePane](#replacepane)|Nahradí jednu podokně jiné.|  
|[CPaneFrameWnd::SaveState](#savestate)|V podokně Stav uloží do registru.|  
|`CPaneFrameWnd::Serialize`|Čtení nebo zápisu tento objekt z nebo do archivu.|  
|[CPaneFrameWnd::SetCaptionButtons](#setcaptionbuttons)|Nastaví titulek tlačítka.|  
|[CPaneFrameWnd::SetDelayShow](#setdelayshow)||  
|[CPaneFrameWnd::SetDockingManager](#setdockingmanager)||  
|[CPaneFrameWnd::SetDockingTimer](#setdockingtimer)|Nastaví časovač ukotvení.|  
|[CPaneFrameWnd::SetDockState](#setdockstate)|Nastaví stav ukotvení.|  
|[CPaneFrameWnd::SetHotPoint](#sethotpoint)||  
|[CPaneFrameWnd::SetPreDockState](#setpredockstate)|Voláno rámcem pro nastavení predocking stavu.|  
|[CPaneFrameWnd::SizeToContent](#sizetocontent)|Upraví velikost zkrácená rámce okna tak, že je ekvivalentní velikost obsažené podokně.|  
|[CPaneFrameWnd::StartTearOff](#starttearoff)|Praskliny vypnout nabídky.|  
|[CPaneFrameWnd::StoreRecentDockSiteInfo](#storerecentdocksiteinfo)||  
|[CPaneFrameWnd::StoreRecentTabRelatedInfo](#storerecenttabrelatedinfo)||  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CPaneFrameWnd::OnCheckRollState](#oncheckrollstate)|Určuje, zda mají být zahrnuty zkrácená rámce okna nahoru nebo dolů.|  
|[CPaneFrameWnd::OnDrawBorder](#ondrawborder)|Nakreslí ohraničení zkrácená rámce okna.|  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CPaneFrameWnd::m_bUseSaveBits](#m_busesavebits)|Určuje, jestli se registrovat třídu okno s `CS_SAVEBITS` třídy stylu.|  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní framework automaticky vytvoří `CPaneFrameWnd` objektu při podokno je přechod z ukotveného stavu na plovoucí stavu.  
  
 Zkrácená rámce okna můžete přetáhnout s jeho obsahem viditelné (okamžitou ukotvení) nebo pomocí přetahování obdélníku (standardní ukotvení). Ukotvení režimu rámečku malé kontejneru podokně Určuje že malé rámečku je přetáhnete chování. Další informace najdete v tématu [CBasePane::GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode).  
  
 Zkrácená rámce okna zobrazí tlačítka na titulek v souladu s omezením podokně styl. Pokud je možné uzavřít podokně ( [CBasePane::CanBeClosed](../../mfc/reference/cbasepane-class.md#canbeclosed)), se zobrazí tlačítko Zavřít. Pokud má v podokně `AFX_CBRS_AUTO_ROLLUP` styl, se zobrazí kód pin.  
  
 Pokud odvodíte třídu od `CPaneFrameWnd`, se musí zjistit rozhraní postupy k jeho vytvoření. Buď vytvořit třídu přepsáním [CPane::CreateDefaultMiniframe](../../mfc/reference/cpane-class.md#createdefaultminiframe), nebo nastavte `CPane::m_pMiniFrameRTC` člen, které se odkazuje na informace o třídě modulu runtime pro vlastní třídy.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CPaneFrameWnd`   
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxPaneFrameWnd.h  
  
##  <a name="addpane"></a>CPaneFrameWnd::AddPane  
 Přidá do podokna.  
  
```  
virtual void AddPane(CBasePane* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWnd`  
 V podokně Přidat.  
  
##  <a name="addremovepanefromgloballist"></a>CPaneFrameWnd::AddRemovePaneFromGlobalList  
 Přidá nebo odebere ze seznamu pro globální podokno.  
  
```  
static BOOL __stdcall AddRemovePaneFromGlobalList(
    CBasePane* pWnd,  
    BOOL bAdd);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWnd`  
 V podokně Přidat nebo odebrat.  
  
 [v]`bAdd`  
 Pokud nulová, přidejte v podokně. Pokud je 0, odeberte v podokně.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud metoda byla úspěšná. jinak 0.  
  
##  <a name="adjustlayout"></a>CPaneFrameWnd::AdjustLayout  
 Upraví rozložení zkrácená rámce okna.  
  
```  
virtual void AdjustLayout();
```  
  
##  <a name="adjustpaneframes"></a>CPaneFrameWnd::AdjustPaneFrames  

  
```  
virtual void AdjustPaneFrames();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="calcbordersize"></a>CPaneFrameWnd::CalcBorderSize  
 Vypočítá velikost ohraničení pro okno miniframe.  
  
```  
virtual void CalcBorderSize(CRect& rectBorderSize) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`rectBorderSize`  
 Obsahuje velikost v pixelech ohraničení miniframe okna.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána rámcem vypočítat velikost okna miniframe ohraničení. Vrácený velikost závisí na okno miniframe obsahuje panel nástrojů nebo [CDockablePane](../../mfc/reference/cdockablepane-class.md).  
  
##  <a name="calcexpecteddockedrect"></a>CPaneFrameWnd::CalcExpectedDockedRect  
 Vypočítejte očekávané rámeček ukotveného okna.  
  
```  
virtual void CalcExpectedDockedRect(
    CWnd* pWndToDock,  
    CPoint ptMouse,  
    CRect& rectResult,  
    BOOL& bDrawTab,  
    CDockablePane** ppTargetBar);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWndToDock`  
 Ukazatel na okno na ukotvení.  
  
 [v]`ptMouse`  
 Umístění myši.  
  
 [out]`rectResult`  
 Počítaný obdélník.  
  
 [out]`bDrawTab`  
 Pokud `TRUE`, kreslení na kartě. Pokud `FALSE`, není kreslení na kartě.  
  
 [out]`ppTargetBar`  
 Ukazatel na podokně cíl.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vypočítá obdélníku, která by zabírají okno, pokud uživatel přetáhli okno bodu určeného `ptMouse` a jej ukotven existuje.  
  
##  <a name="canbeattached"></a>CPaneFrameWnd::CanBeAttached  
 Určuje, zda aktuální podokně lze ukotvit do jiného podokno nebo rámec okna.  
  
```  
virtual BOOL CanBeAttached() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud v podokně lze ukotvit do jiného podokno nebo rámec okna; v opačném případě `FALSE`.  
  
##  <a name="canbedockedtopane"></a>CPaneFrameWnd::CanBeDockedToPane  
 Určuje, zda lze do podokna ukotvit zkrácená rámce okna.  
  
```  
virtual BOOL CanBeDockedToPane(const CDockablePane* pDockingBar) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDockingBar`  
 Podokno.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud můžete ukotvit zkrácená rámečku `pDockingBar`; jinak hodnota 0.  
  
##  <a name="checkgrippervisibility"></a>CPaneFrameWnd::CheckGripperVisibility  

  
```  
virtual void CheckGripperVisibility();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="converttotabbeddocument"></a>CPaneFrameWnd::ConvertToTabbedDocument  
 V podokně se převede do dokumentů s kartami.  
  
```  
virtual void ConvertToTabbedDocument();
```  
  
##  <a name="create"></a>CPaneFrameWnd::Create  
 Vytvoří okno miniframe a připojí jej k [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) objektu.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszWindowName`  
 Určuje text, který se zobrazí v okně miniframe.  
  
 [v]`dwStyle`  
 Určuje styl okna. Další informace najdete v tématu [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 [v]`rect`  
 Určuje počáteční velikost a umístění okna miniframe.  
  
 [v] [out]`pParentWnd`  
 Určuje nadřazený rámec okna miniframe. Tato hodnota nesmí být `NULL`.  
  
 [v] [out]`pContext`  
 Určuje uživatelská kontextu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud je okno vytvořený úspěšně; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Okno miniframe se vytvoří ve dvou krocích. První, vytvoří rozhraní `CPaneFrameWnd` objektu. Za druhé volání `Create` miniframe období systému Windows a vytvořte jej do `CPaneFrameWnd` objektu.  
  
##  <a name="createex"></a>CPaneFrameWnd::CreateEx  
 Vytvoří okno miniframe a připojí jej k [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) objektu.  
  
```  
virtual BOOL CreateEx(
    DWORD dwStyleEx,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    CCreateContext* pContext=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`dwStyleEx`  
 Určuje styl delší okno. Další informace najdete v tématu [rozšířené styly oken](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)  
  
 [v]`lpszWindowName`  
 Určuje text, který se zobrazí v okně miniframe.  
  
 [v]`dwStyle`  
 Určuje styl okna. Další informace najdete v tématu [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 [v]`rect`  
 Určuje počáteční velikost a umístění okna miniframe.  
  
 [v] [out]`pParentWnd`  
 Určuje nadřazený rámec okna miniframe. Tato hodnota nesmí být `NULL`.  
  
 [v] [out]`pContext`  
 Určuje uživatelská kontextu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud je okno vytvořený úspěšně; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Okno miniframe se vytvoří ve dvou krocích. První, vytvoří rozhraní `CPaneFrameWnd` objektu. Za druhé volání `Create` miniframe období systému Windows a vytvořte jej do `CPaneFrameWnd` objektu.  
  
##  <a name="dockpane"></a>CPaneFrameWnd::DockPane  
 Ukotvené podokně.  
  
```  
virtual CDockablePane* DockPane(BOOL& bWasDocked);
```  
  
### <a name="parameters"></a>Parametry  
 [out]`bWasDocked`  
 `TRUE`Pokud v podokně byl již ukotvena; v opačném případě `FALSE`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud byla operace úspěšná, `CDockablePane` , aby byl v podokně ukotven na; jinak hodnota `NULL`.  
  
##  <a name="findfloatingpanebyid"></a>CPaneFrameWnd::FindFloatingPaneByID  
 Podokno s ID ovládací prvek vyhledá v seznamu pro globální plovoucí podoken.  
  
```  
static CBasePane* FindFloatingPaneByID(UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nID`  
 Představuje ID ovládacího prvku v podokně k vyhledání.  
  
### <a name="return-value"></a>Návratová hodnota  
 V podokně s ID ovládací prvek; v opačném `NULL`, pokud žádné podokno má ID zadaný ovládacího prvku.  
  
##  <a name="framefrompoint"></a>CPaneFrameWnd::FrameFromPoint  
 Vyhledá zkrácená rámec okna, který obsahuje zadaný bod.  
  
```  
static CPaneFrameWnd* __stdcall FrameFromPoint(
    CPoint pt,  
    int nSensitivity,  
    CPaneFrameWnd* pFrameToExclude = NULL,  
    BOOL bFloatMultiOnly = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pt`  
 Bod v souřadnice obrazovky.  
  
 [v]`nSensitivity`  
 Tato velikost zvýšit oblasti hledání zkrácená rámce okna. Zkrácená rámce okna splňuje kritéria hledání, pokud danému bodu spadá do oblasti vyšší.  
  
 [v]`pFrameToExclude`  
 Určuje okně s rámečkem zkrácená chcete vyloučit z hledání.  
  
 [v]`bFloatMultiOnly`  
 Pokud `TRUE`, vyhledávat pouze malý rámce windows, které mají `CBRS_FLOAT_MULTI` stylu. Pokud `FALSE`, hledání všech oken s rámečkem zkrácená.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na zkrácená rámec okna, který obsahuje `pt`jinak `NULL`.  
  
##  <a name="getcaptionheight"></a>CPaneFrameWnd::GetCaptionHeight  
 Vrátí výšku titulek zkrácená rámce okna.  
  
```  
virtual int GetCaptionHeight() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výška v pixelech zkrácená rámce okna.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu za účelem určení výšku zkrácená rámce okna. Ve výchozím nastavení, výška nastavena na `SM_CYSMCAPTION`. Další informace najdete v tématu [GetSystemMetrics funkce](http://msdn.microsoft.com/library/windows/desktop/ms724385).  
  
##  <a name="getcaptionrect"></a>CPaneFrameWnd::GetCaptionRect  
 Vypočítá ohraničující obdélník popisek zkrácená rámce okna.  
  
```  
virtual void GetCaptionRect(CRect& rectCaption) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`rectCaption`  
 Obsahuje velikost a umístění titulek okno zkrácená rámečku v souřadnicích obrazovky.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána rámcem k výpočtu ohraničující obdélník popisek zkrácená rámce okna.  
  
##  <a name="getcaptiontext"></a>CPaneFrameWnd::GetCaptionText  
 Vrátí text titulku.  
  
```  
virtual CString GetCaptionText();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Text titulku zkrácená rámce okna.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána rozhraním framework, když se zobrazí text titulku.  
  
##  <a name="getdockingmanager"></a>CPaneFrameWnd::GetDockingManager  

  
```  
CDockingManager* GetDockingManager() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getdockingmode"></a>CPaneFrameWnd::GetDockingMode  
 Vrátí hodnotu režimu ukotvení.  
  
```  
virtual AFX_DOCK_TYPE GetDockingMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukotvení režim. Jedna z následujících hodnot:  
  
- `DT_STANDARD`  
  
- `DT_IMMEDIATE`  
  
- `DT_SMART`  
  
##  <a name="getfirstvisiblepane"></a>CPaneFrameWnd::GetFirstVisiblePane  
 Vrátí první viditelné podokno, které se nachází v okně s rámečkem zkrácená.  
  
```  
virtual CWnd* GetFirstVisiblePane() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 První podokna v okně zkrácená rámce nebo `NULL` Pokud zkrácená rámce okna obsahuje žádné podokna.  
  
##  <a name="gethotpoint"></a>CPaneFrameWnd::GetHotPoint  

  
```  
CPoint GetHotPoint() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getpane"></a>CPaneFrameWnd::GetPane  
 Vrátí podokno, ve kterém se nachází v zkrácená rámce okna.  
  
```  
virtual CWnd* GetPane() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V podokně obsažené v zkrácená rámečku, nebo `NULL` Pokud zkrácená rámce okna obsahuje žádné podokna.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getpanecount"></a>CPaneFrameWnd::GetPaneCount  
 Vrátí počet podokna, které jsou obsaženy v okně s rámečkem zkrácená.  
  
```  
virtual int GetPaneCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet podokny zkrácená rámce okna. Tato hodnota může být nula.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getparent"></a>CPaneFrameWnd::GetParent  

  
```  
CWnd* GetParent();
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getpinstate"></a>CPaneFrameWnd::GetPinState  

  
```  
BOOL GetPinState() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getrecentfloatingrect"></a>CPaneFrameWnd::GetRecentFloatingRect  

  
```  
CRect GetRecentFloatingRect() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getvisiblepanecount"></a>CPaneFrameWnd::GetVisiblePaneCount  
 Vrátí počet viditelné podokna, které jsou obsaženy v okně s rámečkem zkrácená.  
  
```  
virtual int GetVisiblePaneCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet viditelné podokna.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="hittest"></a>CPaneFrameWnd::HitTest  
 Určuje, jaká část zkrácená rámce okna je k danému bodu.  
  
```  
virtual LRESULT HitTest(
    CPoint point,  
    BOOL bDetectCaption);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`point`  
 Bod, který chcete otestovat.  
  
 [v]`bDetectCaption`  
 Pokud `TRUE`, zkontrolujte bodu na popisek. Pokud `FALSE`, ignorovat titulek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jedna z následujících hodnot:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|`HTNOWHERE`|Se bod nachází mimo zkrácená rámce okna.|  
|`HTCLIENT`|Bod je v oblasti klienta.|  
|`HTCAPTION`|Bod je na titulek.|  
|`HTTOP`|Bod je v horní části.|  
|`HTTOPLEFT`|Bod je v levé horní části.|  
|`HTTOPRIGHT`|Bod je vpravo nahoře.|  
|`HTLEFT`|Bod je na levé straně.|  
|`HTRIGHT`|Bod je vpravo.|  
|`HTBOTTOM`|Bod je v dolní části.|  
|`HTBOTTOMLEFT`|Bod je v dolní části vlevo.|  
|`HTBOTTOMRIGHT`|Bod je v pravé dolní části.|  
  
##  <a name="iscaptured"></a>CPaneFrameWnd::IsCaptured  

  
```  
BOOL IsCaptured() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isdelayshow"></a>CPaneFrameWnd::IsDelayShow  

  
```  
BOOL IsDelayShow() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isrolldown"></a>CPaneFrameWnd::IsRollDown  
 Určuje, zda mají být zahrnuty zkrácená rámce okna dolů.  
  
```  
virtual BOOL IsRollDown() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud zkrácená rámce okna musí být vrácena v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána rámcem k určení, zda mají být zahrnuty zkrácená rámce okna dolů. Funkce rollup nebo rolldown je pro zkrácená rámce okna povolena, pokud obsahuje alespoň jeden podokno, které jsou `AFX_CBRS_AUTO_ROLLUP` příznak. Tento příznak nastaven při vytvoření podokno. Další informace najdete v tématu [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).  
  
 Ve výchozím nastavení rozhraní zkontroluje, zda má ukazatel myši uvnitř zkrácená rámce okna ohraničující obdélník k určení, zda se má být vrácena dolů okna. Můžete přepsat toto chování v odvozené třídě.  
  
##  <a name="isrollup"></a>CPaneFrameWnd::IsRollUp  
 Určuje, zda mají být okně s rámečkem zkrácená zahrnuty.  
  
```  
virtual BOOL IsRollUp() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud musí být zahrnuté okně s rámečkem zkrácená; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána rámcem k určení, zda mají být okně s rámečkem zkrácená zahrnuty. Funkce rollup nebo rolldown je pro zkrácená rámce okna povolena, pokud obsahuje alespoň jeden podokno, které jsou `AFX_CBRS_AUTO_ROLLUP` příznak. Tento příznak nastaven při vytvoření podokno. Další informace najdete v tématu [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).  
  
 Ve výchozím nastavení rozhraní zkontroluje, zda má ukazatel myši uvnitř zkrácená rámce okna ohraničující obdélník k určení, zda se má být zahrnuté okna. Můžete přepsat toto chování v odvozené třídě.  
  
##  <a name="killdockingtimer"></a>CPaneFrameWnd::KillDockingTimer  
 Zastaví časovač ukotvení.  
  
```  
void KillDockingTimer();
```  
  
##  <a name="loadstate"></a>CPaneFrameWnd::LoadState  
 V podokně Stav načte z registru.  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszProfileName`  
 Název profilu.  
  
 [v]`uiID`  
 ID podokně.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud podokno stavu byl načten úspěšně; v opačném případě `FALSE`.  
  
##  <a name="m_busesavebits"></a>CPaneFrameWnd::m_bUseSaveBits  
 Určuje, jestli registrace třídy okna, který má `CS_SAVEBITS` třídy stylu.  
  
```  
AFX_IMPORT_DATA static BOOL m_bUseSaveBits;  
```  
  
### <a name="remarks"></a>Poznámky  
 Nastavit tento statický člen na `TRUE` registrace třídy okna zkrácená rámce, který má `CS_SAVEBITS` stylu. To může pomoct snížit, blikání, když uživatel nastavuje tažením zkrácená rámce okna.  
  
##  <a name="onbeforedock"></a>CPaneFrameWnd::OnBeforeDock  
 Určuje, zda je možné ukotvení.  
  
```  
virtual BOOL OnBeforeDock();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud ukotvení je možné; v opačném `FALSE`.  
  
##  <a name="oncheckrollstate"></a>CPaneFrameWnd::OnCheckRollState  
 Určuje, zda mají být zahrnuty zkrácená rámce okna nahoru nebo dolů.  
  
```  
virtual void OnCheckRollState();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána rámcem k určení, zda mají být zahrnuty zkrácená rámce okna nahoru nebo dolů.  
  
 Ve výchozím nastavení, volá framework [CPaneFrameWnd::IsRollUp](#isrollup) a [CPaneFrameWnd::IsRollDown](#isrolldown) a právě roztahovány nebo obnoví zkrácená rámce okna. Můžete přepsat tuto metodu v odvozené třídě a použít jiný vizuální efekt.  
  
##  <a name="ondocktorecentpos"></a>CPaneFrameWnd::OnDockToRecentPos  
 Ukotvené zkrácená rámce okna na nejnovější pozici.  
  
```  
virtual void OnDockToRecentPos();
```  
  
##  <a name="ondrawborder"></a>CPaneFrameWnd::OnDrawBorder  
 Nakreslí ohraničení zkrácená rámce okna.  
  
```  
virtual void OnDrawBorder(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Kontext zařízení použít k vykreslení ohraničení.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána rámcem k vykreslení ohraničení zkrácená rámce okna.  
  
##  <a name="onkillrolluptimer"></a>CPaneFrameWnd::OnKillRollUpTimer  
 Zastaví časovač souhrn.  
  
```  
virtual void OnKillRollUpTimer();
```  
  
##  <a name="onmovepane"></a>CPaneFrameWnd::OnMovePane  
 Zadaný posun přesune zkrácená rámce okna.  
  
```  
virtual void OnMovePane(
    CPane* pBar,  
    CPoint ptOffset);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pBar`  
 Ukazatel na podokno (Ignorovat).  
  
 [v]`ptOffset`  
 Posun, kterým se mají přesunout podokně.  
  
##  <a name="onpanerecalclayout"></a>CPaneFrameWnd::OnPaneRecalcLayout  
 Upraví rozložení podokně uvnitř zkrácená rámce okna.  
  
```  
virtual void OnPaneRecalcLayout();
```  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework volá tuto metodu, když je nutné upravit rozložení podokně uvnitř zkrácená rámce okna.  
  
 Ve výchozím nastavení v podokně je nastavený tak, aby pokrývalo dokončení klientské oblasti zkrácená rámce okna.  
  
##  <a name="onsetrolluptimer"></a>CPaneFrameWnd::OnSetRollUpTimer  
 Nastaví časovač souhrn.  
  
```  
virtual void OnSetRollUpTimer();
```  
  
##  <a name="onshowpane"></a>CPaneFrameWnd::OnShowPane  
 Voláno rámcem při je skrytý nebo zobrazení podokna v okně zkrácená rámce.  
  
```  
virtual void OnShowPane(
    CDockablePane* pBar,  
    BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pBar`  
 V podokně, který je zobrazen nebo skryt.  
  
 [v]`bShow`  
 `TRUE`zda se zobrazí v podokně; `FALSE` Pokud podokně je skryté.  
  
### <a name="remarks"></a>Poznámky  
 Voláno rámcem při podokna v okně zkrácená rámečku je zobrazen nebo skryt. Výchozí implementace neprovede žádnou akci.  
  
##  <a name="pin"></a>CPaneFrameWnd::Pin  

  
```  
void Pin(BOOL bPin = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bPin`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="panefrompoint"></a>CPaneFrameWnd::PaneFromPoint  
 Vrátí podokno, pokud obsahuje bod uživatelem zadané v okně s rámečkem zkrácená.  
  
```  
virtual CBasePane* PaneFromPoint(
    CPoint point,  
    int nSensitivity,  
    BOOL bCheckVisibility);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`point`  
 Bod, který uživatel klikne, souřadnice obrazovky.  
  
 [v]`nSensitivity`  
 Tento parametr není používán.  
  
 [v]`bCheckVisibility`  
 `TRUE`Chcete-li určit, zda má být vrácen pouze viditelné podokna; v opačném `FALSE`.  
  
### <a name="return-value"></a>Návratová hodnota  
 V podokně, který uživatel klikne, nebo `NULL` Pokud žádné podokně existuje v tomto umístění.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu za účelem získání podokně, která obsahuje daný bod.  
  
##  <a name="redrawall"></a>CPaneFrameWnd::RedrawAll  
 Překreslí všechna okna s rámečkem zkrácená.  
  
```  
static void RedrawAll();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda aktualizuje všechna okna s rámečkem zkrácená voláním [CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) pro každé okno.  
  
##  <a name="removenonvalidpanes"></a>CPaneFrameWnd::RemoveNonValidPanes  
 Voláno rámcem odebrat neplatné podokna.  
  
```  
virtual void RemoveNonValidPanes();
```  
  
##  <a name="removepane"></a>CPaneFrameWnd::RemovePane  
 Podokno odebere zkrácená rámce okna.  
  
```  
virtual void RemovePane(
    CBasePane* pWnd,  
    BOOL bDestroy = FALSE,  
    BOOL bNoDelayedDestroy = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWnd`  
 Ukazatel na podokno odebrat.  
  
 [v]`bDestroy`  
 Určuje, co se stane zkrácená rámce okna. Pokud `bDestroy` je `TRUE`, tato metoda zničí zkrácená rámce okna okamžitě. Pokud je `FALSE`, tato metoda zničí zkrácená rámce okna s určitým zpožděním.  
  
 [v]`bNoDelayedDestroy`  
 Pokud `TRUE`, zpožděné odstranění je zakázána. Pokud `FALSE`, zpožděné je povoleno odstraňování.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework může dojít k poškození okna s rámečkem zkrácená okamžitě, nebo s určitým zpožděním. Pokud chcete zpoždění likvidace oken s rámečkem malý, předat `FALSE` v `bNoDelayedDestroy` parametr. Zpožděné odstraňování nastane, když rozhraní zpracovává `AFX_WM_CHECKEMPTYMINIFRAME` zprávy.  
  
##  <a name="replacepane"></a>CPaneFrameWnd::ReplacePane  
 Nahradí jednu podokně jiné.  
  
```  
virtual void ReplacePane(
    CBasePane* pBarOrg,  
    CBasePane* pBarReplaceWith);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pBarOrg`  
 Ukazatel na původní podokně.  
  
 [v]`pBarReplaceWith`  
 Ukazatel na podokně, který nahrazuje původní podokně.  
  
##  <a name="savestate"></a>CPaneFrameWnd::SaveState  
 V podokně Stav uloží do registru.  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszProfileName`  
 Název profilu.  
  
 [v]`uiID`  
 ID podokně.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud podokno stavu byla úspěšně; uložena. v opačném případě `FALSE`.  
  
##  <a name="setcaptionbuttons"></a>CPaneFrameWnd::SetCaptionButtons  
 Nastaví titulek tlačítka.  
  
```  
virtual void SetCaptionButtons(DWORD dwButtons);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`dwButtons`  
 Bitový operátor OR kombinace následující hodnoty:  
  
- `AFX_CAPTION_BTN_CLOSE`  
  
- `AFX_CAPTION_BTN_PIN`  
  
- `AFX_CAPTION_BTN_MENU`  
  
- `AFX_CAPTION_BTN_CUSTOMIZE`  
  
##  <a name="setdelayshow"></a>CPaneFrameWnd::SetDelayShow  

  
```  
void SetDelayShow(BOOL bDelayShow);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bDelayShow`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setdockingmanager"></a>CPaneFrameWnd::SetDockingManager  

  
```  
void SetDockingManager(CDockingManager* pManager);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pManager`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setdockingtimer"></a>CPaneFrameWnd::SetDockingTimer  
 Nastaví časovač ukotvení.  
  
```  
void SetDockingTimer(UINT nTimeOut);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nTimeOut`  
 Hodnota časového limitu v milisekundách.  
  
##  <a name="setdockstate"></a>CPaneFrameWnd::SetDockState  
 Nastaví stav ukotvení.  
  
```  
virtual void SetDockState(CDockingManager* pDockManager);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDockManager`  
 Ukazatel na ukotvení správce.  
  
##  <a name="sethotpoint"></a>CPaneFrameWnd::SetHotPoint  

  
```  
void SetHotPoint(CPoint& ptNew);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`ptNew`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setpredockstate"></a>CPaneFrameWnd::SetPreDockState  
 Voláno rámcem pro nastavení predocking stavu.  
  
```  
virtual BOOL SetPreDockState(
    AFX_PREDOCK_STATE preDockState,  
    CBasePane* pBarToDock = NULL,  
    AFX_DOCK_METHOD dockMethod = DM_MOUSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`preDockState`  
 Možné hodnoty:  
  
- `PDS_NOTHING`,  
  
- `PDS_DOCK_REGULAR`,  
  
- `PDS_DOCK_TO_TAB`  
  
 [v]`pBarToDock`  
 Ukazatel na podokno ukotvení.  
  
 [v]`dockMethod`  
 Ukotvení metoda. (Tento parametr bude ignorován.)  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud není okno zkrácená rámce ukotvený; `FALSE` Pokud jej ukotven.  
  
##  <a name="sizetocontent"></a>CPaneFrameWnd::SizeToContent  
 Upraví velikost zkrácená rámce okna tak, že je ekvivalentní obsažené podokně.  
  
```  
virtual void SizeToContent();
```  
  
### <a name="remarks"></a>Poznámky  
 Voláním této metody lze upravit velikost oken s rámečkem Zkrácená velikost obsažené podokně.  
  
##  <a name="starttearoff"></a>CPaneFrameWnd::StartTearOff  
 Praskliny vypnout nabídky.  
  
```  
BOOL StartTearOff(CMFCPopu* pMenu);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pMenu`  
 Ukazatel na nabídku.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud metoda byla úspěšná. v opačném `FALSE`.  
  
##  <a name="storerecentdocksiteinfo"></a>CPaneFrameWnd::StoreRecentDockSiteInfo  

  
```  
virtual void StoreRecentDockSiteInfo(CPane* pBar);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pBar`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="storerecenttabrelatedinfo"></a>CPaneFrameWnd::StoreRecentTabRelatedInfo  

  
```  
virtual void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,  
    CDockablePane* pTabbedBar);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDockingBar`  
 [v]`pTabbedBar`  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CWnd – třída](../../mfc/reference/cwnd-class.md)
