---
title: Dělení textu v ovládacích prvcích pro úpravy s formátováním | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CRichEditCtrl class [MFC], word breaks in
- word breaks
- breaking words in CRichEditCtrl
- rich edit controls [MFC], word breaks in
ms.assetid: 641dcf9e-7b40-4dc0-85f7-575a8c142f73
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f012897d968d108cb366126fc38992ff1dd11d0a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424609"
---
# <a name="word-breaks-in-rich-edit-controls"></a>Dělení textu v ovládacích prvcích pro úpravy s formátováním

Ovládací prvek pro úpravy s formátováním ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) volá funkci s názvem "konec procedury slovo" najít zalomení mezi slovy a zjistit, kde může dojít k narušení řádky. Ovládací prvek používá tyto informace při provádění operace zalamování slov a při zpracování kombinace kláves CTRL + Šipka doleva a CTRL + ŠIPKA vpravo. Aplikace může odesílat zprávy do ovládacího prvku RichEdit nahradit výchozí postupu dělením slov k načtení informací dělením slov a na zjištění, co daný znak řádku připadá.

## <a name="see-also"></a>Viz také

[Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

