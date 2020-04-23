---
title: CMFCDragFrameImpl – třída
ms.date: 10/18/2018
f1_keywords:
- CMFCDragFrameImpl
helpviewer_keywords:
- CMFCDragFrameImpl class [MFC]
ms.assetid: 500cd824-8188-43c2-8754-b7bb46b5648a
ms.openlocfilehash: 527fd089962e05c44a7e47b1ae52345116da4470
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752438"
---
# <a name="cmfcdragframeimpl-class"></a>CMFCDragFrameImpl – třída

Třída `CMFCDragFrameImpl` nakreslí obdélník přetažení, který se zobrazí, když uživatel přetáhne podokno ve standardním režimu ukotvení.
Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCDragFrameImpl
```

## <a name="remarks"></a>Poznámky

Objekt této třídy je vložen do každého [objektu CPane Class.](../../mfc/reference/cpane-class.md) Každé podokno, které `CanFloat` používá metodu, tedy zobrazí obdélník přetažení, když jej uživatel přetáhne.

Tloušťku obdélníku přetažení můžete řídit pomocí [AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](afx-global-data-structure.md#m_ndragframethicknessfloat) a [AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](afx-global-data-structure.md#m_ndragframethicknessdock).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CMFCDragFrameImpl](../../mfc/reference/cmfcdragframeimpl-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdragframeimpl.h

## <a name="cmfcdragframeimplenddrawdragframe"></a><a name="enddrawdragframe"></a>CMFCDragFrameImpl::EndDrawDragFrame

```cpp
void EndDrawDragFrame(BOOL bClearInternalRects = TRUE);
```

### <a name="parameters"></a>Parametry

[v] *bClearInternalRects*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmfcdragframeimplinit"></a><a name="init"></a>CMFCDragFrameImpl::Init

```cpp
void Init(CWnd* pDraggedWnd);
```

### <a name="parameters"></a>Parametry

[v] *pDraggedWnd*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmfcdragframeimplmovedragframe"></a><a name="movedragframe"></a>CMFCDragFrameImpl::MoveDragFrame

```cpp
void MoveDragFrame(BOOL bForceMove = FALSE);
```

### <a name="parameters"></a>Parametry

[v] *bForceMove*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmfcdragframeimplplacetabpredocking"></a><a name="placetabpredocking"></a>CMFCDragFrameImpl::PlaceTabPreDocking

```cpp
void PlaceTabPreDocking(
    CBaseTabbedPane* pTabbedBar,
    BOOL bFirstTime);

void PlaceTabPreDocking(CWnd* pCBarToPlaceOn);
```

### <a name="parameters"></a>Parametry

[v] *pTabbedBar*<br/>

[v] *bPrvní čas*<br/>

[v] *pCBarToPlaceOn*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmfcdragframeimplremovetabpredocking"></a><a name="removetabpredocking"></a>CMFCDragFrameImpl::RemoveTabPreDocking

```cpp
void RemoveTabPreDocking(CDockablePane* pOldTargetBar = NULL);
```

### <a name="parameters"></a>Parametry

[v] *pOldTargetBar*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmfcdragframeimplresetstate"></a><a name="resetstate"></a>CMFCDragFrameImpl::Stav obnovení

```cpp
void ResetState();
```

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CPane – třída](../../mfc/reference/cpane-class.md)
