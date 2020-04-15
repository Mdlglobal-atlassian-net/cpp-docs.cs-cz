---
title: Použití rozevíracích tlačítek v ovládacím prvku panel nástrojů
ms.date: 11/04/2016
f1_keywords:
- TBN_DROPDOWN
- TBSTYLE_EX_DRAWDDARROWS
helpviewer_keywords:
- CToolBarCtrl class [MFC], drop-down buttons
- toolbars [MFC], drop-down buttons
- drop-down buttons in toolbars
- TBSTYLE_EX_DRAWDDARROWS
- TBN_DROPDOWN notification [MFC]
ms.assetid: b859f758-d2f6-40d9-9c26-0ff61993b9b2
ms.openlocfilehash: 0bc4df4c07ec4b8bc5b488925cbb140609302186
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365066"
---
# <a name="using-drop-down-buttons-in-a-toolbar-control"></a>Použití rozevíracích tlačítek v ovládacím prvku panel nástrojů

Kromě standardních tlačítek může mít panel nástrojů také rozevírací tlačítka. Rozevírací tlačítko je obvykle indikováno přítomností připojené šipky dolů.

> [!NOTE]
> Připojená šipka dolů se zobrazí pouze v případě, že byl nastaven TBSTYLE_EX_DRAWDDARROWS rozšířený styl.

Když uživatel klepne na tuto šipku (nebo samotné tlačítko, pokud není k dispozici žádná šipka), TBN_DROPDOWN oznámení je odeslána nadřazenému ovládacímu prvku panelu nástrojů. Toto oznámení pak můžete zpracovat a zobrazit rozbalovací nabídku. podobně jako chování aplikace Internet Explorer.

Následující postup ukazuje, jak implementovat rozbalovací tlačítko panelu nástrojů s rozbalovací nabídkou:

### <a name="to-implement-a-drop-down-button"></a>Implementace rozevíracího tlačítka

1. Po `CToolBarCtrl` vytvoření objektu nastavte styl TBSTYLE_EX_DRAWDDARROWS pomocí následujícího kódu:

   [!code-cpp[NVC_MFCControlLadenDialog#36](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_1.cpp)]

1. Nastavte styl TBSTYLE_DROPDOWN pro všechna nová tlačítka[(InsertButton](../mfc/reference/ctoolbarctrl-class.md#insertbutton) nebo [AddButtons)](../mfc/reference/ctoolbarctrl-class.md#addbuttons)nebo existující tlačítka[(SetButtonInfo),](../mfc/reference/ctoolbarctrl-class.md#setbuttoninfo)která budou rozevíracími tlačítky. Následující příklad ukazuje úpravu existujícího `CToolBarCtrl` tlačítka v objektu:

   [!code-cpp[NVC_MFCControlLadenDialog#37](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_2.cpp)]

1. Přidejte obslužnou rutinu TBN_DROPDOWN do nadřazené třídy objektu panelu nástrojů.

   [!code-cpp[NVC_MFCControlLadenDialog#38](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_3.cpp)]

1. V nové obslužné rutině zobrazte příslušnou místní nabídku. Následující kód ukazuje jednu metodu:

   [!code-cpp[NVC_MFCControlLadenDialog#39](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_4.cpp)]

## <a name="see-also"></a>Viz také

[Používání atributu CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
