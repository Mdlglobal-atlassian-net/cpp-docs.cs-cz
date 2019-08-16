---
title: Formátování znaků v ovládacích prvcích pro úpravy s formátováním
ms.date: 11/04/2016
helpviewer_keywords:
- formatting [MFC], characters
- rich edit controls [MFC], character formatting in
- CRichEditCtrl class [MFC], character formatting in
ms.assetid: c80f4305-75ad-45f9-8d17-d83d0fe79be5
ms.openlocfilehash: 4ac996c1cb018a29137e37d9603016dc1c151c58
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508974"
---
# <a name="character-formatting-in-rich-edit-controls"></a>Formátování znaků v ovládacích prvcích pro úpravy s formátováním

Můžete použít členské funkce ovládacího prvku Rich Edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) k formátování znaků a načtení informací o formátování. U znaků můžete zadat řez, velikost, barvu a efekty, jako je tučné písmo, kurzíva a ochrana.

Můžete použít formátování znaků pomocí členských funkcí [SetSelectionCharFormat](../mfc/reference/cricheditctrl-class.md#setselectioncharformat) a [SetWordCharFormat](../mfc/reference/cricheditctrl-class.md#setwordcharformat) . Chcete-li zjistit aktuální formátování znaků pro vybraný text, použijte členskou funkci [GetSelectionCharFormat](../mfc/reference/cricheditctrl-class.md#getselectioncharformat) . Struktura [Charformat](/windows/win32/api/richedit/ns-richedit-_charformat) se používá s těmito členskými funkcemi k určení atributů znaků. Jedním z důležitých členů **Charformat** je **dwMask**. V `SetSelectionCharFormat` a `SetWordCharFormat` **dwMask** určuje, které atributy znaků budou nastaveny tímto voláním funkce. `GetSelectionCharFormat`oznamuje atributy prvního znaku ve výběru; **dwMask** určuje atributy, které jsou konzistentní v rámci výběru.

Můžete také získat a nastavit výchozí formátování znaků, což je formátování použité pro jakékoli následně vložené znaky. Například pokud aplikace nastaví výchozí formátování znaků na tučné a uživatel pak zadá znak, je tento znak tučný. Chcete-li získat a nastavit výchozí formátování znaků, použijte členské funkce [GetDefaultCharFormat](../mfc/reference/cricheditctrl-class.md#getdefaultcharformat) a [SetDefaultCharFormat](../mfc/reference/cricheditctrl-class.md#setdefaultcharformat) .

Atribut "protected" nemění vzhled textu. Pokud se uživatel pokusí upravit chráněný text, ovládací prvek RichEdit pošle svému nadřazenému oknu zprávu **EN_PROTECTED** s oznámením, které umožní nadřazenému oknu povolit nebo zakázat změnu. Chcete-li obdržet tuto zprávu oznámení, je nutné ji povolit pomocí členské funkce [SetEventMask](../mfc/reference/cricheditctrl-class.md#seteventmask) . Další informace o masce události najdete v části [oznámení v ovládacím prvku pro úpravy](../mfc/notifications-from-a-rich-edit-control.md)dále v tomto tématu.

Barva popředí je znakový atribut, ale barva pozadí je vlastnost ovládacího prvku Rich Edit. Chcete-li nastavit barvu pozadí, použijte členskou funkci [SetBackgroundColor](../mfc/reference/cricheditctrl-class.md#setbackgroundcolor) .

## <a name="see-also"></a>Viz také:

[Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
