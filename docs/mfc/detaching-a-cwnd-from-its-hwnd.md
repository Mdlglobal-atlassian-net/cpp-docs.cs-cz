---
title: Odpojení třídy CWnd od jejího prvku HWND | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a776b4ff4799750c89a322379a063030db748eec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342676"
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>Odpojení třídy CWnd od jejího prvku HWND
Pokud budete potřebovat k obcházení objekt -`HWND` vztahu MFC poskytuje další `CWnd` – členská funkce [odpojení](../mfc/reference/cwnd-class.md#detach), který objekt okno C++ odpojí od časového období systému Windows. To brání destruktoru zničení období systému Windows, když objekt zničena.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Vytváření oken](../mfc/creating-windows.md)  
  
-   [Posloupnost likvidace okna](../mfc/window-destruction-sequence.md)  
  
-   [Přidělování a rušení přidělení paměti okna](../mfc/allocating-and-deallocating-window-memory.md)  
  
## <a name="see-also"></a>Viz také  
 [Objekty oken](../mfc/window-objects.md)

