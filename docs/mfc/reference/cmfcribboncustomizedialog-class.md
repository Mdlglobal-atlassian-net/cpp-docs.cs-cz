---
title: CMFCRibbonCustomizeDialog – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog
helpviewer_keywords:
- CMFCRibbonCustomizeDialog [MFC], CMFCRibbonCustomizeDialog
ms.assetid: ce67de7f-5eaa-4c75-9b94-f290f36df073
ms.openlocfilehash: a66c0a19c04e0a900b91c0c28c45bb9c766d25c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375210"
---
# <a name="cmfcribboncustomizedialog-class"></a>CMFCRibbonCustomizeDialog – třída

Zobrazí stránku **Přizpůsobení** pásu karet.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonCustomizeDialog : public CMFCPropertySheet
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CmFCRibbonCustomizeDialog::Dialogové okno Přizpůsobení cmfcribbon](#cmfcribboncustomizedialog)|Vytvoří `CMFCRibbonCustomizeDialog` objekt.|
|`CMFCRibbonCustomizeDialog::~CMFCRibbonCustomizeDialog`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|`CMFCRibbonCustomizeDialog::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objektu, který je přidružen k tomuto typu třídy.|

## <a name="remarks"></a>Poznámky

Knihovna MFC vytvoří tuto třídu automaticky, pokud nezpracujete zprávu AFX_WM_ON_RIBBON_CUSTOMIZE nebo pokud vrátíte 0 z obslužné rutiny zprávy.

Pokud chcete použít tuto třídu ve vaší **Customize** aplikaci k zobrazení dialogového okna `DoModal` Přizpůsobení pásu karet, stačí ji vytvořit instanci a zavolat metodu.

Vzhledem k tomu, že tato třída je odvozena z `CMFCPropertySheet` [třídy CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md), můžete přidat vlastní stránky pomocí rozhraní API.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

[CmFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)

[CmFCFCRibbonPřizpůsobenídialog](../../mfc/reference/cmfcribboncustomizedialog-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxribboncustomizedialog.h

## <a name="cmfcribboncustomizedialogcmfcribboncustomizedialog"></a><a name="cmfcribboncustomizedialog"></a>CmFCRibbonCustomizeDialog::Dialogové okno Přizpůsobení cmfcribbon

Vytvoří `CMFCRibbonCustomizeDialog` objekt.

```
CMFCRibbonCustomizeDialog(
    CWnd* pWndParent,
    CMFCRibbonBar* pRibbon);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
[v] Ukazatel na nadřazené okno (obvykle hlavní rámec).

*pStuha karet*<br/>
[v] Ukazatel na `CMFCRibbonBar` který je třeba přizpůsobit.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak `CMFCRibbonCustomizeDialog` vytvořit objekt.

[!code-cpp[NVC_MFC_RibbonApp#18](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizedialog-class_1.cpp)]

### <a name="remarks"></a>Poznámky

Konstruktor vytvoří instance objektu [třídy CMFCRibbonRibbonPropertyPage](../../mfc/reference/cmfcribboncustomizepropertypage-class.md) a přidá jej do kolekce stránek seznamu vlastností.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
