---
title: Podpora více vláken ve starším kódu (Visual C++)
ms.date: 08/27/2018
helpviewer_keywords:
- threading [C++]
- multiple threads
- concurrent programming [C++]
- programming [C++], multithreaded
- multithreading [C++], about multithreading
- multiple concurrent threads
- multithreading [C++]
ms.assetid: 24425b1f-5031-4c6b-aac7-017115a40e7c
ms.openlocfilehash: 6f76ff42d2e28afe251ce234220051111736d3c9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215082"
---
# <a name="multithreading-support-for-older-code-visual-c"></a>Podpora více vláken ve starším kódu (Visual C++)

Vizuál C++ umožňuje mít více souběžných vláken spuštění současně. S více vlákny můžete vypnout úlohy na pozadí, spravovat současné proudy vstupu, spravovat uživatelské rozhraní a mnohem víc.

## <a name="in-this-section"></a>V tomto oddílu

[Multithreading s použitím jazyka C a prostředí Win32](multithreading-with-c-and-win32.md)<br/>
Poskytuje podporu pro vytváření aplikací s více vlákny v systému Microsoft Windows.

[Multithreading s použitím jazyka C++ a prostředí MFC](multithreading-with-cpp-and-mfc.md)<br/>
Popisuje, co jsou procesy a vlákna a co je přístup knihovny MFC k multithreadingu.

[Multithreading a národní prostředí](multithreading-and-locales.md)<br/>
Popisuje problémy, které vznikají při použití funkce národního prostředí knihovny runtime jazyka C i C++ standardní knihovny v aplikaci s více vlákny.

## <a name="related-sections"></a>Související oddíly

[CWinThread](../mfc/reference/cwinthread-class.md)<br/>
Představuje vlákno provádění v rámci aplikace.

[CSyncObject](../mfc/reference/csyncobject-class.md)<br/>
Popisuje čistě virtuální třídu, která poskytuje funkce společné pro objekty synchronizace v systému Win32.

[CSemaphore](../mfc/reference/csemaphore-class.md)<br/>
Představuje semafor, což je synchronizační objekt, který umožňuje omezenému počtu vláken v jednom nebo více procesech získat přístup k prostředku.

[CMutex](../mfc/reference/cmutex-class.md)<br/>
Představuje mutex, což je synchronizační objekt, který umožňuje jednomu vláknu vzájemně exkluzivní přístup k prostředku.

[CCriticalSection](../mfc/reference/ccriticalsection-class.md)<br/>
Představuje kritický oddíl, což je synchronizační objekt umožňující jednomu vláknu v čase získat přístup k prostředku nebo oddílu kódu.

[CEvent](../mfc/reference/cevent-class.md)<br/>
Představuje událost, což je synchronizační objekt, který umožňuje jednomu vláknu oznamovat jiné, že došlo k události.

[CMultiLock](../mfc/reference/cmultilock-class.md)<br/>
Představuje mechanismus pro řízení přístupu, který se používá při řízení přístupu k prostředkům v programu s více vlákny.

[CSingleLock](../mfc/reference/csinglelock-class.md)<br/>
Představuje mechanismus pro řízení přístupu, který se používá při řízení přístupu k prostředku v programu s více vlákny.
