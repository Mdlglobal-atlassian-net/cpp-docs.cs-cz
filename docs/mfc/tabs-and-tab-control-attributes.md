---
title: Karty a atributy ovládacího prvku karta
ms.date: 11/04/2016
helpviewer_keywords:
- attributes [MFC], reference topics
- tab controls [MFC], attributes
- tabs [MFC]
- tabs [MFC], attributes
- CTabCtrl class [MFC], tab control attributes
ms.assetid: ecf190cb-f323-4751-bfdb-766dbe6bb553
ms.openlocfilehash: 982ec40e330e2a7dda5c125d83e54751cd14416d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511239"
---
# <a name="tabs-and-tab-control-attributes"></a>Karty a atributy ovládacího prvku karta

Máte značnou kontrolu nad vzhledem a chováním karet, které tvoří ovládací prvek karta ([atributu CTabCtrl](../mfc/reference/ctabctrl-class.md)). Každá karta může mít popisek, ikonu, stav položky a přidruženou hodnotu 32 definovanou aplikací. Pro každou kartu můžete zobrazit ikonu, popisek nebo obojí.

Kromě toho může mít každá položka karty tři možné stavy: stisknuté, nestisknuté nebo zvýrazněné. Tento stav lze nastavit pouze úpravou existující položky karty. Chcete-li upravit existující položku karty, načtěte ji voláním [GetItem](../mfc/reference/ctabctrl-class.md#getitem), upravte `TCITEM` strukturu (konkrétně datové členy *dwState* a *dwStateMask* ) a pak vraťte upravenou `TCITEM` strukturu voláním metody [SetItem](../mfc/reference/ctabctrl-class.md#setitem). Pokud potřebujete vymazat stavy položek všech položek karty v `CTabCtrl` objektu, zavolejte na [DeselectAll](../mfc/reference/ctabctrl-class.md#deselectall). Tato funkce obnoví stav všech položek karty nebo všech položek s výjimkou aktuálně vybraného.

Následující kód vymaže stav všech položek karty a následně upraví stav třetí položky:

[!code-cpp[NVC_MFCControlLadenDialog#32](../mfc/codesnippet/cpp/tabs-and-tab-control-attributes_1.cpp)]

Další informace o atributech karet naleznete v tématu [karty a atributy tabulátoru](/windows/win32/Controls/tab-controls) v Windows SDK. Další informace o přidávání karet do ovládacího prvku karta najdete v části [Přidání karet k ovládacímu prvku karty](../mfc/adding-tabs-to-a-tab-control.md) dále v tomto tématu.

## <a name="see-also"></a>Viz také:

[Používání atributu CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
