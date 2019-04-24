---
title: CTreeCtrl vs. CTreeView
ms.date: 11/04/2016
f1_keywords:
- CTreeCtrl
- CTreeView
helpviewer_keywords:
- tree view controls
- CTreeCtrl class [MFC], vs. CTreeView class [MFC]
- CTreeView class [MFC], vs. CTreeCtrl class [MFC]
- tree controls [MFC], and tree view
ms.assetid: bba5af25-103f-4b53-84d3-071bc9bd6494
ms.openlocfilehash: 29349e169e5ad8475001235d9b355da52156d683
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62241930"
---
# <a name="ctreectrl-vs-ctreeview"></a>CTreeCtrl vs. CTreeView

Knihovna MFC poskytuje dvě třídy, které provádí zapouzdření stromu ovládacích prvků: [Ctreectrl –](../mfc/reference/ctreectrl-class.md) a [CTreeView](../mfc/reference/ctreeview-class.md). Každá třída je užitečná v různých situacích.

Použití `CTreeCtrl` když potřebujete prostý podřízeného ovládacího prvku okno; například v dialogovém okně. Zejména je vhodné použít `CTreeCtrl` Pokud bude existovat jiné podřízené ovládací prvky v okně, stejně jako v typické dialogového okna.

Použití `CTreeView` kdy má ovládací prvek stromové struktury tak, aby fungoval jako okno zobrazení v architektuře document/view – stejně jako ovládací prvek stromu. A `CTreeView` se využije celou klientskou oblast rámce okna nebo okno s rozdělovačem. To bude automaticky nastavena velikost při změně velikosti jeho nadřazenému oknu, a dokáže zpracovat příkaz zprávy z nabídky přístupové klávesy a panely nástrojů. Vzhledem k tomu, že ovládací prvek stromu obsahuje data potřebná k zobrazení stromu, odpovídající objekt dokumentu, nemusí být složité – může dokonce využít [CDocument](../mfc/reference/cdocument-class.md) jako typ dokumentu v šabloně dokumentu.

## <a name="see-also"></a>Viz také:

[Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
