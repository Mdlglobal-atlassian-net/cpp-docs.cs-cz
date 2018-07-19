---
title: Createstruct – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CREATESTRUCT
dev_langs:
- C++
helpviewer_keywords:
- CREATESTRUCT structure [MFC]
ms.assetid: 028c7b5e-4fdc-48da-a550-d3e4f9e6cc85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6036490b21ccbd86dfed56ea90226cbb2db8d596
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848467"
---
# <a name="createstruct-structure"></a>CREATESTRUCT – struktura
`CREATESTRUCT` Struktury definuje inicializační parametry předány do procedury okna aplikace.  
  
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
 *lpCreateParams*  
 Body k datům se použije k vytvoření okna.  
  
 *hInstance*  
 Identifikuje popisovač instance modulu modulu, který je vlastníkem nové okno.  
  
 *hMenu*  
 Určuje nabídku pro nové okno. Pokud podřízené okno, obsahuje ID celé číslo.  
  
 *hwndParent*  
 Identifikuje okně, které vlastní novém okně. Tento člen má hodnotu NULL, pokud se nové okno je okno nejvyšší úrovně.  
  
 *CY*  
 Určuje výšku nové okno.  
  
 *CX*  
 Určuje šířku nové okno.  
  
 *y*  
 Určuje souřadnici y levého horního rohu nové okno. Souřadnice jsou relativní vzhledem k nadřazené okno, pokud je okno nové podřízené okno; v opačném případě souřadnice jsou relativně ke zdroji obrazovky.  
  
 *x*  
 Určuje souřadnice x levého horního rohu nové okno. Souřadnice jsou relativní vzhledem k nadřazené okno, pokud je okno nové podřízené okno; v opačném případě souřadnice jsou relativně ke zdroji obrazovky.  
  
 *Styl*  
 Určuje nové okno [styl](../../mfc/reference/styles-used-by-mfc.md).  
  
 *lpszName*  
 Odkazuje na řetězec zakončený hodnotou null, který určuje název nového okna.  
  
 *lpszClass*  
 Odkazuje na řetězec zakončený hodnotou null, který určuje název třídy nové okno Windows ( [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) struktury; Další informace najdete v tématu Windows SDK).  
  
 *dwExStyle*  
 Určuje, [rozšířený styl](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) v novém okně.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** winuser  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate)


