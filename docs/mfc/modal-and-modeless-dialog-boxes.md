---
title: "Modální a nemodální dialogová okna | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC]
- MFC dialog boxes [MFC], modal
- modal dialog boxes [MFC]
ms.assetid: e83df336-5994-4b8f-8233-7942f997315b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 982bb8f195c3744246addc18d66bee953914dde4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="modal-and-modeless-dialog-boxes"></a>Modální a nemodální dialogová okna
Třídu můžete použít [CDialog](../mfc/reference/cdialog-class.md) ke správě dva druhy dialogová okna:  
  
-   *Modální dialogová okna*, které vyžadují, aby uživatel reagovat před pokračováním programu  
  
-   *Nemodální dialogová okna*, který Zůstaňte na obrazovce a jsou k dispozici pro použití v každém okamžiku ale povolit další aktivity uživatele  
  
 Úpravy prostředků a postupech pro vytvoření šablony dialogového okna jsou stejné pro modální a nemodální dialogová okna.  
  
 Vytváření dialogového okna pro váš program vyžaduje následující kroky:  
  
1.  Použití [editoru dialogového okna](../windows/dialog-editor.md) návrh dialogové okno a vytvořit její prostředek šablony dialogového okna.  
  
2.  Vytvoření třídy dialogového okna.  
  
3.  Připojení [prostředku dialogového okna Ovládací prvky pro obslužné rutiny zpráv](../windows/adding-event-handlers-for-dialog-box-controls.md) ve třídě dialog.  
  
4.  Přidání členů data související s ovládacími prvky dialogových oken a k určení [výměna dialogových dat](../mfc/dialog-data-exchange.md) a [ověření dat dialogové okno](../mfc/dialog-data-validation.md) ovládacích prvků.  
  
## <a name="see-also"></a>Viz také  
 [Dialogová okna](../mfc/dialog-boxes.md)   
 [Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)

