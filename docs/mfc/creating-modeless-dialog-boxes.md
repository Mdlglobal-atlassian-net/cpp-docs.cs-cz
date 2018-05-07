---
title: Vytváření Nemodálních dialogových oken | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
ms.assetid: 70d78c7f-3d40-477b-9f78-0f33c359f88b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2055312c7418b14c9b274649db8faa297554257e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="creating-modeless-dialog-boxes"></a>Vytváření nemodálních dialogových oken
Pro pole dialogového okna bez režimu je nutné zadat vlastní veřejný konstruktor ve vlastní třídy dialogového okna. Vytvoření nemodálního dialogové okno, volání veřejný konstruktor a pak zavolají objektu dialogového okna [vytvořit](../mfc/reference/cdialog-class.md#create) – členská funkce načíst prostředku dialogového okna. Můžete volat **vytvořit** během nebo po volání konstruktoru. Pokud má vlastnost prostředku dialogového okna **ws_visible –**, okamžitě se zobrazí dialogové okno. Pokud ne, musí volat jeho [ShowWindow](../mfc/reference/cwnd-class.md#showwindow) – členská funkce.  
  
## <a name="see-also"></a>Viz také  
 [Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)

