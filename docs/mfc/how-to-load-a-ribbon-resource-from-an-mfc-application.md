---
title: 'Postupy: načtení prostředku pásu karet z aplikace MFC | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ribbon resource [MFC], loading
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b014e1725ae6c5043c051242a74e29338c3ef2d6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-load-a-ribbon-resource-from-an-mfc-application"></a>Postupy: Načtení prostředku pásu karet z aplikace MFC
Chcete-li použít prostředek pásu karet v aplikaci, upravte aplikaci k načtení prostředku pásu karet.  
  
### <a name="to-load-a-ribbon-resource"></a>Načtení prostředku pásu karet  
  
1.  Deklarovat `Ribbon Control` objekt v `CMainFrame` třídy.  
  
 ```  
    CMFCRibbonBar m_wndRibbonBar;   
 ```  
  
2.  V `CMainFrame::OnCreate`, vytvoření a inicializace ovládacího prvku pásu karet.  
  
 ```  
    if (!m_wndRibbonBar.Create (this))  
 {  
    return -1;  
 }  
 
    if (!m_wndRibbonBar.LoadFromResource(IDR_RIBBON))  
 {  
    return -1;  
 }  
 ```  
  
## <a name="see-also"></a>Viz také  
 [Návrhář pásu karet (MFC)](../mfc/ribbon-designer-mfc.md)

