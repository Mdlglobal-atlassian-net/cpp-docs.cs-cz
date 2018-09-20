---
title: Komunikace s ovládacím prvkem strom | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 78bb6a6d6421a5336f8efbffc7d24a6121e208e6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432149"
---
# <a name="communicating-with-a-tree-control"></a>Komunikace s ovládacím prvkem strom

Použít různé metody pro volání členských funkcí [CTreeCtrl](../mfc/reference/ctreectrl-class.md) objekt v závislosti na způsobu vytvoření objektu:

- Pokud do ovládacího prvku stromu je v dialogovém okně, použijte proměnnou člena typu `CTreeCtrl` , který vytvoříte v poli třídy dialogového okna.

- Pokud do ovládacího prvku stromu je podřízené okno, použijte `CTreeCtrl` objektu (nebo ukazatele) jste použili pro vytvoření objektu.

- Pokud používáte `CTreeView` objektu, použijte funkci [CTreeView::GetTreeCtrl](../mfc/reference/ctreeview-class.md#gettreectrl) získáte odkaz na ovládací prvek stromu. Můžete inicializovat jiný odkaz s touto hodnotou nebo přiřazení adresy proměnné odkazu na `CTreeCtrl` ukazatele.

## <a name="see-also"></a>Viz také

[Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

