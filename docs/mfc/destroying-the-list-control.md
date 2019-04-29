---
title: Likvidace ovládacího prvku seznam
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], destroying
- CListCtrl class [MFC], destroying controls
ms.assetid: 513ec820-3a02-49d2-b073-a6a7a3fc91b3
ms.openlocfilehash: 963da9e6db2f0fe063dee1ca19ab23f545ed5e76
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392881"
---
# <a name="destroying-the-list-control"></a>Likvidace ovládacího prvku seznam

Vložíte-li vaše [CListCtrl](../mfc/reference/clistctrl-class.md) objektu jako datový člen třídy zobrazení nebo dialogového okna, je zničen při zničení vlastníka. Pokud používáte [CListView](../mfc/reference/clistview-class.md), rozhraní zničí ovládacího prvku, když zničí zobrazení.

Pokud můžete uspořádat pro některý ze seznamu data k uložení do aplikace spíše než ovládací prvek seznamu, je potřeba zajistit její zrušení přidělení. Další informace najdete v tématu [položky zpětného volání a maska zpětného volání](/windows/desktop/Controls/using-list-view-controls) v sadě Windows SDK.

Kromě toho zodpovídáte za zrušení přidělení všechny seznamy obrázků jste vytvořili a přidružený objekt ovládacího prvku seznamu.

## <a name="see-also"></a>Viz také:

[Používání atributu CListCtrl](../mfc/using-clistctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
