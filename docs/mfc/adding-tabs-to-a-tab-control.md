---
title: Přidání karet do ovládacího prvku karta
ms.date: 11/04/2016
helpviewer_keywords:
- tab controls [MFC], adding tabs
- putting tabs on CTabCtrls [MFC]
- CTabCtrl class [MFC], adding tabs
- tabs [MFC], adding to CTabCtrl class [MFC]
ms.assetid: 7f3d9340-e3c7-4c71-9912-be57534ecc78
ms.openlocfilehash: 8915b3af083ebe318e8527b2f83099bf61e7e3ce
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509307"
---
# <a name="adding-tabs-to-a-tab-control"></a>Přidání karet do ovládacího prvku karta

Po vytvoření ovládacího prvku karta ([atributu CTabCtrl](../mfc/reference/ctabctrl-class.md)) přidejte tolik karet, kolik potřebujete.

### <a name="to-add-a-tab-item"></a>Přidání položky karty

1. Připravte strukturu [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) .

1. Zavolejte [atributu CTabCtrl:: InsertItem](../mfc/reference/ctabctrl-class.md#insertitem)a předejte strukturu.

1. Opakujte kroky 1 a 2 pro další položky karet.

Další informace naleznete v tématu [vytvoření ovládacího prvku karta](/windows/win32/Controls/tab-controls) v Windows SDK.

## <a name="see-also"></a>Viz také:

[Používání atributu CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
