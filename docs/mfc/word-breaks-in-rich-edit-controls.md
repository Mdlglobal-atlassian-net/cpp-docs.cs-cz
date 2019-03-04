---
title: Dělení textu v ovládacích prvcích pro úpravy s formátováním
ms.date: 11/04/2016
helpviewer_keywords:
- CRichEditCtrl class [MFC], word breaks in
- word breaks
- breaking words in CRichEditCtrl
- rich edit controls [MFC], word breaks in
ms.assetid: 641dcf9e-7b40-4dc0-85f7-575a8c142f73
ms.openlocfilehash: e71643350ced5b8ecff7c8ac7829741cc3e8493b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57291181"
---
# <a name="word-breaks-in-rich-edit-controls"></a>Dělení textu v ovládacích prvcích pro úpravy s formátováním

Ovládací prvek pro úpravy s formátováním ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) volá funkci s názvem "konec procedury slovo" najít zalomení mezi slovy a zjistit, kde může dojít k narušení řádky. Ovládací prvek používá tyto informace při provádění operace zalamování slov a při zpracování kombinace kláves CTRL + Šipka doleva a CTRL + ŠIPKA vpravo. Aplikace může odesílat zprávy do ovládacího prvku RichEdit nahradit výchozí postupu dělením slov k načtení informací dělením slov a na zjištění, co daný znak řádku připadá.

## <a name="see-also"></a>Viz také:

[Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
