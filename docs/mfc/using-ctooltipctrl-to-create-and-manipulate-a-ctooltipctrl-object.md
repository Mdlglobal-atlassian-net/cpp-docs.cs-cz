---
title: Použití objektu CToolTipCtrl k vytvoření objektu CToolTipCtrl a manipulaci s ním
ms.date: 11/04/2016
f1_keywords:
- CToolTipCtrl
helpviewer_keywords:
- tool tips [MFC], creating
- CToolTipCtrl class [MFC], using
ms.assetid: 0a34583f-f66d-46a1-a239-31b80ea395ad
ms.openlocfilehash: b0f008c70eeb43455408e5b0ad302df6b923608e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261203"
---
# <a name="using-ctooltipctrl-to-create-and-manipulate-a-ctooltipctrl-object"></a>Použití objektu CToolTipCtrl k vytvoření objektu CToolTipCtrl a manipulaci s ním

Tady je příklad [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md) využití:

### <a name="to-create-and-manipulate-a-ctooltipctrl"></a>K vytváření a manipulaci atributu CToolTipCtrl

1. Vytvořit `CToolTipCtrl` objektu.

1. Volání [vytvořit](../mfc/reference/ctooltipctrl-class.md#create) Windows nástroj běžné ovládacím prvkem popis tlačítka vytvořit a připojit ji k `CToolTipCtrl` objektu.

1. Volání [AddTool](../mfc/reference/ctooltipctrl-class.md#addtool) zaregistrovat nástroj s ovládacím prvkem popis tlačítka nástroje tak, aby informace uložené v popisu tlačítka se zobrazí, když ukazatel zůstane na nástroj.

1. Volání [SetToolInfo](../mfc/reference/ctooltipctrl-class.md#settoolinfo) nastavení informace, které udržuje popisku tlačítka pro nástroj.

1. Volání [SetToolRect](../mfc/reference/ctooltipctrl-class.md#settoolrect) nastavit nové ohraničující rámeček pro nástroj.

1. Volání [hitTest –](../mfc/reference/ctooltipctrl-class.md#hittest) otestovat bod k určení, zda je v rámci ohraničující obdélník daný nástroj a pokud ano, načíst informace o tomto nástroji.

1. Volání [GetToolCount](../mfc/reference/ctooltipctrl-class.md#gettoolcount) načíst počet nástrojů pro registrovaný s ovládacím prvkem popis tlačítka nástroj.

## <a name="see-also"></a>Viz také:

[Používání atributu CToolTipCtrl](../mfc/using-ctooltipctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
