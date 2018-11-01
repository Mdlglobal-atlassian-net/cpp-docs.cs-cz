---
title: Přidávání položek do ovládacího prvku záhlaví
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], header
- CHeaderCtrl class [MFC], adding items
- header controls [MFC], adding items to
ms.assetid: 2e9a28b1-7302-4a93-8037-c5a4183e589a
ms.openlocfilehash: c751458a3a2e7e049364ef22a161a3dc9f81df13
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483561"
---
# <a name="adding-items-to-the-header-control"></a>Přidávání položek do ovládacího prvku záhlaví

Po vytvoření ovládacího prvku záhlaví ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) v jeho nadřazenému oknu, přidejte libovolný počet "položky hlavičky" podle potřeby: obvykle jeden sloupec.

### <a name="to-add-a-header-item"></a>Chcete-li přidat položky záhlaví

1. Příprava [HD_ITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema) struktury.

1. Volání [CHeaderCtrl::InsertItem](../mfc/reference/cheaderctrl-class.md#insertitem), předejte strukturu.

1. Opakujte kroky 1 a 2 pro další položky.

Další informace najdete v tématu [přidání položky do ovládacího prvku záhlaví](/windows/desktop/Controls/header-controls) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Používání atributu CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

