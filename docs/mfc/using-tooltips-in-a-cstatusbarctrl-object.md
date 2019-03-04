---
title: Použití popisů tlačítek v objektu CStatusBarCtrl
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
helpviewer_keywords:
- tool tips [MFC], using in status bars
- status bars [MFC], tool tips
- CStatusBarCtrl class [MFC], tool tips
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
ms.openlocfilehash: 3f9a1fec7eb951fa76c542e09df751b4c58ddb16
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265081"
---
# <a name="using-tooltips-in-a-cstatusbarctrl-object"></a>Použití popisů tlačítek v objektu CStatusBarCtrl

Pokud chcete povolit tooltips pro ovládací prvek panel stav, vytvořte `CStatusBarCtrl` objekt stylem SBT_TOOLTIPS.

> [!NOTE]
>  Pokud používáte `CStatusBar` objekt implementace stavového řádku, použijte `CStatusBar::CreateEx` funkce. Umožňuje vám určit další styly pro vložený `CStatusBarCtrl` objektu.

Jednou `CStatusBarCtrl` objekt byl úspěšně vytvořen, použijte [CStatusBarCtrl::SetTipText](../mfc/reference/cstatusbarctrl-class.md#settiptext) a [CStatusBarCtrl::GetTipText](../mfc/reference/cstatusbarctrl-class.md#gettiptext) k nastavení a načtení text tipu pro konkrétní podokno.

Po nastavení Popis tlačítka, se zobrazí jenom v případě, že část obsahuje ikonu a žádný text nebo pokud veškerý text nelze zobrazit v této části. Popisy tlačítek v stručném režimu nepodporují.

## <a name="see-also"></a>Viz také:

[Používání atributu CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
