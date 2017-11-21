---
title: "Popisy tlačítek panelu nástrojů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f597d0058e008f1adf1cb366f163594ef4b7472a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="toolbar-tool-tips"></a>Popisy tlačítek na panelu nástrojů
Popisy jsou velmi malé místní windows, která představují krátký popis tlačítka panelu nástrojů účel při umístit ukazatel myši nad tlačítko pro určitou dobu. Když vytvoříte aplikaci pomocí Průvodce aplikací, který má panel nástrojů, nástroj tip podpora je k dispozici pro vás. Tento článek vysvětluje, jak nástroj tip podporu vytvořené v Průvodce vytvořením aplikace a jak přidat nástroj pro podporu tip do vaší aplikace.  
  
 Tento článek se zabývá:  
  
-   [Aktivace popisů tlačítek](#_core_activating_tool_tips)  
  
-   [Průběžné aktualizace stavového řádku](#_core_fly_by_status_bar_updates)  
  
##  <a name="_core_activating_tool_tips"></a>Aktivace popisů tlačítek  
 Chcete-li aktivovat popisů tlačítek v aplikaci, musíte udělat dvě věci:  
  
-   Přidat `CBRS_TOOLTIPS` styl jiných stylů (například **ws_child –**, **ws_visible –**a dalších **CBRS_** styly) předán jako `dwStyle` parametru [ CToolBar::Create](../mfc/reference/ctoolbar-class.md#create) funkce nebo v [SetBarStyle](../mfc/reference/ccontrolbar-class.md#setbarstyle).  
  
-   Jak je popsáno v níže uvedeném postupu, připojí text tlačítka panelu nástrojů, oddělených znak nového řádku ("\n'), k prostředku řetězec obsahující řádku příkazového řádku pro příkaz panelu nástrojů. Řetězec prostředku sdílí ID tlačítka panelu nástrojů.  
  
#### <a name="to-add-the-tool-tip-text"></a>Chcete-li přidat text popisu nástroje  
  
1.  Při úpravách panelu nástrojů v editoru panelu nástrojů, otevřete **vlastnosti tlačítka panelu nástrojů** okna pro danou tlačítko.  
  
2.  V **výzva** zadejte text, který se má zobrazit v popisu tlačítka pro toto tlačítko.  
  
> [!NOTE]
>  Nastavení textu jako vlastnost tlačítka v editoru panelu nástrojů nahrazuje předchozí postup, ve kterém jste museli otevírat a upravovat řetězec prostředku.  
  
 Pokud ovládací prvek panel s popisy povolené podřízené ovládací prvky umístěny na něm, ovládacích pruhů zobrazí popis tlačítka pro každý podřízený ovládací prvek na ovládacím panelu tak dlouho, dokud splňuje následující kritéria:  
  
-   ID ovládacího prvku se - 1.  
  
-   Tabulky řetězců záznam se stejným ID jako podřízený ovládací prvek v souboru prostředků nemá řetězec tip nástroj.  
  
##  <a name="_core_fly_by_status_bar_updates"></a>Aktualizace průběžné stavového řádku  
 Funkce související s popisy je "průběžné" stavovém řádku aktualizace. Ve výchozím nastavení zpráva na stavovém řádku popisuje pouze konkrétní tlačítko panelu nástrojů, když se aktivuje tlačítko. Zahrnutím `CBRS_FLYBY` ve vašem seznamu styly předaný `CToolBar::Create`, může mít tyto zprávy, když myší prochází přes panelu nástrojů bez aktivace ve skutečnosti na tlačítko Aktualizovat.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Implementace panelu nástrojů v prostředí MFC (Přehled informací na panely nástrojů)](../mfc/mfc-toolbar-implementation.md)  
  
-   [Ukotvitelné a plovoucí panely nástrojů](../mfc/docking-and-floating-toolbars.md)  
  
-   [Ctoolbar –](../mfc/reference/ctoolbar-class.md) a [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) třídy  
  
-   [Práce s ovládacím prvkem panel nástrojů](../mfc/working-with-the-toolbar-control.md)  
  
-   [Použití starých panelů nástrojů](../mfc/using-your-old-toolbars.md)  
  
## <a name="see-also"></a>Viz také  
 [Implementace panelu nástrojů v MFC](../mfc/mfc-toolbar-implementation.md)

