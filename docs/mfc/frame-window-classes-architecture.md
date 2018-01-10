---
title: "Třídy oken (Architektura) s rámečkem | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.frame
dev_langs: C++
helpviewer_keywords: frame window classes [MFC], document/view architecture
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f1caf8e4b93e18675b810ced962df6e8adcf521a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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

