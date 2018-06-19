---
title: Vytváření a zobrazování dialogových oken | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- opening dialog boxes
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], displaying
ms.assetid: 1c5219ee-8b46-44bc-9708-83705d4f248b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0fcac345a572f8b33d76692d6852e2dc28698367
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342459"
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

