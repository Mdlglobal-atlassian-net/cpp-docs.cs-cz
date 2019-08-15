---
title: Nastavení klávesové zkratky
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
ms.openlocfilehash: 7b49f24039b130f74693e7567f5287476126f225
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511216"
---
# <a name="setting-a-hot-key"></a>Nastavení klávesové zkratky

Vaše aplikace může používat informace poskytované ovládacím prvkem Hot Key ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) jedním ze dvou způsobů:

- Nastavte globální klávesovou zkratku pro aktivaci nepodřízeného okna odesláním zprávy [WM_SETHOTKEY](/windows/win32/inputdev/wm-sethotkey) do okna, které se má aktivovat.

- Nastavte klávesovou zkratku specifickou pro vlákno voláním funkce Windows [RegisterHotKey](/windows/win32/api/winuser/nf-winuser-registerhotkey).

## <a name="see-also"></a>Viz také:

[Používání atributu CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
