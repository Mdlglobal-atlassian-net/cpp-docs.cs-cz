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
ms.openlocfilehash: 04cf0b06773937bf66defccbb0e5e880c06e8d88
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267976"
---
# <a name="stream-operations-in-rich-edit-controls"></a>Operace s datovými proudy v ovládacích prvcích pro úpravy s formátováním

Datové proudy můžete použít k přenosu dat do nebo ven z ovládacího prvku ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Datový proud je určené [EDITSTREAM](/windows/desktop/api/richedit/ns-richedit-_editstream) struktura, která určuje vyrovnávací paměti a funkci zpětného volání definované aplikací.

Číst data na bohaté ovládacích prvků pro úpravy (tedy Streamovat data v), použijte [StreamIn](../mfc/reference/cricheditctrl-class.md#streamin) členskou funkci. Ovládací prvek opakovaně volá funkci zpětného volání definované aplikací, která přenáší část dat do vyrovnávací paměti pokaždé, když.

Chcete-li uložit obsah s formátováním ovládacích prvků pro úpravy (to znamená, že datový proud stream výstupní data), můžete použít [StreamOut](../mfc/reference/cricheditctrl-class.md#streamout) členskou funkci. Ovládací prvek opakovaně zapíše do vyrovnávací paměti a potom volá funkci zpětného volání definované aplikací. Pro každé volání funkce zpětného volání obsah uloží do vyrovnávací paměti.

## <a name="see-also"></a>Viz také:

[Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
