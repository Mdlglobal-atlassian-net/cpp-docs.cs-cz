---
title: "Windowplacement – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- WINDOWPLACEMENT
dev_langs:
- C++
helpviewer_keywords:
- WINDOWPLACEMENT structure [MFC]
ms.assetid: ea7d61f6-eb57-478e-9b08-7c1d07091aa8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e73065cdf20d68b1da4ba77d1ad555e2bf95e937
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="windowplacement-structure"></a>WINDOWPLACEMENT – struktura
`WINDOWPLACEMENT` Struktura obsahuje informace o umístění okna na obrazovce**.**  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagWINDOWPLACEMENT {     /* wndpl */  
    UINT length;  
    UINT flags;  
    UINT showCmd;  
    POINT ptMinPosition;  
    POINT ptMaxPosition;  
    RECT rcNormalPosition;  
} WINDOWPLACEMENT;  
```  
  
#### <a name="parameters"></a>Parametry  
 *Délka*  
 Určuje délku v bajtech struktury**.**  
  
 `flags`  
 Určuje příznaky, které řídí pozici minimalizované okno a metodu, podle kterého je okno obnovit. Tento člen může být jedno nebo obě následující příznaky:  
  
- **WPF_SETMINPOSITION** určuje lze na x - a y pozici okna minimalizovaném okně**.** Tento příznak musí být zadán, pokud jsou souřadnice nastavené **ptMinPosition** člen.  
  
- **WPF_RESTORETOMAXIMIZED** Určuje, že okno obnovené největší, bez ohledu na to, jestli byl maximalizovaný předtím, než byla minimalizovaná. Toto nastavení je platný pouze při příštím spuštění okna obnovení. Výchozí chování obnovení nemění. Tento příznak je platná pouze tehdy, když **SW_SHOWMINIMIZED** je zadaná hodnota pro **showCmd** člen.  
  
 *showCmd*  
 Určuje aktuální stav zobrazení okna. Tento člen může být jedna z následujících hodnot:  
  
- **SW_HIDE** skryje okna a předává aktivace pro další okno.  
  
- **SW_MINIMIZE** minimalizuje zadané okno a aktivuje okno nejvyšší úrovně v seznamu systému.  
  
- **SW_RESTORE** Activates a zobrazí okno. Pokud je okno minimalizovaná nebo maximalizovaný, Windows se obnoví do původní velikost a umístění (stejné jako **SW_SHOWNORMAL**).  
  
- **SW_SHOW** aktivuje okno a zobrazí v jeho aktuální velikost a umístění.  
  
- **SW_SHOWMAXIMIZED** aktivuje okno a zobrazí jako maximalizovaném okně.  
  
- **SW_SHOWMINIMIZED** aktivuje okno a zobrazí jako ikonu.  
  
- **SW_SHOWMINNOACTIVE** zobrazí okno jako ikonu. Okno, který je aktuálně aktivní zůstává aktivní.  
  
- **SW_SHOWNA** okno se zobrazí v jejím aktuálním stavu. Okno, který je aktuálně aktivní zůstává aktivní.  
  
- **SW_SHOWNOACTIVATE** okno se zobrazí v jeho nejnovější velikost a umístění. Okno, který je aktuálně aktivní zůstává aktivní.  
  
- **SW_SHOWNORMAL** Activates a zobrazí okno. Pokud je okno minimalizovaná nebo maximalizovaný, Windows se obnoví do původní velikost a umístění (stejné jako **SW_RESTORE**).  
  
 *ptMinPosition*  
 Určuje umístění levého horního rohu okna při minimalizaci okna.  
  
 `ptMaxPosition`  
 Pokud je okno maximalizované, určuje umístění levého horního rohu okna.  
  
 *rcNormalPosition*  
 Určuje souřadnice okna, když okno v normální pozice (obnovených).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** winuser  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::SetWindowPlacement](../../mfc/reference/cwnd-class.md#setwindowplacement)

