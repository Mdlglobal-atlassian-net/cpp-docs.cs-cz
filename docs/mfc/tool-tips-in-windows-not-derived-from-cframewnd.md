---
title: Popisy tlačítek v Windows Neodvozených ze třídy CFrameWnd | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- enabling tool tips [MFC]
- TOOLTIPTEXT structure [MFC]
- Help [MFC], tool tips for controls
- TTN_NEEDTEXT message [MFC]
- controls [MFC], tool tips
- handler functions [MFC], tool tips
ms.assetid: cad5ef0f-02e3-4151-ad0d-3d42e6932b0e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ea6f39f8c1478715ecc656ca84c1d6b24b7c03b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46445513"
---
# <a name="tool-tips-in-windows-not-derived-from-cframewnd"></a>Popisy tlačítek v oknech neodvozených ze třídy CFrameWnd

Řada Tento článek popisuje povolení popisů tlačítek pro ovládací prvky obsažené v okně, který není odvozen od [CFrameWnd](../mfc/reference/cframewnd-class.md). Tento článek [popisů tlačítek panelů nástrojů](../mfc/toolbar-tool-tips.md) poskytuje informace o popisy pro ovládací prvky v `CFrameWnd`.

Tento článek řady probíraná témata zahrnují:

- [Povolení popisů tlačítek](../mfc/enabling-tool-tips.md)

- [Zpracování oznámení TTN_NEEDTEXT u popisů tlačítek](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)

- [ToolTipText – struktura](../mfc/tooltiptext-structure.md)

Popisy tlačítek se automaticky zobrazí pro tlačítka a další ovládací prvky obsažené v nadřazené okno odvozené od `CFrameWnd`. Důvodem je, že `CFrameWnd` má výchozí obslužnou rutinu pro [TTN_GETDISPINFO](/windows/desktop/Controls/ttn-getdispinfo) oznámení, která zpracovává **TTN_NEEDTEXT** oznámení z nástroje pro tip ovládací prvky přidružené ovládací prvky.

Nicméně, tato výchozí obslužná rutina není voláno, když **TTN_NEEDTEXT** oznámení se odesílá z ovládacího prvku tip nástroj, který je přidružený k ovládacímu prvku v okně, které nejsou `CFrameWnd`, jako je například ovládací prvek na dialogové okno nebo zobrazení formuláře. Proto je nezbytná k poskytnutí funkci obslužné rutiny pro **TTN_NEEDTEXT** zprávy oznámení, aby bylo možné zobrazit popisy tlačítek pro podřízené prvky.

Popisy tlačítek výchozí k dispozici pro windows pomocí [CWnd::EnableToolTips](../mfc/reference/cwnd-class.md#enabletooltips) nemají text související s nimi. Načíst text tlačítka, který se zobrazí, **TTN_NEEDTEXT** oznámení se posílá ovládacím prvkem popis tlačítka nástroj nadřazenému oknu, těsně před plánovaným se zobrazí okno tipů nástrojů. Pokud neexistuje žádná obslužná rutina pro přiřazení nějakou hodnotu pro tuto zprávu *pszText* členem **TOOLTIPTEXT** struktury, nebude žádný text pro popis tlačítka zobrazen.

## <a name="see-also"></a>Viz také

[Popisy tlačítek](../mfc/tool-tips.md)

