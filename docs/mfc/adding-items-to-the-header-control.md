---
title: Přidávání položek do ovládacího prvku záhlaví | Microsoft Docs
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
ms.openlocfilehash: 69d64265a94df2770e3a234ab992130b4809f9e3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342732"
---
# <a name="adding-items-to-the-header-control"></a>Přidávání položek do ovládacího prvku záhlaví
Po vytvoření ovládacího prvku záhlaví ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) v jeho nadřazeného okna přidat tolik "záhlaví položky" podle potřeby: obvykle jeden na každý sloupec.  
  
### <a name="to-add-a-header-item"></a>Chcete-li přidat položky záhlaví  
  
1.  Příprava [HD_ITEM](http://msdn.microsoft.com/library/windows/desktop/bb775247) struktury.  
  
2.  Volání [CHeaderCtrl::InsertItem](../mfc/reference/cheaderctrl-class.md#insertitem), předávání strukturu.  
  
3.  Opakujte kroky 1 a 2 pro další položky.  
  
 Další informace najdete v tématu [přidání položky do ovládacího prvku záhlaví](http://msdn.microsoft.com/library/windows/desktop/bb775238) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

