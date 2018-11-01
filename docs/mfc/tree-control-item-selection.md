---
title: Výběr položek ovládacího prvku strom
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], item selection
- controls [MFC], selecting items in
- CTreeCtrl class [MFC], item selection
- item selection in tree controls
ms.assetid: 7bcb3b16-b9c8-4c06-9350-7bc3c1c5009b
ms.openlocfilehash: bd3ade31ce1e41481943659ba9a8ef8dd77117fb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50592710"
---
# <a name="tree-control-item-selection"></a>Výběr položek ovládacího prvku strom

Při změně výběru z jedné položky na jiný, ovládací prvek stromu ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) odešle [TVN_SELCHANGING](/windows/desktop/Controls/tvn-selchanging) a [TVN_SELCHANGED](/windows/desktop/Controls/tvn-selchanged) zpráv s oznámením. Obě oznámení zahrnují hodnotu, která určuje, zda změna je výsledkem kliknutí myší nebo stisknutí klávesy. Oznámení také zahrnovat informace o položce, která získává na výběr a položku, která je ztráta výběr. Tyto informace slouží k nastavení atributů položky, které závisí na stavu výběru položky. Vrací **TRUE** v reakci na `TVN_SELCHANGING` brání výběr změny; vrácení **FALSE** umožňuje změnu.

Aplikace můžete změnit výběr voláním [selectitem –](../mfc/reference/ctreectrl-class.md#selectitem) členskou funkci.

## <a name="see-also"></a>Viz také

[Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

