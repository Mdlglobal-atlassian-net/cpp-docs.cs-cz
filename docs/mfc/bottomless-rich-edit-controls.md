---
title: Neomezené ovládací prvky pro úpravy s formátováním
ms.date: 11/04/2016
helpviewer_keywords:
- bottomless rich edit controls
- rich edit controls [MFC], bottomless
- CRichEditCtrl class [MFC], bottomless
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
ms.openlocfilehash: 6f078680777dcf80a4349ea34e4520cb56031f44
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270641"
---
# <a name="bottomless-rich-edit-controls"></a>Neomezené ovládací prvky pro úpravy s formátováním

Aplikace můžete změnit velikost ovládacího prvku ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) podle potřeby tak, aby se vždy stejnou velikost jako jeho obsah. Ovládací prvek RTF podporuje tuto funkci takzvané "neomezené" odesláním nezašle nadřazenému oknu [EN_REQUESTRESIZE](/windows/desktop/Controls/en-requestresize) oznámení při každé změně velikosti jejího obsahu.

Při zpracování **EN_REQUESTRESIZE** zprávy oznámení, aplikace by měl změnit velikost ovládacího prvku s dimenzemi v zadaném [REQRESIZE](/windows/desktop/api/richedit/ns-richedit-_reqresize) struktury. Aplikace může také přesunout všechny informace v ovládacím prvku tak, aby vyhovovaly Změna ovládacího prvku na výšku. Chcete-li změnit velikost ovládacího prvku, můžete použít `CWnd` funkce [SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos).

Můžete vynutit neomezené ovládacího prvku k odeslání **EN_REQUESTRESIZE** zprávy oznámení pomocí [RequestResize](../mfc/reference/cricheditctrl-class.md#requestresize) členskou funkci. Tato zpráva se může hodit v [upravuje místně](../mfc/reference/cwnd-class.md#onsize) obslužné rutiny.

Pro příjem **EN_REQUESTRESIZE** zpráv s oznámením, musíte povolit oznámení pomocí `SetEventMask` členskou funkci.

## <a name="see-also"></a>Viz také:

[Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
