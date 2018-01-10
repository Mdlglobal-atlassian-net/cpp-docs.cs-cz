---
title: "Inicializace dialogových oken | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- initializing dialog boxes [MFC]
- OnInitDialog method [MFC]
- modal dialog boxes [MFC], initializing
- modeless dialog boxes [MFC], initializing
- MFC dialog boxes [MFC], initializing
ms.assetid: 968142f5-19f9-4b34-a1d4-8e6412d4379b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2af05011e8f2af2993edf3ea2f82716137b17857
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="initializing-the-dialog-box"></a>Inicializace dialogových oken
Po dialogové okno pole a všechny její ovládací prvky se vytvoří, ale těsně před dialogové okno pole (buď typu) se zobrazí na obrazovce objektu dialogového okna na [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) členské funkce je volána. Pro modální dialogové okno, k tomu dojde během `DoModal` volání. Nemodální dialogové `OnInitDialog` je volána, když **vytvořit** je volána. Obvykle přepsat `OnInitDialog` se inicializovat ovládací prvky dialogových oken, například nastavení počáteční text textové pole. Je třeba zavolat `OnInitDialog` – členská funkce základní třídy, `CDialog`, z vaší `OnInitDialog` přepsat.  
  
 Pokud chcete nastavit barvu pozadí vašem dialogovém (a u všech dalších dialogových oken v aplikaci), přečtěte si téma [nastavení barvy pozadí v dialogovém](../mfc/setting-the-dialog-boxs-background-color.md).  
  
## <a name="see-also"></a>Viz také  
 [Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)

