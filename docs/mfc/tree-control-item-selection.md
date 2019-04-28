---
title: Výběr položek ovládacího prvku strom
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], item selection
- controls [MFC], selecting items in
- CTreeCtrl class [MFC], item selection
- item selection in tree controls
ms.assetid: 7bcb3b16-b9c8-4c06-9350-7bc3c1c5009b
ms.openlocfilehash: a88a2c8ea5b935bbcb1f40b705337ff676d8b8a5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363548"
---
# <a name="tree-control-item-selection"></a>Výběr položek ovládacího prvku strom

Při změně výběru z jedné položky na jiný, ovládací prvek stromu ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) odešle [TVN_SELCHANGING](/windows/desktop/Controls/tvn-selchanging) a [TVN_SELCHANGED](/windows/desktop/Controls/tvn-selchanged) zpráv s oznámením. Obě oznámení zahrnují hodnotu, která určuje, zda změna je výsledkem kliknutí myší nebo stisknutí klávesy. Oznámení také zahrnovat informace o položce, která získává na výběr a položku, která je ztráta výběr. Tyto informace slouží k nastavení atributů položky, které závisí na stavu výběru položky. Vrací **TRUE** v reakci na `TVN_SELCHANGING` brání výběr změny; vrácení **FALSE** umožňuje změnu.

Aplikace můžete změnit výběr voláním [selectitem –](../mfc/reference/ctreectrl-class.md#selectitem) členskou funkci.

## <a name="see-also"></a>Viz také:

[Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
