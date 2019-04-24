---
title: Vytvoření ovládacího prvku záhlaví
ms.date: 11/04/2016
helpviewer_keywords:
- CHeaderCtrl class [MFC], creating
- header controls [MFC], creating
ms.assetid: 7864d9d2-4a2c-4622-b58b-7b110a1e28d2
ms.openlocfilehash: 669b13cf566f24bfcd5a29ae41af1cdb90513f73
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62242312"
---
# <a name="creating-the-header-control"></a>Vytvoření ovládacího prvku záhlaví

Ovládacího prvku záhlaví není k dispozici přímo v editoru dialogových oken (i když můžete přidat ovládací prvek seznamu, který obsahuje ovládací prvek záhlaví).

### <a name="to-put-a-header-control-in-a-dialog-box"></a>V dialogovém okně Vložit ovládacím prvkem záhlaví

1. Ručně vložit členské proměnné typu [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md) ve vlastní třídy dialogového okna.

1. V [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), vytvoření a nastavení stylů `CHeaderCtrl`, polohy a zobrazit je.

1. Přidání položek do ovládacího prvku záhlaví.

1. Použijte okno Vlastnosti pro mapování obslužné rutiny funkce ve třídě dialog pro všechna oznámení ovládacího prvku záhlaví zprávy je potřeba zpracovat (viz [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md)).

### <a name="to-put-a-header-control-in-a-view-not-a-clistview"></a>Vložit ovládací prvek záhlaví v zobrazení (nikoli CListView)

1. Vložit [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md) objekt ve třídě zobrazení.

1. Styl, pozice a zobrazit okno Ovládací prvek záhlaví v zobrazení [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) členskou funkci.

1. Přidání položek do ovládacího prvku záhlaví.

1. Použití mapování obslužné rutiny funkce ve třídě zobrazení pro všechna oznámení ovládacího prvku záhlaví zprávy v okně Vlastnosti potřeba zpracovat (viz [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md)).

V obou případech se vytvoří vloženému ovládacímu prvku objektu při vytvoření objektu zobrazení nebo dialogového okna. Pak je nutné volat [CHeaderCtrl::Create](../mfc/reference/cheaderctrl-class.md#create) vytvořit okno ovládacího prvku. Pro umístění ovládacího prvku, volejte [CHeaderCtrl::Layout](../mfc/reference/cheaderctrl-class.md#layout) určíte, počáteční velikost a pozice ovládacího prvku a [SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos) pozice chcete nastavit. Pak přidejte položky, jak je popsáno v [přidávání položek do ovládacího prvku záhlaví](../mfc/adding-items-to-the-header-control.md).

Další informace najdete v tématu [vytvoření ovládacího prvku záhlaví](/windows/desktop/Controls/header-controls) v sadě Windows SDK.

## <a name="see-also"></a>Viz také:

[Používání atributu CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
