---
title: "Zpracování zpráv s oznámením ovládacího prvku karta | Microsoft Docs"
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
- notifications [MFC], tab controls
- CTabCtrl class [MFC], processing notifications
- notifications [MFC], processing in CTabCtrl
- processing notifications [MFC]
- tab controls [MFC], processing notifications
ms.assetid: 758ccb7a-9e73-48f8-9073-23f7cb09918c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 840ff6fc5dd47a2059e62608b5a5d6f231f8f17c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="processing-tab-control-notification-messages"></a>Zpracování zpráv s oznámením ovládacího prvku karta
Jak uživatelé kliknou na kartách nebo tlačítka, ovládacího prvku karta ([CTabCtrl](../mfc/reference/ctabctrl-class.md)) odešle zprávy s oznámením jeho nadřazeného okna. Tyto zprávy zpracování, pokud chcete, aby dělala něco v odpovědi. Když uživatel klikne na kartě, můžete chtít přednastavení data ovládacího prvku na stránce před jejich zobrazením.  
  
 Proces **wm_notify –** zprávy z ovládacího prvku karta ve třídě zobrazení nebo dialogové okno. Okno Vlastnosti použít k vytvoření [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) funkce obslužná rutina s příkazem přepínač podle zpráv oznámení, které se právě zpracovává. Seznam oznámení ovládacího prvku karta může odesílat do jeho nadřazeného okna najdete v tématu **oznámení** části [ovládací prvek karty](http://msdn.microsoft.com/library/windows/desktop/bb760548) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTabCtrl](../mfc/using-ctabctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

