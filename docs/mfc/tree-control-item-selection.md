---
title: Výběr položek ovládacího prvku strom
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], item selection
- controls [MFC], selecting items in
- CTreeCtrl class [MFC], item selection
- item selection in tree controls
ms.assetid: 7bcb3b16-b9c8-4c06-9350-7bc3c1c5009b
ms.openlocfilehash: 07c7b673e0f9029f8ece928b0ab17760b3863cc7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513342"
---
# <a name="tree-control-item-selection"></a>Výběr položek ovládacího prvku strom

Když se výběr změní z jedné položky na jinou, stromová struktura ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) odesílá zprávy s oznámeními [TVN_SELCHANGING](/windows/win32/Controls/tvn-selchanging) a [TVN_SELCHANGED](/windows/win32/Controls/tvn-selchanged) . Obě oznámení obsahují hodnotu, která určuje, jestli je změna výsledkem kliknutí myší nebo stisknutí klávesy. Oznámení také obsahují informace o položce, která získá výběr, a položku, která je na výběr ztratila. Tyto informace můžete použít k nastavení atributů položky, které závisí na stavu výběru položky. Vrácení **hodnoty true** v reakci `TVN_SELCHANGING` na zabrání změnu výběru. vrácení **false** umožňuje změnu.

Aplikace může změnit výběr voláním členské funkce [SelectItem](../mfc/reference/ctreectrl-class.md#selectitem) .

## <a name="see-also"></a>Viz také:

[Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
