---
title: Zpracování zpráv s oznámením v ovládacích prvcích seznam | Microsoft Docs
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
ms.openlocfilehash: c5412bbf1fcb7e139394b9563965244080e5c179
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932078"
---
# <a name="processing-notification-messages-in-list-controls"></a>Zpracování zpráv s oznámením v ovládacích prvcích seznamů
Jak uživatelé kliknou na záhlaví sloupců, přetáhněte ikony, Upravit popisky a tak dále, ovládacího prvku seznam ([CListCtrl](../mfc/reference/clistctrl-class.md)) odešle zprávy s oznámením jeho nadřazeného okna. Tyto zprávy zpracování, pokud chcete, aby dělala něco v odpovědi. Po kliknutí na záhlaví sloupce, můžete chtít řadit položky na základě obsahu kliknutelnou sloupce, jako v aplikaci Microsoft Outlook.  
  
 Proces wm_notify – zprávy z ovládacího prvku seznam ve třídě zobrazení nebo dialogové okno. Okno Vlastnosti použít k vytvoření [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) funkce obslužná rutina s příkazem přepínač podle zpráv oznámení, které se právě zpracovává.  
  
 Seznam oznámení ovládací prvek seznamu, můžete odeslat do jeho nadřazeného okna najdete v tématu [odkaz ovládacího prvku zobrazení seznamu](http://msdn.microsoft.com/library/windows/desktop/bb774737) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CListCtrl](../mfc/using-clistctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

