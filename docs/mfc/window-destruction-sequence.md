---
title: Posloupnost likvidace okna
ms.date: 11/04/2016
helpviewer_keywords:
- destruction, windows
- destroying windows
- sequence [MFC], window destruction
- CWnd objects [MFC], destruction sequence
- sequence [MFC]
- windows [MFC], destroying
ms.assetid: 2d819196-6240-415f-a308-db43745e616c
ms.openlocfilehash: d4592e6ac0077d6bc335b50f2d67b140402b4fe2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287658"
---
# <a name="window-destruction-sequence"></a>Posloupnost likvidace okna

V rámci MFC, když uživatel zavře okno rámce okna. výchozí [při zavření](../mfc/reference/cwnd-class.md#onclose) volání obsluhy [destroywindow –](../mfc/reference/cwnd-class.md#destroywindow). Poslední členská funkce volána, když v okně Windows je zničen [onncdestroy –](../mfc/reference/cwnd-class.md#onncdestroy), která dělá to trochu pořádek volá [výchozí](../mfc/reference/cwnd-class.md#default) členské funkce, vyčistěte Windows a nakonec volá virtuální členská funkce [postncdestroy –](../mfc/reference/cwnd-class.md#postncdestroy). [CFrameWnd](../mfc/reference/cframewnd-class.md) provádění `PostNcDestroy` odstraní okno objekt jazyka C++.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Přidělování a rušení přidělení paměti okna](../mfc/allocating-and-deallocating-window-memory.md)

- [Odpojení třídy CWnd od jejího prvku HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>Viz také:

[Zničení objektů oken](../mfc/destroying-window-objects.md)
