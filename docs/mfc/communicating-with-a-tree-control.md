---
title: "Komunikace s ovládacím prvkem strom | Microsoft Docs"
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
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2ef1188c9519e57c8132a2b20fc3b272d6c0ac51
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="communicating-with-a-tree-control"></a>Komunikace s ovládacím prvkem strom
Použít různé metody pro volání členských funkcí [CTreeCtrl](../mfc/reference/ctreectrl-class.md) objekt v závislosti na tom, jak byl vytvořen objekt:  
  
-   Pokud ovládací prvek stromu v dialogovém okně, použijte členské proměnné typu `CTreeCtrl` , které vytvoříte v třídy dialogového okna.  
  
-   Pokud ovládací prvek stromu podřízeného okna, použijte `CTreeCtrl` objektu (nebo ukazatel) jste použili k vytvoření objektu.  
  
-   Pokud používáte `CTreeView` objektu, použijte funkci [CTreeView::GetTreeCtrl](../mfc/reference/ctreeview-class.md#gettreectrl) získat odkaz na ovládací prvek stromu. Můžete inicializovat další odkaz s touto hodnotou nebo přiřadit adresu odkaz na `CTreeCtrl` ukazatel.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

