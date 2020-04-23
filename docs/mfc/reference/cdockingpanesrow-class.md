---
title: CDockingPanesRow – třída
ms.date: 10/18/2018
f1_keywords:
- CDockingPanesRow
- AFXDOCKINGPANESROW/CDockingPanesRow
- AFXDOCKINGPANESROW/CDockingPanesRow::AddPane
- AFXDOCKINGPANESROW/CDockingPanesRow::AddPaneFromRow
- AFXDOCKINGPANESROW/CDockingPanesRow::ArrangePanes
- AFXDOCKINGPANESROW/CDockingPanesRow::CalcFixedLayout
- AFXDOCKINGPANESROW/CDockingPanesRow::Create
- AFXDOCKINGPANESROW/CDockingPanesRow::ExpandStretchedPanes
- AFXDOCKINGPANESROW/CDockingPanesRow::ExpandStretchedPanesRect
- AFXDOCKINGPANESROW/CDockingPanesRow::FixupVirtualRects
- AFXDOCKINGPANESROW/CDockingPanesRow::GetAvailableLength
- AFXDOCKINGPANESROW/CDockingPanesRow::GetAvailableSpace
- AFXDOCKINGPANESROW/CDockingPanesRow::GetClientRect
- AFXDOCKINGPANESROW/CDockingPanesRow::GetDockSite
- AFXDOCKINGPANESROW/CDockingPanesRow::GetExtraSpace
- AFXDOCKINGPANESROW/CDockingPanesRow::GetGroupFromPane
- AFXDOCKINGPANESROW/CDockingPanesRow::GetID
- AFXDOCKINGPANESROW/CDockingPanesRow::GetMaxPaneSize
- AFXDOCKINGPANESROW/CDockingPanesRow::GetPaneCount
- AFXDOCKINGPANESROW/CDockingPanesRow::GetPaneList
- AFXDOCKINGPANESROW/CDockingPanesRow::GetRowAlignment
- AFXDOCKINGPANESROW/CDockingPanesRow::GetRowHeight
- AFXDOCKINGPANESROW/CDockingPanesRow::GetRowOffset
- AFXDOCKINGPANESROW/CDockingPanesRow::GetVisibleCount
- AFXDOCKINGPANESROW/CDockingPanesRow::GetWindowRect
- AFXDOCKINGPANESROW/CDockingPanesRow::HasPane
- AFXDOCKINGPANESROW/CDockingPanesRow::IsEmpty
- AFXDOCKINGPANESROW/CDockingPanesRow::IsExclusiveRow
- AFXDOCKINGPANESROW/CDockingPanesRow::IsHorizontal
- AFXDOCKINGPANESROW/CDockingPanesRow::IsVisible
- AFXDOCKINGPANESROW/CDockingPanesRow::Move
- AFXDOCKINGPANESROW/CDockingPanesRow::MovePane
- AFXDOCKINGPANESROW/CDockingPanesRow::OnResizePane
- AFXDOCKINGPANESROW/CDockingPanesRow::RedrawAll
- AFXDOCKINGPANESROW/CDockingPanesRow::RemovePane
- AFXDOCKINGPANESROW/CDockingPanesRow::ReplacePane
- AFXDOCKINGPANESROW/CDockingPanesRow::RepositionPanes
- AFXDOCKINGPANESROW/CDockingPanesRow::Resize
- AFXDOCKINGPANESROW/CDockingPanesRow::ResizeByPaneDivider
- AFXDOCKINGPANESROW/CDockingPanesRow::ScreenToClient
- AFXDOCKINGPANESROW/CDockingPanesRow::SetExtra
- AFXDOCKINGPANESROW/CDockingPanesRow::ShowDockSiteRow
- AFXDOCKINGPANESROW/CDockingPanesRow::ShowPane
- AFXDOCKINGPANESROW/CDockingPanesRow::UpdateVisibleState
helpviewer_keywords:
- CDockingPanesRow [MFC], AddPane
- CDockingPanesRow [MFC], AddPaneFromRow
- CDockingPanesRow [MFC], ArrangePanes
- CDockingPanesRow [MFC], CalcFixedLayout
- CDockingPanesRow [MFC], Create
- CDockingPanesRow [MFC], ExpandStretchedPanes
- CDockingPanesRow [MFC], ExpandStretchedPanesRect
- CDockingPanesRow [MFC], FixupVirtualRects
- CDockingPanesRow [MFC], GetAvailableLength
- CDockingPanesRow [MFC], GetAvailableSpace
- CDockingPanesRow [MFC], GetClientRect
- CDockingPanesRow [MFC], GetDockSite
- CDockingPanesRow [MFC], GetExtraSpace
- CDockingPanesRow [MFC], GetGroupFromPane
- CDockingPanesRow [MFC], GetID
- CDockingPanesRow [MFC], GetMaxPaneSize
- CDockingPanesRow [MFC], GetPaneCount
- CDockingPanesRow [MFC], GetPaneList
- CDockingPanesRow [MFC], GetRowAlignment
- CDockingPanesRow [MFC], GetRowHeight
- CDockingPanesRow [MFC], GetRowOffset
- CDockingPanesRow [MFC], GetVisibleCount
- CDockingPanesRow [MFC], GetWindowRect
- CDockingPanesRow [MFC], HasPane
- CDockingPanesRow [MFC], IsEmpty
- CDockingPanesRow [MFC], IsExclusiveRow
- CDockingPanesRow [MFC], IsHorizontal
- CDockingPanesRow [MFC], IsVisible
- CDockingPanesRow [MFC], Move
- CDockingPanesRow [MFC], MovePane
- CDockingPanesRow [MFC], OnResizePane
- CDockingPanesRow [MFC], RedrawAll
- CDockingPanesRow [MFC], RemovePane
- CDockingPanesRow [MFC], ReplacePane
- CDockingPanesRow [MFC], RepositionPanes
- CDockingPanesRow [MFC], Resize
- CDockingPanesRow [MFC], ResizeByPaneDivider
- CDockingPanesRow [MFC], ScreenToClient
- CDockingPanesRow [MFC], SetExtra
- CDockingPanesRow [MFC], ShowDockSiteRow
- CDockingPanesRow [MFC], ShowPane
- CDockingPanesRow [MFC], UpdateVisibleState
ms.assetid: e7a17832-0ebb-4bce-b799-cec9b60f76fe
ms.openlocfilehash: d7535ae6c5246a372fd1a48573716bb166991d4e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753309"
---
# <a name="cdockingpanesrow-class"></a>CDockingPanesRow – třída

