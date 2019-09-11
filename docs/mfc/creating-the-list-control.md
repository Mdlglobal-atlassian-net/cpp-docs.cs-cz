---
title: Vytvoření ovládacího prvku seznam
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating control
- list controls [MFC]
ms.assetid: a4cb1729-31b6-4d2b-a44b-367474848a39
ms.openlocfilehash: f1c5d8db93421e1d3ae0e39aec82bdf0f5529f1f
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907928"
---
# <a name="creating-the-list-control"></a>Vytvoření ovládacího prvku seznam

Způsob vytvoření ovládacího prvku seznam ([CListCtrl](../mfc/reference/clistctrl-class.md)) závisí na tom, zda ovládací prvek používáte přímo, nebo místo toho použití třídy [CListView –](../mfc/reference/clistview-class.md) . Pokud použijete `CListView`, rozhraní sestaví zobrazení jako součást sekvence vytváření dokumentů/zobrazení. Vytvořením zobrazení seznamu se vytvoří také ovládací prvek seznam (dva jsou stejné). Ovládací prvek je vytvořen ve funkci obslužné rutiny [Create](../mfc/reference/cwnd-class.md#oncreate) pro zobrazení. V tomto případě je ovládací prvek připraven k přidávání položek prostřednictvím volání [GetListCtrl](../mfc/reference/clistview-class.md#getlistctrl).

### <a name="to-use-clistctrl-directly-in-a-dialog-box"></a>Použití CListCtrl přímo v dialogovém okně

1. V editoru dialogového okna přidejte ovládací prvek seznam do prostředku šablony dialogového okna. Zadejte ID ovládacího prvku.

1. Pomocí [Průvodce přidáním členské proměnné](../ide/adding-a-member-variable-visual-cpp.md) přidejte členskou proměnnou typu `CListCtrl` s vlastností Control. Tento člen můžete použít k volání `CListCtrl` členských funkcí.

1. Použijte [Průvodce třídami](reference/mfc-class-wizard.md) k mapování funkcí obslužných rutin ve třídě dialogového okna pro všechny zprávy s oznámením ovládacího prvku seznam, které je třeba zpracovat (viz [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md)).

1. V [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)nastavte styly pro `CListCtrl`. Viz [Změna stylů ovládacího prvku seznam](../mfc/changing-list-control-styles.md). Tím se určuje druh zobrazení, které se zobrazí v ovládacím prvku, i když můžete zobrazení později změnit.

### <a name="to-use-clistctrl-in-a-nondialog-window"></a>Použití CListCtrl v nedialogovém okně

1. Definujte ovládací prvek ve třídě zobrazení nebo okna.

1. Zavolejte členskou funkci [Create](../mfc/reference/clistctrl-class.md#create) ovládacího prvku, případně v [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), případně jako funkci obslužné rutiny [Create](../mfc/reference/cwnd-class.md#oncreate) nadřazeného okna (Pokud se jedná o podtřídu ovládacího prvku). Nastavte styly ovládacího prvku.

## <a name="see-also"></a>Viz také:

[Používání atributu CListCtrl](../mfc/using-clistctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
