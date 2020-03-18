---
title: Třídy oken s rámečkem (architektura)
ms.date: 11/04/2016
helpviewer_keywords:
- frame window classes [MFC], document/view architecture
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
ms.openlocfilehash: e3ae432c1adc881a5c67d6a6c292dc1f6a583ab3
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441252"
---
# <a name="frame-window-classes-architecture"></a>Třídy oken s rámečkem (architektura)

V architektuře Document/View jsou okna oken s rámečkem okna obsahující okno zobrazení. Také podporují řídicí panely, které jsou k nim připojeny.

V aplikacích MDI (Multiple Document Interface) je hlavní okno odvozeno od `CMDIFrameWnd`. Nepřímo obsahuje rámečky dokumentů, které jsou `CMDIChildWnd` objekty. `CMDIChildWnd` objekty zase obsahují zobrazení Documents.

V aplikacích rozhraní Single Document Interface (SDI) hlavní okno odvozené z `CFrameWnd`obsahuje zobrazení aktuálního dokumentu.

[CFrameWnd](../mfc/reference/cframewnd-class.md)<br/>
Základní třída pro hlavní okno rámce aplikace SDI. Také základní třída pro všechny ostatní třídy oken s rámečkem.

[CMDIFrameWnd –](../mfc/reference/cmdiframewnd-class.md)<br/>
Základní třída okna hlavního rámce aplikace MDI.

[CMDIChildWnd –](../mfc/reference/cmdichildwnd-class.md)<br/>
Základní třída pro okna rámce dokumentu aplikace MDI.

[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)<br/>
Poskytuje okno rámce pro zobrazení při upravovaném dokumentu serveru.

## <a name="see-also"></a>Viz také

[Přehled třídy](../mfc/class-library-overview.md)
