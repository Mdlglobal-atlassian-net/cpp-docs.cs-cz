---
title: Cmfcstandardcolorspropertypage – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CMFCStandardColorsPropertyPage class [MFC]
ms.assetid: b84b7cfb-bb24-4c65-804a-5b642cb64400
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 475780db8883fe9a8c8393648876764406cee376
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380591"
---
# <a name="cmfcstandardcolorspropertypage-class"></a>Cmfcstandardcolorspropertypage – třída

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

[CPropertyPage –](../../mfc/reference/cpropertypage-class.md)

[Cmfcstandardcolorspropertypage –](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxstandardcolorspropertypage.h

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorDialog – třída](../../mfc/reference/cmfccolordialog-class.md)<br/>
[CMFCCustomColorsPropertyPage – třída](../../mfc/reference/cmfccustomcolorspropertypage-class.md)
