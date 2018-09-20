---
title: Použití třídy CStatusBarCtrl k vytvoření objektu CStatusBarCtrl | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CStatusBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- status bar controls [MFC], creating
- CStatusBarCtrl class [MFC], creating
ms.assetid: 365c2b65-12de-49e6-9a2e-416c6ee10d60
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3c68603eff0393d76af4e0617548e5bf1dd4aa63
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413682"
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

