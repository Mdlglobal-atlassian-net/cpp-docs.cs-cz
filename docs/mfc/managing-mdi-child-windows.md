---
title: "Správa podřízených oken MDI | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MDICLIENT
dev_langs: C++
helpviewer_keywords:
- MDI [MFC], child windows
- child windows [MFC], and MDICLIENT window
- MDICLIENT window [MFC]
- windows [MFC], MDI
- frame windows [MFC], MDI child windows
- child windows [MFC]
- MDI [MFC], frame windows
ms.assetid: 1828d96e-a561-48ae-a661-ba9701de6bee
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5ebcd6e484385ada3cd3d5ccfe450e7e25f539eb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="managing-mdi-child-windows"></a>Správa podřízených oken MDI
Oken MDI hlavního rámce, (jeden na aplikaci) obsahovat speciální podřízeného okna volat **MDICLIENT** okno. **MDICLIENT** okno spravuje klientské oblasti hlavního okna rámce a sama má podřízená okna: okna dokumentu odvozen od `CMDIChildWnd`. Protože windows dokumentu okna s rámečkem sami (podřízených oken MDI), budou také obsahovat vlastní podřízené objekty. Ve všech těchto případech nadřazeného okna spravuje jeho podřízených systému windows a předá některé příkazy k nim.  
  
 V rámci okna aplikace MDI spravuje okně s rámečkem **MDICLIENT** okně přemístění ve spojení s ovládací pruhy. **MDICLIENT** okně zase spravuje všechny MDI podřízená rámce okna. Následující obrázek znázorňuje vztah mezi rámce okna MDI, jeho **MDICLIENT** okna a jeho podřízená dokumentu rámce okna.  
  
 ![Podřízená okna v rámci okna aplikace MDI](../mfc/media/vc37gb1.gif "vc37gb1")  
Okna s rámečkem MDI a podřízené položky  
  
 Rámce okna MDI se také funguje ve spojení s aktuální podřízeného okna MDI, jestliže existuje. Rámec okna MDI deleguje příkaz zpráv podřízeného MDI, než se pokusí zpracovat sám sebe.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Vytváření dokumentů, oken s rámečkem](../mfc/creating-document-frame-windows.md)  
  
-   [Styly oken s rámečkem](../mfc/frame-window-styles-cpp.md)  
  
## <a name="see-also"></a>Viz také  
 [Použití oken s rámečkem](../mfc/using-frame-windows.md)

