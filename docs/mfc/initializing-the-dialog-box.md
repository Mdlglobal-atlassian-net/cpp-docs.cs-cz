---
title: Inicializace dialogových oken
ms.date: 11/04/2016
helpviewer_keywords:
- initializing dialog boxes [MFC]
- OnInitDialog method [MFC]
- modal dialog boxes [MFC], initializing
- modeless dialog boxes [MFC], initializing
- MFC dialog boxes [MFC], initializing
ms.assetid: 968142f5-19f9-4b34-a1d4-8e6412d4379b
ms.openlocfilehash: 87b3405f1441e730cf5c9ce7fc03d2c7372e55db
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289530"
---
# <a name="initializing-the-dialog-box"></a>Inicializace dialogových oken

Po dialogového okna se vytvoří pole a všech ovládacích prvků, ale těsně před dialogové okno pole (jednoho z těchto typů) se zobrazí na obrazovce objektu dialogového okna pro [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) členská funkce je volána. Pro modální dialogové okno, k tomu dochází během `DoModal` volání. Pro nemodální dialogové okno `OnInitDialog` je volána, když `Create` je volána. Obvykle přepsat `OnInitDialog` inicializovat ovládací prvky dialogových oken, jako je nastavení počáteční text do textového pole. Je třeba zavolat `OnInitDialog` členskou funkci základní třídy `CDialog`, z vaší `OnInitDialog` přepsat.

Pokud chcete nastavit barvu pozadí pole dialogového okna (a že všechna další dialogová okna ve vaší aplikaci), přečtěte si téma [nastavení barvy pozadí v dialogovém okně](../mfc/setting-the-dialog-boxs-background-color.md).

## <a name="see-also"></a>Viz také:

[Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)
