---
title: "Povolení tipů nástrojů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- initializing tool tips [MFC]
- enabling tool tips [MFC]
- tool tips [MFC], initializing
- tool tips [MFC], enabling
ms.assetid: 06b7c889-7722-4ce6-8b88-9efa50fe6369
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0555af785d75c9247eb365a03a51161441a4722a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="enabling-tool-tips"></a>Povolení tipů nástrojů
Můžete povolit nástroj pro podporu tip pro podřízené prvky okna (například ovládacích prvků na formuláři zobrazení nebo dialogové okno pole).  
  
### <a name="to-enable-tool-tips-for-the-child-controls-of-a-window"></a>Chcete-li povolit popisy pro ovládací prvky podřízená okna  
  
1.  Volání `EnableToolTips` časového intervalu pro který chcete zadat typy nástrojů pro správu.  
  
2.  Zadejte řetězec pro každý ovládací prvek v vaše [oznámení TTN_NEEDTEXT](../mfc/handling-ttn-needtext-notification-for-tool-tips.md) obslužné rutiny. Obslužná rutina se mapy zpráv okna, která obsahuje podřízené ovládací prvky (například třídě zobrazení formuláře). Tato obslužná rutina by měly volat funkci, která identifikuje ovládacího prvku a nastaví **pszText** Určuje text, který používá ovládacím prvkem popis tlačítka.  
  
## <a name="see-also"></a>Viz také  
 [Popisy tlačítek v oknech neodvozených ze třídy CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)

