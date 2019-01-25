---
title: Klávesové zkratky specifické pro vlákno
ms.date: 11/04/2016
helpviewer_keywords:
- CHotKeyCtrl class [MFC], thread-specific hot keys
- keyboard shortcuts [MFC], hot keys
- threading [MFC], hot keys in CHotKeyCtrl
- access keys [MFC], hot keys
ms.assetid: b6021274-1498-483f-bcbf-ba5723547cc8
ms.openlocfilehash: 68c50ec5f29dab271f9af9abc50eb72ec15157e7
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893324"
---
# <a name="thread-specific-hot-keys"></a>Klávesové zkratky specifické pro vlákno

Aplikace nastaví klávesové zkratky specifické pro vlákno ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) s použitím Windows `RegisterHotKey` funkce. Když uživatel stiskne klávesovou zkratku specifické pro vlákno, odešle Windows [WM_HOTKEY](/windows/desktop/inputdev/wm-hotkey) zprávy na začátek fronty zpráv konkrétní vlákno. Zpráva WM_HOTKEY obsahuje virtuální kód, shift stavu a uživatelského ID konkrétní klávesovou zkratku, která byla stisknuta. Seznam kódů standardní virtuální klíče najdete v tématu winuser. Další informace o této metodě naleznete v tématu [RegisterHotKey](/windows/desktop/api/winuser/nf-winuser-registerhotkey).

Všimněte si, že shift stavové značky použité ve volání `RegisterHotKey` nejsou stejné jako vrácené [GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey) členské funkce; bude nutné převést tyto příznaky před voláním `RegisterHotKey`.

## <a name="see-also"></a>Viz také

[Používání atributu CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

