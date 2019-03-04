---
title: CMFCStandardColorsPropertyPage Class
ms.date: 11/04/2016
helpviewer_keywords:
- CMFCStandardColorsPropertyPage class [MFC]
ms.assetid: b84b7cfb-bb24-4c65-804a-5b642cb64400
ms.openlocfilehash: 91cfa609c31e83c02cce8b2a474a9b66ec3ba56f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57260735"
---
# <a name="cmfcstandardcolorspropertypage-class"></a>CMFCStandardColorsPropertyPage Class

Představuje stránku vlastností, která uživatelé použít k výběru standardní barvy v dialogovém okně barev.

## <a name="syntax"></a>Syntaxe

```
class CMFCStandardColorsPropertyPage : public CPropertyPage
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|||
|-|-|
|Název|Popis|
|`CMFCStandardColorsPropertyPage::CMFCStandardColorsPropertyPage`|Výchozí konstruktor.|

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|Název|Popis|
|`CMFCStandardColorsPropertyPage::CreateObject`|Rozhraní používá k vytvoření dynamické instance tohoto typu třídy.|
|`CMFCStandardColorsPropertyPage::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|

### <a name="remarks"></a>Poznámky

`CMFCColorDialog` Třída používá tuto třídu zobrazíte na stránce vlastností standardní barvu. Další informace o `CMFCColorDialog`, naleznete v tématu [cmfccolordialog – třída](../../mfc/reference/cmfccolordialog-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCStandardColorsPropertyPage](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxstandardcolorspropertypage.h

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorDialog – třída](../../mfc/reference/cmfccolordialog-class.md)<br/>
[CMFCCustomColorsPropertyPage – třída](../../mfc/reference/cmfccustomcolorspropertypage-class.md)
