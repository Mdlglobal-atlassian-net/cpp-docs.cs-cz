---
title: Posloupnost likvidace okna | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- destruction, windows
- destroying windows
- sequence [MFC], window destruction
- CWnd objects [MFC], destruction sequence
- sequence [MFC]
- windows [MFC], destroying
ms.assetid: 2d819196-6240-415f-a308-db43745e616c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 04ef1aa9dadbbe965ab17945da681a0e1189c404
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446635"
---
# <a name="window-destruction-sequence"></a>Posloupnost likvidace okna

V rámci MFC, když uživatel zavře okno rámce okna. výchozí [při zavření](../mfc/reference/cwnd-class.md#onclose) volání obsluhy [destroywindow –](../mfc/reference/cwnd-class.md#destroywindow). Poslední členská funkce volána, když v okně Windows je zničen [onncdestroy –](../mfc/reference/cwnd-class.md#onncdestroy), která dělá to trochu pořádek volá [výchozí](../mfc/reference/cwnd-class.md#default) členské funkce, vyčistěte Windows a nakonec volá virtuální členská funkce [postncdestroy –](../mfc/reference/cwnd-class.md#postncdestroy). [CFrameWnd](../mfc/reference/cframewnd-class.md) provádění `PostNcDestroy` odstraní okno objekt jazyka C++.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Přidělování a rušení přidělení paměti okna](../mfc/allocating-and-deallocating-window-memory.md)

- [Odpojení třídy CWnd od jejího prvku HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>Viz také

[Zničení objektů oken](../mfc/destroying-window-objects.md)

