---
title: "Komunikace s ovládacím prvkem strom | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 33835dcaa40b217e9248e5c03b775f968332b687
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="communicating-with-a-tree-control"></a>Komunikace s ovládacím prvkem strom
Použít různé metody pro volání členských funkcí [CTreeCtrl](../mfc/reference/ctreectrl-class.md) objekt v závislosti na tom, jak byl vytvořen objekt:  
  
-   Pokud ovládací prvek stromu v dialogovém okně, použijte členské proměnné typu `CTreeCtrl` , které vytvoříte v třídy dialogového okna.  
  
-   Pokud ovládací prvek stromu podřízeného okna, použijte `CTreeCtrl` objektu (nebo ukazatel) jste použili k vytvoření objektu.  
  
-   Pokud používáte `CTreeView` objektu, použijte funkci [CTreeView::GetTreeCtrl](../mfc/reference/ctreeview-class.md#gettreectrl) získat odkaz na ovládací prvek stromu. Můžete inicializovat další odkaz s touto hodnotou nebo přiřadit adresu odkaz na `CTreeCtrl` ukazatel.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

