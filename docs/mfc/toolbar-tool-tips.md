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
ms.openlocfilehash: 1762931b75734801659fd6271377260bd0473614
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373462"
---
# <a name="toolbar-tool-tips"></a>Popisy tlačítek na panelu nástrojů

Tipy nástrojů jsou malá vyskakovací okna, která představují krátké popisy účelu tlačítka panelu nástrojů, když umístíte myš nad tlačítko po určitou dobu. Při vytváření aplikace pomocí Průvodce aplikací, který má panel nástrojů, je k dispozici podpora tipu nástroje. Tento článek vysvětluje podporu tipu nástroje vytvořenou Průvodcem aplikací a jak přidat podporu tipu nástroje do aplikace.

Tento článek se zabývá:

- [Aktivace tipů nástrojů](#_core_activating_tool_tips)

- [Aktualizace stavového řádku Flyby](#_core_fly_by_status_bar_updates)

## <a name="activating-tool-tips"></a><a name="_core_activating_tool_tips"></a>Aktivace tipů nástrojů

Chcete-li aktivovat tipy nástrojů v aplikaci, musíte udělat dvě věci:

- Přidejte styl CBRS_TOOLTIPS do jiných stylů (například WS_CHILD, WS_VISIBLE a dalších **stylů CBRS_)** předaných jako parametr *dwStyle* do [funkce CToolBar::Create](../mfc/reference/ctoolbar-class.md#create) nebo v [SetBarStyle](../mfc/reference/ccontrolbar-class.md#setbarstyle).

- Jak je popsáno v postupu níže, přidejte text tipu panelu nástrojů oddělený znakem nového řádku (\n' k prostředku řetězce obsahujícího výzvu příkazového řádku pro příkaz panelu nástrojů. Řetězec prostředek sdílí ID tlačítka panelu nástrojů.

#### <a name="to-add-the-tool-tip-text"></a>Přidání textu tipu nástroje

1. Při úpravách panelu nástrojů v editoru panelu nástrojů otevřete okno **Vlastnosti tlačítka panelu nástrojů** pro dané tlačítko.

1. Do pole **Výzva** zadejte text, který se má zobrazit v tipu nástroje pro toto tlačítko.

> [!NOTE]
> Nastavení vlastnosti textu jako tlačítka v editoru panelu nástrojů nahradí dřívější postup, ve kterém bylo třeba otevřít a upravit prostředek řetězce.

Pokud je na ovládacím panelu s povolenými hroty nástrojů umístěny podřízené ovládací prvky, zobrazí se na ovládacím panelu špička nástroje pro každý podřízený ovládací prvek na ovládacím panelu, pokud splňuje následující kritéria:

- ID ovládacího prvku není - 1.

- Položka tabulky řetězců se stejným ID jako podřízený ovládací prvek v souboru prostředků má řetězec tip nástroje.

## <a name="flyby-status-bar-updates"></a><a name="_core_fly_by_status_bar_updates"></a>Aktualizace stavového řádku Flyby

Funkce související s tipy nástrojů je aktualizace stavového řádku "průlet". Ve výchozím nastavení zpráva na stavovém řádku popisuje pouze určité tlačítko panelu nástrojů při aktivaci tlačítka. Zahrnutím CBRS_FLYBY do seznamu `CToolBar::Create`stylů předaných do aplikace můžete tyto zprávy aktualizovat, když kurzor myši přejde přes panel nástrojů, aniž by skutečně aktivoval tlačítko.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o

- [Implementace panelu nástrojů knihovny MFC (přehled informací o panelech nástrojů)](../mfc/mfc-toolbar-implementation.md)

- [Dokovací a plovoucí panely nástrojů](../mfc/docking-and-floating-toolbars.md)

- [Třídy CToolBar](../mfc/reference/ctoolbar-class.md) a [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)

- [Práce s ovládacím prvkem panelu nástrojů](../mfc/working-with-the-toolbar-control.md)

- [Používání starých panelů nástrojů](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>Viz také

[Implementace panelu nástrojů v prostředí MFC](../mfc/mfc-toolbar-implementation.md)
