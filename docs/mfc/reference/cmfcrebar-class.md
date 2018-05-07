---
title: Třída CMFCReBar | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCReBar
- AFXREBAR/CMFCReBar
- AFXREBAR/CMFCReBar::AddBar
- AFXREBAR/CMFCReBar::CalcFixedLayout
- AFXREBAR/CMFCReBar::CanFloat
- AFXREBAR/CMFCReBar::Create
- AFXREBAR/CMFCReBar::EnableDocking
- AFXREBAR/CMFCReBar::GetReBarBandInfoSize
- AFXREBAR/CMFCReBar::GetReBarCtrl
- AFXREBAR/CMFCReBar::OnShowControlBarMenu
- AFXREBAR/CMFCReBar::OnToolHitTest
- AFXREBAR/CMFCReBar::OnUpdateCmdUI
- AFXREBAR/CMFCReBar::SetPaneAlignment
dev_langs:
- C++
helpviewer_keywords:
- CMFCReBar [MFC], AddBar
- CMFCReBar [MFC], CalcFixedLayout
- CMFCReBar [MFC], CanFloat
- CMFCReBar [MFC], Create
- CMFCReBar [MFC], EnableDocking
- CMFCReBar [MFC], GetReBarBandInfoSize
- CMFCReBar [MFC], GetReBarCtrl
- CMFCReBar [MFC], OnShowControlBarMenu
- CMFCReBar [MFC], OnToolHitTest
- CMFCReBar [MFC], OnUpdateCmdUI
- CMFCReBar [MFC], SetPaneAlignment
ms.assetid: 02a60e29-6224-49c1-9e74-e0a7d9f8d023
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: abb880c1add83ec03d787c28b816f2e82caeddd6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcrebar-class"></a>CMFCReBar – třída
A `CMFCReBar` objekt je ovládací prvek panel, který poskytuje informace o stavu pro ovládací prvky matrice, rozložení a trvalost.  
   [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCReBar : public CPane  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCReBar::AddBar](#addbar)|Přidá pásmo matrice.|  
|[CMFCReBar::CalcFixedLayout](#calcfixedlayout)|(Přepisuje [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|  
|[CMFCReBar::CanFloat](#canfloat)|(Přepisuje [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).)|  
|[CMFCReBar::Create](#create)|Vytvoří ovládacího prvku matrice a připojí jej k `CMFCReBar` objektu.|  
|[CMFCReBar::EnableDocking](#enabledocking)|(Přepisuje [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking).)|  
|[CMFCReBar::GetReBarBandInfoSize](#getrebarbandinfosize)||  
|[CMFCReBar::GetReBarCtrl](#getrebarctrl)|Poskytuje přímý přístup k základní [crebarctrl –](../../mfc/reference/crebarctrl-class.md) běžného ovládacího prvku.|  
|[CMFCReBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|(Přepisuje [CPane::OnShowControlBarMenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu).)|  
|[CMFCReBar::OnToolHitTest](#ontoolhittest)|(Přepisuje [CWnd::OnToolHitTest](../../mfc/reference/cwnd-class.md#ontoolhittest).)|  
|[CMFCReBar::OnUpdateCmdUI](#onupdatecmdui)|(Přepisuje [CBasePane::OnUpdateCmdUI](http://msdn.microsoft.com/en-us/e139f06a-9793-4ee2-bc3d-517389368c77).)|  
|[CMFCReBar::SetPaneAlignment](#setpanealignment)|(Přepisuje [CBasePane::SetPaneAlignment](../../mfc/reference/cbasepane-class.md#setpanealignment).)|  
  
## <a name="remarks"></a>Poznámky  
 A `CMFCReBar` objekt může obsahovat celou řadu podřízená okna. To zahrnuje úpravy polí, panely nástrojů a seznamy. Můžete změnit velikost matrice prostřednictvím kódu programu, nebo uživatele můžete ručně změnit velikost matrice přetažením jeho úchytu panelu. Na pozadí objektu matrice můžete vytvořit také pro rastrový obrázek podle svého výběru.  
  
 Objekt matrice se chová podobně jako objekt panelu nástrojů. Ovládacím prvkem matrice může obsahovat jeden nebo více pruhy a každé pásmo může obsahovat úchytu panelu, rastrový obrázek, text popisku a podřízeného okna.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí různých metod v nástroji `CMFCReBar` třídy. Příklad ukazuje postup vytvoření ovládacího prvku matrice a přidejte do ní pásmo. Funkce vzdálené správy jako interní panelu nástrojů. Tento fragment kódu je součástí [testovací matrice – ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_RebarTest#1](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_1.h)]  
[!code-cpp[NVC_MFC_RebarTest#2](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md) [CPane](../../mfc/reference/cpane-class.md) [CMFCReBar](../../mfc/reference/cmfcrebar-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxRebar.h  
  
##  <a name="addbar"></a>  CMFCReBar::AddBar  
 Přidá pásmo matrice.  
  
```  
BOOL AddBar(
    CWnd* pBar,  
    LPCTSTR pszText = NULL,  
    CBitmap* pbmp = NULL,  
    DWORD dwStyle = RBBS_GRIPPERALWAYS | RBBS_FIXEDBMP);

BOOL AddBar(
    CWnd* pBar,  
    COLORREF clrFore,  
    COLORREF clrBack,  
    LPCTSTR pszText = NULL,  
    DWORD dwStyle = RBBS_GRIPPERALWAYS);
```  
  
### <a name="parameters"></a>Parametry  
 [v] [out] `pBar`  
 Ukazatel na podřízeného okna, které má být vložen do matrice. Odkazovaný objekt musí mít **ws_child –** styl oken.  
  
 [v] `pszText`  
 Určuje text, který se zobrazí na matrice. Text není součástí podřízeného okna. Místo toho se zobrazí na matrice sám sebe.  
  
 [v] [out] `pbmp`  
 Určuje rastrový obrázek, který se má zobrazit na pozadí matrice.  
  
 [v] `dwStyle`  
 Obsahuje stylu použít vzdálené správy. Úplný seznam styly vzdálené správy, naleznete v popisu pro `fStyle` v [REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393) struktura v dokumentaci k Windows SDK.  
  
 [v] `clrFore`  
 Představuje barvu popředí matrice.  
  
 [v] `clrBack`  
 Představuje barvu pozadí matrice.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud vzdálené byla úspěšně přidána do matrice; v opačném `FALSE`.  
  
##  <a name="create"></a>  CMFCReBar::Create  
 Vytvoří ovládacího prvku matrice a připojí jej k [CMFCReBar](../../mfc/reference/cmfcrebar-class.md) objektu.  
  
```  
BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = RBS_BANDBORDERS,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,  
    UINT nID = AFX_IDW_REBAR);
```  
  
### <a name="parameters"></a>Parametry  
 [v] [out] `pParentWnd`  
 Ukazatel do nadřazeného okna tohoto ovládacího prvku matrice.  
  
 [v] `dwCtrlStyle`  
 Určuje styl ovládacího prvku matrice. Styl výchozí hodnota je **RBS_BANDBORDERS**, který zobrazí zúžit řádky k oddělení přiléhající pruhy v ovládacím prvku matrice. Seznam styly platná najdete v tématu [– styly ovládacího prvku matrice](http://msdn.microsoft.com/library/windows/desktop/bb774377) v dokumentaci k Windows SDK.  
  
 [v] `dwStyle`  
 Styl okna ovládacího prvku matrice. Seznam styly platná najdete v tématu [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 [v] `nID`  
 ID matrice podřízeného okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud se úspěšně; vytvořil matrice v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getrebarctrl"></a>  CMFCReBar::GetReBarCtrl  
 Poskytuje přímý přístup k `CReBarCtrl` základní běžného ovládacího prvku pro `CMFCReBar` objekty.  
  
```  
CReBarCtrl& GetReBarCtrl() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na základní `CReBarCtrl` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Voláním této metody lze využít výhod funkce běžné ovládací prvek Windows matrice při přizpůsobení vaší matrice.  
  
##  <a name="calcfixedlayout"></a>  CMFCReBar::CalcFixedLayout  

  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bStretch`  
 [v] `bHorz`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="canfloat"></a>  CMFCReBar::CanFloat  

  
```  
virtual BOOL CanFloat() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="enabledocking"></a>  CMFCReBar::EnableDocking  

  
```  
void EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `dwDockStyle`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getrebarbandinfosize"></a>  CMFCReBar::GetReBarBandInfoSize  

  
```  
UINT GetReBarBandInfoSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onshowcontrolbarmenu"></a>  CMFCReBar::OnShowControlBarMenu  

  
```  
virtual BOOL OnShowControlBarMenu(CPoint);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `CPoint`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ontoolhittest"></a>  CMFCReBar::OnToolHitTest  

  
```  
virtual INT_PTR OnToolHitTest(
    CPoint point,  
    TOOLINFO* pTI) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `point`  
 [v] `pTI`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onupdatecmdui"></a>  CMFCReBar::OnUpdateCmdUI  

  
```  
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pTarget`  
 [v] `bDisableIfNoHndler`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setpanealignment"></a>  CMFCReBar::SetPaneAlignment  

  
```  
virtual void SetPaneAlignment(DWORD dwAlignment);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `dwAlignment`  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [Crebarctrl – třída](../../mfc/reference/crebarctrl-class.md)   
 [CPane – třída](../../mfc/reference/cpane-class.md)
