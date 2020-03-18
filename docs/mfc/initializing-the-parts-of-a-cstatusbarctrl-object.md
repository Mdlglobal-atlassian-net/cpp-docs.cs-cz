---
title: Inicializace částí objektu CStatusBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- CStatusBarCtrl class [MFC], simple mode
- status bars [MFC], declaring parts of
- simple status bars [MFC]
- status bars [MFC], icons
- status bars [MFC], simple mode
- icons, using in status bars
- CStatusBarCtrl class [MFC], declaring parts of
ms.assetid: 60e8f285-d2d8-424a-a6ea-2fc548370303
ms.openlocfilehash: a5b65a2bbb68eaa7058f3514bb95a5209a0e5e71
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444447"
---
# <a name="initializing-the-parts-of-a-cstatusbarctrl-object"></a>Inicializace částí objektu CStatusBarCtrl

Ve výchozím nastavení zobrazuje stavový řádek informace o stavu pomocí samostatných podoken. Tato podokna (také označovaná jako součásti) mohou obsahovat textový řetězec, ikonu nebo obojí.

Pomocí [SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts) můžete definovat, kolik částí a délku bude mít stavový řádek. Po vytvoření částí stavového řádku proveďte volání [SetText](../mfc/reference/cstatusbarctrl-class.md#settext) a [SetIcon](../mfc/reference/cstatusbarctrl-class.md#seticon) a nastavte text nebo ikonu pro určitou část stavového řádku. Po úspěšném nastavení této části se ovládací prvek automaticky překreslí.

Následující příklad inicializuje existující objekt `CStatusBarCtrl` (`m_StatusBarCtrl`) se čtyřmi podokny a poté nastaví ikonu (IDI_ICON1) a nějaký text v druhé části.

[!code-cpp[NVC_MFCControlLadenDialog#31](../mfc/codesnippet/cpp/initializing-the-parts-of-a-cstatusbarctrl-object_1.cpp)]

Další informace o nastavení režimu `CStatusBarCtrl` objektu na jednoduché, najdete v tématu [Nastavení režimu objektu CStatusBarCtrl](../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md).

## <a name="see-also"></a>Viz také

[Používání atributu CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
