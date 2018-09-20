---
title: Použití popisů tlačítek v objektu CStatusBarCtrl | Dokumentace Microsoftu
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
- tool tips [MFC], using in status bars
- status bars [MFC], tool tips
- CStatusBarCtrl class [MFC], tool tips
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f17dff6680209664e9d029404e4ef012b9f12046
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392356"
---
# <a name="using-tooltips-in-a-cstatusbarctrl-object"></a>Použití popisů tlačítek v objektu CStatusBarCtrl

Pokud chcete povolit tooltips pro ovládací prvek panel stav, vytvořte `CStatusBarCtrl` objekt stylem SBT_TOOLTIPS.

> [!NOTE]
>  Pokud používáte `CStatusBar` objekt implementace stavového řádku, použijte `CStatusBar::CreateEx` funkce. Umožňuje vám určit další styly pro vložený `CStatusBarCtrl` objektu.

Jednou `CStatusBarCtrl` objekt byl úspěšně vytvořen, použijte [CStatusBarCtrl::SetTipText](../mfc/reference/cstatusbarctrl-class.md#settiptext) a [CStatusBarCtrl::GetTipText](../mfc/reference/cstatusbarctrl-class.md#gettiptext) k nastavení a načtení text tipu pro konkrétní podokno.

Po nastavení Popis tlačítka, se zobrazí jenom v případě, že část obsahuje ikonu a žádný text nebo pokud veškerý text nelze zobrazit v této části. Popisy tlačítek v stručném režimu nepodporují.

## <a name="see-also"></a>Viz také

[Používání atributu CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

