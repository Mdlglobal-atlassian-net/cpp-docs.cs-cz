---
title: "Ovládací pruhy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f3550043e5b85247d4188c830873099c6ea9831a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="control-bars"></a>Ovládací pruhy
"Ovládacích pruhů" je obecné název panely nástrojů, stavové řádky a řádky dialogové okno. MFC – třídy `CToolBar`, `CStatusBar`, `CDialogBar`, `COleResizeBar`, a **CReBar** odvozena od třídy [ccontrolbar –](../mfc/reference/ccontrolbar-class.md), který implementuje své běžné funkce.  
  
 Ovládací pruhy jsou windows, které zobrazují řádky ovládacích prvků, které uživatelé můžete vybrat možnosti, spuštěním příkazů nebo získat informace o programu. Typy ovládacích panelů zahrnují panely nástrojů, dialogové pruhy a stavové řádky.  
  
-   Panely nástrojů v třídě [ctoolbar –](../mfc/reference/ctoolbar-class.md)  
  
-   Stavové řádky v třídě [cstatusbar –](../mfc/reference/cstatusbar-class.md)  
  
-   Dialogové pruhy v třídě [CDialogBar](../mfc/reference/cdialogbar-class.md)  
  
-   Ve třídě tyčová ocel [CReBar](../mfc/reference/crebar-class.md)  
  
> [!IMPORTANT]
>  Od verze knihovny MFC verze 4.0 panely nástrojů, stavové řádky a popisy jsou implementovány pomocí funkce systému v souboru comctl32.dll místo předchozí implementace, které jsou specifické pro MFC. V prostředí MFC verze 6.0 **CReBar**, který také zahrnuje funkce comctl32.dll, byl přidán.  
  
 Postupujte podle stručný přehled typů ovládacích pruhů. Další informace najdete v tématu odkazy níže.  
  
## <a name="control-bars"></a>Ovládací pruhy  
 Ovládací pruhy výrazně zlepšují použitelnost programu tím, že poskytuje rychlé, jednoduchý příkaz akce. Třída `CControlBar` poskytuje běžné funkce všech panely nástrojů, stavové řádky a řádky dialogové okno. `CControlBar`poskytuje funkce pro umístění panelu ovládacího prvku v jeho nadřazeného rámce okna. Ovládací prvek panelu je obvykle podřízeného okna rámce okna nadřazené, proto je na "úrovni" do zobrazení klienta nebo klienta MDI rámce okna. Objekt ovládacího prvku panel používá informace o jeho nadřazeného okna klienta obdélníku na pozici sám sebe. Poté změní zbývající obdélníku okno klienta nadřazeného objektu, tak, aby zobrazení klienta nebo okna MDI klienta vyplnil zbytek okna klienta.  
  
> [!NOTE]
>  Pokud nemá na panelu Ovládací prvek tlačítko **příkaz** nebo **UPDATE_COMMAND_UI** obslužnou rutinu, rozhraní automaticky zakáže tlačítko.  
  
## <a name="toolbars"></a>Panely nástrojů  
 Panel nástrojů je ovládací prvek panel, který zobrazí řádek rastrové tlačítka, která provádět příkazy. Stisknutím tlačítka panelu nástrojů je ekvivalentem možnosti vybrání položku nabídky; volá obslužnou rutinu stejné namapované na položku nabídky, pokud daná položka nabídky má stejné ID jako tlačítka panelu nástrojů. Tlačítka lze nastavit zobrazit, a chovat jako tlačítek, přepínače nebo zaškrtávací políčka. Panel nástrojů je obvykle zarovnán do horní části okna rámce, ale panelu nástrojů MFC můžete "ukotvení" žádné straně jeho nadřazeného okna nebo float v samostatném okně zkrácená rámce. Panel nástrojů můžete také "float" a můžete změnit jeho velikost a přetáhněte ji myší. Panel nástrojů můžete také zobrazit popisy, jako přechodu myší přes tlačítka panelu nástrojů. Popis tlačítka je malá velikost automaticky otevíraném okně, který stručně popisuje účel na tlačítko.  
  
> [!NOTE]
>  Od verze knihovny MFC verze 4.0, třídy [ctoolbar –](../mfc/reference/ctoolbar-class.md) používá Windows běžné ovládací prvek panelu nástrojů. A `CToolBar` obsahuje [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md). Panely nástrojů starší jsou stále podporovány, ale. Najdete v článku [panely nástrojů](../mfc/mfc-toolbar-implementation.md).  
  
## <a name="status-bars"></a>Stavové řádky  
 Stavový řádek je ovládací prvek panel, který obsahuje podokna výstup textu nebo "indikátory." Podokna výstup běžně se používají jako řádky zprávy a jako indikátory stavu. Zpráva řádku Příklady příkazových řádků zprávu nápovědy, které stručně popisují vybrané nabídky nebo příkazu panelu nástrojů v podokně krajní levé stavového řádku výchozí vytvořené průvodcem aplikací MFC. Stav indikátoru příklady SCROLL LOCK NUMLOCK a jiných klíčů. Stavové řádky jsou obvykle zarovnán k dolnímu okraji okna rámce. Viz třída [cstatusbar –](../mfc/reference/cstatusbar-class.md) a třída [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md).  
  
## <a name="dialog-bars"></a>Dialogové pruhy  
 Panel dialogového okna je ovládacích pruhů, založené na prostředek šablony dialogového okna s funkcemi dialogového okna bez režimu. Dialogové pruhy může obsahovat Windows, nebo vlastní ovládací prvky ActiveX. V dialogovém okně může uživatel kartě mezi ovládacími prvky. Dialogové pruhy lze zarovnávat na nahoru, dolů, doleva nebo pravé straně okně s rámečkem a může být také obtékané ve svých vlastních oken s rámečkem. Viz třída [CDialogBar](../mfc/reference/cdialogbar-class.md).  
  
## <a name="rebars"></a>Tyčová ocel  
 A [matrice](../mfc/using-crebarctrl.md) je ovládací prvek panel, který obsahuje informace pro ovládací prvky matrice ukotvení, rozložení, stavu a trvalost. Objekt matrice může obsahovat celou řadu podřízená okna, obvykle další ovládací prvky, včetně polí úpravy, panely nástrojů a seznamy. Objekt matrice můžete zobrazit jeho podřízené systému windows přes zadané rastrového obrázku. Ji může automaticky nebo ručně změnit velikost kliknutím nebo přetažením jeho úchytu pruh. Viz třída [CReBar](../mfc/reference/crebar-class.md).  
  
## <a name="see-also"></a>Viz také  
 [Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)
