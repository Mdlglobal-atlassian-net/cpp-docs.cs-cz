---
title: Formátování odstavců v ovládacích prvcích pro úpravy s formátováním
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC], paragraph formatting in
- paragraph formatting in CRichEditCtrl [MFC]
- CRichEditCtrl class [MFC], paragraph formatting in
- formatting [MFC], paragraphs
ms.assetid: 0df2e4c9-2074-4e41-b913-87cb8c1b4d43
ms.openlocfilehash: f79d9a97554e2f73b42746c9e9094b07a37513d8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581971"
---
# <a name="paragraph-formatting-in-rich-edit-controls"></a>Formátování odstavců v ovládacích prvcích pro úpravy s formátováním

Můžete členské funkce ovládacího prvku RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) formát odstavců a načte informace o formátování. Atributy formátování odstavce zahrnují zarovnání, karty, odrážky a číslování pro identifikátory.

Můžete provést s použitím formátování odstavců [SetParaFormat](../mfc/reference/cricheditctrl-class.md#setparaformat) členskou funkci. Chcete-li zjistit aktuální formát u vybraného textu odstavce, použijte [GetParaFormat](../mfc/reference/cricheditctrl-class.md#getparaformat) členskou funkci. [PARAFORMAT](/windows/desktop/api/richedit/ns-richedit-_paraformat) struktura s tyto členské funkce slouží k určení atributy odstavce. Mezi důležité členy **PARAFORMAT** je *dwMask*. V `SetParaFormat`, *dwMask* Určuje atributy, které odstavec bude nastavena ve volání funkce. `GetParaFormat` sestavy atributy odstavec ve výběru; *dwMask* Určuje atributy, které jsou konzistentní v rámci výběr.

## <a name="see-also"></a>Viz také

[Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

