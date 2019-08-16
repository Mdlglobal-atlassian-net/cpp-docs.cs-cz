---
title: Přidávání položek do ovládacího prvku záhlaví
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], header
- CHeaderCtrl class [MFC], adding items
- header controls [MFC], adding items to
ms.assetid: 2e9a28b1-7302-4a93-8037-c5a4183e589a
ms.openlocfilehash: d9a35123ddbe77b8e5e1779651fc4cde233863ae
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509315"
---
# <a name="adding-items-to-the-header-control"></a>Přidávání položek do ovládacího prvku záhlaví

Po vytvoření ovládacího prvku Header ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) ve svém nadřazeném okně Přidejte tolik položek hlaviček, kolik potřebujete: obvykle je to pro každý sloupec.

### <a name="to-add-a-header-item"></a>Přidání položky záhlaví

1. Příprava struktury [HD_ITEM](/windows/win32/api/commctrl/ns-commctrl-_hd_itemw)

1. Zavolejte [CHeaderCtrl:: InsertItem](../mfc/reference/cheaderctrl-class.md#insertitem)a předejte strukturu.

1. Opakujte kroky 1 a 2 pro další položky.

Další informace naleznete v tématu [Přidání položky do ovládacího prvku záhlaví](/windows/win32/Controls/header-controls) v Windows SDK.

## <a name="see-also"></a>Viz také:

[Používání atributu CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
