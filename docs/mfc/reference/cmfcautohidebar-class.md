---
title: "Třída CMFCAutoHideBar | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar::CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar::AddAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::AllowShowOnPaneMenu
- AFXAUTOHIDEBAR/CMFCAutoHideBar::CalcFixedLayout
- AFXAUTOHIDEBAR/CMFCAutoHideBar::Create
- AFXAUTOHIDEBAR/CMFCAutoHideBar::GetFirstAHWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::GetVisibleCount
- AFXAUTOHIDEBAR/CMFCAutoHideBar::OnShowControlBarMenu
- AFXAUTOHIDEBAR/CMFCAutoHideBar::RemoveAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::SetActiveInGroup
- AFXAUTOHIDEBAR/CMFCAutoHideBar::SetRecentVisibleState
- AFXAUTOHIDEBAR/CMFCAutoHideBar::ShowAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::StretchPane
- AFXAUTOHIDEBAR/CMFCAutoHideBar::UnSetAutoHideMode
- AFXAUTOHIDEBAR/CMFCAutoHideBar::UpdateVisibleState
- AFXAUTOHIDEBAR/CMFCAutoHideBar::m_nShowAHWndDelay
dev_langs:
- C++
helpviewer_keywords:
- CMFCAutoHideBar [MFC], CMFCAutoHideBar
- CMFCAutoHideBar [MFC], AddAutoHideWindow
- CMFCAutoHideBar [MFC], AllowShowOnPaneMenu
- CMFCAutoHideBar [MFC], CalcFixedLayout
- CMFCAutoHideBar [MFC], Create
- CMFCAutoHideBar [MFC], GetFirstAHWindow
- CMFCAutoHideBar [MFC], GetVisibleCount
- CMFCAutoHideBar [MFC], OnShowControlBarMenu
- CMFCAutoHideBar [MFC], RemoveAutoHideWindow
- CMFCAutoHideBar [MFC], SetActiveInGroup
- CMFCAutoHideBar [MFC], SetRecentVisibleState
- CMFCAutoHideBar [MFC], ShowAutoHideWindow
- CMFCAutoHideBar [MFC], StretchPane
- CMFCAutoHideBar [MFC], UnSetAutoHideMode
- CMFCAutoHideBar [MFC], UpdateVisibleState
- CMFCAutoHideBar [MFC], m_nShowAHWndDelay
ms.assetid: 54c8d84f-de64-4efd-8a47-3ea0ade40a70
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3fdf8ae6346335b54e22170d4397ac95e8918470
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcautohidebar-class"></a>CMFCAutoHideBar – třída
`CMFCAutoHideBar` Třída je speciální nástrojů třídu, která implementuje funkce automatického skrytí.  

 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]    
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCAutoHideBar : public CPane  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCAutoHideBar::CMFCAutoHideBar](#cmfcautohidebar)||  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCAutoHideBar::AddAutoHideWindow](#addautohidewindow)||  
|[CMFCAutoHideBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Přepisuje `CPane::AllowShowOnPaneMenu`.)|  
|[CMFCAutoHideBar::CalcFixedLayout](#calcfixedlayout)|(Přepisuje [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|  
|[CMFCAutoHideBar::Create](#create)|Vytvoří ovládacích pruhů a připojí jej k [CPane](../../mfc/reference/cpane-class.md) objektu. (Přepisuje [CPane::Create](../../mfc/reference/cpane-class.md#create).)|  
|[CMFCAutoHideBar::GetFirstAHWindow](#getfirstahwindow)||  
|[CMFCAutoHideBar::GetVisibleCount](#getvisiblecount)||  
|[CMFCAutoHideBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|Voláno rámcem, pokud je speciální podokně nabídka se nezobrazí. (Přepisuje [CPane::OnShowControlBarMenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu).)|  
|[CMFCAutoHideBar::RemoveAutoHideWindow](#removeautohidewindow)||  
|[CMFCAutoHideBar::SetActiveInGroup](#setactiveingroup)|(Přepisuje [CPane::SetActiveInGroup](../../mfc/reference/cpane-class.md#setactiveingroup).)|  
|[CMFCAutoHideBar::SetRecentVisibleState](#setrecentvisiblestate)||  
|[CMFCAutoHideBar::ShowAutoHideWindow](#showautohidewindow)||  
|[CMFCAutoHideBar::StretchPane](#stretchpane)|Podokno roztahovány vodorovně nebo svisle. (Přepisuje [CBasePane::StretchPane](../../mfc/reference/cbasepane-class.md#stretchpane).)|  
|[CMFCAutoHideBar::UnSetAutoHideMode](#unsetautohidemode)||  
|[CMFCAutoHideBar::UpdateVisibleState](#updatevisiblestate)||  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCAutoHideBar::m_nShowAHWndDelay](#m_nshowahwnddelay)|Prodlevu mezi okamžikem, kdy uživatel umístí myší nad [CMFCAutoHideButton třída](../../mfc/reference/cmfcautohidebutton-class.md) a okamžikem, kdy rozhraní ukazuje přidružené okno.|  
  
## <a name="remarks"></a>Poznámky  
 Když uživatel přejde do režimu automaticky skrýt ukotvení podokně, systém automaticky vytvoří `CMFCAutoHideBar` objektu. Vytvoří také nezbytné [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md) a [CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) objekty. Každý `CAutoHideDockSite` objekt je přidružen k jednotlivcům `CMFCAutoHideButton`.  
  
 `CMFCAutoHideBar` Třída implementuje zobrazení `CAutoHideDockSite` při uživatele se ukazatel myši nachází `CMFCAutoHideButton`. Když panelu nástrojů přijme zprávu o WM_MOUSEMOVE `CMFCAutoHideBar` spustí časovač. Po dokončení časovač odešle panelu nástrojů WM_TIMER oznámení události. Panelu nástrojů zpracovává Tato událost kontrolou, jestli je umístěn ukazatel myši nad tlačítko stejné automaticky skrýt, který byl umístěn nad, když se spustí časovač. Pokud se jedná, připojený `CAutoHideDockSite` se zobrazí.  
  
 Délka časovače zpoždění můžete ovládat nastavením `m_nShowAHWndDelay`. Výchozí hodnota je 400 ms.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit `CMFCAutoHideBar` objektu a použít jeho `GetDockSiteRow` metoda.  
  
 [!code-cpp[NVC_MFC_RibbonApp#26](../../mfc/reference/codesnippet/cpp/cmfcautohidebar-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxautohidebar.h  
  
##  <a name="addautohidewindow"></a>CMFCAutoHideBar::AddAutoHideWindow  
 Přidá funkce `CDockablePane` okno, které umožní, aby automaticky skrýt.  
  
```  
CMFCAutoHideButton* AddAutoHideWindow(
    CDockablePane* pAutoHideWnd,  
    DWORD dwAlignment);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pAutoHideWnd`  
 Okno, které chcete skrýt.  
  
 [v]`dwAlignment`  
 Hodnota, která určuje zarovnání automaticky skrýt tlačítko s okna aplikace.  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
 `dwAlignment` Parametr označuje, kde se nachází automaticky skrýt tlačítko v aplikaci. Parametr může být jakýkoli z následujících hodnot:  
  
- `CBRS_ALIGN_LEFT`  
  
- `CBRS_ALIGN_RIGHT`  
  
- `CBRS_ALIGN_TOP`  
  
- `CBRS_ALIGN_BOTTOM`  
  
##  <a name="allowshowonpanemenu"></a>CMFCAutoHideBar::AllowShowOnPaneMenu  

  
```  
virtual BOOL AllowShowOnPaneMenu() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="calcfixedlayout"></a>CMFCAutoHideBar::CalcFixedLayout  

  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bStretch`  
 [v]`bHorz`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="cmfcautohidebar"></a>CMFCAutoHideBar::CMFCAutoHideBar  
 Vytvoří objekt CMFCAutoHideBar.  
  
```  
CMFCAutoHideBar();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="create"></a>CMFCAutoHideBar::Create  

  
```  
virtual BOOL Create(
    LPCTSTR lpszClassName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID,  
    DWORD dwControlBarStyle = AFX_DEFAULT_PANE_STYLE,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszClassName`  
 [v]`dwStyle`  
 [v]`rect`  
 [v]`pParentWnd`  
 [v]`nID`  
 [v]`dwControlBarStyle`  
 [v]`pContext`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getfirstahwindow"></a>CMFCAutoHideBar::GetFirstAHWindow  
 Vrací ukazatel na první okno automaticky skrýt v aplikaci.  
  
```  
CDockablePane* GetFirstAHWindow();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 První okno automaticky skrýt v aplikaci nebo hodnota NULL, pokud není k dispozici.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getvisiblecount"></a>CMFCAutoHideBar::GetVisibleCount  
 Získá počet viditelné automaticky skrýt tlačítka.  
  
```  
int GetVisibleCount();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet viditelné automaticky skrýt tlačítka.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="m_nshowahwnddelay"></a>CMFCAutoHideBar::m_nShowAHWndDelay  
 Prodlevu mezi okamžikem, kdy uživatel umístí myší nad [CMFCAutoHideButton třída](../../mfc/reference/cmfcautohidebutton-class.md) a okamžikem, kdy rozhraní ukazuje přidružené okno.  
  
```  
int CMFCAutoHideBar::m_nShowAHWndDelay = 400;  
```  
  
### <a name="remarks"></a>Poznámky  
 Když uživatel umístí myší nad `CMFCAutoHideButton`, než rozhraní zobrazí okno přidružené k mírnému zpoždění je. Tento parametr určuje délku tohoto zpoždění v milisekundách.  
  
##  <a name="onshowcontrolbarmenu"></a>CMFCAutoHideBar::OnShowControlBarMenu  

  
```  
virtual BOOL OnShowControlBarMenu(CPoint);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`CPoint`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="removeautohidewindow"></a>CMFCAutoHideBar::RemoveAutoHideWindow  
 Odebere a zničí automaticky skrýt okna.  
  
```  
    BOOL RemoveAutoHideWindow(CDockablePane* pAutoHideWnd);
```  
  
### <a name="parameters"></a>Parametry  
 CDockablePane *`pAutoHideWnd`  
 Automaticky skrýt okna odebrat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je úspěšné; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setactiveingroup"></a>CMFCAutoHideBar::SetActiveInGroup  
 Příznaky automaticky skrýt panel jako aktivní.  
  
```  
virtual void SetActiveInGroup(BOOL bActive);  
```  
  
### <a name="parameters"></a>Parametry  
 [v] BOOL`bActive`  
 Hodnota TRUE, mají-li nastavená jako aktivní; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [CPane::SetActiveInGroup](../../mfc/reference/cpane-class.md#setactiveingroup).  
  
##  <a name="setrecentvisiblestate"></a>CMFCAutoHideBar::SetRecentVisibleState  

  
```  
void SetRecentVisibleState(BOOL bState);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bState`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="showautohidewindow"></a>CMFCAutoHideBar::ShowAutoHideWindow  
 Zobrazí okno automaticky skrýt.  
  
```  
BOOL ShowAutoHideWindow(
        CDockablePane* pAutoHideWnd,  
        BOOL bShow,  
        BOOL bDelay);  
```  
  
### <a name="parameters"></a>Parametry  
 [v] CDockablePane *`pAutoHideWnd`  
 [v] BOOL`bShow`  
 Hodnota TRUE, mají-li zobrazit okno.  
  
 [v] BOOL`bDelay`  
 Tento parametr je ignorován.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je úspěšné; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="stretchpane"></a>CMFCAutoHideBar::StretchPane  
 Změní velikost panelu automaticky skrýt v sbalené stavu podle `CMFCAutoHideButton` objektu.  
  
```  
virtual CSize StretchPane(
    int nLength,   
    BOOL bVert);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nLength`  
 Tato hodnota se nepoužívá v základní implementaci. V odvozených implementace používá se k označení délka podokně změněnou tuto hodnotu.  
  
 [v]`bVert`  
 Tato hodnota se nepoužívá v základní implementaci. V odvozených implementacích použít `TRUE` pro případ, kdy panelu automaticky skrýt sbalena ve svislém směru, zpracování a `FALSE` pro případ, kdy panelu automaticky skrýt sbalena vodorovně.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výsledná velikost změněnou podokně.  
  
### <a name="remarks"></a>Poznámky  
 Odvozené třídy mohou přepsat tuto metodu pro přizpůsobení chování.  
  
##  <a name="unsetautohidemode"></a>CMFCAutoHideBar::UnSetAutoHideMode  
 Zakáže automatické skrytí režimu pro skupinu automaticky skrýt řádky.  
  
```  
void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup)  
```  
  
### <a name="parameters"></a>Parametry  
 [pFirstBarInGroup v]  
 Ukazatel na panelu automaticky skrýt první ve skupině.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="updatevisiblestate"></a>CMFCAutoHideBar::UpdateVisibleState  
 Voláno rámcem při panelu automaticky skrýt musí být překreslen.  
  
```  
void UpdateVisibleState();
```  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CPane – třída](../../mfc/reference/cpane-class.md)   
 [CAutoHideDockSite – třída](../../mfc/reference/cautohidedocksite-class.md)   
 [CMFCAutoHideButton – třída](../../mfc/reference/cmfcautohidebutton-class.md)
