---
title: CDockSite Class
ms.date: 10/18/2018
f1_keywords:
- CDockSite
- AFXDOCKSITE/CDockSite
- AFXDOCKSITE/CDockSite::AddRow
- AFXDOCKSITE/CDockSite::AdjustDockingLayout
- AFXDOCKSITE/CDockSite::AdjustLayout
- AFXDOCKSITE/CDockSite::AlignDockSite
- AFXDOCKSITE/CDockSite::CalcFixedLayout
- AFXDOCKSITE/CDockSite::CanAcceptPane
- AFXDOCKSITE/CDockSite::CreateEx
- AFXDOCKSITE/CDockSite::CreateRow
- AFXDOCKSITE/CDockSite::DockPane
- AFXDOCKSITE/CDockSite::DoesAllowDynInsertBefore
- AFXDOCKSITE/CDockSite::FindRowIndex
- AFXDOCKSITE/CDockSite::FixupVirtualRects
- AFXDOCKSITE/CDockSite::GetDockSiteID
- AFXDOCKSITE/CDockSite::GetDockSiteRowsList
- AFXDOCKSITE/CDockSite::IsAccessibilityCompatible
- AFXDOCKSITE/CDockSite::IsDragMode
- AFXDOCKSITE/CDockSite::IsLastRow
- AFXDOCKSITE/CDockSite::IsRectWithinDockSite
- AFXDOCKSITE/CDockSite::IsResizable
- AFXDOCKSITE/CDockSite::MovePane
- AFXDOCKSITE/CDockSite::OnInsertRow
- AFXDOCKSITE/CDockSite::OnRemoveRow
- AFXDOCKSITE/CDockSite::OnResizeRow
- AFXDOCKSITE/CDockSite::OnSetWindowPos
- AFXDOCKSITE/CDockSite::OnShowRow
- AFXDOCKSITE/CDockSite::OnSizeParent
- AFXDOCKSITE/CDockSite::PaneFromPoint
- AFXDOCKSITE/CDockSite::DockPaneLeftOf
- AFXDOCKSITE/CDockSite::FindPaneByID
- AFXDOCKSITE/CDockSite::GetPaneList
- AFXDOCKSITE/CDockSite::RectSideFromPoint
- AFXDOCKSITE/CDockSite::RemovePane
- AFXDOCKSITE/CDockSite::RemoveRow
- AFXDOCKSITE/CDockSite::ReplacePane
- AFXDOCKSITE/CDockSite::RepositionPanes
- AFXDOCKSITE/CDockSite::ResizeDockSite
- AFXDOCKSITE/CDockSite::ResizeRow
- AFXDOCKSITE/CDockSite::ShowPane
- AFXDOCKSITE/CDockSite::ShowRow
- AFXDOCKSITE/CDockSite::SwapRows
helpviewer_keywords:
- CDockSite [MFC], AddRow
- CDockSite [MFC], AdjustDockingLayout
- CDockSite [MFC], AdjustLayout
- CDockSite [MFC], AlignDockSite
- CDockSite [MFC], CalcFixedLayout
- CDockSite [MFC], CanAcceptPane
- CDockSite [MFC], CreateEx
- CDockSite [MFC], CreateRow
- CDockSite [MFC], DockPane
- CDockSite [MFC], DoesAllowDynInsertBefore
- CDockSite [MFC], FindRowIndex
- CDockSite [MFC], FixupVirtualRects
- CDockSite [MFC], GetDockSiteID
- CDockSite [MFC], GetDockSiteRowsList
- CDockSite [MFC], IsAccessibilityCompatible
- CDockSite [MFC], IsDragMode
- CDockSite [MFC], IsLastRow
- CDockSite [MFC], IsRectWithinDockSite
- CDockSite [MFC], IsResizable
- CDockSite [MFC], MovePane
- CDockSite [MFC], OnInsertRow
- CDockSite [MFC], OnRemoveRow
- CDockSite [MFC], OnResizeRow
- CDockSite [MFC], OnSetWindowPos
- CDockSite [MFC], OnShowRow
- CDockSite [MFC], OnSizeParent
- CDockSite [MFC], PaneFromPoint
- CDockSite [MFC], DockPaneLeftOf
- CDockSite [MFC], FindPaneByID
- CDockSite [MFC], GetPaneList
- CDockSite [MFC], RectSideFromPoint
- CDockSite [MFC], RemovePane
- CDockSite [MFC], RemoveRow
- CDockSite [MFC], ReplacePane
- CDockSite [MFC], RepositionPanes
- CDockSite [MFC], ResizeDockSite
- CDockSite [MFC], ResizeRow
- CDockSite [MFC], ShowPane
- CDockSite [MFC], ShowRow
- CDockSite [MFC], SwapRows
ms.assetid: 0fcfff79-5f50-4281-b2de-a55653bbea40
ms.openlocfilehash: ccd1bc115f92e0c2605fe5f587a0567f672c6c09
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259799"
---
# <a name="cdocksite-class"></a>CDockSite Class

Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.

