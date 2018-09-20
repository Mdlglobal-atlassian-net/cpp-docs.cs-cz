---
title: Povolení popisů tlačítek | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- initializing tool tips [MFC]
- enabling tool tips [MFC]
- tool tips [MFC], initializing
- tool tips [MFC], enabling
ms.assetid: 06b7c889-7722-4ce6-8b88-9efa50fe6369
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 968d31b49c6d2b2fe5a5f69e04f58f17de8df5a2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440482"
---
# <a name="enabling-tool-tips"></a>Povolení tipů nástrojů

Můžete povolit nástroj tip podporu pro podřízené ovládací prvky okna (jako je například ovládací prvky na formuláři zobrazení nebo dialogové okno pole).

### <a name="to-enable-tool-tips-for-the-child-controls-of-a-window"></a>Povolení popisů tlačítek pro podřízených ovládacích prvků okna.

1. Volání `EnableToolTips` pro okno, pro které chcete poskytnout popisů tlačítek.

1. Zadejte řetězec pro každý ovládací prvek ve vaší [oznámení TTN_NEEDTEXT](../mfc/handling-ttn-needtext-notification-for-tool-tips.md) obslužné rutiny. Obslužná rutina je v mapování zprávy okna, která obsahuje podřízené ovládací prvky (například vaší třídy formuláře zobrazení). Tuto obslužnou rutinu by měly volat funkci, která identifikuje ovládací prvek a nastaví **pszText** zadat text, který používá ovládacím prvkem popis tlačítka nástroj.

## <a name="see-also"></a>Viz také

[Popisy tlačítek v oknech neodvozených ze třídy CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)

