---
title: Vytvoření ovládacího prvku měsíční kalendář
ms.date: 11/04/2016
helpviewer_keywords:
- CMonthCalCtrl class [MFC], creating
- month calendar controls [MFC], creating
- month calendar controls [MFC]
ms.assetid: 185cc642-85e9-4365-8a4c-d90b75b010f7
ms.openlocfilehash: 9e430a86c2ac08bde0f031a4c91b9ae5c6f570f3
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907494"
---
# <a name="creating-the-month-calendar-control"></a>Vytvoření ovládacího prvku měsíční kalendář

Způsob vytvoření ovládacího prvku měsíční kalendář závisí na tom, zda ovládací prvek používáte v dialogovém okně nebo když ho vytvoříte v nedialogovém okně.

### <a name="to-use-cmonthcalctrl-directly-in-a-dialog-box"></a>Použití atributu CMonthCalCtrl přímo v dialogovém okně

1. V editoru dialogového okna přidejte ovládací prvek měsíční kalendář do prostředku šablony dialogu. Zadejte ID ovládacího prvku.

1. Určete všechny požadované styly pomocí dialogového okna vlastnosti ovládacího prvku měsíční kalendář.

1. Pomocí [Průvodce přidáním členské proměnné](../ide/adding-a-member-variable-visual-cpp.md) přidejte členskou proměnnou typu [atributu CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md) s vlastností Control. Tento člen můžete použít k volání `CMonthCalCtrl` členských funkcí.

1. Použijte [Průvodce třídami](reference/mfc-class-wizard.md) k mapování funkcí obslužných rutin ve třídě dialogového okna pro všechny oznamovací zprávy ovládacího prvku měsíční kalendář, které potřebujete zpracovat (viz [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md)).

1. V [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)nastavte další styly pro `CMonthCalCtrl` objekt.

### <a name="to-use-cmonthcalctrl-in-a-nondialog-window"></a>Použití atributu CMonthCalCtrl v nedialogovém okně

1. Definujte ovládací prvek ve třídě zobrazení nebo okna.

1. Zavolejte členskou funkci [Create](../mfc/reference/cmonthcalctrl-class.md#create) ovládacího prvku, případně v [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), případně jako funkci obslužné rutiny [Create](../mfc/reference/cwnd-class.md#oncreate) nadřazeného okna (Pokud se jedná o podtřídu ovládacího prvku). Nastavte styly ovládacího prvku.

## <a name="see-also"></a>Viz také:

[Používání atributu CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
