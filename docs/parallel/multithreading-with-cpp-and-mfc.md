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
ms.openlocfilehash: eaf28404b06e9b0bf6126d8bbc140bf46cff37da
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512012"
---
# <a name="multithreading-with-c-and-mfc"></a>Multithreading s použitím jazyka C++ a prostředí MFC

Knihovna Microsoft Foundation Class (MFC) poskytuje podporu pro vícevláknové aplikace. Toto téma popisuje procesy a vlákna a přístup knihovny MFC k multithreadingu.

Proces je spuštěná instance aplikace. Například když dvakrát kliknete na ikonu poznámkového bloku, spustíte proces, který spustí Poznámkový blok.

Vlákno je cesta provádění v rámci procesu. Když spustíte program Poznámkový blok, operační systém vytvoří proces a začne provádět primární vlákno tohoto procesu. Když je toto vlákno ukončeno, tak proces. Toto primární vlákno je dodáno operačním systémem spouštěcím kódem ve formě adresy funkce. Obvykle je to adresa `main` funkce nebo `WinMain` , která je dodána.

Pokud chcete, můžete v aplikaci vytvořit další vlákna. Můžete to chtít udělat pro zpracování úloh na pozadí nebo údržby, když nechcete, aby uživatel čekal na jejich dokončení. Všechna vlákna v aplikacích knihovny MFC jsou reprezentována objekty [CWinThread](../mfc/reference/cwinthread-class.md) . Ve většině případů nemusíte ani explicitně vytvářet tyto objekty. místo toho zavolejte pomocnou funkci rozhraní [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), která pro `CWinThread` vás vytvoří objekt.

MFC rozlišuje dva typy vláken: vlákna uživatelského rozhraní a pracovní vlákna. Vlákna uživatelského rozhraní se běžně používají ke zpracování vstupu uživatele a k reakci na události a zprávy generované uživatelem. Pracovní vlákna se běžně používají k dokončení úkolů, jako je například přepočítání, které nevyžadují vstup uživatele. Win32 API nerozlišuje mezi typy vláken; potřebuje jenom znát počáteční adresu vlákna, aby bylo možné spustit vlákno. Knihovna MFC zpracovává vlákna uživatelského rozhraní speciálně tím, že poskytuje pumpu zpráv pro události v uživatelském rozhraní. `CWinApp`je příkladem objektu vlákna uživatelského rozhraní, protože je odvozen z `CWinThread` a zpracovává události a zprávy generované uživatelem.

Zvláštní pozornost byste měli věnovat situacím, kdy více než jedno vlákno může vyžadovat přístup ke stejnému objektu. [Multithreading: Tipy](multithreading-programming-tips.md) pro programování popisují postupy, které můžete použít k získání potíží, které mohou nastat v těchto situacích. [Multithreading: Jak použít synchronizační třídy](multithreading-how-to-use-the-synchronization-classes.md) popisuje, jak použít třídy, které jsou k dispozici pro synchronizaci přístupu z více vláken k jednomu objektu.

Psaní a ladění vícevláknového programování je v podstatě složitým a štychem podniku, protože je nutné zajistit, aby objekty nezískaly více než jedno vlákno najednou. Témata s více vlákny nezpůsobují základy programování s více vlákny, jak použít knihovnu MFC v programu s více vlákny. Ukázky MFC s více vlákny, které jsou C++ součástí vizuálu, ilustrují několik vícevláknových funkcí přidávání a rozhraní Win32 API, které nezahrnuje MFC; jsou však určeny pouze jako výchozí bod.

Další informace o tom, jak operační systém zpracovává procesy a vlákna, naleznete v tématu [procesy a vlákna](/windows/win32/ProcThread/processes-and-threads) v Windows SDK.

Další informace o podpoře multithreadingu knihovnou MFC naleznete v následujících tématech:

- [Multithreading: Vytváření vláken uživatelského rozhraní](multithreading-creating-user-interface-threads.md)

- [Multithreading: Vytváření pracovních vláken](multithreading-creating-worker-threads.md)

- [Multithreading: Jak používat synchronizační třídy](multithreading-how-to-use-the-synchronization-classes.md)

- [Multithreading: Ukončování vláken](multithreading-terminating-threads.md)

- [Multithreading: Tipy k programování](multithreading-programming-tips.md)

- [Multithreading: Kdy použít synchronizační třídy](multithreading-when-to-use-the-synchronization-classes.md)

## <a name="see-also"></a>Viz také:

[Podpora multithreadingu ve starším kódu (Visual C++)](multithreading-support-for-older-code-visual-cpp.md)
