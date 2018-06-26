---
title: Inicializace dialogových oken | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- initializing dialog boxes [MFC]
- OnInitDialog method [MFC]
- modal dialog boxes [MFC], initializing
- modeless dialog boxes [MFC], initializing
- MFC dialog boxes [MFC], initializing
ms.assetid: 968142f5-19f9-4b34-a1d4-8e6412d4379b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c4bc280c57998b23082f11f4ebe42b660177d3c
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929618"
---
# <a name="initializing-the-dialog-box"></a>Inicializace dialogových oken
Po dialogové okno pole a všechny její ovládací prvky se vytvoří, ale těsně před dialogové okno pole (buď typu) se zobrazí na obrazovce objektu dialogového okna na [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) členské funkce je volána. Pro modální dialogové okno, k tomu dojde během `DoModal` volání. Nemodální dialogové `OnInitDialog` je volána, když `Create` je volána. Obvykle přepsat `OnInitDialog` se inicializovat ovládací prvky dialogových oken, například nastavení počáteční text textové pole. Je třeba zavolat `OnInitDialog` – členská funkce základní třídy, `CDialog`, z vaší `OnInitDialog` přepsat.  
  
 Pokud chcete nastavit barvu pozadí vašem dialogovém (a u všech dalších dialogových oken v aplikaci), přečtěte si téma [nastavení barvy pozadí v dialogovém](../mfc/setting-the-dialog-boxs-background-color.md).  
  
## <a name="see-also"></a>Viz také  
 [Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)

