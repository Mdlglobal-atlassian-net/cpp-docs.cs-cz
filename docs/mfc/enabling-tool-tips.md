---
title: Povolení tipů nástrojů
ms.date: 11/04/2016
helpviewer_keywords:
- initializing tool tips [MFC]
- enabling tool tips [MFC]
- tool tips [MFC], initializing
- tool tips [MFC], enabling
ms.assetid: 06b7c889-7722-4ce6-8b88-9efa50fe6369
ms.openlocfilehash: 270eb8bad03679cd6e605e3279c0e4ffc499a765
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571136"
---
# <a name="enabling-tool-tips"></a>Povolení tipů nástrojů

Můžete povolit nástroj tip podporu pro podřízené ovládací prvky okna (jako je například ovládací prvky na formuláři zobrazení nebo dialogové okno pole).

### <a name="to-enable-tool-tips-for-the-child-controls-of-a-window"></a>Povolení popisů tlačítek pro podřízených ovládacích prvků okna.

1. Volání `EnableToolTips` pro okno, pro které chcete poskytnout popisů tlačítek.

1. Zadejte řetězec pro každý ovládací prvek ve vaší [oznámení TTN_NEEDTEXT](../mfc/handling-ttn-needtext-notification-for-tool-tips.md) obslužné rutiny. Obslužná rutina je v mapování zprávy okna, která obsahuje podřízené ovládací prvky (například vaší třídy formuláře zobrazení). Tuto obslužnou rutinu by měly volat funkci, která identifikuje ovládací prvek a nastaví **pszText** zadat text, který používá ovládacím prvkem popis tlačítka nástroj.

## <a name="see-also"></a>Viz také

[Popisy tlačítek v oknech neodvozených ze třídy CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)

