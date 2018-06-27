---
title: Popisy tlačítek panelu nástrojů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tool tips [MFC], activating
- CBRS_TOOLTIPS constant [MFC]
- tool tips [MFC], adding text
- updates [MFC]
- CBRS_FLYBY constant [MFC]
- tool tips [MFC]
- updating status bar messages
- updates, status bar messages
- status bars [MFC], tool tips
- flyby status bar updates
ms.assetid: d1696305-b604-4fad-9f09-638878371412
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 90f325df3825b3546616ce145d4477322a1b4eed
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956291"
---
# <a name="toolbar-tool-tips"></a>Popisy tlačítek na panelu nástrojů
Popisy jsou velmi malé místní windows, která představují krátký popis tlačítka panelu nástrojů účel při umístit ukazatel myši nad tlačítko pro určitou dobu. Když vytvoříte aplikaci pomocí Průvodce aplikací, který má panel nástrojů, nástroj tip podpora je k dispozici pro vás. Tento článek vysvětluje, jak nástroj tip podporu vytvořené v Průvodce vytvořením aplikace a jak přidat nástroj pro podporu tip do vaší aplikace.  
  
 Tento článek se zabývá:  
  
-   [Aktivace popisů tlačítek](#_core_activating_tool_tips)  
  
-   [Průběžné aktualizace stavového řádku](#_core_fly_by_status_bar_updates)  
  
##  <a name="_core_activating_tool_tips"></a> Aktivace popisů tlačítek  
 Chcete-li aktivovat popisů tlačítek v aplikaci, musíte udělat dvě věci:  
  
-   Cbrs_tooltips – styl přidat do jiné styly (například ws_child –, ws_visible – a další **CBRS_** styly) předány jako *dwStyle* parametru [CToolBar::Create](../mfc/reference/ctoolbar-class.md#create) funkce nebo v [SetBarStyle](../mfc/reference/ccontrolbar-class.md#setbarstyle).  
  
-   Jak je popsáno v níže uvedeném postupu, připojí text tlačítka panelu nástrojů, oddělených znak nového řádku ("\n'), k prostředku řetězec obsahující řádku příkazového řádku pro příkaz panelu nástrojů. Řetězec prostředku sdílí ID tlačítka panelu nástrojů.  
  
#### <a name="to-add-the-tool-tip-text"></a>Chcete-li přidat text popisu nástroje  
  
1.  Při úpravách panelu nástrojů v editoru panelu nástrojů, otevřete **vlastnosti tlačítka panelu nástrojů** okna pro danou tlačítko.  
  
2.  V **výzva** zadejte text, který se má zobrazit v popisu tlačítka pro toto tlačítko.  
  
> [!NOTE]
>  Nastavení textu jako vlastnost tlačítka v editoru panelu nástrojů nahrazuje předchozí postup, ve kterém jste museli otevírat a upravovat řetězec prostředku.  
  
 Pokud ovládací prvek panel s popisy povolené podřízené ovládací prvky umístěny na něm, ovládacích pruhů zobrazí popis tlačítka pro každý podřízený ovládací prvek na ovládacím panelu tak dlouho, dokud splňuje následující kritéria:  
  
-   ID ovládacího prvku se - 1.  
  
-   Tabulky řetězců záznam se stejným ID jako podřízený ovládací prvek v souboru prostředků nemá řetězec tip nástroj.  
  
##  <a name="_core_fly_by_status_bar_updates"></a> Aktualizace průběžné stavového řádku  
 Funkce související s popisy je "průběžné" stavovém řádku aktualizace. Ve výchozím nastavení zpráva na stavovém řádku popisuje pouze konkrétní tlačítko panelu nástrojů, když se aktivuje tlačítko. Cbrs_flyby – Pokud uvedete v seznamu styly předaný `CToolBar::Create`, může mít tyto zprávy, když myší prochází přes panelu nástrojů bez aktivace ve skutečnosti na tlačítko Aktualizovat.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Implementace panelu nástrojů v prostředí MFC (Přehled informací na panely nástrojů)](../mfc/mfc-toolbar-implementation.md)  
  
-   [Ukotvitelné a plovoucí panely nástrojů](../mfc/docking-and-floating-toolbars.md)  
  
-   [Ctoolbar –](../mfc/reference/ctoolbar-class.md) a [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) třídy  
  
-   [Práce s ovládacím prvkem panel nástrojů](../mfc/working-with-the-toolbar-control.md)  
  
-   [Použití starých panelů nástrojů](../mfc/using-your-old-toolbars.md)  
  
## <a name="see-also"></a>Viz také  
 [Implementace panelu nástrojů v prostředí MFC](../mfc/mfc-toolbar-implementation.md)

