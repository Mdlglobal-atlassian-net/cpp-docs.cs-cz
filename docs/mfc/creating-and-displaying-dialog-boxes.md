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
ms.openlocfilehash: e0b7ff31576b345ac2911e62a6e10469845eecba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175027"
---
# <a name="creating-and-displaying-dialog-boxes"></a>Vytváření a zobrazování dialogových oken

Vytvoření objektu dialogového okna je dvoufázové operace. Nejprve vytvořte objekt dialogové okno a potom vytvořte dialogového okna. Modální a nemodální dialogová okna se liší trochu v procesu použité k vytvoření a jejich zobrazení. V následující tabulce jsou uvedeny jak modální a nemodální dialogové okno pole jsou obvykle vytvořen a zobrazí.

### <a name="dialog-creation"></a>Vytvoření dialogového okna

|Typ dialogové okno|Jak ji vytvořit|
|-----------------|----------------------|
|[Nemodální](../mfc/creating-modeless-dialog-boxes.md)|Vytvořit `CDialog`, zavolejte `Create` členskou funkci.|
|[Modal](../mfc/creating-modal-dialog-boxes.md)|Vytvořit `CDialog`, zavolejte `DoModal` členskou funkci.|

Pokud chcete, vytvoříte vašem dialogovém okně ze [šablony dialogového okna v paměti](../mfc/using-a-dialog-template-in-memory.md) , který je vytvořen, nikoli z prostředku šablony dialogového okna. Toto je rozšířená, ale.

## <a name="see-also"></a>Viz také:

[Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)
