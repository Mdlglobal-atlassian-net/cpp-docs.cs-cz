---
title: CMFCReBar – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: d348cf7aac57ce213e4d3f602501d12cee8e20d8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505446"
---
# <a name="cmfcrebar-class"></a>CMFCReBar – třída

`CMFCReBar` Objekt je ovládací panel, který poskytuje informace o rozložení, persistenci a stavu pro ovládací prvky matrice.
Další podrobnosti najdete ve zdrojovém kódu ve složce **VC\\atlmfc\\src\\MFC** v instalaci sady Visual Studio.
## <a name="syntax"></a>Syntaxe

```
class CMFCReBar : public CPane
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMFCReBar::AddBar](#addbar)|Přidá do matrice pásmo.|
|[CMFCReBar::CalcFixedLayout](#calcfixedlayout)|(Overrides [CBasePane:: CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CMFCReBar::CanFloat](#canfloat)|(Overrides [CBasePane:: CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).)|
|[CMFCReBar:: Create](#create)|Vytvoří ovládací prvek matrice a připojí ho k `CMFCReBar` objektu.|
|[CMFCReBar::EnableDocking](#enabledocking)|(Overrides [CBasePane:: EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking).)|
|[CMFCReBar::GetReBarBandInfoSize](#getrebarbandinfosize)||
|[CMFCReBar::GetReBarCtrl](#getrebarctrl)|Poskytuje přímý přístup k základnímu [atributu CReBarCtrl](../../mfc/reference/crebarctrl-class.md) běžnému řízení.|
|[CMFCReBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|(Overrides [CPane:: OnShowControlBarMenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu).)|
|[CMFCReBar::OnToolHitTest](#ontoolhittest)|(Potlačení [CWnd:: OnToolHitTest](../../mfc/reference/cwnd-class.md#ontoolhittest).)|
|[CMFCReBar::OnUpdateCmdUI](#onupdatecmdui)|(Overrides [CBasePane:: OnUpdateCmdUI](cbasepane-class.md).)|
|[CMFCReBar::SetPaneAlignment](#setpanealignment)|(Overrides [CBasePane:: SetPaneAlignment](../../mfc/reference/cbasepane-class.md#setpanealignment).)|

## <a name="remarks"></a>Poznámky

`CMFCReBar` Objekt může obsahovat různé podřízené okna. To zahrnuje pole pro úpravy, panely nástrojů a seznamy. Můžete změnit velikost matrice programově nebo uživatel může ručně změnit velikost matrice přetažením jeho pruhového panelu. Pozadí objektu matrice můžete také nastavit na rastr podle vašeho výběru.

Objekt matrice se chová podobně jako objekt Toolbar. Ovládací prvek matrice může obsahovat jeden nebo více pásem a každý pruh může obsahovat ovládací panel, rastrový obrázek, textový popisek a podřízené okno.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít různé metody ve `CMFCReBar` třídě. Příklad ukazuje, jak vytvořit ovládací prvek matrice a přidat do něj pásmo. Funkce Band funguje jako vnitřní panel nástrojů. Tento fragment kódu je součástí [ukázky testu matrice](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_RebarTest#1](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_1.h)]
[!code-cpp[NVC_MFC_RebarTest#2](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)\
└&nbsp;[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CPane](../../mfc/reference/cpane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CMFCReBar](../../mfc/reference/cmfcrebar-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxRebar. h

##  <a name="addbar"></a>CMFCReBar::AddBar

Přidá do matrice pásmo.

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

*pBar*<br/>
[in, out] Ukazatel na podřízené okno, které má být vloženo do matrice. Odkazovaný objekt musí mít styl okna **WS_CHILD** .

*pszText*<br/>
pro Určuje text, který se má zobrazit na matrice. Text není součástí podřízeného okna. Místo toho se zobrazí na samotném matrice.

*pbmp*<br/>
[in, out] Určuje rastrový obrázek, který se má zobrazit na pozadí matrice.

*dwStyle*<br/>
pro Obsahuje styl, který se má použít pro pásmo. Úplný seznam stylů pásem naleznete v popisu `fStyle` ve struktuře [REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) v dokumentaci k Windows SDK.

*clrFore*<br/>
pro Představuje barvu popředí matrice.

*clrBack*<br/>
pro Představuje barvu pozadí matrice.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byl panel úspěšně přidán do matrice; v opačném případě FALSE.

##  <a name="create"></a>CMFCReBar:: Create

Vytvoří ovládací prvek matrice a připojí ho k objektu [CMFCReBar](../../mfc/reference/cmfcrebar-class.md) .

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = RBS_BANDBORDERS,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,
    UINT nID = AFX_IDW_REBAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
[in, out] Ukazatel na nadřazené okno tohoto ovládacího prvku matrice.

*dwCtrlStyle*<br/>
pro Určuje styl ovládacího prvku matrice. Výchozí hodnota Style je **RBS_BANDBORDERS**, která zobrazuje úzké řádky pro oddělit sousední pásma na ovládacím prvku matrice. Seznam platných stylů naleznete v tématu [styly ovládacího prvku matrice](/windows/win32/Controls/rebar-control-styles) v dokumentaci Windows SDK.

*dwStyle*<br/>
pro Styl okna ovládacího prvku matrice Seznam platných stylů naleznete v tématu [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*nID*<br/>
pro ID podřízeného okna matrice

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byl matrice úspěšně vytvořen; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="getrebarctrl"></a>CMFCReBar::GetReBarCtrl

Poskytuje přímý přístup k `CReBarCtrl` základnímu společnému ovládacímu prvku pro `CMFCReBar` objekty.

```
CReBarCtrl& GetReBarCtrl() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na podkladový `CReBarCtrl` objekt.

### <a name="remarks"></a>Poznámky

Voláním této metody můžete využít výhod běžných funkcí ovládacího prvku Windows matrice při přizpůsobování matrice.

##  <a name="calcfixedlayout"></a>CMFCReBar::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

pro *bStretch*<br/>
[in] *bHorz*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="canfloat"></a>CMFCReBar::CanFloat

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="enabledocking"></a>CMFCReBar::EnableDocking

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Parametry

[in] *dwDockStyle*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="getrebarbandinfosize"></a>CMFCReBar::GetReBarBandInfoSize

```
UINT GetReBarBandInfoSize() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="onshowcontrolbarmenu"></a>CMFCReBar::OnShowControlBarMenu

```
virtual BOOL OnShowControlBarMenu(CPoint);
```

### <a name="parameters"></a>Parametry

pro *CPoint*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="ontoolhittest"></a>CMFCReBar::OnToolHitTest

```
virtual INT_PTR OnToolHitTest(
    CPoint point,
    TOOLINFO* pTI) const;
```

### <a name="parameters"></a>Parametry

pro *bod*<br/>
pro *PTI*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="onupdatecmdui"></a>CMFCReBar::OnUpdateCmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Parametry

pro *pTarget*<br/>
pro *bDisableIfNoHndler*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="setpanealignment"></a>CMFCReBar::SetPaneAlignment

```
virtual void SetPaneAlignment(DWORD dwAlignment);
```

### <a name="parameters"></a>Parametry

pro *dwAlignment*<br/>

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CReBarCtrl – třída](../../mfc/reference/crebarctrl-class.md)<br/>
[CPane – třída](../../mfc/reference/cpane-class.md)
