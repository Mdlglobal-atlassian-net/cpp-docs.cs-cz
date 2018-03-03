---
title: "Třída CMFCBaseToolBar | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCBaseToolBar
- AFXBASETOOLBAR/CMFCBaseToolBar
- AFXBASETOOLBAR/CMFCBaseToolBar::GetDockingMode
- AFXBASETOOLBAR/CMFCBaseToolBar::GetMinSize
- AFXBASETOOLBAR/CMFCBaseToolBar::OnAfterChangeParent
dev_langs:
- C++
helpviewer_keywords:
- CMFCBaseToolBar [MFC], GetDockingMode
- CMFCBaseToolBar [MFC], GetMinSize
- CMFCBaseToolBar [MFC], OnAfterChangeParent
ms.assetid: 5d79206d-55e4-46f8-b1b8-042e34d7f9da
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4c57a09465a342a74e69d199d725ec64e7c60ca2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcbasetoolbar-class"></a>CMFCBaseToolBar – třída
Základní třída pro panely nástrojů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCBaseToolBar : public CPane  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|`CMFCBaseToolBar::CMFCBaseToolBar`|Výchozí konstruktor.|  
|`CMFCBaseToolBar::~CMFCBaseToolBar`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|`CMFCBaseToolBar::CreateObject`|Rozhraní používá k vytvoření dynamických instance tohoto typu třídy.|  
|[CMFCBaseToolBar::GetDockingMode](#getdockingmode)|Vrátí hodnotu režimu ukotvení. (Přepisuje [CBasePane::GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode).)|  
|[CMFCBaseToolBar::GetMinSize](#getminsize)|Vrátí minimální velikost panelu nástrojů. (Přepisuje [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).)|  
|[CMFCBaseToolBar::OnAfterChangeParent](#onafterchangeparent)|Voláno rámcem po provedení změn v podokně nadřazené. (Přepisuje [CBasePane::OnAfterChangeParent](../../mfc/reference/cbasepane-class.md#onafterchangeparent).)|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxbasetoolbar.h  
  
##  <a name="getdockingmode"></a>CMFCBaseToolBar::GetDockingMode  
 Vrátí hodnotu režimu ukotvení.  
  
```  
virtual AFX_DOCK_TYPE GetDockingMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukotvení režim.  
  
##  <a name="getminsize"></a>CMFCBaseToolBar::GetMinSize  
 Vrátí minimální velikost panelu nástrojů.  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`size`  
 Minimální velikost panelu nástrojů.  
  
##  <a name="onafterchangeparent"></a>CMFCBaseToolBar::OnAfterChangeParent  
 Voláno rámcem po provedení změn v podokně nadřazené.  
  
```  
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWndOldParent`  
 Ukazatel na předchozí nadřazeného okna.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)
