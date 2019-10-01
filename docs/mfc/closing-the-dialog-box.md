---
title: Zavření dialogového okna
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
ms.openlocfilehash: 48ea954552b3ea9aa7193a47fc2a66d731312d77
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685382"
---
# <a name="closing-the-dialog-box"></a>Zavření dialogového okna

Modální dialogové okno se zavře, když uživatel zvolí jedno z jeho tlačítek, obvykle tlačítko OK nebo tlačítko Storno. Po klepnutí na tlačítko OK nebo Storno dojde v systému Windows k odeslání zprávy ovládacího prvku **BN_CLICKED** pomocí ID tlačítka, buď **IDOK** nebo **IDCANCEL**. `CDialog` poskytuje pro tyto zprávy výchozí funkce obslužných rutin: `OnOK` a `OnCancel`. Výchozí obslužné rutiny volají členskou funkci `EndDialog` pro zavření dialogového okna. Můžete také volat `EndDialog` z vlastního kódu. Další informace naleznete v tématu [EndDialog](../mfc/reference/cdialog-class.md#enddialog) členské funkce třídy `CDialog` v *odkazu knihovny MFC*.

Chcete-li uspořádat pro zavření a odstranění nemodálního dialogového okna, přepište `PostNcDestroy` a volejte operátor **Delete** na **tomto** ukazateli. [Po zničení dialogového okna se](../mfc/destroying-the-dialog-box.md) dozvíte, co se stane dál.

## <a name="see-also"></a>Další informace najdete v tématech

[Práce s dialogovými okny v MFC](../mfc/life-cycle-of-a-dialog-box.md)
