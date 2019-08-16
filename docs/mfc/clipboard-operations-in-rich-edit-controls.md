---
title: Operace se schránkou v ovládacích prvcích pro úpravy s formátováním
ms.date: 11/04/2016
helpviewer_keywords:
- pasting Clipboard data
- CRichEditCtrl class [MFC], paste operation
- cut operation in CRichEditCtrl class [MFC]
- CRichEditCtrl class [MFC], Clipboard operations
- copy operations in rich edit controls
- Clipboard, operations in CRichEditCtrl
- rich edit controls [MFC], Clipboard operations
ms.assetid: 15ce66bc-2636-4a35-a2ae-d52285dc1af6
ms.openlocfilehash: e232010b443ace245844f1c28649477cccc8e9e4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508968"
---
# <a name="clipboard-operations-in-rich-edit-controls"></a>Operace se schránkou v ovládacích prvcích pro úpravy s formátováním

Aplikace může vložit obsah schránky do ovládacího prvku RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) s použitím nejlepšího dostupného formátu schránky nebo konkrétního formátu schránky. Můžete také určit, zda je ovládací prvek s bohatou úpravou schopný Vložit formát schránky.

Obsah aktuálního výběru můžete kopírovat nebo vyjmout pomocí funkce [Kopírovat](../mfc/reference/cricheditctrl-class.md#copy) nebo [Vyjmout](../mfc/reference/cricheditctrl-class.md#cut) členskou funkci. Podobně můžete vložit obsah schránky do ovládacího prvku pro úpravy s formátováním pomocí funkce [Vložit](../mfc/reference/cricheditctrl-class.md#paste) člen. Ovládací prvek se vloží do prvního dostupného formátu, který rozpozná, což je nejpravděpodobnější, že je nejvýstižnější formát.

Pro vložení konkrétního formátu schránky můžete použít členskou funkci [PasteSpecial](../mfc/reference/cricheditctrl-class.md#pastespecial) . Tato funkce je užitečná pro aplikace s příkazem Vložit Special, který umožňuje uživateli vybrat formát schránky. Členskou funkci [CanPaste](../mfc/reference/cricheditctrl-class.md#canpaste) lze použít k určení, zda je daný formát rozpoznáván ovládacím prvkem.

Můžete také použít `CanPaste` k určení, zda je libovolný dostupný formát schránky rozpoznán pomocí ovládacího prvku Rich Edit. Tato funkce je užitečná v `OnInitMenuPopup` obslužné rutině. Aplikace může povolit nebo stínovat svůj příkaz pro vložení v závislosti na tom, zda ovládací prvek může vkládat libovolný dostupný formát.

Ovládací prvky Rich Edit registrují dva formáty schránky: formátovaný text a formát s názvem RichEdit text a objekty. Aplikace může tyto formáty zaregistrovat pomocí funkce [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) a zadat hodnoty **CF_RTF** a **CF_RETEXTOBJ** .

## <a name="see-also"></a>Viz také:

[Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
