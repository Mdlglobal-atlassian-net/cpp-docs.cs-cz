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
ms.openlocfilehash: 97db98322cd7c0d14e46f54a055bbc646c90d785
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57268990"
---
# <a name="handling-ttnneedtext-notification-for-tool-tips"></a>Zpracování oznámení TTN_NEEDTEXT u popisů tlačítek

Jako součást [povolení popisů tlačítek](../mfc/enabling-tool-tips.md), zpracování **TTN_NEEDTEXT** zprávu tak, že přidáte následující položku do mapy zprávu nadřazenému oknu:

[!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_1.cpp)]

*memberFxn*<br/>
Členská funkce se volá, když pro toto tlačítko je nutné zadat text.

Všimněte si, že ID popisku tlačítka je vždy 0.

Deklarace funkce obslužné rutiny v definici třídy následujícím způsobem:

[!code-cpp[NVC_MFCControlLadenDialog#53](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_2.h)]

kde jsou kurzívou parametry:

*id*<br/>
Identifikátor ovládacího prvku, který poslat oznámení. Nepoužívá se. Id ovládacího prvku je převzata z **NMHDR** struktury.

*pNMHDR*<br/>
Ukazatel [NMTTDISPINFO](/windows/desktop/api/commctrl/ns-commctrl-tagnmttdispinfoa) struktury. Tato struktura je také popsáno dále v [ToolTipText – struktura](../mfc/tooltiptext-structure.md).

*pResult*<br/>
Ukazatel na kód výsledku můžete nastavit před vrácením. **TTN_NEEDTEXT** můžete ignorovat obslužné rutiny *pResult* parametru.

Jako příklad obslužnou rutinu oznámení formulářové zobrazení:

[!code-cpp[NVC_MFCControlLadenDialog#54](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_3.cpp)]

Volání `EnableToolTips` (Tento fragment z `OnInitDialog`):

[!code-cpp[NVC_MFCControlLadenDialog#55](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_4.cpp)]

## <a name="see-also"></a>Viz také:

[Popisy tlačítek v oknech neodvozených ze třídy CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)
