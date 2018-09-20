---
title: Vytváření seznamů obrázků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7772b6b6a809e5a89e2cb6b0ef3edb68821805c2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372312"
---
# <a name="creating-the-image-lists"></a>Vytváření seznamů obrázků

Vytváření seznamů obrázků je stejný, ať už používáte [CListView](../mfc/reference/clistview-class.md) nebo [CListCtrl](../mfc/reference/clistctrl-class.md).

> [!NOTE]
>  Pouze potřebovat bitové kopie seznamy pokud obsahuje ovládací prvek seznamu `LVS_ICON` style.

Použití třídy `CImageList` vytvořit jeden nebo více seznamů obrázků (pro reklamy ikony, malé ikony a stavy). Naleznete v tématu [atributu CImageList](../mfc/reference/cimagelist-class.md)a najdete v článku [seznamy obrázků zobrazení seznamu](/windows/desktop/Controls/using-list-view-controls) v sadě Windows SDK.

Volání [CListCtrl::SetImageList](../mfc/reference/clistctrl-class.md#setimagelist) pro každý obrázek seznamu; můžete předat ukazatel na příslušné `CImageList` objektu.

## <a name="see-also"></a>Viz také

[Používání atributu CListCtrl](../mfc/using-clistctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

