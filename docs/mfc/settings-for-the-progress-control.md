---
title: "Nastavení pro ovládací prvek průběh | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CProgressCtrl class [MFC], settings
- progress controls [MFC], settings
ms.assetid: f4616e91-74fa-4000-ba0d-d3ddc0ee075b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1ad62f3a60c8fe4fcd7efdde7f69f5c5e9450d14
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="settings-for-the-progress-control"></a>Nastavení pro ovládací prvek průběh
Základní nastavení pro ovládací prvek průběh ([CProgressCtrl](../mfc/reference/cprogressctrl-class.md)) jsou rozsah a aktuální pozici. Rozsah představuje celou dobu trvání operace. Aktuální pozice představuje proces, který vaše aplikace změněn směrem k dokončení operace. Při změně rozsah nebo pozice dojde k překreslit ovládací prvek průběh.  
  
 Ve výchozím nastavení, je nastaven rozsah 0 - 100 a počáteční pozice nastavena na hodnotu 0. Chcete-li načíst aktuální rozsah nastavení pro ovládací prvek průběh, použijte [getrange –](../mfc/reference/cprogressctrl-class.md#getrange) – členská funkce. Chcete-li změnit rozsah, použijte [SetRange](../mfc/reference/cprogressctrl-class.md#setrange) – členská funkce.  
  
 Pokud chcete nastavit pozici, použijte [SetPos](../mfc/reference/cprogressctrl-class.md#setpos). Načíst aktuální pozici bez zadání nové hodnoty, použijte [GetPos](../mfc/reference/cprogressctrl-class.md#getpos). Například můžete chtít jednoduše zadat dotaz na stav aktuální operace.  
  
 Chcete-li krok aktuální pozici ovládací prvek průběh, použijte [StepIt](../mfc/reference/cprogressctrl-class.md#stepit). Pokud chcete nastavit velikost jednotlivých kroků, použijte [SetStep](../mfc/reference/cprogressctrl-class.md#setstep)  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CProgressCtrl](../mfc/using-cprogressctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

