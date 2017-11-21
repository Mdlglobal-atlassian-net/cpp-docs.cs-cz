---
title: "CListView – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CListView
- AFXCVIEW/CListView
- AFXCVIEW/CListView::CListView
- AFXCVIEW/CListView::GetListCtrl
- AFXCVIEW/CListView::RemoveImageList
dev_langs: C++
helpviewer_keywords:
- CListView [MFC], CListView
- CListView [MFC], GetListCtrl
- CListView [MFC], RemoveImageList
ms.assetid: 7626bdb2-a1b8-4eab-b631-6743710a8432
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a54a66efdaa6589628812a60292767a0e42c2e97
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="clistview-class"></a>CListView – třída
Používání ovládacího prvku seznam, zjednodušuje [CListCtrl](../../mfc/reference/clistctrl-class.md), třídu, která zapouzdřuje funkce ovládací prvek seznamu, s architekturou MFC na zobrazení dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CListView : public CCtrlView  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CListView::CListView](#clistview)|Vytvoří `CListView` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CListView::GetListCtrl](#getlistctrl)|Vrátí ovládací prvek seznamu, které jsou přidružené k zobrazení.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CListView::RemoveImageList](#removeimagelist)|Odebere zadanou bitovou kopii seznamu ze zobrazení seznamu.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace o této architektury, najdete v článku Přehled pro [CView](../../mfc/reference/cview-class.md) třídy a křížové odkazy citovalo existuje.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CListView`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcview.h  
  
##  <a name="clistview"></a>CListView::CListView  
 Vytvoří `CListView` objektu.  
  
```  
CListView();
```  
  
##  <a name="getlistctrl"></a>CListView::GetListCtrl  
 Volání této funkce člen získat odkaz na ovládací prvek seznamu, které jsou přidružené k zobrazení.  
  
```  
CListCtrl& GetListCtrl() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na ovládací prvek seznamu, které jsou přidružené k zobrazení.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCListView#7](../../atl/reference/codesnippet/cpp/clistview-class_1.cpp)]  
  
##  <a name="removeimagelist"></a>CListView::RemoveImageList  
 Odebere zadanou bitovou kopii seznamu ze zobrazení seznamu.  
  
```  
void RemoveImageList(int nImageList);
```  
  
### <a name="parameters"></a>Parametry  
 `nImageList`  
 Index založený na nule bitové kopie k odebrání.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC ROWLIST](../../visual-cpp-samples.md)   
 [CCtrlView – třída](../../mfc/reference/cctrlview-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CCtrlView – třída](../../mfc/reference/cctrlview-class.md)
