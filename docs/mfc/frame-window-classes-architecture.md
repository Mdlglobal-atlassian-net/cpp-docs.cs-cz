---
title: Třídy oken (Architektura) s rámečkem | Microsoft Docs
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
ms.openlocfilehash: b7de72b77be9be90ca876cfef943500a0312d183
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="frame-window-classes-architecture"></a>Třídy oken s rámečkem (architektura)
Okna s rámečkem v architektuře document/view jsou windows, které obsahují okno zobrazení. Také podporují s řízení řádky, které jsou připojené k nim.  
  
 V aplikacích rozhraní (MDI) více dokumentů, hlavní okno je odvozený od `CMDIFrameWnd`. Je nepřímo obsahuje rámce v dokumentech, které jsou `CMDIChildWnd` objekty. `CMDIChildWnd` Objekty, zase obsahovat v dokumentech zobrazeními.  
  
 (SDI rozhraní) aplikací s jedním dokumentem hlavní okno odvozené z `CFrameWnd`, obsahuje zobrazení aktuálního dokumentu.  
  
 [CFrameWnd](../mfc/reference/cframewnd-class.md)  
 Základní třída pro aplikace SDI hlavního rámce okna. Také základní třídu pro všechny ostatní třídy oken s rámečkem.  
  
 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)  
 Základní třída pro aplikace MDI hlavního rámce okna.  
  
 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)  
 Základní třída pro aplikace MDI okna s rámečkem dokumentu.  
  
 [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)  
 Poskytuje okně s rámečkem pro zobrazení, pokud server dokumentu upravována na místě.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../mfc/class-library-overview.md)

