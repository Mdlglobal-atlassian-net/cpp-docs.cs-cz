---
title: Implementace stavového řádku v prostředí MFC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- COldStatusBar
dev_langs:
- C++
helpviewer_keywords:
- status bars [MFC], implementing in MFC
- CStatusBarCtrl class [MFC], and MFC status bars
- CStatusBar class [MFC], and CStatusBarCtrl class [MFC]
- CStatusBarCtrl class [MFC], and CStatusBar class [MFC]
- status bars [MFC], backward compatibility
- status bars [MFC], old with COldStatusBar class [MFC]
- COldStatusBar class [MFC]
- status bars [MFC], and CStatusBarCtrl class
- CStatusBar class [MFC], and MFC status bars
- status indicators
- status bars [MFC], Windows 95 implementation
ms.assetid: be5cd876-38e3-4d5c-b8cb-16d57a16a142
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e593227daabb2d2c25d593cfb58ef23ba7855be7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436712"
---
# <a name="status-bar-implementation-in-mfc"></a>Implementace stavového řádku v prostředí MFC

A [cstatusbar –](../mfc/reference/cstatusbar-class.md) objekt je ovládací prvek panel s řádkem podoken textového výstupu. Výstupní podokna se obvykle používají jako zprávy řádky a indikátory stavu. Mezi příklady patří řádky zprávu nápovědy nabídky, která stručně popisují příkaz vybrané nabídky a indikátory, které zobrazují stav SCROLL LOCK, NUM LOCK a další klíče.

Od verze knihovny MFC verze 4.0, stavové řádky jsou implementovány pomocí třídy [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md), který zapouzdřuje stavového řádku běžný ovládací prvek. Z důvodu zpětné kompatibility knihovny MFC uchovává starší implementace panelu Stav ve třídě `COldStatusBar`. Dokumentace pro starší verze knihovny MFC popisuje `COldStatusBar` pod `CStatusBar`.

[CStatusBar::GetStatusBarCtrl](../mfc/reference/cstatusbar-class.md#getstatusbarctrl), členské funkce nové knihovny MFC 4.0, vám umožní využít výhod podpory Windows běžné ovládacího prvku pro stavového řádku vlastního nastavení a další funkce. `CStatusBar` Členské funkce vám poskytnou většinu funkcí běžných ovládacích prvků Windows; ale při volání `GetStatusBarCtrl`, které poskytnete stavové řádky i více vlastností stavový řádek. Při volání `GetStatusBarCtrl`, vrátí odkaz na `CStatusBarCtrl` objektu. Tento odkaz můžete použít k manipulaci s ovládací prvek panel stavu.

Následující obrázek znázorňuje stavového řádku, který se zobrazí několik ukazatelů.

![Stavový řádek](../mfc/media/vc37dy1.gif "vc37dy1") A stavový řádek

Jako je panel nástrojů stavového objektu se vloží do jeho nadřazenému oknu rámce a je automaticky vytvořen, když je okno rámce. Stavový řádek, stejně jako všechny ovládací pruhy, je zničen automaticky i při zničení nadřazeného rámce.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Aktualizace textu na panelu stavového řádku stav](../mfc/updating-the-text-of-a-status-bar-pane.md)

- MFC – třídy [cstatusbar –](../mfc/reference/cstatusbar-class.md) a [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)

- [Ovládací pruhy](../mfc/control-bars.md)

- [Dialogové pruhy](../mfc/dialog-bars.md)

- [Panely nástrojů (Toolbar implementace MFC)](../mfc/mfc-toolbar-implementation.md)

## <a name="see-also"></a>Viz také

[Stavové řádky](../mfc/status-bars.md)

