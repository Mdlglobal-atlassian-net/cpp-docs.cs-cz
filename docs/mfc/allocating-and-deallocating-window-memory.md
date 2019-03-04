---
title: Přidělování a rušení přidělení paměti okna
ms.date: 11/04/2016
helpviewer_keywords:
- memory allocation, window objects
- memory deallocation
- storage for window objects [MFC]
- memory deallocation, window memory
- window objects [MFC], deallocating memory for
- storage for window objects [MFC], allocating
ms.assetid: 7c962539-8461-4846-b5ca-fe3b15c313dc
ms.openlocfilehash: 60f99c01c7a311c31602269b49efaf434d16827a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267794"
---
# <a name="allocating-and-deallocating-window-memory"></a>Přidělování a rušení přidělení paměti okna

Nepoužívejte C++ **odstranit** operátor zničit okno rámce nebo zobrazení. Namísto toho zavolejte metodu `CWnd` členskou funkci `DestroyWindow`. Oken s rámečkem, proto musí být přidělený k haldě s operátorem **nové**. Buďte opatrní při přidělování oken s rámečkem v rámci zásobníku nebo globálně. Ostatní okna by měl být přiděleny na rámec zásobníku, kdykoli je to možné.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Vytváření oken](../mfc/creating-windows.md)

- [Posloupnost likvidace okna](../mfc/window-destruction-sequence.md)

- [Odpojení třídy CWnd od jejího prvku HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>Viz také:

[Zničení objektů oken](../mfc/destroying-window-objects.md)
