---
title: "Zpracování zpráv s oznámením v ovládacích prvcích seznam | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- processing notifications [MFC]
- CListCtrl class [MFC], processing notifications
ms.assetid: 1f0e296e-d2a3-48fc-ae38-51d7fb096f51
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2c4a900b6fe0741de852c15afca37a974fc3e989
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="processing-notification-messages-in-list-controls"></a>Zpracování zpráv s oznámením v ovládacích prvcích seznamů
Jak uživatelé kliknou na záhlaví sloupců, přetáhněte ikony, Upravit popisky a tak dále, ovládacího prvku seznam ([CListCtrl](../mfc/reference/clistctrl-class.md)) odešle zprávy s oznámením jeho nadřazeného okna. Tyto zprávy zpracování, pokud chcete, aby dělala něco v odpovědi. Po kliknutí na záhlaví sloupce, můžete chtít řadit položky na základě obsahu kliknutelnou sloupce, jako v aplikaci Microsoft Outlook.  
  
 Proces **wm_notify –** zprávy z ovládacího prvku seznam ve třídě zobrazení nebo dialogové okno. Okno Vlastnosti použít k vytvoření [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) funkce obslužná rutina s příkazem přepínač podle zpráv oznámení, které se právě zpracovává.  
  
 Seznam oznámení ovládací prvek seznamu, můžete odeslat do jeho nadřazeného okna najdete v tématu [odkaz ovládacího prvku zobrazení seznamu](http://msdn.microsoft.com/library/windows/desktop/bb774737) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CListCtrl](../mfc/using-clistctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

