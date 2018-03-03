---
title: "Posouvání a změna měřítka zobrazení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- message handlers [MFC]
- scaling views [MFC]
- message handling [MFC], scroll bars in view class [MFC]
- scroll bars [MFC], messages
- scrolling views [MFC]
ms.assetid: f98a3421-c336-407e-97ee-dbb2ffd76fbd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f8bd42a7da91f984c4cedc4deafc0ab9f4417495
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="scrolling-and-scaling-views"></a>Posouvání a změna měřítka zobrazení
MFC podporuje zobrazení, která přejděte a zobrazení, které jsou automaticky škálovat na velikost rámec okna, který je zobrazí. Třída `CScrollView` podporuje oba typy zobrazení.  
  
 Další informace o posouvání a změna měřítka najdete v tématu třídy [CScrollView](../mfc/reference/cscrollview-class.md) v *odkaz knihovny MFC*. Posouvání příklad najdete v tématu [Scribble ukázka](../visual-cpp-samples.md).  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   Posouvání zobrazení  
  
-   Změna měřítka zobrazení  
  
-   [Souřadnice zobrazení](http://msdn.microsoft.com/library/windows/desktop/dd145205)  
  
##  <a name="_core_scrolling_a_view"></a>Posouvání zobrazení  
 Často je větší než velikost, kterou můžete zobrazit jeho zobrazení velikost dokumentu. To může dojít, protože data dokumentu zvyšuje nebo uživatel zmenší okno zobrazení, kterou. V takových případech musí podporovat zobrazení posouvání.  
  
 Všechna zobrazení dokáže zpracovat zprávy posuvníku v jeho `OnHScroll` a `OnVScroll` členské funkce. Můžete buď zpracování implementace posuvníku zpráv v tyto funkce, díky všechnu práci sami nebo můžete použít `CScrollView` třídy pro zpracování posouvání za vás.  
  
 `CScrollView`provede následující akce:  
  
-   Spravuje mapování režimy a velikosti oken a zobrazení  
  
-   Posouvá automaticky v odpovědi na zprávy posuvníku  
  
 Kolik můžete zadat posun "stránky" (když uživatel klikne na posuvníku hřídel) a "řádek" (když uživatel klikne na posouvací šipky). Naplánujte tyto hodnoty tak, aby vyhovovala povaha zobrazení. Například můžete chtít posuňte se v přírůstcích po 1 pixel pro zobrazení grafiky, ale v přírůstcích po založené na výšku řádku textu dokumentů.  
  
##  <a name="_core_scaling_a_view"></a>Změna měřítka zobrazení  
 Pokud chcete, aby zobrazení automaticky přizpůsobit velikost okna jeho rámečku, můžete použít `CScrollView` pro škálování místo posouvání. Logické zobrazení je roztažen tak nebo zmenšit, přesně podle okna klientské oblasti. Škálovat. zobrazení nemá žádné posuvníky.  
  
## <a name="see-also"></a>Viz také  
 [Použití zobrazení](../mfc/using-views.md)

