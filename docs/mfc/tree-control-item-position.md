---
title: Umístění položky v ovládacím prvku strom
ms.date: 11/04/2016
helpviewer_keywords:
- CTreeCtrl class [MFC], item position
- item position in tree controls
- tree controls [MFC], item position
- position, CTreeCtrl items
ms.assetid: cd264344-2cf9-4d90-9ea8-c6900b6f60e7
ms.openlocfilehash: d39e48cf940f3e5e903fc8a1c82952d5c2550c05
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501202"
---
# <a name="tree-control-item-position"></a>Umístění položky v ovládacím prvku strom

Počáteční pozici položky je nastavena, když je položka přidána do ovládacího prvku strom ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) s použitím `InsertItem` členskou funkci. Volání členské funkce Určuje popisovač nadřazené položky a popisovač předmětu, po jejímž uplynutí má být vložen nová položka. Druhý popisovač musí identifikovat podřízenou položku dané nadřazeného objektu nebo jednu z těchto hodnot: `TVI_FIRST`, `TVI_LAST`, nebo `TVI_SORT`.

Když `TVI_FIRST` nebo `TVI_LAST` není zadán, umístí do ovládacího prvku stromu novou položku na začátku nebo konci daná nadřazená položka seznamu podřízených položek. Když `TVI_SORT` je zadán do ovládacího prvku stromu vloží novou položku do seznamu podřízených položek v abecedním pořadí podle textu položky popisky.

Nadřazená položka seznamu podřízených položek můžete umístit do abecedy voláním [SortChildren](../mfc/reference/ctreectrl-class.md#sortchildren) členskou funkci. Tato funkce zahrnuje parametr, který určuje, zda všechny úrovně podřízené položky sestupně z daného nadřazené položky jsou také seřazené podle abecedy.

[SortChildrenCB](../mfc/reference/ctreectrl-class.md#sortchildrencb) členská funkce umožňuje řazení podřízených položek na základě kritérií, které definujete. Při volání této funkce můžete specifikovat, stromové struktury můžete volat pokaždé, když relativního pořadí dvou podřízených položek musí být rozhodnuto funkci zpětného volání definované aplikací. Funkce zpětného volání přijímá dva 32-bit aplikace definované hodnoty pro položky, který se porovnává a třetí hodnota 32-bit, který zadáváte při volání `SortChildrenCB`.

## <a name="see-also"></a>Viz také

[Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

