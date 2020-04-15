---
title: Použití popisů tlačítek v objektu CStatusBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], using in status bars
- status bars [MFC], tool tips
- CStatusBarCtrl class [MFC], tool tips
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
ms.openlocfilehash: 29d326c708743424686d616bbaf172ccd72481ce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374698"
---
# <a name="using-tooltips-in-a-cstatusbarctrl-object"></a>Použití popisů tlačítek v objektu CStatusBarCtrl

Chcete-li povolit popisky ovládacího `CStatusBarCtrl` prvku stavového řádku, vytvořte objekt se stylem SBT_TOOLTIPS.

> [!NOTE]
> Pokud používáte `CStatusBar` objekt k implementaci stavového `CStatusBar::CreateEx` řádku, použijte funkci. Umožňuje zadat další styly pro `CStatusBarCtrl` vložený objekt.

Po `CStatusBarCtrl` úspěšném vytvoření objektu nastavte a načtěte text tipu pro určité podokno pomocí [cstatusbarctrl::SetTipText](../mfc/reference/cstatusbarctrl-class.md#settiptext) a [CStatusBarCtrl::GetTipText.](../mfc/reference/cstatusbarctrl-class.md#gettiptext)

Jakmile je tip nástroje nastaven, zobrazí se pouze v případě, že díl obsahuje ikonu a žádný text nebo pokud nelze zobrazit celý text uvnitř dílu. Tipy nástrojů nejsou podporovány v jednoduchém režimu.

## <a name="see-also"></a>Viz také

[Používání atributu CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
