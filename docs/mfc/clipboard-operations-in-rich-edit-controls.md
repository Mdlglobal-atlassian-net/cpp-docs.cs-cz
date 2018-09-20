---
title: Operace se schránkou v bohatých ovládacích prvcích pro úpravy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- pasting Clipboard data
- CRichEditCtrl class [MFC], paste operation
- cut operation in CRichEditCtrl class [MFC]
- CRichEditCtrl class [MFC], Clipboard operations
- copy operations in rich edit controls
- Clipboard, operations in CRichEditCtrl
- rich edit controls [MFC], Clipboard operations
ms.assetid: 15ce66bc-2636-4a35-a2ae-d52285dc1af6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f978880344113c71f8f22dd3c49e2ec35024a729
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405707"
---
# <a name="clipboard-operations-in-rich-edit-controls"></a>Operace se schránkou v ovládacích prvcích pro úpravy s formátováním

Aplikace můžete vložit obsah schránky do ovládacího prvku ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) pomocí nejlépe dostupné formátu schránky nebo konkrétní formát schránky. Můžete také určit, zda je ovládací prvek RTF dokáže vkládání formát schránky.

Můžete kopírovat nebo vyjmutí obsah aktuální výběr pomocí [kopírování](../mfc/reference/cricheditctrl-class.md#copy) nebo [Vyjmout](../mfc/reference/cricheditctrl-class.md#cut) členskou funkci. Podobně můžete vložit obsah schránky do ovládacího prvku s použitím [vložte](../mfc/reference/cricheditctrl-class.md#paste) členskou funkci. Ovládací prvek vloží první dostupná formát, který rozpozná, což je pravděpodobně nejvíce popisný formátu.

Chcete-li vložit konkrétní formát schránky, můžete použít [PasteSpecial](../mfc/reference/cricheditctrl-class.md#pastespecial) členskou funkci. Tato funkce je užitečná pro aplikace, která umožňuje uživateli vybrat formát schránky Vložit jinak příkazem. Můžete použít [CanPaste](../mfc/reference/cricheditctrl-class.md#canpaste) členskou funkci k určení, zda je daný formát rozpoznáván ovládacího prvku.

Můžete také použít `CanPaste` k určení, zda všechny dostupné formát schránky je rozpoznáván ovládacího prvku. Tato funkce je užitečná v `OnInitMenuPopup` obslužné rutiny. Aplikace může povolit nebo šedý jeho příkaz Paste v závislosti na tom, zda ovládací prvek můžete vložit libovolný formát k dispozici.

RichEdit ovládací prvky registrace dva formáty schránky: formátu RTF a formátu textu RichEdit a objektů. Aplikace můžete registrovat pomocí těchto formátů [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) fungovala, určení **CF_RTF** a **CF_RETEXTOBJ** hodnoty.

## <a name="see-also"></a>Viz také

[Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

