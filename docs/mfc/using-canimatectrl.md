---
title: Používání atributu CAnimateCtrl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CAnimateCtrl
dev_langs:
- C++
helpviewer_keywords:
- animation controls [MFC], CAnimateCtrl class
- controls [MFC], animation
- CAnimateCtrl class [MFC], about CAnimateCtrl class [MFC]
ms.assetid: 696c0805-bef0-4e2e-a9e7-b37b9215b7f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5685d6aed00cd57f4329b3865f96fa75226d7cf6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-canimatectrl"></a>Používání atributu CAnimateCtrl
Ovládacího prvku animace reprezentována třída [CAnimateCtrl](../mfc/reference/canimatectrl-class.md), je okno, které zobrazí klip ve formátu Audio Video prokládaný (AVI) – ve standardním formátu video nebo zvuk systému Windows. Klip souborů AVI je řady rastrový obrázek snímků, jako jsou videa.  
  
 Vzhledem k tomu, že vaše vlákno pokračuje v provádění při souborů AVI klip se zobrazí, je jeden běžně používá pro ovládacího prvku animace indikovat aktivitu systému během časově náročná operace. Dialogové okno Windows najít například zobrazí přesunutí Lupa jako soubor výsledky hledání.  
  
 Ovládací prvky animace můžete přehrát pouze jednoduché klipů souborů AVI a nepodporují zvuku. (Úplný seznam omezení, najdete v části [CAnimateCtrl](../mfc/reference/canimatectrl-class.md).) Vzhledem k tomu, že jsou vážně omezené možnosti ovládacího prvku animace a mohou podléhat změnám, měli byste použít alternativu, jako je třeba Správa MCIWnd Pokud potřebujete zajistit přehrávání multimédií nebo záznam možnosti ovládací prvek. Další informace o řízení MCIWnd multimédií dokumentaci.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Použití ovládacího prvku animace](../mfc/using-an-animation-control.md)  
  
-   [Oznámení zaslaná z ovládacích prvků animace](../mfc/notifications-sent-by-animation-controls.md)  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky](../mfc/controls-mfc.md)

