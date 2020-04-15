---
title: Práce s ovládacím prvkem panel nástrojů
ms.date: 11/04/2016
helpviewer_keywords:
- GetToolBarCtrl method [MFC]
- toolbars [MFC], accessing common control
- CToolBarCtrl class [MFC], accessing toolbar
- toolbar controls [MFC], accessing
ms.assetid: b19409d5-3831-42c7-80ae-195c49dc9085
ms.openlocfilehash: 371f1944fae655556bbc9f89d7ffcce7cc326e5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365252"
---
# <a name="working-with-the-toolbar-control"></a>Práce s ovládacím prvkem panel nástrojů

Tento článek vysvětluje, jak můžete získat přístup k [ctoolbarctrl](../mfc/reference/ctoolbarctrl-class.md) objekt základní [CToolBar](../mfc/reference/ctoolbar-class.md) pro větší kontrolu nad panely nástrojů. Toto je pokročilé téma.

## <a name="procedures"></a>Procedury

#### <a name="to-access-the-toolbar-common-control-underlying-your-ctoolbar-object"></a>Přístup k běžnému ovládacímu prvku panelu nástrojů, který je základem objektu CToolBar

1. Volání [CToolBar::GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl).

`GetToolBarCtrl`vrátí odkaz na objekt [CToolBarCtrl.](../mfc/reference/ctoolbarctrl-class.md) Odkaz můžete použít k volání členských funkcí třídy řízení panelu nástrojů.

> [!CAUTION]
> Při `CToolBarCtrl` volání **Get** funkce je bezpečné, buďte opatrní, pokud voláte **Set** funkce. Toto je pokročilé téma. Za normálních okolností byste neměli potřebovat přístup k základnímu ovládacímu prvku panelu nástrojů.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o

- [Ovládací prvky (běžné ovládací prvky systému Windows)](../mfc/controls-mfc.md)

- [Základy panelu nástrojů](../mfc/toolbar-fundamentals.md)

- [Dokovací a plovoucí panely nástrojů](../mfc/docking-and-floating-toolbars.md)

- [Dynamická změna velikosti panelu nástrojů](../mfc/docking-and-floating-toolbars.md)

- [Tipy nástrojů panelu nástrojů](../mfc/toolbar-tool-tips.md)

- [Aktualizace stavového řádku Flyby](../mfc/toolbar-tool-tips.md)

- [Zpracování oznámení tipu nástroje](../mfc/handling-tool-tip-notifications.md)

- [Třídy CToolBar](../mfc/reference/ctoolbar-class.md) a [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)

- [Zpracování oznámení o přizpůsobení](../mfc/handling-customization-notifications.md)

- [Více panelů nástrojů](../mfc/toolbar-fundamentals.md)

- [Používání starých panelů nástrojů](../mfc/using-your-old-toolbars.md)

- [Ovládací panely](../mfc/control-bars.md)

Obecné informace o použití běžných ovládacích prvků systému Windows naleznete [v tématu Common Controls](/windows/win32/Controls/common-controls-intro).

## <a name="see-also"></a>Viz také

[Implementace panelu nástrojů v prostředí MFC](../mfc/mfc-toolbar-implementation.md)
