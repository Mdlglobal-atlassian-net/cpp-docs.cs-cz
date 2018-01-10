---
title: "Multithreading: Kdy použít synchronizační třídy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- threading [MFC], synchronization classes
- resources [C++], multithreading
- synchronization classes [C++]
- synchronization [C++], multithreading
- controlled resource access [C++]
- synchronization access classes [C++]
- threading [C++], synchronization
- multithreading [C++], synchronization classes
ms.assetid: 4914f54e-68ac-438f-93c9-c013455a657e
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 38437983552dfdf2cf6708ec5fd067e06387ea5c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="multithreading-when-to-use-the-synchronization-classes"></a>Multithreading: Kdy použít synchronizační třídy
Vícevláknové třídy dodávané s knihovnou MFC rozdělit do dvou kategorií: synchronizačními objekty ([CSyncObject](../mfc/reference/csyncobject-class.md), [prohlížení](../mfc/reference/csemaphore-class.md), [CMutex](../mfc/reference/cmutex-class.md), [ CCriticalSection](../mfc/reference/ccriticalsection-class.md), a [CEvent](../mfc/reference/cevent-class.md)) a synchronizace přístup k objektům ([CMultiLock](../mfc/reference/cmultilock-class.md) a [CSingleLock](../mfc/reference/csinglelock-class.md)).  
  
 Třídy synchronizace se používají k zajištění integrity prostředku je třeba kontrolovat přístup k prostředku. Synchronizační přístupové třídy se používají k získání přístupu k těmto řízené prostředkům. Toto téma popisuje, kdy používat jednotlivé třídy.  
  
 Chcete-li zjistit, které třídy byste měli používat, požádejte následující řadu otázek:  
  
1.  Čekání na určitou akci předtím, než ho má přístup k prostředku má aplikace (například data musí být přijata z komunikační port předtím, než je možné zapsat do souboru)?  
  
     Pokud ano, použít `CEvent`.  
  
2.  Můžete více než jedno vlákno ve stejný přístup k aplikaci tento prostředek najednou (například vaše aplikace umožňuje až pět windows se zobrazeními dokumentem)?  
  
     Pokud ano, použít `CSemaphore`.  
  
3.  Můžete použít tento prostředek více než jednu aplikaci (například prostředku je v knihovně DLL)?  
  
     Pokud ano, použít `CMutex`.  
  
     Pokud ne, použijte `CCriticalSection`.  
  
 **CSyncObject** se nikdy nepoužívá přímo. Je základní třídou pro jiné třídy čtyři synchronizace.  
  
## <a name="example-1-using-three-synchronization-classes"></a>Příklad 1: Použití tří tříd synchronizace  
 Jako příklad trvat aplikaci, která udržuje seznam propojené účty. Tato aplikace umožňuje až tři účtů v samostatném systému windows, ale lze aktualizovat pouze jeden konkrétní kdykoli. Při aktualizaci účtu je aktualizovaná data odešlou přes síť dat archivu.  
  
 Tato ukázková aplikace používá všechny tři typy třídy synchronizace. Protože umožňuje v jednom okamžiku až tři účty, používá `CSemaphore` omezit přístup k tři objekty zobrazení. Při pokusu o zobrazení účet čtvrtý dojde, aplikace buď čeká, dokud jeden z prvních tří windows zavře nebo se nezdaří. Při aktualizaci účtu používá aplikace `CCriticalSection` zajistit, že je najednou aktualizován pouze jeden účet. Po úspěšné aktualizaci signalizuje `CEvent`, což uvolní vlákno čeká na signál události. Tento přístup z více vláken odešle nová data do dat archivu.  
  
## <a name="example-2-using-synchronization-access-classes"></a>Příklad 2: Pomocí synchronizační přístupové třídy  
 Výběr, které třídy přístupu používat je ještě jednodušší. Pokud vaše aplikace se týká přístup k jenom jeden řízené prostředku, použijte `CSingleLock`. Pokud potřebuje přístup k libovolnému počtu kontrolovaných prostředky, použít `CMultiLock`. V příkladu 1 `CSingleLock` by byl použit, protože v každém případě je potřeba jenom jeden prostředek v jakémkoli čase.  
  
 Informace o tom, jak se používají synchronizační třídy najdete v tématu [Multithreading: jak používat synchronizační třídy](../parallel/multithreading-how-to-use-the-synchronization-classes.md). Informace o synchronizaci najdete v tématu [synchronizace](http://msdn.microsoft.com/library/windows/desktop/ms686353) v [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]. Informace o podpoře více vláken v prostředí MFC najdete v tématu [Multithreading s C++ a MFC](../parallel/multithreading-with-cpp-and-mfc.md).  
  
## <a name="see-also"></a>Viz také  
 [Multithreading s použitím jazyka C++ a prostředí MFC](../parallel/multithreading-with-cpp-and-mfc.md)