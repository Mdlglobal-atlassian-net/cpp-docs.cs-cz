---
title: Třídy oken s rámečkem (architektura)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.frame
helpviewer_keywords:
- frame window classes [MFC], document/view architecture
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
ms.openlocfilehash: d1022d9a49e12585a6588e7b3202155f533e4706
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431704"
---
# <a name="frame-window-classes-architecture"></a>Třídy oken s rámečkem (architektura)

Okna s rámečkem v architektuře document/view jsou okna obsahující okno zobrazení. Podporují také ovládací prvek s pruhy, které jsou připojené k nim.

Ve více aplikacích dokumentů (MDI) interface, hlavní okno pochází z `CMDIFrameWnd`. Nepřímo obsahuje snímky v dokumentech, které jsou `CMDIChildWnd` objekty. `CMDIChildWnd` Objekty, pak obsahují zobrazení v dokumentech.

V aplikacích rozhraní (SDI) jeden dokument, hlavní okno odvozené od `CFrameWnd`, obsahuje zobrazení aktuálního dokumentu.

[CFrameWnd](../mfc/reference/cframewnd-class.md)<br/>
Základní třída pro okna hlavního rámce aplikace SDI. Také základní třída pro všechny ostatní třídy oken s rámečkem.

[CMDIFrameWnd –](../mfc/reference/cmdiframewnd-class.md)<br/>
Základní třída pro aplikace MDI hlavní okno rámce.

[CMDIChildWnd –](../mfc/reference/cmdichildwnd-class.md)<br/>
Základní třída pro aplikace MDI oken s rámečkem v dokumentu.

[Coleipframewnd –](../mfc/reference/coleipframewnd-class.md)<br/>
Pokud dokument na serveru je upravována v místě, poskytuje okno rámce pro zobrazení.

## <a name="see-also"></a>Viz také

[Přehled tříd](../mfc/class-library-overview.md)

