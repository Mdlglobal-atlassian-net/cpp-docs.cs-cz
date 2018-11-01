---
title: Porovnání atributů CTreeCtrl a. CTreeView
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
ms.openlocfilehash: 97997a57a02ee258a50d405f7f61ed9994ccf734
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50540410"
---
# <a name="ctreectrl-vs-ctreeview"></a>Porovnání atributů CTreeCtrl a. CTreeView

Knihovna MFC poskytuje dvě třídy, které provádí zapouzdření ovládacích prvků strom: [CTreeCtrl](../mfc/reference/ctreectrl-class.md) a [CTreeView](../mfc/reference/ctreeview-class.md). Každá třída je užitečná v různých situacích.

Použití `CTreeCtrl` když potřebujete prostý podřízeného ovládacího prvku okno; například v dialogovém okně. Zejména je vhodné použít `CTreeCtrl` Pokud bude existovat jiné podřízené ovládací prvky v okně, stejně jako v typické dialogového okna.

Použití `CTreeView` kdy má ovládací prvek stromové struktury tak, aby fungoval jako okno zobrazení v architektuře document/view – stejně jako ovládací prvek stromu. A `CTreeView` se využije celou klientskou oblast rámce okna nebo okno s rozdělovačem. To bude automaticky nastavena velikost při změně velikosti jeho nadřazenému oknu, a dokáže zpracovat příkaz zprávy z nabídky přístupové klávesy a panely nástrojů. Vzhledem k tomu, že ovládací prvek stromu obsahuje data potřebná k zobrazení stromu, odpovídající objekt dokumentu, nemusí být složité – může dokonce využít [CDocument](../mfc/reference/cdocument-class.md) jako typ dokumentu v šabloně dokumentu.

## <a name="see-also"></a>Viz také

[Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

