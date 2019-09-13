---
title: Aktualizace textu na panelu stavového řádku
ms.date: 11/04/2016
helpviewer_keywords:
- updating user interface objects [MFC]
- ON_UPDATE_COMMAND_UI macro [MFC]
- user interface objects [MFC], updating
- text, status bar
- CStatusBar class [MFC], updating
- SetText method [MFC]
- panes, status bar
- status bars [MFC], updating
ms.assetid: 4984a3f4-9905-4d8c-a927-dca19781053b
ms.openlocfilehash: 20cd519f15fa9b218bca3dd1348659cfd0d5e473
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907641"
---
# <a name="updating-the-text-of-a-status-bar-pane"></a>Aktualizace textu na panelu stavového řádku

Tento článek vysvětluje, jak změnit text, který se zobrazí v podokně stavového řádku knihovny MFC. Stavový řádek – objekt okna třídy [CStatusBar –](../mfc/reference/cstatusbar-class.md) -obsahuje několik "podoken". Každé podokno je obdélníková oblast stavového řádku, kterou můžete použít k zobrazení informací. Mnoho aplikací například zobrazuje stav Caps Lock, NUM LOCK a dalších klíčů v podoknech vpravo. Aplikace také často zobrazují informativní text v levém podokně (podokno 0), někdy se nazývá podokno zpráva. Například výchozí stavový řádek knihovny MFC používá podokno zpráva k zobrazení řetězce vysvětlujícího aktuálně vybranou položku nabídky nebo tlačítko na panelu nástrojů. Obrázek ve [stavovém](../mfc/status-bar-implementation-in-mfc.md) řádku zobrazuje stavový řádek z Průvodce aplikací – vytvořená aplikace MFC.

Ve výchozím nastavení knihovna MFC při vytváření podokna `CStatusBar` nepovolí podokno. Chcete-li aktivovat podokno, je nutné použít Makro ON_UPDATE_COMMAND_UI pro každé podokno na stavovém řádku a aktualizovat podokna. Vzhledem k tomu, že podokna neodesílají zprávy WM_COMMAND (nejedná se například o tlačítka panelu nástrojů), je nutné kód zadat ručně.

Předpokládejme například, že jedno podokno má `ID_INDICATOR_PAGE` jako identifikátor příkazu a že obsahuje aktuální číslo stránky v dokumentu. Následující postup popisuje, jak vytvořit nové podokno ve stavovém řádku.

### <a name="to-make-a-new-pane"></a>Vytvoření nového podokna

1. Zadejte ID příkazu v podokně.

   V nabídce **zobrazení** klikněte na příkaz **prostředky**. Klikněte pravým tlačítkem na prostředek projektu a klikněte na **symboly prostředků**. V dialogovém okně symboly prostředků klikněte na `New`. Zadejte název ID příkazu: například `ID_INDICATOR_PAGE`. Zadejte hodnotu pro ID nebo přijměte hodnotu navrženou v dialogovém okně symboly prostředků. Například pro `ID_INDICATOR_PAGE`použijte přijměte výchozí hodnotu. Zavřete dialogové okno symboly prostředků.

1. Definujte výchozí řetězec, který se zobrazí v podokně.

   Otevřete-li Prostředky otevřít, poklikejte na **tabulka řetězců** v okně, ve kterém jsou uvedeny typy prostředků pro vaši aplikaci. Otevřete Editor **tabulky řetězců** a v nabídce **Vložit** vyberte **nový řetězec** . Vyberte ID příkazu vašeho podokna (například `ID_INDICATOR_PAGE`) a zadejte výchozí hodnotu řetězce, například "stránka". Zavřete Editor řetězců. (K tomu, abyste se vyhnuli chybě kompilátoru, potřebujete výchozí řetězec.)

1. Přidejte podokno do pole *indikátory* .

   V souboru MAINFRM. CPP vyhledejte pole *indikátory* . V tomto poli jsou uvedena ID příkazů pro všechny indikátory stavového řádku v pořadí zleva doprava. V příslušném okamžiku v poli zadejte ID příkazu vašeho podokna, jak je znázorněno zde `ID_INDICATOR_PAGE`:

   [!code-cpp[NVC_MFCDocView#10](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_1.cpp)]

Doporučený způsob zobrazení textu v podokně je zavolat `SetText` členskou funkci třídy `CCmdUI` ve funkci obslužné rutiny aktualizace pro podokno. Například můžete chtít nastavit celočíselnou proměnnou *m_nPage* , která obsahuje číslo aktuální stránky a použít `SetText` k nastavení textu podokna na verzi řetězce daného čísla.

> [!NOTE]
>  Je `SetText` doporučený přístup. Tuto úlohu je možné provést na mírně nižší úrovni voláním `CStatusBar` členské funkce. `SetPaneText` I tak dál potřebujete obslužnou rutinu aktualizace. Bez takové obslužné rutiny pro podokno MFC automaticky zakáže podokno a mazání jeho obsahu.

Následující postup ukazuje, jak použít funkci obslužné rutiny aktualizace k zobrazení textu v podokně.

#### <a name="to-make-a-pane-display-text"></a>Nastavení zobrazení textu v podokně

1. Přidejte obslužnou rutinu aktualizace příkazu pro příkaz.

   Ručně přidejte prototyp pro obslužnou rutinu, jak je znázorněno `ID_INDICATOR_PAGE` zde pro (v mainfrm. H):

   [!code-cpp[NVC_MFCDocView#11](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_2.h)]

1. V příslušném případě. Soubor cpp, přidejte definici obslužné rutiny, jak je znázorněno `ID_INDICATOR_PAGE` zde pro (v mainfrm. CPP):

   [!code-cpp[NVC_MFCDocView#12](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_3.cpp)]

   Poslední tři řádky této obslužné rutiny jsou kód, který zobrazuje váš text.

1. V příslušném rozvržení zprávy přidejte Makro ON_UPDATE_COMMAND_UI, jak je znázorněno zde pro `ID_INDICATOR_PAGE` (v mainfrm. CPP):

   [!code-cpp[NVC_MFCDocView#13](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_4.cpp)]

Po definování hodnoty členské proměnné *m_nPage* (třídy `CMainFrame`) Tato technika způsobí, že se číslo stránky zobrazí v podokně během nečinnosti zpracování stejným způsobem, jakým aplikace aktualizuje jiné indikátory. Pokud *m_nPage* změny, zobrazení se během další nečinné smyčky změní.

### <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace

- [Aktualizace objektů uživatelského rozhraní (postup aktualizace tlačítek panelu nástrojů a položek nabídky jako změny podmínek programu)](../mfc/how-to-update-user-interface-objects.md)

## <a name="see-also"></a>Viz také:

[Implementace stavového řádku v prostředí MFC](../mfc/status-bar-implementation-in-mfc.md)<br/>
[CStatusBar – třída](../mfc/reference/cstatusbar-class.md)
