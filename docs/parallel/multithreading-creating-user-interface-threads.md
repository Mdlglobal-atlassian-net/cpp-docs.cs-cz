---
title: "Multithreading: Vytváření vláken uživatelského rozhraní | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CREATE_SUSPENDED
- SECURITY_ATTRIBUTES
dev_langs:
- C++
helpviewer_keywords:
- multithreading [C++], user interface threads
- threading [C++], creating threads
- threading [C++], user interface threads
- user interface threads [C++]
- threading [MFC], user interface threads
ms.assetid: 446925c1-db59-46ea-ae5b-d5ae5d5b91d8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 105685e0db4689978ef1e6f8615bb5e5f8acdd43
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="multithreading-creating-user-interface-threads"></a>Multithreading: Vytváření vláken uživatelského rozhraní
Vlákna uživatelského rozhraní se často používá ke zpracování uživatelského vstupu a reakce na události uživatele nezávisle na vláken provádění dalších částí aplikace. Hlavní vlákno aplikace (součástí vaší `CWinApp`-odvozené třídy) je již vytvořena a spuštěna pro vás. Toto téma popisuje kroky potřebné k vytvoření vlákna další uživatelského rozhraní.  
  
 První věc, kterou musíte udělat při vytváření vlákna uživatelského rozhraní, je odvození třídy z [CWinThread](../mfc/reference/cwinthread-class.md). Musíte deklarovat a tuto funkci implementovat pomocí [DECLARE_DYNCREATE –](../mfc/reference/run-time-object-model-services.md#declare_dyncreate) a [IMPLEMENT_DYNCREATE](../mfc/reference/run-time-object-model-services.md#implement_dyncreate) makra. Tato třída musí přepsat některé funkce a ostatní můžete přepsat. Tyto funkce a k čemu by měl použít jsou uvedené v následující tabulce.  
  
### <a name="functions-to-override-when-creating-a-user-interface-thread"></a>Funkce pro přepsání při vytváření vlákna uživatelského rozhraní  
  
|Funkce|Účel|  
|--------------|-------------|  

|[ExitInstance –](../mfc/reference/cwinthread-class.md#exitinstance)| Proveďte čištění po ukončení vlákna. Obvykle přepsána. |  
|[InitInstance –](../mfc/reference/cwinthread-class.md#initinstance)| Provede inicializaci instance vlákna. Musí být přepsána. |  
|[ONIDLE –](../mfc/reference/cwinthread-class.md#onidle)| Proveďte zpracování specifické pro vlákno doby nečinnosti. Obvykle není přepsána. |  
|[PreTranslateMessage –](../mfc/reference/cwinthread-class.md#pretranslatemessage)| Filtrovat zprávy, než jsou odeslány do **TranslateMessage** a **DispatchMessage**. Obvykle není přepsána. |  
|[ProcessWndProcException](../mfc/reference/cwinthread-class.md#processwndprocexception)| Zachytávat neošetřené výjimky vyvolané obslužné rutiny zpráv a příkaz vlákna. Obvykle není přepsána. |  
|[Spustit](../mfc/reference/cwinthread-class.md#run)| Řízení funkce pro vlákno. Obsahuje message pump. Přepsat zřídka. |  

  
 Knihovna MFC poskytuje dvě verze funkce `AfxBeginThread` prostřednictvím přetížení parametru: jednu, která může pouze vytvořit pracovní vlákna, a jednu, která může vytvářet vlákna uživatelského rozhraní nebo pracovní vlákna. Chcete-li spustit vlákno uživatelského rozhraní, volejte přetížení druhý [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), poskytuje následující informace:  
  
-   [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class) třídy odvozené od `CWinThread`.  
  
-   (Volitelné) Požadovaná úroveň priority. Výchozí hodnota je s normální prioritou. Další informace o úrovních k dispozici s prioritou najdete v tématu [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) v [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
-   (Volitelné) Požadovaná velikost zásobníku pro vlákno. Výchozí hodnota je stejná velikost zásobníku jako vytváření vláken.  
  
-   (Volitelné) **CREATE_SUSPENDED** Pokud chcete, aby vlákno vytvořeno v pozastaveném stavu. Výchozí hodnota je 0 nebo normální spuštění vlákna.  
  
-   (Volitelné) Požadované zabezpečení atributy. Výchozí hodnota je stejný přístup jako nadřazené vlákno. Další informace o formátu informací zabezpečení najdete v tématu [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) v [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
 `AfxBeginThread`provede většinu práce. Vytvoří nový objekt vaší třídy, inicializuje s informací, které zadáte a volá [CWinThread::CreateThread](../mfc/reference/cwinthread-class.md#createthread) spustit provádění vlákna. Kontroly se provádějí v celém procesu zajistit, že všechny objekty jsou deallocated správně má libovolná součást vytvoření selhat.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [Multithreading: Ukončení vláken](../parallel/multithreading-terminating-threads.md)  
  
-   [Multithreading: Vytváření pracovních vláken](../parallel/multithreading-creating-worker-threads.md)  
  
-   [Procesy a vlákna](http://msdn.microsoft.com/library/windows/desktop/ms684841)  
  
## <a name="see-also"></a>Viz také  
 [Multithreading s použitím jazyka C++ a prostředí MFC](../parallel/multithreading-with-cpp-and-mfc.md)