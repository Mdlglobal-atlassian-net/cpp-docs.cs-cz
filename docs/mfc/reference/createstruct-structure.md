---
title: "Createstruct – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CREATESTRUCT
dev_langs: C++
helpviewer_keywords: CREATESTRUCT structure [MFC]
ms.assetid: 028c7b5e-4fdc-48da-a550-d3e4f9e6cc85
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 67f04b70b47e980455c73550e56d92f4433ee31c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="createstruct-structure"></a>CREATESTRUCT – struktura
`CREATESTRUCT` Struktura definuje Inicializace parametrů předaných pracovnímu postupu okno aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagCREATESTRUCT {  
    LPVOID lpCreateParams;  
    HANDLE hInstance;  
    HMENU hMenu;  
    HWND hwndParent;  
    int cy;  
    int cx;  
    int y;  
    int x;  
    LONG style;  
    LPCSTR lpszName;  
    LPCSTR lpszClass;  
    DWORD dwExStyle;  
} CREATESTRUCT;  
```  
  
#### <a name="parameters"></a>Parametry  
 `lpCreateParams`  
 Body tak, aby data použít k vytvoření okna.  
  
 `hInstance`  
 Identifikuje instancí modulu popisovač modul, který vlastní nové okno.  
  
 `hMenu`  
 Identifikuje nabídku použije se v novém okně. Pokud podřízeného okna, obsahuje ID celé číslo.  
  
 `hwndParent`  
 Identifikuje okně, které vlastní nové okno. Tento člen je **NULL** Pokud je okno nové okno nejvyšší úrovně.  
  
 `cy`  
 Určuje výšku nové okno.  
  
 `cx`  
 Určuje šířku nové okno.  
  
 `y`  
 Určuje souřadnici y levého horního rohu novém okně. Souřadnice jsou relativní vzhledem k nadřazené okno, pokud je okno nového podřízeného okna; v opačném případě souřadnice jsou relativně ke zdroji obrazovky.  
  
 `x`  
 Určuje souřadnici x v levém horním rohu okna nové. Souřadnice jsou relativní vzhledem k nadřazené okno, pokud je okno nového podřízeného okna; v opačném případě souřadnice jsou relativně ke zdroji obrazovky.  
  
 `style`  
 Určuje nové okno [styl](../../mfc/reference/styles-used-by-mfc.md).  
  
 `lpszName`  
 Odkazuje na řetězec ukončené hodnotou null, který určuje název nové okno.  
  
 `lpszClass`  
 Odkazuje na řetězec ukončené hodnotou null, který určuje název třídy Windows nové okno ( [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) struktury; Další informace najdete v tématu Windows SDK).  
  
 `dwExStyle`  
 Určuje, [rozšířený styl](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) v novém okně.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** winuser  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate)

