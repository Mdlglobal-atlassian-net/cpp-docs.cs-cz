---
title: "Vytváření a zobrazování dialogových oken | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- opening dialog boxes
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], displaying
ms.assetid: 1c5219ee-8b46-44bc-9708-83705d4f248b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 109c4f2e8272293ccfcb58924380c586f8078536
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="creating-and-displaying-dialog-boxes"></a>Vytváření a zobrazování dialogových oken
Vytvoření objektu dialogového okna je dvoufázovou operaci. Nejprve vytvořit objektu dialogového okna a potom vytvořit dialogového okna. Modální a nemodální dialogová okna liší poněkud v procesu slouží k vytvoření a jejich zobrazení. Následující tabulka uvádí, jak modální a nemodální dialogové okno pole jsou obvykle sestavený a zobrazí.  
  
### <a name="dialog-creation"></a>Dialogové okno Vytvoření  
  
|Dialogové okno typu|Jak k jeho vytvoření|  
|-----------------|----------------------|  
|[Nemodální](../mfc/creating-modeless-dialog-boxes.md)|Vytvořit `CDialog`, pak zavolají **vytvořit** – členská funkce.|  
|[Modální](../mfc/creating-modal-dialog-boxes.md)|Vytvořit `CDialog`, pak zavolají `DoModal` – členská funkce.|  
  
 Pokud chcete, vytvořením vašem dialogovém okně z [šablony dialogového okna v paměti](../mfc/using-a-dialog-template-in-memory.md) , kterou jste vytvořili spíše než z prostředku šablony dialogové okno. To je rozšířená, ale.  
  
## <a name="see-also"></a>Viz také  
 [Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)
