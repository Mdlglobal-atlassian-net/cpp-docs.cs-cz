---
title: Podpora multithreadingu ve starším kódu (Visual C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- threading [C++]
- multiple threads
- concurrent programming [C++]
- programming [C++], multithreaded
- multithreading [C++], about multithreading
- multiple concurrent threads
- multithreading [C++]
ms.assetid: 24425b1f-5031-4c6b-aac7-017115a40e7c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 04767bfea727e32fb49d202358127685d9d5d2d0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46421125"
---
# <a name="multithreading-support-for-older-code-visual-c"></a>Podpora více vláken ve starším kódu (Visual C++)

Visual C++ umožňuje mít více souběžných vláken, která provádí současně. Pomocí multithreadingu můžete rozdělit úlohy na pozadí, spravovat několik současných vstupů, spravovat uživatelské rozhraní a spoustu dalších věcí.

## <a name="in-this-section"></a>V tomto oddílu

[Multithreading s použitím jazyka C a prostředí Win32](multithreading-with-c-and-win32.md)<br/>
Poskytuje podporu pro vytváření aplikací s více vlákny s Microsoft Windows

[Multithreading s použitím jazyka C++ a prostředí MFC](multithreading-with-cpp-and-mfc.md)<br/>
Popisuje, co jsou procesy a vlákna a co je přístup knihovny MFC k multithreadingu je.

[Multithreading a národní prostředí](multithreading-and-locales.md)<br/>
Popisuje problémy, které vznikají při použití funkce národního prostředí běhové knihovny jazyka C a standardní knihovny C++ ve vícevláknových aplikacích.

## <a name="related-sections"></a>Související oddíly

[CWinThread](../mfc/reference/cwinthread-class.md)<br/>
Představuje vlákno provádění v rámci aplikace.

[CSyncObject](../mfc/reference/csyncobject-class.md)<br/>
Popisuje čistě virtuální třídu, která poskytuje funkčnost běžnou pro synchronizaci objektů v systému Win32.

[CSemaphore –](../mfc/reference/csemaphore-class.md)<br/>
Představuje semafor, což je synchronizační objekt, který umožňuje omezenému počtu vláken v jednom nebo více procesech přistupovat k prostředku.

[CMutex](../mfc/reference/cmutex-class.md)<br/>
Představuje mutex, což je synchronizační objekt umožňující jeden vlákno vzájemně exkluzivní přístup k prostředku.

[CCriticalSection](../mfc/reference/ccriticalsection-class.md)<br/>
Představuje kritický oddíl, což je synchronizační objekt umožňující vždy jednomu vláknu postupně, aby přístup k prostředku nebo části kódu.

[CEvent](../mfc/reference/cevent-class.md)<br/>
Představuje událost, což je synchronizační objekt umožňující vždy jednomu vláknu upozornit jiné, že došlo k události.

[CMultiLock](../mfc/reference/cmultilock-class.md)<br/>
Představuje mechanismus řízení přístupu, který se používá při řízení přístupu k prostředkům ve vícevláknovém programu.

[CSingleLock](../mfc/reference/csinglelock-class.md)<br/>
Představuje mechanismus řízení přístupu, který se používá při řízení přístupu k prostředku v programu s více vlákny.