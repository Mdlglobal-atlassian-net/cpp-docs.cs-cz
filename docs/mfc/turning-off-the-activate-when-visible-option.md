---
title: Vypnutí možnosti Activate When Visible
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], activate options
- Activate When Visible option [MFC]
ms.assetid: 8f7ddc5a-a7a6-4da8-bcb9-1b569f0ecb48
ms.openlocfilehash: 42dbec7a55085235e43fa14ab6406bfb3526afdb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464828"
---
# <a name="turning-off-the-activate-when-visible-option"></a>Vypnutí možnosti Activate When Visible

Ovládací prvek má dva základní stavy: aktivní a neaktivní. Dříve bylo zvykem, že tyto stavy byly rozlišeny skutečností, zda ovládací prvek má okno. Aktivní ovládací prvek okno měl, neaktivní nikoli. Se zavedením aktivace bez oken není již toto rozlišení univerzální, ale pro mnoho ovládacích prvků je stále platné.

Vytvoření okna ve srovnání s ostatními inicializace obvykle provádí ovládacího prvku ActiveX, je velmi náročná operace. Ovládací prvek v ideálním případě by odložit vytvoření její okno, dokud je nezbytně nutné.

Mnoho ovládacích prvků se nemusíte být aktivní celou dobu, které jsou viditelné v kontejneru. Ovládací prvek často, může zůstat v neaktivním stavu, dokud uživatel provede operaci, která vyžaduje, aby se aktivní (například kliknutí myší nebo stisknutí klávesy TAB). Pokud chcete způsobit, že ovládací prvek zůstat neaktivní, dokud kontejneru je potřeba aktivovat, odeberte **OLEMISC_ACTIVATEWHENVISIBLE** příznak z ovládacího prvku různé příznaky:

[!code-cpp[NVC_MFC_AxOpt#9](../mfc/codesnippet/cpp/turning-off-the-activate-when-visible-option_1.cpp)]

**OLEMISC_ACTIVATEWHENVISIBLE** příznak je vynechána automaticky, pokud vypnete funkci zasílání zpráv **aktivovat When Visible** možnost [nastavení](../mfc/reference/control-settings-mfc-activex-control-wizard.md) stránky ActiveX knihovny MFC Ovládací prvek Průvodce při vytváření ovládacího prvku.

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX: Optimalizace](../mfc/mfc-activex-controls-optimization.md)

