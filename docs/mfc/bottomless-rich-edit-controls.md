---
title: Neomezené ovládací prvky pro úpravy s formátováním
ms.date: 11/04/2016
helpviewer_keywords:
- bottomless rich edit controls
- rich edit controls [MFC], bottomless
- CRichEditCtrl class [MFC], bottomless
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
ms.openlocfilehash: 4affdbeed723ea83beda785116dc4c45771073b2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509145"
---
# <a name="bottomless-rich-edit-controls"></a>Neomezené ovládací prvky pro úpravy s formátováním

Vaše aplikace může změnit velikost ovládacího prvku Rich Edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) podle potřeby tak, aby měla vždycky stejnou velikost jako jeho obsah. Ovládací prvek s bohatou úpravou, který se nazývá "bezchybně", odesílá do svého nadřazeného okna zprávu s oznámením [EN_REQUESTRESIZE](/windows/win32/Controls/en-requestresize) vždy, když se změní velikost jeho obsahu.

Při zpracování zprávy s oznámením **EN_REQUESTRESIZE** by aplikace měla změnit velikost ovládacího prvku na dimenze v zadané struktuře [REQRESIZE](/windows/win32/api/richedit/ns-richedit-reqresize) . Aplikace může také přesunout jakékoli informace v blízkosti ovládacího prvku, aby se vešel na změnu výšky ovládacího prvku. Chcete-li změnit velikost ovládacího prvku, můžete `CWnd` použít funkci [SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos).

K odeslání zprávy s oznámením **EN_REQUESTRESIZE** pomocí členské funkce [REQUESTRESIZE](../mfc/reference/cricheditctrl-class.md#requestresize) můžete vynutit nefunkční ovládací prvek pro úpravy s formátováním. Tato zpráva může být užitečná v obslužné rutině pro [Velikost](../mfc/reference/cwnd-class.md#onsize) .

Chcete-li dostávat zprávy s oznámením **EN_REQUESTRESIZE** , je nutné povolit oznámení `SetEventMask` pomocí členské funkce.

## <a name="see-also"></a>Viz také:

[Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
