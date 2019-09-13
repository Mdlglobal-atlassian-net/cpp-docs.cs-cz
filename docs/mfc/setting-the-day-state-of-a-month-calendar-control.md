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
ms.openlocfilehash: b8a91c8b0c3bdef9256628b9226c5f3ff154ed7d
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907530"
---
# <a name="setting-the-day-state-of-a-month-calendar-control"></a>Nastavení stavu dne v ovládacím prvku měsíční kalendář

Jedním z atributů ovládacího prvku měsíční kalendář je schopnost ukládat informace, které jsou označovány jako denní stav ovládacího prvku, pro každý den v měsíci. Tyto informace slouží k zdůraznění určitých kalendářních dat v aktuálně zobrazeném měsíci.

> [!NOTE]
>  `CMonthCalCtrl` Objekt musí mít styl MCS_DAYSTATE, aby zobrazoval informace o stavu dne.

Informace o stavu dne se vyjadřují jako 32 datový typ **MONTHDAYSTATE**. Každý bit v **MONTHDAYSTATE** bitovém poli (1 až 31) představuje stav dne v měsíci. Pokud je bit zapnutý, zobrazí se odpovídající den tučně. v opačném případě se zobrazí bez zdůraznění.

Existují dva způsoby, jak nastavit stav dne v ovládacím prvku měsíční kalendář: explicitně voláním metody [atributu CMonthCalCtrl:: SetDayState](../mfc/reference/cmonthcalctrl-class.md#setdaystate) nebo zpracováním zprávy s oznámením MCN_GETDAYSTATE.

## <a name="handling-the-mcn_getdaystate-notification-message"></a>Zpracování zprávy s oznámením MCN_GETDAYSTATE

Ovládací prvek odesílá zprávu MCN_GETDAYSTATE, která určuje, jak se mají zobrazovat dny v zobrazených měsících.

> [!NOTE]
>  Vzhledem k tomu, že ovládací prvek ukládá do mezipaměti předchozí a následující měsíce v souvislosti s viditelným měsícem, obdržíte toto oznámení při každém výběru nového měsíce.

Chcete-li správně zpracovat tuto zprávu, je nutné určit, kolik měsíců má být žádáno o stavové informace, inicializovat pole **MONTHDAYSTATE** struktur se správnými hodnotami a inicializovat člena související struktury s novým informace. Následující postup, který podrobně popisuje nezbytné kroky, předpokládá `CMonthCalCtrl` , že máte objekt nazvaný *m_monthcal* a pole objektů **MONTHDAYSTATE** , *mdState*.

#### <a name="to-handle-the-mcn_getdaystate-notification-message"></a>Postup zpracování zprávy s oznámením MCN_GETDAYSTATE

1. Pomocí [Průvodce třídou](reference/mfc-class-wizard.md)přidejte obslužnou rutinu oznámení pro zprávu MCN_GETDAYSTATE do objektu *M_monthcal* (viz [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md)).

1. Do těla obslužné rutiny přidejte následující kód:

   [!code-cpp[NVC_MFCControlLadenDialog#26](../mfc/codesnippet/cpp/setting-the-day-state-of-a-month-calendar-control_1.cpp)]

   Příklad převede ukazatel *pNMHDR* na správný typ a pak určí počet měsíců, o které se mají informace vyžádat (`pDayState->cDayState`). V každém měsíci je aktuální bitového pole (`pDayState->prgDayState[i]`) inicializována na nulu a pak jsou nastavena potřebná data (v tomto případě 15.15 měsíců v měsíci).

## <a name="see-also"></a>Viz také:

[Používání atributu CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
