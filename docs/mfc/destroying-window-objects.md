---
title: Zničení objektů oken | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- frame windows [MFC], destroying
- window objects [MFC], deleting
- window objects [MFC], destroying
- window objects [MFC], removing
ms.assetid: 3241fea0-c614-4a25-957d-20f21bd5fd0c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3aacb01d945429bc36543f78e3635c39ef58223d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343373"
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

