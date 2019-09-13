---
title: Vytvoření ovládacího prvku pro výběr data a času
ms.date: 11/04/2016
helpviewer_keywords:
- DateTimePicker control [MFC], creating
- CDateTimeCtrl class [MFC], creating
ms.assetid: 764ec2fb-98cd-478b-a5f2-d63f0bb12279
ms.openlocfilehash: de9baf63577d163b82da1c5977a6ccba6539c73a
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907592"
---
# <a name="creating-the-date-and-time-picker-control"></a>Vytvoření ovládacího prvku pro výběr data a času

Způsob vytvoření ovládacího prvku pro výběr data a času závisí na tom, jestli ovládací prvek používáte v dialogovém okně nebo když ho vytvoříte v nedialogovém okně.

### <a name="to-use-cdatetimectrl-directly-in-a-dialog-box"></a>Použití atributu CDateTimeCtrl přímo v dialogovém okně

1. V editoru dialogového okna přidejte ovládací prvek pro výběr data a času do prostředku šablony dialogového okna. Zadejte ID ovládacího prvku.

1. Určete všechny požadované styly pomocí dialogového okna vlastnosti ovládacího prvku pro výběr data a času.

1. Pomocí [Průvodce přidáním členské proměnné](../ide/adding-a-member-variable-visual-cpp.md) přidejte členskou proměnnou typu [atributu CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md) s vlastností Control. Tento člen můžete použít k volání `CDateTimeCtrl` členských funkcí.

1. Použijte [Průvodce třídami](reference/mfc-class-wizard.md) k mapování funkcí obslužných rutin ve třídě dialogového okna pro všechny [oznamovací](../mfc/processing-notification-messages-in-date-and-time-picker-controls.md) zprávy ovládacího prvku Výběr data a času, které je třeba zpracovat (viz [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md)).

1. V [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)nastavte další styly pro `CDateTimeCtrl` objekt.

### <a name="to-use-cdatetimectrl-in-a-nondialog-window"></a>Použití atributu CDateTimeCtrl v nedialogovém okně

1. Deklarujte ovládací prvek ve třídě zobrazení nebo okna.

1. Zavolejte členskou funkci [Create](../mfc/reference/ctabctrl-class.md#create) ovládacího prvku, případně v [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), případně jako funkci obslužné rutiny [Create](../mfc/reference/cwnd-class.md#oncreate) nadřazeného okna (Pokud se jedná o podtřídu ovládacího prvku). Nastavte styly ovládacího prvku.

## <a name="see-also"></a>Viz také:

[Používání atributu CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
