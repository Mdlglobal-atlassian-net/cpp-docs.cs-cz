---
title: Metody vytváření popisů tlačítek | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CToolTipCtrl class [MFC], creating tool tips
- tool tips [MFC], tool tip controls
- tool tips [MFC], creating
ms.assetid: b015e9f4-ddfb-49a4-a5a6-fa2d45e4d328
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 16b96228bd2f101e30605e555dbbc75b0dff78c3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374010"
---
# <a name="methods-of-creating-tool-tips"></a>Metody vytváření popisů tlačítek

Knihovna MFC poskytuje tři třídy můžete vytvořit a spravovat nástroj ovládací prvek popis tlačítka: [CWnd](../mfc/reference/cwnd-class.md), [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md), [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md) a [cmfctooltipctrl –](../mfc/reference/cmfctooltipctrl-class.md). Nástroj tip členské funkce v těchto třídách zabalit Windows běžný ovládací prvek rozhraní API. Třída `CToolBarCtrl` a třída `CToolTipCtrl` jsou odvozeny z třídy `CWnd`.

`CWnd` poskytuje čtyři členské funkce můžete vytvářet a spravovat popisů tlačítek: [EnableToolTips](../mfc/reference/cwnd-class.md#enabletooltips), [CancelToolTips](../mfc/reference/cwnd-class.md#canceltooltips), [FilterToolTipMessage](../mfc/reference/cwnd-class.md#filtertooltipmessage), a [ontoolhittest – ](../mfc/reference/cwnd-class.md#ontoolhittest). Podívat se na tyto funkce jednotliví členové pro další informace o způsobu implementace popisů tlačítek.

Pokud vytvoříte pomocí nástrojů `CToolBarCtrl`, můžete implementovat popisů tlačítek pro tento panel nástrojů přímo pomocí následující členské funkce: [GetToolTips](../mfc/reference/ctoolbarctrl-class.md#gettooltips) a [SetToolTips](../mfc/reference/ctoolbarctrl-class.md#settooltips). Podívat se na tyto funkce jednotliví členové a [zpracování oznámení popisů Tip](../mfc/handling-tool-tip-notifications.md) Další informace o způsobu implementace popisů tlačítek.

`CToolTipCtrl` Třída poskytuje funkce pro Windows běžné nástroje ovládacím prvkem popis tlačítka. Ovládacím prvkem popis tlačítka jediného nástroje může poskytnout informace pro více než jeden nástroj. Nástroj je buď okno, jako jsou podřízené okno ovládacího prvku nebo definované aplikací obdélníkovou oblast v rámci klientské oblasti okna. [Cmfctooltipctrl –](../mfc/reference/cmfctooltipctrl-class.md) třída odvozena z `CToolTipCtrl` a poskytuje další vizuální styly a funkce.

## <a name="see-also"></a>Viz také

[Používání atributu CToolTipCtrl](../mfc/using-ctooltipctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

