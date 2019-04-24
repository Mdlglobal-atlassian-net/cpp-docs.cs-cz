---
title: Zničení dialogových oken
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], deleting
- destruction, dialog box
- dialog boxes [MFC], destroying
- dialog boxes [MFC], removing
- modeless dialog boxes [MFC], destroying
- MFC dialog boxes [MFC], destroying
- modal dialog boxes [MFC], destroying
ms.assetid: dabceee7-3639-4d85-bf34-73515441b3d0
ms.openlocfilehash: 84ae5b336bb8eeac4f8ab7b6e5b9f00246f9ca15
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62254303"
---
# <a name="destroying-the-dialog-box"></a>Zničení dialogových oken

Modální dialogová okna jsou obvykle vytvořené v rámci zásobníku a zničeny při ukončení funkce, které byly vytvořeny. Destruktor objektu dialogového okna se volá, když objekt dostane mimo rozsah.

Nemodální dialogová okna jsou obvykle vytvořených a vlastněných platformou nadřazeného zobrazení nebo rámec okna, okna hlavního rámce aplikace nebo okna rámce dokumentu. Výchozí hodnota [při zavření](../mfc/reference/cwnd-class.md#onclose) volání obsluhy [destroywindow –](../mfc/reference/cwnd-class.md#destroywindow), které ničí dialogového okna. Pokud dialogové okno samostatné, s žádné ukazatele nebo jiné sémantice speciální vlastnictví, by měly přepsat [postncdestroy –](../mfc/reference/cwnd-class.md#postncdestroy) ke zničení objektu jazyka C++ dialogového okna. Musí také přepsat [OnCancel](../mfc/reference/cdialog-class.md#oncancel) a volat `DestroyWindow` z ní. V opačném případě vlastník dialogového okna by měl zničit objekt jazyka C++, když už není nezbytné.

## <a name="see-also"></a>Viz také:

[Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)
