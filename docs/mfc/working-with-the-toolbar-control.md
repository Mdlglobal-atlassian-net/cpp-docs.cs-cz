---
title: Práce s ovládacím prvkem panel nástrojů
ms.date: 11/04/2016
helpviewer_keywords:
- GetToolBarCtrl method [MFC]
- toolbars [MFC], accessing common control
- CToolBarCtrl class [MFC], accessing toolbar
- toolbar controls [MFC], accessing
ms.assetid: b19409d5-3831-42c7-80ae-195c49dc9085
ms.openlocfilehash: 60cc527493e2a68751c201b998ab171c564d6c1f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510576"
---
# <a name="working-with-the-toolbar-control"></a>Práce s ovládacím prvkem panel nástrojů

V tomto článku se dozvíte, jak získat přístup k objektu [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) s podkladovým [CToolBar –](../mfc/reference/ctoolbar-class.md) pro lepší kontrolu nad panely nástrojů. Toto je pokročilé téma.

## <a name="procedures"></a>Procedury

#### <a name="to-access-the-toolbar-common-control-underlying-your-ctoolbar-object"></a>Přístup k běžnému ovládacímu prvku panelu nástrojů na podkladovém objektu CToolBar –

1. Zavolejte [CToolBar –:: GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl).

`GetToolBarCtrl`Vrátí odkaz na objekt [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) . Můžete použít odkaz na volání členských funkcí třídy ovládacího prvku ToolBar.

> [!CAUTION]
>  Volání `CToolBarCtrl` funkce **Get** je bezpečné, při volání funkce **set** buďte opatrní. Toto je pokročilé téma. Normálně byste neměli potřebovat přístup k základnímu ovládacímu prvku ToolBar.

### <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace

- [Ovládací prvky (běžné ovládací prvky systému Windows)](../mfc/controls-mfc.md)

- [Základy panelů nástrojů](../mfc/toolbar-fundamentals.md)

- [Ukotvené a plovoucí panely nástrojů](../mfc/docking-and-floating-toolbars.md)

- [Dynamické změny velikosti panelu nástrojů](../mfc/docking-and-floating-toolbars.md)

- [Tipy k nástrojům na panelu nástrojů](../mfc/toolbar-tool-tips.md)

- [Aktualizace stavového řádku Flyby](../mfc/toolbar-tool-tips.md)

- [Zpracování oznámení popisů nástrojů](../mfc/handling-tool-tip-notifications.md)

- Třídy [CToolBar –](../mfc/reference/ctoolbar-class.md) a [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)

- [Zpracování oznámení o přizpůsobení](../mfc/handling-customization-notifications.md)

- [Více panelů nástrojů](../mfc/toolbar-fundamentals.md)

- [Použití starých panelů nástrojů](../mfc/using-your-old-toolbars.md)

- [Ovládací panely](../mfc/control-bars.md)

Obecné informace o použití běžných ovládacích prvků systému Windows naleznete v tématu [běžné ovládací prvky](/windows/win32/Controls/common-controls-intro).

## <a name="see-also"></a>Viz také:

[Implementace panelu nástrojů v prostředí MFC](../mfc/mfc-toolbar-implementation.md)
