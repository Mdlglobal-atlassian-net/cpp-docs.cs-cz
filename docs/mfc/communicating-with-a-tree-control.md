---
title: Komunikace s ovládacím prvkem strom
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
ms.openlocfilehash: 920608724ebb362b91efdcb3eab50b80acd20474
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151252"
---
# <a name="communicating-with-a-tree-control"></a>Komunikace s ovládacím prvkem strom

Použít různé metody pro volání členských funkcí [CTreeCtrl](../mfc/reference/ctreectrl-class.md) objekt v závislosti na způsobu vytvoření objektu:

- Pokud do ovládacího prvku stromu je v dialogovém okně, použijte proměnnou člena typu `CTreeCtrl` , který vytvoříte v poli třídy dialogového okna.

- Pokud do ovládacího prvku stromu je podřízené okno, použijte `CTreeCtrl` objektu (nebo ukazatele) jste použili pro vytvoření objektu.

- Pokud používáte `CTreeView` objektu, použijte funkci [CTreeView::GetTreeCtrl](../mfc/reference/ctreeview-class.md#gettreectrl) získáte odkaz na ovládací prvek stromu. Můžete inicializovat jiný odkaz s touto hodnotou nebo přiřazení adresy proměnné odkazu na `CTreeCtrl` ukazatele.

## <a name="see-also"></a>Viz také:

[Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
