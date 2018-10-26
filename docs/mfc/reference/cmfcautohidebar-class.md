---
title: Cmfcautohidebar – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0a029bb2e2cd231d4a1c19bfcc5c7981cfd7f39b
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50054966"
---
# <a name="cmfcautohidebar-class"></a>Cmfcautohidebar – třída

`CMFCAutoHideBar` Třídy je třída speciální nástrojů, která implementuje funkce automatického skrytí.

Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.

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
|[CMFCAutoHideBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Přepíše `CPane::AllowShowOnPaneMenu`.)|
|[CMFCAutoHideBar::CalcFixedLayout](#calcfixedlayout)|(Přepíše [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CMFCAutoHideBar::Create](#create)|Ovládací panel vytvoří a připojí ho k [cpane –](../../mfc/reference/cpane-class.md) objektu. (Přepíše [CPane::Create](../../mfc/reference/cpane-class.md#create).)|
|[CMFCAutoHideBar::GetFirstAHWindow](#getfirstahwindow)||
|[CMFCAutoHideBar::GetVisibleCount](#getvisiblecount)||
|[CMFCAutoHideBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|Volá se rozhraním, speciální nabídky se zobrazí. (Přepíše [CPane::OnShowControlBarMenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu).)|
|[CMFCAutoHideBar::RemoveAutoHideWindow](#removeautohidewindow)||
|[CMFCAutoHideBar::SetActiveInGroup](#setactiveingroup)|(Přepíše [CPane::SetActiveInGroup](../../mfc/reference/cpane-class.md#setactiveingroup).)|
|[CMFCAutoHideBar::SetRecentVisibleState](#setrecentvisiblestate)||
|[CMFCAutoHideBar::ShowAutoHideWindow](#showautohidewindow)||
|[CMFCAutoHideBar::StretchPane](#stretchpane)|Roztáhne podokno svisle nebo vodorovně. (Přepíše [CBasePane::StretchPane](../../mfc/reference/cbasepane-class.md#stretchpane).)|
|[CMFCAutoHideBar::UnSetAutoHideMode](#unsetautohidemode)||
|[CMFCAutoHideBar::UpdateVisibleState](#updatevisiblestate)||

### <a name="data-members"></a>Datové členy

|Název|Popis|
|----------|-----------------|
|[CMFCAutoHideBar::m_nShowAHWndDelay](#m_nshowahwnddelay)|Časovou prodlevu mezi okamžikem, kdy uživatel umístí kurzor myši přes [cmfcautohidebutton – třída](../../mfc/reference/cmfcautohidebutton-class.md) a v okamžiku, kdy rozhraní ukazuje související okno.|

## <a name="remarks"></a>Poznámky

Když uživatel přejde do režimu automatického skrytí podokně ukotvení, rozhraní automaticky vytvoří `CMFCAutoHideBar` objektu. Také vytvoří nezbytné [cautohidedocksite –](../../mfc/reference/cautohidedocksite-class.md) a [cmfcautohidebutton –](../../mfc/reference/cmfcautohidebutton-class.md) objekty. Každý `CAutoHideDockSite` objekt je přidružený jednotlivec `CMFCAutoHideButton`.

`CMFCAutoHideBar` Třída implementuje zobrazení `CAutoHideDockSite` při uživatele se ukazatel myši nachází `CMFCAutoHideButton`. Když panelu nástrojů obdrží zprávu wm_mousemove a `CMFCAutoHideBar` spustí časovač. Po dokončení časovač odešle panelu nástrojů WM_TIMER oznámení události. Panelu nástrojů zpracovává tuto událost tak, že zkontrolujete, jestli je ukazatel myši umístěn nad stejného automatického skrytí tlačítka, který byl umístěn nad při spuštění časovače. Pokud se jedná, připojeného `CAutoHideDockSite` se zobrazí.

Délka časovače zpoždění můžete řídit nastavením `m_nShowAHWndDelay`. Výchozí hodnota je 400 ms.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit `CMFCAutoHideBar` objektu a použít jeho `GetDockSiteRow` metoda.

[!code-cpp[NVC_MFC_RibbonApp#26](../../mfc/reference/codesnippet/cpp/cmfcautohidebar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[Cmfcautohidebar –](../../mfc/reference/cmfcautohidebar-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxautohidebar.h

## <a name="addautohidewindow"></a>  CMFCAutoHideBar::AddAutoHideWindow

Přidá funkce `CDockablePane` okno, které umožňuje automaticky skrýt.

```
CMFCAutoHideButton* AddAutoHideWindow(
    CDockablePane* pAutoHideWnd,
    DWORD dwAlignment);
```

### <a name="parameters"></a>Parametry

*pAutoHideWnd*<br/>
[in] V okně, které chcete skrýt.

*dwAlignment*<br/>
[in] Hodnota, která určuje zarovnání automaticky skrýt tlačítko podle okna aplikace.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

*DwAlignment* parametr označuje, kde se nachází automaticky skrýt tlačítko v aplikaci. Tento parametr může být jedna z následujících hodnot:

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

## <a name="allowshowonpanemenu"></a>  CMFCAutoHideBar::AllowShowOnPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="calcfixedlayout"></a>  CMFCAutoHideBar::CalcFixedLayout

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

## <a name="cmfcautohidebar"></a>  CMFCAutoHideBar::CMFCAutoHideBar

Vytvoří objekt cmfcautohidebar –.

```
CMFCAutoHideBar();
```

### <a name="remarks"></a>Poznámky

## <a name="create"></a>  CMFCAutoHideBar::Create

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

*lpszClassName*<br/>

*dwStyle*<br/>

*Rect*<br/>

*pParentWnd*<br/>

*nID*<br/>

*dwControlBarStyle*<br/>

*pContext*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="getfirstahwindow"></a>  CMFCAutoHideBar::GetFirstAHWindow

Vrací ukazatel na první okno automatického schovávání v aplikaci.

```
CDockablePane* GetFirstAHWindow();
```

### <a name="return-value"></a>Návratová hodnota

První okno automatického schovávání v aplikaci, nebo hodnota NULL, pokud není k dispozici.

### <a name="remarks"></a>Poznámky

## <a name="getvisiblecount"></a>  CMFCAutoHideBar::GetVisibleCount

Získá počet viditelných automatického skrytí tlačítka.

```
int GetVisibleCount();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet viditelných automatického skrytí tlačítka.

### <a name="remarks"></a>Poznámky

## <a name="m_nshowahwnddelay"></a>  CMFCAutoHideBar::m_nShowAHWndDelay

Časovou prodlevu mezi okamžikem, kdy uživatel umístí kurzor myši přes [cmfcautohidebutton – třída](../../mfc/reference/cmfcautohidebutton-class.md) a v okamžiku, kdy rozhraní ukazuje související okno.

```
int CMFCAutoHideBar::m_nShowAHWndDelay = 400;
```

### <a name="remarks"></a>Poznámky

Když uživatel umístí ukazatel myši nad `CMFCAutoHideButton`, existuje dojde k mírnému zpoždění před rozhraní zobrazí související okno. Tento parametr určuje délku tohoto zpoždění v milisekundách.

## <a name="onshowcontrolbarmenu"></a>  CMFCAutoHideBar::OnShowControlBarMenu

```
virtual BOOL OnShowControlBarMenu(CPoint);
```

### <a name="parameters"></a>Parametry

[in] *CPoint*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="removeautohidewindow"></a>  CMFCAutoHideBar::RemoveAutoHideWindow

Odebere a odstraní okno automatického skrytí.

```
    BOOL RemoveAutoHideWindow(CDockablePane* pAutoHideWnd);
```

### <a name="parameters"></a>Parametry

CDockablePane – * *pAutoHideWnd* automaticky skrýt okno odebrat.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE v případě úspěchu; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

## <a name="setactiveingroup"></a>  CMFCAutoHideBar::SetActiveInGroup

Příznaky automaticky skrývat panel jako aktivní.

```
virtual void SetActiveInGroup(BOOL bActive);
```

### <a name="parameters"></a>Parametry

[in] BOOL *bActive* hodnotu TRUE, chcete-li nastaven na aktivní; jinak hodnota FALSE.

### <a name="remarks"></a>Poznámky

Zobrazit [CPane::SetActiveInGroup](../../mfc/reference/cpane-class.md#setactiveingroup).

## <a name="setrecentvisiblestate"></a>  CMFCAutoHideBar::SetRecentVisibleState

```
void SetRecentVisibleState(BOOL bState);
```

### <a name="parameters"></a>Parametry

*bState*<br/>
[in] Stav nastavení.

### <a name="remarks"></a>Poznámky

## <a name="showautohidewindow"></a>  CMFCAutoHideBar::ShowAutoHideWindow

Zobrazí okno automatické skrývání.

```
BOOL ShowAutoHideWindow(
    CDockablePane* pAutoHideWnd,
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>Parametry

*pAutoHideWnd*<br/>
[in] Okno k zobrazení.

*bShow*<br/>
[in] TRUE, pokud chcete zobrazit v okně.

*bDelay*<br/>
[in] Tento parametr je ignorován.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE v případě úspěchu; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

## <a name="stretchpane"></a>  CMFCAutoHideBar::StretchPane

Změní velikost panelu automatického schovávání ve sbaleném stavu podle `CMFCAutoHideButton` objektu.

```
virtual CSize StretchPane(
    int nLength,
    BOOL bVert);
```

### <a name="parameters"></a>Parametry

*nLength*<br/>
[in] Hodnota se nepoužívá v základní implementaci. V odvozených implementací používejte tuto hodnotu k označení délka změněnou velikostí stavového řádku.

*bVert*<br/>
[in] Hodnota se nepoužívá v základní implementaci. V odvozených implementace, použijte hodnotu PRAVDA, popisovač případ, ve kterém je automatického schovávání panelu svisle sbalený a hodnotu FALSE pro případ, ve kterém je automatického schovávání panelu vodorovně sbalený.

### <a name="return-value"></a>Návratová hodnota

Výsledná velikost podokna změněnou velikostí.

### <a name="remarks"></a>Poznámky

Odvozené třídy mohou přepsat tuto metodu k úpravě chování.

## <a name="unsetautohidemode"></a>  CMFCAutoHideBar::UnSetAutoHideMode

Zakáže automatického schovávání režimu pro skupinu automatického schovávání pruhy.

```
void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup)
```

### <a name="parameters"></a>Parametry

[in] ukazatel na první automatického schovávání panelu ve skupině pFirstBarInGroup.

### <a name="remarks"></a>Poznámky

## <a name="updatevisiblestate"></a>  CMFCAutoHideBar::UpdateVisibleState

Volá se rozhraním, když potřebuje překreslit automatického schovávání panelu.

```
void UpdateVisibleState();
```

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CPane – třída](../../mfc/reference/cpane-class.md)<br/>
[CAutoHideDockSite – třída](../../mfc/reference/cautohidedocksite-class.md)<br/>
[CMFCAutoHideButton – třída](../../mfc/reference/cmfcautohidebutton-class.md)
