---
title: Použití třídy CStatusBarCtrl k vytvoření objektu CStatusBarCtrl
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
helpviewer_keywords:
- status bar controls [MFC], creating
- CStatusBarCtrl class [MFC], creating
ms.assetid: 365c2b65-12de-49e6-9a2e-416c6ee10d60
ms.openlocfilehash: 05baf212f53956095af89377c0877db79b6e25ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552760"
---
# <a name="using-cstatusbarctrl-to-create-a-cstatusbarctrl-object"></a>Použití třídy CStatusBarCtrl k vytvoření objektu CStatusBarCtrl

Tady je příklad typické použití [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md):

### <a name="to-use-a-status-bar-control-with-parts"></a>Použití ovládacích prvků panelu Stav s částí

1. Vytvořit `CStatusBarCtrl` objektu.

1. Volání [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight) Pokud chcete nastavit minimální výšku ovládacího prvku panelu Stav pro kreslení oblasti.

1. Volání [SetBkColor](../mfc/reference/cstatusbarctrl-class.md#setbkcolor) nastavit barvu pozadí ovládacího prvku panelu stavu.

1. Volání [SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts) chcete nastavit počet částí ve stavovém řádku ovládacího prvku a souřadnice pravého okraje každé části.

1. Volání [SetText –](../mfc/reference/cstatusbarctrl-class.md#settext) nastavit text v dané části ovládacího prvku panelu stavu. Zpráva zruší platnost části ovládacího prvku, který se změnil, by ji zobrazíte novým textem, když ovládací prvek dále obdrží zprávu WM_PAINT.

V některých případech se stavový řádek stačí k zobrazení řádku textu. V takovém případě uskutečnit volání [setsimple –](../mfc/reference/cstatusbarctrl-class.md#setsimple). Tento ovládací prvek panelu stavu umístí do režimu "simple", který zobrazuje jeden řádek textu.

## <a name="see-also"></a>Viz také

[Používání atributu CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

