---
title: Komunikace s ovládacím prvkem strom | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af0b248d5e32b535c23cc17b48efdd551dad7a2c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341994"
---
# <a name="communicating-with-a-tree-control"></a>Komunikace s ovládacím prvkem strom
Použít různé metody pro volání členských funkcí [CTreeCtrl](../mfc/reference/ctreectrl-class.md) objekt v závislosti na tom, jak byl vytvořen objekt:  
  
-   Pokud ovládací prvek stromu v dialogovém okně, použijte členské proměnné typu `CTreeCtrl` , které vytvoříte v třídy dialogového okna.  
  
-   Pokud ovládací prvek stromu podřízeného okna, použijte `CTreeCtrl` objektu (nebo ukazatel) jste použili k vytvoření objektu.  
  
-   Pokud používáte `CTreeView` objektu, použijte funkci [CTreeView::GetTreeCtrl](../mfc/reference/ctreeview-class.md#gettreectrl) získat odkaz na ovládací prvek stromu. Můžete inicializovat další odkaz s touto hodnotou nebo přiřadit adresu odkaz na `CTreeCtrl` ukazatel.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

