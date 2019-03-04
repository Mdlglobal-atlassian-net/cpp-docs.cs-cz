---
title: Vytváření seznamů obrázků
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
ms.openlocfilehash: 844bfe71f7b03f299f57b0fd4558b7e9eacf67c2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265779"
---
# <a name="creating-the-image-lists"></a>Vytváření seznamů obrázků

Vytváření seznamů obrázků je stejný, ať už používáte [CListView](../mfc/reference/clistview-class.md) nebo [CListCtrl](../mfc/reference/clistctrl-class.md).

> [!NOTE]
>  Pouze potřebovat bitové kopie seznamy pokud obsahuje ovládací prvek seznamu `LVS_ICON` style.

Použití třídy `CImageList` vytvořit jeden nebo více seznamů obrázků (pro reklamy ikony, malé ikony a stavy). Naleznete v tématu [atributu CImageList](../mfc/reference/cimagelist-class.md)a najdete v článku [seznamy obrázků zobrazení seznamu](/windows/desktop/Controls/using-list-view-controls) v sadě Windows SDK.

Volání [CListCtrl::SetImageList](../mfc/reference/clistctrl-class.md#setimagelist) pro každý obrázek seznamu; můžete předat ukazatel na příslušné `CImageList` objektu.

## <a name="see-also"></a>Viz také:

[Používání atributu CListCtrl](../mfc/using-clistctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
