---
title: Zprávy s oznámením pro posuvník
ms.date: 11/04/2016
helpviewer_keywords:
- CSliderCtrl class [MFC], notifications
- slider controls [MFC], notification messages
- messages, notification
- notifications [MFC], CSliderCtrl
ms.assetid: b9121104-3889-4a10-92bf-f3723f1af9d0
ms.openlocfilehash: 250170d99bfb73c21c6288e0c2b6c31adf4dcefc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50656027"
---
# <a name="slider-notification-messages"></a>Zprávy s oznámením pro posuvník

Ovládací prvek typu jezdec upozorní nadřazené okno ovládacího jeho akcí uživatele odesíláním nadřazené WM_HSCROLL nebo WM_VSCROLL zpráv, v závislosti na orientaci ovládacího prvku v ovládacím prvku posuvník. Pro zpracování těchto zprávách, přidejte obslužné rutiny pro zprávy WM_HSCROLL a WM_VSCROLL do nadřazeného okna. [OnHScroll](../mfc/reference/cwnd-class.md#onhscroll) a [OnVScroll](../mfc/reference/cwnd-class.md#onvscroll) členské funkce se předají kód upozornění, pozice posuvníku a ukazatel [atributu CSliderCtrl](../mfc/reference/csliderctrl-class.md) objektu. Všimněte si, že je ukazatel typu `CScrollBar *` i v případě, že odkazuje `CSliderCtrl` objektu. Budete muset tento ukazatel přetypovat, pokud potřebujete pracovat s ovládacím prvku posuvník.

Místo použití posuvník oznámení kódy, odeslat ovládacích prvků posuvník jinou sadu kódy upozornění. Ovládací prvek typu jezdec odesílá oznámení kódy TB_BOTTOM, TB_LINEDOWN, TB_LINEUP a TB_TOP pouze v případě, že uživatel pracuje s ovládacím prvkem posuvníku pomocí klávesnice. TB_THUMBPOSITION a TB_THUMBTRACK zprávy oznámení se odesílají jenom při uživatele se pomocí myši. Kódy TB_ENDTRACK TB_PAGEDOWN a TB_PAGEUP oznámení se odesílají v obou případech.

V následující tabulce jsou uvedeny zpráv s oznámením ovládacího prvku posuvníku a události (virtuální kódy kláves nebo události myši), které způsobují oznámení k odeslání. (Seznam kódů standardní virtuální klíče najdete v tématu winuser.)

|Oznámení|Události, která způsobila oznámení k odeslání|
|--------------------------|-------------------------------------------|
|TB_BOTTOM|VK_END|
|TB_ENDTRACK|WM_KEYUP (uživatel vydané klíč, který odeslal relevantní virtuální klíče kód)|
|TB_LINEDOWN|VK_RIGHT nebo VK_DOWN|
|TB_LINEUP|VK_LEFT nebo VK_UP|
|TB_PAGEDOWN|VK_NEXT (uživatel klikl na kanál pod nebo napravo od posuvník)|
|TB_PAGEUP|VK_PRIOR (uživatel klikl na kanál nad nebo nalevo od posuvník)|
|TB_THUMBPOSITION|WM_LBUTTONUP následující za zprávou TB_THUMBTRACK oznámení|
|TB_THUMBTRACK|Přesun posuvníku (uživatele kvůli usnadnění použití vypsány posuvník)|
|TB_TOP|VK_HOME|

## <a name="see-also"></a>Viz také

[Používání atributu CSliderCtrl](../mfc/using-csliderctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

