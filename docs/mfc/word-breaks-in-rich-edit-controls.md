---
title: Dělení textu v ovládacích prvcích pro úpravy s formátováním | Microsoft Docs
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
ms.openlocfilehash: 373a30ed4a327cff99cb3cfce873707314608b57
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="word-breaks-in-rich-edit-controls"></a>Dělení textu v ovládacích prvcích pro úpravy s formátováním
Ovládacích prvků pro úpravy s formátováním ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) volá funkci s názvem "zalomení procedury slovo" najít zalomení mezi slovy a určení, kde ji můžete rozdělit řádky. Ovládací prvek používá tyto informace při provádění operací zalamovat a při zpracování kombinace kláves CTRL + ŠIPKA vlevo a CTRL + ŠIPKA vpravo. Aplikace může odesílat zprávy do ovládacího prvku RichEdit nahradit výchozí postupu dělením slov načíst informace o dělením slov a určit, co řádek daného znaku klesne.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

