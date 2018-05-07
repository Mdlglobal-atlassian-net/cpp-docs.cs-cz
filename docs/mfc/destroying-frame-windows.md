---
title: Zničení oken s rámečkem | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- PostNcDestroy
dev_langs:
- C++
helpviewer_keywords:
- Default method [MFC]
- DestroyWindow method [MFC]
- frame windows [MFC], destroying
- OnNcDestroy method, and frame windows
- document frame windows [MFC], destroying
- destroying frame windows
- MFC, frame windows
- windows [MFC], destroying
- OnClose method [MFC]
- PostNcDestroy method [MFC]
ms.assetid: 5affca77-1999-4507-a2b2-9aa226611b4b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 81182c0e5633e19126d3036b5793de7658ad3d2a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="destroying-frame-windows"></a>Zničení oken s rámečkem
Rozhraní MFC framework spravovat odstraňování oken, jakož i vytváření pro tyto windows přidružené framework dokumentů a zobrazení. Pokud vytvoříte další windows, jste zodpovědní za jejich likvidace.  
  
 V rozhraní framework, když uživatel nezavře okno rámce okna výchozí [při zavření](../mfc/reference/cwnd-class.md#onclose) volání obslužné rutiny [destroywindow –](../mfc/reference/cwnd-class.md#destroywindow). Poslední člen funkce volána, když je zničen období systému Windows je [onncdestroy –](../mfc/reference/cwnd-class.md#onncdestroy), na které se některé čištění, zavolá [výchozí](../mfc/reference/cwnd-class.md#default) člen funkce provést čištění Windows a nakonec volá funkce člena virtuální [postncdestroy –](../mfc/reference/cwnd-class.md#postncdestroy). [CFrameWnd](../mfc/reference/cframewnd-class.md) implementace `PostNcDestroy` odstraní objekt okno C++. Nikdy byste neměli používat C++ **odstranit** operátor v okně s rámečkem. Místo nich se používá `DestroyWindow`.  
  
 Hlavní okno zavře, aplikace se zavře. Pokud existuje změní neuložené dokumenty, rozhraní zobrazí okno se zprávou požádat, pokud má být uložen v dokumentech a zajistí, že se příslušné dokumenty uloží v případě potřeby.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Vytváření dokumentů, oken s rámečkem](../mfc/creating-document-frame-windows.md)  
  
## <a name="see-also"></a>Viz také  
 [Použití oken s rámečkem](../mfc/using-frame-windows.md)

