---
title: Aktuální výběr v ovládacích prvcích pro úpravy s formátováním
ms.date: 11/04/2016
helpviewer_keywords:
- current selection in CRichEditCtrls
- CRichEditCtrl class [MFC], current selection in
- rich edit controls [MFC], current selection in
- selection, current in CRichEditCtrl
ms.assetid: f6b2a2b6-5481-4ad3-9720-6dd772ea6fc8
ms.openlocfilehash: e493f46e2a2b5bec695177e8c8da9c09de13376d
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916451"
---
# <a name="current-selection-in-a-rich-edit-control"></a>Aktuální výběr v ovládacích prvcích pro úpravy s formátováním

Uživatel může vybrat text v ovládacím prvku Rich Edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) pomocí myši nebo klávesnice. Aktuální výběr je rozsah vybraných znaků nebo pozice kurzoru, pokud nejsou vybrány žádné znaky. Aplikace může získat informace o aktuálním výběru, nastavit aktuální výběr, určit, kdy se má změnit aktuální výběr, a zobrazit nebo skrýt zvýraznění výběru.

Chcete-li určit aktuální výběr v ovládacím prvku pro úpravy s formátováním, použijte členskou funkci [GetSel](../mfc/reference/cricheditctrl-class.md#getsel) . Chcete-li nastavit aktuální výběr, použijte členskou funkci [SetSel](../mfc/reference/cricheditctrl-class.md#setsel) . Struktura [CHARRANGE](/windows/desktop/api/richedit/ns-richedit-charrange) se používá s těmito funkcemi k určení rozsahu znaků. Chcete-li načíst informace o obsahu aktuálního výběru, můžete použít členskou funkci [GetSelectionType](../mfc/reference/cricheditctrl-class.md#getselectiontype) .

Ve výchozím nastavení ovládací prvek s bohatou úpravou zobrazuje a skrývá zvýraznění výběru, když to získá a ztratí fokus. Zvýrazňování výběru můžete kdykoli zobrazit nebo skrýt pomocí členské funkce [HideSelection](../mfc/reference/cricheditctrl-class.md#hideselection) . Například aplikace může poskytnout dialogové okno hledání k nalezení textu v ovládacím prvku pro úpravy s formátováním. Aplikace může vybrat shodný text bez zavření dialogového okna. v takovém případě musí použít `HideSelection` k zvýraznění výběru.

Chcete-li získat vybraný text v ovládacím prvku pro úpravy s formátováním, použijte členskou funkci [GetSelText](../mfc/reference/cricheditctrl-class.md#getseltext) . Text je zkopírován do zadaného pole znaků. Je nutné zajistit, aby bylo pole dostatečně velké pro uložení vybraného textu a ukončovacího znaku null.

Můžete vyhledat řetězec v ovládacím prvku Rich Edit pomocí členské funkce [hledán FindText](../mfc/reference/cricheditctrl-class.md#findtext) , kterou struktura [FINDTEXTEX](/windows/desktop/api/richedit/ns-richedit-findtextexa) použitá s touto funkcí určuje rozsah textu, který se má hledat, a řetězec, který chcete vyhledat. Můžete také zadat takové možnosti, jako by hledání rozlišuje velká a malá písmena.

## <a name="see-also"></a>Viz také:

[Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
