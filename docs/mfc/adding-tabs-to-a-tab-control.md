---
title: Přidání karet do ovládacího prvku karta | Dokumentace Microsoftu
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
ms.openlocfilehash: cb8caad0b7d1f632a2d97e4ea6bda7c93a2b4d74
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43218294"
---
# <a name="adding-tabs-to-a-tab-control"></a>Přidání karet do ovládacího prvku karta
Po vytvoření ovládacího prvku karta ([atributu CTabCtrl](../mfc/reference/ctabctrl-class.md)), přidejte libovolný počet karet podle potřeby.  
  
### <a name="to-add-a-tab-item"></a>Chcete-li přidat položka karty  
  
1.  Příprava [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) struktury.  
  
2.  Volání [CTabCtrl::InsertItem](../mfc/reference/ctabctrl-class.md#insertitem), předejte strukturu.  
  
3.  Opakujte kroky 1 a 2 pro další položky.  
  
 Další informace najdete v tématu [vytváření ovládacího prvku karta](/windows/desktop/Controls/tab-controls) v sadě Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTabCtrl](../mfc/using-ctabctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

