---
title: Cmfcrebar – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: af74ab381293e04c08a1fa8c601558edaeacf6c4
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43689189"
---
# <a name="cmfcrebar-class"></a>Cmfcrebar – třída
A `CMFCReBar` objekt je ovládací panel, který poskytuje rozvržení, přetrvávání a informace o stavu pro prvky matrice.  
   Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCReBar : public CPane  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCReBar::AddBar](#addbar)|Přidá pásmo matrici.|  
|[CMFCReBar::CalcFixedLayout](#calcfixedlayout)|(Přepíše [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|  
|[CMFCReBar::CanFloat](#canfloat)|(Přepíše [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).)|  
|[CMFCReBar::Create](#create)|Vytvoří ovládací prvek matrice a připojí ho k `CMFCReBar` objektu.|  
|[CMFCReBar::EnableDocking](#enabledocking)|(Přepíše [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking).)|  
|[CMFCReBar::GetReBarBandInfoSize](#getrebarbandinfosize)||  
|[CMFCReBar::GetReBarCtrl](#getrebarctrl)|Poskytuje přímý přístup k podkladovým [atributu CReBarCtrl](../../mfc/reference/crebarctrl-class.md) běžný ovládací prvek.|  
|[CMFCReBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|(Přepíše [CPane::OnShowControlBarMenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu).)|  
|[CMFCReBar::OnToolHitTest](#ontoolhittest)|(Přepíše [CWnd::OnToolHitTest](../../mfc/reference/cwnd-class.md#ontoolhittest).)|  
|[CMFCReBar::OnUpdateCmdUI](#onupdatecmdui)|(Přepíše [CBasePane::OnUpdateCmdUI](cbasepane-class.md).)|  
|[CMFCReBar::SetPaneAlignment](#setpanealignment)|(Přepíše [CBasePane::SetPaneAlignment](../../mfc/reference/cbasepane-class.md#setpanealignment).)|  
  
## <a name="remarks"></a>Poznámky  
 A `CMFCReBar` objekt může obsahovat řadu podřízená okna. To zahrnuje editační políčka, panely nástrojů a pole se seznamem. Můžete změnit velikost matrice prostřednictvím kódu programu nebo uživatele můžete ručně změnit velikost matrice přetažením jeho úchytu panelu. Můžete také nastavit na pozadí objektu matrice do bitmapy podle vašeho výběru.  
  
 Objekt matrice chová podobně jako objekt panelu nástrojů. Ovládacím prvkem matrice může obsahovat jeden nebo více pruhy a každý obsluhy vzdálené správy může obsahovat panel úchytu, bitmapy, textový popisek a podřízené okno.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít různé metody v `CMFCReBar` třídy. Příklad ukazuje, jak vytvořit ovládacím prvkem matrice a přidejte do ní pásmo. Funkce vzdálené jako vnitřní panel nástrojů. Tento fragment kódu je součástí [testovací matrice – ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_RebarTest#1](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_1.h)]  
[!code-cpp[NVC_MFC_RebarTest#2](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject –](../../mfc/reference/cobject-class.md) [CCmdTarget –](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cbasepane –](../../mfc/reference/cbasepane-class.md) [cpane –](../../mfc/reference/cpane-class.md) [cmfcrebar –](../../mfc/reference/cmfcrebar-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxRebar.h  
  
##  <a name="addbar"></a>  CMFCReBar::AddBar  
 Přidá pásmo matrici.  
  
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
 [in] [out] *pBar*  
 Ukazatel na podřízené okno, které má být vložen do matrice. Odkazovaný objekt musí mít **WS_CHILD** styl okna.  
  
 [in] *pszText*  
 Určuje text, který se zobrazí na matrice. Text není součástí podřízené okno. Místo toho se zobrazí na matrice, samotného.  
  
 [in] [out] *pbmp*  
 Určuje rastrový obrázek, který se má zobrazit na pozadí matrice.  
  
 [in] *dwStyle*  
 Obsahuje styl pásma použít. Úplný seznam styly obsluhy vzdálené správy, naleznete v popisu pro `fStyle` v [REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa) struktura v dokumentaci Windows SDK.  
  
 [in] *clrFore*  
 Představuje barvu popředí matrice.  
  
 [in] *clrBack*  
 Představuje barvu pozadí matrice.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je pásmo se úspěšně přidal do matrice; v opačném případě hodnota FALSE.  
  
##  <a name="create"></a>  CMFCReBar::Create  
 Vytvoří ovládací prvek matrice a připojí ho k [cmfcrebar –](../../mfc/reference/cmfcrebar-class.md) objektu.  
  
```  
BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = RBS_BANDBORDERS,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,  
    UINT nID = AFX_IDW_REBAR);
```  
  
### <a name="parameters"></a>Parametry  
 [in] [out] *pParentWnd*  
 Ukazatel na nadřazené okno tohoto ovládacího prvku rebar.  
  
 [in] *dwCtrlStyle*  
 Určuje styl ovládacího prvku rebar. Výchozí hodnota stylu je **RBS_BANDBORDERS**, který zobrazí zúžit řádky k oddělení sousední pruhy v ovládacím prvku matrice. Seznam platný stylů, najdete v části [– styly ovládacího prvku Rebar](/windows/desktop/Controls/rebar-control-styles) v dokumentaci Windows SDK.  
  
 [in] *dwStyle*  
 Stylu okna ovládacího prvku rebar. Seznam platný stylů, najdete v části [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 [in] *nID*  
 ID prvku matrice podřízené okno.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud byl úspěšně; vytvořen matrice v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getrebarctrl"></a>  CMFCReBar::GetReBarCtrl  
 Poskytuje přímý přístup k `CReBarCtrl` základní běžný ovládací prvek pro `CMFCReBar` objekty.  
  
```  
CReBarCtrl& GetReBarCtrl() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na základní `CReBarCtrl` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Voláním této metody lze využít výhody funkcí běžné ovládací prvek Windows matrice při přizpůsobení vašich matrice.  
  
##  <a name="calcfixedlayout"></a>  CMFCReBar::CalcFixedLayout  

  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bStretch*  
 [in] *bHorz*  
  
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
 [in] *dwDockStyle*  
  
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
 [in] *CPoint*  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ontoolhittest"></a>  CMFCReBar::OnToolHitTest  

  
```  
virtual INT_PTR OnToolHitTest(
    CPoint point,  
    TOOLINFO* pTI) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bodu*  
 [in] *pTI*  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onupdatecmdui"></a>  CMFCReBar::OnUpdateCmdUI  

  
```  
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pTarget*  
 [in] *bDisableIfNoHndler*  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setpanealignment"></a>  CMFCReBar::SetPaneAlignment  

  
```  
virtual void SetPaneAlignment(DWORD dwAlignment);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *dwAlignment*  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [Crebarctrl – třída](../../mfc/reference/crebarctrl-class.md)   
 [CPane – třída](../../mfc/reference/cpane-class.md)
