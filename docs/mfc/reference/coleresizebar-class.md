---
title: COleResizeBar – třída
ms.date: 11/04/2016
f1_keywords:
- COleResizeBar
- AFXOLE/COleResizeBar
- AFXOLE/COleResizeBar::COleResizeBar
- AFXOLE/COleResizeBar::Create
helpviewer_keywords:
- COleResizeBar [MFC], COleResizeBar
- COleResizeBar [MFC], Create
ms.assetid: 56a708d9-28c5-4eb0-9404-77b688d91c63
ms.openlocfilehash: beb0c37b6ac23310b7d5c8506fbdaf677dd74d8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376157"
---
# <a name="coleresizebar-class"></a>COleResizeBar – třída

Typ ovládacího panelu, který podporuje změna velikosti položek OLE na místě.

## <a name="syntax"></a>Syntaxe

```
class COleResizeBar : public CControlBar
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[COleResizeBar::COleResizeBar](#coleresizebar)|Vytvoří `COleResizeBar` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[COleResizeBar::Vytvořit](#create)|Vytvoří a inicializuje podřízené okno systému `COleResizeBar` Windows a přidruží jej k objektu.|

## <a name="remarks"></a>Poznámky

`COleResizeBar`objekty se zobrazí jako [CRectTracker](../../mfc/reference/crecttracker-class.md) se šrafovaným okrajem a vnějšími úchyty pro velikost.

`COleResizeBar`objekty jsou obvykle vložené členy objektů frame-window odvozených z třídy [COleIPFrameWnd.](../../mfc/reference/coleipframewnd-class.md)

Další informace naleznete v článku [Aktivace](../../mfc/activation-cpp.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Ovládací panel CControl](../../mfc/reference/ccontrolbar-class.md)

`COleResizeBar`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

## <a name="coleresizebarcoleresizebar"></a><a name="coleresizebar"></a>COleResizeBar::COleResizeBar

Vytvoří `COleResizeBar` objekt.

```
COleResizeBar();
```

### <a name="remarks"></a>Poznámky

Volání `Create` k vytvoření objektu pruhu změny velikosti.

## <a name="coleresizebarcreate"></a><a name="create"></a>COleResizeBar::Vytvořit

Vytvoří podřízené okno a přidruží ho k objektu. `COleResizeBar`

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,
    UINT nID = AFX_IDW_RESIZE_BAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Ukazatel na nadřazené okno panelu změny velikosti.

*dwStyl*<br/>
Určuje atributy [stylu okna.](../../mfc/reference/styles-used-by-mfc.md#window-styles)

*Nid*<br/>
Id podřízeného okna panelu změny velikosti.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl vytvořen pruh změny velikosti; jinak 0.

## <a name="see-also"></a>Viz také

[Vzorek mfc SUPERPAD](../../overview/visual-cpp-samples.md)<br/>
[CControlBar – třída](../../mfc/reference/ccontrolbar-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída COleServerDoc](../../mfc/reference/coleserverdoc-class.md)
