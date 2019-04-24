---
title: Inicializace částí objektu CStatusBarCtrl
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
helpviewer_keywords:
- CStatusBarCtrl class [MFC], simple mode
- status bars [MFC], declaring parts of
- simple status bars [MFC]
- status bars [MFC], icons
- status bars [MFC], simple mode
- icons, using in status bars
- CStatusBarCtrl class [MFC], declaring parts of
ms.assetid: 60e8f285-d2d8-424a-a6ea-2fc548370303
ms.openlocfilehash: 0f00aee03a74799bf14563653b50c487ff001d02
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182316"
---
# <a name="initializing-the-parts-of-a-cstatusbarctrl-object"></a>Inicializace částí objektu CStatusBarCtrl

Ve výchozím nastavení ve stavovém řádku zobrazí informace o stavu pomocí samostatných podoken. Těchto podoken můžete vizualizaci (také označované jako částí) může obsahovat textový řetězec, ikona nebo obojí.

Použití [SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts) určit, kolik částí a délku, bude mít stavový řádek. Po vytvoření části stavový řádek provádět volání do [SetText –](../mfc/reference/cstatusbarctrl-class.md#settext) a [SetIcon](../mfc/reference/cstatusbarctrl-class.md#seticon) nastavit text nebo ikonu pro určitou část ve stavovém řádku. Po úspěšném nastavení části je automaticky překreslení ovládacího prvku.

Následující příklad inicializuje existující `CStatusBarCtrl` objektu (`m_StatusBarCtrl`) pomocí čtyř podoken a v druhé části nastaví ikonu (IDI_ICON1) a nějakým textem.

[!code-cpp[NVC_MFCControlLadenDialog#31](../mfc/codesnippet/cpp/initializing-the-parts-of-a-cstatusbarctrl-object_1.cpp)]

Další informace o nastavení režimu `CStatusBarCtrl` objektu na jednoduchý, viz [nastavení režimu objektu CStatusBarCtrl](../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md).

## <a name="see-also"></a>Viz také:

[Používání atributu CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
