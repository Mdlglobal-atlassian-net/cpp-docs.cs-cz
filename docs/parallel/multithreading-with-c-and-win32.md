---
title: "Multithreading s použitím jazyka C a Win32 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Windows API [C++], multithreading
- multithreading [C++], C and Win32
- Visual C, multithreading
- Win32 applications [C++], multithreading
- threading [C++], C and Win32
- Win32 [C++], multithreading
- threading [C]
ms.assetid: 67cdc99e-1ad9-452b-a042-ed246b70040e
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0e2ce9377d0ea4b2bd7b04255eb1c8099341af39
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="multithreading-with-c-and-win32"></a>Multithreading s použitím jazyka C a prostředí Win32
Microsoft Visual C++ poskytuje podporu pro vytváření aplikací s více vlákny se systémem Microsoft Windows: Windows XP, Windows 2000, Windows NT, Windows Me a Windows 98. Měli byste zvážit použití více než jedno vlákno, pokud aplikace potřebuje ke správě více aktivit, jako je vstup souběžných klávesnice a myši. Jedno vlákno může zpracovat vstup z klávesnice, zatímco druhé filtruje aktivity myši. Třetí vlákno můžete aktualizovat obrazovku na základě dat z vláken myši a klávesnice. Jiná vlákna ve stejnou dobu, můžete získat přístup k souborům disku nebo získat data z komunikační port.  
  
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
 [Podpora více vláken ve starším kódu (Visual C++)](../parallel/multithreading-support-for-older-code-visual-cpp.md)