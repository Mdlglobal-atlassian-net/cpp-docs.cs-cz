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
ms.openlocfilehash: ceae20c89d9a6d3f4393f838b3594938107785f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353575"
---
# <a name="control-bars"></a>Ovládací pruhy

Ovládací panel je obecný název panelů nástrojů, stavových pruhů a dialogových panelů. Třídy `CToolBar`knihovny `CDialogBar` `COleResizeBar`MFC `CReBar` , `CStatusBar`, , a odvozují z třídy [CControlBar](../mfc/reference/ccontrolbar-class.md), která implementuje jejich běžné funkce.

Ovládací panely jsou okna, která zobrazují řádky ovládacích prvků, pomocí kterých mohou uživatelé vybírat možnosti, spouštět příkazy nebo získávat informace o programu. Mezi typy ovládacích panelů patří panely nástrojů, dialogové panely a stavové panely.

- Panely nástrojů ve třídě [CToolBar](../mfc/reference/ctoolbar-class.md)

- Stavové panely ve třídě [CStatusBar](../mfc/reference/cstatusbar-class.md)

- Dialogová okna ve třídě [CDialogBar](../mfc/reference/cdialogbar-class.md)

- Výztuži, ve třídě [CReBar](../mfc/reference/crebar-class.md)

> [!IMPORTANT]
> Od knihovny MFC verze 4.0 jsou panely nástrojů, stavové panely a tipy nástrojů implementovány pomocí funkcí systému implementovaných v *comctl32.dll* namísto předchozí implementace specifické pro knihovnu MFC. V knihovně MFC `CReBar`verze 6.0 byla přidána funkce comctl32.dll , která také zalomí funkci comctl32.dll.

Následují stručné úvody k typům ovládacích panelů. Další informace naleznete v níže uvedených odkazech.

## <a name="control-bars"></a>Ovládací pruhy

Ovládací panely výrazně zvyšují použitelnost programu tím, že poskytují rychlé akce příkazů v jednom kroku. Třída `CControlBar` poskytuje běžné funkce všech panelů nástrojů, stavových panelů a dialogových panelů. `CControlBar`poskytuje funkce pro umístění ovládacího panelu v jeho nadřazeném okně rámce. Vzhledem k tomu, že ovládací panel je obvykle podřízeným oknem nadřazeného okna rámce, jedná se o "na stejné úrovni" pro zobrazení klienta klienta nebo klienta MDI okna rámce. Objekt ovládacího panelu používá informace o obdélníku klienta nadřazeného okna k umístění sebe sama. Potom změní nadřazený obdélník zbývající klient-okno tak, aby zobrazení klienta nebo okno klienta MDI vyplní zbytek okna klienta.

> [!NOTE]
> Pokud tlačítko na ovládacím panelu nemá obslužnou rutinu **PŘÍKAZ** nebo **UPDATE_COMMAND_UI,** rozhraní automaticky zakáže tlačítko.

## <a name="toolbars"></a>Panely nástrojů

Panel nástrojů je ovládací panel, který zobrazuje řadu bitmapovaných tlačítek, která provádějí příkazy. Stisknutí tlačítka panelu nástrojů je ekvivalentní výběru položky nabídky; volá stejnou obslužnou rutinu mapovanou na položku nabídky, pokud má tato položka nabídky stejné ID jako tlačítko panelu nástrojů. Tlačítka lze nakonfigurovat tak, aby se zobrazovala a chovala se jako tlačítka, přepínací tlačítka nebo zaškrtávací políčka. Panel nástrojů je obvykle zarovnán k horní části okna rámce, ale panel nástrojů knihovny MFC může "ukotvit" na libovolnou stranu nadřazeného okna nebo plovoucí ve vlastním okně minirámečku. Panel nástrojů může také "plovoucí" a můžete změnit jeho velikost a přetáhnout ji myší. Panel nástrojů může také zobrazit tipy nástrojů, když uživatel pohybuje myší nad tlačítky panelu nástrojů. Tip nástroje je malé vyskakovací okno, které stručně popisuje účel tlačítka.

> [!NOTE]
> Od knihovny MFC verze 4.0 používá panel nástrojů [CToolBar](../mfc/reference/ctoolbar-class.md) třídy běžný ovládací prvek panelu nástrojů systému Windows. A `CToolBar` obsahuje [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md). Starší panely nástrojů jsou však stále podporovány. Viz článek [Panely nástrojů](../mfc/mfc-toolbar-implementation.md).

## <a name="status-bars"></a>Stavové řádky

Stavový řádek je ovládací panel, který obsahuje podokna výstupu textu nebo indikátory. Výstupní podokna se běžně používají jako řádky zpráv a jako indikátory stavu. Příklady řádků zprávy zahrnují řádky nápovědy příkazu, které stručně vysvětlují vybranou nabídku nebo příkaz panelu nástrojů v levém podokně výchozího stavového řádku vytvořeného Průvodcem aplikací knihovny MFC. Mezi příklady indikátorů stavu patří SCROLL LOCK, NUM LOCK a další klávesy. Stavové pruhy jsou obvykle zarovnány ke spodní části okna rámce. Viz třída [CStatusBar](../mfc/reference/cstatusbar-class.md) a třída [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md).

## <a name="dialog-bars"></a>Dialogové pruhy

Dialogové okno je ovládací panel založený na prostředku šablony dialogového okna s funkcemi nemodálního dialogového okna. Dialogová panelová panelová panelová okna mohou obsahovat ovládací prvky systému Windows, vlastní nebo ActiveX. Stejně jako v dialogovém okně může uživatel mezi ovládacími prvky tabulátorem. Dialogové čáry mohou být zarovnány k horní, dolní, levé nebo pravé straně okna rámečku a mohou být také plovoucí ve vlastním okně rámečku. Viz třída [CDialogBar](../mfc/reference/cdialogbar-class.md).

## <a name="rebars"></a>Zpřísněná tyčí

[Výztuže](../mfc/using-crebarctrl.md) je ovládací panel, který poskytuje informace o ukotvení, rozložení, stavu a trvalosti pro ovládací prvky výztuže. Objekt výztuže může obsahovat různé podřízené oken, obvykle další ovládací prvky, včetně editačních polí, panelů nástrojů a seznamů. Objekt výztuže může zobrazit podřízená okna přes zadanou bitmapu. Lze ji automaticky nebo ručně nastavit kliknutím nebo přetažením úchopné tyče. Viz třída [CReBar](../mfc/reference/crebar-class.md).

## <a name="see-also"></a>Viz také

[Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)
