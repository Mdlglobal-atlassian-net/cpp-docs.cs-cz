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
ms.openlocfilehash: 8d1a13b1921f111d97bb515e7932a0116277f9ed
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411601"
---
# <a name="using-drop-down-buttons-in-a-toolbar-control"></a>Použití rozevíracích tlačítek v ovládacím prvku panel nástrojů

Kromě standardních tlačítek panelu nástrojů můžete taky nechat rozevíracích tlačítek. Tlačítko rozevíracího seznamu je obvykle indikován přítomnosti připojené dolů šipkami.

> [!NOTE]
>  Připojené klávesu šipka se zobrazí jenom v případě, že byla nastavena TBSTYLE_EX_DRAWDDARROWS rozšířený styl.

Když uživatel klikne na tuto šipku (nebo tlačítko, samostatně, pokud je k dispozici žádné šipka), tbn_dropdown – oznámení, přijde na nadřazený ovládací prvek panelu nástrojů. Potom můžete zpracovávat toto oznámení a zobrazí místní nabídka; Podobně se aplikace Internet Explorer.

Následující postup ukazuje, jak implementovat tlačítko rozevíracího seznamu nástrojů pomocí místní nabídky:

### <a name="to-implement-a-drop-down-button"></a>Chcete-li implementovat tlačítko rozevíracího seznamu

1. Jakmile vaše `CToolBarCtrl` objekt byl vytvořen, nastavit styl TBSTYLE_EX_DRAWDDARROWS, pomocí následujícího kódu:

   [!code-cpp[NVC_MFCControlLadenDialog#36](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_1.cpp)]

1. Nastavit styl TBSTYLE_DROPDOWN pro všechny nové ([InsertButton](../mfc/reference/ctoolbarctrl-class.md#insertbutton) nebo [AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons)) nebo existující ([SetButtonInfo](../mfc/reference/ctoolbarctrl-class.md#setbuttoninfo)) tlačítka, které se bude rozevíracích tlačítek. Následující příklad ukazuje úprava existující tlačítko v `CToolBarCtrl` objektu:

   [!code-cpp[NVC_MFCControlLadenDialog#37](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_2.cpp)]

1. Přidáte obslužnou rutinu tbn_dropdown – nadřazené třídy objektu panelu nástrojů.

   [!code-cpp[NVC_MFCControlLadenDialog#38](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_3.cpp)]

1. V obslužné rutině nové zobrazení příslušné místní nabídka. Následující kód ukazuje jednu metodu:

   [!code-cpp[NVC_MFCControlLadenDialog#39](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_4.cpp)]

## <a name="see-also"></a>Viz také:

[Používání atributu CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
