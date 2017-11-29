---
title: "Wm_ – zprávy: T – Z | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ON_WM_TCARD
- ON_WM_WININICHANGE
- ON_WM_VSCROLLCLIPBOARD
- ON_WM_VSCROLL
- ON_WM_WINDOWPOSCHANGED
- ON_WM_TIMECHANGE
- ON_WM_TIMER
- ON_WM_VKEYTOITEM
- ON_WM_WINDOWPOSCHANGING
dev_langs: C++
helpviewer_keywords:
- ON_WM_VSCROLLCLIPBOARD [MFC]
- ON_WM_WININICHANGE [MFC]
- ON_WM_WINDOWPOSCHANGED [MFC]
- ON_WM_TCARD [MFC]
- ON_WM_TIMECHANGE [MFC]
- ON_WM_TIMER [MFC]
- WM_ messages [MFC]
- ON_WM_WINDOWPOSCHANGING [MFC]
- ON_WM_VKEYTOITEM [MFC]
- ON_WM_VSCROLL
ms.assetid: c528bb2e-ddb5-4da6-b652-432a387408b8
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0c28988b147575db35a45064bc45fff4250c95b5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="wm-messages-t---z"></a>WM_ – zprávy: T–Z
Následující položky mapy odpovídají prototypy funkcí:  
  
|Položku mapování|Prototyp funkce|  
|---------------|------------------------|  
|ON_WM_TCARD()|afx_msg void [OnTCard](../../mfc/reference/cwnd-class.md#ontcard)(UINT, DWORD);|  
|ON_WM_TIMECHANGE()|afx_msg void [OnTimeChange](../../mfc/reference/cwnd-class.md#ontimechange)();|  
|ON_WM_TIMER()|afx_msg void [časovém intervalu](../../mfc/reference/cwnd-class.md#ontimer)(UINT_PTR);|  
|ON_WM_UNICHAR()|afx_msg void [OnUniChar](../../mfc/reference/cwnd-class.md#onunichar)(UINT, UINT, UINT);|  
|ON_WM_UNINITMENUPOPUP()|afx_msg void [OnUnInitMenuPopup](../../mfc/reference/cwnd-class.md#onuninitmenupopup)(cmenu – *, UINT);|  
|ON_WM_USERCHANGED()|afx_msg void [OnUserChanged](../../mfc/reference/cwnd-class.md#onuserchanged)();|  
|ON_WM_VKEYTOITEM()|afx_msg int [OnVKeyToItem](../../mfc/reference/cwnd-class.md#onvkeytoitem)(Celé_číslo CWnd *, UINT);|  
|ON_WM_VSCROLL()|afx_msg void [OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)(UINT, UINT, CWnd *);|  
|ON_WM_VSCROLLCLIPBOARD()|afx_msg void [OnVScrollClipboard](../../mfc/reference/cwnd-class.md#onvscrollclipboard)(CWnd *, UINT, UINT);|  
|ON_WM_WINDOWPOSCHANGED()|afx_msg void [OnWindowPosChanged](../../mfc/reference/cwnd-class.md#onwindowposchanged)(windowpos – *);|  
|ON_WM_WINDOWPOSCHANGING()|afx_msg void [OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging)(windowpos – *);|  
|ON_WM_WININICHANGE()|afx_msg void [OnWinIniChange](../../mfc/reference/cwnd-class.md#onwininichange)(LPSTR);|  
|ON_WM_WTSSESSION_CHANGE()|afx_msg void [OnSessionChange](../../mfc/reference/cwnd-class.md#onsessionchange)(UINT, UINT);|  
|ON_WM_XBUTTONDBLCLK()|afx_msg void [OnXButtonDblClk](../../mfc/reference/cwnd-class.md#onxbuttondblclk)(UINT, UINT, CPoint);|  
|ON_WM_XBUTTONDOWN()|afx_msg void [OnXButtonDown](../../mfc/reference/cwnd-class.md#onxbuttondown)(UINT, UINT, CPoint);|  
|ON_WM_XBUTTONUP()|afx_msg void [OnXButtonUp](../../mfc/reference/cwnd-class.md#onxbuttonup)(UINT, UINT, CPoint);|  
  
## <a name="see-also"></a>Viz také  
 [Mapy zpráv](../../mfc/reference/message-maps-mfc.md)   
 [Obslužné rutiny pro zprávy WM_](../../mfc/reference/handlers-for-wm-messages.md)
