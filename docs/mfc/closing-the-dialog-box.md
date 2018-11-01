---
title: Zavření dialogového okna
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
ms.openlocfilehash: fe57c5603f1b0e9ea0b6fb9e6ea8d80bec961f6e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448110"
---
# <a name="closing-the-dialog-box"></a>Zavření dialogového okna

Modální dialogové okno se zavře, když uživatel vybere jeden z jeho tlačítka, obvykle na tlačítko OK nebo na tlačítko Storno. Kliknutím na tlačítko OK nebo zrušit způsobí, že Windows k odesílání objektu dialogového okna **BN_CLICKED** zprávy oznámení ovládacího prvku pomocí tlačítka je buď ID, **IDOK** nebo **IDCANCEL**. `CDialog` poskytuje výchozí funkce obslužné rutiny pro tyto zprávy: `OnOK` a `OnCancel`. Výchozí volání obslužné rutiny `EndDialog` členskou funkci, zavřete dialogové okno. Můžete také volat `EndDialog` z vlastního kódu. Další informace najdete v tématu [EndDialog](../mfc/reference/cdialog-class.md#enddialog) členské funkce třídy `CDialog` v *odkaz knihovny MFC*.

Pokud chcete uspořádat pro zavření a odstranění nemodální dialogové okno, přepište `PostNcDestroy` a vyvolat **odstranit** operátoru u **to** ukazatele. [Zničení dialogových oken](../mfc/destroying-the-dialog-box.md) vysvětluje, co bude dál.

## <a name="see-also"></a>Viz také

[Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)

