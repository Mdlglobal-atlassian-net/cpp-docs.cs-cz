---
title: Přidávání položek do ovládacího prvku | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CListCtrl class [MFC], adding items
ms.assetid: 715994bd-340d-4ad2-9882-411654137830
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a2e9434e93640de190b78e92a1f009a0ad9cbecf
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43214434"
---
# <a name="adding-items-to-the-control"></a>Přidávání položek do ovládacího prvku
Přidání položek do ovládacího prvku seznam ([CListCtrl](../mfc/reference/clistctrl-class.md)), volání jednoho z několika verzí [metody InsertItem](../mfc/reference/clistctrl-class.md#insertitem) členskou funkci, v závislosti na tom, jaké informací, které jsou potřeba. Přijímá jednu verzi [LV_ITEM](/windows/desktop/api/commctrl/ns-commctrl-taglvitema) struktura, která je připravit. Vzhledem k tomu, `LV_ITEM` struktura obsahuje mnoho členů, budete mít větší kontrolu nad atributy položku ovládacího prvku seznamu.  
  
 Dva důležité členy (ve vztahu zobrazení sestavy) `LV_ITEM` struktury jsou `iItem` a `iSubItem` členy. `iItem` Člen je z nuly vycházející index položky odkazuje na strukturu a `iSubItem` člen je založen na jedničce index podpoložku nebo nula, pokud struktura obsahuje informace o položce. Se tyto dva členy můžete určit, za položky, typu a hodnoty podřízenou položku informace, které se zobrazí, když je ovládací prvek seznam v zobrazení sestavy. Další informace najdete v tématu [CListCtrl::SetItem](../mfc/reference/clistctrl-class.md#setitem).  
  
 Další členy zadejte text položky, ikona, stav a data položky. "Položky dat" je hodnota definovaného aplikací přidružených k položce zobrazení seznamu. Další informace o `LV_ITEM` struktury, přečtěte si téma [CListCtrl::GetItem](../mfc/reference/clistctrl-class.md#getitem).  
  
 Další verze `InsertItem` provést jeden nebo více samostatných hodnoty odpovídající členy v `LV_ITEM` struktury, což umožňuje inicializovat pouze ty členy, které chcete podporovat. Obecně platí ovládací prvek seznamu spravuje úložiště pro položky seznamu, ale můžete uložit některé z informací ve vaší aplikaci místo toho pomocí "položky zpětného volání." Další informace najdete v tématu [položky zpětného volání a maska zpětného volání](../mfc/callback-items-and-the-callback-mask.md) v tomto tématu a [položky zpětného volání a maska zpětného volání](/windows/desktop/Controls/using-list-view-controls) v sadě Windows SDK.  
  
 Další informace najdete v tématu [přidávání zobrazení seznamu položek a podpoložek](/windows/desktop/Controls/using-list-view-controls).  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CListCtrl](../mfc/using-clistctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

