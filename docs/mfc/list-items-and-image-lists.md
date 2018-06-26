---
title: Položky seznamu a seznamy obrázků | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CImageList class [MFC], and list items
- image lists [MFC], list items
- CListCtrl class [MFC], image lists
- list items [MFC], image lists
ms.assetid: 317d095f-f978-47da-acb6-7bfe7dd3bc69
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6e12c212939a708a4411a28bff0ebe5026a21b1e
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932127"
---
# <a name="list-items-and-image-lists"></a>Položky seznamu a seznamy obrázků
"Položka" v ovládacím prvku seznam ([CListCtrl](../mfc/reference/clistctrl-class.md)) se skládá z ikony, štítky a pravděpodobně Další informace (v "podřízených položek").  
  
 Ikon pro ovládací prvek položky seznamu jsou obsaženy v seznamech obrázků. Jeden seznam image obsahuje plné velikosti ikony používané v zobrazení ikon. Seznam druhou, volitelné, image obsahuje menší verze stejné ikony pro použití v ostatních zobrazeních ovládacího prvku. Třetí volitelný seznam obsahuje "stavu" image, jako jsou zaškrtnutí políček u zobrazení před malé ikony v určitých zobrazení. Čtvrtý volitelný seznam obsahuje bitové kopie, které se zobrazí v záhlaví jednotlivé položky ovládacího prvku seznam.  
  
> [!NOTE]
>  Pokud ovládacího prvku zobrazení seznamu je vytvořen s styl LVS_SHAREIMAGELISTS, jste zodpovědní za zničení seznamů obrázků, když je již používán. Zadejte, že seznamy tento stylů, pokud přiřadíte stejnou bitovou kopii do více ovládací prvky zobrazení seznamu; více než jeden ovládací prvek, jinak může pokusit destroy stejné seznamu obrázků.  
  
 Další informace o položkách seznamu najdete v tématu [seznamy obrázků zobrazení seznamu](http://msdn.microsoft.com/library/windows/desktop/bb774736) a [položky a podřízených položek](http://msdn.microsoft.com/library/windows/desktop/bb774736) ve Windows SDK. Informace v tématu třídy [CImageList](../mfc/reference/cimagelist-class.md) v *odkaz knihovny MFC* a [pomocí ovládacího prvku CImageList](../mfc/using-cimagelist.md) v této rodině článků.  
  
 Pokud chcete vytvořit ovládací prvek seznamu, budete muset zadat seznamy obrázků, který se má použít při vkládání nových položek do seznamu. Následující příklad ukazuje, tento postup, kde *m_pImagelist* je ukazatel typu `CImageList` a *m_listctrl* je `CListCtrl` – datový člen.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#19](../mfc/codesnippet/cpp/list-items-and-image-lists_1.cpp)]  
  
 Ale pokud nemáte v úmyslu zobrazení ikon v zobrazení seznamu nebo ovládací prvek seznamu, nepotřebujete seznamů obrázků.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CListCtrl](../mfc/using-clistctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

