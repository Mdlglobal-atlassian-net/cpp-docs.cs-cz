---
title: "CTreeView – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTreeView
- AFXCVIEW/CTreeView
- AFXCVIEW/CTreeView::CTreeView
- AFXCVIEW/CTreeView::GetTreeCtrl
dev_langs:
- C++
helpviewer_keywords:
- CTreeView [MFC], CTreeView
- CTreeView [MFC], GetTreeCtrl
ms.assetid: 5df583a6-d69f-42ca-9d8d-57e04558afff
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7530569d5e5313ebfcbdaf92ebd245962b9e443c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
