---
title: Vytváření seznamů obrázků
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
ms.openlocfilehash: 6687b62b70103894d957a21019008e8781385feb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508779"
---
# <a name="creating-the-image-lists"></a>Vytváření seznamů obrázků

Vytváření seznamů obrázků je stejné, ať už používáte [CListView –](../mfc/reference/clistview-class.md) nebo [CListCtrl](../mfc/reference/clistctrl-class.md).

> [!NOTE]
>  Seznam obrázků potřebujete pouze v `LVS_ICON` případě, že ovládací prvek seznam obsahuje styl.

Použijte třídu `CImageList` k vytvoření jednoho nebo více seznamů obrázků (pro ikony plné velikosti, malé ikony a stavy). Viz [atributu CImageList](../mfc/reference/cimagelist-class.md)a [seznam obrázků zobrazení seznamu](/windows/win32/Controls/using-list-view-controls) v Windows SDK.

Pro každý seznam obrázků zavolejte [CListCtrl:: SetImageList](../mfc/reference/clistctrl-class.md#setimagelist) ; předat ukazatel na příslušný `CImageList` objekt.

## <a name="see-also"></a>Viz také:

[Používání atributu CListCtrl](../mfc/using-clistctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
