---
title: Neomezené ovládací prvky pro úpravy s formátováním
ms.date: 11/04/2016
helpviewer_keywords:
- bottomless rich edit controls
- rich edit controls [MFC], bottomless
- CRichEditCtrl class [MFC], bottomless
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
ms.openlocfilehash: d5650d34ffc350444061aa6147c38af016458811
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915257"
---
# <a name="bottomless-rich-edit-controls"></a>Neomezené ovládací prvky pro úpravy s formátováním

Vaše aplikace může změnit velikost ovládacího prvku Rich Edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) podle potřeby tak, aby měla vždycky stejnou velikost jako jeho obsah. Ovládací prvek s bohatou úpravou, který se nazývá "bezchybně", odesílá do svého nadřazeného okna zprávu s oznámením [EN_REQUESTRESIZE](/windows/desktop/Controls/en-requestresize) vždy, když se změní velikost jeho obsahu.

Při zpracování zprávy s oznámením **EN_REQUESTRESIZE** by aplikace měla změnit velikost ovládacího prvku na dimenze v zadané struktuře [REQRESIZE](/windows/desktop/api/richedit/ns-richedit-reqresize) . Aplikace může také přesunout jakékoli informace v blízkosti ovládacího prvku, aby se vešel na změnu výšky ovládacího prvku. Chcete-li změnit velikost ovládacího prvku, můžete `CWnd` použít funkci [SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos).

K odeslání zprávy s oznámením **EN_REQUESTRESIZE** pomocí členské funkce [REQUESTRESIZE](../mfc/reference/cricheditctrl-class.md#requestresize) můžete vynutit nefunkční ovládací prvek pro úpravy s formátováním. Tato zpráva může být užitečná v obslužné rutině pro [Velikost](../mfc/reference/cwnd-class.md#onsize) .

Chcete-li dostávat zprávy s oznámením **EN_REQUESTRESIZE** , je nutné povolit oznámení `SetEventMask` pomocí členské funkce.

## <a name="see-also"></a>Viz také:

[Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
