---
title: ToolTipText – struktura | Dokumentace Microsoftu
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
ms.openlocfilehash: 82c06b98acec18e845fd1353875c1453c4bee8b1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097156"
---
# <a name="tooltiptext-structure"></a>TOOLTIPTEXT – struktura
Písemně vaše [popisovač oznámení obslužné rutiny](../mfc/handling-ttn-needtext-notification-for-tool-tips.md), budete muset použít **TOOLTIPTEXT** struktury. Členové **TOOLTIPTEXT** struktury jsou:  
  
```cpp
typedef struct {
    NMHDR     hdr;        // required for all WM_NOTIFY messages
    LPTSTR    lpszText;   // see below
    TCHAR     szText[80]; // buffer for tool tip text
    HINSTANCE hinst;      // see below
    UINT      uflags;     // flag indicating how to interpret the
                          // idFrom member of the NMHDR structure
                          // that is included in the structure
} TOOLTIPTEXT, FAR *LPTOOLTIPTEXT;
```
  
 *HDR*  
 Určuje nástroj, který potřebuje text. Jediným členem této struktury, které je třeba je ID ovládacího prvku příkazu. ID příkazu ovládacího prvku bude v *idFrom* člena **NMHDR** strukturu, k němu přistupovat pomocí syntaxe `hdr.idFrom`. Zobrazit [NMHDR](/windows/desktop/api/richedit/ns-richedit-_nmhdr) diskuzi o členy **NMHDR** struktury.  
  
 *lpszText*  
 Adresa řetězce na přijetí textu pro nástroj.  
  
 *szText*  
 Vyrovnávací paměť, která přijímá text tipu nástroj. Aplikace můžete zkopírovat text do této vyrovnávací paměti jako alternativu k zadání adresy řetězec.  
  
 *hinst*  
 Popisovač instance, která obsahuje řetězec, který má být použit jako text tipu nástroj. Pokud *lpszText* je adresa nástroj text tipu, tento člen je NULL.  
  
Při zpracování `TTN_NEEDTEXT` oznámení zprávu, zadejte řetězec, který se má zobrazit v jednom z následujících způsobů:  
  
-   Zkopírujte text do vyrovnávací paměti určené parametrem *szText* člena.  
  
-   Zkopírujte adresu vyrovnávací paměti, který obsahuje text, který má *lpszText* člena.  
  
-   Zkopírujte identifikátor řetězce prostředku k *lpszText* člen a kopírování popisovač instance, která obsahuje prostředek, který má *hinst* člena.  
  
## <a name="see-also"></a>Viz také  
 [Popisy tlačítek v oknech neodvozených ze třídy CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)

