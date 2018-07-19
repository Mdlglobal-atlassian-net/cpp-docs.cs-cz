---
title: WINDOWPOS – Struktura1 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- WINDOWPOS
dev_langs:
- C++
helpviewer_keywords:
- WINDOWPOS structure [MFC]
ms.assetid: a4ea7cd9-c4c2-4480-9c55-cbbff72195e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: db51e8f9924d69406989b3a9ac12b45f0e55e870
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37885959"
---
# <a name="windowpos-structure1"></a>WINDOWPOS – Struktura1
`WINDOWPOS` Struktura obsahuje informace o velikosti a pozice okna.  
  
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
 Identifikuje v okně, za které je umístěn v tomto okně.  
  
 *x*  
 Určuje umístění levého okraje okna.  
  
 *y*  
 Určuje pozici pravém okraji okna.  
  
 *CX*  
 Určuje šířku okna v pixelech.  
  
 *CY*  
 Určuje výšku okna v pixelech.  
  
 *příznaky*  
 Určuje umístění v okně Možnosti. Tento člen může být jeden z následujících hodnot:  
  
- SWP_DRAWFRAME vykreslí rámec (definované v popisu třídy okna) kolem okna. V okně přijme zprávu WM_NCCALCSIZE.  
  
- Odešle SWP_FRAMECHANGED WM_NCCALCSIZE zprávu do okna, i v případě, že nedojde ke změně velikosti okna. Pokud tento příznak není zadán, je odeslána WM_NCCALCSIZE pouze při změně velikosti okna.  
  
- SWP_HIDEWINDOW skryje okno.  
  
- SWP_NOACTIVATE neaktivuje okna.  
  
- SWP_NOCOPYBITS zahodí celý obsah od klientské oblasti. Pokud tento příznak není zadán, se uloží a zkopíruje zpět do klientské oblasti, poté, co je v okně velikosti nebo změnit umístění platný obsah od klientské oblasti.  
  
- SWP_NOMOVE zachová aktuální pozice (ignoruje `x` a `y` členů).  
  
- SWP_NOOWNERZORDER nemění nadřazenému oknu pozici v pořadí vykreslování.  
  
- SWP_NOSIZE zachová aktuální velikost (ignoruje `cx` a `cy` členů).  
  
- SWP_NOREDRAW zůstávají beze změny změny.  
  
- SWP_NOREPOSITION stejné jako SWP_NOOWNERZORDER.  
  
- SWP_NOSENDCHANGING zabraňuje okně WM_WINDOWPOSCHANGING zprávu.  
  
- SWP_NOZORDER zachová aktuální řazení (ignoruje `hwndInsertAfter` člen).  
  
- SWP_SHOWWINDOW zobrazí okno.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** winuser  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging)

