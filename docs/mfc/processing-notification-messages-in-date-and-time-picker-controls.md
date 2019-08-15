---
title: Zpracování oznamovacích zpráv v ovládacích prvcích pro výběr data a času
ms.date: 11/04/2016
f1_keywords:
- DTN_CLOSEUP
- DTN_DATETIMECHANGE
- DTN_DROPDOWN
helpviewer_keywords:
- DTN_DROPDOWN notification [MFC]
- DTN_DATETIMECHANGE notification [MFC]
- DTN_CLOSEUP notification [MFC]
- DateTimePicker control [MFC], handling notifications
- CDateTimeCtrl class [MFC], handling notifications
- DTN_FORMAT notification [MFC]
- DateTimePicker control [MFC]
ms.assetid: ffbe29ab-ff80-4609-89f7-260b404439c4
ms.openlocfilehash: fead5643299aee4beace55abde0b6a6c801a324f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507881"
---
# <a name="processing-notification-messages-in-date-and-time-picker-controls"></a>Zpracování oznamovacích zpráv v ovládacích prvcích pro výběr data a času

Když uživatelé komunikují s ovládacím prvkem pro výběr data a času, ovládací`CDateTimeCtrl`prvek () posílá oznamovací zprávy do svého nadřazeného okna, obvykle do zobrazení nebo z objektu dialogového okna. Pokud chcete něco udělat v reakci, Zpracujte tyto zprávy. Například když uživatel otevře ovládací prvek pro výběr data a času pro zobrazení vloženého ovládacího prvku měsíční kalendář, pošle se oznámení DTN_DROPDOWN.

Pomocí okno Vlastnosti přidejte do nadřazené třídy obslužné rutiny oznámení pro ty zprávy, které chcete implementovat.

Následující seznam popisuje různá oznámení odesílaná ovládacím prvkem pro výběr data a času.

- DTN_DROPDOWN upozorní nadřazeného objektu na zobrazení vloženého ovládacího prvku měsíční kalendář. Toto oznámení se posílá pouze v případě, že není nastaven styl DTS_UPDOWN. Další informace o tomto oznámení najdete v tématu [přístup k vloženému ovládacímu prvku měsíční kalendář](../mfc/accessing-the-embedded-month-calendar-control.md).

- DTN_CLOSEUP upozorní nadřazenou položku, že se chystá zavřít vložený ovládací prvek měsíčního kalendáře. Toto oznámení se posílá pouze v případě, že není nastaven styl DTS_UPDOWN.

- DTN_DATETIMECHANGE upozorní nadřazenou položku, že v ovládacím prvku došlo ke změně.

- DTN_FORMAT oznámí nadřazenému objektu, že text je potřeba zobrazit v poli zpětného volání. Další informace o tomto poli oznámení a zpětná volání naleznete v tématu [použití polí zpětného volání v ovládacím prvku pro výběr data a času](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md).

- DTN_FORMATQUERY vyžádá nadřazenou položku, aby poskytovala maximální povolenou velikost řetězce, který se zobrazí v poli zpětného volání. Manipulace s tímto oznámením umožňuje ovládacímu prvku správně zobrazit výstup a snížit tak blikání v zobrazení ovládacího prvku. Další informace o tomto oznámení najdete v tématu [použití polí zpětného volání v ovládacím prvku pro výběr data a času](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md).

- DTN_USERSTRING upozorní nadřazenou položku, že uživatel dokončil úpravu obsahu ovládacího prvku pro výběr data a času. Toto oznámení se posílá pouze v případě, že je nastaven styl DTS_APPCANPARSE.

- DTN_WMKEYDOWN upozorní nadřazenou položku, pokud uživatel zadá pole v poli zpětného volání. Zpracujte toto oznámení, aby emuluje stejnou odezvu klávesnice podporovanou pro pole bez zpětného volání v ovládacím prvku pro výběr data a času. Další informace o tomto oznámení naleznete v tématu [Podpora polí zpětného volání v ovládacím prvku DTP](/windows/win32/Controls/date-and-time-picker-controls) v Windows SDK.

## <a name="see-also"></a>Viz také:

[Používání atributu CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
