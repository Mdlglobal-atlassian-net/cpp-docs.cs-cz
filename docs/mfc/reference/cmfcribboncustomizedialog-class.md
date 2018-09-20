---
title: Cmfcribboncustomizedialog – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonCustomizeDialog [MFC], CMFCRibbonCustomizeDialog
ms.assetid: ce67de7f-5eaa-4c75-9b94-f290f36df073
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a51fe21594bc900923b7d8d0ff30e8599a378da8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409347"
---
# <a name="cmfcribboncustomizedialog-class"></a>Cmfcribboncustomizedialog – třída

Zobrazí na pásu karet **vlastní** stránky.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonCustomizeDialog : public CMFCPropertySheet
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog](#cmfcribboncustomizedialog)|Vytvoří `CMFCRibbonCustomizeDialog` objektu.|
|`CMFCRibbonCustomizeDialog::~CMFCRibbonCustomizeDialog`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|`CMFCRibbonCustomizeDialog::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|

## <a name="remarks"></a>Poznámky

MFC vytvoří instanci této třídy automaticky pokud nezpracovává zprávy AFX_WM_ON_RIBBON_CUSTOMIZE nebo vrátí 0 z obslužné rutiny zprávy.

Pokud chcete použít tuto třídu v aplikaci zobrazit na pásu karet **vlastní** dialogové okno pole, stačí vytvořit její instanci a volat `DoModal` metody.

Protože tato třída je odvozena z [CMFCPropertySheet – třída](../../mfc/reference/cmfcpropertysheet-class.md), můžete přidat vlastní stránky pomocí `CMFCPropertySheet` rozhraní API.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

[CMFCPropertySheet –](../../mfc/reference/cmfcpropertysheet-class.md)

[Cmfcribboncustomizedialog –](../../mfc/reference/cmfcribboncustomizedialog-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxribboncustomizedialog.h

##  <a name="cmfcribboncustomizedialog"></a>  CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog

Vytvoří `CMFCRibbonCustomizeDialog` objektu.

```
CMFCRibbonCustomizeDialog(
    CWnd* pWndParent,
    CMFCRibbonBar* pRibbon);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
[in] Ukazatel do nadřazeného okna (obvykle hlavního rámce).

*pRibbon*<br/>
[in] Ukazatel `CMFCRibbonBar` , který je možné přizpůsobit.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit `CMFCRibbonCustomizeDialog` objektu.

[!code-cpp[NVC_MFC_RibbonApp#18](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizedialog-class_1.cpp)]

### <a name="remarks"></a>Poznámky

Vytvoří instanci konstruktoru [cmfcribboncustomizepropertypage – třída](../../mfc/reference/cmfcribboncustomizepropertypage-class.md) objektu a přidá jej do kolekce stránky vlastností.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
