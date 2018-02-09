---
title: "Multithreading s použitím jazyka C a Win32 | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Windows API [C++], multithreading
- multithreading [C++], C and Win32
- Visual C, multithreading
- Win32 applications [C++], multithreading
- threading [C++], C and Win32
- Win32 [C++], multithreading
- threading [C]
ms.assetid: 67cdc99e-1ad9-452b-a042-ed246b70040e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 16353937046384f9dc130048c510197697fb678f
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2018
---
# <a name="multithreading-with-c-and-win32"></a>Multithreading s použitím jazyka C a prostředí Win32
Microsoft Visual C++ poskytuje podporu pro vytváření aplikací s více vlákny. Měli byste zvážit použití více než jedno vlákno, pokud aplikace potřebuje k provedení drahými operacemi, které by způsobily uživatelského rozhraní pro přestat reagovat.  
  
 S Visual C++, existují dva způsoby, jak program s více vlákny: pomocí knihovny Microsoft Foundation Class (MFC) nebo běhové knihovny jazyka C a Win32 API. Informace o vytváření aplikací s více vlákny s knihovnou MFC najdete v tématu [Multithreading s C++ a MFC](../parallel/multithreading-with-cpp-and-mfc.md) po přečtení v následujících tématech o multithreading v C.  
  
 Tato témata vysvětlují funkce v jazyce Visual C++, které podporují vytvoření programy s více vlákny.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [Co více vláken je o](../parallel/multithread-programs.md)  
  
-   [Podpora knihovny pro multithreading](../parallel/library-support-for-multithreading.md)  
  
-   [Zahrnout soubory pro multithreading](../parallel/include-files-for-multithreading.md)  
  
-   [C Run-Time – funkce knihovny pro řízení vláken](../parallel/c-run-time-library-functions-for-thread-control.md)  
  
-   [Ukázka s více vlákny programu v jazyce C](../parallel/sample-multithread-c-program.md)  
  
-   [Psaní programů s více vlákny Win32](../parallel/writing-a-multithreaded-win32-program.md)  
  
-   [Kompilování a propojování programů s více vlákny](../parallel/compiling-and-linking-multithread-programs.md)  
  
-   [Obcházení problémových oblastí pomocí programů s více vlákny](../parallel/avoiding-problem-areas-with-multithread-programs.md)  
  
-   [Lokální úložiště vláken (TLS)](../parallel/thread-local-storage-tls.md)  
  
## <a name="see-also"></a>Viz také  
 [Podpora multithreadingu ve starším kódu (Visual C++)](../parallel/multithreading-support-for-older-code-visual-cpp.md)