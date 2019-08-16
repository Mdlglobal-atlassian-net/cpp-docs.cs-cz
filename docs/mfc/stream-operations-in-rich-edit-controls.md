---
title: Operace s datovými proudy v ovládacích prvcích pro úpravy s formátováním
ms.date: 11/04/2016
helpviewer_keywords:
- CRichEditCtrl class [MFC], stream operations
- CRichEditCtrl class [MFC], stream storage
- rich edit controls [MFC], stream operations
- storage, stream in CRichEditCtrl
- stream operations in CRichEditCtrl
- stream storage and CRichEditCtrl
ms.assetid: 110b4684-1e76-4ca6-9ef0-5bc8b2d93c78
ms.openlocfilehash: 73277f59dc0ad4dfe21d481d0b893903ed407ea9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512952"
---
# <a name="stream-operations-in-rich-edit-controls"></a>Operace s datovými proudy v ovládacích prvcích pro úpravy s formátováním

Datové proudy můžete použít k přenosu dat do nebo z ovládacího prvku Rich Edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Datový proud je definován pomocí struktury [EDITSTREAM](/windows/win32/api/richedit/ns-richedit-editstream) , která určuje vyrovnávací paměť a funkci zpětného volání definované aplikací.

Chcete-li číst data do ovládacího prvku pro úpravy s formátováním (to znamená streamování dat v rámci), použijte členskou funkci [streamin](../mfc/reference/cricheditctrl-class.md#streamin) . Ovládací prvek opakovaně volá funkci zpětného volání definovaného aplikací, která pokaždé převede část dat do vyrovnávací paměti.

Pokud chcete uložit obsah ovládacího prvku pro úpravy s formátováním (to znamená streamování dat z datového proudu), můžete [](../mfc/reference/cricheditctrl-class.md#streamout) použít členskou funkci streamování. Ovládací prvek opakovaně zapisuje do vyrovnávací paměti a pak zavolá funkci zpětného volání definované aplikací. Pro každé volání funkce zpětného volání uloží obsah vyrovnávací paměti.

## <a name="see-also"></a>Viz také:

[Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
