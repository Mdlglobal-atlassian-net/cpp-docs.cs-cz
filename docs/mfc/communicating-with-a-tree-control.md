---
title: Komunikace s ovládacím prvkem strom
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
ms.openlocfilehash: a5749b76468a7ba30cd48dc3a9b61f2de7ac67b9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654180"
---
# <a name="communicating-with-a-tree-control"></a>Komunikace s ovládacím prvkem strom

Použít různé metody pro volání členských funkcí [CTreeCtrl](../mfc/reference/ctreectrl-class.md) objekt v závislosti na způsobu vytvoření objektu:

- Pokud do ovládacího prvku stromu je v dialogovém okně, použijte proměnnou člena typu `CTreeCtrl` , který vytvoříte v poli třídy dialogového okna.

- Pokud do ovládacího prvku stromu je podřízené okno, použijte `CTreeCtrl` objektu (nebo ukazatele) jste použili pro vytvoření objektu.

- Pokud používáte `CTreeView` objektu, použijte funkci [CTreeView::GetTreeCtrl](../mfc/reference/ctreeview-class.md#gettreectrl) získáte odkaz na ovládací prvek stromu. Můžete inicializovat jiný odkaz s touto hodnotou nebo přiřazení adresy proměnné odkazu na `CTreeCtrl` ukazatele.

## <a name="see-also"></a>Viz také

[Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

