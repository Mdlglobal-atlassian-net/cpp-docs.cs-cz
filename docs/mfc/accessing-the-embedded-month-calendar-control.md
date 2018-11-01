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
ms.openlocfilehash: 56a735f9e79ca4f5423201139adc740878afb279
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652533"
---
# <a name="accessing-the-embedded-month-calendar-control"></a>Přístup k vloženému ovládacímu prvku měsíční kalendář

Objekt ovládacího prvku Kalendář vložený měsíc je přístupný z `CDateTimeCtrl` objektu voláním [GetMonthCalCtrl](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl) členskou funkci.

> [!NOTE]
>  Ovládací prvek vložený měsíční kalendář se používá jenom v případě prvku Výběr data a času nemá **DTS_UPDOWN** stylu sady.

To je užitečné, pokud chcete změnit určité atributy před zobrazením vloženému ovládacímu prvku. K dosažení tohoto zpracování **dtn_dropdown –** oznámení, načíst ovládací prvek měsíční kalendář (pomocí [CDateTimeCtrl::GetMonthCalCtrl](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl)) a zkontrolujte provedené změny. Ovládací prvek měsíční kalendář bohužel není trvalý.

Jinými slovy, když uživatel požádá o zobrazení ovládací prvek měsíční kalendář, ovládací prvek nový měsíční kalendář je vytvořen (před **dtn_dropdown –** oznámení). Ovládací prvek zničen (až **dtn_closeup –** oznámení) při uživatelem zamítnuta. To znamená, že všechny atributy, které změníte, před zobrazením vloženému ovládacímu prvku, je ztracena při vloženému ovládacímu prvku se zavře.

Následující příklad ukazuje tento postup pomocí obslužné rutiny pro **dtn_dropdown –** oznámení. Kód změní barvu pozadí v ovládacím prvku měsíční kalendář, voláním [SetMonthCalColor](../mfc/reference/cdatetimectrl-class.md#setmonthcalcolor), šedou barvu. Kód je následujícím způsobem:

[!code-cpp[NVC_MFCControlLadenDialog#5](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_1.cpp)]

Jak bylo uvedeno dříve, všechny změny vlastnosti prvku měsíční kalendář bude ztracen, se dvěma výjimkami, když se zavře vloženému ovládacímu prvku. První výjimkou barvy ovládací prvek měsíční kalendář již probírali. Druhou výjimkou je písmo použité v ovládacím prvku měsíční kalendář. Výchozí písmo můžete upravit tak, že volání [CDateTimeCtrl::SetMonthCalFont](../mfc/reference/cdatetimectrl-class.md#setmonthcalfont), předávání popisovač existující písma. Následující příklad (kde `m_dtPicker` je objekt ovládacího prvku datum a čas) ukazuje možných metod:

[!code-cpp[NVC_MFCControlLadenDialog#6](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_2.cpp)]

Jakmile změníte písmo, voláním `CDateTimeCtrl::SetMonthCalFont`, jsou uloženy a používány při příštím měsíčním kalendáři je zobrazený nový písma.

## <a name="see-also"></a>Viz také

[Používání atributu CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

