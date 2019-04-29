---
title: Třídy oken s rámečkem (architektura)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.frame
helpviewer_keywords:
- frame window classes [MFC], document/view architecture
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
ms.openlocfilehash: affa217f481cc6d9e125d526f1b97be9120e0990
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392840"
---
# <a name="frame-window-classes-architecture"></a>Třídy oken s rámečkem (architektura)

Okna s rámečkem v architektuře document/view jsou okna obsahující okno zobrazení. Podporují také ovládací prvek s pruhy, které jsou připojené k nim.

Ve více aplikacích dokumentů (MDI) interface, hlavní okno pochází z `CMDIFrameWnd`. Nepřímo obsahuje snímky v dokumentech, které jsou `CMDIChildWnd` objekty. `CMDIChildWnd` Objekty, pak obsahují zobrazení v dokumentech.

V aplikacích rozhraní (SDI) jeden dokument, hlavní okno odvozené od `CFrameWnd`, obsahuje zobrazení aktuálního dokumentu.

[CFrameWnd](../mfc/reference/cframewnd-class.md)<br/>
Základní třída pro okna hlavního rámce aplikace SDI. Také základní třída pro všechny ostatní třídy oken s rámečkem.

[CMDIFrameWnd –](../mfc/reference/cmdiframewnd-class.md)<br/>
Základní třída pro aplikace MDI hlavní okno rámce.

[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)<br/>
Základní třída pro aplikace MDI oken s rámečkem v dokumentu.

[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)<br/>
Pokud dokument na serveru je upravována v místě, poskytuje okno rámce pro zobrazení.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../mfc/class-library-overview.md)
