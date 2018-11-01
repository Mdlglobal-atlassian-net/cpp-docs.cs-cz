---
title: Cmfcbasetoolbar – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCBaseToolBar
- AFXBASETOOLBAR/CMFCBaseToolBar
- AFXBASETOOLBAR/CMFCBaseToolBar::GetDockingMode
- AFXBASETOOLBAR/CMFCBaseToolBar::GetMinSize
- AFXBASETOOLBAR/CMFCBaseToolBar::OnAfterChangeParent
helpviewer_keywords:
- CMFCBaseToolBar [MFC], GetDockingMode
- CMFCBaseToolBar [MFC], GetMinSize
- CMFCBaseToolBar [MFC], OnAfterChangeParent
ms.assetid: 5d79206d-55e4-46f8-b1b8-042e34d7f9da
ms.openlocfilehash: 84756eb177fcec1981f3f2ed018d57eb27df9823
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523696"
---
# <a name="cmfcbasetoolbar-class"></a>Cmfcbasetoolbar – třída

Základní třída pro panely nástrojů.

## <a name="syntax"></a>Syntaxe

```
class CMFCBaseToolBar : public CPane
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|`CMFCBaseToolBar::CMFCBaseToolBar`|Výchozí konstruktor.|
|`CMFCBaseToolBar::~CMFCBaseToolBar`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|`CMFCBaseToolBar::CreateObject`|Rozhraní používá k vytvoření dynamické instance tohoto typu třídy.|
|[CMFCBaseToolBar::GetDockingMode](#getdockingmode)|Vrátí režim ukotvení. (Přepíše [CBasePane::GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode).)|
|[CMFCBaseToolBar::GetMinSize](#getminsize)|Vrátí minimální velikost panelu nástrojů. (Přepíše [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).)|
|[CMFCBaseToolBar::OnAfterChangeParent](#onafterchangeparent)|Volá se rozhraním po změně nadřazené v podokně. (Přepíše [CBasePane::OnAfterChangeParent](../../mfc/reference/cbasepane-class.md#onafterchangeparent).)|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[Cmfcbasetoolbar –](../../mfc/reference/cmfcbasetoolbar-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxbasetoolbar.h

##  <a name="getdockingmode"></a>  CMFCBaseToolBar::GetDockingMode

Vrátí režim ukotvení.

```
virtual AFX_DOCK_TYPE GetDockingMode() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukotvení režimu.

##  <a name="getminsize"></a>  CMFCBaseToolBar::GetMinSize

Vrátí minimální velikost panelu nástrojů.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
[out] Minimální velikost panelu nástrojů.

##  <a name="onafterchangeparent"></a>  CMFCBaseToolBar::OnAfterChangeParent

Volá se rozhraním po změně nadřazené v podokně.

```
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```

### <a name="parameters"></a>Parametry

*pWndOldParent*<br/>
[in] Ukazatel na předchozí nadřazené okno.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
