---
title: Posloupnost likvidace okna | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- destruction, windows
- destroying windows
- sequence [MFC], window destruction
- CWnd objects [MFC], destruction sequence
- sequence [MFC]
- windows [MFC], destroying
ms.assetid: 2d819196-6240-415f-a308-db43745e616c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8b873d51f585336425537756064582eb709988f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="window-destruction-sequence"></a>Posloupnost likvidace okna
V rozhraní MFC framework, když uživatel nezavře okno rámce okna výchozí [při zavření](../mfc/reference/cwnd-class.md#onclose) volání obslužné rutiny [destroywindow –](../mfc/reference/cwnd-class.md#destroywindow). Poslední člen funkce volána, když je zničen období systému Windows je [onncdestroy –](../mfc/reference/cwnd-class.md#onncdestroy), na které se některé čištění, zavolá [výchozí](../mfc/reference/cwnd-class.md#default) člen funkce provést čištění Windows a nakonec volá funkce člena virtuální [postncdestroy –](../mfc/reference/cwnd-class.md#postncdestroy). [CFrameWnd](../mfc/reference/cframewnd-class.md) implementace `PostNcDestroy` odstraní objekt okno C++.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Přidělování a rušení přidělení paměti okna](../mfc/allocating-and-deallocating-window-memory.md)  
  
-   [Odpojení třídy CWnd od jejího prvku HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
## <a name="see-also"></a>Viz také  
 [Zničení objektů oken](../mfc/destroying-window-objects.md)

