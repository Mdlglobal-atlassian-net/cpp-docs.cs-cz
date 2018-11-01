---
title: Vytvoření ovládacího prvku pro výběr data a času
ms.date: 11/04/2016
helpviewer_keywords:
- DateTimePicker control [MFC], creating
- CDateTimeCtrl class [MFC], creating
ms.assetid: 764ec2fb-98cd-478b-a5f2-d63f0bb12279
ms.openlocfilehash: 27a3a654a73300b7dd667d422fe84c73de524f3c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456120"
---
# <a name="creating-the-date-and-time-picker-control"></a>Vytvoření ovládacího prvku pro výběr data a času

Vytvoření prvku Výběr data a času závisí na tom, jestli jsou pomocí ovládacího prvku v dialogovém okně nebo vytváří v okně nondialog.

### <a name="to-use-cdatetimectrl-directly-in-a-dialog-box"></a>Použití atributu CDateTimeCtrl přímo v dialogovém okně

1. V editoru dialogového okna přidáte do šablony prostředku dialogového okna k datu a ovládacího prvku pro výběr času. Zadejte své ID ovládacího prvku.

1. Zadejte všechny styly potřeby pomocí dialogového okna Vlastnosti prvku Výběr data a času.

1. Použití [Průvodce přidáním členské proměnné](../ide/adding-a-member-variable-visual-cpp.md) přidat členskou proměnnou typu [atributu CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md) s vlastností ovládacího prvku. Tento člen můžete použít k volání `CDateTimeCtrl` členské funkce.

1. Použijte okno Vlastnosti pro mapování obslužné rutiny funkce ve třídě dialogového okna pro ovládací prvek výběru libovolné datum čas [oznámení](../mfc/processing-notification-messages-in-date-and-time-picker-controls.md) potřebujete zpracovávat zprávy (viz [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md)).

1. V [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), nastavte pro všechny další styly `CDateTimeCtrl` objektu.

### <a name="to-use-cdatetimectrl-in-a-nondialog-window"></a>V okně nondialog použití atributu CDateTimeCtrl

1. Deklarujte ve třídě zobrazení nebo okna ovládacího prvku.

1. Volání ovládacího prvku [vytvořit](../mfc/reference/ctabctrl-class.md#create) členské funkce, případně v [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), může být co nejdříve jako nadřazené okno [OnCreate](../mfc/reference/cwnd-class.md#oncreate) funkci obslužné rutiny (Pokud jste vytvoření podtřídy ovládacího prvku). Nastavení stylů pro ovládací prvek.

## <a name="see-also"></a>Viz také

[Používání atributu CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

