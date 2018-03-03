---
title: "Posuvník – styly ovládacího prvku | Microsoft Docs"
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
- slider controls [MFC], styles
- CSliderCtrl class [MFC], styles
- styles [MFC], CSliderCtrl
- styles [MFC], slider controls
ms.assetid: 64c491fc-5af1-4f97-ae30-854071b3dc02
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 747f5d55821c6911e80087ebbad65b2169e6fc49
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="slider-control-styles"></a>Posuvník – styly ovládacího prvku
Ovládací prvky posuvníku ([CSliderCtrl](../mfc/reference/csliderctrl-class.md)) může mít svislé nebo vodorovné orientaci. Mají osové značky na obou stranách obě strany, nebo ani jeden z nich. Můžete také používají k určení rozsahu po sobě jdoucích hodnot. Tyto vlastnosti jsou řízena pomocí posuvník – styly ovládacích prvků, které určíte při vytváření ovládacího prvku posuvník.  
  
 `TBS_HORZ` a `TBS_VERT` styly určit orientaci posuvníku. Pokud nezadáte orientace, je v ovládacím prvku posuvník orientované vodorovně.  
  
 `TBS_AUTOTICKS` Styl vytvoří ovládací prvek typu jezdec, který má značky pro každý přírůstek v jeho rozsah hodnot. Tyto značky se přidávají automaticky při volání [SetRange](../mfc/reference/csliderctrl-class.md#setrange) – členská funkce. Pokud nezadáte `TBS_AUTOTICKS`, můžete používat členské funkce, jako třeba [SetTic](../mfc/reference/csliderctrl-class.md#settic) a [SetTicFreq](../mfc/reference/csliderctrl-class.md#setticfreq), určit polohy značek. Pokud chcete vytvořit ovládací prvek typu jezdec, který nezobrazuje osové značky, můžete použít `TBS_NOTICKS` stylu.  
  
 Osové značky můžete zobrazit na jednoho nebo obou stranách ovládacího prvku posuvník. Pro ovládací prvky posuvníku vodorovné, můžete zadat `TBS_BOTTOM` nebo `TBS_TOP` stylu. Pro ovládací prvky posuvníku svislé, můžete zadat `TBS_RIGHT` nebo `TBS_LEFT` stylu. (`TBS_BOTTOM` a `TBS_RIGHT` jsou výchozí nastavení.) Osové značky na obou stranách ovládacího prvku posuvník v jakékoli orientaci, zadejte `TBS_BOTH` stylu.  
  
 Ovládací prvek typu jezdec můžete zobrazit výběr rozsahu pouze v případě, že zadáte `TBS_ENABLESELRANGE` stylu při jeho vytvoření. Pokud ovládací prvek typu jezdec tento styl, značek na počáteční a koncová pozice výběru rozsahu zobrazují jako trojúhelníčky (namísto svislé pomlčky) a výběr rozsahu je zvýrazněn. Výběr rozsahy například může být užitečné při plánování jednoduchou aplikaci. Uživatel může vybrat rozsah osové značky odpovídající hodin za den k identifikaci čas naplánované schůzky.  
  
 Ve výchozím nastavení závisí na délce posuvník ovládacího prvku posuvník změny výběru rozsahu. Pokud má ovládací prvek jezdec **TBS_FIXEDLENGTH** styl, délka jezdec zůstává stejná, i když se změní výběr rozsahu. Ovládací prvek typu jezdec, který má **TBS_NOTHUMB** styl nezahrnuje jezdce.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CSliderCtrl](../mfc/using-csliderctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

