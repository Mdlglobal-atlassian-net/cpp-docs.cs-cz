---
title: Styly oken s rámečkem (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 102b3a4c8372a53aada23ad448ce5dc1cf323a97
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343754"
---
# <a name="frame-window-styles-c"></a>Styly oken s rámečkem (C++)
Rámce windows získáte pomocí rozhraní jsou vhodné pro většinu programy, ale můžete získat větší flexibilita pomocí pokročilé funkce [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) a globální funkce MFC [afxregisterwndclass – ](../mfc/reference/application-information-and-management.md#afxregisterwndclass). `PreCreateWindow` člen funkcí `CWnd`.  
  
 Pokud použijete **ws_hscroll –** a **ws_vscroll –** styly do okna hlavního rámce, místo toho použijí se **MDICLIENT** okno, takže uživatelé mohou posunutím **MDICLIENT** oblasti.  
  
 Pokud okno **fws_addtotitle –** je nastaven bit stylu (který je ve výchozím nastavení), zobrazení informuje rámce okna jaké nápis, který se zobrazí v záhlaví okna na základě názvu zobrazení dokumentu.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Správa podřízených oken MDI (MDICLIENT)](../mfc/managing-mdi-child-windows.md), okno v rámci MDI rámce, který obsahuje podřízených oken MDI  
  
-   [Změna stylů okna vytvořeného rozhraním MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)  
  
-   [Styly oken](../mfc/reference/styles-used-by-mfc.md#window-styles)  
  
## <a name="see-also"></a>Viz také  
 [Okna s rámečkem](../mfc/frame-windows.md)

