---
title: "Třídy oken s rámečkem | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- frame window classes [MFC], about frame window classes
- frame window classes [MFC]
- windows [MFC], MDI
- document frame windows [MFC], classes
- single document interface (SDI), frame windows
- window classes [MFC], frame
- MFC, frame windows
- MDI [MFC], frame windows
- classes [MFC], window
ms.assetid: c27e43a7-8ad0-4759-b1b7-43f4725f4132
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b5e67ef155c029285d0b306ca2d05179e993de78
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="frame-window-classes"></a>Třídy oken s rámečkem
Každá aplikace má jeden "hlavního rámce okna," plochy okno, které obvykle má název aplikace v jeho záhlaví. Každý dokument má obvykle jeden "rámce okna dokumentu." Okně s rámečkem dokument obsahuje alespoň jedno zobrazení, který představuje data dokumentu.  
  
## <a name="frame-windows-in-sdi-and-mdi-applications"></a>Okna s rámečkem v SDI a MDI aplikace  
 Aplikace SDI je jeden odvozené od třídy oken s rámečkem [CFrameWnd](../mfc/reference/cframewnd-class.md). Toto okno se hlavního rámce okna a rámce okna dokumentu. Pro aplikace MDI hlavního okna rámce je odvozená od třídy [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md), a v dokumentu okna s rámečkem, které jsou podřízených oken MDI, jsou odvozena od třídy [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md).  
  
## <a name="use-the-frame-window-class-or-derive-from-it"></a>Použití třídy oken s rámečkem nebo z něj odvodit  
 Tyto třídy poskytují většinu oken s rámečkem funkcí, které potřebujete pro vaše aplikace. Za normálních okolností výchozí chování a vzhled, které poskytují bude vyhovovat vašim potřebám. Pokud potřebujete další funkce, odvozujte z těchto tříd.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Třídy oken s rámečkem vytvořené průvodcem aplikací](../mfc/frame-window-classes-created-by-the-application-wizard.md)  
  
-   [Styly oken s rámečkem](../mfc/frame-window-styles-cpp.md)  
  
-   [Změna stylů okna vytvořeného rozhraním MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)  
  
## <a name="see-also"></a>Viz také  
 [Okna s rámečkem](../mfc/frame-windows.md)

