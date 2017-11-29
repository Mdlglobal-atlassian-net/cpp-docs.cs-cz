---
title: "Wm_ – zprávy: S | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ON_WM_SYSDEADCHAR
- ON_WM_SYSKEYDOWN
- ON_WM_STYLECHANGING
- ON_WM_STYLECHANGED
- ON_WM_SPOOLERSTATUS
- ON_WM_SYSCHAR
- ON_WM_SETFOCUS
- ON_WM_SIZE
- ON_WM_SIZING
- ON_WM_SETCURSOR
- ON_WM_SYSCOMMAND
- ON_WM_SETTINGCHANGE
- ON_WM_SHOWWINDOW
- ON_WM_SYSKEYUP
- ON_WM_SIZECLIPBOARD
- ON_WM_SYSCOLORCHANGE
dev_langs: C++
helpviewer_keywords:
- ON_WM_SIZE [MFC]
- ON_WM_SETFOCUS [MFC]
- ON_WM_SIZING [MFC]
- ON_WM_SYSCHAR [MFC]
- ON_WM_SETTINGCHANGE [MFC]
- ON_WM_SYSDEADCHAR [MFC]
- ON_WM_SHOWWINDOW [MFC]
- ON_WM_STYLECHANGING [MFC]
- ON_WM_SYSCOMMAND [MFC]
- ON_WM_STYLECHANGED [MFC]
- ON_WM_SPOOLERSTATUS [MFC]
- ON_WM_SYSCOLORCHANGE [MFC]
- ON_WM_SETCURSOR [MFC]
- ON_WM_SIZECLIPBOARD [MFC]
- ON_WM_SYSKEYUP [MFC]
- ON_WM_SYSKEYDOWN [MFC]
- WM_ messages
ms.assetid: 4b9aec79-a98f-4aa0-a3d9-110941b6dcbc
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3db56509d17b254655ead80f2125895a0eff25a6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="wm-messages-s"></a>WM_ – zprávy: S
Následující položky mapy odpovídají prototypy funkcí.  
  
|Položku mapování|Prototyp funkce|  
|---------------|------------------------|  
|(ON_WM_SETCURSOR)|afx_msg BOOL [onsetcursor –](../../mfc/reference/cwnd-class.md#onsetcursor)(CWnd *, UINT, UINT);|  
|(ON_WM_SETFOCUS)|afx_msg void [OnSetFocus](../../mfc/reference/cwnd-class.md#onsetfocus)(CWnd *);|  
|(ON_WM_SETTINGCHANGE)|afx_msg void [onsettingchange –](../../mfc/reference/cwnd-class.md#onsettingchange)(Celé_číslo uFlags LPCTSTR lpszSection);|  
|(ON_WM_SHOWWINDOW)|afx_msg void [OnShowWindow](../../mfc/reference/cwnd-class.md#onshowwindow)(BOOL, UINT);|  
|(ON_WM_SIZE)|afx_msg void [OnSize](../../mfc/reference/cwnd-class.md#onsize)(UINT, int, int);|  
|(ON_WM_SIZECLIPBOARD)|afx_msg void [OnSizeClipboard](../../mfc/reference/cwnd-class.md#onsizeclipboard)(CWnd *, POPISOVAČ);|  
|(ON_WM_SIZING)|afx_msg void [OnSizing](../../mfc/reference/cwnd-class.md#onsizing)(UINT, lprect –);|  
|(ON_WM_SPOOLERSTATUS)|afx_msg void [OnSpoolerStatus](../../mfc/reference/cwnd-class.md#onspoolerstatus)(UINT, UINT);|  
|(ON_WM_STYLECHANGED)|afx_msg void [OnStyleChanged](../../mfc/reference/cwnd-class.md#onstylechanged)(int, LPSTYLESTRUCT);|  
|(ON_WM_STYLECHANGING)|afx_msg void [OnStyleChanging](../../mfc/reference/cwnd-class.md#onstylechanging)(int, LPSTYLESTRUCT);|  
|(ON_WM_SYSCHAR)|afx_msg void [OnSysChar](../../mfc/reference/cwnd-class.md#onsyschar)(UINT, UINT, UINT);|  
|(ON_WM_SYSCOLORCHANGE)|afx_msg void [onsyscolorchange –](../../mfc/reference/cwnd-class.md#onsyscolorchange)();|  
|(ON_WM_SYSCOMMAND)|afx_msg void [OnSysCommand](../../mfc/reference/cwnd-class.md#onsyscommand)(UINT, LONG);|  
|(ON_WM_SYSDEADCHAR)|afx_msg void [OnSysDeadChar](../../mfc/reference/cwnd-class.md#onsysdeadchar)(UINT, UINT, UINT);|  
|(ON_WM_SYSKEYDOWN)|afx_msg void [OnSysKeyDown](../../mfc/reference/cwnd-class.md#onsyskeydown)(UINT, UINT, UINT);|  
|(ON_WM_SYSKEYUP)|afx_msg void [OnSysKeyUp](../../mfc/reference/cwnd-class.md#onsyskeyup)(UINT, UINT, UINT);|  
  
## <a name="see-also"></a>Viz také  
 [Mapy zpráv](../../mfc/reference/message-maps-mfc.md)   
 [Obslužné rutiny pro zprávy WM_](../../mfc/reference/handlers-for-wm-messages.md)
