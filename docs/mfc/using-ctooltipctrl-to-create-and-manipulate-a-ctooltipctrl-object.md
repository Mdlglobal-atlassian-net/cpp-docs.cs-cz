---
title: Použití objektu CToolTipCtrl k vytvoření objektu CToolTipCtrl a manipulaci s ním
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], creating
- CToolTipCtrl class [MFC], using
ms.assetid: 0a34583f-f66d-46a1-a239-31b80ea395ad
ms.openlocfilehash: 37dc7bc5a411ebab3737b87fd6977b26cff68178
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442215"
---
# <a name="using-ctooltipctrl-to-create-and-manipulate-a-ctooltipctrl-object"></a>Použití objektu CToolTipCtrl k vytvoření objektu CToolTipCtrl a manipulaci s ním

Tady je příklad použití [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md) :

### <a name="to-create-and-manipulate-a-ctooltipctrl"></a>Vytvoření a manipulace s CToolTipCtrl

1. Sestavte objekt `CToolTipCtrl`.

1. Vyvoláním metody [Create](../mfc/reference/ctooltipctrl-class.md#create) Vytvořte běžný ovládací prvek popisů Windows a připojte ho k objektu `CToolTipCtrl`.

1. Zavolejte [AddTool](../mfc/reference/ctooltipctrl-class.md#addtool) k registraci nástroje pomocí ovládacího prvku popis tlačítka, aby se informace uložené v popisu tlačítka zobrazily, když je ukazatel myši na nástroji.

1. Zavolejte [SetToolInfo](../mfc/reference/ctooltipctrl-class.md#settoolinfo) a nastavte informace, které Popis nástroje udržuje pro nástroj.

1. Zavolejte [SetToolRect](../mfc/reference/ctooltipctrl-class.md#settoolrect) a nastavte nový ohraničující obdélník pro nástroj.

1. Zavolejte [HitTest](../mfc/reference/ctooltipctrl-class.md#hittest) k otestování bodu, abyste zjistili, zda se nachází uvnitř ohraničujícího obdélníku daného nástroje, a pokud ano, načtěte informace o nástroji.

1. Zavolejte [GetToolCount](../mfc/reference/ctooltipctrl-class.md#gettoolcount) a načtěte počet nástrojů zaregistrovaných pomocí ovládacího prvku Tip nástroje.

## <a name="see-also"></a>Viz také

[Používání atributu CToolTipCtrl](../mfc/using-ctooltipctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
