---
title: Klávesové zkratky specifické pro vlákno
ms.date: 11/04/2016
helpviewer_keywords:
- CHotKeyCtrl class [MFC], thread-specific hot keys
- keyboard shortcuts [MFC], hot keys
- threading [MFC], hot keys in CHotKeyCtrl
- access keys [MFC], hot keys
ms.assetid: b6021274-1498-483f-bcbf-ba5723547cc8
ms.openlocfilehash: 4b393fe1af060a4b235162ce8cdfd94a1a391085
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594152"
---
# <a name="thread-specific-hot-keys"></a>Klávesové zkratky specifické pro vlákno

Aplikace nastaví klávesové zkratky specifické pro vlákno ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) s použitím Windows `RegisterHotKey` funkce. Když uživatel stiskne klávesovou zkratku specifické pro vlákno, odešle Windows [WM_HOTKEY](/windows/desktop/inputdev/wm-hotkey) zprávy na začátek fronty zpráv konkrétní vlákno. Zpráva WM_HOTKEY obsahuje virtuální kód, shift stavu a uživatelského ID konkrétní klávesovou zkratku, která byla stisknuta. Seznam kódů standardní virtuální klíče najdete v tématu winuser. Další informace o této metodě naleznete v tématu [RegisterHotKey](https://msdn.microsoft.com/library/windows/desktop/ms646309).

Všimněte si, že shift stavové značky použité ve volání `RegisterHotKey` nejsou stejné jako vrácené [GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey) členské funkce; bude nutné převést tyto příznaky před voláním `RegisterHotKey`.

## <a name="see-also"></a>Viz také

[Používání atributu CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

