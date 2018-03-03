---
title: "Přidávání položek do ovládacího prvku záhlaví | Microsoft Docs"
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
- controls [MFC], header
- CHeaderCtrl class [MFC], adding items
- header controls [MFC], adding items to
ms.assetid: 2e9a28b1-7302-4a93-8037-c5a4183e589a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4de62d534da103f17df113b04b88021561739cfc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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

