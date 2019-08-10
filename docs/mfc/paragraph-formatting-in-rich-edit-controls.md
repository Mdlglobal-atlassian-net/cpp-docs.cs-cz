---
title: Formátování odstavců v ovládacích prvcích pro úpravy s formátováním
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC], paragraph formatting in
- paragraph formatting in CRichEditCtrl [MFC]
- CRichEditCtrl class [MFC], paragraph formatting in
- formatting [MFC], paragraphs
ms.assetid: 0df2e4c9-2074-4e41-b913-87cb8c1b4d43
ms.openlocfilehash: 0988e7940c8d8947b86e97a35d71586f8f5c316a
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916378"
---
# <a name="paragraph-formatting-in-rich-edit-controls"></a>Formátování odstavců v ovládacích prvcích pro úpravy s formátováním

Můžete použít členské funkce ovládacího prvku Rich Edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) k formátování odstavců a načtení informací o formátování. Mezi atributy formátování odstavce patří zarovnání, tabulátory, odsazení a číslování.

Formátování odstavců můžete použít pomocí členské funkce [SetParaFormat](../mfc/reference/cricheditctrl-class.md#setparaformat) . Chcete-li zjistit aktuální formátování odstavce pro vybraný text, použijte členskou funkci [GetParaFormat](../mfc/reference/cricheditctrl-class.md#getparaformat) . Struktura [PARAFORMAT](/windows/desktop/api/richedit/ns-richedit-paraformat) se používá s těmito členskými funkcemi k určení atributů odstavce. Jedním z důležitých členů **PARAFORMAT** je *dwMask*. V `SetParaFormat` *dwMask* určuje, které atributy odstavce budou nastaveny tímto voláním funkce. `GetParaFormat`nahlásí atributy prvního odstavce výběru. *dwMask* určuje atributy, které jsou konzistentní v rámci výběru.

## <a name="see-also"></a>Viz také:

[Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
