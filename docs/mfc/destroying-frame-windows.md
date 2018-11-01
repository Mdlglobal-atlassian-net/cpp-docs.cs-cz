---
title: Zničení oken s rámečkem
ms.date: 11/04/2016
f1_keywords:
- PostNcDestroy
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
ms.openlocfilehash: f3b3e022f869a3019f80ba5ee082ce5a959853a9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50645399"
---
# <a name="destroying-frame-windows"></a>Zničení oken s rámečkem

Rozhraní MFC framework spravuje odstraňování oken, jakož i vytváření pro tato okna přidružené framework dokumentů a zobrazení. Pokud vytvoříte další okna, zodpovídáte za jejich zničení.

V rozhraní, když uživatel zavře okno rámce okna. výchozí [při zavření](../mfc/reference/cwnd-class.md#onclose) volání obsluhy [destroywindow –](../mfc/reference/cwnd-class.md#destroywindow). Poslední členská funkce volána, když v okně Windows je zničen [onncdestroy –](../mfc/reference/cwnd-class.md#onncdestroy), která dělá to trochu pořádek volá [výchozí](../mfc/reference/cwnd-class.md#default) členské funkce, vyčistěte Windows a nakonec volá virtuální členská funkce [postncdestroy –](../mfc/reference/cwnd-class.md#postncdestroy). [CFrameWnd](../mfc/reference/cframewnd-class.md) provádění `PostNcDestroy` odstraní okno objekt jazyka C++. Nikdy byste neměli používat C++ **odstranit** operátor v okně rámce. Místo nich se používá `DestroyWindow`.

Když hlavní okno se zavře, aplikace se zavře. Pokud upravované neuložené dokumenty, rozhraní zobrazí okno se zprávou požádat, pokud by měla uložit dokumenty a zajišťuje, že odpovídající dokumenty jsou uloženy v případě potřeby.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Vytváření oken s rámečkem v dokumentu](../mfc/creating-document-frame-windows.md)

## <a name="see-also"></a>Viz také

[Použití oken s rámečkem](../mfc/using-frame-windows.md)

