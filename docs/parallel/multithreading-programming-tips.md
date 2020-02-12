---
title: 'Multithreading: Tipy pro programování v MFC'
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
ms.openlocfilehash: 79e7d440b478c759c5d4fd683d6af3423e7e8661
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140450"
---
# <a name="multithreading-mfc-programming-tips"></a>Multithreading: Tipy pro programování v MFC

Vícevláknové aplikace vyžadují přísnější péči než aplikace s jedním vláknem, aby se zajistilo, že k operacím dojde v zamýšleném pořadí, a že všechna data, ke kterým je přístup více vlákny, nejsou poškozená. Toto téma vysvětluje techniky pro předcházení potenciálním problémům při programování aplikací s více vlákny pomocí knihovny Microsoft Foundation Class (MFC).

- [Přístup k objektům z více vláken](#_core_accessing_objects_from_multiple_threads)

- [Přístup k objektům knihovny MFC z non-MFC vláken](#_core_accessing_mfc_objects_from_non.2d.mfc_threads)

- [Mapy popisovačů Windows](#_core_windows_handle_maps)

- [Komunikace mezi vlákny](#_core_communicating_between_threads)

## <a name="_core_accessing_objects_from_multiple_threads"></a>Přístup k objektům z více vláken

Objekty MFC nejsou bezpečné pro přístup z více vláken. Dvě samostatná vlákna nemohou manipulovat se stejným objektem, pokud nepoužíváte synchronizační třídy knihovny MFC a případně příslušné synchronizační objekty Win32, například důležité oddíly. Další informace o důležitých částech a dalších souvisejících objektech naleznete v tématu [synchronizace](/windows/win32/Sync/synchronization) v Windows SDK.

Knihovna tříd interně používá kritické oddíly k ochraně globálních datových struktur, jako jsou ty, které se používají při přidělování paměti ladění.

## <a name="_core_accessing_mfc_objects_from_non.2d.mfc_threads"></a>Přístup k objektům knihovny MFC z non-MFC vláken

Máte-li vícevláknovou aplikaci, která vytváří vlákno v jiném než použití objektu [CWinThread](../mfc/reference/cwinthread-class.md) , nemůžete získat přístup k jiným OBJEKTŮM knihovny MFC z tohoto vlákna. Jinými slovy, pokud chcete získat přístup k libovolnému objektu knihovny MFC ze sekundárního vlákna, je nutné vytvořit toto vlákno pomocí jedné z metod popsaných v [tématu Multithreading: vytváření vláken uživatelského rozhraní](multithreading-creating-user-interface-threads.md) nebo [Multithreading: vytváření pracovních vláken](multithreading-creating-worker-threads.md). Tyto metody jsou pouze ty, které umožňují knihovně tříd inicializovat interní proměnné nezbytné pro zpracování vícevláknových aplikací.

## <a name="_core_windows_handle_maps"></a>Mapy popisovačů Windows

Jako obecné pravidlo vlákno má přístup pouze k objektům MFC, které vytvořil. Je to proto, že dočasné a trvalé mapy popisovačů systému Windows jsou uchovávány v thread local úložiště, aby bylo možné udržet ochranu před současným přístupem z více vláken. Pracovní vlákno například nemůže provést výpočet a potom volat `UpdateAllViews` členskou funkcí dokumentu tak, aby obsahovala okna, která obsahují zobrazení na nových změněných dat. To nemá žádný vliv, protože mapa z `CWnd` objektů na HWND je místní pro primární vlákno. To znamená, že jedno vlákno může mít mapování z popisovače Windows na C++ objekt, ale jiné vlákno může mapovat stejný popisovač na jiný C++ objekt. Změny provedené v jednom vlákně by se neprojevily v druhém.

Existuje několik způsobů, jak tento problém vyřešit. První je předat jednotlivé popisovače (například HWND) místo C++ objektů do pracovního vlákna. Pracovní vlákno následně přidá tyto objekty do jeho dočasné mapy voláním příslušné členské funkce `FromHandle`. Můžete také přidat objekt k trvalé mapě vlákna voláním `Attach`, ale to by mělo být provedeno pouze v případě, že je zaručeno, že objekt bude existovat déle než vlákno.

Další metodou je vytvořit nové uživatelsky definované zprávy odpovídající různým úlohám, které budou vaše pracovní vlákna provádět, a publikovat tyto zprávy do hlavního okna aplikace pomocí `::PostMessage`. Tato metoda komunikace je podobná dvou různým aplikacím konverzující s tím rozdílem, že obě vlákna jsou spouštěna ve stejném adresním prostoru.

Další informace o mapách popisovačů najdete v části [technická Poznámka 3](../mfc/tn003-mapping-of-windows-handles-to-objects.md). Další informace o službě thread local Storage najdete v tématu věnovaném [místnímu úložišti vláken](/windows/win32/ProcThread/thread-local-storage) a [použití místního úložiště vlákna](/windows/win32/ProcThread/using-thread-local-storage) v Windows SDK.

## <a name="_core_communicating_between_threads"></a>Komunikace mezi vlákny

Knihovna MFC poskytuje několik tříd, které umožňují vláknům synchronizovat přístup k objektům pro zajištění bezpečnosti vláken. Použití těchto tříd je popsáno v [tématu Multithreading: jak používat synchronizační třídy](multithreading-how-to-use-the-synchronization-classes.md) a [Multithreading: Kdy použít synchronizační třídy](multithreading-when-to-use-the-synchronization-classes.md). Další informace o těchto objektech naleznete v tématu [synchronizace](/windows/win32/Sync/synchronization) v Windows SDK.

## <a name="see-also"></a>Viz také

[Multithreading s použitím jazyka C++ a prostředí MFC](multithreading-with-cpp-and-mfc.md)
