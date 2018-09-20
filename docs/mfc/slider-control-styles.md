---
title: Posuvník – styly ovládacího prvku | Dokumentace Microsoftu
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
ms.openlocfilehash: 8ddc96133f07011969e3d2afc4b1707e9f395e6b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424115"
---
# <a name="slider-control-styles"></a>Posuvník – styly ovládacího prvku

Ovládacích prvků posuvník ([atributu CSliderCtrl](../mfc/reference/csliderctrl-class.md)) může mít svislé nebo vodorovné orientace. Značky mohou mít na obou stranách obě strany, nebo ani jeden. Můžete také používají k určení rozsahu po sobě jdoucích hodnot. Tyto vlastnosti jsou řízeny pomocí – styly ovládacího prvku posuvník, který lze určit při vytváření v ovládacím prvku posuvník.

Styly TBS_HORZ a TBS_VERT Určuje orientaci ovládacího prvku posuvník. Pokud nezadáte orientaci, je v ovládacím prvku posuvník orientovaný vodorovně.

Styl TBS_AUTOTICKS vytvoří ovládací prvek posuvník, který má značku pro každý přírůstek ve svém rozsahu hodnot. Tyto značky se automaticky přidají při volání [SetRange](../mfc/reference/csliderctrl-class.md#setrange) členskou funkci. Pokud nezadáte TBS_AUTOTICKS, můžete použít členské funkce, jako například [SetTic](../mfc/reference/csliderctrl-class.md#settic) a [SetTicFreq](../mfc/reference/csliderctrl-class.md#setticfreq), chcete-li určit podle polohy značek. Vytvoření ovládacího prvku posuvník, který nezobrazí osové značky, můžete použít styl TBS_NOTICKS.

Zobrazení značek na jednoho nebo obou stranách v ovládacím prvku posuvník. Pro ovládací prvky vodorovný posuvník můžete zadat TBS_BOTTOM nebo TBS_TOP style. Pro svislý posuvník ovládací prvky můžete zadat TBS_RIGHT nebo TBS_LEFT style. (Výchozí nastavení jsou TBS_BOTTOM a TBS_RIGHT.) Pro značky na obou stranách ovládací prvek posuvník v jakékoli orientaci zadejte styl TBS_BOTH.

Ovládací prvek typu jezdec můžete zobrazit oblast výběru pouze v případě, že zadáte TBS_ENABLESELRANGE stylu při vytváření. Při tímto stylem má ovládací prvek posuvník, značek na počáteční a koncové pozice výběru rozsahu se zobrazují jako trojúhelníky (namísto svislé pomlčky) a je zvýrazněn rozsahu výběru. Výběr oblasti může být například užitečné při plánování jednoduchou aplikaci. Uživatel může vybrat oblast značky odpovídající hodin za den pro identifikaci čas naplánované schůzky.

Ve výchozím nastavení závisí na délce posuvník ovládacího prvku posuvník změny výběru rozsahu. Pokud v ovládacím prvku posuvník TBS_FIXEDLENGTH styl, délka posuvník zůstává stejná, i když se změní výběr rozsahu. Posuvník, který má styl TBS_NOTHUMB nezahrnuje ovládací prvek posuvník.

## <a name="see-also"></a>Viz také

[Používání atributu CSliderCtrl](../mfc/using-csliderctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

