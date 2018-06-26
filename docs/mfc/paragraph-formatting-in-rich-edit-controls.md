---
title: Formátování odstavců v ovládacích prvcích pro úpravy s formátováním | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rich edit controls [MFC], paragraph formatting in
- paragraph formatting in CRichEditCtrl [MFC]
- CRichEditCtrl class [MFC], paragraph formatting in
- formatting [MFC], paragraphs
ms.assetid: 0df2e4c9-2074-4e41-b913-87cb8c1b4d43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9417fe9bab9b1fca8ec8292e27efc02afec5511c
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929144"
---
# <a name="paragraph-formatting-in-rich-edit-controls"></a>Formátování odstavců v ovládacích prvcích pro úpravy s formátováním
Můžete použít členské funkce ovládacího prvku RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) k formátování odstavců a načíst informace o formátování. Atributy formátování odstavce zahrnují zarovnání, tabulátory, odsazení a číslování.  
  
 Můžete provést pomocí formátování odstavců [SetParaFormat](../mfc/reference/cricheditctrl-class.md#setparaformat) – členská funkce. Chcete-li zjistit aktuální formátování pro vybraný text odstavce, použijte [GetParaFormat](../mfc/reference/cricheditctrl-class.md#getparaformat) – členská funkce. [PARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787940) struktura s tyto členské funkce slouží k určení atributy odstavce. Mezi důležité členů **PARAFORMAT** je *dwMask*. V `SetParaFormat`, *dwMask* určuje voláním této funkce bude nastavena atributy, které odstavce. `GetParaFormat` sestavy atributy prvním odstavci ve výběru; *dwMask* Určuje atributy, které jsou konzistentní v rámci výběr.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

