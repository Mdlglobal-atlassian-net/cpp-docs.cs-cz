---
title: "Když třeba inicializovat objekty CWnd | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- window objects [MFC], when to initialize CWnd
- initializing CWnd objects [MFC]
- initializing objects [MFC], CWnd
- CWnd objects [MFC], when HWND is attached
- HWND, when attached to CWnd object
- CWnd objects [MFC], when to initialize
ms.assetid: 4d31bcb1-73db-4f2f-b71c-89b087569a10
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c2e9d99fe2f01111308a9a7a002aeefbf472a0b3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="when-to-initialize-cwnd-objects"></a>Kdy je třeba inicializovat objekty CWnd
Nelze vytvořit vlastní podřízenou windows nebo volat jakékoli funkce rozhraní API systému Windows v konstruktoru `CWnd`-odvozené objektu. Důvodem je, že `HWND` pro `CWnd` ještě nebyl vytvořen objekt. Inicializace nejvíce specifické pro systém Windows, jako je například přidávání podřízená okna, je třeba provést [OnCreate](../mfc/reference/cwnd-class.md#oncreate) obslužné rutiny zpráv.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Vytváření dokumentů, oken s rámečkem](../mfc/creating-document-frame-windows.md)  
  
-   [Vytváření dokumentů/zobrazení](../mfc/document-view-creation.md)  
  
## <a name="see-also"></a>Viz také  
 [Použití oken s rámečkem](../mfc/using-frame-windows.md)

