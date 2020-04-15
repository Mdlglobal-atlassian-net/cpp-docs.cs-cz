---
title: Třída CMFCAutohidebar
ms.date: 10/18/2018
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
ms.openlocfilehash: 62750f4fb1261f4f30286297c3a240ab67e6df1c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369903"
---
# <a name="cmfcautohidebar-class"></a>Třída CMFCAutohidebar

Třída `CMFCAutoHideBar` je speciální třída panelu nástrojů, která implementuje funkci automatického skrytí.

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCAutoHideBar : public CPane
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCAutoHideBar::CMFCAutoHideBar](#cmfcautohidebar)||

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCAutoHideBar::AddAutoHideWindow](#addautohidewindow)||
|[CMFCAutoHideBar::AllowShowonpaneMenu](#allowshowonpanemenu)|(Přepíše `CPane::AllowShowOnPaneMenu`.)|
|[CMFCAutoHideBar::CalcFixedLayout](#calcfixedlayout)|(Přepíše [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CMFCAutoHideBar::Vytvořit](#create)|Vytvoří ovládací panel a připojí jej k objektu [CPane.](../../mfc/reference/cpane-class.md) (Přepíše [CPane::Create](../../mfc/reference/cpane-class.md#create).)|
|[CMFCAutoHideBar::GetFirstAHWindow](#getfirstahwindow)||
|[CMFCAutoHideBar::GetvisibleCount](#getvisiblecount)||
|[CMFCAutoHideBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|Volat rámci při speciální podokno menu se chystá k zobrazení. (Přepíše [CPane::OnShowControlBarMenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu).)|
|[CMFCAutoHideBar::RemoveAutoHideWindow](#removeautohidewindow)||
|[CMFCAutoHideBar::SetActiveInGroup](#setactiveingroup)|(Přepíše [CPane::SetActiveInGroup](../../mfc/reference/cpane-class.md#setactiveingroup).)|
|[CMFCAutoHideBar::SetRecentVisibleState](#setrecentvisiblestate)||
|[CMFCAutoHideBar::ShowAutoHideWindow](#showautohidewindow)||
|[CMFCAutoHideBar::StretchPane](#stretchpane)|Roztáhne podokno svisle nebo vodorovně. (Přepíše [CBasePane::StretchPane](../../mfc/reference/cbasepane-class.md#stretchpane).)|
|[CMFCAutoHideBar::UnsetAutoHideMode](#unsetautohidemode)||
|[CMFCAutoHideBar::Aktualizovat visiblestate](#updatevisiblestate)||

### <a name="data-members"></a>Členové dat

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCAutoHideBar::m_nShowAHWndDelay](#m_nshowahwnddelay)|Časová prodleva mezi okamžikem, kdy uživatel umístí kurzor myši nad [třídu CMFCAutoHideButton,](../../mfc/reference/cmfcautohidebutton-class.md) a okamžikem, kdy rozhraní zobrazuje přidružené okno.|

## <a name="remarks"></a>Poznámky

Když uživatel přepne dokovací podokno do režimu automatického skrytí, rozhraní automaticky vytvoří `CMFCAutoHideBar` objekt. Také vytvoří potřebné [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md) a [CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) objekty. Každý `CAutoHideDockSite` objekt je spojen `CMFCAutoHideButton`s jednotlivcem .

Třída `CMFCAutoHideBar` implementuje zobrazení, `CAutoHideDockSite` když myši uživatele najet `CMFCAutoHideButton`myší nad . Když panel nástrojů obdrží zprávu `CMFCAutoHideBar` WM_MOUSEMOVE, spustí časovač. Po dokončení časovače odešle panelu nástrojů WM_TIMER oznámení události. Panel nástrojů zpracovává tuto událost kontrolou, zda je ukazatel myši umístěn nad stejným tlačítkem automatického skrytí, které bylo umístěno při spuštění časovače. Pokud ano, zobrazí `CAutoHideDockSite` se připojená.

Délku zpoždění časovače můžete nastavit nastavením `m_nShowAHWndDelay`. Výchozí hodnota je 400 ms.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak `CMFCAutoHideBar` vytvořit objekt `GetDockSiteRow` a použít jeho metodu.

[!code-cpp[NVC_MFC_RibbonApp#26](../../mfc/reference/codesnippet/cpp/cmfcautohidebar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCAutohidebar](../../mfc/reference/cmfcautohidebar-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxautohidebar.h

## <a name="cmfcautohidebaraddautohidewindow"></a><a name="addautohidewindow"></a>CMFCAutoHideBar::AddAutoHideWindow

Přidá funkce do `CDockablePane` okna, které umožňuje automatické skrytí.

```
CMFCAutoHideButton* AddAutoHideWindow(
    CDockablePane* pAutoHideWnd,
    DWORD dwAlignment);
```

### <a name="parameters"></a>Parametry

*pAutoHideWnd*<br/>
[v] Okno, které chcete skrýt.

*dwAlignment*<br/>
[v] Hodnota, která určuje zarovnání tlačítka automatického skrytí s oknem aplikace.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Parametr *dwAlignment* označuje, kde se v aplikaci nachází tlačítko automatického skrytí. Parametr může být některá z následujících hodnot:

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

## <a name="cmfcautohidebarallowshowonpanemenu"></a><a name="allowshowonpanemenu"></a>CMFCAutoHideBar::AllowShowonpaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcautohidebarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFCAutoHideBar::CalcFixedLayout

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

## <a name="cmfcautohidebarcmfcautohidebar"></a><a name="cmfcautohidebar"></a>CMFCAutoHideBar::CMFCAutoHideBar

Vytvoří objekt CMFCAutoHideBar.

```
CMFCAutoHideBar();
```

### <a name="remarks"></a>Poznámky

## <a name="cmfcautohidebarcreate"></a><a name="create"></a>CMFCAutoHideBar::Vytvořit

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

*název lpszClassName*<br/>

*dwStyl*<br/>

*Rect*<br/>

*pParentWnd*<br/>

*Nid*<br/>

*dwControlBarStyle*<br/>

*pKontext*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcautohidebargetfirstahwindow"></a><a name="getfirstahwindow"></a>CMFCAutoHideBar::GetFirstAHWindow

Vrátí ukazatel na první okno automatického skrytí v aplikaci.

```
CDockablePane* GetFirstAHWindow();
```

### <a name="return-value"></a>Návratová hodnota

První okno automatického skrytí v aplikaci nebo NULL, pokud neexistuje.

### <a name="remarks"></a>Poznámky

## <a name="cmfcautohidebargetvisiblecount"></a><a name="getvisiblecount"></a>CMFCAutoHideBar::GetvisibleCount

Získá počet viditelných automaticky skrýt tlačítka.

```
int GetVisibleCount();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet viditelných tlačítek automatického skrytí.

### <a name="remarks"></a>Poznámky

## <a name="cmfcautohidebarm_nshowahwnddelay"></a><a name="m_nshowahwnddelay"></a>CMFCAutoHideBar::m_nShowAHWndDelay

Časová prodleva mezi okamžikem, kdy uživatel umístí kurzor myši nad [třídu CMFCAutoHideButton,](../../mfc/reference/cmfcautohidebutton-class.md) a okamžikem, kdy rozhraní zobrazuje přidružené okno.

```
int CMFCAutoHideBar::m_nShowAHWndDelay = 400;
```

### <a name="remarks"></a>Poznámky

Když uživatel umístí kurzor `CMFCAutoHideButton`myši nad , je mírné zpoždění před rozhraní zobrazí přidružené okno. Tento parametr určuje délku tohoto zpoždění v milisekundách.

## <a name="cmfcautohidebaronshowcontrolbarmenu"></a><a name="onshowcontrolbarmenu"></a>CMFCAutoHideBar::OnShowControlBarMenu

```
virtual BOOL OnShowControlBarMenu(CPoint);
```

### <a name="parameters"></a>Parametry

[v] *CPoint*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcautohidebarremoveautohidewindow"></a><a name="removeautohidewindow"></a>CMFCAutoHideBar::RemoveAutoHideWindow

Odstraní a zničí okno automatického skrytí.

```
    BOOL RemoveAutoHideWindow(CDockablePane* pAutoHideWnd);
```

### <a name="parameters"></a>Parametry

CDockablePane* *pAutoHideWnd* Okno automatického skrytí, které chcete odebrat.

### <a name="return-value"></a>Návratová hodnota

PRAVDA v případě úspěchu; jinak FALSE.

### <a name="remarks"></a>Poznámky

## <a name="cmfcautohidebarsetactiveingroup"></a><a name="setactiveingroup"></a>CMFCAutoHideBar::SetActiveInGroup

Označí pruh automatického skrytí jako aktivní.

```
virtual void SetActiveInGroup(BOOL bActive);
```

### <a name="parameters"></a>Parametry

[v] BOOL *bActive* TRUE pro nastavení na aktivní; jinak FALSE.

### <a name="remarks"></a>Poznámky

Viz [cpane::SetActiveInGroup](../../mfc/reference/cpane-class.md#setactiveingroup).

## <a name="cmfcautohidebarsetrecentvisiblestate"></a><a name="setrecentvisiblestate"></a>CMFCAutoHideBar::SetRecentVisibleState

```
void SetRecentVisibleState(BOOL bState);
```

### <a name="parameters"></a>Parametry

*bStát*<br/>
[v] nastavit stav.

### <a name="remarks"></a>Poznámky

## <a name="cmfcautohidebarshowautohidewindow"></a><a name="showautohidewindow"></a>CMFCAutoHideBar::ShowAutoHideWindow

Zobrazí okno automatického skrytí.

```
BOOL ShowAutoHideWindow(
    CDockablePane* pAutoHideWnd,
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>Parametry

*pAutoHideWnd*<br/>
[v] Okno k zobrazení.

*bZobrazit*<br/>
[v] TRUE pro zobrazení okna.

*bZpoždění*<br/>
[v] Tento parametr je ignorován.

### <a name="return-value"></a>Návratová hodnota

PRAVDA v případě úspěchu; jinak FALSE.

### <a name="remarks"></a>Poznámky

## <a name="cmfcautohidebarstretchpane"></a><a name="stretchpane"></a>CMFCAutoHideBar::StretchPane

Změní velikost automaticky skrýt pruh v jeho sbaleném stavu tak, aby odpovídal objektu. `CMFCAutoHideButton`

```
virtual CSize StretchPane(
    int nLength,
    BOOL bVert);
```

### <a name="parameters"></a>Parametry

*nDélka*<br/>
[v] Hodnota je nevyužita v základní implementaci. V odvozených implementacích použijte tuto hodnotu k označení délky podokna velikosti.

*bVertovat*<br/>
[v] Hodnota je nevyužita v základní implementaci. V odvozených implementacích použijte hodnotu TRUE ke zpracování případu, kdy je pruh automatického skrytí sbalený svisle, a NEPRAVDA pro případ, kdy je pruh automatického skrytí vodorovně sbalen.

### <a name="return-value"></a>Návratová hodnota

Výsledná velikost podokna se změnami velikosti.

### <a name="remarks"></a>Poznámky

Odvozené třídy můžete přepsat tuto metodu přizpůsobit chování.

## <a name="cmfcautohidebarunsetautohidemode"></a><a name="unsetautohidemode"></a>CMFCAutoHideBar::UnsetAutoHideMode

Zakáže režim automatického skrytí pro skupinu pruhů automatického skrytí.

```
void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup)
```

### <a name="parameters"></a>Parametry

[in] pFirstBarInGroup A ukazatel na první automaticky skrýt pruh ve skupině.

### <a name="remarks"></a>Poznámky

## <a name="cmfcautohidebarupdatevisiblestate"></a><a name="updatevisiblestate"></a>CMFCAutoHideBar::Aktualizovat visiblestate

Volat rámci při automatické skrýt pruh je třeba překreslit.

```
void UpdateVisibleState();
```

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CPane – třída](../../mfc/reference/cpane-class.md)<br/>
[CAutoHideDockSite – třída](../../mfc/reference/cautohidedocksite-class.md)<br/>
[Třída CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md)
