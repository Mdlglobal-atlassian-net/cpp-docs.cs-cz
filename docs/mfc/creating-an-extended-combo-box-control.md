---
title: Vytvoření ovládacího prvku rozšířené pole se seznamem
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes
- CComboBoxEx class [MFC], creating extended combo box controls
- extended combo boxes [MFC], creating
ms.assetid: a964267e-97b6-4e77-9f89-55bb5c68913f
ms.openlocfilehash: 87e2e1cd3c29ba838a17c24ece4a89adda21db0c
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907723"
---
# <a name="creating-an-extended-combo-box-control"></a>Vytvoření ovládacího prvku rozšířené pole se seznamem

Způsob vytvoření rozšířeného ovládacího prvku pole se seznamem závisí na tom, zda ovládací prvek používáte v dialogovém okně nebo když ho vytvoříte v nedialogovém okně.

### <a name="to-use-ccomboboxex-directly-in-a-dialog-box"></a>Použití atributu CComboBoxEx přímo v dialogovém okně

1. V editoru dialogového okna přidejte ovládací prvek rozšířený pole se seznamem do prostředku šablony dialogového okna. Zadejte ID ovládacího prvku.

1. Určete všechny požadované styly pomocí dialogového okna vlastnosti ovládacího prvku rozšířené pole se seznamem.

1. Pomocí [Průvodce přidáním členské proměnné](../ide/adding-a-member-variable-visual-cpp.md) přidejte členskou proměnnou typu [atributu CComboBoxEx](../mfc/reference/ccomboboxex-class.md) s vlastností Control. Tento člen můžete použít k volání `CComboBoxEx` členských funkcí.

1. Použijte [Průvodce třídami](reference/mfc-class-wizard.md) k mapování funkcí obslužných rutin ve třídě dialogového okna pro jakékoli rozšířené zprávy s ovládacími prvky pole se seznamem, které je třeba zpracovat (viz [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md)).

1. V [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)nastavte další styly pro `CComboBoxEx` objekt.

### <a name="to-use-ccomboboxex-in-a-nondialog-window"></a>Použití atributu CComboBoxEx v nedialogovém okně

1. Definujte ovládací prvek ve třídě zobrazení nebo okna.

1. Zavolejte funkci pro [Vytvoření](../mfc/reference/ctabctrl-class.md#create) členské funkce ovládacího prvku, případně v [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), možná jako počáteční funkci obslužné rutiny pro [Vytvoření](../mfc/reference/cwnd-class.md#oncreate) nadřazeného okna. Nastavte styly ovládacího prvku.

## <a name="see-also"></a>Viz také:

[Používání atributu CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
