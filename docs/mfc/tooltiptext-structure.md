---
title: TOOLTIPTEXT – struktura
ms.date: 11/04/2016
f1_keywords:
- TOOLTIPTEXT
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- tool tips [MFC], notifications
ms.assetid: 547591bf-80f5-400e-a2a7-0708cfffbb5d
ms.openlocfilehash: 7d77ca7dc55273e6084e919323ed71e55fa68a2c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62181844"
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

*hdr*<br/>
Určuje nástroj, který potřebuje text. Jediným členem této struktury, které je třeba je ID ovládacího prvku příkazu. ID příkazu ovládacího prvku bude v *idFrom* člena **NMHDR** strukturu, k němu přistupovat pomocí syntaxe `hdr.idFrom`. Zobrazit [NMHDR](/windows/desktop/api/richedit/ns-richedit-_nmhdr) diskuzi o členy **NMHDR** struktury.

*lpszText*<br/>
Adresa řetězce na přijetí textu pro nástroj.

*szText*<br/>
Vyrovnávací paměť, která přijímá text tipu nástroj. Aplikace můžete zkopírovat text do této vyrovnávací paměti jako alternativu k zadání adresy řetězec.

*hinst*<br/>
Popisovač instance, která obsahuje řetězec, který má být použit jako text tipu nástroj. Pokud *lpszText* je adresa nástroj text tipu, tento člen je NULL.

Při zpracování `TTN_NEEDTEXT` oznámení zprávu, zadejte řetězec, který se má zobrazit v jednom z následujících způsobů:

- Zkopírujte text do vyrovnávací paměti určené parametrem *szText* člena.

- Zkopírujte adresu vyrovnávací paměti, který obsahuje text, který má *lpszText* člena.

- Zkopírujte identifikátor řetězce prostředku k *lpszText* člen a kopírování popisovač instance, která obsahuje prostředek, který má *hinst* člena.

## <a name="see-also"></a>Viz také:

[Popisy tlačítek v oknech neodvozených ze třídy CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)
