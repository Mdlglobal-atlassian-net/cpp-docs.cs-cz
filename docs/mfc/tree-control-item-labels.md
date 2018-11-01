---
title: Popisky položek ovládacího prvku strom
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], item labels
- labels, CTreeCtrl items
- CTreeCtrl class [MFC], item labels
- item labels, tree controls
- item labels
ms.assetid: fe834107-1a25-4280-aced-774c11565805
ms.openlocfilehash: 0abfeee170dbc9cbb4639e896e7a22d7184b35a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438191"
---
# <a name="tree-control-item-labels"></a>Popisky položek ovládacího prvku strom

Text popisku položky zadáte obvykle při přidání položky do ovládacího prvku strom ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)). `InsertItem` Můžete členské funkce předat [TVITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtvitema) strukturu, která definuje vlastnosti položky, včetně řetězec obsahující text popisku. `InsertItem` má několik přetížení, které mohou být volány pomocí různých kombinací parametry.

Ovládací prvek stromu přiděluje paměť pro ukládání každé položky; text položky popisky zabírá podstatnou část tuto paměť. Pokud vaše aplikace udržuje kopie řetězce v ovládacím prvku stromu, můžete snížit požadavky na paměť ovládacího prvku tak, že zadáte **LPSTR_TEXTCALLBACK** hodnotu *pszText* člen `TV_ITEM` nebo *lpszItem* parametr místo předávání skutečné řetězce do ovládacího prvku stromu. Pomocí **LPSTR_TEXTCALLBACK** způsobí, že získání textu popisku položky z aplikace vždy, když je položka vyžadovaly překreslení ovládacího prvku stromu. Načíst text, odešle do ovládacího prvku stromu [TVN_GETDISPINFO](/windows/desktop/Controls/tvn-getdispinfo) zprávy oznámení, který obsahuje adresu [NMTVDISPINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtvdispinfoa) struktury. Musí odpovídat nastavením příslušných členů struktury zahrnuté.

Ovládací prvek stromu používá paměti přidělené z haldy procesu, který vytvoří ovládací prvek stromu. Maximální počet položek v ovládacím prvku stromu je podle množství paměti v haldě k dispozici. Každá položka má 64 bajtů.

## <a name="see-also"></a>Viz také

[Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

