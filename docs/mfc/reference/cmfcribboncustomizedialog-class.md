---
title: Cmfcribboncustomizedialog – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog
helpviewer_keywords:
- CMFCRibbonCustomizeDialog [MFC], CMFCRibbonCustomizeDialog
ms.assetid: ce67de7f-5eaa-4c75-9b94-f290f36df073
ms.openlocfilehash: d73fd05a775ac26f5d289a5233341102f40e9af3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259994"
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

[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)

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

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