Spravuje seznam podoken, které jsou umístěny ve stejném vodorovném nebo svislém řádku (sloupci) ukotvitého webu.

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CDockingPanesRow : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|`CDockingPanesRow::CDockingPanesRow`|Výchozí konstruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDockingPanesRow::AddPane](#addpane)||
|[CDockingPanesRow::AddPaneFromRow](#addpanefromrow)||
|[CDockingPanesRow::Uspořádat podokna](#arrangepanes)|Uspořádá podokna do řádku podle zadaného okraje a parametrů mezer.|
|[CDockingPanesRow::CalcFixedLayout](#calcfixedlayout)||
|[CDockingPanesRow::Vytvořit](#create)||
|[CDockingPanesRow::Roztaženírozených panetů](#expandstretchedpanes)||
|[CDockingPanesRow::ExpandStretchedPanesRect](#expandstretchedpanesrect)||
|[CDockingPanesRow::Opravavirtuálnírekty](#fixupvirtualrects)||
|[CDockingPanesRow::GetAvailableLength](#getavailablelength)||
|[CDockingPanesRow::GetAvailableSpace](#getavailablespace)||
|[CDockingPanesRow::GetClientRect](#getclientrect)||
|[CDockingPanesRow::GetDockSite](#getdocksite)||
|[CDockingPanesRow::GetExtraSpace](#getextraspace)||
|[CDockingPanesRow::GetGroupFromPane](#getgroupfrompane)||
|[CDockingPanesRow::GetID](#getid)||
|[CDockingPanesRow::GetMaxPaneSize](#getmaxpanesize)||
|[CDockingPanesRow::GetPaneCount](#getpanecount)||
|[CDockingPanesRow::GetPaneList](#getpanelist)||
|[CDockingPanesRow::GetRowAlignment](#getrowalignment)||
|[CDockingPanesRow::GetRowHeight](#getrowheight)||
|[CDockingPanesRow::GetRowOffset](#getrowoffset)||
|[CDockingPanesRow::GetVisibleCount](#getvisiblecount)||
|[CDockingPanesRow::GetWindowRect](#getwindowrect)||
|[CDockingPanesRow::HasPane](#haspane)||
|[CDockingPanesRow::IsEmpty](#isempty)||
|[CDockingPanesRow::IsExclusiveRow](#isexclusiverow)||
|[CDockingPanesRow::Jevodorovný](#ishorizontal)||
|[CDockingPanesRow::Jeviditelný](#isvisible)||
|[CDockingPanesRow::Přesunout](#move)||
|[CDockingPanesRow::MovePane](#movepane)||
|[CDockingPanesRow::OnResizePane](#onresizepane)||
|[CDockingPanesRow::PřekreslitVšechny](#redrawall)||
|[CDockingPanesRow::RemovePane](#removepane)||
|[CDockingPanesRow::ReplacePane](#replacepane)||
|[CDockingPanesRow::RepositionPanes](#repositionpanes)||
|[CDockingPanesRow::Změna velikosti](#resize)||
|[CDockingPanesRow::Změna velikostiMěřidlaPanDivider](#resizebypanedivider)||
|[CDockingPanesRow::ScreenToClient](#screentoclient)||
|[CDockingPanesRow::SetExtra](#setextra)||
|[CDockingPanesRow::ShowDockSiteRow](#showdocksiterow)||
|[CDockingPanesRow::ShowPane](#showpane)||
|[CDockingPanesRow::UpdateVisibleState](#updatevisiblestate)||

## <a name="remarks"></a>Poznámky

`CDockingPanesRow`objekty jsou vytvářeny interně objekty dokovací sítě.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak `CDockingPanesRow` získat objekt `CMFCAutoHideBar` z objektu.

[!code-cpp[NVC_MFC_RibbonApp#26](../../mfc/reference/codesnippet/cpp/cdockingpanesrow-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CDockingPanesRow](../../mfc/reference/cdockingpanesrow-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxDockingPanesRow.h

## <a name="cdockingpanesrowaddpane"></a><a name="addpane"></a>CDockingPanesRow::AddPane

```
virtual void AddPane(
    CPane* pControlBar,
    AFX_DOCK_METHOD dockMethod,
    LPCRECT lpRect = NULL,
    BOOL bAddLast = FALSE);
```

### <a name="parameters"></a>Parametry

[v] *pControlBar*<br/>

[v] *dockMethod*<br/>

[v] *lpRect*<br/>

[v] *bAddLast*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowaddpanefromrow"></a><a name="addpanefromrow"></a>CDockingPanesRow::AddPaneFromRow

```
virtual void AddPaneFromRow(
    CPane* pControlBar,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>Parametry

[v] *pControlBar*<br/>

[v] *dockMethod*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowarrangepanes"></a><a name="arrangepanes"></a>CDockingPanesRow::Uspořádat podokna

Uspořádá dokovací podokna do řádku podle zadaného okraje a parametrů mezer.

```
virtual void ArrangePanes(
    int nMargin,
    int nSpacing);
```

### <a name="parameters"></a>Parametry

*nMarže*<br/>
[v] Určuje posun prvního podokna v obrazových bodech od levého horního rohu řádku.

*nSpacing*<br/>
[v] Určuje mezery mezi podokny v obrazových bodech.

### <a name="remarks"></a>Poznámky

Volání této metody uspořádat podokna v řádku, kde budou ukotveny. Po volání této metody `CDockingPanesRow::FixupVirtualRects(FALSE, NULL)`je nutné volat .

## <a name="cdockingpanesrowcalcfixedlayout"></a><a name="calcfixedlayout"></a>CDockingPanesRow::CalcFixedLayout

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

## <a name="cdockingpanesrowcdockingpanesrow"></a><a name="cdockingpanesrow"></a>CDockingPanesRow::CDockingPanesRow

```
CDockingPanesRow(
    CDockSite* pParentDockBar,
    int nOffset,
    int nHeight);
```

### <a name="parameters"></a>Parametry

[v] *pParentDockBar*<br/>

[v] *nOffset*<br/>

[v] *nVýška*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowcreate"></a><a name="create"></a>CDockingPanesRow::Vytvořit

```
virtual BOOL Create();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowexpandstretchedpanes"></a><a name="expandstretchedpanes"></a>CDockingPanesRow::Roztaženírozených panetů

```cpp
void ExpandStretchedPanes();
```

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowexpandstretchedpanesrect"></a><a name="expandstretchedpanesrect"></a>CDockingPanesRow::ExpandStretchedPanesRect

```cpp
void ExpandStretchedPanesRect();
```

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowfixupvirtualrects"></a><a name="fixupvirtualrects"></a>CDockingPanesRow::Opravavirtuálnírekty

```cpp
void FixupVirtualRects(
    bool bMoveBackToVirtualRect,
    CPane* pBarToExclude = NULL);
```

### <a name="parameters"></a>Parametry

[v] *bMoveBackToVirtualRect*<br/>

[v] *pBarToVyloučit*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowgetavailablelength"></a><a name="getavailablelength"></a>CDockingPanesRow::GetAvailableLength

```
virtual int GetAvailableLength(BOOL bUseVirtualRect = FALSE) const;
```

### <a name="parameters"></a>Parametry

[v] *bUseVirtualRect*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowgetavailablespace"></a><a name="getavailablespace"></a>CDockingPanesRow::GetAvailableSpace

```
virtual void GetAvailableSpace(CRect& rect);
```

### <a name="parameters"></a>Parametry

[v] *rect*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowgetclientrect"></a><a name="getclientrect"></a>CDockingPanesRow::GetClientRect

```cpp
void GetClientRect(CRect& rect) const;
```

### <a name="parameters"></a>Parametry

[v] *rect*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowgetdocksite"></a><a name="getdocksite"></a>CDockingPanesRow::GetDockSite

```
CDockSite* GetDockSite() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowgetextraspace"></a><a name="getextraspace"></a>CDockingPanesRow::GetExtraSpace

```
int GetExtraSpace() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowgetgroupfrompane"></a><a name="getgroupfrompane"></a>CDockingPanesRow::GetGroupFromPane

```cpp
void GetGroupFromPane(
    CPane* pBar,
    CObList& lst);
```

### <a name="parameters"></a>Parametry

[v] *pBar*<br/>

[v] *lst*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowgetid"></a><a name="getid"></a>CDockingPanesRow::GetID

```
int GetID() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowgetmaxpanesize"></a><a name="getmaxpanesize"></a>CDockingPanesRow::GetMaxPaneSize

```
int GetMaxPaneSize(BOOL bSkipHiddenBars = TRUE) const;
```

### <a name="parameters"></a>Parametry

[v] *bSkipHiddenBars*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowgetpanecount"></a><a name="getpanecount"></a>CDockingPanesRow::GetPaneCount

```
int GetPaneCount() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowgetpanelist"></a><a name="getpanelist"></a>CDockingPanesRow::GetPaneList

```
const CObList& GetPaneList() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowgetrowalignment"></a><a name="getrowalignment"></a>CDockingPanesRow::GetRowAlignment

```
DWORD GetRowAlignment() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowgetrowheight"></a><a name="getrowheight"></a>CDockingPanesRow::GetRowHeight

```
int GetRowHeight() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowgetrowoffset"></a><a name="getrowoffset"></a>CDockingPanesRow::GetRowOffset

```
int GetRowOffset() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowgetvisiblecount"></a><a name="getvisiblecount"></a>CDockingPanesRow::GetVisibleCount

```
virtual int GetVisibleCount();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowgetwindowrect"></a><a name="getwindowrect"></a>CDockingPanesRow::GetWindowRect

```cpp
void GetWindowRect(CRect& rect) const;
```

### <a name="parameters"></a>Parametry

[v] *rect*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowhaspane"></a><a name="haspane"></a>CDockingPanesRow::HasPane

```
BOOL HasPane(CBasePane* pControlBar);
```

### <a name="parameters"></a>Parametry

[v] *pControlBar*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowisempty"></a><a name="isempty"></a>CDockingPanesRow::IsEmpty

```
virtual BOOL IsEmpty() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowisexclusiverow"></a><a name="isexclusiverow"></a>CDockingPanesRow::IsExclusiveRow

```
virtual BOOL IsExclusiveRow() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowishorizontal"></a><a name="ishorizontal"></a>CDockingPanesRow::Jevodorovný

```
bool IsHorizontal() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowisvisible"></a><a name="isvisible"></a>CDockingPanesRow::Jeviditelný

```
virtual BOOL IsVisible() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowmove"></a><a name="move"></a>CDockingPanesRow::Přesunout

```
virtual void Move(int nOffset);
```

### <a name="parameters"></a>Parametry

[v] *nOffset*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowmovepane"></a><a name="movepane"></a>CDockingPanesRow::MovePane

```cpp
void MovePane(
    CPane* pControlBar,
    CPoint ptOffset,
    BOOL bSwapControlBars,
    HDWP& hdwp);

void MovePane(
    CPane* pControlBar,
    CRect rectTarget,
    HDWP& hdwp);

void MovePane(
    CPane* pControlBar,
    int nOffset,
    bool bForward,
    HDWP& hdwp);

void MovePane(
    CPane* pControlBar,
    int nAbsolutOffset,
    HDWP& hdwp);
```

### <a name="parameters"></a>Parametry

[v] *pControlBar*<br/>

[v] *ptOffset*<br/>

[v] *bSwapControlBars*<br/>

[v] *hdwp*<br/>

[v] *rectTarget*<br/>

[v] *nOffset*<br/>

[v] *bVpřed*<br/>

[v] *nAbsolutOffset*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowonresizepane"></a><a name="onresizepane"></a>CDockingPanesRow::OnResizePane

```
virtual void OnResizePane(CBasePane* pControlBar);
```

### <a name="parameters"></a>Parametry

[v] *pControlBar*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowredrawall"></a><a name="redrawall"></a>CDockingPanesRow::PřekreslitVšechny

```cpp
void RedrawAll();
```

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowremovepane"></a><a name="removepane"></a>CDockingPanesRow::RemovePane

```
virtual void RemovePane(CPane* pControlBar);
```

### <a name="parameters"></a>Parametry

[v] *pControlBar*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowreplacepane"></a><a name="replacepane"></a>CDockingPanesRow::ReplacePane

```
virtual BOOL ReplacePane(
    CPane* pBarOld,
    CPane* pBarNew);
```

### <a name="parameters"></a>Parametry

[v] *pBarOld*<br/>

[v] *pBarNew*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowrepositionpanes"></a><a name="repositionpanes"></a>CDockingPanesRow::RepositionPanes

```
virtual void RepositionPanes(
    CRect& rectNewParentBarArea,
    UINT nSide = (UINT)-1,
    BOOL bExpand = FALSE,
    int nOffset = 0);
```

### <a name="parameters"></a>Parametry

[v] *rectNewParentBarArea*<br/>

[v] *nSide*<br/>

[v] *bRozbalit*<br/>

[v] *nOffset*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowresize"></a><a name="resize"></a>CDockingPanesRow::Změna velikosti

```
virtual int Resize(int nOffset);
```

### <a name="parameters"></a>Parametry

[v] *nOffset*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowresizebypanedivider"></a><a name="resizebypanedivider"></a>CDockingPanesRow::Změna velikostiMěřidlaPanDivider

```
virtual int ResizeByPaneDivider(int /*ignored*/);
```

### <a name="parameters"></a>Parametry

[v] *ignorováno*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowscreentoclient"></a><a name="screentoclient"></a>CDockingPanesRow::ScreenToClient

```cpp
void ScreenToClient(CRect& rect) const;
```

### <a name="parameters"></a>Parametry

[v] *rect*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowsetextra"></a><a name="setextra"></a>CDockingPanesRow::SetExtra

```cpp
void SetExtra(
    int nExtraSpace,
    AFX_ROW_ALIGNMENT rowExtraAlign);
```

### <a name="parameters"></a>Parametry

[v] *nExtraspace*<br/>

[v] *řádekExtraAlign*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowshowdocksiterow"></a><a name="showdocksiterow"></a>CDockingPanesRow::ShowDockSiteRow

```
virtual void ShowDockSiteRow(
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>Parametry

[v] *bZobrazit*<br/>

[v] *bZpoždění*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowshowpane"></a><a name="showpane"></a>CDockingPanesRow::ShowPane

```
virtual BOOL ShowPane(
    CPane* pControlBar,
    BOOL bShow,
    BOOL bDelay = FALSE);
```

### <a name="parameters"></a>Parametry

[v] *pControlBar*<br/>

[v] *bZobrazit*<br/>

[v] *bZpoždění*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cdockingpanesrowupdatevisiblestate"></a><a name="updatevisiblestate"></a>CDockingPanesRow::UpdateVisibleState

```
virtual void UpdateVisibleState(BOOL bDelay);
```

### <a name="parameters"></a>Parametry

[v] *bZpoždění*<br/>

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Třída CDocksite](../../mfc/reference/cdocksite-class.md)<br/>
[CPane – třída](../../mfc/reference/cpane-class.md)
