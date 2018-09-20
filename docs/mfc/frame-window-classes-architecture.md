---
title: Snímků tříd oken (Architektura) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.frame
dev_langs:
- C++
helpviewer_keywords:
- frame window classes [MFC], document/view architecture
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 117554b2c34853aa166c12d80b4821d3721e5992
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394124"
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

