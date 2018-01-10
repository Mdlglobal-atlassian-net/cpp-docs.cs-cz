---
title: Struktura CMFCTabToolTipInfo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: CMFCTabToolTipInfo
dev_langs: C++
helpviewer_keywords: CMFCTabToolTipInfo struct
ms.assetid: 9c3b3fb9-1497-4d59-932b-0da9348dd5e2
caps.latest.revision: "27"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4cfb12ca9660259a4451d2841a921a566cf54505
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfctabtooltipinfo-structure"></a>Struktura CMFCTabToolTipInfo
Tato struktura poskytuje informace o kartě MDI, který uživatel ukazatele myši.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct CMFCTabToolTipInfo  
```  
  
## <a name="members"></a>Členové  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCTabToolTipInfo::m_nTabIndex](#m_ntabindex)|Určuje index ovládacího prvku karta.|  
|[CMFCTabToolTipInfo::m_pTabWnd](#m_ptabwnd)|Ukazatel na ovládacího prvku karta.|  
|[CMFCTabToolTipInfo::m_strText](#m_strtext)|Text popisku.|  
  
## <a name="remarks"></a>Poznámky  
 Ukazatel na `CMFCTabToolTipInfo` struktura je předán jako parametr `AFX_WM_ON_GET_TAB_TOOLTIP` zprávy. Tato zpráva se vygeneruje, když MDI karty jsou povolené a uživatel bude umístěn nad ovládacího prvku karta.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob `CMFCTabToolTipInfo` se používá v [MDITabsDemo ukázka: MFC – záložkami aplikace MDI](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CMFCTabToolTipInfo](../../mfc/reference/cmfctabtooltipinfo-structure.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxbasetabctrl.h  
  
##  <a name="m_ntabindex"></a>CMFCTabToolTipInfo::m_nTabIndex  
 Určuje index ovládacího prvku karta.  
  
```  
int m_nTabIndex;  
```  
  
### <a name="remarks"></a>Poznámky  
 Index na kartě, přes který uživatel ukazatele.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob `m_nTabIndex` se používá v [MDITabsDemo ukázka: MFC – záložkami aplikace MDI](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]  
  
##  <a name="m_ptabwnd"></a>CMFCTabToolTipInfo::m_pTabWnd  
 Ukazatel na ovládacího prvku karta.  
  
```  
CMFCBaseTabCtrl* m_pTabWnd;  
```  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob `m_pTabWnd` se používá v [MDITabsDemo ukázka: MFC – záložkami aplikace MDI](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]  
  
##  <a name="m_strtext"></a>CMFCTabToolTipInfo::m_strText  
 Text popisku.  
  
```  
CString m_strText;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud je řetězec prázdný, se nezobrazí popisek.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob `m_strText` se používá v [MDITabsDemo ukázka: MFC – záložkami aplikace MDI](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)
