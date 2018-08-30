---
title: Přidávání položek do ovládacího prvku záhlaví | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [MFC], header
- CHeaderCtrl class [MFC], adding items
- header controls [MFC], adding items to
ms.assetid: 2e9a28b1-7302-4a93-8037-c5a4183e589a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a6450d99b8df436c64337e52fc14244ecbb0edfc
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206144"
---
# <a name="adding-items-to-the-header-control"></a>Přidávání položek do ovládacího prvku záhlaví
Po vytvoření ovládacího prvku záhlaví ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) v jeho nadřazenému oknu, přidejte libovolný počet "položky hlavičky" podle potřeby: obvykle jeden sloupec.  
  
### <a name="to-add-a-header-item"></a>Chcete-li přidat položky záhlaví  
  
1.  Příprava [HD_ITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema) struktury.  
  
2.  Volání [CHeaderCtrl::InsertItem](../mfc/reference/cheaderctrl-class.md#insertitem), předejte strukturu.  
  
3.  Opakujte kroky 1 a 2 pro další položky.  
  
 Další informace najdete v tématu [přidání položky do ovládacího prvku záhlaví](/windows/desktop/Controls/header-controls) v sadě Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

