---
title: Používání atributu CHotKeyCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- keys, hot and CHotKeyCtrl
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: 9b207117-d848-4224-8888-c3d197bb0c95
ms.openlocfilehash: e2002d96a1eba913e260fa92281f730355a83ca5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447239"
---
# <a name="using-chotkeyctrl"></a>Používání atributu CHotKeyCtrl

Klávesová zkratka, reprezentovaná třídou [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md), je okno, které zobrazuje textovou reprezentaci klíče, do které uživatel patří, jako je například kombinace kláves CTRL + SHIFT + Q. Udržuje také interní reprezentace tohoto klíče ve formě kódu virtuálního klíče a sady příznaků, které reprezentují stav posunu. Klávesová zkratka v současnosti nenastavuje klávesovou zkratku, která je v programu. (Seznam kódů standardních virtuálních klíčů najdete v tématu Winuser. h.)

Použijte ovládací prvek klávesová zkratka pro získání vstupu uživatele, pro který je klávesová zkratka spojena s oknem nebo vláknem. Klávesové zkratky jsou často používány v dialogových oknech, jako je například zobrazení při dotazování uživatele na přiřazení klávesových zkratek. Je zodpovědností programu načítat hodnoty popisující klávesovou zkratku z ovládacího prvku klávesová zkratka a volat příslušné funkce pro přidružení klávesy Hot k oknu nebo vláknu.

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace

- [Použití ovládacího prvku klávesová zkratka](../mfc/using-a-hot-key-control.md)

- [Nastavení klávesové zkratky](../mfc/setting-a-hot-key.md)

- [Globální klávesové zkratky](../mfc/global-hot-keys.md)

- [Klávesové zkratky specifické pro vlákno](../mfc/thread-specific-hot-keys.md)

## <a name="see-also"></a>Viz také

[Ovládací prvky](../mfc/controls-mfc.md)
