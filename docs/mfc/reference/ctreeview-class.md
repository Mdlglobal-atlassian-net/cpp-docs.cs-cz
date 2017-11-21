---
title: "CTreeView – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTreeView
- AFXCVIEW/CTreeView
- AFXCVIEW/CTreeView::CTreeView
- AFXCVIEW/CTreeView::GetTreeCtrl
dev_langs: C++
helpviewer_keywords:
- CTreeView [MFC], CTreeView
- CTreeView [MFC], GetTreeCtrl
ms.assetid: 5df583a6-d69f-42ca-9d8d-57e04558afff
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6d1d8ee7d06e9926a240ca185ce36ba0b1a180af
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ctreeview-class"></a>CTreeView – třída
Používání ovládacího prvku strom, zjednodušuje [CTreeCtrl](../../mfc/reference/ctreectrl-class.md), třídu, která zapouzdřuje funkce ovládací prvek stromu s architekturou MFC na zobrazení dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CTreeView : public CCtrlView  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CTreeView::CTreeView](#ctreeview)|Vytvoří `CTreeView` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CTreeView::GetTreeCtrl](#gettreectrl)|Vrátí ovládací prvek stromu přidružené zobrazení.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace o této architektury, najdete v článku Přehled pro [CView](../../mfc/reference/cview-class.md) třídy a křížové odkazy citovalo existuje.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CTreeView`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcview.h  
  
##  <a name="ctreeview"></a>CTreeView::CTreeView  
 Vytvoří `CTreeView` objektu.  
  
```  
CTreeView();
```  
  
##  <a name="gettreectrl"></a>CTreeView::GetTreeCtrl  
 Vrátí odkaz na ovládací prvek stromu přidružené zobrazení.  
  
```  
CTreeCtrl& GetTreeCtrl() const;  
```  
  
## <a name="see-also"></a>Viz také  
 [CCtrlView – třída](../../mfc/reference/cctrlview-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CView – třída](../../mfc/reference/cview-class.md)   
 [CCtrlView – třída](../../mfc/reference/cctrlview-class.md)   
 [CTreeCtrl – třída](../../mfc/reference/ctreectrl-class.md)
