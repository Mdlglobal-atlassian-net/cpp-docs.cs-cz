---
title: Tisk v ovládacích prvcích pro úpravy s formátováním
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC], CRichEditCtrl
- rich edit controls [MFC], printing
- CRichEditCtrl class [MFC], printing
ms.assetid: dbda0e40-018f-424e-b5d8-7b489aaf27af
ms.openlocfilehash: 671aec27584af975ce1635793ae80879e7208d4b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508000"
---
# <a name="printing-in-rich-edit-controls"></a>Tisk v ovládacích prvcích pro úpravy s formátováním

Můžete říct ovládacímu prvku Rich Edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)), který vykreslí jeho výstup pro konkrétní zařízení, jako je například tiskárna. Můžete také zadat výstupní zařízení, pro které ovládací prvek s formátováním RTF formátuje text.

Chcete-li formátovat část obsahu ovládacího prvku pro úpravy s formátováním pro konkrétní zařízení, můžete použít členskou funkci [FormatRange](../mfc/reference/cricheditctrl-class.md#formatrange) . Struktura [FormatRange](/windows/win32/api/richedit/ns-richedit-formatrange) použitá s touto funkcí určuje rozsah textu, který se má formátovat, i kontext zařízení (DC) pro cílové zařízení.

Po formátování textu pro výstupní zařízení můžete odeslat výstup do zařízení pomocí členské funkce [DisplayBand](../mfc/reference/cricheditctrl-class.md#displayband) . Opakovaným použitím `FormatRange` a `DisplayBand`, aplikace, která tiskne obsah ovládacího prvku pro úpravy s formátováním, může implementovat řazení do pásem. (Pro účely tisku je dělení výstupu rozdělené na menší části.)

Členskou funkci [SetTargetDevice](../mfc/reference/cricheditctrl-class.md#settargetdevice) můžete použít k určení cílového zařízení, pro které ovládací prvek s bohatým úpravou formátuje svůj text. Tato funkce je užitečná pro zobrazení WYSIWYG (co vidíte), ve kterém aplikace místo obrazovky umisťuje text pomocí výchozí metriky písma tiskárny.

## <a name="see-also"></a>Viz také:

[Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
