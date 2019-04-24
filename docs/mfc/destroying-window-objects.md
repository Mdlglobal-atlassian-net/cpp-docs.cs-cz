---
title: Likvidace objektů oken
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], destroying
- window objects [MFC], deleting
- window objects [MFC], destroying
- window objects [MFC], removing
ms.assetid: 3241fea0-c614-4a25-957d-20f21bd5fd0c
ms.openlocfilehash: f50d198f9868a70d25370f6c1399b66efaa5490b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297239"
---
# <a name="destroying-window-objects"></a>Likvidace objektů oken

Musíte věnovat pozornost s vlastním podřízená okna zničit okno objekt jazyka C++. Po dokončení se v okně uživatele. Pokud tyto objekty nejsou zničeny, vaše aplikace nebude obnovit jejich paměť. Naštěstí že rozhraní spravuje odstraňování oken, jakož i vytváření oken s rámečkem, zobrazeních a dialogových oknech. Pokud vytvoříte další okna, zodpovídáte za jejich zničení.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Posloupnost likvidace okna](../mfc/window-destruction-sequence.md)

- [Přidělování a rušení přidělení paměti okna](../mfc/allocating-and-deallocating-window-memory.md)

- [Odpojení třídy CWnd od jejího prvku HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)

- [Obecná posloupnost vytvoření okna](../mfc/general-window-creation-sequence.md)

- [Zničení oken s rámečkem](../mfc/destroying-frame-windows.md)

## <a name="see-also"></a>Viz také:

[Objekty oken](../mfc/window-objects.md)
