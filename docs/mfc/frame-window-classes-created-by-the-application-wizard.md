---
title: Třídy oken s rámečkem vytvořené průvodcem aplikací | Microsoft Docs
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
ms.openlocfilehash: d3446de072266fdf7661d2e8d8ca0fc968279646
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33345039"
---
# <a name="frame-window-classes-created-by-the-application-wizard"></a>Třídy oken s rámečkem vytvořené průvodcem aplikací
Při použití [– Průvodce aplikací](../ide/creating-desktop-projects-by-using-application-wizards.md) k vytvoření kostru aplikace, kromě aplikací, dokumentů a zobrazení třídy, vytvoří průvodce třídu odvozenou oken s rámečkem hlavního rámce okna aplikace. Třídy se nazývá `CMainFrame` ve výchozím nastavení a soubory, které ji obsahují jsou pojmenované MAINFRM. H a MAINFRM. CPP.  
  
 Pokud je vaše aplikace SDI, vaše `CMainFrame` třída je odvozena od třídy [CFrameWnd](../mfc/reference/cframewnd-class.md).  
  
 Pokud je vaše aplikace MDI, `CMainFrame` je odvozená od třídy [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md). V takovém případě `CMainFrame` implementuje hlavního rámce, který obsahuje řádky nabídky panelu nástrojů a stav. Průvodce aplikace neodvozuje nové třídy oken s rámečkem dokumentu pro vás. Místo toho použije výchozí implementace v [CMDIChildWnd – třída](../mfc/reference/cmdichildwnd-class.md). Rozhraní MFC framework vytvoří podřízeného okna tak, aby obsahovala jednotlivých zobrazení (může být typu `CScrollView`, `CEditView`, `CTreeView`, `CListView`a tak dále), aplikace vyžaduje. Pokud potřebujete přizpůsobit vaší rámce okna dokumentu, můžete vytvořit nové třídy oken s rámečkem dokumentu (viz [přidání třídy](../ide/adding-a-class-visual-cpp.md)).  
  
 Pokud si zvolíte pro podporu panelu nástrojů, třída také obsahuje členské proměnné typu [ctoolbar –](../mfc/reference/ctoolbar-class.md) a [cstatusbar –](../mfc/reference/cstatusbar-class.md) a `OnCreate` funkce obslužné rutiny zpráv k chybě při inicializaci dva [ řízení řádky](../mfc/control-bars.md).  
  
 Tyto třídy oken s rámečkem fungovat, jak byl vytvořen, ale pokud chcete zvýšit jejich funkce, je nutné přidat členské proměnné a členské funkce. Můžete také mít vaší třídy oken, zpracování dalších zpráv systému Windows. Další informace najdete v tématu [změna stylů okna vytvořeného rozhraním MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md).  
  
## <a name="see-also"></a>Viz také  
 [Třídy oken s rámečkem](../mfc/frame-window-classes.md)   
 [Program knihovny MFC nebo zdroj ovládacího prvku a soubory hlaviček](../ide/mfc-program-or-control-source-and-header-files.md)

