---
title: CGlobalUtils – třída
ms.date: 10/18/2018
f1_keywords:
- CGlobalUtils
- AFXGLOBALUTILS/CGlobalUtils
- AFXGLOBALUTILS/CGlobalUtils::AdjustRectToWorkArea
- AFXGLOBALUTILS/CGlobalUtils::CalcExpectedDockedRect
- AFXGLOBALUTILS/CGlobalUtils::CanBeAttached
- AFXGLOBALUTILS/CGlobalUtils::CanPaneBeInFloatingMultiPaneFrameWnd
- AFXGLOBALUTILS/CGlobalUtils::CheckAlignment
- AFXGLOBALUTILS/CGlobalUtils::CyFromString
- AFXGLOBALUTILS/CGlobalUtils::DecimalFromString
- AFXGLOBALUTILS/CGlobalUtils::FlipRect
- AFXGLOBALUTILS/CGlobalUtils::ForceAdjustLayout
- AFXGLOBALUTILS/CGlobalUtils::GetDockingManager
- AFXGLOBALUTILS/CGlobalUtils::GetOppositeAlignment
- AFXGLOBALUTILS/CGlobalUtils::GetPaneAndAlignFromPoint
- AFXGLOBALUTILS/CGlobalUtils::GetWndIcon
- AFXGLOBALUTILS/CGlobalUtils::SetNewParent
- AFXGLOBALUTILS/CGlobalUtils::StringFromCy
- AFXGLOBALUTILS/CGlobalUtils::StringFromDecimal
helpviewer_keywords:
- CGlobalUtils [MFC], AdjustRectToWorkArea
- CGlobalUtils [MFC], CalcExpectedDockedRect
- CGlobalUtils [MFC], CanBeAttached
- CGlobalUtils [MFC], CanPaneBeInFloatingMultiPaneFrameWnd
- CGlobalUtils [MFC], CheckAlignment
- CGlobalUtils [MFC], CyFromString
- CGlobalUtils [MFC], DecimalFromString
- CGlobalUtils [MFC], FlipRect
- CGlobalUtils [MFC], ForceAdjustLayout
- CGlobalUtils [MFC], GetDockingManager
- CGlobalUtils [MFC], GetOppositeAlignment
- CGlobalUtils [MFC], GetPaneAndAlignFromPoint
- CGlobalUtils [MFC], GetWndIcon
- CGlobalUtils [MFC], SetNewParent
- CGlobalUtils [MFC], StringFromCy
- CGlobalUtils [MFC], StringFromDecimal
ms.assetid: 2c5bd1a6-f80c-4e79-a476-b4ceebabfb2f
ms.openlocfilehash: dbac56ea7efca98218133b23657f8508ea6bac28
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752914"
---
# <a name="cglobalutils-class"></a>CGlobalUtils – třída

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CGlobalUtils
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CGlobalUtils::AdjustRectToWorkArea](#adjustrecttoworkarea)||
|[CGlobalUtils::CalcExpectedDockedRect](#calcexpecteddockedrect)||
|[CGlobalUtils::CanBeAttached](#canbeattached)||
|[CGlobalUtils::CanPaneBeInFloatingMultiPanePaneWnd](#canpanebeinfloatingmultipaneframewnd)||
|[CGlobalUtils::CheckAlignment](#checkalignment)||
|[CGlobalUtils::CyFromString](#cyfromstring)||
|[CGlobalUtils::DecimalFromString](#decimalfromstring)||
|[CGlobalUtils::FlipRect](#fliprect)||
|[CGlobalUtils::Rozložení ForceAdjustLayout](#forceadjustlayout)||
|[CGlobalUtils::GetDockingManager](#getdockingmanager)||
|[CGlobalUtils::GetOppositeAlignment](#getoppositealignment)||
|[CGlobalUtils::GetPaneAndAlignFromPoint](#getpaneandalignfrompoint)||
|[CGlobalUtils::GetWndIcon](#getwndicon)||
|[CGlobalUtils::SetNewParent](#setnewparent)||
|[CGlobalUtils::StringFromCy](#stringfromcy)||
|[CGlobalUtils::StringFromDecimal](#stringfromdecimal)||

## <a name="remarks"></a>Poznámky

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CGlobalUtils](../../mfc/reference/cglobalutils-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxglobalutils.h

## <a name="cglobalutilsadjustrecttoworkarea"></a><a name="adjustrecttoworkarea"></a>CGlobalUtils::AdjustRectToWorkArea

```cpp
void AdjustRectToworkArea(
    CRect& rect,
    CRect* pRectDelta = NULL);
```

### <a name="parameters"></a>Parametry

[dovnitř, ven] *rect*<br/>
[v] *pRectDelta*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cglobalutilscalcexpecteddockedrect"></a><a name="calcexpecteddockedrect"></a>CGlobalUtils::CalcExpectedDockedRect

```cpp
void CalcExpectedDockedRect(
    CPaneContainerManager& barContainerManager,
    CWnd* pWndTodock,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>Parametry

[v] *barContainerManager*<br/>

[v] *pWndTodock*<br/>

[v] *ptMouse*<br/>

[out] *rectVýsledek*<br/>

[out] *bDrawTab*<br/>

[out] *ppCílový bar*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cglobalutilscanbeattached"></a><a name="canbeattached"></a>CGlobalUtils::CanBeAttached

```
BOOL CanBeAttached(CWnd* pWnd) const;
```

### <a name="parameters"></a>Parametry

[v] *pWnd*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cglobalutilscanpanebeinfloatingmultipaneframewnd"></a><a name="canpanebeinfloatingmultipaneframewnd"></a>CGlobalUtils::CanPaneBeInFloatingMultiPanePaneWnd

```
BOOL CanPaneBeInFloatingMultiPaneFrameWnd(CWnd* pWnd) const;
```

### <a name="parameters"></a>Parametry

[v] *pWnd*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cglobalutilscheckalignment"></a><a name="checkalignment"></a>CGlobalUtils::CheckAlignment

```
BOOL CheckAlignment(
    CPoint point,
    CBasePane* pBar,
    int nSensitivity,
    const CDockingManager* pDockManager,
    BOOL bOuterEdge,
    DWORD& dwAlignment,
    DWORD dwEnabledDockBars = CBRS_ALIGN_ANY,
    LPCRECT lpRectBounds = NULL) const;
```

### <a name="parameters"></a>Parametry

[v] *bod*<br/>

[v] *pBar*<br/>

[v] *nCitlivost*<br/>

[v] *pDockManager*<br/>

[v] *bOuterEdge*<br/>

[out] *dwAlignment*<br/>

[v] *dwEnabledDockBars*<br/>

[v] *lpRectBounds*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cglobalutilscyfromstring"></a><a name="cyfromstring"></a>CGlobalUtils::CyFromString

```
BOOL CyFromString(
    CY& cy,
    LPCTSTR psz);
```

### <a name="parameters"></a>Parametry

[out] *cy*<br/>

[v] *psz*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cglobalutilsdecimalfromstring"></a><a name="decimalfromstring"></a>CGlobalUtils::DecimalFromString

```
BOOL DecimalFromString(
    DECIMAL& decimal,
    LPCTSTR psz);
```

### <a name="parameters"></a>Parametry

[out] *desítkové místo*<br/>

[v] *psz*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cglobalutilsfliprect"></a><a name="fliprect"></a>CGlobalUtils::FlipRect

```cpp
void FlipRect(
    CRect& rect,
    int nDegrees);
```

### <a name="parameters"></a>Parametry

[dovnitř, ven] *rect*<br/>
[v] *nStupně*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cglobalutilsforceadjustlayout"></a><a name="forceadjustlayout"></a>CGlobalUtils::Rozložení ForceAdjustLayout

```cpp
void ForceAdjustLayout(
    CDockingManager* pDockManager,
    BOOL bForce = FALSE,
    BOOL bForceInvisible = FALSE);
```

### <a name="parameters"></a>Parametry

[dovnitř, ven] *pDockManager*<br/>

[v] *bSíla*<br/>

[v] *bForceInvisible*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cglobalutilsgetdockingmanager"></a><a name="getdockingmanager"></a>CGlobalUtils::GetDockingManager

```
CDockingManager* GetDockingManager(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

[v] *pWnd*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cglobalutilsgetoppositealignment"></a><a name="getoppositealignment"></a>CGlobalUtils::GetOppositeAlignment

```
DWORD GetOppositeAlignment(DWORD dwAlign);
```

### <a name="parameters"></a>Parametry

[v] *dwZarovnat*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cglobalutilsgetpaneandalignfrompoint"></a><a name="getpaneandalignfrompoint"></a>CGlobalUtils::GetPaneAndAlignFromPoint

```
BOOL GetPaneAndAlignFromPoint(
    CPaneContainerManager& barContainerManager,
    CPoint pt,
    CDockablePane** ppTargetControlBar,
    DWORD& dwAlignment,
    BOOL& bTabArea,
    BOOL& bCaption);
```

### <a name="parameters"></a>Parametry

[v] *barContainerManager*<br/>

[v] *pt*<br/>

[out] *ppTargetControlBar*<br/>

[out] *dwAlignment*<br/>

[out] *bTabArea*<br/>

[out] *bTitulek*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cglobalutilsgetwndicon"></a><a name="getwndicon"></a>CGlobalUtils::GetWndIcon

```
HICON GetWndIcon(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

[v] *pWnd*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cglobalutilssetnewparent"></a><a name="setnewparent"></a>CGlobalUtils::SetNewParent

```cpp
void SetNewParent(
    CObList& lstControlBars,
    CWnd* pNewParent,
    BOOL bCheckVisibility = TRUE);
```

### <a name="parameters"></a>Parametry

[v] *LstControlBars*<br/>

[v] *pNewParent*<br/>

[v] *bCheckVisibility*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cglobalutilsstringfromcy"></a><a name="stringfromcy"></a>CGlobalUtils::StringFromCy

```
BOOL StringFromCy(
    CString& str,
    CY& cy);
```

### <a name="parameters"></a>Parametry

[out] *str*<br/>

[v] *cy*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cglobalutilsstringfromdecimal"></a><a name="stringfromdecimal"></a>CGlobalUtils::StringFromDecimal

```
BOOL StringFromDecimal(
    CString& str,
    DECIMAL& decimal);
```

### <a name="parameters"></a>Parametry

[out] *str*<br/>

[v] *desítkové místo*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
