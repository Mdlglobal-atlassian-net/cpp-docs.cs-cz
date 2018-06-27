---
title: Styly pro ovládací prvek průběh | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- PBS_SMOOTH style
- progress controls [MFC], styles
- PBS_VERTICAL style
- CProgressCtrl class [MFC], styles
ms.assetid: 39eb8081-bc20-4552-91b9-e7cdd1b7d8ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b29d0df8342ce00a2ddb0d46970d9504a06edd8
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956678"
---
# <a name="styles-for-the-progress-control"></a>Styly pro ovládací prvek průběh
Při počátečním vytváření ovládací prvek průběh ([CProgressCtrl::Create](../mfc/reference/cprogressctrl-class.md#create)), použijte *dwStyle* parametr k určení požadované okno Styly pro ovládací prvek průběh. V následujícím seznamu jsou styly použít oken. Ovládací prvek ignoruje všechny styl okna než ty, které jsou zde uvedeny. Vždy byste měli vytvořit ovládacího prvku jako podřízeného okna, obvykle z nadřazené pole dialogové okno.  
  
|Styl okna|Efekt|  
|------------------|------------|  
|WS_BORDER –|Vytvoří ohraničení kolem okna.|  
|WS_CHILD –|Vytvoří podřízeného okna (by se měl pro `CProgressCtrl`).|  
|WS_CLIPCHILDREN –|Vyloučí oblasti obsazena podřízená okna při kreslení v rámci nadřazeného okna. Používá se při vytváření nadřazené okno.|  
|WS_CLIPSIBLINGS –|Podřízená okna klipů relativně k sobě navzájem.|  
|WS_DISABLED –|Vytvoří okno, které je původně zakázána.|  
|WS_VISIBLE –|Vytvoří okno, které je původně viditelná.|  
|WS_TABSTOP –|Určuje, že ovládací prvek mohou získat fokus po stisknutí klávesy TAB pro přesun do ní.|  
  
 Kromě toho můžete zadat dvě stylů, které se vztahují pouze na ovládací prvek průběh pbs_vertical – a pbs_smooth –.  
  
 Pbs_vertical – použijte pro orientaci ovládacího prvku ve svislém směru, než vodorovně. Funkce pbs_smooth – k řízení úplně, místo zobrazení malé vymezen čtverce, které postupně vyplnění ovládacího prvku.  
  
 Bez pbs_smooth – styl:  
  
 ![Styl panelu Standardní průběh](../mfc/media/vc4ruw1.gif "vc4ruw1")  
  
 S pbs_smooth – a pbs_vertical – styly:  
  
 ![Průběhu panelu styl, technologie smooth a svislého](../mfc/media/vc4ruw2.gif "vc4ruw2")  
  
 Další informace najdete v tématu [styly oken](../mfc/reference/styles-used-by-mfc.md#frame-window-styles-mfc) v *odkaz knihovny MFC*.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CProgressCtrl](../mfc/using-cprogressctrl.md)

