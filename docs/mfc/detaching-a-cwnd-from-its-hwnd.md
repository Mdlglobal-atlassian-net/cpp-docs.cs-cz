---
title: Odpojení třídy CWnd od jejího prvku HWND | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CWnd
dev_langs:
- C++
helpviewer_keywords:
- HWND, detaching CWnd from
- removing HWNDs from CWnds
- CWnd objects [MFC], detaching from HWND
- detaching CWnds from HWNDs
- Detach method (CWnd class)
ms.assetid: 6efadf84-0517-4a3f-acfd-216e088f19c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c69703d8c528d82a696fc94be76ac4a569628b4e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392642"
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>Odpojení třídy CWnd od jejího prvku HWND

Pokud chcete obejít objekt -`HWND` vztah, knihovna MFC poskytuje další `CWnd` členskou funkci, [odpojit](../mfc/reference/cwnd-class.md#detach), který Odpojí okno objekt jazyka C++ z okna Windows. Tím se destruktoru zabrání zničení okna Windows při zničení objektu.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Vytváření oken](../mfc/creating-windows.md)

- [Posloupnost likvidace okna](../mfc/window-destruction-sequence.md)

- [Přidělování a rušení přidělení paměti okna](../mfc/allocating-and-deallocating-window-memory.md)

## <a name="see-also"></a>Viz také

[Objekty oken](../mfc/window-objects.md)

