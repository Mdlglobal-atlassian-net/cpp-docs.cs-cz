---
title: "Postupy: načtení prostředku pásu karet z aplikace MFC | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: ribbon resource [MFC], loading
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2384ff8b92936e646bc434583c6a20e07ccc85e7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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

