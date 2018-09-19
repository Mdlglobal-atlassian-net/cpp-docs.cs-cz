---
title: Formátování znaků v ovládacích prvcích pro úpravy s formátováním | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- formatting [MFC], characters
- rich edit controls [MFC], character formatting in
- CRichEditCtrl class [MFC], character formatting in
ms.assetid: c80f4305-75ad-45f9-8d17-d83d0fe79be5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75ac8637e5157434cd5729695b30a443bbd31cf5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403149"
---
# <a name="character-formatting-in-rich-edit-controls"></a>Formátování znaků v ovládacích prvcích pro úpravy s formátováním

Můžete členské funkce ovládacího prvku RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) k formátování znaků a načte informace o formátování. Pro znaky můžete zadat písmo, velikost, barvu a efekty, jako je například tučné, kurzíva a chráněné.

Můžete použít formátování s použitím [SetSelectionCharFormat](../mfc/reference/cricheditctrl-class.md#setselectioncharformat) a [SetWordCharFormat](../mfc/reference/cricheditctrl-class.md#setwordcharformat) členské funkce. Chcete-li zjistit aktuální formátování vybraného textu, použijte [GetSelectionCharFormat](../mfc/reference/cricheditctrl-class.md#getselectioncharformat) členskou funkci. [CHARFORMAT](/windows/desktop/api/richedit/ns-richedit-_charformat) struktura s tyto členské funkce slouží k určení znaku atributy. Mezi důležité členy **CHARFORMAT** je **dwMask**. V `SetSelectionCharFormat` a `SetWordCharFormat`, **dwMask** Určuje atributy, které znak se nastaví ve volání funkce. `GetSelectionCharFormat` sestavy atributy prvního znaku ve výběru; **dwMask** Určuje atributy, které jsou konzistentní v rámci výběr.

Můžete také získat a nastavit "výchozí formátování," tedy formátování použité pro všechny následně vložené znaky. Například pokud aplikace nastaví výchozí formátování mají být zobrazena tučně a uživatel potom zadá znak, tento znak je tučně. K získání a nastavení výchozí formátování znaků, použijte [GetDefaultCharFormat](../mfc/reference/cricheditctrl-class.md#getdefaultcharformat) a [SetDefaultCharFormat](../mfc/reference/cricheditctrl-class.md#setdefaultcharformat) členské funkce.

Atribut "chráněné" znak nedojde ke změně vzhledu textu. Pokud uživatel se pokusí upravit chráněný text, odešle ovládacího prvku nadřazenému oknu **EN_PROTECTED** zpráva s oznámením, což nadřazené okno Povolit nebo zakázat změny. Pokud chcete dostávat tato oznámení, musíte povolit ho pomocí [seteventmask –](../mfc/reference/cricheditctrl-class.md#seteventmask) členskou funkci. Další informace o masky události najdete v tématu [oznámení z ovládacího prvku Rich upravit](../mfc/notifications-from-a-rich-edit-control.md)dále v tomto tématu.

Barva popředí je znak atributu, ale je barva pozadí vlastnost ovládacího prvku RichEdit. Chcete-li nastavit barvu pozadí, použijte [SetBackgroundColor](../mfc/reference/cricheditctrl-class.md#setbackgroundcolor) členskou funkci.

## <a name="see-also"></a>Viz také

[Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

