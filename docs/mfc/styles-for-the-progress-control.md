---
title: Styly pro ovládací prvek průběh | Dokumentace Microsoftu
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
ms.openlocfilehash: ce520991b078f01e0551661516bfe7f24c53cf46
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442913"
---
# <a name="styles-for-the-progress-control"></a>Styly pro ovládací prvek průběh

Když nejprve vytvoříte ovládací prvek průběh ([CProgressCtrl::Create](../mfc/reference/cprogressctrl-class.md#create)), použijte *dwStyle* parametr určit požadovanou okno Styly pro ovládací prvek průběh. Následující seznam obsahuje podrobnosti o styly příslušné okno. Ovládací prvek ignoruje jakýkoli styl okna než ty, které jsou tady uvedené. Vždy byste měli vytvořit ovládacího prvku jako podřízeného okna, obvykle z nadřazené pole dialogového okna.

|Styl okna|Efekt|
|------------------|------------|
|WS_BORDER|Vytvoří ohraničení okna.|
|WS_CHILD|Vytvoří podřízené okno (by měl vždycky použije `CProgressCtrl`).|
|WS_CLIPCHILDREN|Vyloučí zabraná podřízená okna při kreslení v rámci nadřazeného okna. Při vytváření nadřazeného okna.|
|WS_CLIPSIBLINGS|Uchycení podřízených oken vzhledem k sobě navzájem.|
|WS_DISABLED|Vytvoří okno, které je zpočátku zakázáno.|
|WS_VISIBLE|Vytvoří okno, které je zpočátku viditelné.|
|WS_TABSTOP|Určuje, že ovládací prvek může získat fokus, když uživatel stiskne klávesu TAB pro přesun do něj.|

Kromě toho můžete zadat dva styly, které se vztahují pouze na ovládací prvek průběh pbs_vertical – a pbs_smooth –.

Pbs_vertical – použijte k orientaci ovládacího prvku ve svislém směru, spíše než vodorovně. Pbs_smooth – použijte k vyplnění ovládací prvek zcela, namísto zobrazení malých čtverečků vymezen, které postupně výplně ovládacího prvku.

Bez pbs_smooth – styl:

![Styl panelu Standardní průběh](../mfc/media/vc4ruw1.gif "vc4ruw1")

Pbs_smooth – a pbs_vertical – styly:

![Indikátor styl hladký a vertikální průběhu](../mfc/media/vc4ruw2.gif "vc4ruw2")

Další informace najdete v tématu [styly oken](../mfc/reference/styles-used-by-mfc.md#frame-window-styles-mfc) v *odkaz knihovny MFC*.

## <a name="see-also"></a>Viz také

[Používání atributu CProgressCtrl](../mfc/using-cprogressctrl.md)

