---
title: "Vytváření seznamů obrázků | Microsoft Docs"
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
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bfb42dc2c14b5092aeb667ea22008abe4d581a6f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="creating-the-image-lists"></a>Vytváření seznamů obrázků
Vytváření seznamů obrázků je stejný, ať používáte [CListView](../mfc/reference/clistview-class.md) nebo [CListCtrl](../mfc/reference/clistctrl-class.md).  
  
> [!NOTE]
>  Vytvořením pouze potřebovat bitové kopie seznamy vaše ovládací prvek seznamu obsahuje-li `LVS_ICON` stylu.  
  
 Použití třídy `CImageList` vytvořit jeden nebo více seznamů obrázků (pro plné velikosti ikony, ikony. Malé ikony a stavy). V tématu [CImageList](../mfc/reference/cimagelist-class.md)a zobrazit [seznamy obrázků zobrazení seznamu](http://msdn.microsoft.com/library/windows/desktop/bb774736) ve Windows SDK.  
  
 Volání [CListCtrl::SetImageList](../mfc/reference/clistctrl-class.md#setimagelist) pro každou obraz seznamu; předat ukazatel na příslušné `CImageList` objektu.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CListCtrl](../mfc/using-clistctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

