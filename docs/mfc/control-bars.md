---
title: Ovládací pruhy
ms.date: 11/04/2016
helpviewer_keywords:
- command bars [MFC], types of
- toolbars [MFC], control bars
- control bars [MFC]
- MFC, control bars
- control bars [MFC], types of
- CDialogBar class [MFC], control bars
- status bars [MFC], control bars
- CControlBar class [MFC], MFC control bars
- dialog bars [MFC], control bars
- CToolBar class [MFC], control bars
- CStatusBar class [MFC], control bars
ms.assetid: 31831910-3d23-4d70-9e71-03cc02f01ec4
ms.openlocfilehash: 4b75d9a96f091d0424592f34bdb1ed7ce76c2372
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283576"
---
# <a name="control-bars"></a>Ovládací pruhy

"Ovládací prvek panel" je obecný název pro dialogové pruhy, panely nástrojů a stavové řádky. MFC – třídy `CToolBar`, `CStatusBar`, `CDialogBar`, `COleResizeBar`, a `CReBar` odvozen od třídy [ccontrolbar –](../mfc/reference/ccontrolbar-class.md), který implementuje své běžné funkce.

Ovládací pruhy jsou windows, které zobrazují řádků ovládacích prvků, pomocí kterých můžete uživatele vyberte možnosti, spusťte příkazy nebo získat informace o programu. Typy ovládacích pruhů zahrnují panely nástrojů, dialogové pruhy a stavové řádky.

- Panely nástrojů ve třídě [ctoolbar –](../mfc/reference/ctoolbar-class.md)

- Stavové řádky, ve třídě [cstatusbar –](../mfc/reference/cstatusbar-class.md)

- Dialogové pruhy ve třídě [CDialogBar](../mfc/reference/cdialogbar-class.md)

- Rebars ve třídě [crebar –](../mfc/reference/crebar-class.md)

> [!IMPORTANT]
>  MFC verze 4.0, panely nástrojů, stavovém řádku a nástroje jsou implementovány pomocí funkce systému, které jsou implementované v tipy *comctl32.dll* místo předchozích implementacích specifické pro knihovny MFC. V prostředí MFC verze 6.0 `CReBar`, což také zahrnuje funkce knihovny comctl32.dll, která byla přidána.

Postupujte podle stručné úvodní informace k typům ovládacích panelů. Další informace najdete na odkazech níže.

## <a name="control-bars"></a>Ovládací pruhy

Ovládací pruhy výrazně zlepšují použitelnost programu tím, že poskytuje rychlé, jednoduchý příkaz akce. Třída `CControlBar` poskytuje běžné funkce panely nástrojů, stavovém řádku a dialogové pruhy. `CControlBar` poskytuje funkce pro umístění panelu ovládacího prvku v jeho nadřazenému oknu rámce. Protože ovládací panel, je obvykle podřízené okno nadřazené okno rámce, je na "stejné" k zobrazení klienta nebo klienta MDI okna rámce. Objekt ovládacích panelů používá informace o jeho nadřazenému oknu klientský obdélník k umístění samotný. Poté změní nadřazeného objektu zbývající obdélník okno klienta tak, aby zobrazení klientů nebo okno klienta MDI vyplnil zbývající část okna klienta.

> [!NOTE]
>  Pokud už se tlačítko na panelu ovládacího prvku **příkaz** nebo **UPDATE_COMMAND_UI** obslužnou rutinu, rozhraní automaticky zakáže tlačítko.

## <a name="toolbars"></a>Panely nástrojů

Panel nástrojů se ovládací panel, který zobrazuje řádek tlačítek s rastrovými obrázky, provádět příkazy. Stisknutím tlačítka panelu nástrojů je ekvivalentem možnosti vybrání položky nabídky; volá obslužnou rutinu stejné namapované na položku nabídky, pokud tuto položku nabídky má stejné ID jako tlačítko panelu nástrojů. Tlačítka lze nastavit na a chovají se jako tlačítek, přepínacích tlačítek nebo zaškrtávací políčka. Panel nástrojů je obvykle zarovnán do horní části okna rámce, ale knihovny MFC nástrojů můžete "dock" na žádné straně její nadřazené okno nebo plovoucí desetinnou čárkou v samostatném okně okna s minirámcem. Panel nástrojů můžete také "float" a můžete změnit jeho velikost a přetažením myší. Panel nástrojů můžete také zobrazit popisy tlačítek, jak uživatel přesouvá ukazatel myši nad tlačítka panelu nástrojů. Popisku tlačítka je malý automaticky otevíraném okně, která stručně popisuje účel tlačítka.

> [!NOTE]
>  Od verze 4.0 knihovna MFC, třídy [ctoolbar –](../mfc/reference/ctoolbar-class.md) používá Windows běžné ovládací prvek panelu nástrojů. A `CToolBar` obsahuje [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md). Starší panely nástrojů jsou nadále podporován. Přečtěte si článek [panely nástrojů](../mfc/mfc-toolbar-implementation.md).

## <a name="status-bars"></a>Stavové řádky

Stavový řádek je ovládací panel, který obsahuje podoken textového výstupu nebo "ukazatelů". Výstupní podokna se obvykle používají jako zprávy řádky a indikátory stavu. Zpráva řádku Příklady příkazových řádků zprávu nápovědy, které stručně popisují vybrané nabídky nebo panelu nástrojů příkazu v podokně úplně vlevo ve stavovém řádku výchozí vytvořené průvodcem aplikací MFC. Stav indikátoru příklady SCROLL LOCK a NUM LOCK, další klíče. Stavové řádky jsou obvykle zarovnány k dolnímu okraji okna rámce. Viz třída [cstatusbar –](../mfc/reference/cstatusbar-class.md) a třída [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md).

## <a name="dialog-bars"></a>Dialogové pruhy

Panel dialogového okna se ovládací panel, založené na prostředek šablony dialogového okna s funkcemi nemodální dialogové okno. Dialogové pruhy může obsahovat Windows, nebo vlastní ovládací prvky ActiveX. Stejně jako v dialogovém okně vytvořit kartu uživatele mezi ovládacími prvky. Dialogové pruhy lze zarovnávat na horní, dolní, levé nebo pravé straně okna rámce a může být také obtékané ve své vlastní okna rámce. Viz třída [CDialogBar](../mfc/reference/cdialogbar-class.md).

## <a name="rebars"></a>Rebars

A [matrice](../mfc/using-crebarctrl.md) se ovládací panel, který poskytuje informace o ukotvení, rozložení, stavu a trvalosti pro prvky matrice. Matrice objekt může obsahovat řadu podřízených oken, obvykle další ovládací prvky, včetně textových polí, panely nástrojů a pole se seznamem. Objekt matrice můžete zobrazit jeho podřízených oken přes zadané rastrový obrázek. To může automaticky nebo ručně změnit velikost můžete také kliknout nebo přetažením jeho úchytu panelu. Viz třída [crebar –](../mfc/reference/crebar-class.md).

## <a name="see-also"></a>Viz také:

[Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)
