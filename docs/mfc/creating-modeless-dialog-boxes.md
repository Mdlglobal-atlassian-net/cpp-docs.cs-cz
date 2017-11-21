---
title: "Vytváření Nemodálních dialogových oken | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
ms.assetid: 70d78c7f-3d40-477b-9f78-0f33c359f88b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7c5a701f42b2707b957753c1f8a22640c7818d72
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="creating-modeless-dialog-boxes"></a>Vytváření nemodálních dialogových oken
Pro pole dialogového okna bez režimu je nutné zadat vlastní veřejný konstruktor ve vlastní třídy dialogového okna. Vytvoření nemodálního dialogové okno, volání veřejný konstruktor a pak zavolají objektu dialogového okna [vytvořit](../mfc/reference/cdialog-class.md#create) – členská funkce načíst prostředku dialogového okna. Můžete volat **vytvořit** během nebo po volání konstruktoru. Pokud má vlastnost prostředku dialogového okna **ws_visible –**, okamžitě se zobrazí dialogové okno. Pokud ne, musí volat jeho [ShowWindow](../mfc/reference/cwnd-class.md#showwindow) – členská funkce.  
  
## <a name="see-also"></a>Viz také  
 [Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)

