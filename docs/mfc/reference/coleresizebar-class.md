---
title: Coleresizebar – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleResizeBar
- AFXOLE/COleResizeBar
- AFXOLE/COleResizeBar::COleResizeBar
- AFXOLE/COleResizeBar::Create
dev_langs:
- C++
helpviewer_keywords:
- COleResizeBar [MFC], COleResizeBar
- COleResizeBar [MFC], Create
ms.assetid: 56a708d9-28c5-4eb0-9404-77b688d91c63
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf1e2b447b4cfe0e2f503d2263354f3537bbb849
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391381"
---
# <a name="coleresizebar-class"></a>Coleresizebar – třída

Typ ovládací panel, který podporuje změnu velikosti ve umístěných položek OLE.

## <a name="syntax"></a>Syntaxe

```
class COleResizeBar : public CControlBar
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[COleResizeBar::COleResizeBar](#coleresizebar)|Vytvoří `COleResizeBar` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleResizeBar::Create](#create)|Vytvoří a inicializuje podřízeného okna Windows a přidruží ji k `COleResizeBar` objektu.|

## <a name="remarks"></a>Poznámky

`COleResizeBar` objekty se zobrazí jako [crecttracker –](../../mfc/reference/crecttracker-class.md) šrafované ohraničení a vnější úchyty pro změnu velikosti.

`COleResizeBar` objekty jsou obvykle vložené členy odvozené od objektů oken s rámečkem [COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md) třídy.

Další informace najdete v článku [aktivace](../../mfc/activation-cpp.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[Ccontrolbar –](../../mfc/reference/ccontrolbar-class.md)

`COleResizeBar`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

##  <a name="coleresizebar"></a>  COleResizeBar::COleResizeBar

Vytvoří `COleResizeBar` objektu.

```
COleResizeBar();
```

### <a name="remarks"></a>Poznámky

Volání `Create` k vytvoření objektu změnu velikosti panelu.

##  <a name="create"></a>  COleResizeBar::Create

Vytvoří podřízené okno a přidruží ji k `COleResizeBar` objektu.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,
    UINT nID = AFX_IDW_RESIZE_BAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Ukazatel na nadřazené okno panelu změny velikosti.

*dwStyle*<br/>
Určuje, [styl okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) atributy.

*nID*<br/>
ID podřízené okno na změnu velikosti panelu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl vytvořen příčku; jinak 0.

## <a name="see-also"></a>Viz také

[Ukázky knihovny MFC SUPERPAD](../../visual-cpp-samples.md)<br/>
[CControlBar – třída](../../mfc/reference/ccontrolbar-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleServerDoc – třída](../../mfc/reference/coleserverdoc-class.md)
