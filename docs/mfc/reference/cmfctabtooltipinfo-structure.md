---
title: CmFCTabTabTipInfo struktura
ms.date: 11/04/2016
f1_keywords:
- CMFCTabToolTipInfo
helpviewer_keywords:
- CMFCTabToolTipInfo struct
ms.assetid: 9c3b3fb9-1497-4d59-932b-0da9348dd5e2
ms.openlocfilehash: a507d1e69b3524074e50fde0e87fc5ebb6e5ca03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367343"
---
# <a name="cmfctabtooltipinfo-structure"></a>CmFCTabTabTipInfo struktura

Tato struktura poskytuje informace o kartě MDI, nad kterou uživatel najede na druhou položku.

## <a name="syntax"></a>Syntaxe

```
struct CMFCTabToolTipInfo
```

## <a name="members"></a>Členové

### <a name="data-members"></a>Členové dat

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCTabToolTipInfo::m_nTabIndex](#m_ntabindex)|Určuje index ovládacího prvku karta.|
|[CMFCTabToolTipInfo::m_pTabWnd](#m_ptabwnd)|Ukazatel na ovládací prvek karta.|
|[CMFCTabToolTipInfo::m_strText](#m_strtext)|Text popisku.|

## <a name="remarks"></a>Poznámky

Ukazatel na `CMFCTabToolTipInfo` strukturu je předán jako parametr zprávy AFX_WM_ON_GET_TAB_TOOLTIP. Tato zpráva je generována, když jsou povoleny karty MDI a uživatel najedou nad ovládacím prvkem karty.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak `CMFCTabToolTipInfo` se používá v [mditabsdemo ukázka: MFC tabulátory MDI aplikace](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CmFCTabToolTipInfo](../../mfc/reference/cmfctabtooltipinfo-structure.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxbasetabctrl.h

## <a name="cmfctabtooltipinfom_ntabindex"></a><a name="m_ntabindex"></a>CMFCTabToolTipInfo::m_nTabIndex

Určuje index ovládacího prvku karta.

```
int m_nTabIndex;
```

### <a name="remarks"></a>Poznámky

Index karty, na které uživatel je vznášející se.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak `m_nTabIndex` se používá v [mditabsdemo ukázka: MFC tabulátory MDI aplikace](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="cmfctabtooltipinfom_ptabwnd"></a><a name="m_ptabwnd"></a>CMFCTabToolTipInfo::m_pTabWnd

Ukazatel na ovládací prvek karta.

```
CMFCBaseTabCtrl* m_pTabWnd;
```

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak `m_pTabWnd` se používá v [mditabsdemo ukázka: MFC tabulátory MDI aplikace](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="cmfctabtooltipinfom_strtext"></a><a name="m_strtext"></a>CMFCTabToolTipInfo::m_strText

Text popisku.

```
CString m_strText;
```

### <a name="remarks"></a>Poznámky

Pokud je řetězec prázdný, popis ekvivalce se nezobrazí.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak `m_strText` se používá v [mditabsdemo ukázka: MFC tabulátory MDI aplikace](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
