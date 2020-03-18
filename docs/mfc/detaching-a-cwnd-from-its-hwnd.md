---
title: Odpojení třídy CWnd od jejího prvku HWND
ms.date: 11/04/2016
helpviewer_keywords:
- HWND, detaching CWnd from
- removing HWNDs from CWnds
- CWnd objects [MFC], detaching from HWND
- detaching CWnds from HWNDs
- Detach method (CWnd class)
ms.assetid: 6efadf84-0517-4a3f-acfd-216e088f19c6
ms.openlocfilehash: f7a6f97ba9f1dd3a928a5450c1a899ce09a4ac5f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446955"
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>Odpojení třídy CWnd od jejího prvku HWND

Pokud potřebujete obejít relaci Object-`HWND`, knihovna MFC poskytuje jinou `CWnd` členskou funkci, [Odpojit](../mfc/reference/cwnd-class.md#detach), která odpojí objekt C++ okna z okna systému Windows. To brání destruktoru v zničení okna systému Windows, když je objekt zničen.

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace

- [Vytváření oken](../mfc/creating-windows.md)

- [Sekvence zničení okna](../mfc/window-destruction-sequence.md)

- [Přidělování a rušení přidělení paměti okna](../mfc/allocating-and-deallocating-window-memory.md)

## <a name="see-also"></a>Viz také

[Objekty oken](../mfc/window-objects.md)
