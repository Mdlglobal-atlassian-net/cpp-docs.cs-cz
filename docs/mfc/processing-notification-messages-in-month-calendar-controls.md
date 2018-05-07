---
title: Zpracování zpráv s oznámením v měsíci ovládacím prvku Kalendář | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CMonthCalCtrl class [MFC], notifications
- CMonthCalCtrl class [MFC], day states
- month calendar controls [MFC], notification messages
- notifications [MFC], for CMonthCalCtrl
- notifications [MFC], month calendar control
ms.assetid: 607c3e90-0756-493b-9503-ce835a50c7ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 26b4d73284b0cff362ba16248e0906b76c7f52a1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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

