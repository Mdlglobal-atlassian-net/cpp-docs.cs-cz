---
title: "Třída CMFCDragFrameImpl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDragFrameImpl
dev_langs:
- C++
helpviewer_keywords:
- CMFCDragFrameImpl class [MFC]
ms.assetid: 500cd824-8188-43c2-8754-b7bb46b5648a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2fe293a8fa64cb323771db4f0f2929204790d210
ms.sourcegitcommit: 185e11ab93af56ffc650fe42fb5ccdf1683e3847
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2018
---
# <a name="cmfcdragframeimpl-class"></a>CMFCDragFrameImpl – třída
`CMFCDragFrameImpl` Třída nevykresluje přetáhněte obdélníku, která se zobrazí, když uživatel nastavuje tažením podokno v režimu standardní ukotvení.  
   [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
   
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCDragFrameImpl  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato třída objektu vložené v každé [CPane třída](../../mfc/reference/cpane-class.md) objektu. Proto jednotlivých panelech, který používá `CanFloat` metoda zobrazí obdélníku přetažení, když se uživatel nastavuje tažením ho.  
  
 Tloušťka rámeček přetáhněte můžete řídit pomocí [AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](afx-global-data-structure.md#m_ndragframethicknessfloat) a [AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](afx-global-data-structure.md#m_ndragframethicknessdock).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CMFCDragFrameImpl](../../mfc/reference/cmfcdragframeimpl-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdragframeimpl.h  
  
##  <a name="enddrawdragframe"></a>CMFCDragFrameImpl::EndDrawDragFrame  

  
```  
void EndDrawDragFrame(BOOL bClearInternalRects = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `bClearInternalRects`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="init"></a>CMFCDragFrameImpl::Init  

  
```  
void Init(CWnd* pDraggedWnd);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pDraggedWnd`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="movedragframe"></a>CMFCDragFrameImpl::MoveDragFrame  

  
```  
void MoveDragFrame(BOOL bForceMove = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `bForceMove`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="placetabpredocking"></a>CMFCDragFrameImpl::PlaceTabPreDocking  

  
```  
void PlaceTabPreDocking(
    CBaseTabbedPane* pTabbedBar,  
    BOOL bFirstTime);  
  
void PlaceTabPreDocking(CWnd* pCBarToPlaceOn);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pTabbedBar`  
 [in] `bFirstTime`  
 [in] `pCBarToPlaceOn`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="removetabpredocking"></a>CMFCDragFrameImpl::RemoveTabPreDocking  

  
```  
void RemoveTabPreDocking(CDockablePane* pOldTargetBar = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pOldTargetBar`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="resetstate"></a>CMFCDragFrameImpl::ResetState  

  
```  
void ResetState();
```  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CPane – třída](../../mfc/reference/cpane-class.md)