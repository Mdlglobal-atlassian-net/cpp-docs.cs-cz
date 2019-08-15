---
title: TOOLTIPTEXT – struktura
ms.date: 11/04/2016
f1_keywords:
- TOOLTIPTEXT
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- tool tips [MFC], notifications
ms.assetid: 547591bf-80f5-400e-a2a7-0708cfffbb5d
ms.openlocfilehash: 80b95225a277a7985c30e5ea453597b06e501753
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513298"
---
# <a name="tooltiptext-structure"></a>TOOLTIPTEXT – struktura

Při psaní [obslužné rutiny oznámení o popisu nástroje](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)je nutné použít strukturu **ToolTipText** . Členové struktury **ToolTipText** jsou:

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

*hdr*<br/>
Určuje nástroj, který potřebuje text. Jediný člen této struktury, který může být potřeba, je ID příkazu ovládacího prvku. ID příkazu ovládacího prvku bude v *idFrom* členu struktury **NMHDR** , ke kterému se dá použít syntaxe `hdr.idFrom`. Diskuzi o členech struktury **NMHDR** najdete v tématu [NMHDR](/windows/win32/api/richedit/ns-richedit-nmhdr) .

*lpszText*<br/>
Adresa řetězce, který získá text pro nástroj.

*szText*<br/>
Vyrovnávací paměť, která přijímá text tipu nástroje. Aplikace může zkopírovat text do této vyrovnávací paměti jako alternativu k zadání adresy řetězce.

*hinst*<br/>
Popisovač instance, která obsahuje řetězec, který má být použit jako text tipu nástroje. Pokud *lpszText* je adresa textu tipu nástroje, má tento člen hodnotu null.

Při zpracování `TTN_NEEDTEXT` zprávy s oznámením zadejte řetězec, který se má zobrazit v jednom z následujících způsobů:

- Zkopírujte text do vyrovnávací paměti určené členem *szText* .

- Zkopírujte adresu vyrovnávací paměti, která obsahuje text k *lpszText* členu.

- Zkopírujte identifikátor prostředku řetězce do člena *lpszText* a zkopírujte popisovač instance, která obsahuje prostředek, do členu *hInst* .

## <a name="see-also"></a>Viz také:

[Popisy tlačítek v oknech neodvozených ze třídy CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)
