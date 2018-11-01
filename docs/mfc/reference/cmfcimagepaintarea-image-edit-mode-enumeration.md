---
title: CMFCImagePaintArea::IMAGE_EDIT_MODE – výčet
ms.date: 11/04/2016
f1_keywords:
- IMAGE_EDIT_MODE Enumeration
helpviewer_keywords:
- IMAGE_EDIT_MODE Enumeration method [MFC]
ms.assetid: e51db66a-fa1c-4766-9dac-a25b595f871a
ms.openlocfilehash: 6460a83d63a0dd08d8607061bf1deca471fad3c5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658039"
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
