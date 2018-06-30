---
title: Třída CTabbedPane | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTabbedPane
- AFXTABBEDPANE/CTabbedPane
- AFXTABBEDPANE/CTabbedPane::DetachPane
- AFXTABBEDPANE/CTabbedPane::EnableTabAutoColor
- AFXTABBEDPANE/CTabbedPane::FloatTab
- AFXTABBEDPANE/CTabbedPane::GetTabArea
- AFXTABBEDPANE/CTabbedPane::GetTabWnd
- AFXTABBEDPANE/CTabbedPane::HasAutoHideMode
- AFXTABBEDPANE/CTabbedPane::IsTabLocationBottom
- AFXTABBEDPANE/CTabbedPane::ResetTabs
- AFXTABBEDPANE/CTabbedPane::SetTabAutoColors
- AFXTABBEDPANE/CTabbedPane::m_bTabsAlwaysTop
- AFXTABBEDPANE/CTabbedPane::m_pTabWndRTC
dev_langs:
- C++
helpviewer_keywords:
- CTabbedPane [MFC], DetachPane
- CTabbedPane [MFC], EnableTabAutoColor
- CTabbedPane [MFC], FloatTab
- CTabbedPane [MFC], GetTabArea
- CTabbedPane [MFC], GetTabWnd
- CTabbedPane [MFC], HasAutoHideMode
- CTabbedPane [MFC], IsTabLocationBottom
- CTabbedPane [MFC], ResetTabs
- CTabbedPane [MFC], SetTabAutoColors
- CTabbedPane [MFC], m_bTabsAlwaysTop
- CTabbedPane [MFC], m_pTabWndRTC
ms.assetid: f4dc5215-b789-4f2d-8c62-477aceda3578
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f9da7016e98d9bd84e62c3b05cae32346827142f
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121835"
---
# <a name="ctabbedpane-class"></a>CTabbedPane – třída
Implementuje funkce podokně odpojitelných karty.  

 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CTabbedPane : public CBaseTabbedPane  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|`CTabbedPane::CTabbedPane`|Výchozí konstruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CTabbedPane::DetachPane](#detachpane)|(Přepisuje [CBaseTabbedPane::DetachPane](../../mfc/reference/cbasetabbedpane-class.md#detachpane).)|  
|[CTabbedPane::EnableTabAutoColor](#enabletabautocolor)|Povolí nebo zakáže automatické barevné zvýrazňování karet.|  
|[CTabbedPane::FloatTab](#floattab)|Obtéká podokno, ale pouze, pokud se v podokně se aktuálně nachází v odpojitelných kartě. (Přepisuje [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).)|  
|[CTabbedPane::GetTabArea](#gettabarea)|Vrátí velikost a umístění oblast karty v okně s kartami.|  
|[CTabbedPane::GetTabWnd](#gettabwnd)||  
|[CTabbedPane::HasAutoHideMode](#hasautohidemode)|Určuje, zda v záložkách podokně můžete přepnout do režimu autohide –. (Přepisuje [CBaseTabbedPane::HasAutoHideMode](../../mfc/reference/cbasetabbedpane-class.md#hasautohidemode).)|  
|[CTabbedPane::IsTabLocationBottom](#istablocationbottom)|Určuje, zda karty jsou umístěné v dolní části okna.|  
|[CTabbedPane::ResetTabs](#resettabs)|Všechny záložkách podokna obnoví do výchozího stavu.|  
|[CTabbedPane::SetTabAutoColors](#settabautocolors)|Nastaví seznam vlastních barev, které lze použít, pokud je povolena funkce automatického barev.|  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CTabbedPane::m_bTabsAlwaysTop](#m_btabsalwaystop)|Výchozí umístění pro karty v aplikaci.|  
|[CTabbedPane::m_pTabWndRTC](#m_ptabwndrtc)|Informace o třídě modulu runtime pro vlastní `CMFCTabCtrl`-odvozené objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní framework automaticky vytvoří instance této třídy, když uživatel připojí jeden podokně do jiného tak, že odkazuje na titulek druhé části okna. Všechny záložkách podokna, které jsou vytvořené pomocí rozhraní mají ID-1.  
  
 Chcete-li zadat regulární karty místo karty stylu Outlook, předat AFX_CBRS_REGULAR_TABS styl, který se [CDockablePane::CreateEx](../../mfc/reference/cdockablepane-class.md#createex) metoda.  
  
 Pokud vytvoříte záložkách podokně odpojitelných karty, v podokně může být zničený, automaticky podle rozhraní framework, neměli byste ukládat ukazatele. Získání ukazatele do podokna s kartami, volání `CBasePane::GetParentTabbedPane` metoda.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu vytvoříme `CTabbedPane` objektu. V dalším kroku používáme [CBaseTabbedPane::AddTab](../../mfc/reference/cbasetabbedpane-class.md#addtab) připojit další karty.  
  
```  
CTabbedPane* pTabbededBar = new CTabbedPane (TRUE);

if (!pTabbededBar->Create (_T(""),
    this,
    CRect (0,
    0,
    200,
    200),  
    TRUE, 
 (UINT) -1,  
    WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS |  
    WS_CLIPCHILDREN | CBRS_LEFT |    
    CBRS_FLOAT_MULTI)) 
{  
    TRACE0("Failed to create Solution Explorer bar\n");

    return FALSE;      // fail to create  
}  
 
pTabbededBar->AddTab (&m_wndClassView);
pTabbededBar->AddTab (&m_wndResourceView);

pTabbededBar->AddTab (&m_wndFileView);
pTabbededBar->EnableDocking(CBRS_ALIGN_ANY);

DockPane(pTabbededBar);
```  
  
## <a name="example"></a>Příklad  
 Jiný způsob, jak vytvořit objekt ovládacího prvku na kartách panelu je použití [CDockablePane::AttachToTabWnd](../../mfc/reference/cdockablepane-class.md#attachtotabwnd). `AttachToTabWnd` Metoda dynamicky vytvoří objekt podokno s kartami pomocí informace o třídě runtime, která nastavuje [CDockablePane::SetTabbedPaneRTC](../../mfc/reference/cdockablepane-class.md#settabbedpanertc).  
  
 V tomto příkladu, že jsme záložkách podokně vytvořit dynamicky připojení dvě karty a ujistěte se, druhý karta bez odpojitelných.  
  
```  
DockPane(&m_wndClassView);

CTabbedPane* pTabbedBar = NULL;  
m_wndResourceView.AttachToTabWnd (&m_wndClassView,
    DM_SHOW,
    TRUE,  
 (CDockablePane**) &pTabbedBar);

m_wndFileView.AttachToTabWnd (pTabbedBar,
    DM_SHOW,
    TRUE,  
 (CDockablePane**) &pTabbedBar);

pTabbedBar->GetUnderlyingWindow ()->EnableTabDetach (1,
    FALSE);
```  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)  
  
 [CTabbedPane](../../mfc/reference/ctabbedpane-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxTabbedPane.h  
  
##  <a name="detachpane"></a>  CTabbedPane::DetachPane  

  
```  
virtual BOOL DetachPane(
    CWnd* pBar,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *pBar*  
 [v] *bHide*  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="enabletabautocolor"></a>  CTabbedPane::EnableTabAutoColor  
 Povolí nebo zakáže automatické barevné zvýrazňování karet.  
  
```  
static void EnableTabAutoColor(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *bEnable*  
 Hodnota TRUE, mají-li povolit automatické barevné zvýrazňování karet; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tuto statickou metodu použijte k povolení nebo zakázání automatické barevné zvýrazňování karet ve všech záložkách podokna v aplikaci. Pokud je tato funkce povolena, každé kartě vyplní vlastní barvy. Můžete najít seznam barev, které se používají k barva karty voláním [CMFCBaseTabCtrl::GetAutoColors](../../mfc/reference/cmfcbasetabctrl-class.md#getautocolors) metoda.  
  
 Můžete zadat seznam barev, které se použijí u tabulátorů voláním [CTabbedPane::SetTabAutoColors](#settabautocolors).  
  
 Ve výchozím nastavení je tato možnost vypnuta.  
  
##  <a name="floattab"></a>  CTabbedPane::FloatTab  

  
```  
virtual BOOL FloatTab(
    CWnd* pBar,  
    int nTabID,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *pBar*  
 [v] *nTabID*  
 [v] *dockMethod*  
 [v] *bHide*  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="gettabarea"></a>  CTabbedPane::GetTabArea  
 Vrátí velikost a umístění oblast karty v okně s kartami.  
  
```  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out] *rectTabAreaTop*  
 Obsahuje velikost a umístění, v souřadnice obrazovky oblasti nejvyšší karet.  
  
 [out] *rectTabAreaBottom*  
 Obsahuje velikost a umístění, v souřadnice obrazovky oblasti dolní karet.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework volá tuto metodu za účelem určit, jak se ukotvení podokno, ve kterém je přetáhnete uživatele. Když uživatel nastavuje tažením podokno přes oblast karty podokna cíl, rozhraní se pokusí ji přidat jako novou kartu cíl podokna. Jinak pokusí se ukotvení v podokně na stranu podokna target, která zahrnuje vytvoření nového kontejneru podokně s podokně oddělovač, který odděluje.  
  
 Potlačí tuto metodu v `CTabbedPane`-odvozené třídy toto chování změnit.  
  
##  <a name="gettabwnd"></a>  CTabbedPane::GetTabWnd  

  
```  
CMFCTabCtrl* GetTabWnd() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="hasautohidemode"></a>  CTabbedPane::HasAutoHideMode  

  
```  
virtual BOOL HasAutoHideMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="istablocationbottom"></a>  CTabbedPane::IsTabLocationBottom  
 Určuje, zda karty jsou umístěné v dolní části okna.  
  
```  
virtual BOOL IsTabLocationBottom() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud oblast karty se nachází v dolní části okna s kartami; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="m_btabsalwaystop"></a>  CTabbedPane::m_bTabsAlwaysTop  
 Výchozí umístění pro karty v aplikaci.  
  
```  
AFX_IMPORT_DATA static BOOL m_bTabsAlwaysTop;  
```  
  
### <a name="remarks"></a>Poznámky  
 Nastavte tento statický člen na hodnotu PRAVDA, aby platnost všechny karty v aplikaci, který se zobrazí v horní části podokna s kartami.  
  
 Předtím, než byl vytvořen s kartami podokně, je nutné nastavit tuto hodnotu.  
  
 Výchozí hodnota je FALSE.  
  
##  <a name="m_ptabwndrtc"></a>  CTabbedPane::m_pTabWndRTC  
 Informace o třídě modulu runtime pro vlastní `CMFCTabCtrl`-odvozené objektu.  
  
```  
AFX_IMPORT_DATA static CRuntimeClass* m_pTabWndRTC;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tuto proměnnou statický člen nastavit na ukazatel na informace třída runtime `CMFCTabCtrl`-odvozené objektu, pokud používáte vlastní okno s kartami v záložkách podokně.  
  
##  <a name="resettabs"></a>  CTabbedPane::ResetTabs  
 Všechny záložkách podokna obnoví do výchozího stavu.  
  
```  
static void ResetTabs();
```  
  
### <a name="remarks"></a>Poznámky  
 Voláním této metody vrátit zpět všechny záložkách podokna do výchozího stavu. Při volání, tato metoda obnoví ohraničení velikosti a stav barva automatické všech záložkách podoken.  
  
##  <a name="settabautocolors"></a>  CTabbedPane::SetTabAutoColors  
 Nastaví seznam vlastních barev, které se používají, pokud je povolena funkce barva automaticky.  
  
```  
static void SetTabAutoColors(const CArray<COLORREF, COLORREF>& arColors);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *arColors*  
 Obsahuje-li nastavit pole.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte, chcete-li přizpůsobit seznam barev, které se používají, pokud je povolena funkce automatického barev. Toto je statickou funkci a ovlivňuje všechny záložkách podokna ve vaší aplikaci.  
  
 Použití [CTabbedPane::EnableTabAutoColor](#enabletabautocolor) chcete povolit nebo zakázat funkci Automatické barev.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CDockablePane – třída](../../mfc/reference/cdockablepane-class.md)   
 [CBaseTabbedPane – třída](../../mfc/reference/cbasetabbedpane-class.md)   
 [CMFCOutlookBar – třída](../../mfc/reference/cmfcoutlookbar-class.md)
