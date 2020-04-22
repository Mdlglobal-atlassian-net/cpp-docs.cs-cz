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
ms.openlocfilehash: d7f3b7c43d98c4f2c42d0c27c8e224f33e4b3301
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749122"
---
# <a name="clistview-class"></a>CListView – třída

Zjednodušuje použití ovládacího prvku seznamu a [clistctrl](../../mfc/reference/clistctrl-class.md), třídy, která zapouzdřuje funkce řízení seznamu, s architekturou zobrazení dokumentu knihovny MFC.

## <a name="syntax"></a>Syntaxe

```
class CListView : public CCtrlView
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CListView::CListView](#clistview)|Vytvoří `CListView` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CListView::GetListCtrl](#getlistctrl)|Vrátí ovládací prvek seznamu přidružený k zobrazení.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
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

```cpp
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
