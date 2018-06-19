---
title: Zničení dialogových oken | Microsoft Docs
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
ms.openlocfilehash: 66a3ef9a72107ffb36a75834a6e197aba394c420
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343921"
---
# <a name="destroying-the-dialog-box"></a>Zničení dialogových oken
Modální dialogová okna jsou obvykle vytvoří na rámec zásobníku a zničen při ukončení funkce, které byly vytvořeny. Destruktoru objektu dialogového okna je volána, když objekt ocitne mimo rozsah.  
  
 Nemodální dialogová okna jsou obvykle vytvořeny a vlastníkem nadřazeného zobrazení nebo rámce okna – okno hlavního rámce aplikace nebo okně s rámečkem dokumentu. Výchozí hodnota [při zavření](../mfc/reference/cwnd-class.md#onclose) volání obslužné rutiny [destroywindow –](../mfc/reference/cwnd-class.md#destroywindow), který zničí dialogového okna. Pokud dialogové okno znamená samostatně, s žádné ukazatele na jeho nebo jiné speciální vlastnictví sémantiku, by měly přepsat [postncdestroy –](../mfc/reference/cwnd-class.md#postncdestroy) odstranění objektu C++ dialogového okna. Měli byste také přepsat [oncancel –](../mfc/reference/cdialog-class.md#oncancel) a volání `DestroyWindow` z v něm. Pokud ne, vlastník dialogového okna měli zničit objekt C++, když už není nutné.  
  
## <a name="see-also"></a>Viz také  
 [Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)

