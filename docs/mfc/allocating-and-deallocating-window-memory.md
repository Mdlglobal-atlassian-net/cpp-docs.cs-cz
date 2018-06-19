---
title: Přidělování a rušení přidělení paměti okna | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a1364b4d29e2ccd2c9563359716eba6880df5436
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341456"
---
# <a name="allocating-and-deallocating-window-memory"></a>Přidělování a rušení přidělení paměti okna
Nepoužívejte C++ **odstranit** operátor ke zničení oken s rámečkem nebo zobrazení. Místo toho zavolejte `CWnd` – členská funkce `DestroyWindow`. Okna s rámečkem, proto by měla být přidělená v haldě pomocí operátoru **nové**. Buďte opatrní při přidělování okna s rámečkem na rámec zásobníku nebo globálně. Další windows by měla být přidělená na rámec zásobníku, kdykoli je to možné.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Vytváření oken](../mfc/creating-windows.md)  
  
-   [Posloupnost likvidace okna](../mfc/window-destruction-sequence.md)  
  
-   [Odpojení třídy CWnd od jejího prvku HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
## <a name="see-also"></a>Viz také  
 [Zničení objektů oken](../mfc/destroying-window-objects.md)

