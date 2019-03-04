---
title: Multithreading s použitím jazyka C++ a prostředí MFC
ms.date: 08/27/2018
helpviewer_keywords:
- MFC [C++], multithreading
- threading [C++], MFC
- worker threads [C++]
- synchronization classes [C++]
- synchronization [C++], multithreading
- threading [MFC], about threading
- CWinThread class, purpose of
- multithreading [C++], MFC
- threading [MFC]
- user interface threads [C++]
ms.assetid: 979605f8-3988-44b5-ac9c-b8cce7fcce14
ms.openlocfilehash: bcffc2964d8e15fd47f437366863748175e12622
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57258343"
---
# <a name="multithreading-with-c-and-mfc"></a>Multithreading s použitím jazyka C++ a prostředí MFC

Knihovny Microsoft Foundation Class (MFC) poskytuje podporu pro víceprocesové aplikace. Toto téma popisuje procesy a vlákna a přístup knihovny MFC k multithreadingu.

Proces je vykonávající instance aplikace. Například když dvakrát kliknete na ikonu programu Poznámkový blok, spustí se proces, který spustí Poznámkový blok.

Vlákno je cesta provádění v rámci procesu. Když spustíte program Poznámkový blok, operační systém vytvoří proces a začne vykonávat primární vlákno tohoto procesu. Když toto vlákno ukončeno, ukončí se i proces. Tato primární vlákno je dodáno operačnímu systému spouštěcím kódem ve tvaru adresy funkce. Obvykle je to adresa `main` nebo `WinMain` funkce, která je zadána.

Pokud chcete, můžete vytvořit další vlákna ve vaší aplikaci. Můžete chtít provádět zpracování úkolů údržby nebo na pozadí, když nechcete, aby uživatel musel čekat jejich dokončení. Všechna vlákna v aplikacích MFC jsou představovány [CWinThread](../mfc/reference/cwinthread-class.md) objekty. Ve většině případů můžete dokonce nemusíte explicitně vytvářet tyto objekty; Místo toho zavolejte pomocnou funkci [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), která vytvoří `CWinThread` objekt za vás.

Knihovna MFC rozlišuje dva typy vláken: vlákna uživatelského rozhraní a pracovních vláken. Vlákna uživatelského rozhraní se běžně používají ke zpracování vstupu uživatele a reagují na události a zprávy generované uživatelem. Pracovní vlákna se běžně používají k dokončení úlohy, jako je například přepočet, které nevyžadují, aby uživatelský vstup. Rozhraní API Win32 nerozlišuje mezi typy vláken; potřebuje pouze znát počáteční adresu vlákna a mohli začít ke spuštění vlákna. Knihovna MFC zpracovává vlákna uživatelského rozhraní speciálně poskytnutím zprávy odeslané pro události v uživatelském rozhraní. `CWinApp` je příkladem objektu vlákna uživatelského rozhraní, protože se odvozuje od `CWinThread` a zpracovává události a zprávy generované uživatelem.

Zvláštní pozornost by měla být věnována situacím, kdy více než jedno vlákno může vyžadovat přístup ke stejnému objektu. [Multithreading: Tipy pro programování](multithreading-programming-tips.md) popisuje techniky, které můžete použít k vyřešení problémů, které mohou nastat v těchto situacích. [Multithreading: Jak používat synchronizační třídy](multithreading-how-to-use-the-synchronization-classes.md) popisuje způsob použití třídy, které jsou k dispozici pro synchronizaci přístupu z více vláken na jeden objekt.

Psaní a ladění programování s je ve své podstatě složitým a záludným, protože musíte zajistit, že současně objekty přístupné více než jedno vlákno. Témata multithreadingu neučí základy vícevláknové programování, pouze jak použít knihovnu MFC ve vašem vícevláknovém programu. Vícevláknové knihovny MFC vzorků zahrnutých v jazyce Visual C++ ukazují několik vícevláknových funkcí přidání a rozhraní Win32 API, která nejsou zahrnuta knihovnou MFC; ale že jsou určeny pouze pro jako výchozí bod.

Další informace o tom, jak operační systém zpracovává procesy a vlákna, naleznete v tématu [procesy a vlákna](/windows/desktop/ProcThread/processes-and-threads) v sadě Windows SDK.

Další informace o podpoře multithreadingu knihovnou MFC naleznete v následujících tématech:

- [Multithreading: Vytváření vláken uživatelského rozhraní](multithreading-creating-user-interface-threads.md)

- [Multithreading: Vytváření pracovních vláken](multithreading-creating-worker-threads.md)

- [Multithreading: Jak používat synchronizační třídy](multithreading-how-to-use-the-synchronization-classes.md)

- [Multithreading: Ukončení vláken](multithreading-terminating-threads.md)

- [Multithreading: Tipy pro programování](multithreading-programming-tips.md)

- [Multithreading: Kdy použít synchronizační třídy](multithreading-when-to-use-the-synchronization-classes.md)

## <a name="see-also"></a>Viz také:

[Podpora multithreadingu ve starším kódu (Visual C++)](multithreading-support-for-older-code-visual-cpp.md)
