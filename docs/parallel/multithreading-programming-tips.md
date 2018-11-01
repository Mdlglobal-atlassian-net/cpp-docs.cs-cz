---
title: 'Multithreading: Tipy pro programování MFC'
ms.date: 08/27/2018
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
ms.openlocfilehash: 0fbee2e836c2e898488da348e4dec9ea00ac4370
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494275"
---
# <a name="multithreading-mfc-programming-tips"></a>Multithreading: Tipy pro programování MFC

Vícevláknové aplikace vyžaduje větší péči než aplikace s jedním vláknem zajistíte, že operace prováděny v zamýšleném pořadí a všechna data, která je přístup prostřednictvím více vláken není poškozen. Toto téma popisuje postupy pro předcházení potenciálních problémů při programování aplikací s více vlákny pomocí knihovny Microsoft Foundation Class (MFC).

- [Přístup k objektům z více vláken](#_core_accessing_objects_from_multiple_threads)

- [Přístup k objektům MFC z vlákna mimo MFC](#_core_accessing_mfc_objects_from_non.2d.mfc_threads)

- [Mapování zpracování Windows](#_core_windows_handle_maps)

- [Komunikace mezi vlákny](#_core_communicating_between_threads)

##  <a name="_core_accessing_objects_from_multiple_threads"></a> Přístup k objektům z více vláken

Objekty knihovny MFC nejsou bezpečné pro vlákna samy o sobě. Dvou samostatných vláknech nelze pracovat na stejný objekt, pokud nechcete použít synchronizační třídy knihovny MFC a/nebo synchronizaci objektů Win32, jako je například kritické oddíly. Další informace o kritických oddílů a další související objekty, najdete v článku [synchronizace](/windows/desktop/Sync/synchronization) v sadě Windows SDK.

Knihovna tříd kritické oddíly interně používá k ochraně globální datové struktury, jako jsou ty používané ladit přidělování paměti.

##  <a name="_core_accessing_mfc_objects_from_non.2d.mfc_threads"></a> Přístup k objektům MFC z vlákna mimo MFC

Pokud máte aplikace s více vlákny, která vytvoří vlákno způsobem než pomocí [CWinThread](../mfc/reference/cwinthread-class.md) objektu nelze přistupovat k ostatním objektům MFC z tohoto vlákna. Jinými slovy, pokud chcete pro přístup k libovolného objektu knihovny MFC z jiného vlákna, musíte vytvořit toto vlákno s některou z metod popsaných v [Multithreading: vytváření vláken uživatelského rozhraní](multithreading-creating-user-interface-threads.md) nebo [Multithreading: Vytváření pracovních vláken](multithreading-creating-worker-threads.md). Tyto metody jsou pouze ty, které umožňují knihovny tříd inicializovat interní proměnné, které jsou potřeba ke zpracování aplikací s více vlákny.

##  <a name="_core_windows_handle_maps"></a> Mapování zpracování Windows

Obecně platí vlákno můžete přistupovat pouze objekty knihovny MFC, které je vytvořené. Je to proto dočasné a trvalé popisovače mapy Windows jsou uloženy v místním úložišti vláken, který pomáhá zajistit ochranu před mělo současně přístup z více vláken. Například pracovní podproces nelze provést výpočet a poté zavolejte dokumentu `UpdateAllViews` členská funkce systému Windows, které obsahují názory na nová data upravit. Tato akce nemá vliv, protože mapování z `CWnd` objektů HWND je lokální vzhledem k primárnímu vláknu. To znamená, že jedno vlákno může mít mapování z Windows popisovač pro objekt jazyka C++, ale jiné vlákno může mapovat stejné zpracování na jiný objekt jazyka C++. Změny provedené v jednom vlákně se nemusí projevit v jiném.

Existuje několik způsobů, jak vyřešit tento problém. První je předat jednotlivé popisovače (například popisovačem HWND) namísto objektů jazyka C++ pracovní podproces. Pracovní podproces poté přidá tyto objekty do své dočasné mapování voláním příslušné `FromHandle` členskou funkci. Můžete také přidat objekt do mapy trvalé vlákna voláním `Attach`, ale to by mělo být provedeno pouze v případě, že je zaručeno, že objekt bude existovat déle než vlákno.

Jinou metodou je vytvoření nové zprávy uživatelem definované odpovídající pro různé úkoly pracovních vláken provádění se publikovat do hlavního okna aplikace tyto zprávy pomocí `::PostMessage`. Tato metoda komunikace je podobná rozhovory s tím rozdílem, že oba vlákna jsou spuštěny ve stejném adresním prostoru dva různé aplikace.

Další informace o mapování najdete v tématu [Technická poznámka 3](../mfc/tn003-mapping-of-windows-handles-to-objects.md). Další informace o místním úložišti vláken naleznete v tématu [úložiště Thread Local](/windows/desktop/ProcThread/thread-local-storage) a [pomocí úložiště Thread Local](/windows/desktop/ProcThread/using-thread-local-storage) v sadě Windows SDK.

##  <a name="_core_communicating_between_threads"></a> Komunikace mezi vlákny

Knihovna MFC poskytuje několik tříd, které umožňují vláken k synchronizaci přístupu k objektům zajistit bezpečný přístup z více vláken. Použití těchto tříd je popsána v [Multithreading: jak používat synchronizační třídy](multithreading-how-to-use-the-synchronization-classes.md) a [Multithreading: kdy použít synchronizační třídy](multithreading-when-to-use-the-synchronization-classes.md). Další informace o těchto objektů najdete v tématu [synchronizace](/windows/desktop/Sync/synchronization) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Multithreading s použitím jazyka C++ a prostředí MFC](multithreading-with-cpp-and-mfc.md)