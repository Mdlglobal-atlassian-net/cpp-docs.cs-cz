---
title: "Přidání karet do ovládacího prvku karta | Microsoft Docs"
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
- tab controls [MFC], adding tabs
- putting tabs on CTabCtrls [MFC]
- CTabCtrl class [MFC], adding tabs
- tabs [MFC], adding to CTabCtrl class [MFC]
ms.assetid: 7f3d9340-e3c7-4c71-9912-be57534ecc78
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 46012a265c1ecefa7af63f829be22e6132e036cb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="adding-tabs-to-a-tab-control"></a>Přidání karet do ovládacího prvku karta
Po vytvoření ovládacího prvku karta ([CTabCtrl](../mfc/reference/ctabctrl-class.md)), přidat libovolný počet záložek, kolik potřebujete.  
  
### <a name="to-add-a-tab-item"></a>Přidat položku Karta  
  
1.  Příprava [TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554) struktury.  
  
2.  Volání [CTabCtrl::InsertItem](../mfc/reference/ctabctrl-class.md#insertitem), předávání strukturu.  
  
3.  Opakujte kroky 1 a 2 pro další karta položky.  
  
 Další informace najdete v tématu [vytvoření ovládacího prvku karta](http://msdn.microsoft.com/library/windows/desktop/bb760550) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTabCtrl](../mfc/using-ctabctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

