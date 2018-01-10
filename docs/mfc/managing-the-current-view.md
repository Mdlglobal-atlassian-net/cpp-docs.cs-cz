---
title: "Správa aktuálního zobrazení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- views [MFC], and OnActivateView method [MFC]
- views [MFC], deactivating
- views [MFC], activating
- frame windows [MFC], current view
- OnActivateView method [MFC]
- views [MFC], current
- deactivating views [MFC]
- current view in frame window [MFC]
ms.assetid: 0a1cc22d-d646-4536-9ad2-3cb6d7092e4a
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e1510b005f452174acfe8ad65ae3f66cf8aafaa2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="managing-the-current-view"></a>Správa aktuálního zobrazení
Jako součást výchozí implementaci třídy oken s rámečkem uchovává informace okně s rámečkem o aktuálně aktivní zobrazení. Pokud okně s rámečkem obsahuje více než jedno zobrazení, jako například v rozděleném okně, je aktuální zobrazení poslední zobrazení používá. Aktivní zobrazení je nezávislé na aktivní okno v systému Windows nebo aktuální zaměření pro vstup.  
  
 Při aktivním zobrazení změní, rozhraní upozorní aktuální zobrazení voláním jeho [OnActivateView](../mfc/reference/cview-class.md#onactivateview) – členská funkce. Můžete zjistit, zda zobrazení se aktivace nebo deaktivace prověřením `OnActivateView`na `bActivate` parametr. Ve výchozím nastavení `OnActivateView` nastaví fokus na aktuální zobrazení na aktivaci. Můžete přepsat `OnActivateView` provádět žádné zvláštní zpracování, pokud je zobrazení deaktivovala nebo znovu aktivovat. Můžete například chtít zadat speciální vizuální upozornění k rozlišení aktivní zobrazení z jiných, neaktivní zobrazení.  
  
 Okně s rámečkem předá příkazy na jeho aktuální zobrazení (aktivní), jak je popsáno v [směrování příkazů](../mfc/command-routing.md), jako součást standardního směrování příkazů.  
  
## <a name="see-also"></a>Viz také  
 [Použití oken s rámečkem](../mfc/using-frame-windows.md)

