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
ms.openlocfilehash: c75b560509738e071accdc3dba31dfdea35a14aa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307754"
---
# <a name="setting-the-day-state-of-a-month-calendar-control"></a>Nastavení stavu dne v ovládacím prvku měsíční kalendář

Jeden z atributů ovládací prvek měsíční kalendář je možnost ukládat informace, označované jako den stav ovládacího prvku pro každý den v měsíci. Tyto informace slouží ke zvýraznění některých dat pro aktuálně zobrazený měsíc.

> [!NOTE]
>  `CMonthCalCtrl` Musí mít objekt style MCS_DAYSTATE zobrazíte informace o stavu den.

Informace o stavu den je vyjádřena jako typ dat 32-bit **MONTHDAYSTATE**. Každý bit ve **MONTHDAYSTATE** bitového pole (1 až 31) představuje stav den v měsíci. Pokud bit zapnutý, zobrazí se odpovídající den v bold; v opačném případě se zobrazí s žádné zvýraznění.

Existují dvě metody pro nastavení stavu dne ovládací prvek měsíční kalendář: explicitně pomocí volání [CMonthCalCtrl::SetDayState](../mfc/reference/cmonthcalctrl-class.md#setdaystate) nebo zpracovává zprávy mcn_getdaystate – oznámení.

## <a name="handling-the-mcngetdaystate-notification-message"></a>Zpracování zprávy mcn_getdaystate – oznámení

Mcn_getdaystate – zpráva je odeslána ovládacího prvku určit, jak mají být zobrazeny dny viditelné měsíců.

> [!NOTE]
>  Vzhledem k tomu, že ovládací prvek předchozích a následujících měsíců, z hlediska zobrazený měsíc ukládá do mezipaměti, zobrazí se toto oznámení pokaždé, když je vybrán nový měsíc.

Správně zpracovat tuto zprávu, musíte určit, kolik měsíců se informace o stavu den požadované pro inicializaci pole **MONTHDAYSTATE** struktury s odpovídajícími hodnotami a inicializace související struktury člena pomocí nové informace. Následující postup s podrobnostmi o nezbytných kroků se předpokládá, že máte `CMonthCalCtrl` objektu s názvem *m_monthcal* a pole **MONTHDAYSTATE** objekty, *mdState*.

#### <a name="to-handle-the-mcngetdaystate-notification-message"></a>Aby se zpracovala zpráva mcn_getdaystate – oznámení

1. V okně Vlastnosti přidejte obslužnou rutinu oznámení pro mcn_getdaystate – zpráva, která má *m_monthcal* objektu (naleznete v tématu [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md)).

1. Do těla obslužné rutiny přidejte následující kód:

   [!code-cpp[NVC_MFCControlLadenDialog#26](../mfc/codesnippet/cpp/setting-the-day-state-of-a-month-calendar-control_1.cpp)]

   Tento příklad převede *pNMHDR* ukazatel na správný typ, pak určuje, kolik měsíců informace jsou požadovány (`pDayState->cDayState`). Pro každý měsíc, aktuální bitového pole (`pDayState->prgDayState[i]`) je inicializován na nulu a potom potřeba data jsou nastaveny (v tomto případě 15. dne každého měsíce).

## <a name="see-also"></a>Viz také:

[Používání atributu CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
