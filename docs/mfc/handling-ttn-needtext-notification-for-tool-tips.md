---
title: "Zpracování oznámení TTN_NEEDTEXT u popisů tlačítek | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TTN_NEEDTEXT
dev_langs:
- C++
helpviewer_keywords:
- TTN_NEEDTEXT message [MFC]
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: d0370a65-21ba-4676-bcc5-8cf851bbb15c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 26a3b74ca0bc11b169e195599c5172b245cf0529
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="handling-ttnneedtext-notification-for-tool-tips"></a>Zpracování oznámení TTN_NEEDTEXT u popisů tlačítek
Jako součást [povolení tipů nástrojů](../mfc/enabling-tool-tips.md), zpracováváte **TTN_NEEDTEXT** zpráva přidáním následující položku do nadřazené okno mapy zpráv:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_1.cpp)]  
  
 `memberFxn`  
 Členská funkce se volá, když pro toto tlačítko je nutné zadat text.  
  
 Všimněte si, že ID popisku tlačítka je vždy 0.  
  
 Funkce obslužných rutin v definici třídy deklarujte následujícím způsobem:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#53](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_2.h)]  
  
 kde jsou kurzívou parametry:  
  
 `id`  
 Identifikátor ovládacího prvku, který odesílá oznámení. Nepoužívá se. Id ovládacího prvku jsou převzaty z **NMHDR** struktury.  
  
 `pNMHDR`  
 Ukazatel [NMTTDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb760258) struktury. Tato struktura je také popsáno v další [ToolTipText – struktura](../mfc/tooltiptext-structure.md).  
  
 `pResult`  
 Ukazatel na kód výsledku můžete nastavit před vrácením. **TTN_NEEDTEXT** můžete ignorovat obslužné rutiny `pResult` parametr.  
  
 Jako příklad obslužnou rutinu oznámení zobrazení formuláře:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#54](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_3.cpp)]  
  
 Volání `EnableToolTips` (fragment převzaty z `OnInitDialog`):  
  
 [!code-cpp[NVC_MFCControlLadenDialog#55](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_4.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Popisy tlačítek v oknech neodvozených ze třídy CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)

