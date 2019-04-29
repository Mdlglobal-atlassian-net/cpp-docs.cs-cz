---
title: Cmfcrebar – třída
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
ms.openlocfilehash: 7776bf504d502feee8ef51949b8adc8e44f94c8e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410132"
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

Následující příklad ukazuje, jak použít různé metody v `CMFCReBar` třídy. Příklad ukazuje, jak vytvořit ovládacím prvkem matrice a přidejte do ní pásmo. Funkce vzdálené jako vnitřní panel nástrojů. Tento fragment kódu je součástí [testovací matrice – ukázka](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_RebarTest#1](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_1.h)]
[!code-cpp[NVC_MFC_RebarTest#2](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject –](../../mfc/reference/cobject-class.md) [CCmdTarget –](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md) [CPane](../../mfc/reference/cpane-class.md) [CMFCReBar](../../mfc/reference/cmfcrebar-class.md)

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

*pBar*<br/>
[out v] Ukazatel na podřízené okno, které má být vložen do matrice. Odkazovaný objekt musí mít **WS_CHILD** styl okna.

*pszText*<br/>
[in] Určuje text, který se zobrazí na matrice. Text není součástí podřízené okno. Místo toho se zobrazí na matrice, samotného.

*pbmp*<br/>
[out v] Určuje rastrový obrázek, který se má zobrazit na pozadí matrice.

*dwStyle*<br/>
[in] Obsahuje styl pásma použít. Úplný seznam styly obsluhy vzdálené správy, naleznete v popisu pro `fStyle` v [REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa) struktura v dokumentaci Windows SDK.

*clrFore*<br/>
[in] Představuje barvu popředí matrice.

*clrBack*<br/>
[in] Představuje barvu pozadí matrice.

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

*pParentWnd*<br/>
[out v] Ukazatel na nadřazené okno tohoto ovládacího prvku rebar.

*dwCtrlStyle*<br/>
[in] Určuje styl ovládacího prvku rebar. Výchozí hodnota stylu je **RBS_BANDBORDERS**, který zobrazí zúžit řádky k oddělení sousední pruhy v ovládacím prvku matrice. Seznam platný stylů, najdete v části [– styly ovládacího prvku Rebar](/windows/desktop/Controls/rebar-control-styles) v dokumentaci Windows SDK.

*dwStyle*<br/>
[in] Stylu okna ovládacího prvku rebar. Seznam platný stylů, najdete v části [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*nID*<br/>
[in] ID prvku matrice podřízené okno.

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

[in] *bStretch*<br/>
[in] *bHorz*<br/>

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

[in] *dwDockStyle*<br/>

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

[in] *CPoint*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="ontoolhittest"></a>  CMFCReBar::OnToolHitTest

```
virtual INT_PTR OnToolHitTest(
    CPoint point,
    TOOLINFO* pTI) const;
```

### <a name="parameters"></a>Parametry

[in] *bodu*<br/>
[in] *pTI*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="onupdatecmdui"></a>  CMFCReBar::OnUpdateCmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Parametry

[in] *pTarget*<br/>
[in] *bDisableIfNoHndler*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="setpanealignment"></a>  CMFCReBar::SetPaneAlignment

```
virtual void SetPaneAlignment(DWORD dwAlignment);
```

### <a name="parameters"></a>Parametry

[in] *dwAlignment*<br/>

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CReBarCtrl – třída](../../mfc/reference/crebarctrl-class.md)<br/>
[CPane – třída](../../mfc/reference/cpane-class.md)
