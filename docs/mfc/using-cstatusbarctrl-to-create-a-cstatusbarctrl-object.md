---
title: Použití třídy CStatusBarCtrl k vytvoření objektu CStatusBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- status bar controls [MFC], creating
- CStatusBarCtrl class [MFC], creating
ms.assetid: 365c2b65-12de-49e6-9a2e-416c6ee10d60
ms.openlocfilehash: 12d5664b9fc59c4569ec2ee7db4ae883911f7bcd
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442379"
---
# <a name="using-cstatusbarctrl-to-create-a-cstatusbarctrl-object"></a>Použití třídy CStatusBarCtrl k vytvoření objektu CStatusBarCtrl

Tady je příklad typického použití [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md):

### <a name="to-use-a-status-bar-control-with-parts"></a>Použití ovládacího prvku stavového řádku s částmi

1. Sestavte objekt `CStatusBarCtrl`.

1. Zavolejte [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight) , pokud chcete nastavit minimální výšku oblasti kreslení ovládacího prvku stavového řádku.

1. Zavolejte [SetBkColor](../mfc/reference/cstatusbarctrl-class.md#setbkcolor) k nastavení barvy pozadí ovládacího prvku stavového řádku.

1. Zavolejte [SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts) k nastavení počtu částí v ovládacím prvku stavového řádku a souřadnice pravého okraje každé části.

1. Zavolejte [SetText](../mfc/reference/cstatusbarctrl-class.md#settext) a nastavte text v dané části ovládacího prvku stavového řádku. Zpráva zruší platnost části ovládacího prvku, který se změnil, což způsobí, že se zobrazí nový text, když ovládací prvek příště obdrží zprávu WM_PAINT.

V některých případech stavový řádek potřebuje jenom zobrazit řádek textu. V takovém případě zavolejte na [SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple). Tím se ovládací prvek stavového řádku vloží do režimu "jednoduchý", který zobrazí jeden řádek textu.

## <a name="see-also"></a>Viz také

[Používání atributu CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
