---
title: CMFCTabToolTipInfo Structure
ms.date: 11/04/2016
f1_keywords:
- CMFCTabToolTipInfo
helpviewer_keywords:
- CMFCTabToolTipInfo struct
ms.assetid: 9c3b3fb9-1497-4d59-932b-0da9348dd5e2
ms.openlocfilehash: 87c8820bc33f3a344933faa797a9fc60d2422b13
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252955"
---
# <a name="cmfctabtooltipinfo-structure"></a>CMFCTabToolTipInfo Structure

Tato struktura obsahuje informace o kartě MDI, která je uživatel najede myší.

## <a name="syntax"></a>Syntaxe

```
struct CMFCTabToolTipInfo
```

## <a name="members"></a>Členové

### <a name="data-members"></a>Datové členy

|Název|Popis|
|----------|-----------------|
|[CMFCTabToolTipInfo::m_nTabIndex](#m_ntabindex)|Určuje index ovládacího prvku karta.|
|[CMFCTabToolTipInfo::m_pTabWnd](#m_ptabwnd)|Ukazatel na ovládací prvek karty.|
|[CMFCTabToolTipInfo::m_strText](#m_strtext)|Text popisku.|

## <a name="remarks"></a>Poznámky

Ukazatel `CMFCTabToolTipInfo` struktura je předán jako parametr AFX_WM_ON_GET_TAB_TOOLTIP zprávy. Tato zpráva se vygeneruje, když jsou povolené karet MDI a uživatel najede myší na ovládací prvek karty.

## <a name="example"></a>Příklad

Následující příklad ukazuje jak `CMFCTabToolTipInfo` je používán [MDITabsDemo vzorku: Knihovny MFC s kartami MDI aplikaci](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CMFCTabToolTipInfo](../../mfc/reference/cmfctabtooltipinfo-structure.md)

## <a name="requirements"></a>Požadavky

**Header:** afxbasetabctrl.h

##  <a name="m_ntabindex"></a>  CMFCTabToolTipInfo::m_nTabIndex

Určuje index ovládacího prvku karta.

```
int m_nTabIndex;
```

### <a name="remarks"></a>Poznámky

Index karty nad tím, které uživatel umístěný kurzor.

### <a name="example"></a>Příklad

Následující příklad ukazuje jak `m_nTabIndex` je používán [MDITabsDemo vzorku: Knihovny MFC s kartami MDI aplikaci](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

##  <a name="m_ptabwnd"></a>  CMFCTabToolTipInfo::m_pTabWnd

Ukazatel na ovládací prvek karty.

```
CMFCBaseTabCtrl* m_pTabWnd;
```

### <a name="example"></a>Příklad

Následující příklad ukazuje jak `m_pTabWnd` je používán [MDITabsDemo vzorku: Knihovny MFC s kartami MDI aplikaci](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

##  <a name="m_strtext"></a>  CMFCTabToolTipInfo::m_strText

Text popisku.

```
CString m_strText;
```

### <a name="remarks"></a>Poznámky

Pokud je řetězec prázdný, popisek se nezobrazí.

### <a name="example"></a>Příklad

Následující příklad ukazuje jak `m_strText` je používán [MDITabsDemo vzorku: Knihovny MFC s kartami MDI aplikaci](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
