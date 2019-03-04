---
title: Odpojení třídy CWnd od jejího prvku HWND
ms.date: 11/04/2016
f1_keywords:
- CWnd
helpviewer_keywords:
- HWND, detaching CWnd from
- removing HWNDs from CWnds
- CWnd objects [MFC], detaching from HWND
- detaching CWnds from HWNDs
- Detach method (CWnd class)
ms.assetid: 6efadf84-0517-4a3f-acfd-216e088f19c6
ms.openlocfilehash: 259af94958f88643e9c3ce725b25c4e92cc38226
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271122"
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>Odpojení třídy CWnd od jejího prvku HWND

Pokud chcete obejít objekt -`HWND` vztah, knihovna MFC poskytuje další `CWnd` členskou funkci, [odpojit](../mfc/reference/cwnd-class.md#detach), který Odpojí okno objekt jazyka C++ z okna Windows. Tím se destruktoru zabrání zničení okna Windows při zničení objektu.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Vytváření oken](../mfc/creating-windows.md)

- [Posloupnost likvidace okna](../mfc/window-destruction-sequence.md)

- [Přidělování a rušení přidělení paměti okna](../mfc/allocating-and-deallocating-window-memory.md)

## <a name="see-also"></a>Viz také:

[Objekty oken](../mfc/window-objects.md)
