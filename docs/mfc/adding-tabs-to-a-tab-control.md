---
title: Přidání karet do ovládacího prvku karta
ms.date: 11/04/2016
helpviewer_keywords:
- tab controls [MFC], adding tabs
- putting tabs on CTabCtrls [MFC]
- CTabCtrl class [MFC], adding tabs
- tabs [MFC], adding to CTabCtrl class [MFC]
ms.assetid: 7f3d9340-e3c7-4c71-9912-be57534ecc78
ms.openlocfilehash: be622035355a68d1527a515bfdcb633a3af274d8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618267"
---
# <a name="adding-tabs-to-a-tab-control"></a>Přidání karet do ovládacího prvku karta

Po vytvoření ovládacího prvku karta ([atributu CTabCtrl](../mfc/reference/ctabctrl-class.md)), přidejte libovolný počet karet podle potřeby.

### <a name="to-add-a-tab-item"></a>Chcete-li přidat položka karty

1. Příprava [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) struktury.

1. Volání [CTabCtrl::InsertItem](../mfc/reference/ctabctrl-class.md#insertitem), předejte strukturu.

1. Opakujte kroky 1 a 2 pro další položky.

Další informace najdete v tématu [vytváření ovládacího prvku karta](/windows/desktop/Controls/tab-controls) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Používání atributu CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

