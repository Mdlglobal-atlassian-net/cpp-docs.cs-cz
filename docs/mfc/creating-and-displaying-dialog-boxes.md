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
ms.openlocfilehash: 6d23e4d2c9249ce248eb8092963036f2ba5cacac
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685737"
---
# <a name="creating-and-displaying-dialog-boxes"></a>Vytváření a zobrazování dialogových oken

Vytvoření objektu dialogového okna je dvoufázové operace. Nejprve Sestavte objekt dialogového okna a pak vytvořte dialogové okno. Modální a nemodální dialogová okna se trochu liší v procesu použitém k jejich vytvoření a zobrazení. Následující tabulka uvádí, jak jsou modální a nemodální dialogová okna normálně vytvořená a zobrazená.

### <a name="dialog-creation"></a>Vytvoření dialogového okna

|Typ dialogového okna|Jak ho vytvořit|
|-----------------|----------------------|
|[Modální](../mfc/creating-modeless-dialog-boxes.md)|Konstrukce `CDialog` a volání členské funkce `Create`.|
|[Převodu](../mfc/creating-modal-dialog-boxes.md)|Konstrukce `CDialog` a volání členské funkce `DoModal`.|

V případě potřeby můžete vytvořit dialogové okno ze [šablony dialogového okna v paměti](../mfc/using-a-dialog-template-in-memory.md) , kterou jste vytvořili, nikoli z prostředku šablony dialogového okna. Toto je pokročilé téma, ale.

## <a name="see-also"></a>Další informace najdete v tématech

[Práce s dialogovými okny v MFC](../mfc/life-cycle-of-a-dialog-box.md)