Poskytuje funkce pro uspořádání podoken, které jsou odvozeny z [cpane – třída](../../mfc/reference/cpane-class.md) do sady řádků.

## <a name="syntax"></a>Syntaxe

```
class CDockSite: public CBasePane
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDockSite::AddRow](#addrow)||
|[CDockSite::AdjustDockingLayout](#adjustdockinglayout)|(Přepíše [CBasePane::AdjustDockingLayout](../../mfc/reference/cbasepane-class.md#adjustdockinglayout).)|
|[CDockSite::AdjustLayout](#adjustlayout)|(Přepíše [CBasePane::AdjustLayout](../../mfc/reference/cbasepane-class.md#adjustlayout).)|
|[CDockSite::AlignDockSite](#aligndocksite)||
|[CDockSite::CalcFixedLayout](#calcfixedlayout)|(Přepíše [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CDockSite::CanAcceptPane](#canacceptpane)|(Přepíše [CBasePane::CanAcceptPane](../../mfc/reference/cbasepane-class.md#canacceptpane).)|
|[CDockSite::CreateEx](#createex)|(Přepíše [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).)|
|[CDockSite::CreateRow](#createrow)||
|[CDockSite::DockPane](#dockpane)|(Přepíše [CBasePane::DockPane](../../mfc/reference/cbasepane-class.md#dockpane).)|
|[CDockSite::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|(Přepíše [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CDockSite::FindRowIndex](#findrowindex)||
|[CDockSite::FixupVirtualRects](#fixupvirtualrects)||
|[CDockSite::GetDockSiteID](#getdocksiteid)||
|[CDockSite::GetDockSiteRowsList](#getdocksiterowslist)||
|[CDockSite::IsAccessibilityCompatible](#isaccessibilitycompatible)|(Přepíše `CBasePane::IsAccessibilityCompatible`.)|
|[CDockSite::IsDragMode](#isdragmode)||
|[CDockSite::IsLastRow](#islastrow)||
|[CDockSite::IsRectWithinDockSite](#isrectwithindocksite)||
|[CDockSite::IsResizable](#isresizable)|(Přepíše [CBasePane::IsResizable](../../mfc/reference/cbasepane-class.md#isresizable).)|
|[CDockSite::MovePane](#movepane)||
|[CDockSite::OnInsertRow](#oninsertrow)||
|[CDockSite::OnRemoveRow](#onremoverow)||
|[CDockSite::OnResizeRow](#onresizerow)||
|[CDockSite::OnSetWindowPos](#onsetwindowpos)||
|[CDockSite::OnShowRow](#onshowrow)||
|[CDockSite::OnSizeParent](#onsizeparent)||
|[CDockSite::PaneFromPoint](#panefrompoint)|Vrátí podokno, které je ukotveno na dokovacím místě v místě určeném daný parametr.|
|[CDockSite::DockPaneLeftOf](#dockpaneleftof)|Ukotvené podokno nalevo od jiného podokna.|
|[CDockSite::FindPaneByID](#findpanebyid)|Vrátí podokno, který je identifikován podle dané ID.|
|[CDockSite::GetPaneList](#getpanelist)|Vrátí seznam podoken, které jsou ukotveno na dokovacím místě.|
|[CDockSite::RectSideFromPoint](#rectsidefrompoint)||
|[CDockSite::RemovePane](#removepane)||
|[CDockSite::RemoveRow](#removerow)||
|[CDockSite::ReplacePane](#replacepane)||
|[CDockSite::RepositionPanes](#repositionpanes)||
|[CDockSite::ResizeDockSite](#resizedocksite)||
|[CDockSite::ResizeRow](#resizerow)||
|[CDockSite::ShowPane](#showpane)|V podokně se zobrazí.|
|[CDockSite::ShowRow](#showrow)||
|[CDockSite::SwapRows](#swaprows)||

## <a name="remarks"></a>Poznámky

Vytvoří rozhraní `CDockSite` objekty automaticky při volání [CFrameWndEx::EnableDocking](../../mfc/reference/cframewndex-class.md#enabledocking). Ukotvit webu windows jsou umístěny v hraniční části klientské oblasti okna hlavního rámce.

Obvykle není nutné volat služby poskytované dokovacího webu, protože [cframewndex – třída](../../mfc/reference/cframewndex-class.md) zpracovává tyto služby.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CDockSite` třídy.

