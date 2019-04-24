---
title: Nastavení klávesové zkratky
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
ms.openlocfilehash: a77aad4881acd04c6dabb6dce90acc01be2cfbc8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307780"
---
# <a name="setting-a-hot-key"></a>Nastavení klávesové zkratky

Aplikace můžete použít klávesovou zkratku na základě informací poskytnutých ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) ovládacího prvku v jednom ze dvou způsobů:

- Nastavení globální klávesové zkratky pro aktivaci okno nonchild odesláním [WM_SETHOTKEY](/windows/desktop/inputdev/wm-sethotkey) zprávu do okna aktivaci.

- Nastavení klávesové zkratky specifické pro vlákno voláním funkce Windows [RegisterHotKey](/windows/desktop/api/winuser/nf-winuser-registerhotkey).

## <a name="see-also"></a>Viz také:

[Používání atributu CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
