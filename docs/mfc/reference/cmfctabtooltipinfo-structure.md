---
title: Cmfctabtooltipinfo – struktura
ms.date: 11/04/2016
f1_keywords:
- CMFCTabToolTipInfo
helpviewer_keywords:
- CMFCTabToolTipInfo struct
ms.assetid: 9c3b3fb9-1497-4d59-932b-0da9348dd5e2
ms.openlocfilehash: b785754a7970573c42fcc1d0736541416f522c9a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429160"
---
# <a name="cmfctabtooltipinfo-structure"></a>Cmfctabtooltipinfo – struktura

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

Následující příklad ukazuje jak `CMFCTabToolTipInfo` je používán [MDITabsDemo vzorku: aplikace s kartami MDI MFC](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Cmfctabtooltipinfo –](../../mfc/reference/cmfctabtooltipinfo-structure.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxbasetabctrl.h

##  <a name="m_ntabindex"></a>  CMFCTabToolTipInfo::m_nTabIndex

Určuje index ovládacího prvku karta.

```
int m_nTabIndex;
```

### <a name="remarks"></a>Poznámky

Index karty nad tím, které uživatel umístěný kurzor.

### <a name="example"></a>Příklad

Následující příklad ukazuje jak `m_nTabIndex` je používán [MDITabsDemo vzorku: aplikace s kartami MDI MFC](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

##  <a name="m_ptabwnd"></a>  CMFCTabToolTipInfo::m_pTabWnd

Ukazatel na ovládací prvek karty.

```
CMFCBaseTabCtrl* m_pTabWnd;
```

### <a name="example"></a>Příklad

Následující příklad ukazuje jak `m_pTabWnd` je používán [MDITabsDemo vzorku: aplikace s kartami MDI MFC](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

##  <a name="m_strtext"></a>  CMFCTabToolTipInfo::m_strText

Text popisku.

```
CString m_strText;
```

### <a name="remarks"></a>Poznámky

Pokud je řetězec prázdný, popisek se nezobrazí.

### <a name="example"></a>Příklad

Následující příklad ukazuje jak `m_strText` je používán [MDITabsDemo vzorku: aplikace s kartami MDI MFC](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
