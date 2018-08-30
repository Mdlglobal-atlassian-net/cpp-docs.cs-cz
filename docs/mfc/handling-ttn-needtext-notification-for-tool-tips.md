---
title: Zpracování oznámení TTN_NEEDTEXT u popisů tlačítek | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TTN_NEEDTEXT
dev_langs:
- C++
helpviewer_keywords:
- TTN_NEEDTEXT message [MFC]
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: d0370a65-21ba-4676-bcc5-8cf851bbb15c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 65278571fabf24011960ad577461347f1dfebf73
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200515"
---
# <a name="handling-ttnneedtext-notification-for-tool-tips"></a>Zpracování oznámení TTN_NEEDTEXT u popisů tlačítek
Jako součást [povolení popisů tlačítek](../mfc/enabling-tool-tips.md), zpracování **TTN_NEEDTEXT** zprávu tak, že přidáte následující položku do mapy zprávu nadřazenému oknu:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_1.cpp)]  
  
 `memberFxn`  
 Členská funkce se volá, když pro toto tlačítko je nutné zadat text.  
  
 Všimněte si, že ID popisku tlačítka je vždy 0.  
  
 Deklarace funkce obslužné rutiny v definici třídy následujícím způsobem:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#53](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_2.h)]  
  
 kde jsou kurzívou parametry:  
  
 `id`  
 Identifikátor ovládacího prvku, který poslat oznámení. Nepoužívá se. Id ovládacího prvku je převzata z **NMHDR** struktury.  
  
 `pNMHDR`  
 Ukazatel [NMTTDISPINFO](/windows/desktop/api/commctrl/ns-commctrl-tagnmttdispinfoa) struktury. Tato struktura je také popsáno dále v [ToolTipText – struktura](../mfc/tooltiptext-structure.md).  
  
 `pResult`  
 Ukazatel na kód výsledku můžete nastavit před vrácením. **TTN_NEEDTEXT** můžete ignorovat obslužné rutiny *pResult* parametru.  
  
 Jako příklad obslužnou rutinu oznámení formulářové zobrazení:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#54](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_3.cpp)]  
  
 Volání `EnableToolTips` (Tento fragment z `OnInitDialog`):  
  
 [!code-cpp[NVC_MFCControlLadenDialog#55](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_4.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Popisy tlačítek v oknech neodvozených ze třídy CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)

