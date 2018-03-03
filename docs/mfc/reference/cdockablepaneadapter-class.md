---
title: "Třída CDockablePaneAdapter | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDockablePaneAdapter
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::GetWrappedWnd
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::LoadState
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::SaveState
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::SetWrappedWnd
dev_langs:
- C++
helpviewer_keywords:
- CDockablePaneAdapter [MFC], GetWrappedWnd
- CDockablePaneAdapter [MFC], LoadState
- CDockablePaneAdapter [MFC], SaveState
- CDockablePaneAdapter [MFC], SetWrappedWnd
ms.assetid: 6ed6cf82-f39c-4d0c-bf7c-8641495cf8f3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5bb0e10490a381784e40167e16d1c7ec4e7e1a19
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cdockablepaneadapter-class"></a>CDockablePaneAdapter – třída
Poskytuje ukotvení podporu pro `CWnd`-odvozené podokna.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDockablePaneAdapter : public CDockablePane  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDockablePaneAdapter::GetWrappedWnd](#getwrappedwnd)|Vrátí zabalené okna.|  
|[CDockablePaneAdapter::LoadState](#loadstate)|(Přepisuje [CDockablePane::LoadState](http://msdn.microsoft.com/en-us/96110136-4f46-4764-8a76-3b4abaf77917).)|  
|[CDockablePaneAdapter::SaveState](#savestate)|(Přepisuje [CDockablePane::SaveState](http://msdn.microsoft.com/en-us/c5c24249-8d0d-46cb-96d9-9f5c6dc191db).)|  
|[CDockablePaneAdapter::SetWrappedWnd](#setwrappedwnd)||  
  
## <a name="remarks"></a>Poznámky  
 Obvykle rozhraní vytváří instance objektů této třídy při použití [CMFCBaseTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) nebo [CMFCBaseTabCtrl::InsertTab](../../mfc/reference/cmfcbasetabctrl-class.md#inserttab) metody.  
  
 Pokud chcete přizpůsobit `CDockablePaneAdapter` chování, stačí odvodit novou třídu z něj a nastavit informace o třídě runtime okno s kartami pomocí [CMFCBaseTabCtrl::SetDockingBarWrapperRTC](../../mfc/reference/cmfcbasetabctrl-class.md#setdockingbarwrapperrtc).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md) [CPane](../../mfc/reference/cpane-class.md) [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxDockablePaneAdapter.h  
  
##  <a name="getwrappedwnd"></a>CDockablePaneAdapter::GetWrappedWnd  
 Vrátí základní okna pro adaptér lze ukotvit podokně.  
  
```  
virtual CWnd* GetWrappedWnd() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na zabalené okna.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce můžete zabalené k oknu přístup.  
  
##  <a name="loadstate"></a>CDockablePaneAdapter::LoadState  
 Stav v podokně načte z registru.  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszProfileName`  
 Název profilu.  
  
 [v]`nIndex`  
 Profil index.  
  
 [v]`uiID`  
 ID podokně.  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="savestate"></a>CDockablePaneAdapter::SaveState  
 Uloží stav v podokně do registru.  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszProfileName`  
 Název profilu.  
  
 [v]`nIndex`  
 Profil index (výchozí hodnota je ID ovládacího prvku okna).  
  
 [v]`uiID`  
 ID podokně.  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setwrappedwnd"></a>CDockablePaneAdapter::SetWrappedWnd  
 Nastaví základní okna pro adaptér lze ukotvit podokně.  
  
```  
virtual BOOL SetWrappedWnd(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWnd`  
 Ukazatel na okna pro adaptér podokně zabalit.  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CDockablePane – třída](../../mfc/reference/cdockablepane-class.md)
