---
title: Vytváření seznamů obrázků
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
ms.openlocfilehash: 440ab6fdfe7663557f6c6a6607e617c793d26674
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371578"
---
# <a name="creating-the-image-lists"></a>Vytváření seznamů obrázků

Vytváření seznamů obrázků je stejné, zda používáte [CListView](../mfc/reference/clistview-class.md) nebo [CListCtrl](../mfc/reference/clistctrl-class.md).

> [!NOTE]
> Seznamy obrázků potřebujete pouze v `LVS_ICON` případě, že ovládací prvek seznamu obsahuje styl.

Pomocí `CImageList` třídy můžete vytvořit jeden nebo více seznamů obrázků (pro ikony v plné velikosti, malé ikony a stavy). Viz [CImageList](../mfc/reference/cimagelist-class.md)a viz [Seznam obrázků zobrazení seznamu](/windows/win32/Controls/using-list-view-controls) v sadě Windows SDK.

Volání [CListCtrl::SetImageList](../mfc/reference/clistctrl-class.md#setimagelist) pro každý seznam obrázků; předá ukazatel na `CImageList` příslušný objekt.

## <a name="see-also"></a>Viz také

[Používání atributu CListCtrl](../mfc/using-clistctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
