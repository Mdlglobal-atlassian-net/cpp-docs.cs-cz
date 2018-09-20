---
title: Zavření dialogového okna | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e9ad4b8af63b68912c232767bf1fd14070fda261
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409048"
---
# <a name="closing-the-dialog-box"></a>Zavření dialogového okna

Modální dialogové okno se zavře, když uživatel vybere jeden z jeho tlačítka, obvykle na tlačítko OK nebo na tlačítko Storno. Kliknutím na tlačítko OK nebo zrušit způsobí, že Windows k odesílání objektu dialogového okna **BN_CLICKED** zprávy oznámení ovládacího prvku pomocí tlačítka je buď ID, **IDOK** nebo **IDCANCEL**. `CDialog` poskytuje výchozí funkce obslužné rutiny pro tyto zprávy: `OnOK` a `OnCancel`. Výchozí volání obslužné rutiny `EndDialog` členskou funkci, zavřete dialogové okno. Můžete také volat `EndDialog` z vlastního kódu. Další informace najdete v tématu [EndDialog](../mfc/reference/cdialog-class.md#enddialog) členské funkce třídy `CDialog` v *odkaz knihovny MFC*.

Pokud chcete uspořádat pro zavření a odstranění nemodální dialogové okno, přepište `PostNcDestroy` a vyvolat **odstranit** operátoru u **to** ukazatele. [Zničení dialogových oken](../mfc/destroying-the-dialog-box.md) vysvětluje, co bude dál.

## <a name="see-also"></a>Viz také

[Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)

