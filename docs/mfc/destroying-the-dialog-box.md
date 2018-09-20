---
title: Zničení dialogových oken | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [MFC], deleting
- destruction, dialog box
- dialog boxes [MFC], destroying
- dialog boxes [MFC], removing
- modeless dialog boxes [MFC], destroying
- MFC dialog boxes [MFC], destroying
- modal dialog boxes [MFC], destroying
ms.assetid: dabceee7-3639-4d85-bf34-73515441b3d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 863b70f3bf4e9828d69024b838dce43abbba26be
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425909"
---
# <a name="destroying-the-dialog-box"></a>Zničení dialogových oken

Modální dialogová okna jsou obvykle vytvořené v rámci zásobníku a zničeny při ukončení funkce, které byly vytvořeny. Destruktor objektu dialogového okna se volá, když objekt dostane mimo rozsah.

Nemodální dialogová okna jsou obvykle vytvořených a vlastněných platformou nadřazeného zobrazení nebo rámec okna, okna hlavního rámce aplikace nebo okna rámce dokumentu. Výchozí hodnota [při zavření](../mfc/reference/cwnd-class.md#onclose) volání obsluhy [destroywindow –](../mfc/reference/cwnd-class.md#destroywindow), které ničí dialogového okna. Pokud dialogové okno samostatné, s žádné ukazatele nebo jiné sémantice speciální vlastnictví, by měly přepsat [postncdestroy –](../mfc/reference/cwnd-class.md#postncdestroy) ke zničení objektu jazyka C++ dialogového okna. Musí také přepsat [OnCancel](../mfc/reference/cdialog-class.md#oncancel) a volat `DestroyWindow` z ní. V opačném případě vlastník dialogového okna by měl zničit objekt jazyka C++, když už není nezbytné.

## <a name="see-also"></a>Viz také

[Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)