[!code-cpp[NVC_MFC_RibbonApp#27](../../mfc/reference/codesnippet/cpp/cdocksite-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject –](../../mfc/reference/cobject-class.md) [CCmdTarget –](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md) [CDockSite](../../mfc/reference/cdocksite-class.md)

## <a name="requirements"></a>Požadavky

**Header:** afxDockSite.h

##  <a name="addrow"></a>  CDockSite::AddRow

```
CDockingPanesRow* AddRow(
    POSITION pos,
    int nHeight);
```

### <a name="parameters"></a>Parametry

[in] *pos*<br/>

[in] *nHeight*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="adjustdockinglayout"></a>  CDockSite::AdjustDockingLayout

```
virtual void AdjustDockingLayout();
```

### <a name="remarks"></a>Poznámky

##  <a name="adjustlayout"></a>  CDockSite::AdjustLayout

```
virtual void AdjustLayout();
```

### <a name="remarks"></a>Poznámky

##  <a name="aligndocksite"></a>  CDockSite::AlignDockSite

```
void AlignDockSite(
    const CRect& rectToAlignBy,
    CRect& rectResult,
    BOOL bMoveImmediately);
```

### <a name="parameters"></a>Parametry

[in] *rectToAlignBy*<br/>

[in] *rectResult*<br/>

[in] *bMoveImmediately*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="calcfixedlayout"></a>  CDockSite::CalcFixedLayout

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

##  <a name="canacceptpane"></a>  CDockSite::CanAcceptPane

```
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>Parametry

[in] *pBar*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="createex"></a>  CDockSite::CreateEx

```
virtual BOOL CreateEx(
    DWORD dwStyleEx,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    DWORD dwControlBarStyle,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Parametry

[in] *dwStyleEx*<br/>

[in] *dwStyle*<br/>

[in] *rect*<br/>

[in] *pParentWnd*<br/>

[in] *dwControlBarStyle*<br/>

[in] *pContext*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="createrow"></a>  CDockSite::CreateRow

```
virtual CDockingPanesRow* CreateRow(
    CDockSite* pParentDockBar,
    int nOffset,
    int nRowHeight);
```

### <a name="parameters"></a>Parametry

[in] *pParentDockBar*<br/>

[in] *nOffset*<br/>

[in] *nRowHeight*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="dockpane"></a>  CDockSite::DockPane

```
virtual void DockPane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Parametry

[in] *pWnd*<br/>

[in] *dockMethod*<br/>

[in] *lpRect*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="dockpaneleftof"></a>  CDockSite::DockPaneLeftOf

Ukotvené podokno nalevo od jiného podokna.

```
virtual BOOL DockPaneLeftOf(
    CPane* pBarToDock,
    CPane* pTargetBar);
```

### <a name="parameters"></a>Parametry

*pBarToDock*<br/>
[out v] Ukazatel do podokna ukotvit vlevo od *pTargetBar*.

*pTargetBar*<br/>
[out v] Ukazatel do podokna cíl.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud se v podokně je ukotven úspěšně; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="doesallowdyninsertbefore"></a>  CDockSite::DoesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="findpanebyid"></a>  CDockSite::FindPaneByID

Vrátí podokno s daným ID.

```
CPane* FindPaneByID(UINT nID);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
[in] ID příkazu podokna nalezen.

### <a name="return-value"></a>Návratová hodnota

Ukazatel do podokna s ID zadaného příkazu, nebo hodnota NULL, pokud nebyl nalezen v podokně.

### <a name="remarks"></a>Poznámky

##  <a name="findrowindex"></a>  CDockSite::FindRowIndex

```
int FindRowIndex(CDockingPanesRow* pRow);
```

### <a name="parameters"></a>Parametry

[in] *pRow*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="fixupvirtualrects"></a>  CDockSite::FixupVirtualRects

```
virtual void FixupVirtualRects();
```

### <a name="remarks"></a>Poznámky

##  <a name="getdocksiteid"></a>  CDockSite::GetDockSiteID

```
virtual UINT GetDockSiteID() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="getdocksiterowslist"></a>  CDockSite::GetDockSiteRowsList

```
const CObList& GetDockSiteRowsList() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="getpanelist"></a>  CDockSite::GetPaneList

Vrátí seznam podoken, které jsou ukotveno na dokovacím místě.

```
const CObList& GetPaneList() const;
```

### <a name="return-value"></a>Návratová hodnota

Jen pro čtení odkaz na seznam podoken aktuálně v dokovací panel ukotven.

##  <a name="isaccessibilitycompatible"></a>  CDockSite::IsAccessibilityCompatible

```
virtual BOOL IsAccessibilityCompatible();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="isdragmode"></a>  CDockSite::IsDragMode

```
virtual BOOL IsDragMode() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="islastrow"></a>  CDockSite::IsLastRow

```
bool IsLastRow(CDockingPanesRow* pRow) const;
```

### <a name="parameters"></a>Parametry

[in] *pRow*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="isrectwithindocksite"></a>  CDockSite::IsRectWithinDockSite

```
BOOL IsRectWithinDockSite(
    CRect rect,
    CPoint& ptDelta);
```

### <a name="parameters"></a>Parametry

[in] *rect*<br/>

[in] *ptDelta*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="isresizable"></a>  CDockSite::IsResizable

```
virtual BOOL IsResizable() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="movepane"></a>  CDockSite::MovePane

```
virtual BOOL MovePane(
    CPane* pWnd,
    UINT nFlags,
    CPoint ptOffset);
```

### <a name="parameters"></a>Parametry

[in] *pWnd*<br/>

[in] *nFlags*<br/>

[in] *ptOffset*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="oninsertrow"></a>  CDockSite::OnInsertRow

```
virtual void OnInsertRow(POSITION pos);
```

### <a name="parameters"></a>Parametry

[in] *pos*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="onremoverow"></a>  CDockSite::OnRemoveRow

```
virtual void OnRemoveRow(
    POSITION pos,
    BOOL bByShow = FALSE);
```

### <a name="parameters"></a>Parametry

[in] *pos*<br/>

[in] *bByShow*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="onresizerow"></a>  CDockSite::OnResizeRow

```
virtual int OnResizeRow(
    CDockingPanesRow* pRowToResize,
    int nOffset);
```

### <a name="parameters"></a>Parametry

[in] *pRowToResize*<br/>

[in] *nOffset*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="onsizeparent"></a>  CDockSite::OnSizeParent

```
virtual void OnSizeParent(
    CRect& rectAvailable,
    UINT nSide,
    BOOL bExpand,
    int nOffset);
```

### <a name="parameters"></a>Parametry

[in] *rectAvailable*<br/>

[in] *nSide*<br/>

[in] *bExpand*<br/>

[in] *nOffset*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="onsetwindowpos"></a>  CDockSite::OnSetWindowPos

```
virtual BOOL OnSetWindowPos(
    const CWnd* pWndInsertAfter,
    const CRect& rectWnd,
    UINT nFlags);
```

### <a name="parameters"></a>Parametry

[in] *pWndInsertAfter*<br/>

[in] *rectWnd*<br/>

[in] *nFlags*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="onshowrow"></a>  CDockSite::OnShowRow

```
virtual void OnShowRow(
    POSITION pos,
    BOOL bShow);
```

### <a name="parameters"></a>Parametry

[in] *pos*<br/>

[in] *bShow*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="panefrompoint"></a>  CDockSite::PaneFromPoint

Vrátí podokno, které je ukotveno na dokovacím místě v místě určeném daný parametr.

```
virtual CPane* PaneFromPoint(CPoint pt);
```

### <a name="parameters"></a>Parametry

*pt*<br/>
[in] Bod, v souřadnicovém systému obrazovky, podokna pro načtení.

### <a name="return-value"></a>Návratová hodnota

Ukazatel do podokna umístěny v zadaném bodu nebo hodnota NULL, pokud žádné podokně nebyl nalezen zadaný okamžiku.

### <a name="remarks"></a>Poznámky

##  <a name="rectsidefrompoint"></a>  CDockSite::RectSideFromPoint

```
static int __stdcall RectSideFromPoint(
    const CRect& rect,
    const CPoint& point);
```

### <a name="parameters"></a>Parametry

[in] *rect*<br/>

[in] *bodu*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="removepane"></a>  CDockSite::RemovePane

```
virtual void RemovePane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>Parametry

[in] *pWnd*<br/>

[in] *dockMethod*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="removerow"></a>  CDockSite::RemoveRow

```
void RemoveRow(CDockingPanesRow* pRow);
```

### <a name="parameters"></a>Parametry

[in] *pRow*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="replacepane"></a>  CDockSite::ReplacePane

```
BOOL ReplacePane(
    CPane* pOldBar,
    CPane* pNewBar);
```

### <a name="parameters"></a>Parametry

[in] *pOldBar*<br/>

[in] *pNewBar*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="repositionpanes"></a>  CDockSite::RepositionPanes

```
virtual void RepositionPanes(CRect& rectNewClientArea);
```

### <a name="parameters"></a>Parametry

[in] *rectNewClientArea*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="resizedocksite"></a>  CDockSite::ResizeDockSite

```
void ResizeDockSite(
    int nNewWidth,
    int nNewHeight);
```

### <a name="parameters"></a>Parametry

[in] *nNewWidth*<br/>

[in] *nNewHeight*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="resizerow"></a>  CDockSite::ResizeRow

```
int ResizeRow(
    CDockingPanesRow* pRow,
    int nNewSize,
    BOOL bAdjustLayout = TRUE);
```

### <a name="parameters"></a>Parametry

[in] *pRow*<br/>

[in] *nNewSize*<br/>

[in] *bAdjustLayout*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="showpane"></a>  CDockSite::ShowPane

V podokně se zobrazí.

```
virtual BOOL ShowPane(
    CBasePane* pBar,
    BOOL bShow,
    BOOL bDelay,
    BOOL bActivate);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[out v] Ukazatel do podokna zobrazený nebo skrytý.

*bShow*<br/>
[in] TRUE, pokud chcete určit, že v podokně má být zobrazen; FALSE, pokud chcete určit, že v podokně jako skryté.

*bDelay*<br/>
[in] TRUE, pokud chcete určit, že rozložení v podokně zpoždění až poté, co se zobrazuje v podokně; v opačném případě hodnota FALSE.

*bActivate*<br/>
[in] Tento parametr se nepoužívá.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se v podokně zobrazený nebo skrytý úspěšně. FALSE, pokud zadaný podokně nepatří do této dokovacího webu.

### <a name="remarks"></a>Poznámky

Voláním této metody lze zobrazit nebo skrýt ukotveného podokna. Za normálních okolností není nutné volat `CDockSite::ShowPane` přímo, protože je volána v nadřazené okno rámce nebo základní podokně.

##  <a name="showrow"></a>  CDockSite::ShowRow

```
void ShowRow(
    CDockingPanesRow* pRow,
    BOOL bShow,
    BOOL bAdjustLayout);
```

### <a name="parameters"></a>Parametry

[in] *pRow*<br/>

[in] *bShow*<br/>

[in] *bAdjustLayout*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="swaprows"></a>  CDockSite::SwapRows

```
void SwapRows(
    CDockingPanesRow* pFirstRow,
    CDockingPanesRow* pSecondRow);
```

### <a name="parameters"></a>Parametry

[in] *pFirstRow*<br/>

[in] *pSecondRow*<br/>

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CBasePane – třída](../../mfc/reference/cbasepane-class.md)
