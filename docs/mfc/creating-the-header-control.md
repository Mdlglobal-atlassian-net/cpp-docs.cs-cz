---
title: Vytvoření ovládacího prvku záhlaví
ms.date: 11/04/2016
helpviewer_keywords:
- CHeaderCtrl class [MFC], creating
- header controls [MFC], creating
ms.assetid: 7864d9d2-4a2c-4622-b58b-7b110a1e28d2
ms.openlocfilehash: 99269214666c324214422ad989dbbd8bff6fc345
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508807"
---
# <a name="creating-the-header-control"></a>Vytvoření ovládacího prvku záhlaví

Ovládací prvek záhlaví není přímo k dispozici v editoru dialogových oken (i když můžete přidat ovládací prvek seznam, který obsahuje ovládací prvek záhlaví).

### <a name="to-put-a-header-control-in-a-dialog-box"></a>Vložení ovládacího prvku záhlaví do dialogového okna

1. Ručně vložte členskou proměnnou typu [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md) do vaší třídy dialogu.

1. V [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)vytvořte a nastavte styly pro `CHeaderCtrl`, umístěte ho a zobrazte.

1. Přidejte položky do ovládacího prvku záhlaví.

1. Použijte okno Vlastnosti k mapování funkcí obslužných rutin ve třídě dialogového okna pro všechny zprávy oznámení ovládacího prvku záhlaví, které je třeba zpracovat (viz [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md)).

### <a name="to-put-a-header-control-in-a-view-not-a-clistview"></a>Vložení ovládacího prvku záhlaví do zobrazení (ne do CListView –)

1. Do třídy zobrazení vložte objekt [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md) .

1. Styl, umístění a zobrazení okna ovládacího prvku záhlaví v členské funkci zobrazení. [](../mfc/reference/cview-class.md#oninitialupdate)

1. Přidejte položky do ovládacího prvku záhlaví.

1. Použijte okno Vlastnosti k mapování funkcí obslužných rutin ve třídě zobrazení pro všechny zprávy oznámení ovládacího prvku záhlaví, které je třeba zpracovat (viz [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md)).

V obou případech je vložený objekt ovládacího prvku vytvořen při vytvoření objektu zobrazení nebo dialogového okna. Pak je nutné zavolat [CHeaderCtrl:: Create](../mfc/reference/cheaderctrl-class.md#create) k vytvoření okna ovládacího prvku. Chcete-li ovládací prvek umístit, zavolejte [CHeaderCtrl:: layout](../mfc/reference/cheaderctrl-class.md#layout) , abyste určili počáteční velikost a polohu ovládacího prvku a [SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos) k nastavení požadované pozice. Pak přidejte položky, jak je popsáno v tématu [Přidání položek do ovládacího prvku záhlaví](../mfc/adding-items-to-the-header-control.md).

Další informace naleznete v tématu [vytvoření ovládacího prvku záhlaví](/windows/win32/Controls/header-controls) v Windows SDK.

## <a name="see-also"></a>Viz také:

[Používání atributu CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
