---
title: Zničení ovládacího prvku seznam | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- list controls [MFC], destroying
- CListCtrl class [MFC], destroying controls
ms.assetid: 513ec820-3a02-49d2-b073-a6a7a3fc91b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 25642357e3dd9117ae2817307ed5fa3c4a0921d0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424534"
---
# <a name="destroying-the-list-control"></a>Zničení ovládacího prvku seznam

Vložíte-li vaše [CListCtrl](../mfc/reference/clistctrl-class.md) objektu jako datový člen třídy zobrazení nebo dialogového okna, je zničen při zničení vlastníka. Pokud používáte [CListView](../mfc/reference/clistview-class.md), rozhraní zničí ovládacího prvku, když zničí zobrazení.

Pokud můžete uspořádat pro některý ze seznamu data k uložení do aplikace spíše než ovládací prvek seznamu, je potřeba zajistit její zrušení přidělení. Další informace najdete v tématu [položky zpětného volání a maska zpětného volání](/windows/desktop/Controls/using-list-view-controls) v sadě Windows SDK.

Kromě toho zodpovídáte za zrušení přidělení všechny seznamy obrázků jste vytvořili a přidružený objekt ovládacího prvku seznamu.

## <a name="see-also"></a>Viz také

[Používání atributu CListCtrl](../mfc/using-clistctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

