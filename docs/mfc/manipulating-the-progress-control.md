---
title: Manipulace s ovládacím prvkem průběh
ms.date: 11/04/2016
helpviewer_keywords:
- CProgressCtrl class [MFC], working with
- progress controls [MFC], manipulating
- CProgressCtrl class [MFC], manipulating
- controlling progress controls [MFC]
- CProgressCtrl class [MFC], using
ms.assetid: 9af561d1-980b-4003-a6da-ff79be15bf23
ms.openlocfilehash: c7c602dcdd70a3539f9137589d31820ee5470e49
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461578"
---
# <a name="manipulating-the-progress-control"></a>Manipulace s ovládacím prvkem průběh

Existují tři způsoby, jak změnit aktuální pozici ovládací prvek průběh ([atributu CProgressCtrl](../mfc/reference/cprogressctrl-class.md)).

- Umístění můžete změnit předvolby zvýšení množství.

- Umístění můžete změnit libovolné množství.

- Umístění můžete změnit na určitou hodnotu.

### <a name="to-change-the-position-by-a-preset-amount"></a>Chcete-li změnit pozici předvolby množství

1. Použití [SetStep](../mfc/reference/cprogressctrl-class.md#setstep) členskou funkci pro nastavení velikosti přírůstku. Ve výchozím nastavení tato hodnota je 10. Tato hodnota je obvykle nastavena jako jeden z počátečního nastavení pro ovládací prvek. Hodnota kroku může být záporné.

1. Použití [StepIt](../mfc/reference/cprogressctrl-class.md#stepit) členská funkce se zvýší na pozici. To způsobí, že svoje vlastní překreslení ovládacího prvku.

    > [!NOTE]
    >  `StepIt` způsobí zalomení pozice. Mějme například rozsah 1 – 100 krok 20 a pozice 90, `StepIt` nastaví pozici na 10.

### <a name="to-change-the-position-by-an-arbitrary-amount"></a>Chcete-li změnit umístění libovolné množství

1. Použití [OffsetPos](../mfc/reference/cprogressctrl-class.md#offsetpos) členská funkce, chcete-li změnit umístění. `OffsetPos` přijme záporné hodnoty.

    > [!NOTE]
    >  `OffsetPos`, na rozdíl od `StepIt`, nebude zabalení pozici. Zůstat v rozsahu se upraví na nové pozici.

### <a name="to-change-the-position-to-a-specific-value"></a>Chcete-li změnit umístění na určitou hodnotu

1. Použití [SetPos](../mfc/reference/cprogressctrl-class.md#setpos) členskou funkci pro nastavení pozice na určitou hodnotu. V případě potřeby upraví se do rozsahu na nové pozici.

Ovládací prvek průběh se obvykle používá pouze pro výstup. K získání aktuální pozici bez zadání nové hodnoty použijte [GetPos](../mfc/reference/cprogressctrl-class.md#getpos).

## <a name="see-also"></a>Viz také

[Používání atributu CProgressCtrl](../mfc/using-cprogressctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

