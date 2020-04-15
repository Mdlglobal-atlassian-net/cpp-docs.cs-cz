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
ms.openlocfilehash: 723046fc1721cc46608e00f19a4431ef081be13d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366694"
---
# <a name="updating-the-text-of-a-status-bar-pane"></a>Aktualizace textu na panelu stavového řádku

Tento článek vysvětluje, jak změnit text, který se zobrazí v podokně stavového řádku knihovny MFC. Stavový řádek – objekt okna třídy [CStatusBar](../mfc/reference/cstatusbar-class.md) – obsahuje několik "podoken". Každé podokno je obdélníková oblast stavového řádku, kterou lze použít k zobrazení informací. Mnoho aplikací například zobrazuje stav CAPS LOCK, NUM LOCK a dalších kláves v podokně zcela vpravo. Aplikace také často zobrazují informativní text v levém podokně (podokno 0), někdy nazývaném "podokno zpráv". Například výchozí stavový řádek knihovny MFC používá podokno zpráv k zobrazení řetězce vysvětlujícího aktuálně vybranou položku nabídky nebo tlačítko panelu nástrojů. Obrázek ve [stavových stavových stavových panelech](../mfc/status-bar-implementation-in-mfc.md) zobrazuje stavový řádek z aplikace MFC vytvořené Průvodcem aplikací.

Ve výchozím nastavení knihovna `CStatusBar` MFC nepovolí podokno při vytváření podokna. Chcete-li podokno aktivovat, je nutné použít ON_UPDATE_COMMAND_UI makro pro každé podokno na stavovém řádku a aktualizovat podokna. Vzhledem k tomu, že podokna neodesílají WM_COMMAND zprávy (nejsou jako tlačítka panelu nástrojů), je nutné zadat kód ručně.

Předpokládejme například, `ID_INDICATOR_PAGE` že jedno podokno má jako svůj identifikátor příkazu a že obsahuje aktuální číslo stránky v dokumentu. Následující postup popisuje, jak vytvořit nové podokno ve stavovém řádku.

### <a name="to-make-a-new-pane"></a>Vytvoření nového podokna

1. Definujte ID příkazu podokna.

   V nabídce **View** klepněte na **položku Zobrazení zdrojů**. Klepněte pravým tlačítkem myši na zdroj projektu a klepněte na příkaz **Symboly zdrojů**. V dialogovém okně Symboly prostředků klepněte na tlačítko `New`. Zadejte název ID příkazu: `ID_INDICATOR_PAGE`například . Zadejte hodnotu ID nebo přijměte hodnotu navrženou v dialogovém okně Symboly prostředků. Například pro `ID_INDICATOR_PAGE`, přijmout výchozí hodnotu. Zavřete dialogové okno Symboly prostředků.

1. Definujte výchozí řetězec, který se zobrazí v podokně.

   Po otevření zobrazení prostředků poklikejte v okně, ve které jsou uvedeny typy prostředků pro vaši aplikaci, **poklikejte na tabulku řetězců.** Když je editor **tabulky řetězců** otevřený, zvolte **Nový řetězec** z nabídky **Vložit.** Vyberte ID příkazu podokna `ID_INDICATOR_PAGE`(například) a zadejte výchozí hodnotu řetězce, například "Stránka ". Zavřete editor řetězců. (Potřebujete výchozí řetězec, abyste se vyhnuli chybě kompilátoru.)

1. Přidejte podokno do pole *indikátorů.*

   V souboru MAINFRM. CPP, vyhledejte pole *indikátorů.* Toto pole obsahuje id příkazů pro všechny indikátory stavového řádku v pořadí zleva doprava. V příslušném bodě pole zadejte ID příkazu podokna, `ID_INDICATOR_PAGE`jak je znázorněno zde pro :

   [!code-cpp[NVC_MFCDocView#10](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_1.cpp)]

Doporučeným způsobem zobrazení textu v podokně `SetText` je volání `CCmdUI` členské funkce třídy v funkci obslužné rutiny aktualizace pro podokno. Můžete například nastavit celou proměnnou *m_nPage,* která obsahuje aktuální číslo `SetText` stránky, a použít k nastavení textu podokna na řetězcovou verzi tohoto čísla.

> [!NOTE]
> Tento `SetText` přístup se doporučuje. Je možné provést tento úkol na mírně nižší `CStatusBar` úrovni `SetPaneText`voláním členské funkce . I tak stále potřebujete obslužnou rutinu aktualizace. Bez takové obslužné rutiny pro podokno knihovna MFC automaticky zakáže podokno a vymaže jeho obsah.

Následující postup ukazuje, jak pomocí funkce obslužné rutiny aktualizace zobrazit text v podokně.

#### <a name="to-make-a-pane-display-text"></a>Vytvoření textu v podokně

1. Přidejte obslužnou rutinu aktualizace příkazu pro příkaz.

   Ručně přidejte prototyp obslužné `ID_INDICATOR_PAGE` rutiny, jak je znázorněno zde (v MAINFRM. H):

   [!code-cpp[NVC_MFCDocView#11](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_2.h)]

1. V příslušném . CPP, přidejte definici obslužné `ID_INDICATOR_PAGE` rutiny, jak je znázorněno zde (v MAINFRM. CPP):

   [!code-cpp[NVC_MFCDocView#12](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_3.cpp)]

   Poslední tři řádky této obslužné rutiny jsou kód, který zobrazuje text.

1. Do příslušné mapy zpráv přidejte ON_UPDATE_COMMAND_UI makro, `ID_INDICATOR_PAGE` jak je znázorněno zde (v MAINFRM. CPP):

   [!code-cpp[NVC_MFCDocView#13](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_4.cpp)]

Jakmile definujete hodnotu *m_nPage* členské proměnné `CMainFrame`(třídy ), tato technika způsobí, že číslo stránky se zobrazí v podokně během nečinnosti zpracování stejným způsobem, že aplikace aktualizuje další ukazatele. Pokud *m_nPage* změní, zobrazení se změní během další smyčky nečinnosti.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o

- [Aktualizace objektů uživatelského rozhraní (jak aktualizovat tlačítka panelu nástrojů a položky nabídky při změně podmínek programu)](../mfc/how-to-update-user-interface-objects.md)

## <a name="see-also"></a>Viz také

[Implementace stavového řádku v prostředí MFC](../mfc/status-bar-implementation-in-mfc.md)<br/>
[CStatusBar – třída](../mfc/reference/cstatusbar-class.md)
