---
title: "Zpracování oznamovacích zpráv v výběr data a času ovládací prvky | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DTN_CLOSEUP
- DTN_DATETIMECHANGE
- DTN_DROPDOWN
dev_langs:
- C++
helpviewer_keywords:
- DTN_DROPDOWN notification [MFC]
- DTN_DATETIMECHANGE notification [MFC]
- DTN_CLOSEUP notification [MFC]
- DateTimePicker control [MFC], handling notifications
- CDateTimeCtrl class [MFC], handling notifications
- DTN_FORMAT notification [MFC]
- DateTimePicker control [MFC]
ms.assetid: ffbe29ab-ff80-4609-89f7-260b404439c4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 836714f7a7ca17d759d0d71a7cbb30d63fdfaf95
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="processing-notification-messages-in-date-and-time-picker-controls"></a>Zpracování oznamovacích zpráv v ovládacích prvcích pro výběr data a času
Jak uživatelé pracují s datum a čas ovládací prvek pro výběr, ovládacího prvku (`CDateTimeCtrl`) odešle zprávy s oznámením do nadřazeného okna, obvykle objekt zobrazení nebo dialogové okno. Tyto zprávy zpracování, pokud chcete, aby dělala něco v odpovědi. Například když uživatel otevře nástroje pro výběr data a času zobrazit vložené ovládací prvek měsíční kalendář, **dtn_dropdown –** odeslání oznámení.  
  
 Okno Vlastnosti použijte pro přidání obslužné rutiny oznamovacích do nadřazené třídy pro ty zprávy, které chcete implementovat.  
  
 Následující seznam popisuje různé oznámení zaslaná z prvku pro výběr data a času.  
  
-   **Dtn_dropdown –** upozorní nadřazeného objektu, který ovládací prvek embedded měsíční kalendář se nezobrazí. Toto oznámení je odeslán, pouze když **DTS_UPDOWN** styl nebyl nastaven. Další informace o tomto oznámení najdete v tématu [přístup k Embedded ovládací prvek měsíční kalendář](../mfc/accessing-the-embedded-month-calendar-control.md).  
  
-   **Dtn_closeup –** upozorní nadřazeného objektu, který je ovládací prvek embedded měsíční kalendář bude uzavřen. Toto oznámení je odeslán, pouze když **DTS_UPDOWN** styl nebyl nastaven.  
  
-   **Dtn_datetimechange –** upozorní nadřazeného objektu, který má v ovládacím prvku došlo ke změně.  
  
-   **Dtn_format –** upozorní nadřazený, je nutné zadat text, který se má zobrazit v poli zpětného volání. Další informace v tomto oznámení a pole zpětného volání najdete v tématu [použití polí zpětného volání v datum a čas ovládací prvek výběru](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md).  
  
-   **Dtn_formatquery –** požadavky nadřazené zadat maximální povolenou velikost řetězce, který bude zobrazen v poli zpětného volání. Zpracování toto oznámení umožňuje řízení správně zobrazení výstupu vždy, omezení blikání v rámci zobrazení ovládacího prvku. Další informace o tomto oznámení najdete v tématu [použití polí zpětného volání v datum a čas ovládací prvek výběru](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md).  
  
-   **DTN_USERSTRING** nadřazené upozorní, že uživatel dokončil obsah prvku pro výběr data a času úpravy. Toto oznámení je odeslán, pouze když **DTS_APPCANPARSE** styl byla nastavena.  
  
-   **DTN_WMKEYDOWN** upozorní nadřazený, když uživatel zadá v poli zpětného volání. Zpracování toto oznámení emulovat stejné odpovědi klávesnice podporuje pro pole zpětného volání v ovládacím prvku pro výběr data a času. Další informace o tomto oznámení najdete v tématu [podpora pole zpětného volání v ovládacím prvku DTP](http://msdn.microsoft.com/library/windows/desktop/bb761726) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

