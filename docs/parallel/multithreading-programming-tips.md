---
title: 'Multithreading: Programovací tipy | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ad830117323aef807fcebc1ef61b4dfb1900bd9
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591308"
---
# <a name="multithreading-programming-tips"></a>Multithreading: Tipy pro programování
Vícevláknové aplikace vyžaduje větší péči než aplikace s jedním vláknem při přístupu k datům. Vzhledem k tomu, že existuje více nezávislých cest spouštění v používat současně ve vícevláknových aplikacích algoritmy, data nebo obojí musí mějte na paměti tato data by mohly používat současně více než jedno vlákno. Toto téma popisuje postupy pro předcházení potenciálních problémů při programování aplikací s více vlákny pomocí knihovny Microsoft Foundation Class (MFC).  
  
- [Přístup k objektům z více vláken](#_core_accessing_objects_from_multiple_threads)  
  
- [Přístup k objektům MFC z vlákna mimo MFC](#_core_accessing_mfc_objects_from_non.2d.mfc_threads)  
  
- [Mapování zpracování Windows](#_core_windows_handle_maps)  
  
- [Komunikace mezi vlákny](#_core_communicating_between_threads)  
  
##  <a name="_core_accessing_objects_from_multiple_threads"></a> Přístup k objektům z více vláken  
 
Z důvodů výkonu a velikosti MFC objekty nejsou bezpečné pro vlákna na úrovni objektu, pouze na úrovni třídy. To znamená, že můžete mít dvou samostatných vláknech manipulace s dva různé `CString` objekty, ale ne dvě vlákna, manipulace se stejné `CString` objektu. Pokud vůbec musí mít stejný objekt manipulace s více vláken, Chraňte takový přístup pomocí příslušné mechanismy Win32 synchronizace, jako je například kritické oddíly. Další informace o kritických oddílů a další související objekty, najdete v článku [synchronizace](http://msdn.microsoft.com/library/windows/desktop/ms686353) v sadě Windows SDK.  
  
Knihovna tříd kritické oddíly interně používá k ochraně globální datové struktury, jako jsou ty používané ladit přidělování paměti.  
  
##  <a name="_core_accessing_mfc_objects_from_non.2d.mfc_threads"></a> Přístup k objektům MFC z vlákna mimo MFC  
 
Pokud máte aplikace s více vlákny, která vytvoří vlákno způsobem než pomocí [CWinThread](../mfc/reference/cwinthread-class.md) objektu nelze přistupovat k ostatním objektům MFC z tohoto vlákna. Jinými slovy, pokud chcete pro přístup k libovolného objektu knihovny MFC z jiného vlákna, musíte vytvořit toto vlákno s některou z metod popsaných v [Multithreading: vytváření vláken uživatelského rozhraní](../parallel/multithreading-creating-user-interface-threads.md) nebo [Multithreading: Vytváření pracovních vláken](../parallel/multithreading-creating-worker-threads.md). Tyto metody jsou pouze ty, které umožňují knihovny tříd inicializovat interní proměnné, které jsou potřeba ke zpracování aplikací s více vlákny.  
  
##  <a name="_core_windows_handle_maps"></a> Mapování zpracování Windows  
 
Obecně platí vlákno můžete přistupovat pouze objekty knihovny MFC, které je vytvořené. Je to proto dočasné a trvalé popisovače mapy Windows jsou uloženy v místním úložišti vláken, který pomáhá zajistit ochranu před mělo současně přístup z více vláken. Například pracovní podproces nelze provést výpočet a poté zavolejte dokumentu `UpdateAllViews` členská funkce systému Windows, které obsahují názory na nová data upravit. Tato akce nemá vliv, protože mapování z `CWnd` objektů HWND je lokální vzhledem k primárnímu vláknu. To znamená, že jedno vlákno může mít mapování z Windows popisovač pro objekt jazyka C++, ale jiné vlákno může mapovat stejné zpracování na jiný objekt jazyka C++. Změny provedené v jednom vlákně se nemusí projevit v jiném.  
  
Existuje několik způsobů, jak vyřešit tento problém. První je předat jednotlivé popisovače (například popisovačem HWND) namísto objektů jazyka C++ pracovní podproces. Pracovní podproces poté přidá tyto objekty do své dočasné mapování voláním příslušné `FromHandle` členskou funkci. Můžete také přidat objekt do mapy trvalé vlákna voláním `Attach`, ale to by mělo být provedeno pouze v případě, že je zaručeno, že objekt bude existovat déle než vlákno.  
  
Jinou metodou je vytvoření nové zprávy uživatelem definované odpovídající pro různé úkoly pracovních vláken provádění se publikovat do hlavního okna aplikace tyto zprávy pomocí `::PostMessage`. Tato metoda komunikace je podobná rozhovory s tím rozdílem, že oba vlákna jsou spuštěny ve stejném adresním prostoru dva různé aplikace.  
  
Další informace o mapování najdete v tématu [Technická poznámka 3](../mfc/tn003-mapping-of-windows-handles-to-objects.md). Další informace o místním úložišti vláken naleznete v tématu [úložiště Thread Local](http://msdn.microsoft.com/library/windows/desktop/ms686749) a [pomocí úložiště Thread Local](http://msdn.microsoft.com/library/windows/desktop/ms686991) v sadě Windows SDK.  
  
##  <a name="_core_communicating_between_threads"></a> Komunikace mezi vlákny  
 
Knihovna MFC poskytuje několik tříd, které umožňují vláken k synchronizaci přístupu k objektům zajistit bezpečný přístup z více vláken. Použití těchto tříd je popsána v [Multithreading: jak používat synchronizační třídy](../parallel/multithreading-how-to-use-the-synchronization-classes.md) a [Multithreading: kdy použít synchronizační třídy](../parallel/multithreading-when-to-use-the-synchronization-classes.md). Další informace o těchto objektů najdete v tématu [synchronizace](http://msdn.microsoft.com/library/windows/desktop/ms686353) v sadě Windows SDK.  
  
## <a name="see-also"></a>Viz také  

[Multithreading s použitím jazyka C++ a prostředí MFC](../parallel/multithreading-with-cpp-and-mfc.md)