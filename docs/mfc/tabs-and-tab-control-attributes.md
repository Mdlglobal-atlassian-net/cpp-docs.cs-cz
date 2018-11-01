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
ms.openlocfilehash: ba63fdca32af28d0763dd4cf2da3465a99ddeb1f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571987"
---
# <a name="tabs-and-tab-control-attributes"></a>Karty a atributy ovládacího prvku karta

Máte značné ovládat vzhled a chování karet, které tvoří ovládacího prvku karta ([atributu CTabCtrl](../mfc/reference/ctabctrl-class.md)). Každá karta může mít popisek, ikony, stavu položky a s ním spojená hodnotu 32-bit definovaného aplikací. Pro každou kartu můžete zobrazit ikonu, popisek nebo obojí.

Kromě toho každá karta položka může mít tři možné stavy: stisknutí stavů a zvýrazněn. Tento stav lze nastavit pouze tak, že upravíte existující položka karty. Pokud chcete upravit existující položka karty, načíst pomocí volání [GetItem](../mfc/reference/ctabctrl-class.md#getitem), změnit `TCITEM` struktury (konkrétně *dwState* a *dwStateMask* datové členy ) a pak se vraťte upravené `TCITEM` struktura voláním [SetItem](../mfc/reference/ctabctrl-class.md#setitem). Pokud budete muset vymazat stavy položky karty položek v `CTabCtrl` objektu, volání [DeselectAll](../mfc/reference/ctabctrl-class.md#deselectall). Tato funkce Vynuluje stav všech položek kartu nebo všechny položky s výjimkou jednoho aktuálně vybrané.

Následující kód vymaže stav všech položek kartu a pak změní stav třetí položka:

[!code-cpp[NVC_MFCControlLadenDialog#32](../mfc/codesnippet/cpp/tabs-and-tab-control-attributes_1.cpp)]

Další informace o atributech kartu, najdete v části [karty a atributy karta](/windows/desktop/Controls/tab-controls) v sadě Windows SDK. Další informace o přidání karet do ovládacího prvku karta, naleznete v tématu [přidání karet do ovládacího prvku karta](../mfc/adding-tabs-to-a-tab-control.md) dále v tomto tématu.

## <a name="see-also"></a>Viz také

[Používání atributu CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

