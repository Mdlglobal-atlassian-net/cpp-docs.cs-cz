---
title: Zavření dialogového okna
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
ms.openlocfilehash: 07e4159eccde1fab89d4a5ffadee4e6d11fc20f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326843"
---
# <a name="closing-the-dialog-box"></a>Zavření dialogového okna

Modální dialogové okno se zavře, když uživatel vybere jeden z jeho tlačítka, obvykle na tlačítko OK nebo na tlačítko Storno. Kliknutím na tlačítko OK nebo zrušit způsobí, že Windows k odesílání objektu dialogového okna **BN_CLICKED** zprávy oznámení ovládacího prvku pomocí tlačítka je buď ID, **IDOK** nebo **IDCANCEL**. `CDialog` poskytuje výchozí funkce obslužné rutiny pro tyto zprávy: `OnOK` a `OnCancel`. Výchozí volání obslužné rutiny `EndDialog` členskou funkci, zavřete dialogové okno. Můžete také volat `EndDialog` z vlastního kódu. Další informace najdete v tématu [EndDialog](../mfc/reference/cdialog-class.md#enddialog) členské funkce třídy `CDialog` v *odkaz knihovny MFC*.

Pokud chcete uspořádat pro zavření a odstranění nemodální dialogové okno, přepište `PostNcDestroy` a vyvolat **odstranit** operátoru u **to** ukazatele. [Zničení dialogových oken](../mfc/destroying-the-dialog-box.md) vysvětluje, co bude dál.

## <a name="see-also"></a>Viz také:

[Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)
