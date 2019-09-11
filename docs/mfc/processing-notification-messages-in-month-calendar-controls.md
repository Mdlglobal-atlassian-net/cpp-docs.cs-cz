---
title: Zpracování zpráv s oznámením v ovládacím prvku měsíční kalendář
ms.date: 11/04/2016
helpviewer_keywords:
- CMonthCalCtrl class [MFC], notifications
- CMonthCalCtrl class [MFC], day states
- month calendar controls [MFC], notification messages
- notifications [MFC], for CMonthCalCtrl
- notifications [MFC], month calendar control
ms.assetid: 607c3e90-0756-493b-9503-ce835a50c7ab
ms.openlocfilehash: 452d24bf1ffd157366f357a510e8c8cfaad28d91
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908081"
---
# <a name="processing-notification-messages-in-month-calendar-controls"></a>Zpracování zpráv s oznámením v ovládacím prvku měsíční kalendář

Jelikož uživatelé pracují s ovládacím prvkem měsíční kalendář (výběr dat nebo zobrazení jiného měsíce), ovládací prvek (`CMonthCalCtrl`) odesílá oznámení do svého nadřazeného okna, obvykle v zobrazení nebo v objektu dialogového okna. Pokud chcete něco udělat v reakci, Zpracujte tyto zprávy. Když například uživatel vybere nový měsíc k zobrazení, můžete zadat sadu kalendářních dat, která by měla být zvýrazněna.

Pomocí [Průvodce třídou](reference/mfc-class-wizard.md) přidejte do nadřazené třídy obslužné rutiny oznámení pro ty zprávy, které chcete implementovat.

Následující seznam popisuje různá oznámení odesílaná ovládacím prvkem měsíční kalendář.

- MCN_GETDAYSTATE žádosti o informace o tom, které dny by se měly zobrazovat tučně. Informace o zpracování tohoto oznámení naleznete v tématu [Nastavení stavu dne v ovládacím prvku měsíční kalendář](../mfc/setting-the-day-state-of-a-month-calendar-control.md).

- MCN_SELCHANGE upozorní nadřazeného objektu na změnu vybraného data nebo rozsahu data.

- MCN_SELECT upozorní nadřazenou položku, že byl proveden explicitní výběr data.

## <a name="see-also"></a>Viz také:

[Používání atributu CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
