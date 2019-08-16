---
title: Klávesové zkratky specifické pro vlákno
ms.date: 11/04/2016
helpviewer_keywords:
- CHotKeyCtrl class [MFC], thread-specific hot keys
- keyboard shortcuts [MFC], hot keys
- threading [MFC], hot keys in CHotKeyCtrl
- access keys [MFC], hot keys
ms.assetid: b6021274-1498-483f-bcbf-ba5723547cc8
ms.openlocfilehash: 49bac6ac357924c26f131bbd8e1092cd74514167
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511135"
---
# <a name="thread-specific-hot-keys"></a>Klávesové zkratky specifické pro vlákno

Aplikace nastaví klávesovou zkratku ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) specifickou pro vlákno pomocí funkce Windows `RegisterHotKey` . Když uživatel stiskne klávesovou zkratku specifickou pro vlákno, Windows pošle zprávu [WM_HOTKEY](/windows/win32/inputdev/wm-hotkey) na začátek konkrétní fronty zpráv vlákna. Zpráva WM_HOTKEY obsahuje kód virtuálního klíče, stav posunu a uživatelem definované ID konkrétní klávesové zkratky, která byla stisknuta. Seznam standardních kódů virtuálních klíčů naleznete v tématu Winuser. h. Další informace o této metodě naleznete v tématu [RegisterHotKey](/windows/win32/api/winuser/nf-winuser-registerhotkey).

Všimněte si, že příznaky stavu posunu používané při volání `RegisterHotKey` nejsou stejné jako hodnoty vrácené členskou funkcí getctrl+SHIFT+F3 [](../mfc/reference/chotkeyctrl-class.md#gethotkey) ; před voláním `RegisterHotKey`je nutné tyto příznaky přeložit.

## <a name="see-also"></a>Viz také:

[Používání atributu CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
