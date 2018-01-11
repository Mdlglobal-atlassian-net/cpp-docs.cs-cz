---
title: "Multithreading: Tipy pro programování | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- multithreading [C++], programming tips
- handle maps [C++]
- access control [C++], multithreading
- objects [C++], multiple threads and
- non-MFC threads [C++]
- threading [MFC], programming tips
- critical sections [C++]
- synchronization [C++], multithreading
- programming [C++], multithreaded
- communications [C++], between threads
- threading [C++], best practices
- troubleshooting [C++], multithreading
- Windows handle maps [C++]
ms.assetid: ad14cc70-c91c-4c24-942f-13a75e58bf8a
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 30ecf45c8a22dfb42917affa59152aeefbc35425
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="multithreading-programming-tips"></a>Multithreading: Tipy pro programování
Vícevláknové aplikace vyžadují přísnější zacházení než jednovláknové aplikace při přístupu k datům. Protože existuje více, nezávislé cesty spouštění v používat současně v vícevláknové aplikace na algoritmy, data nebo obojí musí mít přehled dat může používat více než jedno vlákno najednou. Toto téma popisuje postupy pro předcházení potenciálních problémů při programování vícevláknové aplikace s knihovnou Microsoft Foundation Class (MFC).  
  
-   [Přístup k objektům z více vláken](#_core_accessing_objects_from_multiple_threads)  
  
-   [Přístup k objektům MFC z vlákna mimo MFC](#_core_accessing_mfc_objects_from_non.2d.mfc_threads)  
  
-   [Mapování zpracování systému Windows](#_core_windows_handle_maps)  
  
-   [Komunikace mezi vlákny](#_core_communicating_between_threads)  
  
##  <a name="_core_accessing_objects_from_multiple_threads"></a>Přístup k objektům z více vláken  
 Velikost a výkon z důvodů nejsou objekty MFC bezpečné pro přístup z více vláken na úrovni objektu, jenom na úrovni třídy. To znamená, že můžete mít dvou samostatných vláknech manipulace s dva různé `CString` objekty, ale není dvěma vlákny manipulace s stejné `CString` objektu. Pokud musíte mít nezbytně více vláken manipulace s stejný objekt, chraňte přístup příslušné mechanismy Win32 synchronizace, jako je například kritické oddíly. Další informace o kritické oddíly a další související objekty, najdete v části [synchronizace](http://msdn.microsoft.com/library/windows/desktop/ms686353) v [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
 Kritické oddíly knihovny tříd interně používá k ochraně struktury globální data, jako jsou ty používané přidělení paměti ladění.  
  
##  <a name="_core_accessing_mfc_objects_from_non.2d.mfc_threads"></a>Přístup k objektům MFC z vlákna mimo MFC  
 Pokud máte vícevláknových aplikací, který vytvoří vlákno jiným způsobem než pomocí [CWinThread](../mfc/reference/cwinthread-class.md) objektu nelze přístup k ostatním objektům MFC z tohoto vlákna. Jinými slovy, pokud chcete pro přístup k libovolného objektu knihovny MFC z jiného vlákna, musíte vytvořit daném vláknu jedna z metod popsaných v [Multithreading: vytváření vláken uživatelského rozhraní](../parallel/multithreading-creating-user-interface-threads.md) nebo [Multithreading: Vytváření pracovních vláken](../parallel/multithreading-creating-worker-threads.md). Tyto metody jsou pouze ty, které umožňují knihovny tříd inicializovat interní proměnné, které jsou nutné ke zpracování vícevláknové aplikace.  
  
##  <a name="_core_windows_handle_maps"></a>Mapování zpracování systému Windows  
 Obecně platí vlákno k přístup pouze MFC objekty, které se vytvořily. To je proto dočasné a trvalé mapování zpracování systému Windows jsou uchovávány v lokální úložiště vláken pro zachování ochrany z současný přístup z více vláken. Například pracovní vlákno nelze provedou výpočtu a pak zavolají dokumentu `UpdateAllViews` – členská funkce systému Windows, které obsahují zobrazení na nová data upravit. To nemá žádný vliv, protože mapa z `CWnd` objekty ke `HWND`je umístěna na primární vlákno. To znamená, že jedno vlákno může mít mapování z popisovačů systému Windows na objekt C++, ale jiné vlákno může mapovat stejné zpracování na jiný objekt C++. Změny provedené v jedno vlákno se nemusí projevit v dalších.  
  
 Existuje několik způsobů tento problém vyřešit. První je předat jednotlivá zpracování (například `HWND`) místo objektů jazyka C++ pracovní vlákno. Pracovní podproces poté přidá tyto objekty do jeho dočasné mapy voláním příslušné `FromHandle` – členská funkce. Můžete také přidat objekt do dočasné mapy vlákna voláním **Attach**, ale to by mělo být provedeno pouze v případě, že je zaručeno, že objekt bude existovat déle, než vlákno.  
  
 Další možností je vytvořit nové vlastní zprávy odpovídající různých úloh pracovních vláken bude provádění a odeslání tyto zprávy na hlavní okno aplikace pomocí **:: zpravy**. Tato metoda komunikace je podobná dvě různé aplikace konverzaci s tím rozdílem, že jsou obě vlákna spuštěna ve stejném adresním prostoru.  
  
 Další informace o mapování zpracování najdete v tématu [technické poznámky 3](../mfc/tn003-mapping-of-windows-handles-to-objects.md). Další informace o úložiště thread local najdete v tématu [úložiště Thread Local](http://msdn.microsoft.com/library/windows/desktop/ms686749) a [pomocí místní úložiště vláken](http://msdn.microsoft.com/library/windows/desktop/ms686991) v [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
##  <a name="_core_communicating_between_threads"></a>Komunikace mezi vlákny  
 Knihovna MFC poskytuje několik tříd, které umožňují vláken synchronizovat přístup k objektům pro zachování zabezpečení vlákna. Použití těchto tříd je popsaná v [Multithreading: jak používat synchronizační třídy](../parallel/multithreading-how-to-use-the-synchronization-classes.md) a [Multithreading: kdy použít synchronizační třídy](../parallel/multithreading-when-to-use-the-synchronization-classes.md). Další informace o těchto objektů najdete v tématu [synchronizace](http://msdn.microsoft.com/library/windows/desktop/ms686353) v [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
## <a name="see-also"></a>Viz také  
 [Multithreading s použitím jazyka C++ a prostředí MFC](../parallel/multithreading-with-cpp-and-mfc.md)