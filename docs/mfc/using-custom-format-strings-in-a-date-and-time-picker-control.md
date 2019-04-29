---
title: Použití řetězců vlastního formátu v ovládacím prvku pro výběr data a času
ms.date: 11/04/2016
helpviewer_keywords:
- CDateTimeCtrl class [MFC], display styles
- DateTimePicker control [MFC], display styles
- DateTimePicker control [MFC]
ms.assetid: 7d577f03-6ca0-4597-9093-50b78f304719
ms.openlocfilehash: 8da5ecaf473d6d3c35ddc1b95ac856ce8c12f163
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411618"
---
# <a name="using-custom-format-strings-in-a-date-and-time-picker-control"></a>Použití řetězců vlastního formátu v ovládacím prvku pro výběr data a času

Ve výchozím nastavení prvků pro výběr data a času poskytují že tři typy (každý formát odpovídá stylu jedinečný) formát pro zobrazení aktuálního data a času:

- **DTS_LONGDATEFORMAT** zobrazí datum v dlouhém formátu vytváří výstup podobný "Wednesday, 3 leden 2000".

- **DTS_SHORTDATEFORMAT** zobrazí datum v krátkém formátu vytváří výstup podobný "1/3/00".

- **DTS_TIMEFORMAT** zobrazí čas v dlouhém formátu vytváří výstup podobný "17:31:42: 00".

Můžete však přizpůsobit vzhled data a času pomocí vlastního formátovacího řetězce. Tento vlastní řetězec se skládá z existující formátování znaků, znaky nonformat nebo kombinaci obojího. Jakmile vlastního řetězce sestavován, volají [CDateTimeCtrl::SetFormat](../mfc/reference/cdatetimectrl-class.md#setformat) předávání do vlastního řetězce. Prvku Výběr data a času se potom zobrazí aktuální hodnotu pomocí vlastního formátovacího řetězce.

Následující příklad kódu (kde *m_dtPicker* je `CDateTimeCtrl` objekt) ukazuje jedním z možných řešení:

[!code-cpp[NVC_MFCControlLadenDialog#7](../mfc/codesnippet/cpp/using-custom-format-strings-in-a-date-and-time-picker-control_1.cpp)]

Kromě vlastních formátovacích řetězců, výběr data a času řídí také podporu [pole zpětného volání](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md).

## <a name="see-also"></a>Viz také:

[Používání atributu CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
