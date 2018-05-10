---
title: Multithreading s použitím C++ a MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 778602a0e9236ad8cc788d8a2306e8f2d143ec49
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="multithreading-with-c-and-mfc"></a>Multithreading s použitím jazyka C++ a prostředí MFC
Knihovna Microsoft Foundation Class (MFC) poskytuje podporu pro vícevláknové aplikace. Toto téma popisuje procesy a vláken a MFC přístup k více vláken.  
  
 Proces je spuštěných instancí aplikace. Například když dvakrát kliknete na ikonu programu Poznámkový blok, můžete spustit proces, který spouští program Poznámkový blok.  
  
 Vlákno je cesta provádění v rámci procesu. Když spustíte program Poznámkový blok, operační systém vytvoří proces a zahájí provádění primární vlákno tohoto procesu. Po ukončení této vlákna, takže nemá proces. Tato primární vlákno poskytl kód spuštění ve formátu adresy funkce operačního systému. Obvykle je to adresa **hlavní** nebo `WinMain` funkce, která je zadána.  
  
 Pokud chcete, můžete vytvořit další vlákna ve vaší aplikaci. Můžete k tomu zpracování úkolů údržby nebo pozadí, pokud nechcete, aby uživatel má počkat na jejich dokončení. Všechna vlákna v aplikacích MFC jsou reprezentované pomocí [CWinThread](../mfc/reference/cwinthread-class.md) objekty. Ve většině případů i nemáte nemusel vytvářet tyto objekty; Místo toho zavolejte pomocnou funkci [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), která vytvoří `CWinThread` objektu za vás.  
  
 Knihovna MFC rozlišuje dva typy vláken: vlákna uživatelského rozhraní a pracovních vláken. Vlákna uživatelského rozhraní běžně se používají ke zpracování uživatelského vstupu a reakce na události a zprávy generované uživatelem. Pracovní vlákna běžně se používají k dokončení úkolů, například při každém přepočítání, které nevyžadují vstup uživatele. Rozhraní API Win32 nerozlišuje mezi typy vláken; potřebuje pouze vědět vlákna počáteční adresa, takže můžete začít provést vlákno. Knihovna MFC zpracovává vlákna uživatelského rozhraní speciálně poskytnutím zprávy odeslané pro události v uživatelském rozhraní. `CWinApp` je příkladem objekt vlákna uživatelského rozhraní, protože je odvozen z `CWinThread` a zpracovává události a zprávy generované uživatelem.  
  
 Zvláštní pozornost má být poskytnut k situacích, kde více než jedno vlákno může vyžadovat přístup ke stejnému objektu. [Multithreading: Tipy pro programování](../parallel/multithreading-programming-tips.md) popisuje techniky, které můžete použít k vyřešení problému, které by mohly nastat v těchto situacích. [Multithreading: Jak používat synchronizační třídy](../parallel/multithreading-how-to-use-the-synchronization-classes.md) popisuje způsob použití třídy, které jsou k dispozici pro synchronizaci přístup z více vláken pro jediný objekt.  
  
 Psaní a ladění vícevláknové programování je ze své podstaty podniku složitý a složité, protože musíte zajistit, že současně objekty přístupné více než jedno vlákno. Více vláken témata není naučit se základy vícevláknové programování pouze to, jak používat MFC v programu s více vlákny. Vícevláknové knihovny MFC vzorků zahrnutých v jazyce Visual C++ ilustrují několik vícevláknové přidávání funkce a rozhraní API Win32 nejsou zahrnuta podle MFC; ale že jsou určeny pouze pro počáteční bod.  
  
 Další informace o tom, jak operační systém zpracovává vláken a procesů najdete v tématu [vláken a procesů](http://msdn.microsoft.com/library/windows/desktop/ms684841) v [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
 Další informace o MFC podpora více vláken najdete v následujících tématech:  
  
-   [Multithreading: Vytváření vláken uživatelského rozhraní](../parallel/multithreading-creating-user-interface-threads.md)  
  
-   [Multithreading: Vytváření pracovních vláken](../parallel/multithreading-creating-worker-threads.md)  
  
-   [Multithreading: Jak používat synchronizační třídy](../parallel/multithreading-how-to-use-the-synchronization-classes.md)  
  
-   [Multithreading: Ukončení vláken](../parallel/multithreading-terminating-threads.md)  
  
-   [Multithreading: Tipy pro programování](../parallel/multithreading-programming-tips.md)  
  
-   [Multithreading: Kdy použít synchronizační třídy](../parallel/multithreading-when-to-use-the-synchronization-classes.md)  
  
## <a name="see-also"></a>Viz také  
 [Podpora multithreadingu ve starším kódu (Visual C++)](../parallel/multithreading-support-for-older-code-visual-cpp.md)