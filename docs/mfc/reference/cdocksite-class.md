---
title: Třída CDocksite
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
ms.openlocfilehash: 471d68ead1bc5a11ace29f572647c4a7f2406b4e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753268"
---
# <a name="cdocksite-class"></a>Třída CDocksite

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

Poskytuje funkce pro uspořádání podoken, které jsou odvozeny z [CPane třídy](../../mfc/reference/cpane-class.md) do sad řádků.

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
|[CDockSite::Upravit rozložení](#adjustlayout)|(Přepíše [CBasePane::AdjustLayout](../../mfc/reference/cbasepane-class.md#adjustlayout).)|
|[CDockSite::AlignDockSite](#aligndocksite)||
|[CDockSite::CalcFixedLayout](#calcfixedlayout)|(Přepíše [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CDockSite::CanAcceptPane](#canacceptpane)|(Přepíše [CBasePane::CanAcceptPane](../../mfc/reference/cbasepane-class.md#canacceptpane).)|
|[CDockSite::CreateEx](#createex)|(Přepíše [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).)|
|[CDockSite::CreateRow](#createrow)||
|[CDockSite::DockPane](#dockpane)|(Přepíše [CBasePane::DockPane](../../mfc/reference/cbasepane-class.md#dockpane).)|
|[CDockSite::DoesAllowDynInsertPřed](#doesallowdyninsertbefore)|(Přepíše [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CDockSite::FindRowIndex](#findrowindex)||
|[CDockSite::FixupVirtualRects](#fixupvirtualrects)||
|[CDocksite::GetdocksiteID](#getdocksiteid)||
|[CDockSite::GetDockSiteRowsList](#getdocksiterowslist)||
|[CDockSite::Kompatibilní s isaccessibility](#isaccessibilitycompatible)|(Přepíše `CBasePane::IsAccessibilityCompatible`.)|
|[CDockSite::IsDragMode](#isdragmode)||
|[CDockSite::IsLastRow](#islastrow)||
|[CDockSite::IsRectWithinDockSite](#isrectwithindocksite)||
|[CDockSite::Lze si](#isresizable)|(Přepíše [CBasePane::IsResizable](../../mfc/reference/cbasepane-class.md#isresizable).)|
|[CDockSite::MovePane](#movepane)||
|[CDockSite::OnInsertRow](#oninsertrow)||
|[CDockSite::OnRemoveRow](#onremoverow)||
|[CDockSite::OnResizeRow](#onresizerow)||
|[CDockSite::OnSetWindowPos](#onsetwindowpos)||
|[CDockSite::OnShowRow](#onshowrow)||
|[CDockSite::OnSizeParent](#onsizeparent)||
|[CDockSite::PaneFromPoint](#panefrompoint)|Vrátí podokno, které je ukotveno v lokalitě dock v bodě určeném daným parametrem.|
|[CDockSite::DockPaneLeftOf](#dockpaneleftof)|Ukotví podokno nalevo od jiného podokna.|
|[CDockSite::FindpaneByID](#findpanebyid)|Vrátí podokno, které je identifikováno daným ID.|
|[CDockSite::GetPaneList](#getpanelist)|Vrátí seznam podoken, které jsou ukotveny v lokalitě dock.|
|[CDockSite::RectSideFromPoint](#rectsidefrompoint)||
|[CDockSite::RemovePane](#removepane)||
|[CDockSite::RemoveRow](#removerow)||
|[CDockSite::ReplacePane](#replacepane)||
|[CDockSite::Přemístit podokna](#repositionpanes)||
|[CDockSite::ResizeDockSite](#resizedocksite)||
|[CDockSite::Změna velikostiřádku](#resizerow)||
|[CDockSite::Zobrazit](#showpane)|Zobrazí podokno.|
|[CDockSite::ShowRow](#showrow)||
|[CDockSite::SwapRows](#swaprows)||

## <a name="remarks"></a>Poznámky

Rozhraní vytvoří `CDockSite` objekty automaticky při volání [CFrameWndEx::EnableDocking](../../mfc/reference/cframewndex-class.md#enabledocking). Okna lokality docku jsou umístěna na okraji klientské oblasti v okně hlavního rámce.

Obvykle není třeba volat služby poskytované lokality dock, protože [CFrameWndEx Class](../../mfc/reference/cframewndex-class.md) zpracovává tyto služby.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CDockSite` třídy.

[!code-cpp[NVC_MFC_RibbonApp#27](../../mfc/reference/codesnippet/cpp/cdocksite-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)\
啦&nbsp;[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;啦&nbsp;[CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;啦&nbsp;[CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;啦&nbsp;[CDockSite](../../mfc/reference/cdocksite-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxDockSite.h

## <a name="cdocksiteaddrow"></a><a name="addrow"></a>CDockSite::AddRow

```
CDockingPanesRow* AddRow(
    POSITION pos,
    int nHeight);
```

### <a name="parameters"></a>Parametry

[v] *pos*<br/>

[v] *nVýška*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdocksiteadjustdockinglayout"></a><a name="adjustdockinglayout"></a>CDockSite::AdjustDockingLayout

```
virtual void AdjustDockingLayout();
```

### <a name="remarks"></a>Poznámky

## <a name="cdocksiteadjustlayout"></a><a name="adjustlayout"></a>CDockSite::Upravit rozložení

```
virtual void AdjustLayout();
```

### <a name="remarks"></a>Poznámky

## <a name="cdocksitealigndocksite"></a><a name="aligndocksite"></a>CDockSite::AlignDockSite

```cpp
void AlignDockSite(
    const CRect& rectToAlignBy,
    CRect& rectResult,
    BOOL bMoveImmediately);
```

### <a name="parameters"></a>Parametry

[v] *rectToAlignBy*<br/>

[v] *rectVýsledek*<br/>

[v] *bMoveOkamžitě*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cdocksitecalcfixedlayout"></a><a name="calcfixedlayout"></a>CDockSite::CalcFixedLayout

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

## <a name="cdocksitecanacceptpane"></a><a name="canacceptpane"></a>CDockSite::CanAcceptPane

```
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>Parametry

[v] *pBar*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdocksitecreateex"></a><a name="createex"></a>CDockSite::CreateEx

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

[v] *dwStyleEx*<br/>

[v] *dwStyl*<br/>

[v] *rect*<br/>

[v] *pParentWnd*<br/>

[v] *dwControlBarStyle*<br/>

[v] *pKontext*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdocksitecreaterow"></a><a name="createrow"></a>CDockSite::CreateRow

```
virtual CDockingPanesRow* CreateRow(
    CDockSite* pParentDockBar,
    int nOffset,
    int nRowHeight);
```

### <a name="parameters"></a>Parametry

[v] *pParentDockBar*<br/>

[v] *nOffset*<br/>

[v] *nRowHeight*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdocksitedockpane"></a><a name="dockpane"></a>CDockSite::DockPane

```
virtual void DockPane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Parametry

[v] *pWnd*<br/>

[v] *dockMethod*<br/>

[v] *lpRect*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cdocksitedockpaneleftof"></a><a name="dockpaneleftof"></a>CDockSite::DockPaneLeftOf

Ukotví podokno nalevo od jiného podokna.

```
virtual BOOL DockPaneLeftOf(
    CPane* pBarToDock,
    CPane* pTargetBar);
```

### <a name="parameters"></a>Parametry

*pBarToDock*<br/>
[dovnitř, ven] Ukazatel na podokno, které má být ukotveno vlevo od *pTargetBar*.

*pCílový panel*<br/>
[dovnitř, ven] Ukazatel na cílové podokno.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je podokno úspěšně ukotveno; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

## <a name="cdocksitedoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CDockSite::DoesAllowDynInsertPřed

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdocksitefindpanebyid"></a><a name="findpanebyid"></a>CDockSite::FindpaneByID

Vrátí podokno s daným ID.

```
CPane* FindPaneByID(UINT nID);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
[v] ID příkazu podokna, které má být nalezeno.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na podokno se zadaným ID příkazu nebo hodnotou NULL, pokud podokno nebylo nalezeno.

### <a name="remarks"></a>Poznámky

## <a name="cdocksitefindrowindex"></a><a name="findrowindex"></a>CDockSite::FindRowIndex

```
int FindRowIndex(CDockingPanesRow* pRow);
```

### <a name="parameters"></a>Parametry

[v] *pŘádek*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdocksitefixupvirtualrects"></a><a name="fixupvirtualrects"></a>CDockSite::FixupVirtualRects

```
virtual void FixupVirtualRects();
```

### <a name="remarks"></a>Poznámky

## <a name="cdocksitegetdocksiteid"></a><a name="getdocksiteid"></a>CDocksite::GetdocksiteID

```
virtual UINT GetDockSiteID() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdocksitegetdocksiterowslist"></a><a name="getdocksiterowslist"></a>CDockSite::GetDockSiteRowsList

```
const CObList& GetDockSiteRowsList() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdocksitegetpanelist"></a><a name="getpanelist"></a>CDockSite::GetPaneList

Vrátí seznam podoken, které jsou ukotveny v lokalitě dock.

```
const CObList& GetPaneList() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz jen pro čtení na seznam podoken, které jsou aktuálně ukotveny v dokovacílce.

## <a name="cdocksiteisaccessibilitycompatible"></a><a name="isaccessibilitycompatible"></a>CDockSite::Kompatibilní s isaccessibility

```
virtual BOOL IsAccessibilityCompatible();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdocksiteisdragmode"></a><a name="isdragmode"></a>CDockSite::IsDragMode

```
virtual BOOL IsDragMode() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdocksiteislastrow"></a><a name="islastrow"></a>CDockSite::IsLastRow

```
bool IsLastRow(CDockingPanesRow* pRow) const;
```

### <a name="parameters"></a>Parametry

[v] *pŘádek*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdocksiteisrectwithindocksite"></a><a name="isrectwithindocksite"></a>CDockSite::IsRectWithinDockSite

```
BOOL IsRectWithinDockSite(
    CRect rect,
    CPoint& ptDelta);
```

### <a name="parameters"></a>Parametry

[v] *rect*<br/>

[v] *ptDelta*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdocksiteisresizable"></a><a name="isresizable"></a>CDockSite::Lze si

```
virtual BOOL IsResizable() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdocksitemovepane"></a><a name="movepane"></a>CDockSite::MovePane

```
virtual BOOL MovePane(
    CPane* pWnd,
    UINT nFlags,
    CPoint ptOffset);
```

### <a name="parameters"></a>Parametry

[v] *pWnd*<br/>

[v] *nPříznaky*<br/>

[v] *ptOffset*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdocksiteoninsertrow"></a><a name="oninsertrow"></a>CDockSite::OnInsertRow

```
virtual void OnInsertRow(POSITION pos);
```

### <a name="parameters"></a>Parametry

[v] *pos*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cdocksiteonremoverow"></a><a name="onremoverow"></a>CDockSite::OnRemoveRow

```
virtual void OnRemoveRow(
    POSITION pos,
    BOOL bByShow = FALSE);
```

### <a name="parameters"></a>Parametry

[v] *pos*<br/>

[v] *bByZobrazit*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cdocksiteonresizerow"></a><a name="onresizerow"></a>CDockSite::OnResizeRow

```
virtual int OnResizeRow(
    CDockingPanesRow* pRowToResize,
    int nOffset);
```

### <a name="parameters"></a>Parametry

[v] *pRowToResize*<br/>

[v] *nOffset*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdocksiteonsizeparent"></a><a name="onsizeparent"></a>CDockSite::OnSizeParent

```
virtual void OnSizeParent(
    CRect& rectAvailable,
    UINT nSide,
    BOOL bExpand,
    int nOffset);
```

### <a name="parameters"></a>Parametry

[v] *rectAvailable*<br/>

[v] *nSide*<br/>

[v] *bRozbalit*<br/>

[v] *nOffset*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cdocksiteonsetwindowpos"></a><a name="onsetwindowpos"></a>CDockSite::OnSetWindowPos

```
virtual BOOL OnSetWindowPos(
    const CWnd* pWndInsertAfter,
    const CRect& rectWnd,
    UINT nFlags);
```

### <a name="parameters"></a>Parametry

[v] *pWndInsertPo*<br/>

[v] *rektWnd*<br/>

[v] *nPříznaky*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdocksiteonshowrow"></a><a name="onshowrow"></a>CDockSite::OnShowRow

```
virtual void OnShowRow(
    POSITION pos,
    BOOL bShow);
```

### <a name="parameters"></a>Parametry

[v] *pos*<br/>

[v] *bZobrazit*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cdocksitepanefrompoint"></a><a name="panefrompoint"></a>CDockSite::PaneFromPoint

Vrátí podokno, které je ukotveno v lokalitě dock v bodě určeném daným parametrem.

```
virtual CPane* PaneFromPoint(CPoint pt);
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
[v] Bod, v souřadnicích obrazovky, pro podokno načíst.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na podokno umístěné v zadaném bodě nebo NULL, pokud v zadaném bodě nebylo žádné podokno.

### <a name="remarks"></a>Poznámky

## <a name="cdocksiterectsidefrompoint"></a><a name="rectsidefrompoint"></a>CDockSite::RectSideFromPoint

```
static int __stdcall RectSideFromPoint(
    const CRect& rect,
    const CPoint& point);
```

### <a name="parameters"></a>Parametry

[v] *rect*<br/>

[v] *bod*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdocksiteremovepane"></a><a name="removepane"></a>CDockSite::RemovePane

```
virtual void RemovePane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>Parametry

[v] *pWnd*<br/>

[v] *dockMethod*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cdocksiteremoverow"></a><a name="removerow"></a>CDockSite::RemoveRow

```cpp
void RemoveRow(CDockingPanesRow* pRow);
```

### <a name="parameters"></a>Parametry

[v] *pŘádek*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cdocksitereplacepane"></a><a name="replacepane"></a>CDockSite::ReplacePane

```
BOOL ReplacePane(
    CPane* pOldBar,
    CPane* pNewBar);
```

### <a name="parameters"></a>Parametry

[v] *pOldBar*<br/>

[v] *pNewBar*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdocksiterepositionpanes"></a><a name="repositionpanes"></a>CDockSite::Přemístit podokna

```
virtual void RepositionPanes(CRect& rectNewClientArea);
```

### <a name="parameters"></a>Parametry

[v] *rectNewClientArea*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cdocksiteresizedocksite"></a><a name="resizedocksite"></a>CDockSite::ResizeDockSite

```cpp
void ResizeDockSite(
    int nNewWidth,
    int nNewHeight);
```

### <a name="parameters"></a>Parametry

[v] *nNová šířka*<br/>

[v] *nNewHeight*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cdocksiteresizerow"></a><a name="resizerow"></a>CDockSite::Změna velikostiřádku

```
int ResizeRow(
    CDockingPanesRow* pRow,
    int nNewSize,
    BOOL bAdjustLayout = TRUE);
```

### <a name="parameters"></a>Parametry

[v] *pŘádek*<br/>

[v] *nNová velikost*<br/>

[v] *bAdjustLayout*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdocksiteshowpane"></a><a name="showpane"></a>CDockSite::Zobrazit

Zobrazí podokno.

```
virtual BOOL ShowPane(
    CBasePane* pBar,
    BOOL bShow,
    BOOL bDelay,
    BOOL bActivate);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[dovnitř, ven] Ukazatel na podokno, které má být zobrazeno nebo skryto.

*bZobrazit*<br/>
[v] TRUE, chcete-li určit, že má být podokno zobrazeno; FALSE určit, že podokno má být skryté.

*bZpoždění*<br/>
[v] TRUE určit, že rozložení podokna by měla být odložena až po zobrazení podokna; jinak NEPRAVDA.

*bAktivovat*<br/>
[v] Tento parametr se nepoužívá.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud bylo podokno úspěšně zobrazeno nebo skryto. FALSE, pokud zadané podokno nepatří do tohoto ukotvení webu.

### <a name="remarks"></a>Poznámky

Volánítéto metody zobrazit nebo skrýt ukotvené podokna. Za normálních okolností `CDockSite::ShowPane` není nutné volat přímo, protože je volána nadřazeným oknem rámce nebo základním podoknem.

## <a name="cdocksiteshowrow"></a><a name="showrow"></a>CDockSite::ShowRow

```cpp
void ShowRow(
    CDockingPanesRow* pRow,
    BOOL bShow,
    BOOL bAdjustLayout);
```

### <a name="parameters"></a>Parametry

[v] *pŘádek*<br/>

[v] *bZobrazit*<br/>

[v] *bAdjustLayout*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cdocksiteswaprows"></a><a name="swaprows"></a>CDockSite::SwapRows

```cpp
void SwapRows(
    CDockingPanesRow* pFirstRow,
    CDockingPanesRow* pSecondRow);
```

### <a name="parameters"></a>Parametry

[v] *pFirstRow*<br/>

[v] *pSecondRow*<br/>

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CBasePane – třída](../../mfc/reference/cbasepane-class.md)
