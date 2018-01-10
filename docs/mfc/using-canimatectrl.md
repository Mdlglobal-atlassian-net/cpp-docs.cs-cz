---
title: "Používání atributu CAnimateCtrl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CAnimateCtrl
dev_langs: C++
helpviewer_keywords:
- animation controls [MFC], CAnimateCtrl class
- controls [MFC], animation
- CAnimateCtrl class [MFC], about CAnimateCtrl class [MFC]
ms.assetid: 696c0805-bef0-4e2e-a9e7-b37b9215b7f0
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f27fd24c3c4334476c78ba0b59c90cbbb0d51f5d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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

