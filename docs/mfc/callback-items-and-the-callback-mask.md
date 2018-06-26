---
title: Položky zpětného volání a maska zpětného volání | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- callback items in CListCtrl class [MFC]
- CListCtrl class [MFC], callback item and callback mask
ms.assetid: 67c1f76f-6144-453e-9376-6712f89430ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4f3608fbc0c7e34de4ae67ae60a12af23e9ac885
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931685"
---
# <a name="callback-items-and-the-callback-mask"></a>Položky zpětného volání a maska zpětného volání
Pro každý z jeho položky ovládacího prvku zobrazení seznamu obvykle ukládá na text popisku, index bitové kopie seznamu položky ikony, a sadu bit flags pro stav položky. Jednotlivé položky můžete definovat jako položky zpětného volání, které jsou užitečné, pokud již aplikace ukládá některé z informací pro položku.  
  
 Jako položka zpětného volání definujete tak, že zadáte odpovídající hodnoty pro položky `pszText` a `iImage` členy **LV_ITEM** struktury (najdete v části [CListCtrl::GetItem](../mfc/reference/clistctrl-class.md#getitem)). Pokud aplikace udržuje text položky nebo podřízenou položku na, zadejte **LPSTR_TEXTCALLBACK** hodnota `pszText` člen. Pokud ikonu pro položku uchovává informace o aplikaci, zadejte **I_IMAGECALLBACK** hodnota `iImage` člen.  
  
 Kromě definování položky zpětného volání, můžete také upravit maska zpětného volání ovládacího prvku. Tato maska je sada bitové příznaky, které určují stavy položek, pro které aplikace, nikoli ovládacího prvku, uloží aktuální data. Maska zpětného volání platí pro všechny položky ovládacího prvku, na rozdíl od označení položky zpětného volání, která se vztahuje na konkrétní položku. Maska zpětného volání je nulová ve výchozím nastavení, což znamená, že ovládací prvek sleduje všechny stavy položek. Chcete-li změnit toto výchozí chování, inicializace maska na libovolnou kombinaci těchto hodnot:  
  
-   **LVIS_CUT** položka je označen pro operace vyjímání a vkládání.  
  
-   **LVIS_DROPHILITED** položka je označený jako cíl přetažení myší.  
  
-   **LVIS_FOCUSED** položka je aktivní.  
  
-   **LVIS_SELECTED** vybranou položku.  
  
-   **LVIS_OVERLAYMASK** aplikace ukládá seznam index bitové kopie aktuální Image překrytí pro každou položku.  
  
-   **LVIS_STATEIMAGEMASK** aplikace ukládá seznam index bitové kopie aktuální stav obrázku pro každou položku.  
  
 Další informace o načtení a nastavení tuto masku, najdete v části [CListCtrl::GetCallbackMask](../mfc/reference/clistctrl-class.md#getcallbackmask) a [CListCtrl::SetCallbackMask](../mfc/reference/clistctrl-class.md#setcallbackmask).  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CListCtrl](../mfc/using-clistctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

