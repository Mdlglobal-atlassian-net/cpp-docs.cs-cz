---
title: "Vytváření Nemodálních dialogových oken | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
ms.assetid: 70d78c7f-3d40-477b-9f78-0f33c359f88b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0549f898a076b140e7b5bed23c1c1e8c60d6adba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="creating-modeless-dialog-boxes"></a>Vytváření nemodálních dialogových oken
Pro pole dialogového okna bez režimu je nutné zadat vlastní veřejný konstruktor ve vlastní třídy dialogového okna. Vytvoření nemodálního dialogové okno, volání veřejný konstruktor a pak zavolají objektu dialogového okna [vytvořit](../mfc/reference/cdialog-class.md#create) – členská funkce načíst prostředku dialogového okna. Můžete volat **vytvořit** během nebo po volání konstruktoru. Pokud má vlastnost prostředku dialogového okna **ws_visible –**, okamžitě se zobrazí dialogové okno. Pokud ne, musí volat jeho [ShowWindow](../mfc/reference/cwnd-class.md#showwindow) – členská funkce.  
  
## <a name="see-also"></a>Viz také  
 [Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)

