---
title: Cmfcdragframeimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDragFrameImpl
dev_langs:
- C++
helpviewer_keywords:
- CMFCDragFrameImpl class [MFC]
ms.assetid: 500cd824-8188-43c2-8754-b7bb46b5648a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa4846ec2d6263e353dec05d145f6e2e33a59eb4
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062376"
---
# <a name="cmfcdragframeimpl-class"></a>Cmfcdragframeimpl – třída

`CMFCDragFrameImpl` Třídy vykresluje obdélník, který se zobrazí, když uživatel přetáhne podokno v režimu standardního ukotvení.
Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCDragFrameImpl
```

## <a name="remarks"></a>Poznámky

Objekt této třídy je vložený v každém [cpane – třída](../../mfc/reference/cpane-class.md) objektu. Díky tomu se každý podokno, které používá `CanFloat` metoda zobrazí obdélník přetažení, když ho uživatel přetáhne.

Tloušťka obdélník můžete řídit pomocí [AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](afx-global-data-structure.md#m_ndragframethicknessfloat) a [AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](afx-global-data-structure.md#m_ndragframethicknessdock).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Cmfcdragframeimpl –](../../mfc/reference/cmfcdragframeimpl-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdragframeimpl.h

##  <a name="enddrawdragframe"></a>  CMFCDragFrameImpl::EndDrawDragFrame

```
void EndDrawDragFrame(BOOL bClearInternalRects = TRUE);
```

### <a name="parameters"></a>Parametry

[in] *bClearInternalRects*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="init"></a>  CMFCDragFrameImpl::Init

```
void Init(CWnd* pDraggedWnd);
```

### <a name="parameters"></a>Parametry

[in] *pDraggedWnd*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="movedragframe"></a>  CMFCDragFrameImpl::MoveDragFrame

```
void MoveDragFrame(BOOL bForceMove = FALSE);
```

### <a name="parameters"></a>Parametry

[in] *bForceMove*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="placetabpredocking"></a>  CMFCDragFrameImpl::PlaceTabPreDocking

```
void PlaceTabPreDocking(
    CBaseTabbedPane* pTabbedBar,
    BOOL bFirstTime);

void PlaceTabPreDocking(CWnd* pCBarToPlaceOn);
```

### <a name="parameters"></a>Parametry

[in] *pTabbedBar*<br/>

[in] *bFirstTime*<br/>

[in] *pCBarToPlaceOn*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="removetabpredocking"></a>  CMFCDragFrameImpl::RemoveTabPreDocking

```
void RemoveTabPreDocking(CDockablePane* pOldTargetBar = NULL);
```

### <a name="parameters"></a>Parametry

[in] *pOldTargetBar*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="resetstate"></a>  CMFCDragFrameImpl::ResetState

```
void ResetState();
```

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CPane – třída](../../mfc/reference/cpane-class.md)