---
title: Přidání karet do ovládacího prvku karta | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tab controls [MFC], adding tabs
- putting tabs on CTabCtrls [MFC]
- CTabCtrl class [MFC], adding tabs
- tabs [MFC], adding to CTabCtrl class [MFC]
ms.assetid: 7f3d9340-e3c7-4c71-9912-be57534ecc78
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 86032bd3d1ce10221cb5d8094e4ba6de866e1eea
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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

