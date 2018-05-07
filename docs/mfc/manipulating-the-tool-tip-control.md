---
title: Manipulace s ovládacím prvkem popis tlačítka | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CToolTipCtrl class [MFC], manipulating tool tip attributes
- tool tips [MFC], attributes
ms.assetid: 3600afe5-712a-4b56-8456-96e85fe879af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 76976c0907d645ad945700c4d396217880712f11
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="manipulating-the-tool-tip-control"></a>Manipulace s ovládacím prvkem popis tlačítka
Třída `CToolTipCtrl` poskytuje funkce, které řídí různé atributy skupinu člena `CToolTipCtrl` objekt a tip okno nástroje.  
  
 Počáteční, automaticky otevírané okno a reshow doby trvání pro tip okna nástrojů můžete nastavit a načíst pomocí volání [GetDelayTime](../mfc/reference/ctooltipctrl-class.md#getdelaytime) a [SetDelayTime](../mfc/reference/ctooltipctrl-class.md#setdelaytime).  
  
 Změna vzhledu windows tip nástroj s následující funkce:  
  
-   [GetMargin](../mfc/reference/ctooltipctrl-class.md#getmargin) a [SetMargin](../mfc/reference/ctooltipctrl-class.md#setmargin) načítá a nastaví šířku ohraničení tip nástroj až nástroj tip text.  
  
-   [GetMaxTipWidth](../mfc/reference/ctooltipctrl-class.md#getmaxtipwidth) a [SetMaxTipWidth](../mfc/reference/ctooltipctrl-class.md#setmaxtipwidth) načítá a nastaví maximální šířku nástroj tip okno.  
  
-   [GetTipBkColor](../mfc/reference/ctooltipctrl-class.md#gettipbkcolor) a [SetTipBkColor](../mfc/reference/ctooltipctrl-class.md#settipbkcolor) načítá a nastaví barvu pozadí nástroje tip okno.  
  
-   [GetTipTextColor](../mfc/reference/ctooltipctrl-class.md#gettiptextcolor) a [SetTipTextColor](../mfc/reference/ctooltipctrl-class.md#settiptextcolor) načítá a nastaví barvu textu nástroje tip okno.  
  
 Aby ovládacím prvkem popis tlačítka upozornit důležité zprávy, jako například **WM_LBUTTONXXX** zprávy, musí předávání zpráv do vašeho prvkem popis tlačítka. Nejlepší metody pro tento předávání se provést volání [CToolTipCtrl::RelayEvent](../mfc/reference/ctooltipctrl-class.md#relayevent)v `PreTranslateMessage` funkce okna vlastníka. Následující příklad ilustruje jeden možný způsob (za předpokladu, že ovládacím prvkem popis tlačítka se nazývá `m_ToolTip`):  
  
 [!code-cpp[NVC_MFCControlLadenDialog#41](../mfc/codesnippet/cpp/manipulating-the-tool-tip-control_1.cpp)]  
  
 Okamžitě odstranit okno nástroj tip, volání [Pop](../mfc/reference/ctooltipctrl-class.md#pop) – členská funkce.  
  
## <a name="see-also"></a>Viz také  
 [Použití objektu CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

