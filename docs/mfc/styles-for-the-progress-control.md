---
title: "Styly pro ovládací prvek průběh | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- PBS_SMOOTH style
- progress controls [MFC], styles
- PBS_VERTICAL style
- CProgressCtrl class [MFC], styles
ms.assetid: 39eb8081-bc20-4552-91b9-e7cdd1b7d8ae
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ed0fe26aeeccef7488a64b42438da711feddf5a9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="styles-for-the-progress-control"></a>Styly pro ovládací prvek průběh
Při počátečním vytváření ovládací prvek průběh ([CProgressCtrl::Create](../mfc/reference/cprogressctrl-class.md#create)), použijte `dwStyle` parametr k určení požadované okno Styly pro ovládací prvek průběh. V následujícím seznamu jsou styly použít oken. Ovládací prvek ignoruje všechny styl okna než ty, které jsou zde uvedeny. Vždy byste měli vytvořit ovládacího prvku jako podřízeného okna, obvykle z nadřazené pole dialogové okno.  
  
|Styl okna|Efekt|  
|------------------|------------|  
|`WS_BORDER`|Vytvoří ohraničení kolem okna.|  
|**WS_CHILD –**|Vytvoří podřízeného okna (by se měl pro `CProgressCtrl`).|  
|**WS_CLIPCHILDREN –**|Vyloučí oblasti obsazena podřízená okna při kreslení v rámci nadřazeného okna. Používá se při vytváření nadřazené okno.|  
|**WS_CLIPSIBLINGS –**|Podřízená okna klipů relativně k sobě navzájem.|  
|**WS_DISABLED –**|Vytvoří okno, které je původně zakázána.|  
|**WS_VISIBLE –**|Vytvoří okno, které je původně viditelná.|  
|**WS_TABSTOP –**|Určuje, že ovládací prvek mohou získat fokus po stisknutí klávesy TAB pro přesun do ní.|  
  
 Kromě toho můžete zadat dvě stylů, které se vztahují pouze na ovládací prvek Průběh `PBS_VERTICAL` a `PBS_SMOOTH`.  
  
 Použití `PBS_VERTICAL` pro orientaci ovládacího prvku ve svislém směru, než vodorovně. Použití `PBS_SMOOTH` vyplníte ovládací prvek úplně, místo zobrazení malé vymezen čtverce, které postupně vyplnění ovládacího prvku.  
  
 Bez `PBS_SMOOTH` styl:  
  
 ![Styl panelu Standardní průběh](../mfc/media/vc4ruw1.gif "vc4ruw1")  
  
 S `PBS_SMOOTH` a `PBS_VERTICAL` styly:  
  
 ![Průběhu panelu styl, technologie smooth a svislého](../mfc/media/vc4ruw2.gif "vc4ruw2")  
  
 Další informace najdete v tématu [styly oken](../mfc/reference/styles-used-by-mfc.md#frame-window-styles-mfc) v *odkaz knihovny MFC*.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CProgressCtrl](../mfc/using-cprogressctrl.md)

