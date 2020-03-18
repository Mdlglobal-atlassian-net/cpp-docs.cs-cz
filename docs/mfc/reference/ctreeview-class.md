---
title: CTreeView – – třída
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
ms.openlocfilehash: fec8379a3944d981672754274f50dd4e60f71b61
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421427"
---
# <a name="ctreeview-class"></a>CTreeView – – třída

Zjednodušuje použití ovládacího prvku stromu a třídy [CTreeCtrl](../../mfc/reference/ctreectrl-class.md), třída, která zapouzdřuje funkce ovládacího prvku stromu s architekturou zobrazení dokumentů a knihovny MFC.

## <a name="syntax"></a>Syntaxe

```
class CTreeView : public CCtrlView
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CTreeView –:: CTreeView –](#ctreeview)|Vytvoří objekt `CTreeView`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CTreeView –:: GetTreeCtrl](#gettreectrl)|Vrátí ovládací prvek stromu přidružený k zobrazení.|

## <a name="remarks"></a>Poznámky

Další informace o této architektuře naleznete v přehledu třídy [CView](../../mfc/reference/cview-class.md) a křížových odkazů, které jsou zde uvedeny.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CTreeView`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcview. h

##  <a name="ctreeview"></a>CTreeView –:: CTreeView –

Vytvoří objekt `CTreeView`.

```
CTreeView();
```

##  <a name="gettreectrl"></a>CTreeView –:: GetTreeCtrl

Vrátí odkaz na ovládací prvek stromu přidružený k zobrazení.

```
CTreeCtrl& GetTreeCtrl() const;
```

## <a name="see-also"></a>Viz také

[CCtrlView – třída](../../mfc/reference/cctrlview-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CView – třída](../../mfc/reference/cview-class.md)<br/>
[CCtrlView – třída](../../mfc/reference/cctrlview-class.md)<br/>
[CTreeCtrl – třída](../../mfc/reference/ctreectrl-class.md)
