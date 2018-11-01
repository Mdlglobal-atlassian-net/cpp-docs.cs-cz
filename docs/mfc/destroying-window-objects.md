---
title: Zničení objektů oken
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], destroying
- window objects [MFC], deleting
- window objects [MFC], destroying
- window objects [MFC], removing
ms.assetid: 3241fea0-c614-4a25-957d-20f21bd5fd0c
ms.openlocfilehash: 363ff2a4cee48b1660de87714d73c93e795017cd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488803"
---
# <a name="destroying-window-objects"></a>Zničení objektů oken

Musíte věnovat pozornost s vlastním podřízená okna zničit okno objekt jazyka C++. Po dokončení se v okně uživatele. Pokud tyto objekty nejsou zničeny, vaše aplikace nebude obnovit jejich paměť. Naštěstí že rozhraní spravuje odstraňování oken, jakož i vytváření oken s rámečkem, zobrazeních a dialogových oknech. Pokud vytvoříte další okna, zodpovídáte za jejich zničení.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Posloupnost likvidace okna](../mfc/window-destruction-sequence.md)

- [Přidělování a rušení přidělení paměti okna](../mfc/allocating-and-deallocating-window-memory.md)

- [Odpojení třídy CWnd od jejího prvku HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)

- [Obecná posloupnost vytvoření okna](../mfc/general-window-creation-sequence.md)

- [Zničení oken s rámečkem](../mfc/destroying-frame-windows.md)

## <a name="see-also"></a>Viz také

[Objekty oken](../mfc/window-objects.md)

