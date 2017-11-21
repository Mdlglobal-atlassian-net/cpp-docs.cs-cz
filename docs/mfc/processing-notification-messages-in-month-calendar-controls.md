---
title: "Zpracování zpráv s oznámením v měsíci ovládacím prvku Kalendář | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CMonthCalCtrl class [MFC], notifications
- CMonthCalCtrl class [MFC], day states
- month calendar controls [MFC], notification messages
- notifications [MFC], for CMonthCalCtrl
- notifications [MFC], month calendar control
ms.assetid: 607c3e90-0756-493b-9503-ce835a50c7ab
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d775d1f27be328a27e9b4bc843e1780a8efb02ad
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="processing-notification-messages-in-month-calendar-controls"></a>Zpracování zpráv s oznámením v ovládacím prvku měsíční kalendář
Jak uživatelé pracují s ovládacím prvku měsíční kalendář (Výběr data a/nebo zobrazení na jiný měsíc), ovládacího prvku (`CMonthCalCtrl`) odešle zprávy s oznámením do nadřazeného okna, obvykle objekt zobrazení nebo dialogové okno. Tyto zprávy zpracování, pokud chcete, aby dělala něco v odpovědi. Například pokud uživatel vybere na nový měsíc, chcete-li zobrazit, je možné zadat sadu kalendářních dat, které by měl být zdůrazňují.  
  
 Okno Vlastnosti použijte pro přidání obslužné rutiny oznamovacích do nadřazené třídy pro ty zprávy, které chcete implementovat.  
  
 Následující seznam popisuje různé oznámení zaslaná z ovládací prvek měsíční kalendář.  
  
-   **Mcn_getdaystate –** vyžaduje informace o tom, které by měl být dny zobrazeny tučně. Informace o zpracování toto oznámení, naleznete v části [nastavení stavu dne ovládací prvek měsíční kalendář](../mfc/setting-the-day-state-of-a-month-calendar-control.md).  
  
-   **MCN_SELCHANGE** upozorní nadřazeného objektu, který došlo ke změně vybrané datum nebo rozsah data.  
  
-   **MCN_SELECT** upozorní nadřazeného objektu, který provedl se výběru explicitní data.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

