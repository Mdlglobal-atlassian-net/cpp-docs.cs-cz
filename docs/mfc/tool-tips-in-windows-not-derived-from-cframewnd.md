---
title: Popisy tlačítek v oknech neodvozených ze třídy CFrameWnd
ms.date: 11/04/2016
helpviewer_keywords:
- enabling tool tips [MFC]
- TOOLTIPTEXT structure [MFC]
- Help [MFC], tool tips for controls
- TTN_NEEDTEXT message [MFC]
- controls [MFC], tool tips
- handler functions [MFC], tool tips
ms.assetid: cad5ef0f-02e3-4151-ad0d-3d42e6932b0e
ms.openlocfilehash: 1f68fb62335219ea498163e6124c8e91e49f2938
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511034"
---
# <a name="tool-tips-in-windows-not-derived-from-cframewnd"></a>Popisy tlačítek v oknech neodvozených ze třídy CFrameWnd

Tato rodina článků popisuje povolení tipů nástrojů pro ovládací prvky obsažené v okně, které není odvozeno od [CFrameWnd](../mfc/reference/cframewnd-class.md). Tipy nástrojů pro [panely nástrojů](../mfc/toolbar-tool-tips.md) najdete informace o tipech nástrojů pro ovládací prvky v `CFrameWnd`.

Témata, která jsou popsaná v tomto článku, zahrnují:

- [Povolení popisů tlačítek](../mfc/enabling-tool-tips.md)

- [Zpracování oznámení TTN_NEEDTEXT u popisů tlačítek](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)

- [Struktura TOOLTIPTEXT](../mfc/tooltiptext-structure.md)

Popisy tlačítek jsou automaticky zobrazeny pro tlačítka a další ovládací prvky obsažené v nadřazeném okně odvozeném z `CFrameWnd`. Důvodem je `CFrameWnd` , že má výchozí obslužnou rutinu pro oznámení [TTN_GETDISPINFO](/windows/win32/Controls/ttn-getdispinfo) , která zpracovává oznámení **TTN_NEEDTEXT** z ovládacích prvků popisů tlačítek přidružených k ovládacím prvkům.

Nicméně tato výchozí obslužná rutina není volána, když je oznámení **TTN_NEEDTEXT** odesláno z ovládacího prvku popis tlačítka přidruženého k ovládacímu prvku v okně, který `CFrameWnd`není, jako je například ovládací prvek v dialogovém okně nebo ve formulářovém zobrazení. Proto je nutné zadat funkci obslužné rutiny pro zprávu oznámení **TTN_NEEDTEXT** , aby zobrazovala popisy tlačítek pro podřízené ovládací prvky.

Výchozí tipy k nástrojům, které jsou k dispozici pro Windows podle [CWnd:: EnableToolTips](../mfc/reference/cwnd-class.md#enabletooltips) , nemají přidružený text. Chcete-li načíst text pro popis tlačítka, který se má zobrazit, pošle se oznámení **TTN_NEEDTEXT** do nadřazeného okna ovládacího prvku Tip nástroje těsně před zobrazením okna s popisem tlačítka. Není-li pro tuto zprávu k dispozici žádná obslužná rutina pro přiřazení nějaké hodnoty *pszText* členu struktury **ToolTipText** , nezobrazí se žádný text pro popis tlačítka.

## <a name="see-also"></a>Viz také:

[Popisy tlačítek](../mfc/tool-tips.md)
