---
title: "Formátování odstavců v ovládacích prvcích pro úpravy s formátováním | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- rich edit controls [MFC], paragraph formatting in
- paragraph formatting in CRichEditCtrl [MFC]
- CRichEditCtrl class [MFC], paragraph formatting in
- formatting [MFC], paragraphs
ms.assetid: 0df2e4c9-2074-4e41-b913-87cb8c1b4d43
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0f0dc12d923f6f424fe84768b0d934d8dd7ff20b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="paragraph-formatting-in-rich-edit-controls"></a>Formátování odstavců v ovládacích prvcích pro úpravy s formátováním
Můžete použít členské funkce ovládacího prvku RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) k formátování odstavců a načíst informace o formátování. Atributy formátování odstavce zahrnují zarovnání, tabulátory, odsazení a číslování.  
  
 Můžete provést pomocí formátování odstavců [SetParaFormat](../mfc/reference/cricheditctrl-class.md#setparaformat) – členská funkce. Chcete-li zjistit aktuální formátování pro vybraný text odstavce, použijte [GetParaFormat](../mfc/reference/cricheditctrl-class.md#getparaformat) – členská funkce. [PARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787940) struktura s tyto členské funkce slouží k určení atributy odstavce. Mezi důležité členů **PARAFORMAT** je **dwMask**. V `SetParaFormat`, **dwMask** určuje voláním této funkce bude nastavena atributy, které odstavce. `GetParaFormat`sestavy atributy prvním odstavci ve výběru; **dwMask** Určuje atributy, které jsou konzistentní v rámci výběr.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

