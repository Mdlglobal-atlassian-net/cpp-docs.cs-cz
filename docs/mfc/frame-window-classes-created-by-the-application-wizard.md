---
title: Třídy oken s rámečkem vytvořené průvodcem aplikací
ms.date: 11/04/2016
f1_keywords:
- CMainFrame
helpviewer_keywords:
- application wizards [MFC], frame window classes created by
- window classes [MFC]
- classes [MFC], frame-window
- CMDIFrameWnd class [MFC], frame windows
- window classes [MFC], frame
- CFrameWnd class [MFC], frame windows
- CMDIChildWnd class [MFC], frame windows
- frame window classes [MFC], created by application wizards
- CMainFrame class [MFC]
ms.assetid: 9947df73-4470-49a0-ac61-7b6ee401a74e
ms.openlocfilehash: c17ba2b6dd79e8e62baa29bba403c136d16a0d95
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077536"
---
# <a name="frame-window-classes-created-by-the-application-wizard"></a>Třídy oken s rámečkem vytvořené průvodcem aplikací

Když vytváříte nový projekt knihovny MFC z dialogového okna **Nový projekt** , kromě tříd aplikace, dokumentu a zobrazení, vytvoří Průvodce aplikací odvozenou třídu okna pro hlavní rámec vaší aplikace. Třída se ve výchozím nastavení nazývá `CMainFrame` a soubory, které ji obsahují, mají název MAINFRM. H a MAINFRM. CPP.

Pokud je vaše aplikace SDI, vaše `CMainFrame` třída je odvozena od třídy [CFrameWnd](../mfc/reference/cframewnd-class.md).

Pokud je vaše aplikace MDI, `CMainFrame` je odvozena ze třídy [CMDIFrameWnd –](../mfc/reference/cmdiframewnd-class.md). V tomto případě `CMainFrame` implementuje hlavní rámec, který obsahuje nabídku, panel nástrojů a stavové řádky. Průvodce aplikací neodvozuje pro vás novou třídu oken s rámcem dokumentu. Místo toho používá výchozí implementaci ve [třídě CMDIChildWnd –](../mfc/reference/cmdichildwnd-class.md). Rozhraní MFC Framework vytvoří podřízené okno obsahující každé zobrazení (které může být typu `CScrollView`, `CEditView`, `CTreeView`, `CListView`a tak dále), které aplikace vyžaduje. Pokud potřebujete přizpůsobit okno rámce dokumentu, můžete vytvořit novou třídu okna s rámcem dokumentu (viz [Přidání třídy](../ide/adding-a-class-visual-cpp.md)).

Pokud se rozhodnete podporovat panel nástrojů, třída má také členské proměnné typu [CToolBar –](../mfc/reference/ctoolbar-class.md) a [CStatusBar –](../mfc/reference/cstatusbar-class.md) a funkci obslužné rutiny zpráv `OnCreate` k inicializaci dvou [ovládacích panelů](../mfc/control-bars.md).

Tyto třídy oken s rámečkem fungují jako vytvořené, ale pro vylepšení jejich funkcí je nutné přidat členské proměnné a členské funkce. Můžete také chtít, aby vaše třídy oken zpracovávala jiné zprávy systému Windows. Další informace naleznete v tématu [Změna stylů okna vytvořeného pomocí knihovny MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md).

## <a name="see-also"></a>Viz také

[Třídy oken s rámečkem](../mfc/frame-window-classes.md)<br/>
[Program knihovny MFC nebo zdroj ovládacího prvku a soubory hlaviček](../build/reference/mfc-program-or-control-source-and-header-files.md)
