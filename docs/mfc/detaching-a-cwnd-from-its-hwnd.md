---
title: "Odpojení třídy CWnd od jejího prvku HWND | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CWnd
dev_langs:
- C++
helpviewer_keywords:
- HWND, detaching CWnd from
- removing HWNDs from CWnds
- CWnd objects [MFC], detaching from HWND
- detaching CWnds from HWNDs
- Detach method (CWnd class)
ms.assetid: 6efadf84-0517-4a3f-acfd-216e088f19c6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6aa24e0e9a0d9ee50a0c5c69e280ea7a727ca38b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>Odpojení třídy CWnd od jejího prvku HWND
Pokud budete potřebovat k obcházení objekt -`HWND` vztahu MFC poskytuje další `CWnd` – členská funkce [odpojení](../mfc/reference/cwnd-class.md#detach), který objekt okno C++ odpojí od časového období systému Windows. To brání destruktoru zničení období systému Windows, když objekt zničena.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Vytváření oken](../mfc/creating-windows.md)  
  
-   [Posloupnost likvidace okna](../mfc/window-destruction-sequence.md)  
  
-   [Přidělování a rušení přidělení paměti okna](../mfc/allocating-and-deallocating-window-memory.md)  
  
## <a name="see-also"></a>Viz také  
 [Objekty oken](../mfc/window-objects.md)

