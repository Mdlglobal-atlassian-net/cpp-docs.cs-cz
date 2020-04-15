---
title: Nastavení stavu dne v ovládacím prvku měsíční kalendář
ms.date: 11/04/2016
f1_keywords:
- MCN_GETDAYSTATE
helpviewer_keywords:
- CMonthCalCtrl class [MFC], setting day state info
- MCN_GETDAYSTATE notification [MFC]
- month calendar controls [MFC], day state info
ms.assetid: 435d1b11-ec0e-4121-9e25-aaa6af812a3c
ms.openlocfilehash: 9892f2d853687787dd76428fc9bc95f3a4f74565
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365432"
---
# <a name="setting-the-day-state-of-a-month-calendar-control"></a>Nastavení stavu dne v ovládacím prvku měsíční kalendář

Jedním z atributů ovládacího prvku kalendář měsíce je možnost ukládat informace, označované jako den stavu ovládacího prvku, pro každý den v měsíci. Tyto informace slouží ke zdůraznění určitých dat aktuálně zobrazeného měsíce.

> [!NOTE]
> Objekt `CMonthCalCtrl` musí mít MCS_DAYSTATE styl, aby se zobrazily informace o stavu dne.

Informace o stavu dne jsou vyjádřeny jako 32bitový datový typ **MONTHDAYSTATE**. Každý bit v bitovém poli **MONTHDAYSTATE** (1 až 31) představuje stav dne v měsíci. Pokud je bit zapnutý, odpovídající den se zobrazí tučně; v opačném případě se zobrazí bez důrazu.

Existují dvě metody pro nastavení stavu den ovládacího prvku kalendáře měsíce: explicitně s voláním [CMonthCalCtrl::SetDayState](../mfc/reference/cmonthcalctrl-class.md#setdaystate) nebo zpracováním MCN_GETDAYSTATE oznámení.

## <a name="handling-the-mcn_getdaystate-notification-message"></a>Zpracování MCN_GETDAYSTATE oznamovací zprávy

Zpráva MCN_GETDAYSTATE je odeslána ovládacím prvkem k určení, jak by měly být zobrazeny dny ve viditelných měsících.

> [!NOTE]
> Vzhledem k tomu, že ovládací prvek ukládá do mezipaměti předchozí a následující měsíce, ve vztahu k viditelnému měsíci obdržíte toto oznámení pokaždé, když je vybrán nový měsíc.

Chcete-li správně zpracovat tuto zprávu, musíte určit, kolik měsíců den informace o stavu je požadováno pro, inicializovat pole **MONTHDAYSTATE** struktury se správnými hodnotami a inicializovat související člen struktury s nové informace. Následující postup, podrobně nezbytné kroky, předpokládá, že `CMonthCalCtrl` máte objekt s názvem *m_monthcal* a pole **MONTHDAYSTATE** objekty, *mdState*.

#### <a name="to-handle-the-mcn_getdaystate-notification-message"></a>Zpracování MCN_GETDAYSTATE oznámení

1. Pomocí [Průvodce pro třídy](reference/mfc-class-wizard.md)přidejte do *objektu m_monthcal* obslužnou rutinu oznámení pro zprávu MCN_GETDAYSTATE (viz [Mapování zpráv na funkce).](../mfc/reference/mapping-messages-to-functions.md)

1. V těle obslužné rutiny přidejte následující kód:

   [!code-cpp[NVC_MFCControlLadenDialog#26](../mfc/codesnippet/cpp/setting-the-day-state-of-a-month-calendar-control_1.cpp)]

   Příklad převede ukazatel *pNMHDR* na správný typ a pak určí, kolik`pDayState->cDayState`měsíců informací je požadováno ( ). Pro každý měsíc je aktuální`pDayState->prgDayState[i]`bitfield ( ) inicializován na nulu a pak jsou nastavena potřebná data (v tomto případě 15. dne každého měsíce).

## <a name="see-also"></a>Viz také

[Používání atributu CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
