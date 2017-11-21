---
title: "Popisy tlačítek v oknech Neodvozených ze třídy CFrameWnd | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- enabling tool tips [MFC]
- TOOLTIPTEXT structure [MFC]
- Help [MFC], tool tips for controls
- TTN_NEEDTEXT message [MFC]
- controls [MFC], tool tips
- handler functions [MFC], tool tips
ms.assetid: cad5ef0f-02e3-4151-ad0d-3d42e6932b0e
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d584f610a7cab58dc15a3f34859b317ae8c2571d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="tool-tips-in-windows-not-derived-from-cframewnd"></a>Popisy tlačítek v oknech neodvozených ze třídy CFrameWnd
Rodina Tento článek popisuje povolení popisy pro ovládací prvky obsažené v okně, které není odvozen od [CFrameWnd](../mfc/reference/cframewnd-class.md). Článek [panely nástrojů popisy](../mfc/toolbar-tool-tips.md) poskytuje informace o popisy pro ovládací prvky v `CFrameWnd`.  
  
 Obsahuje následující témata v této rodině článku:  
  
-   [Povolení tipů nástrojů](../mfc/enabling-tool-tips.md)  
  
-   [Zpracování oznámení TTN_NEEDTEXT u popisů tlačítek](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)  
  
-   [ToolTipText – struktura](../mfc/tooltiptext-structure.md)  
  
 Pro tlačítka se automaticky zobrazují popisy tlačítek a jiných ovládacích prvků, součástí nadřazeného okna odvozen od `CFrameWnd`. Důvodem je, že `CFrameWnd` má výchozí obslužnou rutinu pro [TTN_GETDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb760269) oznámení, která zpracovává **TTN_NEEDTEXT** oznámení z nástroje tip ovládací prvky přidružené k ovládací prvky.  
  
 Tento výchozí obslužnou rutinu však není volána při **TTN_NEEDTEXT** oznámení se odesílá z ovládacího prvku popisek nástroj spojené s ovládacím prvkem v okně, které není `CFrameWnd`, jako je například ovládací prvek dialogového okna nebo zobrazení formuláře. Proto je nutné k funkci obslužné rutiny pro zabezpečení **TTN_NEEDTEXT** zprávy oznámení, aby bylo možné zobrazit popisy pro podřízené ovládací prvky.  
  
 Popisy tlačítek výchozí, zadaná pro váš windows podle [CWnd::EnableToolTips](../mfc/reference/cwnd-class.md#enabletooltips) nemají text související s nimi. K načtení textu pro tip nástroj, který chcete zobrazit, **TTN_NEEDTEXT** oznámení se odesílá do nadřazeného okna prvkem popis tlačítka, těsně před se zobrazí okno tip nástroje. Pokud není žádná obslužná rutina pro tuto zprávu přiřadit některé hodnotu **pszText** členem **ToolTipText –** struktury, budou existovat žádný text pro popis tlačítka zobrazen.  
  
## <a name="see-also"></a>Viz také  
 [Popisy tlačítek](../mfc/tool-tips.md)

