---
title: Zpracování zpráv s oznámením ovládacího prvku karta | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- notifications [MFC], tab controls
- CTabCtrl class [MFC], processing notifications
- notifications [MFC], processing in CTabCtrl
- processing notifications [MFC]
- tab controls [MFC], processing notifications
ms.assetid: 758ccb7a-9e73-48f8-9073-23f7cb09918c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6ce59bfe298798d4574bf158998e989c4a6af62c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="processing-tab-control-notification-messages"></a>Zpracování zpráv s oznámením ovládacího prvku karta
Jak uživatelé kliknou na kartách nebo tlačítka, ovládacího prvku karta ([CTabCtrl](../mfc/reference/ctabctrl-class.md)) odešle zprávy s oznámením jeho nadřazeného okna. Tyto zprávy zpracování, pokud chcete, aby dělala něco v odpovědi. Když uživatel klikne na kartě, můžete chtít přednastavení data ovládacího prvku na stránce před jejich zobrazením.  
  
 Proces **wm_notify –** zprávy z ovládacího prvku karta ve třídě zobrazení nebo dialogové okno. Okno Vlastnosti použít k vytvoření [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) funkce obslužná rutina s příkazem přepínač podle zpráv oznámení, které se právě zpracovává. Seznam oznámení ovládacího prvku karta může odesílat do jeho nadřazeného okna najdete v tématu **oznámení** části [ovládací prvek karty](http://msdn.microsoft.com/library/windows/desktop/bb760548) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTabCtrl](../mfc/using-ctabctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

