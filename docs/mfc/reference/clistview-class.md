---
title: CListView – třída
ms.date: 11/04/2016
f1_keywords:
- CListView
- AFXCVIEW/CListView
- AFXCVIEW/CListView::CListView
- AFXCVIEW/CListView::GetListCtrl
- AFXCVIEW/CListView::RemoveImageList
helpviewer_keywords:
- CListView [MFC], CListView
- CListView [MFC], GetListCtrl
- CListView [MFC], RemoveImageList
ms.assetid: 7626bdb2-a1b8-4eab-b631-6743710a8432
ms.openlocfilehash: 698e37b2853a2ca3698ee0a426c8ded688c99c58
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "58776619"
---
# <a name="clistview-class"></a>CListView – třída

Zjednodušuje použití ovládacího prvku seznam a [CListCtrl](../../mfc/reference/clistctrl-class.md), třídy, která zapouzdřuje funkce ovládacího prvku seznam architektuře document / view knihovny MFC.

## <a name="syntax"></a>Syntaxe

```
class CListView : public CCtrlView
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CListView::CListView](#clistview)|Vytvoří `CListView` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CListView::GetListCtrl](#getlistctrl)|Vrátí ovládací prvek seznamu, který je přidružený k zobrazení.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[CListView::RemoveImageList](#removeimagelist)|Odebere seznam zadané bitové kopie ze zobrazení seznamu.|

## <a name="remarks"></a>Poznámky

Další informace na této architektuře, najdete v přehledu pro [CView](../../mfc/reference/cview-class.md) třídy a křížové odkazy uvedené existuje.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget –](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CListView`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcview.h

##  <a name="clistview"></a>  CListView::CListView

Vytvoří `CListView` objektu.

```
CListView();
```

##  <a name="getlistctrl"></a>  CListView::GetListCtrl

Voláním této členské funkce k získání odkazu na ovládací prvek seznamu, který je přidružený k zobrazení.

```
CListCtrl& GetListCtrl() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na ovládací prvek seznamu, který je přidružený k zobrazení.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCListView#7](../../atl/reference/codesnippet/cpp/clistview-class_1.cpp)]

##  <a name="removeimagelist"></a>  CListView::RemoveImageList

Odebere seznam zadané bitové kopie ze zobrazení seznamu.

```
void RemoveImageList(int nImageList);
```

### <a name="parameters"></a>Parametry

*nImageList*<br/>
Z nuly vycházející index bitové kopie k odebrání.

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC ROWLIST](../../overview/visual-cpp-samples.md)<br/>
[Cctrlview – třída](../../mfc/reference/cctrlview-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Cctrlview – třída](../../mfc/reference/cctrlview-class.md)
