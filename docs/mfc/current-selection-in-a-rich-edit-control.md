---
title: Aktuální výběr v ovládacím prvku pro úpravy s formátováním | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- current selection in CRichEditCtrls
- CRichEditCtrl class [MFC], current selection in
- rich edit controls [MFC], current selection in
- selection, current in CRichEditCtrl
ms.assetid: f6b2a2b6-5481-4ad3-9720-6dd772ea6fc8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c5870c7c3352a53d85bdd15020a1e7f535ef6efc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403666"
---
# <a name="current-selection-in-a-rich-edit-control"></a>Aktuální výběr v ovládacích prvcích pro úpravy s formátováním

Uživatel může vybrat text v ovládacím prvku RTF ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) pomocí myši nebo klávesnice. Aktuální výběr je rozsah vybrané znaky nebo jsou vybrány pozice kurzoru, pokud žádné znaky. Aplikace můžete získat informace o aktuální výběr, nastavit aktuální výběr, určují, kdy zvýrazněte aktuálního výběru změny a zobrazit nebo skrýt výběr.

Chcete-li zjistit aktuální výběr v ovládacím prvku RichEdit, použijte [GetSel](../mfc/reference/cricheditctrl-class.md#getsel) členskou funkci. Chcete-li nastavit aktuální výběr, použijte [SetSel](../mfc/reference/cricheditctrl-class.md#setsel) členskou funkci. [CHARRANGE](/windows/desktop/api/richedit/ns-richedit-_charrange) struktura se tyto funkce slouží k určení rozsahu znaků. Pokud chcete načíst informace o obsahu aktuálně vybraný, můžete použít [GetSelectionType](../mfc/reference/cricheditctrl-class.md#getselectiontype) členskou funkci.

Ve výchozím nastavení ovládacího prvku zobrazí a skryje zvýraznění výběr při získává a ztratí fokus. Můžete zobrazit nebo skrýt zvýraznění výběr kdykoli pomocí [HideSelection](../mfc/reference/cricheditctrl-class.md#hideselection) členskou funkci. Aplikace může například poskytovat dialogové okno hledání, hledání v textu v ovládacím prvku RichEdit. Aplikace může vybrat odpovídající text bez zavření dialogového okna, v takovém případě musíte použít `HideSelection` zvýrazněte výběr.

Chcete-li získat vybraný text v ovládacím prvku RichEdit, použijte [GetSelText](../mfc/reference/cricheditctrl-class.md#getseltext) členskou funkci. Text, je zkopírován do zadané pole znaků. Ujistěte se, že pole je příliš velká pro uložení vybraného textu a ukončujícího znaku null.

Můžete hledat pomocí řetězce v ovládacím prvku RichEdit [FindText](../mfc/reference/cricheditctrl-class.md#findtext) členskou funkci [FINDTEXTEX](/windows/desktop/api/richedit/ns-richedit-_findtextexa) struktury použité s touto funkcí určuje rozsah textu vyhledávání a hledaný řetězec. Tyto možnosti můžete zadat také určuje, zda je hledání malá a velká písmena.

## <a name="see-also"></a>Viz také

[Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

