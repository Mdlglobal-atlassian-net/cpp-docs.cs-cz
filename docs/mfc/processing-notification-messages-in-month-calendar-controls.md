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
ms.openlocfilehash: fc0bb475a95450c281c92b500083c9502df50931
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346145"
---
# <a name="processing-notification-messages-in-month-calendar-controls"></a>Zpracování zpráv s oznámením v ovládacím prvku měsíční kalendář

Jak uživatelé komunikovat s ovládacím prvku měsíční kalendář (Výběr data a/nebo zobrazení jiného měsíce), ovládacího prvku (`CMonthCalCtrl`) odesílá zprávy s oznámením nezašle nadřazenému oknu, obvykle objekt zobrazení nebo dialogového okna. Tyto zprávy zpracovávají, pokud budete chtít udělat něco v odpovědi. Například když uživatel vybere na nový měsíc, chcete-li zobrazit, můžete poskytnout sadu kalendářních dat, které by měl být oznámil.

Použijte okno Vlastnosti pro přidání obslužné rutiny oznamovacích do nadřazené třídu pro ty zprávy, které chcete implementovat.

Následující seznam popisuje různé upozornění odeslaných nástrojem ovládací prvek měsíční kalendář.

- Vyžaduje mcn_getdaystate – informace o tom, které mají být zobrazeny dny tučným písmem. Informace o zpracování toto oznámení, naleznete v tématu [nastavení stavu dne ovládací prvek měsíční kalendář](../mfc/setting-the-day-state-of-a-month-calendar-control.md).

- Upozorňují MCN_SELCHANGE nadřazeného objektu, který došlo ke změně vybrané datum nebo rozsah data.

- Upozorňují MCN_SELECT nadřazeného objektu, který byl proveden výběru explicitní data.

## <a name="see-also"></a>Viz také:

[Používání atributu CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
