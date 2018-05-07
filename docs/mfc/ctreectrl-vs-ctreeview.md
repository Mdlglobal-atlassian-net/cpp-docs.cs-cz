---
title: CTreeCtrl vs. CTreeView | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CTreeCtrl
- CTreeView
dev_langs:
- C++
helpviewer_keywords:
- tree view controls
- CTreeCtrl class [MFC], vs. CTreeView class [MFC]
- CTreeView class [MFC], vs. CTreeCtrl class [MFC]
- tree controls [MFC], and tree view
ms.assetid: bba5af25-103f-4b53-84d3-071bc9bd6494
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d71048b6f03f7f1b4400c0a88c178d1b97acdf2f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ctreectrl-vs-ctreeview"></a>CTreeCtrl vs. CTreeView
MFC poskytuje dvě třídy, které zapouzdření ovládací prvky stromů: [CTreeCtrl](../mfc/reference/ctreectrl-class.md) a [CTreeView](../mfc/reference/ctreeview-class.md). Každá třída je užitečná v různých situacích.  
  
 Použití `CTreeCtrl` Pokud budete potřebovat prvku okno prostý podřízené; pro instanci v dialogovém okně. Zejména by chcete použít `CTreeCtrl` Pokud bude jiné podřízené ovládací prvky v okně jako typický dialogové okno.  
  
 Použití `CTreeView` kdy se má ovládací prvek stromu tak, aby fungoval jako okno zobrazení v architektuře document/view i ovládacím prvkem strom. A `CTreeView` bude zabírat celého klienta oken s rámečkem nebo rozdělovače oken. Jej bude automaticky nastavena velikost při změně velikosti jeho nadřazeného okna a může zpracovat příkaz zprávy z nabídek, klávesy akcelerátoru a panelů nástrojů. Vzhledem k tomu, že ovládacím prvkem strom obsahuje data potřebná k zobrazení stromu, odpovídající objekt dokumentu nemusí být složité – můžete použít i [CDocument](../mfc/reference/cdocument-class.md) jako typ dokumentu v šabloně dokumentu.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

