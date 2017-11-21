---
title: "Přidávání položek do ovládacího prvku | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: CListCtrl class [MFC], adding items
ms.assetid: 715994bd-340d-4ad2-9882-411654137830
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1469209307f5bfc3016a7232095c36f47b38855b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="adding-items-to-the-control"></a>Přidávání položek do ovládacího prvku
K přidávání položek do ovládacího prvku seznam ([CListCtrl](../mfc/reference/clistctrl-class.md)), volání jednoho z několika verzích [metody InsertItem](../mfc/reference/clistctrl-class.md#insertitem) – členská funkce, v závislosti na tom, jaké informace, které máte. Přebírá jednu verzi [LV_ITEM](http://msdn.microsoft.com/library/windows/desktop/bb774760) struktura, která je připravit. Protože `LV_ITEM` struktura obsahuje mnoho členů, máte větší kontrolu nad atributy ovládacího prvku položky seznamu.  
  
 Dvě důležité členy (ohledně zobrazení sestavy) `LV_ITEM` struktura jsou `iItem` a `iSubItem` členy. `iItem` Člen je index položky strukturu odkazuje založený na nule a `iSubItem` člen je na základě jeden index podpoložek nebo nula, pokud struktura obsahuje informace o položce. Tyto dva členy můžete určit, na položku, typ a hodnotu podpoložek informace, které se zobrazí, když je ovládací prvek seznamu v zobrazení sestavy. Další informace najdete v tématu [CListCtrl::SetItem](../mfc/reference/clistctrl-class.md#setitem).  
  
 Další členové zadat text položky, ikona, stav a data položek. "Položky dat" je hodnota definované aplikací přidružené položky zobrazení seznamu. Další informace o `LV_ITEM` struktury najdete v tématu [CListCtrl::GetItem](../mfc/reference/clistctrl-class.md#getitem).  
  
 Jiné verze `InsertItem` trvat jeden nebo více samostatných hodnoty odpovídající členů `LV_ITEM` struktura, což umožňuje inicializovat pouze členové, které chcete podporovat. Obecně platí ovládacího prvku seznam spravuje úložiště pro položky seznamu, ale můžete ukládat některé z informací v aplikaci místo toho pomocí "položky zpětného volání." Další informace najdete v tématu [položky zpětného volání a maska zpětného volání](../mfc/callback-items-and-the-callback-mask.md) v tomto tématu a [položky zpětného volání a maska zpětného volání](http://msdn.microsoft.com/library/windows/desktop/bb774736) ve Windows SDK.  
  
 Další informace najdete v tématu [přidání položky zobrazení seznamu a podřízených položek](http://msdn.microsoft.com/library/windows/desktop/bb774736).  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CListCtrl](../mfc/using-clistctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

