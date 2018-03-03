---
title: "Položky seznamu a seznamy obrázků | Microsoft Docs"
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
- CImageList class [MFC], and list items
- image lists [MFC], list items
- CListCtrl class [MFC], image lists
- list items [MFC], image lists
ms.assetid: 317d095f-f978-47da-acb6-7bfe7dd3bc69
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 525d8353c308796d70f974fa56cde3aa76c12142
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="list-items-and-image-lists"></a>Položky seznamu a seznamy obrázků
"Položka" v ovládacím prvku seznam ([CListCtrl](../mfc/reference/clistctrl-class.md)) se skládá z ikony, štítky a pravděpodobně Další informace (v "podřízených položek").  
  
 Ikon pro ovládací prvek položky seznamu jsou obsaženy v seznamech obrázků. Jeden seznam image obsahuje plné velikosti ikony používané v zobrazení ikon. Seznam druhou, volitelné, image obsahuje menší verze stejné ikony pro použití v ostatních zobrazeních ovládacího prvku. Třetí volitelný seznam obsahuje "stavu" image, jako jsou zaškrtnutí políček u zobrazení před malé ikony v určitých zobrazení. Čtvrtý volitelný seznam obsahuje bitové kopie, které se zobrazí v záhlaví jednotlivé položky ovládacího prvku seznam.  
  
> [!NOTE]
>  Pokud je vytvořen ovládacího prvku zobrazení seznamu s `LVS_SHAREIMAGELISTS` styl, je zodpovědná za zničení seznamů obrázků, když je již používán. Zadejte, že seznamy tento stylů, pokud přiřadíte stejnou bitovou kopii do více ovládací prvky zobrazení seznamu; více než jeden ovládací prvek, jinak může pokusit destroy stejné seznamu obrázků.  
  
 Další informace o položkách seznamu najdete v tématu [seznamy obrázků zobrazení seznamu](http://msdn.microsoft.com/library/windows/desktop/bb774736) a [položky a podřízených položek](http://msdn.microsoft.com/library/windows/desktop/bb774736) ve Windows SDK. Informace v tématu třídy [CImageList](../mfc/reference/cimagelist-class.md) v *odkaz knihovny MFC* a [pomocí ovládacího prvku CImageList](../mfc/using-cimagelist.md) v této rodině článků.  
  
 Pokud chcete vytvořit ovládací prvek seznamu, budete muset zadat seznamy obrázků, který se má použít při vkládání nových položek do seznamu. Následující příklad ukazuje, tento postup, kde `m_pImagelist` je ukazatel typu `CImageList` a `m_listctrl` je `CListCtrl` – datový člen.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#19](../mfc/codesnippet/cpp/list-items-and-image-lists_1.cpp)]  
  
 Ale pokud nemáte v úmyslu zobrazení ikon v zobrazení seznamu nebo ovládací prvek seznamu, nepotřebujete seznamů obrázků.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CListCtrl](../mfc/using-clistctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

