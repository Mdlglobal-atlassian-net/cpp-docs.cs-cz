---
title: Zpracování zpráv s oznámením v ovládacích prvcích seznam | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- processing notifications [MFC]
- CListCtrl class [MFC], processing notifications
ms.assetid: 1f0e296e-d2a3-48fc-ae38-51d7fb096f51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3362074ce0f8d4d7a3a3463d22f9089f847e747d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43208707"
---
# <a name="processing-notification-messages-in-list-controls"></a>Zpracování zpráv s oznámením v ovládacích prvcích seznamů
Jak uživatelé kliknou na záhlaví sloupců, přetáhněte ikony, Upravit popisky a tak dále, ovládacího prvku seznam ([CListCtrl](../mfc/reference/clistctrl-class.md)) odesílá zprávy s oznámením nezašle nadřazenému oknu. Tyto zprávy zpracovávají, pokud budete chtít udělat něco v odpovědi. Když uživatel klikne na záhlaví sloupce, můžete chtít řadit položky podle obsahu kliknutí na sloupec, stejně jako v aplikaci Microsoft Outlook.  
  
 Zpracovat wm_notify – zprávy z ovládacího prvku seznam ve třídě zobrazení nebo dialogového okna. Okno Vlastnosti použít k vytvoření [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) funkci obslužné rutiny pomocí příkazu switch podle zpráv oznámení, které se právě zpracovává.  
  
 Seznam oznámení ovládacího prvku seznamu můžete poslat nezašle nadřazenému oknu, naleznete v tématu [odkaz na ovládací prvek zobrazení seznamu](/windows/desktop/Controls/list-view-control-reference) v sadě Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CListCtrl](../mfc/using-clistctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

