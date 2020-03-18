---
title: Použití popisů tlačítek v objektu CStatusBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], using in status bars
- status bars [MFC], tool tips
- CStatusBarCtrl class [MFC], tool tips
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
ms.openlocfilehash: a607a5fb8c9470df42d12c771865b924891b2dac
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442539"
---
# <a name="using-tooltips-in-a-cstatusbarctrl-object"></a>Použití popisů tlačítek v objektu CStatusBarCtrl

Chcete-li povolit popisy tlačítek pro ovládací prvek stavového řádku, vytvořte objekt `CStatusBarCtrl` se stylem SBT_TOOLTIPS.

> [!NOTE]
>  Pokud k implementaci stavového řádku používáte objekt `CStatusBar`, použijte funkci `CStatusBar::CreateEx`. Umožňuje zadat další styly pro vložený objekt `CStatusBarCtrl`.

Po úspěšném vytvoření objektu `CStatusBarCtrl` použijte [CStatusBarCtrl:: SetTipText](../mfc/reference/cstatusbarctrl-class.md#settiptext) a [CStatusBarCtrl:: GetTipText](../mfc/reference/cstatusbarctrl-class.md#gettiptext) pro nastavení a načtení textu tipu pro konkrétní podokno.

Po nastavení popisu tlačítka se zobrazí pouze v případě, že má část ikonu a žádný text, nebo pokud se celý text v části nedá zobrazit. Tipy nástrojů nejsou v jednoduchém režimu podporovány.

## <a name="see-also"></a>Viz také

[Používání atributu CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
