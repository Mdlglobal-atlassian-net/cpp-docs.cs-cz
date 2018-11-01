---
title: Nastavení klávesové zkratky
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
ms.openlocfilehash: a5dc885767137a4e53d1ea0d066944d5f276c38c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508794"
---
# <a name="setting-a-hot-key"></a>Nastavení klávesové zkratky

Aplikace můžete použít klávesovou zkratku na základě informací poskytnutých ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) ovládacího prvku v jednom ze dvou způsobů:

- Nastavení globální klávesové zkratky pro aktivaci okno nonchild odesláním [WM_SETHOTKEY](/windows/desktop/inputdev/wm-sethotkey) zprávu do okna aktivaci.

- Nastavení klávesové zkratky specifické pro vlákno voláním funkce Windows [RegisterHotKey](https://msdn.microsoft.com/library/windows/desktop/ms646309).

## <a name="see-also"></a>Viz také

[Používání atributu CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

