---
title: Zpracování oznámení TTN_NEEDTEXT u popisů tlačítek
ms.date: 11/04/2016
f1_keywords:
- TTN_NEEDTEXT
helpviewer_keywords:
- TTN_NEEDTEXT message [MFC]
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: d0370a65-21ba-4676-bcc5-8cf851bbb15c
ms.openlocfilehash: a63154f3da539676f31709899568b6486dc6017e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508521"
---
# <a name="handling-ttn_needtext-notification-for-tool-tips"></a>Zpracování oznámení TTN_NEEDTEXT u popisů tlačítek

V rámci [povolování tipů](../mfc/enabling-tool-tips.md)k nástrojům zpracováváte zprávu **TTN_NEEDTEXT** přidáním následujícího záznamu do mapy zpráv vašeho okna vlastníka:

[!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_1.cpp)]

*memberFxn*<br/>
Členská funkce, která má být volána, je-li pro toto tlačítko vyžadován text

Všimněte si, že ID tipu nástroje je vždy 0.

Deklarujte svou funkci obslužné rutiny v definici třídy následujícím způsobem:

[!code-cpp[NVC_MFCControlLadenDialog#53](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_2.h)]

kde jsou tyto parametry kurzívou:

*id*<br/>
Identifikátor ovládacího prvku, který odeslal oznámení Nepoužívá se. ID ovládacího prvku se převezme ze struktury **NMHDR** .

*pNMHDR*<br/>
Ukazatel na strukturu [NMTTDISPINFO](/windows/win32/api/commctrl/ns-commctrl-nmttdispinfow) . Tato struktura je také popsána dále ve [struktuře ToolTipText](../mfc/tooltiptext-structure.md).

*pResult*<br/>
Ukazatel na kód výsledku, který můžete nastavit před vrácením. Obslužné rutiny **TTN_NEEDTEXT** mohou ignorovat parametr *pResult* .

Jako příklad obslužné rutiny oznámení typu formulář-zobrazení:

[!code-cpp[NVC_MFCControlLadenDialog#54](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_3.cpp)]

Zavolat `EnableToolTips` (Tento fragment povedený z `OnInitDialog`):

[!code-cpp[NVC_MFCControlLadenDialog#55](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_4.cpp)]

## <a name="see-also"></a>Viz také:

[Popisy tlačítek v oknech neodvozených ze třídy CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)
