---
title: "Zničení objektů oken | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- frame windows [MFC], destroying
- window objects [MFC], deleting
- window objects [MFC], destroying
- window objects [MFC], removing
ms.assetid: 3241fea0-c614-4a25-957d-20f21bd5fd0c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 67d2df7d72de079a0408847c433000a652ac6aaa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="destroying-window-objects"></a>Zničení objektů oken
Musí dát pozor s vlastními podřízená okna odstranění objektu okna C++ po dokončení se uživatel s okna. Pokud nejsou tyto objekty zničený, vaše aplikace nebude obnovit jejich paměti. Naštěstí rozhraní spravovat odstraňování oken, jakož i vytvoření oken s rámečkem, zobrazeních a dialogových oken. Pokud vytvoříte další windows, jste zodpovědní za jejich likvidace.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Posloupnost likvidace okna](../mfc/window-destruction-sequence.md)  
  
-   [Přidělování a rušení přidělení paměti okna](../mfc/allocating-and-deallocating-window-memory.md)  
  
-   [Odpojení třídy CWnd od jejího prvku HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
-   [Obecná posloupnost vytvoření okna](../mfc/general-window-creation-sequence.md)  
  
-   [Zničení oken s rámečkem](../mfc/destroying-frame-windows.md)  
  
## <a name="see-also"></a>Viz také  
 [Objekty oken](../mfc/window-objects.md)

