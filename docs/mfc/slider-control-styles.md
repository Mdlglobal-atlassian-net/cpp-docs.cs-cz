---
title: Posuvník – styly ovládacího prvku | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- slider controls [MFC], styles
- CSliderCtrl class [MFC], styles
- styles [MFC], CSliderCtrl
- styles [MFC], slider controls
ms.assetid: 64c491fc-5af1-4f97-ae30-854071b3dc02
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f76fbe9f85d978a5c2865b48720588b620508a07
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951049"
---
# <a name="slider-control-styles"></a>Posuvník – styly ovládacího prvku
Ovládací prvky posuvníku ([CSliderCtrl](../mfc/reference/csliderctrl-class.md)) může mít svislé nebo vodorovné orientaci. Mají osové značky na obou stranách obě strany, nebo ani jeden z nich. Můžete také používají k určení rozsahu po sobě jdoucích hodnot. Tyto vlastnosti jsou řízena pomocí posuvník – styly ovládacích prvků, které určíte při vytváření ovládacího prvku posuvník.  
  
 Styly TBS_HORZ a TBS_VERT určit orientaci posuvníku. Pokud nezadáte orientace, je v ovládacím prvku posuvník orientované vodorovně.  
  
 Styl TBS_AUTOTICKS vytvoří ovládací prvek typu jezdec, který má značky pro každý přírůstek v jeho rozsah hodnot. Tyto značky se přidávají automaticky při volání [SetRange](../mfc/reference/csliderctrl-class.md#setrange) – členská funkce. Pokud nezadáte TBS_AUTOTICKS, můžete použít členské funkce, jako například [SetTic](../mfc/reference/csliderctrl-class.md#settic) a [SetTicFreq](../mfc/reference/csliderctrl-class.md#setticfreq), určit polohy značek. Pokud chcete vytvořit ovládací prvek typu jezdec, který nezobrazuje osové značky, můžete použít styl TBS_NOTICKS.  
  
 Osové značky můžete zobrazit na jednoho nebo obou stranách ovládacího prvku posuvník. Pro ovládací prvky posuvníku vodorovné můžete určit styl TBS_BOTTOM nebo TBS_TOP. Pro ovládací prvky posuvníku svislé můžete určit styl TBS_RIGHT nebo TBS_LEFT. (TBS_BOTTOM a TBS_RIGHT jsou výchozí nastavení). Osové značky na obou stranách ovládacího prvku posuvník v jakékoli orientaci zadejte styl TBS_BOTH.  
  
 Ovládací prvek typu jezdec můžete zobrazit výběr rozsahu pouze v případě, že zadáte styl TBS_ENABLESELRANGE při jeho vytvoření. Pokud ovládací prvek typu jezdec tento styl, značek na počáteční a koncová pozice výběru rozsahu zobrazují jako trojúhelníčky (namísto svislé pomlčky) a výběr rozsahu je zvýrazněn. Výběr rozsahy například může být užitečné při plánování jednoduchou aplikaci. Uživatel může vybrat rozsah osové značky odpovídající hodin za den k identifikaci čas naplánované schůzky.  
  
 Ve výchozím nastavení závisí na délce posuvník ovládacího prvku posuvník změny výběru rozsahu. Pokud v ovládacím prvku posuvník styl TBS_FIXEDLENGTH, délka jezdec zůstává stejná, i když se změní výběr rozsahu. Ovládací prvek typu jezdec, který má styl TBS_NOTHUMB nezahrnuje jezdce.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CSliderCtrl](../mfc/using-csliderctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

