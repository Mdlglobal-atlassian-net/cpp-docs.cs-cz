---
title: "Podpora více vláken ve starším kódu (Visual C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- threading [C++]
- multiple threads
- concurrent programming [C++]
- programming [C++], multithreaded
- multithreading [C++], about multithreading
- multiple concurrent threads
- multithreading [C++]
ms.assetid: 24425b1f-5031-4c6b-aac7-017115a40e7c
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d949c1ff19be6f3b89673753fdaccc2996bbef36
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="multithreading-support-for-older-code-visual-c"></a>Podpora více vláken ve starším kódu (Visual C++)
Visual C++ můžete mít více souběžných vláken, která se provádí současně. S více vláken, můžete číselníku úlohy na pozadí, spravovat několik současných vstup, spravovat uživatelské rozhraní a mnoho dalšího.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Multithreading s použitím jazyka C a Win32](../parallel/multithreading-with-c-and-win32.md)  
 Poskytuje podporu pro vytváření aplikací s více vlákny se systémem Microsoft Windows  
  
 [Multithreading s použitím C++ a MFC](../parallel/multithreading-with-cpp-and-mfc.md)  
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
  
 [(NOTINBUILD) Metody programování Visual C++](http://msdn.microsoft.com/en-us/0822f806-fa81-4b65-bf0f-1e2921f30c95)  
 Obsahuje odkazy na témata popisující rámcové informace o knihovnách Visual C++ a témata pojednávající o různých technikách a technologiích programování kódu.