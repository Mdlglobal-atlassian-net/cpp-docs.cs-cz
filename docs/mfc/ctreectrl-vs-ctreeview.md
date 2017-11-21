---
title: CTreeCtrl vs. CTreeView | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CTreeCtrl
- CTreeView
dev_langs: C++
helpviewer_keywords:
- tree view controls
- CTreeCtrl class [MFC], vs. CTreeView class [MFC]
- CTreeView class [MFC], vs. CTreeCtrl class [MFC]
- tree controls [MFC], and tree view
ms.assetid: bba5af25-103f-4b53-84d3-071bc9bd6494
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b5a0dfd4f7b658cc585972ace1335a80b9bbd93a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ctreectrl-vs-ctreeview"></a>CTreeCtrl vs. CTreeView
MFC poskytuje dvě třídy, které zapouzdření ovládací prvky stromů: [CTreeCtrl](../mfc/reference/ctreectrl-class.md) a [CTreeView](../mfc/reference/ctreeview-class.md). Každá třída je užitečná v různých situacích.  
  
 Použití `CTreeCtrl` Pokud budete potřebovat prvku okno prostý podřízené; pro instanci v dialogovém okně. Zejména by chcete použít `CTreeCtrl` Pokud bude jiné podřízené ovládací prvky v okně jako typický dialogové okno.  
  
 Použití `CTreeView` kdy se má ovládací prvek stromu tak, aby fungoval jako okno zobrazení v architektuře document/view i ovládacím prvkem strom. A `CTreeView` bude zabírat celého klienta oken s rámečkem nebo rozdělovače oken. Jej bude automaticky nastavena velikost při změně velikosti jeho nadřazeného okna a může zpracovat příkaz zprávy z nabídek, klávesy akcelerátoru a panelů nástrojů. Vzhledem k tomu, že ovládacím prvkem strom obsahuje data potřebná k zobrazení stromu, odpovídající objekt dokumentu nemusí být složité – můžete použít i [CDocument](../mfc/reference/cdocument-class.md) jako typ dokumentu v šabloně dokumentu.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

