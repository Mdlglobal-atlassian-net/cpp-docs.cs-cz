---
title: Používání atributu CHotKeyCtrl
ms.date: 11/04/2016
f1_keywords:
- CHotKeyCtrl
helpviewer_keywords:
- keys, hot and CHotKeyCtrl
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: 9b207117-d848-4224-8888-c3d197bb0c95
ms.openlocfilehash: f52d676f68718cdd4d16cf93bf0d7e3fd6b03822
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349851"
---
# <a name="using-chotkeyctrl"></a>Používání atributu CHotKeyCtrl

Horké ovládacího prvku, reprezentovaný třídou [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md), je okno, které zobrazuje textová reprezentace kombinace kláves uživatel zadá do ní, jako je například CTRL + SHIFT + Q. Také udržuje vnitřní reprezentaci tohoto klíče ve formuláři virtuální klíče kódu a sada příznaků, které představují posun stavu. Výměně klíčů ovládacího prvku není nastavený ve skutečnosti klávesové zkratky – způsobem, který se do programu. (Seznam kódů standardní virtuální klíče najdete v tématu winuser.)

Použití ovládacího prvku horké k získání vstupu uživatele, pro které klávesové zkratky pro přidružení k okno nebo vlákna. Ovládací prvky klávesových zkratek se často používají v dialogových oknech, jako například může zobrazit, když uživatel přiřadit klávesovou zkratku. Je zodpovědností váš program načíst hodnoty popisující klávesovou zkratku z ovládacího prvku výměně klíčů a volat odpovídající funkce přidružení klávesovou zkratku k window, nebo vlákna.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Použití ovládacího prvku klávesová zkratka](../mfc/using-a-hot-key-control.md)

- [Nastavení klávesové zkratky](../mfc/setting-a-hot-key.md)

- [Globální klávesové zkratky](../mfc/global-hot-keys.md)

- [Klávesové zkratky specifické pro vlákno](../mfc/thread-specific-hot-keys.md)

## <a name="see-also"></a>Viz také:

[Ovládací prvky](../mfc/controls-mfc.md)
