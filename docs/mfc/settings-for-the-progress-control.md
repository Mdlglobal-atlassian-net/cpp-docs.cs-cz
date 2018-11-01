---
title: Nastavení pro ovládací prvek průběh
ms.date: 11/04/2016
helpviewer_keywords:
- CProgressCtrl class [MFC], settings
- progress controls [MFC], settings
ms.assetid: f4616e91-74fa-4000-ba0d-d3ddc0ee075b
ms.openlocfilehash: 444dc45c816e0dfc2fd45bad999ad90c2acacc01
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481776"
---
# <a name="settings-for-the-progress-control"></a>Nastavení pro ovládací prvek průběh

Základní nastavení pro ovládací prvek průběh ([atributu CProgressCtrl](../mfc/reference/cprogressctrl-class.md)) jsou rozsahu a aktuální pozici. Rozsah představuje celou dobu trvání operace. Aktuální pozice představuje pokroku, který vaše aplikace odeslala směrem k dokončení operace. Všechny změny oblast nebo umístění způsobit, že ovládací prvek průběh svoje vlastní překreslení.

Ve výchozím nastavení, je nastaven rozsah 0 - 100 a počáteční pozice je nastavena na hodnotu 0. Chcete-li načíst aktuální nastavení rozsahu pro ovládací prvek průběh, použijte [getrange –](../mfc/reference/cprogressctrl-class.md#getrange) členskou funkci. Chcete-li změnit rozsah, použijte [SetRange](../mfc/reference/cprogressctrl-class.md#setrange) členskou funkci.

Nastavit pozici, použijte [SetPos](../mfc/reference/cprogressctrl-class.md#setpos). Pokud chcete načíst aktuální pozici bez zadání nové hodnoty, použijte [GetPos](../mfc/reference/cprogressctrl-class.md#getpos). Můžete například chtít jednoduše dotazování na stav aktuální operace.

Chcete-li aktuální pozici ovládacím prvkem průběh, použijte [StepIt](../mfc/reference/cprogressctrl-class.md#stepit). Chcete-li nastavit dobu, každý krok, použijte [SetStep](../mfc/reference/cprogressctrl-class.md#setstep)

## <a name="see-also"></a>Viz také

[Používání atributu CProgressCtrl](../mfc/using-cprogressctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

