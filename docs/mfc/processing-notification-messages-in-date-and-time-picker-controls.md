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
ms.openlocfilehash: ce84863744629d30248f94b94448d776177f9841
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57292884"
---
# <a name="processing-notification-messages-in-date-and-time-picker-controls"></a>Zpracování oznamovacích zpráv v ovládacích prvcích pro výběr data a času

Jak uživatelé komunikovat s datem a ovládací prvek pro výběr času, ovládací prvek (`CDateTimeCtrl`) odesílá zprávy s oznámením nezašle nadřazenému oknu, obvykle objekt zobrazení nebo dialogového okna. Tyto zprávy zpracovávají, pokud budete chtít udělat něco v odpovědi. Například když uživatel otevře výběr data a času, chcete-li zobrazit ovládací prvek vložený měsíční kalendář, dtn_dropdown – oznámení se posílá.

Použijte okno Vlastnosti pro přidání obslužné rutiny oznamovacích do nadřazené třídu pro ty zprávy, které chcete implementovat.

Následující seznam popisuje různé oznámení zaslaná z prvku Výběr data a času.

- Dtn_dropdown – upozorní nadřazený objekt, který ovládací prvek vložený měsíc kalendář se má zobrazit. Toto oznámení se odesílají jenom při styl DTS_UPDOWN nebyla nastavena. Další informace o tomto oznámení najdete v tématu [přístup k vloženému ovládacímu prvku kalendářní měsíc](../mfc/accessing-the-embedded-month-calendar-control.md).

- Dtn_closeup – upozorní nadřazený objekt, který ovládací prvek vložený měsíc kalendář je bude uzavřen. Toto oznámení se odesílají jenom při styl DTS_UPDOWN nebyla nastavena.

- Dtn_datetimechange – upozorňují nadřazeného objektu, který má došlo ke změně v ovládacím prvku.

- Dtn_format – upozorní nadřazené položky, která je text potřeby zobrazit v poli zpětného volání. Další informace o tomto oznámení a polí zpětného volání, naleznete v tématu [použití polí zpětného volání v datu a ovládacího prvku pro výběr času](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md).

- Dtn_formatquery – požadavky nadřazené zadat maximální povolenou velikost řetězce, který se zobrazí v poli zpětného volání. Zpracování tohoto oznámení umožňuje ovládacímu prvku správně zobrazení výstupu vůbec časy omezení blikání v rámci ovládacího prvku zobrazení. Další informace o tomto oznámení najdete v tématu [použití polí zpětného volání v datu a ovládacího prvku pro výběr času](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md).

- Upozorňují DTN_USERSTRING nadřazené, že uživatel dokončil úpravy obsahu prvku Výběr data a času. Toto oznámení je odeslán, pouze pokud byl nastaven styl DTS_APPCANPARSE.

- DTN_WMKEYDOWN upozorní nadřazený, když uživatel zadá v poli zpětného volání. Zpracuje toto oznámení k emulaci stejnou odpověď klávesnice podporována pro pole bez zpětného volání v ovládacím prvku Výběr data a času. Další informace o tomto oznámení najdete v tématu [podporuje pole zpětného volání v ovládacím prvku DTP](/windows/desktop/Controls/date-and-time-picker-controls) v sadě Windows SDK.

## <a name="see-also"></a>Viz také:

[Používání atributu CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
