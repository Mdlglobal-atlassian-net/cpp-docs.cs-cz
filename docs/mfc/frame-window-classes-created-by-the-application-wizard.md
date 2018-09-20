---
title: Třídy oken s rámečkem vytvořené průvodcem aplikací | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CMainFrame
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aff98636c723de17056f4bef337b46f4a686ddec
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420605"
---
# <a name="frame-window-classes-created-by-the-application-wizard"></a>Třídy oken s rámečkem vytvořené průvodcem aplikací

Při použití [Průvodce aplikací](../ide/creating-desktop-projects-by-using-application-wizards.md) vytvoření kostru aplikace, kromě aplikace, dokumentů a zobrazení tříd, Průvodce aplikací vytvoří třídu odvozenou oken s rámečkem pro okna hlavního rámce aplikace. Třída se nazývá `CMainFrame` ve výchozím nastavení a soubory, které obsahují jsou pojmenovány MAINFRM. H a MAINFRM. CPP.

Pokud je vaše aplikace SDI, vaše `CMainFrame` třída je odvozena od třídy [CFrameWnd](../mfc/reference/cframewnd-class.md).

Pokud je vaše aplikace MDI, `CMainFrame` je odvozena z třídy [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md). V tomto případě `CMainFrame` implementuje hlavního rámce, který obsahuje nabídky, nástrojů a stavové řádky. Průvodce aplikací neodvozuje nové třídy oken s rámečkem dokumentu pro vás. Místo toho používá výchozí implementace v [CMDIChildWnd – třída](../mfc/reference/cmdichildwnd-class.md). Rozhraní MFC vytvoří podřízené okno tak, aby obsahovala každé zobrazení (které můžou být typu `CScrollView`, `CEditView`, `CTreeView`, `CListView`, a tak dále), která aplikace požaduje. Pokud potřebujete přizpůsobit okna rámce dokumentu, můžete vytvořit nové dokumentové třídy oken s rámečkem (viz [přidání třídy](../ide/adding-a-class-visual-cpp.md)).

Pokud se rozhodnete pro podporu nástrojů, má také třída členské proměnné typu [ctoolbar –](../mfc/reference/ctoolbar-class.md) a [cstatusbar –](../mfc/reference/cstatusbar-class.md) a `OnCreate` obslužná rutina zprávy funkce lze inicializovat dvou [ ovládací prvek pruhy](../mfc/control-bars.md).

Tyto třídy oken s rámečkem práci při vytváření, ale k rozšíření svých funkcí, je nutné přidat členské proměnné a členské funkce. Také můžete chtít mít třídy okna zpracovávat dalších zpráv Windows. Další informace najdete v tématu [změna stylů okna vytvořeného rozhraním MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md).

## <a name="see-also"></a>Viz také

[Třídy oken s rámečkem](../mfc/frame-window-classes.md)<br/>
[Program knihovny MFC nebo zdroj ovládacího prvku a soubory hlaviček](../ide/mfc-program-or-control-source-and-header-files.md)

