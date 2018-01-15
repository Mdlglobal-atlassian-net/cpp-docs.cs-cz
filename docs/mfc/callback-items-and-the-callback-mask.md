---
title: "Položky zpětného volání a maska zpětného volání | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- callback items in CListCtrl class [MFC]
- CListCtrl class [MFC], callback item and callback mask
ms.assetid: 67c1f76f-6144-453e-9376-6712f89430ae
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 24d9992b8a9db679b30624d85ede1a35bfd9826d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="callback-items-and-the-callback-mask"></a>Položky zpětného volání a maska zpětného volání
Pro každý z jeho položky ovládacího prvku zobrazení seznamu obvykle ukládá na text popisku, index bitové kopie seznamu položky ikony, a sadu bit flags pro stav položky. Jednotlivé položky můžete definovat jako položky zpětného volání, které jsou užitečné, pokud již aplikace ukládá některé z informací pro položku.  
  
 Jako položka zpětného volání definujete tak, že zadáte odpovídající hodnoty pro položky `pszText` a `iImage` členy **LV_ITEM** struktury (najdete v části [CListCtrl::GetItem](../mfc/reference/clistctrl-class.md#getitem)). Pokud aplikace udržuje text položky nebo podřízenou položku na, zadejte **LPSTR_TEXTCALLBACK** hodnota `pszText` člen. Pokud ikonu pro položku uchovává informace o aplikaci, zadejte **I_IMAGECALLBACK** hodnota `iImage` člen.  
  
 Kromě definování položky zpětného volání, můžete také upravit maska zpětného volání ovládacího prvku. Tato maska je sada bitové příznaky, které určují stavy položek, pro které aplikace, nikoli ovládacího prvku, uloží aktuální data. Maska zpětného volání platí pro všechny položky ovládacího prvku, na rozdíl od označení položky zpětného volání, která se vztahuje na konkrétní položku. Maska zpětného volání je nulová ve výchozím nastavení, což znamená, že ovládací prvek sleduje všechny stavy položek. Chcete-li změnit toto výchozí chování, inicializace maska na libovolnou kombinaci těchto hodnot:  
  
-   `LVIS_CUT`Operace Vyjmout a vložit je označena jako položka.  
  
-   `LVIS_DROPHILITED`Položka je označený jako cíl přetažení myší.  
  
-   `LVIS_FOCUSED`Položka má fokus.  
  
-   `LVIS_SELECTED`Vybranou položku.  
  
-   **LVIS_OVERLAYMASK** aplikace ukládá seznam index bitové kopie aktuální Image překrytí pro každou položku.  
  
-   **LVIS_STATEIMAGEMASK** aplikace ukládá seznam index bitové kopie aktuální stav obrázku pro každou položku.  
  
 Další informace o načtení a nastavení tuto masku, najdete v části [CListCtrl::GetCallbackMask](../mfc/reference/clistctrl-class.md#getcallbackmask) a [CListCtrl::SetCallbackMask](../mfc/reference/clistctrl-class.md#setcallbackmask).  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CListCtrl](../mfc/using-clistctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

