---
title: ToolTipText – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TOOLTIPTEXT
dev_langs:
- C++
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- tool tips [MFC], notifications
ms.assetid: 547591bf-80f5-400e-a2a7-0708cfffbb5d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8cae7efbee59b24ff34518b62ff212d436973053
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953929"
---
# <a name="tooltiptext-structure"></a>TOOLTIPTEXT – struktura
Při psaní vaše [popisovač oznámení obslužné rutiny](../mfc/handling-ttn-needtext-notification-for-tool-tips.md), budete muset použít **ToolTipText –** struktura. Členové **ToolTipText –** struktura jsou:  
  
 `typedef struct {`  
  
 `NMHDR     hdr;        // required for all WM_NOTIFY messages`  
  
 `LPTSTR    lpszText;   // see below`  
  
 `TCHAR     szText[80]; // buffer for tool tip text`  
  
 `HINSTANCE hinst;      // see below`  
  
 `UINT      uflags;     // flag indicating how to interpret the`  
  
 `// idFrom member of the NMHDR structure`  
  
 `// that is included in the structure`  
  
 `} TOOLTIPTEXT, FAR *LPTOOLTIPTEXT;`  
  
 *záhlaví*  
 Určuje nástroj, který potřebuje text. Pouze členové tuto strukturu, které byste měli je ID ovládacího prvku příkazu. ID příkazu ovládacího prvku bude v *idFrom* členem **NMHDR** struktura, získat přístup pomocí syntaxe `hdr.idFrom`. V tématu [NMHDR](http://msdn.microsoft.com/library/windows/desktop/bb775514) diskuzi o členy **NMHDR** struktury.  
  
 *lpszText*  
 Adresa řetězec získat text pro nástroj.  
  
 *szText*  
 Vyrovnávací paměť, která přijímá text popisu nástroje. Aplikace můžete zkopírovat text do této vyrovnávací paměti jako alternativu k zadání adresy řetězec.  
  
 *hinst*  
 Popisovač instance, který obsahuje řetězec, který se má použít jako text popisu nástroje. Pokud *lpszText* je adresa text popisu nástroje tento člen je NULL.  
  
 Při zpracování `TTN_NEEDTEXT` oznámení zprávy, zadejte řetězec, který se má zobrazit v jednom z následujících způsobů:  
  
-   Zkopírujte text do vyrovnávací paměti určeného *szText* člen.  
  
-   Zkopírujte adresu vyrovnávací paměti, která obsahuje text, který má *lpszText* člen.  
  
-   Zkopírovat identifikátor řetězec prostředku *lpszText* člen a zkopírujte popisovač instance, který obsahuje prostředek, který *hinst* člen.  
  
## <a name="see-also"></a>Viz také  
 [Popisy tlačítek v oknech neodvozených ze třídy CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)

