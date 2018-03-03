---
title: "Přidělování a rušení přidělení paměti okna | Microsoft Docs"
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
- memory allocation, window objects
- memory deallocation
- storage for window objects [MFC]
- memory deallocation, window memory
- window objects [MFC], deallocating memory for
- storage for window objects [MFC], allocating
ms.assetid: 7c962539-8461-4846-b5ca-fe3b15c313dc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 294de3c4d4ecdfcb31f6e8c227bd8a3c6764268d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="allocating-and-deallocating-window-memory"></a>Přidělování a rušení přidělení paměti okna
Nepoužívejte C++ **odstranit** operátor ke zničení oken s rámečkem nebo zobrazení. Místo toho zavolejte `CWnd` – členská funkce `DestroyWindow`. Okna s rámečkem, proto by měla být přidělená v haldě pomocí operátoru **nové**. Buďte opatrní při přidělování okna s rámečkem na rámec zásobníku nebo globálně. Další windows by měla být přidělená na rámec zásobníku, kdykoli je to možné.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Vytváření oken](../mfc/creating-windows.md)  
  
-   [Posloupnost likvidace okna](../mfc/window-destruction-sequence.md)  
  
-   [Odpojení třídy CWnd od jejího prvku HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
## <a name="see-also"></a>Viz také  
 [Zničení objektů oken](../mfc/destroying-window-objects.md)

