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
ms.openlocfilehash: 0c6691f37a1b0754835aba5c09d251c4986c4fb1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50592536"
---
# <a name="updating-the-text-of-a-status-bar-pane"></a>Aktualizace textu na panelu stavového řádku

Tento článek vysvětluje, jak změnit text, který se zobrazí panelu stavového řádku stav knihovny MFC. Stavový řádek – vytvoření objektu třídy okna [cstatusbar –](../mfc/reference/cstatusbar-class.md) – obsahuje několik "podokna." Každé podokno je obdélníkovou oblast, ve stavovém řádku, který můžete použít k zobrazení informací. Například mnoho aplikací zobrazit stav CAPS LOCK a NUM LOCK, další klíče v podoknech úplně vpravo. Aplikace také často zobrazit informativní text v podokně úplně vlevo (podokno 0), někdy označuje jako "podokně zpráv." Například výchozí knihovny MFC stavový řádek používá podokně zprávy pro zobrazení řetězce s vysvětlením, aktuálně vybraný položka nabídky nebo panelu nástrojů tlačítko. Obrázek v [stavové řádky](../mfc/status-bar-implementation-in-mfc.md) ukazuje stavový řádek z aplikace vytvoří Průvodce aplikací knihovny MFC.

Ve výchozím nastavení, neumožňuje knihovny MFC `CStatusBar` podokně, když se vytvoří v podokně. Pokud chcete aktivovat na stavového řádku, musíte použít ON_UPDATE_COMMAND_UI – makro pro každé podokno ve stavovém řádku a aktualizace podokna. Protože podokna Neodesílat wm_command – zprávy (nejsou jako tlačítka na panelu nástrojů), je nutné zadat kód ručně.

Předpokládejme například, že obsahuje jedno podokno `ID_INDICATOR_PAGE` i jeho identifikátor příkazu, který obsahuje aktuální číslo stránky v dokumentu. Následující postup popisuje, jak vytvořit nové podokno ve stavovém řádku.

### <a name="to-make-a-new-pane"></a>Aby se nové podokno

1. Definování v podokně ID příkazu.

   Na **zobrazení** nabídky, klikněte na tlačítko **zobrazení prostředků**. Klikněte pravým tlačítkem na projekt prostředků a klikněte na tlačítko **symbolů prostředků**. V dialogovém okně symbolů prostředků klikněte na tlačítko `New`. Zadejte název ID příkazu: například `ID_INDICATOR_PAGE`. Zadejte hodnotu pro ID nebo přijmout hodnotu navrhovanou v dialogovém okně symbolů prostředků. Například pro `ID_INDICATOR_PAGE`, přijměte výchozí hodnotu. Symboly prostředků dialogové okno zavřete.

1. Definujte výchozí řetězec k zobrazení v podokně.

   Otevřít zobrazení prostředků, poklepejte na **tabulka řetězců** v okně, které jsou uvedeny typy prostředků pro vaši aplikaci. S **tabulka řetězců** editor otevřít, zvolte **nový řetězec** z **vložit** nabídky. V okně Vlastnosti řetězce vyberte ID do podokna příkazu (například `ID_INDICATOR_PAGE`) a zadejte výchozí hodnotu řetězce, jako je například "Stránky". Zavřete editor řetězců. (Budete potřebovat výchozí řetězec, aby se zabránilo chybu kompilátoru.)

1. Přidat podokně tak, aby *indikátory* pole.

   V souboru MAINFRM. CPP, vyhledejte *indikátory* pole. Toto pole obsahuje ID příkazu pro všechny indikátory stavového řádku v pořadí zleva doprava. V odpovídajícím bodě v poli zadejte ID do podokna příkazu, jak je znázorněno zde pro `ID_INDICATOR_PAGE`:

   [!code-cpp[NVC_MFCDocView#10](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_1.cpp)]

Doporučeným způsobem zobrazování textu v podokně se má volat `SetText` členské funkce třídy `CCmdUI` ve funkci obslužné rutiny aktualizace podokna. Například můžete chtít nastavit proměnnou celého čísla *m_nPage* obsahující číslo aktuální stránky a použijte `SetText` nastavit text v podokně na řetězec verze tohoto čísla.

> [!NOTE]
>  `SetText` Přístup se doporučuje. Je možné provést tuto úlohu trochu nižší úrovni pomocí volání `CStatusBar` členskou funkci `SetPaneText`. I tak stále je nutné obslužnou rutinu aktualizace. Bez těchto obslužnou rutinu pro podokno MFC automaticky zakáže v podokně mazání jeho obsah.

Následující postup ukazuje, jak používat funkci obslužné rutiny aktualizace k zobrazení textu v podokně.

#### <a name="to-make-a-pane-display-text"></a>Chcete-li do podokna zobrazení textu

1. Přidáte aktualizace obslužná rutina příkazu pro příkaz.

   Ručně přidejte prototyp obslužné rutiny, jak je znázorněno zde pro `ID_INDICATOR_PAGE` (v MAINFRM. H):

   [!code-cpp[NVC_MFCDocView#11](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_2.h)]

1. Do odpovídajícího. CPP přidejte obslužnou rutinu definice, jak je znázorněno zde pro `ID_INDICATOR_PAGE` (v MAINFRM. CPP):

   [!code-cpp[NVC_MFCDocView#12](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_3.cpp)]

   Poslední tři řádky z této obslužné rutiny jsou kód, který zobrazí text.

1. Na mapě odpovídající zprávu přidat ON_UPDATE_COMMAND_UI – makro, jak je znázorněno zde pro `ID_INDICATOR_PAGE` (v MAINFRM. CPP):

   [!code-cpp[NVC_MFCDocView#13](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_4.cpp)]

Jakmile definujete hodnotu *m_nPage* členské proměnné (třídy `CMainFrame`), tento postup způsobí, že číslo stránky, v podokně se zobrazí během zpracování při nečinnosti stejným způsobem, že aplikace aktualizuje další indikátory. Pokud *m_nPage* změn, změny zobrazení během další nečinné smyčky.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Aktualizace objektů uživatelského rozhraní (jak aktualizovat tlačítka na panelu nástrojů a položky v nabídce jako změnit podmínky programu)](../mfc/how-to-update-user-interface-objects.md)

## <a name="see-also"></a>Viz také

[Implementace stavového řádku v prostředí MFC](../mfc/status-bar-implementation-in-mfc.md)<br/>
[CStatusBar – třída](../mfc/reference/cstatusbar-class.md)
