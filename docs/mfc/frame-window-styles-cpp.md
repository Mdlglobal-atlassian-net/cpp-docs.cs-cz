---
title: "Styly oken s rámečkem (C++) | Microsoft Docs"
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
- window styles [MFC]
- PreCreateWindow method, setting window styles
- windows [MFC], MFC
- frame windows [MFC], styles
- MFC, frame windows
- styles [MFC], windows
ms.assetid: fc5058c1-eec8-48d8-9f76-3fc01cfa53f7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a5bdc0204c538f476c791657d8b29a28b7baedd4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="frame-window-styles-c"></a>Styly oken s rámečkem (C++)
Rámce windows získáte pomocí rozhraní jsou vhodné pro většinu programy, ale můžete získat větší flexibilita pomocí pokročilé funkce [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) a globální funkce MFC [afxregisterwndclass – ](../mfc/reference/application-information-and-management.md#afxregisterwndclass). `PreCreateWindow`člen funkcí `CWnd`.  
  
 Pokud použijete **ws_hscroll –** a **ws_vscroll –** styly do okna hlavního rámce, místo toho použijí se **MDICLIENT** okno, takže uživatelé mohou posunutím **MDICLIENT** oblasti.  
  
 Pokud okno **fws_addtotitle –** je nastaven bit stylu (který je ve výchozím nastavení), zobrazení informuje rámce okna jaké nápis, který se zobrazí v záhlaví okna na základě názvu zobrazení dokumentu.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Správa podřízených oken MDI (MDICLIENT)](../mfc/managing-mdi-child-windows.md), okno v rámci MDI rámce, který obsahuje podřízených oken MDI  
  
-   [Změna stylů okna vytvořeného rozhraním MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)  
  
-   [Styly oken](../mfc/reference/styles-used-by-mfc.md#window-styles)  
  
## <a name="see-also"></a>Viz také  
 [Okna s rámečkem](../mfc/frame-windows.md)

