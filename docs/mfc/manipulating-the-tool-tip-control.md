---
title: Manipulace s ovládacím prvkem popis tlačítka
ms.date: 11/04/2016
helpviewer_keywords:
- CToolTipCtrl class [MFC], manipulating tool tip attributes
- tool tips [MFC], attributes
ms.assetid: 3600afe5-712a-4b56-8456-96e85fe879af
ms.openlocfilehash: d8c994748239871f17b878dd8ea7505a2a8a0b65
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279195"
---
# <a name="manipulating-the-tool-tip-control"></a>Manipulace s ovládacím prvkem popis tlačítka

Třída `CToolTipCtrl` poskytuje skupinu členské funkce, které řídí různé atributy `CToolTipCtrl` objektu a tip panel nástrojů.

Počáteční, automaticky otevíraném okně a reshow doby trvání pro tip okna nástrojů můžete nastavit a načíst pomocí volání [GetDelayTime](../mfc/reference/ctooltipctrl-class.md#getdelaytime) a [SetDelayTime](../mfc/reference/ctooltipctrl-class.md#setdelaytime).

Změna vzhledu windows tip nástroj s následující funkce:

- [GetMargin](../mfc/reference/ctooltipctrl-class.md#getmargin) a [SetMargin](../mfc/reference/ctooltipctrl-class.md#setmargin) získá a nastaví text tipu šířku mezi ohraničením nástroj tip a nástroj.

- [GetMaxTipWidth](../mfc/reference/ctooltipctrl-class.md#getmaxtipwidth) a [SetMaxTipWidth](../mfc/reference/ctooltipctrl-class.md#setmaxtipwidth) získá a nastaví maximální šířku nástroj tip okna.

- [GetTipBkColor](../mfc/reference/ctooltipctrl-class.md#gettipbkcolor) a [SetTipBkColor](../mfc/reference/ctooltipctrl-class.md#settipbkcolor) získá a nastaví barvu pozadí nástroje tip okna.

- [GetTipTextColor](../mfc/reference/ctooltipctrl-class.md#gettiptextcolor) a [SetTipTextColor](../mfc/reference/ctooltipctrl-class.md#settiptextcolor) získá a nastaví barvu textu nástroje tip okna.

Aby ovládacím prvkem popis tlačítka nástroj upozornit důležité zprávy, jako je například WM_LBUTTONXXX zprávy musí zpráv přenosu do vaší ovládacím prvkem popis tlačítka nástroj. Nejlepší metody pro toto propojení je, aby volání [CToolTipCtrl::RelayEvent](../mfc/reference/ctooltipctrl-class.md#relayevent)v `PreTranslateMessage` funkce nadřazenému oknu. Následující příklad ukazuje jednu metodu je to možné (za předpokladu, že ovládacím prvkem popis tlačítka nástroj se nazývá `m_ToolTip`):

[!code-cpp[NVC_MFCControlLadenDialog#41](../mfc/codesnippet/cpp/manipulating-the-tool-tip-control_1.cpp)]

Pokud chcete okamžitě odstranit popis tlačítka panelu nástrojů, zavolejte [vyvolat přes Pop](../mfc/reference/ctooltipctrl-class.md#pop) členskou funkci.

## <a name="see-also"></a>Viz také:

[Používání atributu CToolTipCtrl](../mfc/using-ctooltipctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
