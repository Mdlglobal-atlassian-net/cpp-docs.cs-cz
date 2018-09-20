---
title: Formátování odstavců v ovládacích prvcích pro úpravy s formátováním | Dokumentace Microsoftu
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
ms.openlocfilehash: 3192f53ae60f5249cd57fdd23c810b5590e394ab
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375447"
---
# <a name="paragraph-formatting-in-rich-edit-controls"></a>Formátování odstavců v ovládacích prvcích pro úpravy s formátováním

Můžete členské funkce ovládacího prvku RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) formát odstavců a načte informace o formátování. Atributy formátování odstavce zahrnují zarovnání, karty, odrážky a číslování pro identifikátory.

Můžete provést s použitím formátování odstavců [SetParaFormat](../mfc/reference/cricheditctrl-class.md#setparaformat) členskou funkci. Chcete-li zjistit aktuální formát u vybraného textu odstavce, použijte [GetParaFormat](../mfc/reference/cricheditctrl-class.md#getparaformat) členskou funkci. [PARAFORMAT](/windows/desktop/api/richedit/ns-richedit-_paraformat) struktura s tyto členské funkce slouží k určení atributy odstavce. Mezi důležité členy **PARAFORMAT** je *dwMask*. V `SetParaFormat`, *dwMask* Určuje atributy, které odstavec bude nastavena ve volání funkce. `GetParaFormat` sestavy atributy odstavec ve výběru; *dwMask* Určuje atributy, které jsou konzistentní v rámci výběr.

## <a name="see-also"></a>Viz také

[Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

