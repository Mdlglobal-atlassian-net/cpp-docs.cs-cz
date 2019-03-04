---
title: Popisy tlačítek na panelu nástrojů
ms.date: 11/04/2016
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
ms.openlocfilehash: 4582b03844e1be3d4cf70bcc3fff1c3b66119ae3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57258356"
---
# <a name="toolbar-tool-tips"></a>Popisy tlačítek na panelu nástrojů

Popisy tlačítek jsou velmi malé zobrazována místní okna, které představují krátký popis tlačítka panelu nástrojů účel když umístíte ukazatel myši nad tlačítko pro určitou dobu. Když vytvoříte aplikaci pomocí Průvodce aplikací s panelem nástrojů, nástroj tip podpora se poskytuje pro vás. Tento článek vysvětluje i nástroj tip podporu vytvořené v Průvodci aplikace a jak přidat nástroj pro tip podporu pro vaši aplikaci.

Tento článek se týká:

- [Aktivace popisů tlačítek](#_core_activating_tool_tips)

- [Aktualizace stavového řádku](#_core_fly_by_status_bar_updates)

##  <a name="_core_activating_tool_tips"></a> Aktivace popisů tlačítek

Chcete-li aktivovat popisů tlačítek v aplikaci, musíte udělat dvě věci:

- Přidat styl CBRS_TOOLTIPS se styly (jako je například WS_CHILD, WS_VISIBLE a další **CBRS_** styly) předá jako *dwStyle* parametr [CToolBar::Create](../mfc/reference/ctoolbar-class.md#create) funkce nebo v [SetBarStyle](../mfc/reference/ccontrolbar-class.md#setbarstyle).

- Jak je popsáno v níže uvedeného postupu, připojte text tipu nástrojů, oddělených znakem nového řádku ('\n'), k prostředku řetězců obsahující příkazového řádku pro příkaz nástrojů. Prostředek řetězce sdílí Identifikátor panelu nástrojů.

#### <a name="to-add-the-tool-tip-text"></a>Chcete-li přidat text tipu nástroj

1. Při úpravách panelu nástrojů v editoru panelu nástrojů, otevřete **vlastnosti tlačítka panelu nástrojů** okna pro daný tlačítko.

1. V **výzvy** zadejte text, které se mají zobrazit v popisu tlačítka pro tlačítko.

> [!NOTE]
>  Nastavení textu jako vlastnosti tlačítka panelu nástrojů editoru nahradí předchozí postup, ve kterém jste museli otevírat a upravovat prostředek řetězce.

Pokud ovládací panel s popisy tlačítek povolené má podřízené ovládací prvky umístěné na to, bude ovládací panel zobrazení popisu tlačítka pro každý podřízený ovládací prvek na ovládacím panelu tak dlouho, dokud splňuje následující kritéria:

- ID ovládacího prvku se - 1.

- Vstupní tabulka řetězců se stejným ID jako podřízený ovládací prvek v souboru prostředků má tip řetězec nástroje.

##  <a name="_core_fly_by_status_bar_updates"></a> Aktualizace stavového stavového řádku

Funkce související s popisy tlačítek je "stavového" stavového řádku aktualizace. Ve výchozím nastavení zprávy ve stavovém řádku popisuje pouze konkrétní tlačítka při aktivaci na tlačítko. Zahrnutím CBRS_FLYBY ve vašem seznamu styly předán `CToolBar::Create`, může mít tyto zprávy při kurzoru myši přetahovaného panelu nástrojů bez aktivace ve skutečnosti na tlačítko Aktualizovat.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Implementace panelu nástrojů v prostředí MFC (Přehled informací na panely nástrojů)](../mfc/mfc-toolbar-implementation.md)

- [Ukotvitelné a plovoucí panely nástrojů](../mfc/docking-and-floating-toolbars.md)

- [Ctoolbar –](../mfc/reference/ctoolbar-class.md) a [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) třídy

- [Práce s ovládacím prvkem panel nástrojů](../mfc/working-with-the-toolbar-control.md)

- [Použití starých panelů nástrojů](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>Viz také:

[Implementace panelu nástrojů v prostředí MFC](../mfc/mfc-toolbar-implementation.md)
