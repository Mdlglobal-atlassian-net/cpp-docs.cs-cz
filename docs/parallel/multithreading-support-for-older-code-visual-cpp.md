---
title: Podpora více vláken ve starším kódu (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: b4ecd5f210aa01c41b3806ce15e19e77b8c93324
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="multithreading-support-for-older-code-visual-c"></a>Podpora více vláken ve starším kódu (Visual C++)
Visual C++ můžete mít více souběžných vláken, která se provádí současně. S více vláken, můžete číselníku úlohy na pozadí, spravovat několik současných vstup, spravovat uživatelské rozhraní a mnoho dalšího.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Multithreading s použitím jazyka C a prostředí Win32](../parallel/multithreading-with-c-and-win32.md)  
 Poskytuje podporu pro vytváření aplikací s více vlákny se systémem Microsoft Windows  
  
 [Multithreading s použitím jazyka C++ a prostředí MFC](../parallel/multithreading-with-cpp-and-mfc.md)  
 Popisuje, jaké jsou vláken a procesů a co je přístup knihovny MFC do více vláken je.  
  
 [Multithreading a národní prostředí](../parallel/multithreading-and-locales.md)  
 Popisuje problémy, které nastat při použití funkce národního prostředí běhové knihovny jazyka C a standardní knihovny C++ v aplikaci s více vlákny.  
  
## <a name="related-sections"></a>Související oddíly  
 [CWinThread](../mfc/reference/cwinthread-class.md)  
 Představuje vlákno při provádění v rámci aplikace.  
  
 [CSyncObject](../mfc/reference/csyncobject-class.md)  
 Popisuje čistě virtuální třídu, která poskytuje funkce, které jsou společné pro objekty synchronizace v Win32.  
  
 [Prohlížení](../mfc/reference/csemaphore-class.md)  
 Představuje semafor, který je na synchronizační objekt, který umožňuje omezený počet vláken v jedné nebo více procesech pro přístup k prostředkům.  
  
 [CMutex](../mfc/reference/cmutex-class.md)  
 Představuje objekt mutex, který je na synchronizační objekt, který umožňuje jedno vlákno vzájemně se vylučuje přístupu k prostředku.  
  
 [CCriticalSection](../mfc/reference/ccriticalsection-class.md)  
 Reprezentuje kritické oddíl, který je na synchronizační objekt, který umožňuje jedno vlákno najednou k přístupu k prostředku nebo části kódu.  
  
 [CEvent](../mfc/reference/cevent-class.md)  
 Představuje událost, která je na synchronizační objekt, který umožňuje jedno vlákno oznámit jiné, který došlo k události.  
  
 [CMultiLock](../mfc/reference/cmultilock-class.md)  
 Představuje mechanismus řízení přístupu používá při řízení přístupu k prostředkům v programu s více vlákny.  
  
 [CSingleLock](../mfc/reference/csinglelock-class.md)  
 Představuje mechanismus řízení přístupu používá při řízení přístupu k prostředku v programu s více vlákny.  
