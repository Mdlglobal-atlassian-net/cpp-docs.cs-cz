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
ms.openlocfilehash: ae1a76e4cdd052ff44dcbd69d467c51741bcc2ff
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370142"
---
# <a name="clistview-class"></a>CListView – třída

Zjednodušuje použití ovládacího prvku seznamu a [clistctrl](../../mfc/reference/clistctrl-class.md), třídy, která zapouzdřuje funkce řízení seznamu, s architekturou zobrazení dokumentu knihovny MFC.

## <a name="syntax"></a>Syntaxe

```
class CListView : public CCtrlView
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CListView::CListView](#clistview)|Vytvoří `CListView` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CListView::GetListCtrl](#getlistctrl)|Vrátí ovládací prvek seznamu přidružený k zobrazení.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CListView::RemoveImageList](#removeimagelist)|Odebere zadaný seznam obrázků ze zobrazení seznamu.|

## <a name="remarks"></a>Poznámky

Další informace o této architektuře naleznete v přehledu pro [CView](../../mfc/reference/cview-class.md) třídy a křížové odkazy citované zde.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cview](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CListView`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcview.h

## <a name="clistviewclistview"></a><a name="clistview"></a>CListView::CListView

Vytvoří `CListView` objekt.

```
CListView();
```

## <a name="clistviewgetlistctrl"></a><a name="getlistctrl"></a>CListView::GetListCtrl

Volání této členské funkce získat odkaz na ovládací prvek seznamu přidružené k zobrazení.

```
CListCtrl& GetListCtrl() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na ovládací prvek seznamu přidružený k zobrazení.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCListView#7](../../atl/reference/codesnippet/cpp/clistview-class_1.cpp)]

## <a name="clistviewremoveimagelist"></a><a name="removeimagelist"></a>CListView::RemoveImageList

Odebere zadaný seznam obrázků ze zobrazení seznamu.

```
void RemoveImageList(int nImageList);
```

### <a name="parameters"></a>Parametry

*nSeznam obrázků*<br/>
Index na základě nuly obrázku odebrat.

## <a name="see-also"></a>Viz také

[Řádek řádku vzorku knihovny MFC](../../overview/visual-cpp-samples.md)<br/>
[CCtrlView – třída](../../mfc/reference/cctrlview-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CCtrlView – třída](../../mfc/reference/cctrlview-class.md)
