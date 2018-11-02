---
title: Vytváření a zobrazování dialogových oken
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- opening dialog boxes
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], displaying
ms.assetid: 1c5219ee-8b46-44bc-9708-83705d4f248b
ms.openlocfilehash: 778ee0cbb154c65b0cc74a207a175354c2e2a90b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431080"
---
# <a name="creating-and-displaying-dialog-boxes"></a>Vytváření a zobrazování dialogových oken

Vytvoření objektu dialogového okna je dvoufázové operace. Nejprve vytvořte objekt dialogové okno a potom vytvořte dialogového okna. Modální a nemodální dialogová okna se liší trochu v procesu použité k vytvoření a jejich zobrazení. V následující tabulce jsou uvedeny jak modální a nemodální dialogové okno pole jsou obvykle vytvořen a zobrazí.

### <a name="dialog-creation"></a>Vytvoření dialogového okna

|Typ dialogové okno|Jak ji vytvořit|
|-----------------|----------------------|
|[Nemodální](../mfc/creating-modeless-dialog-boxes.md)|Vytvořit `CDialog`, zavolejte `Create` členskou funkci.|
|[Modální okno](../mfc/creating-modal-dialog-boxes.md)|Vytvořit `CDialog`, zavolejte `DoModal` členskou funkci.|

Pokud chcete, vytvoříte vašem dialogovém okně ze [šablony dialogového okna v paměti](../mfc/using-a-dialog-template-in-memory.md) , který je vytvořen, nikoli z prostředku šablony dialogového okna. Toto je rozšířená, ale.

## <a name="see-also"></a>Viz také

[Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)

