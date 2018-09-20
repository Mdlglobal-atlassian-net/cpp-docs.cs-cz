---
title: Cmfcimagepaintarea::image_edit_mode – výčet | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- IMAGE_EDIT_MODE Enumeration
dev_langs:
- C++
helpviewer_keywords:
- IMAGE_EDIT_MODE Enumeration method [MFC]
ms.assetid: e51db66a-fa1c-4766-9dac-a25b595f871a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 913a87383e617f331043751c4e3089acac744c7f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374641"
---
# <a name="cmfcimagepaintareaimageeditmode-enumeration"></a>CMFCImagePaintArea::IMAGE_EDIT_MODE – výčet

Určuje režim kreslení, který můžete použít ke změně obrázku v dialogovém okně editor obrázků.

## <a name="syntax"></a>Syntaxe

```
enum IMAGE_EDIT_MODE
{
    IMAGE_EDIT_MODE_PEN = 0,
    IMAGE_EDIT_MODE_FILL,
    IMAGE_EDIT_MODE_LINE,
    IMAGE_EDIT_MODE_RECT,
    IMAGE_EDIT_MODE_ELLIPSE,
    IMAGE_EDIT_MODE_COLOR
};
```

## <a name="members"></a>Členové

|||
|-|-|
|Název|Popis|
|IMAGE_EDIT_MODE_PEN|Použít k vykreslení jednotlivých pixelech.|
|IMAGE_EDIT_MODE_FILL|Použitou k vyplnění všechny sousedící oblasti, které obsahují barvu na aktuální umístění kurzoru.|
|IMAGE_EDIT_MODE_LINE|Používá k nakreslení čáry.|
|IMAGE_EDIT_MODE_RECT|Použít k vykreslení obdélníku.|
|IMAGE_EDIT_MODE_ELLIPSE|Umožňuje Nakreslit elipsu.|
|IMAGE_EDIT_MODE_COLOR|Slouží k nastavení aktuální barvu na barvu na aktuální pozici kurzoru.|

### <a name="remarks"></a>Poznámky

`CMFCImagePaintArea` a `CMFCImageEditorDialog` třídy používají tento výčet nastavit aktuální režim vykreslování. Režim kreslení a aktuální barva se používají k úpravě oblast obrázku v dialogovém okně editoru obrázků. Další informace o `CMFCImagePaintArea` a `CMFCImageEditorDialog`, naleznete v tématu [cmfcimagepaintarea – třída](../../mfc/reference/cmfcimagepaintarea-class.md) a [CMFCImageEditorDialog – třída](../../mfc/reference/cmfcimageeditordialog-class.md).

Při výběru barvy z obrázku pomocí režimu vykreslování IMAGE_EDIT_MODE_COLOR, nastaví rozhraní IMAGE_EDIT_MODE_PEN aktuální režim vykreslování.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afximagepaintarea.h

## <a name="see-also"></a>Viz také

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCImagePaintArea – třída](../../mfc/reference/cmfcimagepaintarea-class.md)<br/>
[CMFCImageEditorDialog – třída](../../mfc/reference/cmfcimageeditordialog-class.md)
