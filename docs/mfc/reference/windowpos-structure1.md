---
title: "Windowpos – – Struktura1 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- WINDOWPOS
dev_langs:
- C++
helpviewer_keywords:
- WINDOWPOS structure [MFC]
ms.assetid: a4ea7cd9-c4c2-4480-9c55-cbbff72195e1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7db3991a6767e33c73857daf40a977ac5f6f0b85
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="windowpos-structure1"></a>Windowpos – – Struktura1
`WINDOWPOS` Struktura obsahuje informace o velikosti a pozice časového období.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagWINDOWPOS { /* wp */  
    HWND hwnd;  
    HWND hwndInsertAfter;  
    int x;  
    int y;  
    int cx;  
    int cy;  
    UINT flags;  
} WINDOWPOS;  
```  
  
#### <a name="parameters"></a>Parametry  
 *hWnd*  
 Identifikuje okna.  
  
 *hwndInsertAfter*  
 Určuje interval, za které je umístěn toto okno.  
  
 *x*  
 Určuje umístění levého okraje okna.  
  
 *y*  
 Určuje pozici pravému okraji okna.  
  
 `cx`  
 Určuje šířku okna v pixelech.  
  
 `cy`  
 Určuje výšku okna v pixelech.  
  
 `flags`  
 Určuje umístění okno Možnosti. Tento člen může být jedna z následujících hodnot:  
  
- **SWP_DRAWFRAME** nevykresluje kolem okna rámečkem (definovanou v popisu třídy pro okno). Okno obdrží `WM_NCCALCSIZE` zprávy.  
  
- **SWP_FRAMECHANGED** odešle `WM_NCCALCSIZE` zprávy do okna, i když nedojde ke změně velikost okna. Pokud tento příznak není zadán, `WM_NCCALCSIZE` je odeslat pouze v případě, že mění se velikost okna.  
  
- **SWP_HIDEWINDOW** skryje okna.  
  
- `SWP_NOACTIVATE`Neaktivuje okna.  
  
- **SWP_NOCOPYBITS** zahodí celý obsah klientské oblasti. Pokud tento příznak není zadán, jsou platný obsah klientské oblasti uložit a zkopírovat zpět do klientské oblasti po okna je velikost nebo změnit jejich umístění.  
  
- `SWP_NOMOVE`Zachová aktuální pozici (ignoruje **x** a **y** členy).  
  
- **SWP_NOOWNERZORDER** nezmění okno vlastník pozice v pořadí.  
  
- `SWP_NOSIZE`Zachová aktuální velikost (ignoruje **cx** a **cy** členy).  
  
- **SWP_NOREDRAW** není ho překreslit změny.  
  
- **SWP_NOREPOSITION** stejné jako **SWP_NOOWNERZORDER**.  
  
- **SWP_NOSENDCHANGING** přijetí brání okna `WM_WINDOWPOSCHANGING` zprávy.  
  
- `SWP_NOZORDER`Zachová aktuální řazení (ignoruje **hwndInsertAfter** člen).  
  
- **SWP_SHOWWINDOW** zobrazí okno.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** winuser  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging)

