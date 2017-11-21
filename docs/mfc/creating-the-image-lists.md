---
title: "Vytváření seznamů obrázků | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4878caa735562a76bc4afe64b7d5bb1ecb22e069
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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

