---
title: Tisk v ovládacích prvcích pro úpravy s formátováním
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC], CRichEditCtrl
- rich edit controls [MFC], printing
- CRichEditCtrl class [MFC], printing
ms.assetid: dbda0e40-018f-424e-b5d8-7b489aaf27af
ms.openlocfilehash: 6ae7212eaa8eed1088a507973c80311f169c7751
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916270"
---
# <a name="printing-in-rich-edit-controls"></a>Tisk v ovládacích prvcích pro úpravy s formátováním

Můžete říct ovládacímu prvku Rich Edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)), který vykreslí jeho výstup pro konkrétní zařízení, jako je například tiskárna. Můžete také zadat výstupní zařízení, pro které ovládací prvek s formátováním RTF formátuje text.

Chcete-li formátovat část obsahu ovládacího prvku pro úpravy s formátováním pro konkrétní zařízení, můžete použít členskou funkci [FormatRange](../mfc/reference/cricheditctrl-class.md#formatrange) . Struktura [FormatRange](/windows/desktop/api/richedit/ns-richedit-formatrange) použitá s touto funkcí určuje rozsah textu, který se má formátovat, i kontext zařízení (DC) pro cílové zařízení.

Po formátování textu pro výstupní zařízení můžete odeslat výstup do zařízení pomocí členské funkce [DisplayBand](../mfc/reference/cricheditctrl-class.md#displayband) . Opakovaným použitím `FormatRange` a `DisplayBand`, aplikace, která tiskne obsah ovládacího prvku pro úpravy s formátováním, může implementovat řazení do pásem. (Pro účely tisku je dělení výstupu rozdělené na menší části.)

Členskou funkci [SetTargetDevice](../mfc/reference/cricheditctrl-class.md#settargetdevice) můžete použít k určení cílového zařízení, pro které ovládací prvek s bohatým úpravou formátuje svůj text. Tato funkce je užitečná pro zobrazení WYSIWYG (co vidíte), ve kterém aplikace místo obrazovky umisťuje text pomocí výchozí metriky písma tiskárny.

## <a name="see-also"></a>Viz také:

[Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
