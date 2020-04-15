---
title: CTreeView – třída
ms.date: 11/04/2016
f1_keywords:
- CTreeView
- AFXCVIEW/CTreeView
- AFXCVIEW/CTreeView::CTreeView
- AFXCVIEW/CTreeView::GetTreeCtrl
helpviewer_keywords:
- CTreeView [MFC], CTreeView
- CTreeView [MFC], GetTreeCtrl
ms.assetid: 5df583a6-d69f-42ca-9d8d-57e04558afff
ms.openlocfilehash: 2ef93152c83d3bbec2b89ada0596ee612b24701b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373291"
---
# <a name="ctreeview-class"></a>CTreeView – třída

Zjednodušuje použití stromového ovládacího prvku a [ctreectrl](../../mfc/reference/ctreectrl-class.md), třídy, která zapouzdřuje funkce řízení stromu, s architekturou zobrazení dokumentu knihovny MFC.

## <a name="syntax"></a>Syntaxe

```
class CTreeView : public CCtrlView
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CTreeView::CTreeView](#ctreeview)|Vytvoří `CTreeView` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CTreeView::GetTreeCtrl](#gettreectrl)|Vrátí ovládací prvek stromu přidružený k zobrazení.|

## <a name="remarks"></a>Poznámky

Další informace o této architektuře naleznete v přehledu pro [CView](../../mfc/reference/cview-class.md) třídy a křížové odkazy citované zde.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cview](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CTreeView`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcview.h

## <a name="ctreeviewctreeview"></a><a name="ctreeview"></a>CTreeView::CTreeView

Vytvoří `CTreeView` objekt.

```
CTreeView();
```

## <a name="ctreeviewgettreectrl"></a><a name="gettreectrl"></a>CTreeView::GetTreeCtrl

Vrátí odkaz na stromový ovládací prvek přidružený k zobrazení.

```
CTreeCtrl& GetTreeCtrl() const;
```

## <a name="see-also"></a>Viz také

[CCtrlView – třída](../../mfc/reference/cctrlview-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CView](../../mfc/reference/cview-class.md)<br/>
[CCtrlView – třída](../../mfc/reference/cctrlview-class.md)<br/>
[CTreeCtrl – třída](../../mfc/reference/ctreectrl-class.md)
