---
title: CTreeView – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTreeView
- AFXCVIEW/CTreeView
- AFXCVIEW/CTreeView::CTreeView
- AFXCVIEW/CTreeView::GetTreeCtrl
dev_langs:
- C++
helpviewer_keywords:
- CTreeView [MFC], CTreeView
- CTreeView [MFC], GetTreeCtrl
ms.assetid: 5df583a6-d69f-42ca-9d8d-57e04558afff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a760e567718ad7a485ebe469903c7cbd566daccc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375395"
---
# <a name="ctreeview-class"></a>CTreeView – třída

Zjednodušuje použití ovládacího prvku strom a [CTreeCtrl](../../mfc/reference/ctreectrl-class.md), třídy, která zapouzdřuje funkce ovládacího prvku strom architektuře document / view knihovny MFC.

## <a name="syntax"></a>Syntaxe

```
class CTreeView : public CCtrlView
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CTreeView::CTreeView](#ctreeview)|Vytvoří `CTreeView` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CTreeView::GetTreeCtrl](#gettreectrl)|Vrátí ovládací prvek stromu přidružený k zobrazení.|

## <a name="remarks"></a>Poznámky

Další informace na této architektuře, najdete v přehledu pro [CView](../../mfc/reference/cview-class.md) třídy a křížové odkazy uvedené existuje.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[Cctrlview –](../../mfc/reference/cctrlview-class.md)

`CTreeView`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcview.h

##  <a name="ctreeview"></a>  CTreeView::CTreeView

Vytvoří `CTreeView` objektu.

```
CTreeView();
```

##  <a name="gettreectrl"></a>  CTreeView::GetTreeCtrl

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
