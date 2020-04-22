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
ms.openlocfilehash: 409c97aba64c97ecf0443d14a70848cc298a44ba
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749998"
---
# <a name="cmfcrebar-class"></a>CMFCReBar – třída

Objekt `CMFCReBar` je ovládací panel, který poskytuje informace o rozložení, trvalosti a stavu ovládacích prvků výztuže.
Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCReBar : public CPane
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCRebar::Addbar](#addbar)|Přidá k výztuze pruh.|
|[CMFCReBar::CalcFixedLayout](#calcfixedlayout)|(Přepíše [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CMFCRebar::Canfloat](#canfloat)|(Přepíše [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).)|
|[CMFCRebar::Vytvořit](#create)|Vytvoří ovládací prvek výztuže `CMFCReBar` a připojí jej k objektu.|
|[CMFCReBar::EnableDocking](#enabledocking)|(Přepíše [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking).)|
|[CMFCRebar::GetRebarBandInfoSize](#getrebarbandinfosize)||
|[CMFCRebar::GetRebarctrl](#getrebarctrl)|Poskytuje přímý přístup k základní [CReBarCtrl](../../mfc/reference/crebarctrl-class.md) společný ovládací prvek.|
|[CMFCRebar::OnShowControlBarMenu](#onshowcontrolbarmenu)|(Přepíše [CPane::OnShowControlBarMenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu).)|
|[CMFCRebar::OnToolHitTest](#ontoolhittest)|(Přepíše [CWnd::OnToolHitTest](../../mfc/reference/cwnd-class.md#ontoolhittest).)|
|[CMFCReBar::OnUpdateCmdUI](#onupdatecmdui)|(Přepíše [CBasePane::OnUpdateCmdUI](cbasepane-class.md).)|
|[CMFCRebar::Setpanealignment](#setpanealignment)|(Přepíše [CBasePane::SetPaneAlignment](../../mfc/reference/cbasepane-class.md#setpanealignment).)|

## <a name="remarks"></a>Poznámky

Objekt `CMFCReBar` může obsahovat různé podřízené okna. To zahrnuje editační pole, panely nástrojů a seznamy. Můžete změnit velikost výztuže programově nebo uživatel může ručně změnit velikost výztuže přetažením úchytu. Můžete také nastavit pozadí objektu výztuže na rastrovou mapu podle vašeho výběru.

Objekt výztuže se chová podobně jako objekt panelu nástrojů. Ovládací prvek výztuže může obsahovat jedno nebo více pásů a každé pásmo může obsahovat úchyt, bitmapu, textový popisek a podřízené okno.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat různé `CMFCReBar` metody ve třídě. Příklad ukazuje, jak vytvořit ovládací prvek výztuže a přidat do něj pásmo. Pásmo funguje jako vnitřní panel nástrojů. Tento fragment kódu je součástí [ukázky testu výztuže](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_RebarTest#1](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_1.h)]
[!code-cpp[NVC_MFC_RebarTest#2](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)\
啦&nbsp;[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;啦&nbsp;[CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;啦&nbsp;[CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;啦&nbsp;[CPane](../../mfc/reference/cpane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;啦&nbsp;[CMFCRebar](../../mfc/reference/cmfcrebar-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxRebar.h

## <a name="cmfcrebaraddbar"></a><a name="addbar"></a>CMFCRebar::Addbar

Přidá k výztuze pruh.

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
[dovnitř, ven] Ukazatel na podřízené okno, které má být vloženo do výztuže. Odkazovaný objekt musí mít **styl WS_CHILD** okna.

*pszText*<br/>
[v] Určuje text, který se má zobrazit na výztuze. Text není součástí podřízeného okna. Spíše se zobrazí na samotné výztuze.

*pbmp*<br/>
[dovnitř, ven] Určuje bitmapu, která má být zobrazena na pozadí výztuže.

*dwStyl*<br/>
[v] Obsahuje styl, který se má použít pro pásmo. Úplný seznam stylů pásma naleznete v `fStyle` popisu ve struktuře [REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) v dokumentaci k sada Windows SDK.

*clrFore*<br/>
[v] Představuje barvu popředí výztuže.

*zpět*<br/>
[v] Představuje barvu pozadí výztuže.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud bylo pásmo úspěšně přidáno do výztuže; jinak NEPRAVDA.

## <a name="cmfcrebarcreate"></a><a name="create"></a>CMFCRebar::Vytvořit

Vytvoří ovládací prvek výztuže a připojí jej k objektu [CMFCReBar.](../../mfc/reference/cmfcrebar-class.md)

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = RBS_BANDBORDERS,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,
    UINT nID = AFX_IDW_REBAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
[dovnitř, ven] Ukazatel na nadřazené okno tohoto ovládacího prvku výztuže.

*dwCtrlStyl*<br/>
[v] Určuje styl ovládacího prvku výztuže. Výchozí hodnota stylu je **RBS_BANDBORDERS**, která zobrazuje úzké čáry pro oddělení sousedních pásem v ovládacím prvku výztuže. Seznam platných stylů naleznete v [tématu Styly ovládacích prvků výztuže](/windows/win32/Controls/rebar-control-styles) v dokumentaci k sada Windows SDK.

*dwStyl*<br/>
[v] Styl okna ovládacího prvku výztuže. Seznam platných stylů naleznete v [tématu Styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*Nid*<br/>
[v] Id podřízeného okna výztuže.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byla výztuž vytvořena úspěšně; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

## <a name="cmfcrebargetrebarctrl"></a><a name="getrebarctrl"></a>CMFCRebar::GetRebarctrl

Poskytuje přímý `CReBarCtrl` přístup k základní `CMFCReBar` společný ovládací prvek pro objekty.

```
CReBarCtrl& GetReBarCtrl() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na základní `CReBarCtrl` objekt.

### <a name="remarks"></a>Poznámky

Volání této metody využít funkce windows výztuže společné řízení při přizpůsobení výztuže.

## <a name="cmfcrebarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFCReBar::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

[v] *bÚsek*<br/>
[v] *bHorz*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcrebarcanfloat"></a><a name="canfloat"></a>CMFCRebar::Canfloat

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcrebarenabledocking"></a><a name="enabledocking"></a>CMFCReBar::EnableDocking

```cpp
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Parametry

[v] *dwDockStyl*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmfcrebargetrebarbandinfosize"></a><a name="getrebarbandinfosize"></a>CMFCRebar::GetRebarBandInfoSize

```
UINT GetReBarBandInfoSize() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcrebaronshowcontrolbarmenu"></a><a name="onshowcontrolbarmenu"></a>CMFCRebar::OnShowControlBarMenu

```
virtual BOOL OnShowControlBarMenu(CPoint);
```

### <a name="parameters"></a>Parametry

[v] *CPoint*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcrebarontoolhittest"></a><a name="ontoolhittest"></a>CMFCRebar::OnToolHitTest

```
virtual INT_PTR OnToolHitTest(
    CPoint point,
    TOOLINFO* pTI) const;
```

### <a name="parameters"></a>Parametry

[v] *bod*<br/>
[v] *pTI*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcrebaronupdatecmdui"></a><a name="onupdatecmdui"></a>CMFCReBar::OnUpdateCmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Parametry

[v] *pCíl*<br/>
[v] *bDisableIfNoHndler*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmfcrebarsetpanealignment"></a><a name="setpanealignment"></a>CMFCRebar::Setpanealignment

```
virtual void SetPaneAlignment(DWORD dwAlignment);
```

### <a name="parameters"></a>Parametry

[v] *dwAlignment*<br/>

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CRebarctrl](../../mfc/reference/crebarctrl-class.md)<br/>
[CPane – třída](../../mfc/reference/cpane-class.md)
