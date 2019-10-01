---
title: Zničení dialogového okna
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
ms.openlocfilehash: 8b407c6e832dde7a5865146e7cc12d1840d3234a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685859"
---
# <a name="destroying-the-dialog-box"></a>Zničení dialogového okna

Modální dialogová okna jsou obvykle vytvořena v bloku zásobníku a zničena v případě, že funkce, která je vytvořila, končí. Destruktor objektu dialogového okna se volá, když se objekt dostane mimo rozsah.

Nemodální dialogová okna se obvykle vytváří a vlastní v rámci nadřazeného zobrazení nebo okna rámce – hlavní okno rámce aplikace nebo okno rámce dokumentu. Výchozí obslužná rutina pro [ukončení](../mfc/reference/cwnd-class.md#onclose) volá [DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow), což zničí okno dialogového okna. Pokud se dialogové okno nachází samostatně, bez ukazatelů na něj nebo jiné sémantiky zvláštního vlastnictví, byste měli přepsat [PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy) pro zničení objektu C++ dialogového okna. Měli byste také přepsat příkaz pro [zrušení](../mfc/reference/cdialog-class.md#oncancel) a volání `DestroyWindow` v rámci něj. V takovém případě by vlastník dialogového okna měl zničit C++ objekt, když již není nutný.

## <a name="see-also"></a>Další informace najdete v tématech

[Práce s dialogovými okny v MFC](../mfc/life-cycle-of-a-dialog-box.md)
