---
title: Přístup k vloženému ovládacímu prvku měsíční kalendář
ms.date: 11/04/2016
helpviewer_keywords:
- DateTimePicker control [MFC], accessing month calendar
- CDateTimeCtrl class [MFC], accessing embedded control
- month calendar controls [MFC], embedded in date/time picker
- CMonthCalCtrl class [MFC], changing the font
- month calendar controls [MFC], changing the font
- DateTimePicker control [MFC]
ms.assetid: 355e97ed-cf81-4df3-a2f8-9ddbbde93227
ms.openlocfilehash: 69270cc5663406f2c5d38ffccdbd35f39298a3d5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354186"
---
# <a name="accessing-the-embedded-month-calendar-control"></a>Přístup k vloženému ovládacímu prvku měsíční kalendář

Vložený objekt ovládacího prvku kalendáře měsíce `CDateTimeCtrl` lze přistupovat z objektu s voláním členské funkce [GetMonthCalCtrl.](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl)

> [!NOTE]
> Vložený ovládací prvek kalendáře měsíce se používá pouze v případě, že ovládací prvek výběru data a času nemá **nastavenDTS_UPDOWN** styl.

To je užitečné, pokud chcete upravit určité atributy před zobrazením vloženého ovládacího prvku. Chcete-li to provést, zpracovat **DTN_DROPDOWN** oznámení, načíst ovládací prvek kalendář měsíce (pomocí [CDateTimeCtrl::GetMonthCalCtrl](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl)) a proveďte změny. Bohužel ovládací prvek měsíčního kalendáře není trvalý.

Jinými slovy, když uživatel požádá o zobrazení ovládacího prvku kalendáře měsíce, vytvoří se nový ovládací prvek kalendáře měsíce (před **DTN_DROPDOWN** oznámení). Ovládací prvek je zničen (po **DTN_CLOSEUP** oznámení) při zavření uživatelem. To znamená, že všechny atributy, které upravíte před zobrazením vloženého ovládacího prvku, budou ztraceny při zavření vloženého ovládacího prvku.

Následující příklad ukazuje tento postup pomocí obslužné rutiny pro **oznámení DTN_DROPDOWN.** Kód změní barvu pozadí ovládacího prvku měsíčního kalendáře s voláním [SetMonthCalColor](../mfc/reference/cdatetimectrl-class.md#setmonthcalcolor)na šedou. Kód je následující:

[!code-cpp[NVC_MFCControlLadenDialog#5](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_1.cpp)]

Jak již bylo uvedeno dříve, všechny změny vlastností ovládacího prvku kalendář měsíce jsou ztraceny, se dvěma výjimkami, když je vložený ovládací prvek zamítnut. První výjimka, barvy ovládacího prvku měsíčního kalendáře, již byla diskutována. Druhou výjimkou je písmo používané ovládacím prvkem kalendáře měsíce. Výchozí písmo můžete upravit voláním [cDateTimeCtrl::SetMonthCalFont](../mfc/reference/cdatetimectrl-class.md#setmonthcalfont), předáním popisovače existujícího písma. Následující příklad (kde `m_dtPicker` je objekt řízení data a času) ukazuje jednu možnou metodu:

[!code-cpp[NVC_MFCControlLadenDialog#6](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_2.cpp)]

Po změně písma, s voláním na `CDateTimeCtrl::SetMonthCalFont`, nové písmo je uložen a použit při příštím měsíční kalendář má být zobrazen.

## <a name="see-also"></a>Viz také

[Používání atributu CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
